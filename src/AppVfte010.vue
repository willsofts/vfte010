<!-- App.vue -->
<template>
  <div id="fswaitlayer" class="fa fa-spinner fa-spin"></div>
  <div class="pt-page pt-page-current pt-page-controller search-pager">
    <PageHeader ref="pageHeader" :labels="labels" pid="vfte010" version="1.0.0" showLanguage="true" @language-changed="changeLanguage" :multiLanguages="multiLanguages" :build="buildVersion" :visible="displayPageHeader" />
    <div id="fscontroltablayerpolicy" class="row">
      <ul class="nav nav-tabs navbar-left nav-tabbar-policy">
        <li class="nav-item active">
          <a @click="policySettingClick" id="policysettinglinker" class="nav-link active" href="#panelpolicysetting" data-toggle="tab">{{ labels.policy_setting }}</a>
        </li>
        <li class="nav-item">
          <a @click="reserveWordClick" id="reservewordlinker" class="nav-link" href="#panelreserveword" data-toggle="tab">{{ labels.reserve_setting }}</a>
        </li>
        <li class="nav-item">
          <a @click="reserveNumberClick" id="reservenumberlinker" class="nav-link" href="#panelreservenumber" data-toggle="tab">{{ labels.reservenumber_setting }}</a>
        </li>
      </ul>
    </div>    
    <div id="panelpolicysetting" v-show="visiblePanel('S')">
      <div id="entrylayerpolicy" class="entry-layer">
        <EntryForm ref="entryForm" :labels="labels" :dataCategory="dataCategory" @data-saved="dataSaved" @data-updated="dataUpdated" />
      </div>
    </div>
    <div id="panelreserveword" v-show="visiblePanel('W')">
      <SearchFormWord ref="searchFormWord" :labels="labels" :dataCategory="dataCategory" @data-select="dataSelectedWord" @data-insert="dataInsertWord" />
    </div>
    <div id="panelreservenumber" v-show="visiblePanel('N')">
      <SearchFormNumber ref="searchFormNumber" :labels="labels" :dataCategory="dataCategory" @data-select="dataSelectedNumber" @data-insert="dataInsertNumber" />
    </div>
  </div>
  <teleport to="#modaldialogword">
    <EntryFormWord ref="entryFormWord" :labels="labels" :dataCategory="dataCategory" @data-saved="dataSavedWord" @data-updated="dataUpdatedWord" @data-deleted="dataDeletedWord" />
  </teleport>
  <teleport to="#modaldialognum">
    <EntryFormNumber ref="entryFormNumber" :labels="labels" :dataCategory="dataCategory" @data-saved="dataSavedNumber" @data-updated="dataUpdatedNumber" @data-deleted="dataDeletedNumber" />
  </teleport>
</template>
<style>
#fscontroltablayerpolicy { margin-left: 10px; margin-right: 15px; padding-right: 3px; }
#entrylayerpolicy { margin-left: 15px; margin-top: 0px; }
.nav-tabbar-policy { width:100%; }
</style>
<script>
import { ref } from 'vue';
import { PageHeader } from '@willsofts/will-control';
import SearchFormWord from '@/components/SearchFormWord.vue';
import SearchFormNumber from '@/components/SearchFormNumber.vue';
import EntryForm from '@/components/EntryForm.vue';
import EntryFormWord from '@/components/EntryFormWord.vue';
import EntryFormNumber from '@/components/EntryFormNumber.vue';
import { getLabelModel, getMultiLanguagesModel, getMetaInfo } from "@willsofts/will-app";
import { getDefaultLanguage, setDefaultLanguage } from "@willsofts/will-app";
import { startApplication, loadAndMergeLabel }  from "@willsofts/will-app";

const buildVersion = process.env.VUE_APP_BUILD_DATETIME;
export default {
  components: {
    PageHeader, EntryForm, SearchFormWord, SearchFormNumber, EntryFormWord, EntryFormNumber
  },
  setup() {
    let labels = ref(getLabelModel());
    const multiLanguages = ref(getMultiLanguagesModel());
	const displayPageHeader = !(String(getMetaInfo().DISPLAY_PAGE_HEADER)=="false");
    const currentPanel = ref("S");
    return { displayPageHeader, buildVersion, multiLanguages, labels, currentPanel };
  },
  mounted() {
    console.log("App: mounted ...");
    this.$nextTick(async () => {
      //ensure ui completed then invoke startApplication 
      startApplication("vfte010",(data) => {
        console.log("vueapp: message",data);
        if(data.type=="language") {
          let lang = data.language;
          if(lang) {
            this.changeLanguage(lang);
          }
        } else {
          this.multiLanguages = getMultiLanguagesModel();
          this.messagingHandler(data);
          this.$refs.pageHeader.changeLanguage(getDefaultLanguage());
          loadAndMergeLabel("vfte010", (success) => {
            if (success) {
              this.changeLanguage(getDefaultLanguage());
            }
          });
        }
      });
    });
  },
  methods: {
    visiblePanel(name) {
      return this.currentPanel == name;
    },
    messagingHandler(data) {
      console.log("messagingHandler: data",data); 
    },
    changeLanguage(lang) {
      setDefaultLanguage(lang);
      let labelModel = getLabelModel(lang);
      this.labels = labelModel;
    },
    dataSaved(data,response) {
      //listen action from entry form when after saved
      console.log("App: record saved");
      console.log("data",data,"response",response);
    },
    dataUpdated(data,response) {
      //listen action from entry form when after updated
      console.log("App: record updated");
      console.log("data",data,"response",response);
    },
    dataSelectedWord(item,action) {
      //listen action from search form
      console.log("App: dataSelected",item,"action",action);
      if("edit"==action) {
        this.$refs.entryFormWord.retrieveRecord({reservepwd: item.reservepwd});
      } else if("delete"==action) {
        this.$refs.entryFormWord.startDeleteRecord({reservepwd: item.reservepwd});
      }
    },
    dataInsertWord(filters) {
      //listen action from search form
      console.log("App: record insert",filters);
      this.$refs.entryFormWord.startInsertRecord();
    },
    dataSavedWord(data,response) {
      //listen action from entry form when after saved
      console.log("App: record saved");
      console.log("data",data,"response",response);
      this.$refs.searchFormWord.search();
    },
    dataUpdatedWord(data,response) {
      //listen action from entry form when after updated
      console.log("App: record updated");
      console.log("data",data,"response",response);
      this.$refs.searchFormWord.search();
    },
    dataDeletedWord(data,response) {
      //listen action from entry form when after deleted
      console.log("App: record deleted");
      console.log("data",data,"response",response);
      this.$refs.searchFormWord.search(true);
    },
    dataSelectedNumber(item,action) {
      //listen action from search form
      console.log("App: dataSelected",item,"action",action);
      if("edit"==action) {
        this.$refs.entryFormNumber.retrieveRecord({reservenum: item.reservenum});
      } else if("delete"==action) {
        this.$refs.entryFormNumber.startDeleteRecord({reservenum: item.reservenum});
      }
    },
    dataInsertNumber(filters) {
      //listen action from search form
      console.log("App: record insert",filters);
      this.$refs.entryFormNumber.startInsertRecord();
    },
    dataSavedNumber(data,response) {
      //listen action from entry form when after saved
      console.log("App: record saved");
      console.log("data",data,"response",response);
      this.$refs.searchFormNumber.search();
    },
    dataUpdatedNumber(data,response) {
      //listen action from entry form when after updated
      console.log("App: record updated");
      console.log("data",data,"response",response);
      this.$refs.searchFormNumber.search();
    },
    dataDeletedNumber(data,response) {
      //listen action from entry form when after deleted
      console.log("App: record deleted");
      console.log("data",data,"response",response);
      this.$refs.searchFormNumber.search(true);
    },
    policySettingClick() {
      this.currentPanel = "S";
    },
    reserveWordClick() {
      this.currentPanel = "W";
    },
    reserveNumberClick() {
      this.currentPanel = "N";
    },
  }
};
</script>
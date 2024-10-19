<template>
        <div class="row row-height">
          <div class="col-height col-md-8">
            <div class="checkbox form-check">
              <input ref="checkreservepwd" type="checkbox" id="checkreservepwd" true-value="1" false-value="0" v-model="localData.checkreservepwd" class="form-control input-md form-check-input" />
              <label for="checkreservepwd" class="control-label">{{ labels.checkreservepwd_label }}</label>
						</div>
          </div>
        </div>
        <div class="row row-height">
          <div class="col-height col-md-8">
            <div class="checkbox form-check">
              <input ref="checkmatchnumber" type="checkbox" id="checkmatchnumber" true-value="1" false-value="0" v-model="localData.checkmatchnumber" class="form-control input-md form-check-input" />
              <label for="checkmatchnumber" class="control-label">{{ labels.checkmatchnumber_label }}</label>
						</div>
          </div>
        </div>
        <div class="row row-height">
          <div class="col-height col-md-8">
            <div class="checkbox form-check">
              <input ref="checkpersonal" type="checkbox" id="checkpersonal" true-value="1" false-value="0" v-model="localData.checkpersonal" class="form-control input-md form-check-input" />
              <label for="checkpersonal" class="control-label">{{ labels.checkpersonal_label }}</label>
						</div>
          </div>
        </div>
        <div class="row row-height">
          <div class="col-height col-md-3">
            <label for="pwdexpireday" class="control-label">{{ labels.pwdexpireday_label }}</label>
            <div class="input-group has-validation" :class="{'has-error': v$.pwdexpireday.$error}">
              <InputNumber ref="pwdexpireday" v-model="localData.pwdexpireday" id="pwdexpireday" /> 
              <label class="required">*</label>
            </div>
            <span v-if="v$.pwdexpireday.$error" class="has-error">{{ v$.pwdexpireday.$errors[0].$message }}</span>
          </div>
        </div>
        <div class="row row-height">
          <div class="col-height col-md-3">
            <label for="minpwdlength" class="control-label">{{ labels.minpwdlength_label }}</label>
            <div class="input-group has-validation" :class="{'has-error': v$.minpwdlength.$error}">
              <InputNumber ref="minpwdlength" v-model="localData.minpwdlength" id="minpwdlength" /> 
              <label class="required">*</label>
            </div>
            <span v-if="v$.minpwdlength.$error" class="has-error">{{ v$.minpwdlength.$errors[0].$message }}</span>
          </div>
        </div>
        <div class="row row-height">
          <div class="col-height col-md-3">
            <label for="maxpwdlength" class="control-label">{{ labels.maxpwdlength_label }}</label>
            <div class="input-group has-validation" :class="{'has-error': v$.maxpwdlength.$error}">
              <InputNumber ref="maxpwdlength" v-model="localData.maxpwdlength" id="maxpwdlength" /> 
              <label class="required">*</label>
            </div>
            <span v-if="v$.maxpwdlength.$error" class="has-error">{{ v$.maxpwdlength.$errors[0].$message }}</span>
          </div>
        </div>
        <div class="row row-height">
          <div class="col-height col-md-3">
            <label for="alphainpwd" class="control-label">{{ labels.alphainpwd_label }}</label>
            <div class="input-group has-validation" :class="{'has-error': v$.alphainpwd.$error}">
              <InputNumber ref="alphainpwd" v-model="localData.alphainpwd" id="alphainpwd" /> 
              <label class="required">*</label>
            </div>
            <span v-if="v$.alphainpwd.$error" class="has-error">{{ v$.alphainpwd.$errors[0].$message }}</span>
          </div>
        </div>
        <div class="row row-height">
          <div class="col-height col-md-3">
            <label for="otherinpwd" class="control-label">{{ labels.otherinpwd_label }}</label>
            <div class="input-group has-validation" :class="{'has-error': v$.otherinpwd.$error}">
              <InputNumber ref="otherinpwd" v-model="localData.otherinpwd" id="otherinpwd" /> 
              <label class="required">*</label>
            </div>
            <span v-if="v$.otherinpwd.$error" class="has-error">{{ v$.otherinpwd.$errors[0].$message }}</span>
          </div>
        </div>
        <div class="row row-height">
          <div class="col-height col-md-3">
            <label for="digitinpwd" class="control-label">{{ labels.digitinpwd_label }}</label>
            <div class="input-group has-validation" :class="{'has-error': v$.digitinpwd.$error}">
              <InputNumber ref="digitinpwd" v-model="localData.digitinpwd" id="digitinpwd" /> 
              <label class="required">*</label>
            </div>
            <span v-if="v$.digitinpwd.$error" class="has-error">{{ v$.digitinpwd.$errors[0].$message }}</span>
          </div>
        </div>
        <div class="row row-height">
          <div class="col-height col-md-3">
            <label for="upperinpwd" class="control-label">{{ labels.upperinpwd_label }}</label>
            <div class="input-group has-validation" :class="{'has-error': v$.upperinpwd.$error}">
              <InputNumber ref="upperinpwd" v-model="localData.upperinpwd" id="upperinpwd" /> 
              <label class="required">*</label>
            </div>
            <span v-if="v$.upperinpwd.$error" class="has-error">{{ v$.upperinpwd.$errors[0].$message }}</span>
          </div>
        </div>
        <div class="row row-height">
          <div class="col-height col-md-3">
            <label for="lowerinpwd" class="control-label">{{ labels.lowerinpwd_label }}</label>
            <div class="input-group has-validation" :class="{'has-error': v$.lowerinpwd.$error}">
              <InputNumber ref="lowerinpwd" v-model="localData.lowerinpwd" id="lowerinpwd" /> 
              <label class="required">*</label>
            </div>
            <span v-if="v$.lowerinpwd.$error" class="has-error">{{ v$.lowerinpwd.$errors[0].$message }}</span>
          </div>
        </div>
        <div class="row row-height">
          <div class="col-height col-md-3">
            <label for="timenotusedoldpwd" class="control-label">{{ labels.timenotusedoldpwd_label }}</label>
            <div class="input-group has-validation" :class="{'has-error': v$.timenotusedoldpwd.$error}">
              <InputNumber ref="timenotusedoldpwd" v-model="localData.timenotusedoldpwd" id="timenotusedoldpwd" /> 
              <label class="required">*</label>
            </div>
            <span v-if="v$.timenotusedoldpwd.$error" class="has-error">{{ v$.timenotusedoldpwd.$errors[0].$message }}</span>
          </div>
        </div>
        <div class="row row-height">
          <div id="fs_controlbuttonfooterlayer" class="col-md-12 pull-right text-right">
            <button ref="savebutton" id="savebutton" class="btn btn-dark btn-sm" @click="saveClick" v-if="insertMode"><em class="fa fa-save fa-btn-icon"></em>{{ labels.save_button }}</button>
            <button ref="updatebutton" id="updatebutton" class="btn btn-dark btn-sm" @click="updateClick" v-if="updateMode"><em class="fa fa-save fa-btn-icon"></em>{{ labels.update_button }}</button>
          </div>
        </div>
</template>
<style>
label.control-label { white-space: nowrap; }
#fs_controlbuttonfooterlayer { margin-right: 20px; margin-bottom:5px; margin-top: 10px; }
#fs_controlbuttonfooterlayer button { margin-right: 5px; }
</style>
<script>
import { ref, computed, watch } from 'vue';
import { useVuelidate } from '@vuelidate/core';
import { required, helpers } from '@vuelidate/validators';
import $ from "jquery";
import { DEFAULT_CONTENT_TYPE, getApiUrl, disableControls }  from '@willsofts/will-app';
import { startWaiting, stopWaiting, submitFailure, detectErrorResponse }  from '@willsofts/will-app';
import { confirmUpdate, confirmSave, successbox, serializeParameters } from '@willsofts/will-app';
import { InputNumber } from '@willsofts/will-control';

const APP_URL = "/api/sfte010";
const defaultData = {
  userid: "DEFAULT",
  checkreservepwd: "1",
  checkmatchnumber: "0",
  checkpersonal: "0",
  pwdexpireday: 120,
  minpwdlength: 3,
  maxpwdlength: 8,
  alphainpwd: 1,
  otherinpwd: 1,
  digitinpwd: 1,
  upperinpwd: 1,
  lowerinpwd: 1,
  timenotusedoldpwd: 0,
};

export default {
  components: {
    InputNumber
  },
  props: {
    modes: Object,
    labels: Object,
    dataCategory: Object
  },
  emits: ["data-saved","data-updated","data-retrieved"],
  setup(props) {
    const mode = ref({action: "new", ...props.modes});
    const localData = ref({ ...defaultData }); 
    const disabledKeyField = ref(false);
    const reqalert = ref(props.labels.empty_alert);
    const requiredMessage = () => {
      return helpers.withMessage(reqalert, required);
    }
    const validateRules = computed(() => { 
      return {
        pwdexpireday: { required: requiredMessage() },
        minpwdlength: { required: requiredMessage() },
        maxpwdlength: { required: requiredMessage() },
        alphainpwd: { required: requiredMessage() },
        otherinpwd: { required: requiredMessage() },
        digitinpwd: { required: requiredMessage() },
        upperinpwd: { required: requiredMessage() },
        lowerinpwd: { required: requiredMessage() },
        timenotusedoldpwd: { required: requiredMessage() },
      } 
    });
    const v$ = useVuelidate(validateRules, localData, { $lazy: true, $autoDirty: true });
    return { mode, v$, localData, disabledKeyField, reqalert };
  },
  created() {
    watch(this.$props, (newProps) => {      
      this.reqalert = newProps.labels.empty_alert;
    });
  },
  computed: {
    insertMode() {
      return this.mode.action=="insert" || this.mode.action=="new";
    },
    updateMode() {
      return this.mode.action=="update" || this.mode.action=="edit";
    },
  },
  mounted() {
    this.$nextTick(function () {
      this.retrieveRecord();
    });
  },
  methods: {
    reset(newData,newMode) {
      if(newData) this.localData = {...newData};
      if(newMode) this.mode = {...newMode};
    },
    async saveClick() {
      console.log("click: save");
      disableControls($("#savebutton"));
      let valid = await this.validateForm();
      if(!valid) return;
      this.startSaveRecord();
    },
    async updateClick() {
      console.log("click: update");
      disableControls($("#updatebutton"));
      let valid = await this.validateForm();
      if(!valid) return;
      this.startUpdateRecord();
    },
    async validateForm(focusing=true) {
      const valid = await this.v$.$validate();
      console.log("validate form: valid",valid);
      console.log("error:",this.v$.$errors);
      if(!valid) {
        if(focusing) {
          this.focusFirstError();
        }
        return false;
      }
      return true;
    },
    focusFirstError() {
      if(this.v$.$errors && this.v$.$errors.length > 0) {
        let input = this.v$.$errors[0].$property;
        let el = this.$refs[input];
        if(el) el.focus(); //if using ref
        else $("#"+input).trigger("focus"); //if using id
      }
    },
    resetRecord() {
      //reset to default data 
      this.reset(defaultData,{action:"insert"});
      //reset validator
      this.v$.$reset();
      //enable key field
      this.disabledKeyField = false;
    },
    startInsertRecord() {
      this.resetRecord();
    },
    startSaveRecord() {
      confirmSave(() => {
        this.saveRecord(this.localData);
      });
    },
    startUpdateRecord() {
      confirmUpdate(() => { 
        this.updateRecord(this.localData);
      });
    },
    saveRecord(dataRecord) {
        let jsondata = {ajax: true};
        let formdata = serializeParameters(jsondata,dataRecord);
        startWaiting();
        $.ajax({
          url: getApiUrl()+APP_URL+"/insertpolicy",
          data: formdata.jsondata,
          headers : formdata.headers,
          type: "POST",
          dataType: "json",
          contentType: DEFAULT_CONTENT_TYPE,
          error : function(transport,status,errorThrown) {
            console.error("error: status",status,"errorThrown",errorThrown);
            submitFailure(transport,status,errorThrown);
          },
          success: (data) => {
            stopWaiting();
            console.log("success",data);
            if(detectErrorResponse(data)) return;
            successbox(() => {
              //reset data for new record insert
              this.resetRecord();
              this.$emit('data-saved',dataRecord,data);
            });
          }
      });
    },
    updateRecord(dataRecord) {
        let jsondata = {ajax: true};
        let formdata = serializeParameters(jsondata,dataRecord);
        startWaiting();
        $.ajax({
          url: getApiUrl()+APP_URL+"/updatepolicy",
          data: formdata.jsondata,
          headers : formdata.headers,
          type: "POST",
          dataType: "json",
          contentType: DEFAULT_CONTENT_TYPE,
          error : function(transport,status,errorThrown) {
            console.error("error: status",status,"errorThrown",errorThrown);
            submitFailure(transport,status,errorThrown);
          },
          success: (data) => {
            stopWaiting();
            console.log("success",data);
            if(detectErrorResponse(data)) return;
            successbox(() => {
              this.$emit('data-updated',dataRecord,data);
            });
          }
      });
    },
    retrieveRecord(dataKeys) {
      let jsondata = {ajax: true};
      let formdata = serializeParameters(jsondata,dataKeys || {});
      startWaiting();
      $.ajax({
        url: getApiUrl()+APP_URL+"/retrievepolicy",
        data: formdata.jsondata,
        headers : formdata.headers,
        type: "POST",
        dataType: "json",
        contentType: DEFAULT_CONTENT_TYPE,
        error : function(transport,status,errorThrown) {
          console.error("retrieveRecord: error: status",status,"errorThrown",errorThrown);
          submitFailure(transport,status,errorThrown);
        },
        success: (data) => {
          stopWaiting();
          console.log("retrieveRecord: success",data);
          if(data.body.dataset) {
            if(data.body.action=="add") {
              this.reset(Object.assign({},defaultData,data.body.dataset),{action:"insert"});
            } else {
              this.reset(data.body.dataset,{action:"edit"});
            }
            this.v$.$reset();
            this.disabledKeyField = true;
            this.$emit('data-retrieved',dataKeys,data);
          }
        }
      });	
    },
  }
};
</script>

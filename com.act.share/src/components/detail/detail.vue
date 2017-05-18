<template>
  <div class="detail">
    <helmet :actDetail="actDetail" :defaultUrl="url"></helmet>
    <basicmsg :actDetail="actDetail" :defaultUrl="url"></basicmsg>
  </div>
</template>

<script type="text/ecmascript-6">
import helmet from 'components/helmet/helmet';
import basicmsg from 'components/basicmsg/basicmsg';

const URL = 'http://dever.juju.im/jsm/utils/downloadImg/';

export default {
    data() {
      return {
        actDetail: {},
        url: URL
      };
    },
    created() {
        this.$http.get('http://dever.juju.im/jsf/activity/getActivityDetail', {params: {userId: this.$route.params.userId, activityId: this.$route.params.id}}).then(response => {
            response.json();
            response = response.body;
            if (response.code === '1') {
               this.actDetail = response.data;
               console.log(JSON.parse(JSON.stringify(this.actDetail)));
            }
        });
    },
    components: {
        helmet,
        basicmsg
    }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>

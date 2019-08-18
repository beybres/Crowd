<template>
    <Page>
        <ActionBar title="CROWD"/>
        <GridLayout columns="*" rows="*">
            <Label class="message" :text="msg" col="0" row="0"/>
        </GridLayout>

        <Button id="mainbutton" text="Color" class="btn btn-primary btn-rounded-sm"/>
    </Page>
</template>

<script>
  export default {
    data() {
      return {
        msg: 'Hello World!'
      };
    },
  }
</script>

<style scoped>
    ActionBar {
        background-color: #2274A5;
        color: #ffffff;
    }

    .message {
        vertical-align: center;
        text-align: center;
        font-size: 20;
        color: #333333;
    }
</style>

<template>
    <Page>
    <ActionBar title="CROWD"/>
      <Stacklayout>
        <TabView height="300px">
          <TabViewItem title="Favourites">
            <Label text="En sida med favourites" />
          </TabViewItem>
        <TabViewItem title="Search">
          <Label text="En söksida" />
        </TabViewItem>
          <TabViewItem title="Settings">
            <Label text="En sida med inställningar" />
          </TabViewItem>
          </TabView>
      </Stacklayout>
    </Page>
</template>

<script>
  export default {
    data() {
      return {
        msg: 'Hello World!'
      }
    }
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

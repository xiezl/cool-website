<template>
  <el-container class="main">
    <div class="header">
      <svg-icon icon-class="logo"
                class="logo" />
    </div>
    <el-container class="top-container">
      <el-col>
        <el-row class="top-title">Cool: a COhort OnLine analytical processing system</el-row>
        <el-row class="sub-top-title">Cool is an online cohort analytical processing system that
          supports various types of data analytics,including cubequery,
          ice-berg query and cohort query.The objective of Cool is to
          provide high performance (nearreal-time) analytical response
          for emerging data warehouse domain.
        </el-row>
      </el-col>
      <el-col>
        <svg-icon icon-class="p1"
                  class="p1" />
      </el-col>
    </el-container>
    <el-container class="box">
      <el-row class="title">Architecture</el-row>
      <el-container class="arch-container">
        <el-col :span="12">
          <svg-icon icon-class="p2"
                    class="p1" />
        </el-col>
        <el-col :span="12"
                class="arch-title">
          Similar to conventional databases, Cool organizes data records
          intables. Each table is maintained by a user-defined schema,
          consisting of multiple columns called fields or dimensions. A
          dimension filere cording the hierarchy of several dimensions is
          also given by the users in order to support cube queries.Each
          dimension of the table is bound to a field type describing the
          format of the values.The primitive types include varied-length
          integer, float, string,boolean, time and event.The first four are
          similar to underlying database types while the remaining types
          are specifically defined by Cool.Time deals with the timestamps
          of the records and event is a particular string representing user
          actions or behaviors. A dimension tree is constructed in systems
          etup guided by the dimension file and persisted in storage.
        </el-col>
      </el-container>
    </el-container>
    <el-container class="box">
      <el-row class="title">Storage Layout</el-row>
      <el-row class="storage-desc">Cool employs a hybrid orientation plan for data storage.
        The tables are horizontally split into
        different partitions called cublets. Each cublet consists of multiple chunks,
        where the metaChunk contains all the values for a corresponding field in this cublet.
      </el-row>
      <el-row class="storage-content">
        <svg-icon icon-class="p3"
                  class="p1" />
      </el-row>
    </el-container>
    <el-container class="box query-box">
      <el-row class="query-title">Data Model & Query</el-row>
      <el-row class="query-desc">
        In Cool, all the queries are written in JSON format with a pre-defined syntax.
        Two types of queries are supported:
      </el-row>
      <el-container class="query-container">
        <el-row>
          <svg-icon icon-class="icon1" />
        </el-row>
        <el-row v-for="(item,index) in queryList"
                :key="index">{{item}}</el-row>
      </el-container>
    </el-container>
    <el-container class="example">
      <el-row class="example-title">Here are two query examples:</el-row>
      <el-row>
        <svg-icon icon-class="icon2"
                  class="icon2" />
      </el-row>
      <el-container class="code-container">
        <el-col>
          <svg-icon icon-class="code1" />
        </el-col>
        <el-col>
          <svg-icon icon-class="code2" />
        </el-col>
      </el-container>
    </el-container>
    <el-container class="box demo">
      <el-row class="title">Demo</el-row>
      <el-row class="storage-desc">
        Cool is born from our previous work, Cohana,
        a cohort analysis processing system.
        Here is a video illustrating ageneral example about
        cohort analysis and our systems:
      </el-row>
      <el-row class="img-content">
        <img src="@/assets/images/demo.jpg" />
      </el-row>
    </el-container>
    <el-container class="box footer">
      <el-row>We will release our code and
        the new version of Cool in a very near future.
      </el-row>
      <el-row>Please keep attention!</el-row>
      <el-row></el-row>
      <el-row>
        © 2020 DBsystem &nbsp; &nbsp; &nbsp;
        All rights reserved by the team from DBsystem, School of Computing, NUS
      </el-row>
    </el-container>
  </el-container>
</template>

<script>
export default {
  data() {
    return {
      queryList: [
        '(1) OLAP query. Cool can be treated as a conventional OLAP system dealing with cube queries.The system supports basic cube operations, including roll-up, drill-down, pivot and slice and dice,upon data cubes built atop the fields and the dimension tree. Cool can also provide responses for iceberg query, a prevailing type of query selecting a small number of records which satisfy some given conditions.',
        '(2) Cohort Query. Cool cansupport an enhanced version of cohort queries.Traditional cohort query can only support aggregations on cohorts born with a single event along a fixed time window.However, Cool supports aggregations on cohorts born with a series of events, namely an event sequence, along either a fixed time window or an elastictime window delimited by givenevents. ',
        'Cool supports composite query processing by runninga successive query atop the result of a precedentquery.  The type of the precedent query and the successive query can be any combination of the two aforementioned query types.For instance, a cohort generated in a precedent cohort query can act as a data source for either a successive OLAP query or a successive cohort query.Such composite query is sometimes called funnel analysis in the literature. In the implementation,based on the user-defined schema and the dimension tree, data cube and cohort are stored conceptually as the intermediate structures to support such query. The meaning of “conceptually”here isthat Cool materializes the matched records of the precedent query as well as the correspondingd imension structure int hestorage layer and aggregates the corresponding results in runtime,instead of storingt here sultant cohort or data cube tuplesdirectly. By default,such intermediate structure sexistina fixed period and the system can be configured toper sisthempermanently.',
      ],
    };
  },
};
</script>

<style lang="scss" scoped>
@import '@/assets/styles/views/dashboard.scss';
</style>

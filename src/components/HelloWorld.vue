<template>
    <div class="container">
        <ais-instant-search
                :search-client="searchClient"
                index-name="poki"
        >
            <div class="search-panel">
                <div class="search-panel__results">
                    <ais-search-box placeholder="Search here…" class="searchbox"/>
                    <ais-hits>
                        <template slot="item" slot-scope="{ item }">
                            <h1>
                                <ais-highlight :hit="item" attribute="name.french"/>
                            </h1>
                            <p>
                                HP :
                                <ais-highlight :hit="item" attribute="base.HP"/>
                            </p>
                            <p>
                                Attack :
                                <ais-highlight :hit="item" attribute="base.Attack"/>
                            </p>
                            <p>
                                Defense :
                                <ais-highlight :hit="item" attribute="base.Defense"/>
                            </p>
                            <p>
                                Attack sp. :
                                <ais-highlight :hit="item" attribute="base.Sp. Attack"/>
                            </p>
                            <p>
                                Defense sp. :
                                <ais-highlight :hit="item" attribute="base.Sp. Defense"/>
                            </p>
                            <p>
                                Speed :
                                <ais-highlight :hit="item" attribute="base.Speed"/>
                            </p>
                        </template>
                    </ais-hits>

                    <div class="pagination">
                        <ais-pagination/>
                    </div>
                </div>
            </div>
        </ais-instant-search>
    </div>
</template>

<script>

  import algoliasearch from 'algoliasearch/lite';

  export default {
    name: 'SearchTest',
    props: {
      msg: String
    },
    data() {
      return {
        searchClient: algoliasearch(
          'QZGU4SAHW5',
          'e8fc66beb42ff8fce47b917140d83646'
        ),
      };
    },
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    h1 {
        margin: 0;
        padding: 0;
    }

    body {
        font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica,
        Arial, sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol';
    }

    .ais-Highlight-highlighted {
        background: cyan;
        font-style: normal;
    }

    .header {
        display: flex;
        align-items: center;
        min-height: 50px;
        padding: 0.5rem 1rem;
        background-image: linear-gradient(to right, #4dba87, #2f9088);
        color: #fff;
        margin-bottom: 1rem;
    }

    .header a {
        color: #fff;
        text-decoration: none;
    }

    .header-title {
        font-size: 1.2rem;
        font-weight: normal;
    }

    .header-title::after {
        content: ' ▸ ';
        padding: 0 0.5rem;
    }

    .header-subtitle {
        font-size: 1.2rem;
    }

    .container {
        max-width: 1200px;
        margin: 0 auto;
        padding: 1rem;
    }

    .search-panel {
        display: flex;
    }

    .search-panel__filters {
        flex: 1;
        margin-right: 1em;
    }

    .search-panel__results {
        flex: 3;
    }

    .searchbox {
        margin-bottom: 2rem;
    }

    .pagination {
        margin: 2rem auto;
        text-align: center;
    }
</style>


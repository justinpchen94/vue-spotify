<script>
import {mapState} from 'vuex'

import SearchResult from './SearchResult.vue'

export default {
  name: 'search-results',
  components: [
    SearchResult
  ],
  computed: mapState([
    'isBusy',
    'results'
  ]),
  render (h) {
    return (
      <div class='search-results'>
        {this.isBusy
          ? <div class='loading-overlay'>
              <i class="loading fa fa-spinner fa-pulse fa-4x fa-fw"></i>
            </div>
          : <ul class='results-list'>
              {this.results.map((item) => <SearchResult result={item} />)}
            </ul>
        }
      </div>
    )
  }
}
</script>

<style>
.search-results {
  background-color: #3F3F3F;
  height: calc(100vh - 108px);
  overflow-y: auto;
  padding-top: 54px;
  width: 100%;

  -webkit-overflow-scrolling: touch;
}
.results-list {
  list-style-type: none;
  padding: 0 0 0 0.25em;
  margin: 0;
}
.loading-overlay {
  background-color: #303030;
  height: 100%;
  opacity: 0.3;
  position: fixed;
  width: 100%;
  z-index: 1;
}
.loading {
  left: 50%;
  margin: -0.75em 0 0 -0.75em;
  position: fixed;
  top: 50%;
}
.results-list>li:not(:last-child) {
  border-bottom: 1px solid rgba(255, 255, 255, 0.5);
}
</style>

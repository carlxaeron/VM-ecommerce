<!-- =========================================================================================
  File Name: ECommerceShop.vue
  Description: eCommerce Shop Page
  ----------------------------------------------------------------------------------------
  Item Name: Vuexy - Vuejs, HTML & Laravel Admin Dashboard Template
    Author: Pixinvent
  Author URL: http://www.themeforest.net/user/pixinvent
========================================================================================== -->

<template>
  <div>
    <ais-instant-search :search-client="searchClient" index-name="instant_search" id="algolia-instant-search-demo">
      <!-- AIS CONFIG -->
      <ais-configure :hits-per-page.camel="6" />

      <div id="algolia-content-container" class="relative clearfix">

        <!-- RIGHT COL -->
        <div>

          <!-- SEARCH RESULT -->
          <ais-hits>
            <div slot-scope="{ items }">

              <!-- GRID VIEW -->
              <template v-if="currentItemView == 'item-grid-view'">
                <h2 class="mb-6">Daily Deals</h2>
                <div class="items-grid-view vx-row match-height">
                  <div class="vx-col lg:w-1/3 sm:w-1/2 w-full" v-for="item in items" :key="item.objectID">

                    <item-grid-view :item="item">
                      <!-- SLOT: ACTION BUTTONS -->
                      <template slot="action-buttons">
                        <div class="flex flex-wrap">

                          <!-- PRIMARY BUTTON: ADD TO WISH LIST -->
                          <div
                            class="item-view-primary-action-btn p-3 flex flex-grow items-center justify-center cursor-pointer"
                            @click="toggleItemInWishList(item)">
                            <feather-icon icon="HeartIcon"
                              :svgClasses="[{'text-danger fill-current' : isInWishList(item.objectID)}, 'h-4 w-4']" />

                            <span class="text-sm font-semibold ml-2">WISHLIST</span>
                          </div>

                          <!-- SECONDARY BUTTON: ADD-TO/VIEW-IN CART -->
                          <div
                            class="item-view-secondary-action-btn bg-primary p-3 flex flex-grow items-center justify-center text-white cursor-pointer"
                            @click="cartButtonClicked(item)">
                            <feather-icon icon="ShoppingBagIcon" svgClasses="h-4 w-4" />

                            <span class="text-sm font-semibold ml-2" v-if="isInCart(item.objectID)">VIEW IN CART</span>
                            <span class="text-sm font-semibold ml-2" v-else>ADD TO CART</span>
                          </div>
                        </div>
                      </template>
                    </item-grid-view>

                  </div>
                </div>
              </template>

              <!-- LIST VIEW -->
              <template v-else>
                <div class="items-list-view mb-base" v-for="item in items" :key="item.objectID">

                  <item-list-view :item="item">

                    <!-- SLOT: ACTION BUTTONS -->
                    <template slot="action-buttons">
                      <div
                        class="item-view-primary-action-btn p-3 rounded-lg flex flex-grow items-center justify-center cursor-pointer mb-3"
                        @click="toggleItemInWishList(item)">
                        <feather-icon icon="HeartIcon"
                          :svgClasses="[{'text-danger fill-current' : isInWishList(item.objectID)}, 'h-4 w-4']" />
                        <span class="text-sm font-semibold ml-2">WISHLIST</span>
                      </div>
                      <div
                        class="item-view-secondary-action-btn bg-primary p-3 rounded-lg flex flex-grow items-center justify-center text-white cursor-pointer"
                        @click="cartButtonClicked(item)">
                        <feather-icon icon="ShoppingBagIcon" svgClasses="h-4 w-4" />

                        <span class="text-sm font-semibold ml-2" v-if="isInCart(item.objectID)">VIEW IN CART</span>
                        <span class="text-sm font-semibold ml-2" v-else>ADD TO CART</span>
                      </div>
                    </template>
                  </item-list-view>

                </div>
              </template>
            </div>
          </ais-hits>
        </div>
      </div>
    </ais-instant-search>

    <ais-instant-search :search-client="searchClient" index-name="instant_search" id="algolia-instant-search-demo">
      <!-- AIS CONFIG -->
      <ais-configure :hits-per-page.camel="6" />

      <div id="algolia-content-container" class="relative clearfix">

        <!-- RIGHT COL -->
        <div>

          <!-- SEARCH RESULT -->
          <ais-hits>
            <div slot-scope="{ items }">

              <!-- GRID VIEW -->
              <template v-if="currentItemView == 'item-grid-view'">
                <h2 class="mb-6">Top Picks</h2>
                <div class="items-grid-view vx-row match-height">
                  <div class="vx-col lg:w-1/3 sm:w-1/2 w-full" v-for="item in items" :key="item.objectID">

                    <item-grid-view :item="item">
                      <!-- SLOT: ACTION BUTTONS -->
                      <template slot="action-buttons">
                        <div class="flex flex-wrap">

                          <!-- PRIMARY BUTTON: ADD TO WISH LIST -->
                          <div
                            class="item-view-primary-action-btn p-3 flex flex-grow items-center justify-center cursor-pointer"
                            @click="toggleItemInWishList(item)">
                            <feather-icon icon="HeartIcon"
                              :svgClasses="[{'text-danger fill-current' : isInWishList(item.objectID)}, 'h-4 w-4']" />

                            <span class="text-sm font-semibold ml-2">WISHLIST</span>
                          </div>

                          <!-- SECONDARY BUTTON: ADD-TO/VIEW-IN CART -->
                          <div
                            class="item-view-secondary-action-btn bg-primary p-3 flex flex-grow items-center justify-center text-white cursor-pointer"
                            @click="cartButtonClicked(item)">
                            <feather-icon icon="ShoppingBagIcon" svgClasses="h-4 w-4" />

                            <span class="text-sm font-semibold ml-2" v-if="isInCart(item.objectID)">VIEW IN CART</span>
                            <span class="text-sm font-semibold ml-2" v-else>ADD TO CART</span>
                          </div>
                        </div>
                      </template>
                    </item-grid-view>

                  </div>
                </div>
              </template>

              <!-- LIST VIEW -->
              <template v-else>
                <div class="items-list-view mb-base" v-for="item in items" :key="item.objectID">

                  <item-list-view :item="item">

                    <!-- SLOT: ACTION BUTTONS -->
                    <template slot="action-buttons">
                      <div
                        class="item-view-primary-action-btn p-3 rounded-lg flex flex-grow items-center justify-center cursor-pointer mb-3"
                        @click="toggleItemInWishList(item)">
                        <feather-icon icon="HeartIcon"
                          :svgClasses="[{'text-danger fill-current' : isInWishList(item.objectID)}, 'h-4 w-4']" />
                        <span class="text-sm font-semibold ml-2">WISHLIST</span>
                      </div>
                      <div
                        class="item-view-secondary-action-btn bg-primary p-3 rounded-lg flex flex-grow items-center justify-center text-white cursor-pointer"
                        @click="cartButtonClicked(item)">
                        <feather-icon icon="ShoppingBagIcon" svgClasses="h-4 w-4" />

                        <span class="text-sm font-semibold ml-2" v-if="isInCart(item.objectID)">VIEW IN CART</span>
                        <span class="text-sm font-semibold ml-2" v-else>ADD TO CART</span>
                      </div>
                    </template>
                  </item-list-view>

                </div>
              </template>
            </div>
          </ais-hits>
        </div>
      </div>
    </ais-instant-search>
  </div>
</template>

<script>
import {
  AisClearRefinements,
  AisConfigure,
  AisHierarchicalMenu,
  AisHits,
  AisInstantSearch,
  AisNumericMenu,
  AisPagination,
  AisRangeInput,
  AisRatingMenu,
  AisRefinementList,
  AisSearchBox,
  AisSortBy,
  AisStats
} from 'vue-instantsearch'
import algoliasearch from 'algoliasearch/lite'

export default {
  components: {
    ItemGridView: () => import('./components/ItemGridView.vue'),
    ItemListView: () => import('./components/ItemListView.vue'),
    AisClearRefinements,
    AisConfigure,
    AisHierarchicalMenu,
    AisHits,
    AisInstantSearch,
    AisNumericMenu,
    AisPagination,
    AisRangeInput,
    AisRatingMenu,
    AisRefinementList,
    AisSearchBox,
    AisSortBy,
    AisStats
  },
  data () {
    return {
      searchClient: algoliasearch(
        'latency',
        '6be0576ff61c053d5f9a3225e2a90f76'
      ),
      // Filter Sidebar
      isFilterSidebarActive: true,
      clickNotClose: true,
      currentItemView: 'item-grid-view',
      numericItems:
      [
        {
          label: 'All'
        },
        {
          label: '<= $10',
          end: 10
        },
        {
          label: '$10 - $100',
          start: 10,
          end: 100
        },
        {
          label: '$100 - $500',
          start: 100,
          end: 500
        },
        {
          label: '>= $500',
          start: 500
        }
      ],
      algoliaCategories: [
        'hierarchicalCategories.lvl0',
        'hierarchicalCategories.lvl1',
        'hierarchicalCategories.lvl2',
        'hierarchicalCategories.lvl3'
      ]
    }
  },
  computed: {
    toValue () {
      return (value, range) => [
        value.min !== null ? value.min : range.min,
        value.max !== null ? value.max : range.max
      ]
    },

    // GRID VIEW
    isInCart () {
      return (itemId) => this.$store.getters['eCommerce/isInCart'](itemId)
    },
    isInWishList () {
      return (itemId) => this.$store.getters['eCommerce/isInWishList'](itemId)
    },
    windowWidth () {
      return this.$store.state.windowWidth
    }
  },
  watch: {
    windowWidth () {
      this.setSidebarWidth()
    }
  },
  methods: {
    setSidebarWidth () {
      if (this.windowWidth < 992) {
        this.isFilterSidebarActive = this.clickNotClose = false
      } else {
        this.isFilterSidebarActive = this.clickNotClose = true
      }
    },

    // GRID VIEW - ACTIONS
    toggleFilterSidebar () {
      if (this.clickNotClose) return
      this.isFilterSidebarActive = !this.isFilterSidebarActive
    },
    toggleItemInWishList (item) {
      this.$store.dispatch('eCommerce/toggleItemInWishList', item)
    },
    additemInCart (item) {
      this.$store.dispatch('eCommerce/additemInCart', item)
    },
    cartButtonClicked (item) {
      this.isInCart(item.objectID) ? this.$router.push('/apps/eCommerce/checkout').catch(() => { }) : this.additemInCart(item)
    }
  },
  created () {
    this.setSidebarWidth()
  }
}
</script>

<style lang="scss">
#algolia-instant-search-demo {
  .algolia-header {
    .algolia-filters-label {
      width: calc(260px + 2.4rem);
    }
  }

  #algolia-content-container {

    .vs-sidebar {
      position: relative;
      float: left;
    }
  }

  .algolia-search-input-right-aligned-icon {
    padding: 1rem 1.5rem;
  }

  .algolia-price-slider {
    min-width: unset;
  }

  .item-view-primary-action-btn {
    color: #2c2c2c !important;
    background-color: #f6f6f6;
    min-width: 50%;
  }

  .item-view-secondary-action-btn {
    min-width: 50%;
  }
}

.theme-dark {
  #algolia-instant-search-demo {
    #algolia-content-container {
      .vs-sidebar {
        background-color: #10163a;
      }
    }
  }
}

@media (min-width: 992px) {
  .vs-sidebar-rounded {
    .vs-sidebar {
      border-radius: .5rem;
    }

    .vs-sidebar--items {
      border-radius: .5rem;
    }
  }
}

@media (max-width: 992px) {
  #algolia-content-container {
    .vs-sidebar {
      position: absolute !important;
      float: none !important;
    }
  }
}
</style>

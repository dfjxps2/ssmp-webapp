<script lang="jsx">
  import Vue from 'vue'
  import {Tree as ElTree} from 'element-ui'

  Vue.use(ElTree)

  export default {
    name: 'MenuTree',

    functional: true,

    render: (h, {props, data: $data}) => {
      return (
        <div class="essentials-view-tree">
          <el-tree {...props} {...{...$data, ref: $data.ref || 'tree'}} class="filter-tree mt-6"/>
        </div>
      )
    },
  }
</script>

<style lang="scss">
  .essentials-view-tree {
    .el-tree-node {
      @apply relative outline-none whitespace-no-wrap border-l border-dashed border-gray ml-6;
    }

    .el-tree-node__label {
      @apply pl-4;
    }

    .el-tree-node__expand-icon.is-leaf + .el-tree-node__label {
      @apply pl-10;
    }

    .el-tree-node__content > .el-tree-node__expand-icon {
      @apply p-2 absolute bg-white border border-solid border-gray;

      left: -7px;
    }

    .el-tree-node__content {
      padding-left: 0 !important;
    }

    .el-icon-caret-right:before {
      @apply absolute;

      left: -1px;
      top: -1px;
      content: "\E6D9";
    }

    .el-tree-node__expand-icon.is-leaf {
      @apply relative text-blue bg-white cursor-default z-10;

      border: none;
      padding: 0 !important;
      padding-left: 20px !important;
      left: 7px;

      &::before {
        @apply bg-white absolute;

        content: "\E785";
        border: none;
        left: 7px;
        top: -5px;
      }

      &::after {
        @apply absolute border-b border-dashed border-gray;

        content: '';
        width: 8px;
        height: 2px;
        left: -5px;
        top: -1px;
      }
    }

    .el-tree-node__expand-icon.expanded {
      transform: none;

      &::before {
        content: "\E6D8";
      }
    }

    .el-tree-node__content > .el-tree-node__expand-icon {
      padding: 5px;
    }
  }
</style>

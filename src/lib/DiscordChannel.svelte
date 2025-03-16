<script lang="ts">
  import hash from "./Hash.svg";

  const { name }: { name: string } = $props();
</script>

<div
  class="channelContainer"
  style="box-sizing: border-box; margin: 0; padding: 1px 0; overflow: visible; margin-left: 8px; color: oklab(0.686636 -0.00407365 -0.0149199);"
>
  <span
    class="channelName"
    style="cursor: pointer; box-sizing: border-box; padding: 6px 8px; display: flex; flex-direction: column; border-radius: 4px;"
  >
    <div style="display: flex;">
      <div style="vertical-align: baseline; margin-right: 6px; height: 20px;">
        <img src={hash} alt="#" style="width: 20px; height: 20px; " />
      </div>
      <div
        style="vertical-align: baseline; line-height: 20px; white-space: nowrap; overflow: hidden; flex: 1 1 auto; text-overflow: ellipsis; font-weight: 500;"
      >
        {name}
      </div>
    </div>
  </span>
</div>

<script lang="ts">
  import BotLabel from "./BotLabel.svelte";

  interface MemberData {
    name: string;
    iconUrl: string;
    isBot: boolean;
  }
  const { data }: { data: MemberData } = $props();
</script>

<div class="memberContainer" style="width: 224px; margin-left: 8px; color: oklab(0.686636 -0.00407365 -0.0149199);">
  <div class="memberName" style="cursor: pointer; border-radius: 4px; padding: 0 8px;">
    <div style="display: flex; align-items: center; height: 42px; z-index: 1; position: relative; width: fit-content; max-width: 100%; ">
      <div
        style="display: flex; align-items: center; justify-content: center; flex: 0 0 auto; width: 32px; height: 32px; margin-right: 12px;"
      >
        <div style="width: 32px; height: 32px; border-radius: 50%; overflow: hidden; display: grid;">
          <img
            src={data.iconUrl}
            alt="icon"
            style="display: block; object-fit: cover; pointer-events: none; width: 100%; height: 100%; grid-area: 1 / 1;"
          />
        </div>
      </div>
      <div style="white-space: nowrap; text-overflow: ellipsis; overflow: hidden; flex: 1 1 auto;">
        <div style="display: flex; justify-content: flex-start; align-items: center; font-weight: 500;">
          <div style="white-space: nowrap; text-overflow: ellipsis; overflow: hidden;">{data.name}</div>
          {#if data.isBot}<BotLabel />{/if}
        </div>
      </div>
    </div>
  </div>
</div>

<script lang="ts">
  import DiscordChannel from "./lib/DiscordChannel.svelte";
  import DiscordGuildMember from "./lib/DiscordGuildMember.svelte";
  import hash from "./lib/Hash.svg";

  let guilds = $state([...new Array(30).keys()].map(v => `guilds-${v.toString().padStart(3, "0")} ${"あ".repeat(30)}`));
  let guildName = $state("server-01 " + "あ".repeat(130));
  let channels = $state([...new Array(130).keys()].map(v => `channel-${v.toString().padStart(3, "0")} ${"あ".repeat(30)}`));
  let channelName = $state("channel-01 " + "あ".repeat(130));
  let messages = $state(
    [...new Array(30).keys()].map(v => ({
      content: "Message Content",
      author: {
        username: "message_author",
        global_name: "Message Author",
        avatar: null,
        bot: false
      },
      timestamp: `${new Date().toISOString()}`,
      isEdited: false,
      attachments: [],
      embeds: [],
      reactions: [],
      sticker_items: [],
      components: [],
      interaction_metadata: []
    }))
  );
  let members = $state(
    [...new Array(15).keys()].map(v => ({
      name: `member-${v.toString().padStart(3, "0")} ${"あ".repeat(30)}`,
      iconUrl: import.meta.env.BASE_URL + "/9855d7e3b9780976.png",
      isBot: v > 12
    }))
  );
</script>

<main style="height: 100%;">
  <div style="overflow: hidden; width: 100%; height: 100%; display: flex;">
    <div style="height: 100%; background: #1E1F22; display: flex; flex-direction: column; width: 72px;">
      <div class="scroll" style="box-sizing: border-box; overflow: hidden scroll; flex: 0 1 auto; padding-top: 12px; height: 100%;">
        {#each guilds as v}
          <div style="margin: 0 0 8px; display: flex; justify-content: center; width: 72px;">
            <div style="width: 48px; height: 48px;">
              <div data-name={v} style="width: 100%; height: 100%; background: #313338; border-radius: 50%;"></div>
            </div>
          </div>
        {/each}
      </div>
    </div>
    <div style="flex-grow: 1; height: 100%; display: flex; overflow: hidden;">
      <div style="width: 240px; flex: 0 0 auto; flex-direction: column; display: flex; background: #2B2D31">
        <div
          style="padding: 12px 16px; box-sizing: border-box; box-shadow: 0 2px 0 0 hsl(none 0% 0%/0.05),0 1.5px 0 0 hsl(none 0% 0%/0.05),0 1px 0 0 hsl(none 0% 0%/0.16);"
        >
          <div style="justify-content: space-between; height: 24px; display: flex; align-items: center;">
            <div
              style="margin: 0; padding: 0; font-size: 16px; line-height: 1.25; font-weight: 600; overflow: hidden; text-overflow: ellipsis; white-space: nowrap; margin-right: auto; color: oklab(0.89908 -0.00192907 -0.0048306);"
            >
              {guildName}
            </div>
          </div>
        </div>
        <div class="scroll" style="overflow: hidden scroll; padding-right: 8px; box-sizing: border-box; flex: 1 1 auto;">
          <div style="height: 12px;"></div>
          {#each channels as v}<DiscordChannel name={v} />{/each}
          <div style="height: 12px;"></div>
        </div>
      </div>
      <div style="height: 100svh; background: #313338; display: flex; flex-direction: column; overflow: hidden; flex: 1 1 auto; position">
        <div
          style="display: flex; flex-direction: column; box-shadow: rgba(0, 0, 0, 0.05) 0px 2px 0px 0px, rgba(0, 0, 0, 0.05) 0px 1.5px 0px 0px, rgba(0, 0, 0, 0.16) 0px 1px 0px 0px;"
        >
          <div
            style="box-sizing: border-box; display: flex; flex-direction: column; justify-content: center; width: 100%; flex: 0 0 auto; padding: 8px; height: 48px; font-size: 16px; line-height: 20px; cursor: default; flex: 0 0 auto;"
          >
            <div style="display: flex; flex: 1;">
              <div style="flex: 1 1 auto; display: flex; align-items: center; overflow: hidden;">
                <div style="height: 24px; width: auto; flex: 0 0 auto; margin: 0 8px;">
                  <img src={hash} alt="#" />
                </div>
                <div style="margin: 0 8px 0 0; flex: 0 0 auto;">
                  <div
                    style="justify-content: flex-start; overflow: hidden; white-space: nowrap; display: flex; align-items: center; font-size: 16px; line-height: 1.25; font-weight: 600; color: oklab(0.89908 -0.00192907 -0.0048306)"
                  >
                    {channelName}
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div
          style="height: calc(100svh - 48px); flex: 1 1 auto; display: flex; flex-direction: row; justify-content: stretch; align-items: stretch;"
        >
          <div style="display: flex; flex-direction: column; flex: 1 1 auto;">MESSAGES</div>
          <div style="height: 100%; display: flex; flex-direction: column; background: oklab(0.296709 -0.000735492 -0.00772537);">
            <div style="height: 100%; justify-content: center; width: 240px; display: flex;">
              <div class="scroll" style="box-sizing: border-box; overflow: hidden scroll; flex: 1 1 auto; width: 240px;">
                <div>
                  <div style="height: 12px;"></div>
                  {#each members as v}<DiscordGuildMember data={v} />{/each}
                  <div style="height: 12px;"></div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</main>

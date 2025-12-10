<!--
@component
### Hero component 
Renders a visual replica of the Immersive Template hero. 

#### Optional properties
- sectionLabel: string;
- headline: string;
- timestamp: string;
- heroImageUrl: string;
- heroImageCaption: string;
- heroImageAltText: string;
- dek: string;
- authorName: string;
- authorBioUrl: string;

#### Example
```svelte
<Hero
  sectionLabel = "Section label",
  headline = "Lorem ipsum dolor sit amet consectetur adipiscing elit",
  timestamp = "Dec. 1, 1977",
  heroImageUrl = "https://arc.stimg.co/startribunemedia/4SPNT7DI36ANT2SOB5N5EJAIJU.jpg",
  heroImageCaption = "",
  heroImageAltText = "",
  dek = "Lorem ipsum dolor sit amet consectetur adipiscing elit, fusce sociis at montes vitae tempor enim, venenatis tristique feugiat arcu dis ridiculus.",
  authorName = "Bryan Brussee",
  authorBioUrl = "https://www.startribune.com/bryan-brussee/8455834",
>
```
-->

<script>
  import Grid from "../Grid/Grid.svelte";
  import GridRow from "../Grid/_GridRow.svelte";
  import SectionLabel from "./_SectionLabel.svelte";
  import Headline from "./_Headline.svelte";
  import Timestamp from "./_Timestamp.svelte";
  import Image from "../Image/Image.svelte";
  import Dek from "./_Dek.svelte";
  import Byline from "./_Byline.svelte";

  /** @type {{sectionLabel?: string; headline?: string; timestamp?: string; heroImageUrl?: string; heroImageCaption?: string; heroImageAltText?: string; dek?: string; authorName?: string; authorBioUrl?: string;}} */
  let {
    sectionLabel = "",
    headline = "",
    timestamp = "",
    heroImageUrl = "",
    heroImageCaption = "",
    heroImageAltText = "",
    dek = "",
    authorName = "",
    authorBioUrl = "",
  } = $props();
</script>
<div class="herobox">
<Grid additionalClasses="">


    <GridRow variant={"fullBleed"}>
      <Image
        variant={"captionCentered"}
        src={"https://static.startribune.com/news/projects/all/2025-VIKES-ALLQC/png%20assets/test-hero.png"}

      />
    </GridRow>
  

  <GridRow
    additionalClasses="justify-self-center text-center w-[100vw]]"
  >
  <div class="flex flex-col gap-y-6 md:gap-y-8 text-center max-w-[800px] mx-auto leading-[1] pb-6 pt-4">
    <Headline>Meet the Minnesota Star Tribune’s Vikings All-Quarter-Century Team</Headline>
    <!-- <Timestamp>{timestamp}</Timestamp> -->
  </div>
    <div class="flex flex-col gap-y-5 md:justify-items-center md:items-center mx-auto max-w-[550px]">
      <Dek additionalClasses="text-[1.75rem]">
        Three longtime Vikings reporters picked 27 players and a head coach who were the best at their position from 2000 to 2025. 
      </Dek>
      <div class="flex items-center w-full gap-x-2 md:justify-center">
        <div class="flex flex-col gap-y-0.5 gap-x-1 md:flex-row">
          {#if authorName}
            <div class="flex">
              <Byline href={authorBioUrl}>By {authorName}</Byline>
            </div>
          {/if}

          <span class="text-text-secondary font-utility-label-reg-02 pb-14">
            The Minnesota Star Tribune
          </span>
        </div>
      </div>
    </div>



  </GridRow>
  <GridRow
  additionalClasses="justify-self-center text-center w-[60%] mx-auto pt-12 pb-0"
>
<hr style="border-width: 2px;border-color: #ffb601 !important;">
<div style="
margin: -45px auto auto auto;
max-width: 85px;
background: white;
padding: 10px;
"><img src="https://static.startribune.com/news/projects/all/2025-VIKES-ALLQC/png%20assets/purple%20logo1.png"></div>
</GridRow>
</Grid>
</div>
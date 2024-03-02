<script>
    import Scroller from "@sveltejs/svelte-scroller";
    import App from "./App.svelte" 
    let count, index, offset, progress;
    import * as d3 from 'd3';
    import 'd3-transition';
    import * as d3selection from 'd3-selection';

</script>


<Scroller
  top={0.0}
  bottom={1}
  threshold={0.5}
  bind:count
  bind:index
  bind:offset
  bind:progress
>
  <div class="background" slot="background">
    
    <div class="progress-bars">
        <p>current section: <strong>{index + 1}/{count}</strong></p>
        <progress value={count ? (index + 1) / count : 0} />
  
        <p>offset in current section</p>
        <progress value={offset || 0} />
  
        <p>total progress</p>
        <progress value={progress || 0} />
      </div>

      <!-- <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
        <circle cx = 12 cy = 12 r =12/>
        Add other SVG elements as needed
    </svg> -->
    

  </div>

  <div class="foreground" slot="foreground">
    <section>This is the first section.</section>
    <section>This is the second section.</section>
    <section>This is the third section.</section>
    <section>This is the fourth section.</section>
    <section>This is the fifth section.</section>
    <!-- Add More If needed -->
  </div>
</Scroller>



<style>

  .background {
      width: 100%;
      height: 100vh;
      position: relative;
      outline: green solid 3px;
  }
  
  .foreground {
    width: 50%;
    margin: 0 auto;
    height: auto;
    position: relative;
    outline: red solid 3px;
  }
  
  .progress-bars {
    position: absolute;
    background: rgba(170, 51, 120, 0.2) /*  40% opaque */;
    visibility: visible;
  }

  section {
    height: 80vh;
    background-color: rgba(0, 0, 0, 0.2);
    /* 20% opaque */
    /* color: white;*/
    outline: magenta solid 3px;
    text-align: center;
    max-width: 750px;
    /* adjust at will */
    color: black;
    padding: 1em;
    margin: 0 0 2em 0;
  }
</style>
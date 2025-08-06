
<!-- 24fps_animation.mp4 -->


<style>
  :root {
    background-color: #0a0a0a;
  }
</style>

<div>
  <style>
    @font-family
    {
      font-family: "NotoSans"
                   src: url("fonts/NotoSans-Regular.ttf")
    }

    body {
      background-color: #0a0a0a;
      color: tan;
    }

    div {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      padding-top: 50px;
    }

    .media_list {
      display: flex;
      flex-direction: row;
      align-items: center;
      justify-content: center;
      background-color: #0f0f0f;
      font-size: 0.8em
    }

    .button_list {
      display: flex;
      flex-direction: row;
      align-items: center;
      justify-content: center;
      background-color: #0f0f0f;
      font-size: 0.8em;
    }

    .button_simple {
      padding: 50px 50px;
      padding-left: 10px;
      padding-right: 10px;
    }

    .video_container {
      max-width: 400px;
      max-height: 400px;
      padding-left: 10px;
      padding-right: 10px;
    }

    h1 {
      font-size:  2em
    }

  </style>
  <h1 font-size=50> Mallchad </h1>

  <p margin=2px>
    general@mallchad.com
  </p>
  <p margin=50px>
    This are visual examples of some of the systems and rendering engines I've created
  </p>

  <div class="media_list">

    <div class="video_container">
      <p> This is a video player I made with raw C++ and SDL3. It has a fairly stable timekeeping system and has an artificial exposure slider for working with in VFX projects. The buttons are unlabelled currently but its about 1 line of code to add when appropriate"
      <video src="24fps_animation.mp4"
             autoplay=true
             loop=true
             controls=true/>
    </div>

    <div class="video_container">
      <p> A very simple responsive thing written using ncurses and C++ </p>
      <video src="profiler.mp4"
             autoplay=true
             loop=true
             controls=true/>
    </div>
    <div class="video_container">
      <video src="interactable.mp4"
             autoplay=true
             loop=true
             controls=true/>
    </div>

    <image src="spinny_metallic_and_specular.gif">

      <!-- exposure_animation.mp4 -->
      <!-- favicon.svg -->
      <!-- interactable.mp4 -->
      <!-- profiler.mp4 -->
      <!-- spinny_metallic_and_specular.gif -->
  </div>
  <div class="button_list">

    <a href="https://mallchad.com/notes"
       class= "bg-transparent hover:bg-tan text-tan; font-semibold hover:text-white py-2 px-4 border border-tan  hover:rounded-full rounded">
      Personal Notes
    </a>

    <a href="https://mallchad.com/github"
       class= "bg-transparent hover:bg-tan text-tan font-semibold hover:text-white py-2 px-4 border border-tan  hover:rounded-full rounded">
      GitHub
    </a>

    <a href="https://www.youtube.com/@Mallchad/videos"
       class= "bg-transparent hover:bg-tan text-tan font-semibold hover:text-white py-2 px-4 border border-tan rounded hover:rounded-full">
      YouTube
    </a>

  </div>
</div>



<!-- <div> -->
<!-- <style> -->
<!--   h1 { left: 50; } -->
<!-- </style> -->
<!--   <h1 font-size=50> Mallchad2 </h1> -->
<!-- </div> -->

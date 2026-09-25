
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
      padding-top: 20px;
    }
    
    .media_list {
      display: grid;
      grid-auto-flow: row;
      /* grid-template-columns: repeat(5, 1fr); */
      /* grid-column-gap: 10px; */
      align-items: center;
      justify-content: center;
      background-color: #00000000;
      font-size: 0.8em;
      width: 95%;
    }

    .button_simple {
      width: 20vw;
      padding: 50px 50px;
      padding-top: 10;
    }

    .video_container {
      padding-left: 1vw;
      padding-right: 1vw;
    }
    .a {
      padding-top: 100px;
    }

    h1 {
      font-size:  2em
    }

    @media screen and (width <=720px) {
      
      /* body { */
        /* width: 95%; */
      /* } */

      .media_list {
        grid-template-columns: 100%;
      }

      .video_container {
        /* width: 100%; */
        /* height: 100%; */
      }

      .video_box {
        width: 100%;
        height 100%;
        object-fit: cover;
        padding-left: 5vw;
        
      }
    }

    @media screen and (width > 720px) and (width < 1080px) {

      body {
        width: 95vw;
      }

      .media_list {
        grid-template-columns: 50% 50%;
      }

      .video_box {
        width: 100;
      }

      .video_box {
        width: 100%;
        padding-left: 5vw;
        padding-right: 5vw;
      }
    }

    @media screen and (width >=1080px) {

      body {
        width: 95vw;
      }

      .media_list {
        width: 80vw;
        grid-template-columns: 1fr 1fr 1fr 1fr 1fr;
      }

      .media_container {
        width: 100vw;
      }
    }

    /* @media (max-width: 1250px) */
    /* { */
    /* } */

    .button_list {
      display: grid;
      grid-template-columns: auto auto auto auto;
      justify-content: center;
      background-color: #0f0f0f;
      font-size: 0.8em;
      gap: 5px;
      white-space: nowrap;
    }

  </style>
  <h1 font-size=50> Mallchad </h1>

  <p>
    general@mallchad.com
  </p>
  <p>
    This are visual examples of some of the systems and rendering engines I've created
  </p>

  <div class="media_list">

    <div class="video_container">
      <video class="video_box" src="24fps_animation.mp4"
             autoplay=true
             loop=true
             controls=true>
      </video>
      <p> This is a video player I made with raw C++ and SDL3. It has a fairly stable timekeeping system and has an artificial exposure slider for working with in VFX projects. The buttons are unlabelled currently but its about 1 line of code to add when appropriate. <p>
    </div>

    <div class="video_container">
      <video class="video_box" src="profiler.mp4"
             autoplay=true
             loop=true
             controls=true/>
          <p> A very simple responsive thing written using ncurses and C++ </p>
    </div>
    <div class="video_container">
      <video class="video_box" src="interactable.mp4"
             autoplay=true
             loop=true
             controls=true/>
      <p> Making custom UI elements with debug draw overlay <p>
    </div>

    <div class="video_container">
      <image class="video_box" src="spinny_metallic_and_specular.gif">
        <p> Phong material renderer from scratch in C++, using OpenGL, X11/Xlib and Linux.
    </div>

      <!-- exposure_animation.mp4 -->
      <!-- favicon.svg -->
      <!-- interactable.mp4 -->
      <!-- profiler.mp4 -->
      <!-- spinny_metallic_and_specular.gif -->
  </div>
  <div class="button_list">
    <a href="/simple_animations"
       class= "bg-transparent font-semibold hover:text-white py-2 px-4 border border-tan rounded hover:rounded-full">
      Solar System Toy
      </a>
    <a href="https://notes-vu8.pages.dev/"
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

  <div class="button_list">
      <a href="/"
       class= "bg-transparent font-semibold hover:text-white py-2 px-4 border border-tan rounded hover:rounded-full">
        Home </a>

      <a href="/dev"
         class= "bg-transparent hover:bg-tan text-tan font-semibold hover:text-white py-2 px-4 border border-tan rounded hover:rounded-full">
        Home (Experimental) </a>

  </div>


</div>



<!-- <div> -->
<!-- <style> -->
<!--   h1 { left: 50; } -->
<!-- </style> -->
<!--   <h1 font-size=50> Mallchad2 </h1> -->
<!-- </div> -->

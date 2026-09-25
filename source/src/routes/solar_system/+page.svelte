<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Test Page</title>
</head>

<style>

  /* Need to apply default colours here or previous svelte routes break this page's theme */
:root {
  /* Variables */
  --color-foreground: tan;
  --color-background: #0f0f0f;
  --color-hover: #ffffff;
  /* Universal Ultra high contrast colors*/
  /* --color-foreground: #ffffff; */
  /* --color-background: #000000; */
  /* 
     Color Specific AI suggested perceptual contras
   | Observer Type | Primary Constraint | Optimization Strategy | The "Ideal" Salient Combo |
   | :--- | :--- | :--- | :--- |
   | **Normal Vision** | Visual Fatigue | Luminance/Neutrality | White/Black or Dark Gray/Light Gray |
   | **Achromatopsia** | Low Luminance Sensitivity | **Luminance Peak ($\lambda \approx 555\text{nm}$)**    | **`#E6FFD2` on `#050800`** |
   | **Protanopia** (Red-Blind) | Missing Long-Wave Signal | **Blue-Yellow Opponent Gap** | **`#F0FF00` on `#000520`** |
| **Deuteranopia** (Green-Blind) | Missing Medium-Wave Signal | **Blue-Red Opponent Gap** | **`#FFD700` on `#080010`** |*/
  /* Archromatopsia Test */
  /* --color-foreground: #e6ffd2; */
  /* --color-background: #050800; */
  /* Protanopia */
  /* --color-foreground: #f0ff00; */
  /* --color-background: #000520; */

  /* --color-foreground: #ffd700; */
  /* --color-background: #080010; */

  

    color: var(--color-foreground);
    background-color: var(--color-background);

}
body {
    /* <!-- display: flex; --> */
    /* <!-- justify-content: center; --> */
    align-items: center;
    height: 100vh;
    margin: 0;
    overflow-y: auto; /* This restores vertical scrolling */
    overflow-x: hidden; /* This prevents annoying horizontal side-scrolling */
}

svg {
  /* transform: translateZ(0); /\* Forces GPU acceleration *\/ */
  /* shape-rendering: geometricPrecision; */
  /* shape-rendering: optimizeSpeed */
}

button {
    border-radius: 5px;
    border: 2px solid; /* Soft Tan Border */
    background-color: transparent;

    padding: 10px 20px;
    cursor: pointer;
    font-family: sans-serif; /* Set a font family for consistency */
}
button:hover {
  color: var(--color-hover);
  border-radius: 1em;
}

.button_list {
  display: grid;
  grid-template-columns: auto auto auto auto;
  justify-content: center;
  font-size: 0.8em;
  gap: 5px;
  white-space: nowrap;
}

.slider-input {
    appearance: none;
    -webkit-appearance: none; /* Remove default browser styling */
    outline: none; /* Remove outline */

    /* Ensure the slider itself uses the theme colors */
    <!-- background-color: none; -->
                                 color: var(--color-foreground);
    /* You may need to override default browser styling for the track/thumb */
    cursor: pointer;
    background: none;
    border: 2px solid;
    border-radius: 10px;
    opacity: 0.7;

}

.slider-input::-webkit-slider-thumb {
  -webkit-appearance: none; /* Override default look */
  appearance: none;
  width: 15px; /* Set a specific slider handle width */
  height: 15px; /* Slider handle height */
  border-radius: 40px;
    border: 3px solid;
    background: inherit-foreground;
  cursor: pointer; /* Cursor on hover */
}

.slider-input::-webkit-slider-thumb:hover {
  background: none;
  transition: background-color 0.1s ease-in-out;
}

</style>

<body >

  <p >Solar System Toy</p>

    <!-- New Buttons -->
    <button id="startRender" class = "soft-tan-button">Start Render</button>
    <button id="pauseRender">Pause Render</button>
    <button id="saveRender">Save Render</button>

<!-- Add this slider somewhere in your body -->
<div style="display: flex; flex-direction: column; gap 10px; width: fit-content">
  <label id="scale_label" for="scale_slider"> System Scale Division (base 1 pixel/meter):</label>
    <input type="range" id="scale_slider" class="slider-input" min="1" max="100" value="1">

    <label id="timestep_label" for="timestep_slider"> Time Acceleration </label>
    <input type="range" id="timestep_slider" class="slider-input" min="1" max="1000" value="1">

</div>
    <div id="debug_box"> </div>

    <svg id="solar_system" width="1000" height="1000" xmlns="http://www.w3.org/2000/svg">
      <circle id="orbit_mercury" cx="500" cy="500" r="1838.6875" stroke="var(--color-foreground)" stroke-width="0.2em" fill="none" />
      <circle id="orbit_earth" cx="500" cy="500" r="1838.6875" stroke="var(--color-foreground)" stroke-width="0.2em" fill="none" />
      <circle id="body_sun" cx="500" cy="500" r="8.69625" stroke="var(--color-foreground)" fill="white" />
      <circle id="body_earth" cx="500" cy="500" r="3" fill="black" stroke="var(--color-foreground)" stroke-width="2" />

    </svg>


    <div class="button_list">
      <a href="/solar_system"
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


    <script>
      var tau = 6.28
      var earth_angle = 0;
      // base_position is abitrary stat point, will have to be added to argument or periapsis
      var base_position = 0.0
      // Scalar to modify time scale using user inpput
      var timestep_value = 1.0;
      // Time scale in seconds,  (60 * 60 * 24) -> 1s = 1 day
      var day_seconds = (60 * 60 * 24)
      var time_scale_default_s = (60 * 60 * 24)
      var time_scale = time_scale_default_s

      var sim_time = 0
      var sim_time_base = 0
      var dom_time_base = 0;
      var dom_time_s = 0

      var is_running = true;
      var animation_frame = null;
      // --- JavaScript Functions (Empty functions for no popup) ---

      document.getElementById('startRender').addEventListener('click', function() {
          console.log("Start render" )
        is_running = true;
      });

      document.getElementById('pauseRender').addEventListener('click', function() {
          console.log( "Stop render" )
      is_running = false;
      });

      document.getElementById('saveRender').addEventListener('click', function() {
          console.log( "save render" )
      
      });

      var timestep_slider = document.getElementById('timestep_slider')
      var timestep_label = document.getElementById('timestep_label')
      var debug_box = document.getElementById('debug_box')
      var debug_string = ""
      var debug_enabled = false


      function update_solar_system( dom_time_ms )
      {
        dom_time_s = (dom_time_ms / 1000)
        const scale_value = parseFloat(scale_slider.value);
        const sim_time_advance_part = (((dom_time_s - dom_time_base) * time_scale))
        sim_time = sim_time_base + sim_time_advance_part
        debug_seconds = sim_time_advance_part / day_seconds
        debug_string += `${debug_seconds}\n`
        
          // Temporary reinstate
        // sim_time = dom_time_s * time_scale
        console.log( "scale value", scale_value )

        const solar_system = document.getElementById('solar_system')
        // meters to pixels
        const system_scale_base = 800e6
        const system_scale = system_scale_base * scale_value
        const orbit_earth_radius = 147.095e9 / system_scale
        const sun_radius = 695700000 / system_scale
        const orbit_mercury_radius = 28954615515 / system_scale

        const orbit_mercury = document.getElementById('orbit_mercury');
        orbit_mercury.setAttribute( "r", orbit_mercury_radius )
        const orbit_earth = document.getElementById('orbit_earth');
        orbit_earth.setAttribute( "r", orbit_earth_radius )
        const body_sun = document.getElementById('body_sun');
        body_sun.setAttribute( "r", sun_radius )

        // --- ORBITAL MOVEMENT LOGIC ---
        if (is_running) {
          /* 
             Let the timestamp be expressed as the time elapsed since the rendering epoch.
             The position of a body is given by the `time elapsed * angular velocity`
             Let the angular velocity be `1 turn / orbital period in seconds`.
             Let the base time acceleration be `1 day per second` calculated as `1s * (60 * 60 * 24)`
           
             Let timestep_value be an abitrary scaling factor applied on time
             acceleration timestep * scaling factor 
          
             
          */
          
          // orbital period = 1 turn / days
          orbital_period = 365.25 * day_seconds
          const angular_velocity = (tau / orbital_period)
          earth_angle = base_position + 1 * angular_velocity * (sim_time % orbital_period);

          // Calculate X and Y using trigonometry:
          // x = center_x + radius * cos(angle)
          // y = center_y + radius * sin(angle)
          const earth_x = 500 + orbit_earth_radius * Math.cos(earth_angle);
          const earth_y = 500 + orbit_earth_radius * Math.sin(earth_angle);

          // Update Earth's position
          const earth_element = document.getElementById('body_earth');
          earth_element.setAttribute("cx", earth_x);
          earth_element.setAttribute("cy", earth_y);
        }

        const days_elapsed = Math.ceil(dom_time_s * time_scale * (1/day_seconds))
        debug_string += `days elapsed: ${days_elapsed}`
        
        if (debug_enabled)
        {
          debug_box.innerText = debug_string
        }
        debug_string = ""
        animation_frame = requestAnimationFrame( update_solar_system );
      }

      function update_base_orbits()
      {
        timestep_value = parseFloat( timestep_slider.value );
        // update time scale to base * slider value
        time_scale = (time_scale_default_s * timestep_value)
        sim_time_base = sim_time
        dom_time_base = dom_time_s
        
        // Stamp out calculated angle permanantly to provide new setpoint to
        // keeping timescale modification smooth
        current_position = earth_angle % tau

        days = time_scale / day_seconds
        timestep_label.innerText = `Time Acceleration: ${days} days/s`
        console.log( `Time Acceleration: ${days} day/s` )
        
      }
      
      // Register listeners
      timestep_slider.addEventListener( 'input', update_base_orbits );
      // run listeners that need it once first so it can update
      update_base_orbits()

      requestAnimationFrame( update_solar_system );
      
      // update_solar_system()
      // cancelAnimationFrame(animation_frame); 

    </script>
</body>


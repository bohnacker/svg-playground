<script>
  function calculatePosition(xi, yi) {
    // xi (eine Zahl von 0 bis 10) wird in Pixel umgerechnet
    let x = xi * 100;
    // yi (eine Zahl von 0 bis 9) is vor allem für die vertikale Positionierung zuständig,
    // wird aber auch für die horizontale Versetzung jeder zweiten Reihe gebraucht.
    // Jede zweite Reihe um 50 Pixel nach rechts versetzen, wenn yi ungerade ist
    if (yi % 2 === 1) {
      x = x + 50;
    }
    // yi benutzen, um die vertikale Positionierung zu berechnen
    const y = yi * 90;
    // Rückgabe eines Strings, der die Koordinaten im Format "x y" enthält. Dieser kann direkt im translate() verwendet werden.
    return x + " " + y;
  }
</script>

<svg viewbox="0 0 1000 1000" xmlns="http://www.w3.org/2000/svg" stroke-linejoin="round" stroke-linecap="round" stroke-width="1" fill="none" stroke="#000000">
    <rect x="0" y="0" width="1000" height="1000" fill="#000" stroke="none"/>

    <!-- Variante mit Funktionsaufruf -->
    {#each Array(12) as _, yi}
      {#each Array(11) as _, xi}
        <polygon transform="translate({calculatePosition(xi, yi)})" points="0 -60, 50 -30, 50 30, 0 60, -50 30, -50 -30" stroke="#ffffff99"/> 
      {/each}
    {/each}

    <!-- Variante mit Modulo -->
    <!-- {#each Array(10) as _, j}
      {#each Array(10) as _, i}
        <polygon transform="translate({50 + (j%2 * 50) +i*100} {100+j*90})" points="0 -60, 50 -30, 50 30, 0 60, -50 30, -50 -30" /> 
      {/each}
    {/each} -->

    <!-- Variante mit Doppelelement -->
    <!-- {#each Array(5) as _, j}    
      {#each Array(10) as _, i}
        <polygon transform="translate({50+i*100} {100+j*180})" points="0 -60, 50 -30, 50 30, 0 60, -50 30, -50 -30" /> 
        <polygon transform="translate({100+i*100} {190+j*180})" points="0 -60, 50 -30, 50 30, 0 60, -50 30, -50 -30" /> 
      {/each}
    {/each} -->

    <!-- "Von Hand" positionierte Sechsecke -->
    <!-- 
    <polygon transform="translate(50 100)" points="0 -60, 50 -30, 50 30, 0 60, -50 30, -50 -30" />
    <polygon transform="translate(150 100)" points="0 -60, 50 -30, 50 30, 0 60, -50 30, -50 -30" />
    <polygon transform="translate(250 100)" points="0 -60, 50 -30, 50 30, 0 60, -50 30, -50 -30" />

    <polygon transform="translate(100 190)" points="0 -60, 50 -30, 50 30, 0 60, -50 30, -50 -30" />
    <polygon transform="translate(200 190)" points="0 -60, 50 -30, 50 30, 0 60, -50 30, -50 -30" />
    <polygon transform="translate(300 190)" points="0 -60, 50 -30, 50 30, 0 60, -50 30, -50 -30" /> -->


    <!-- Typische Reihenfolge der Transformationen -->
    <!-- <polygon transform="translate(50 100) rotate(20) scale(0.5 1)" points="0 -60, 50 -30, 50 30, 0 60, -50 30, -50 -30" /> -->

    <!-- Positionierung durch Koordinaten der einzelnen Punkte -->
    <!-- <polygon points="100 20, 180 60, 180 150, 100 190, 20 150, 20 60" />
    <polygon points="260 20, 340 60, 340 150, 260 190, 180 150, 180 60" /> -->

    <!-- SVG Grafik-Elemente -->
    <!-- <g stroke="#000000" stroke-width="2">
      <circle cx="100" cy="100" r="80" fill="#ffcc00"  />
      <ellipse cx="300" cy="100" rx="80" ry="40" fill="#00ccff"  />
      <rect x="450" y="20" width="160" height="160" fill="#cc00ff"  />
      <polygon points="700 20, 780 180, 620 180" fill="#00ff00" stroke-width="20" />
      <polyline points="870 20, 950 180, 800 180" fill="#66aaff" stroke="#ff0000" />
      <line x1="100" y1="300" x2="300" y2="400" stroke="#0000ff" stroke-width="40"/>
      <path d="M450 300 C 500 200, 600 400, 700 300 S 800 400, 850 300" fill="none" stroke="#ff00ff" stroke-width="4"/>
  </g> -->



</svg>


<style>
  /* make sure the SVG does not make the container larger than intended */
  svg {
    max-width: 100%;
    max-height: 100%;
    display: block;
    padding: 20px;
    margin: 0;
    box-sizing: border-box;
  }
</style>

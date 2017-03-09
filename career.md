---
title:        "Career"
permalink: /career/
---

<div class="container">
    <div class="row">
        <div class="col-lg-12 text-center" id="i18_skills">
            <div class="navy-line"></div>
            <h1><span data-i18n="skills.my_skills">Skills</span></h1>
        </div>
    </div>
    <div class="row features-block">
    <h1>{{ site.author }}</h1>
        {% for skills in site.skills %}
            {% assign loopindex = forloop.index | modulo: 2 %}
          <div class="wow zoomIn col-lg-5 col-lg-offset-1">
              <canvas id="{{ skills.id }}" height="500" width="500"></canvas>
          </div>
          <div class="col-lg-1"></div>
          <script>
          var ctx = document.getElementById("{{ skills.id }}");
          var data = {
              labels: "{{ skills.aspects }}".split(","),
              datasets: [{
                  label: "{{ skills.label }}",
                  backgroundColor: "rgba(179,181,198,0.2)",
                  borderColor: "#3385FF",
                  pointBackgroundColor: "#3385FF",
                  pointBorderColor: "#fff",
                  pointHoverBackgroundColor: "#3385FF",
                  pointHoverBorderColor: "#3385FF",
                  data: [{{ skills.percentage }}]
                  }]
          };
          var myRadarChart = new Chart(ctx, {
              type: 'radar',
              data: data,
              options: {
                  scale: {
                      responsive: true,
                      ticks: {min: 0, max: 100},
                      lineArc: false,
                      pointLabels: {fontSize: 14},
                  },
                  legend: {display: false},
              }
          });
          </script>
      {% endfor %}
  </div>
</div>

<template>
  <div>

    <nav class="navbar navbar-expand-md navbar-light bg-light  py-3 box-shadow">


      <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent"
        aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Abrir Navegação">
        <span class="navbar-toggler-icon"></span>
      </button>

      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav ml-auto">

          <li class="nav-item">
            <a class="btn btn-outline-primary" href="inscricao.html">Register</a>
          </li>
        </ul>
      </div>
    </nav>


    <!-- Main -->
    <br />

    <div class="container ">
      <img class="img-fluid" src='../assets/tata-resized.jpg'>

      <p class="text-center tata-nome">Forest Fire Alert System</p>
    </div>

    <div class="container">
      <div class="row">
        <!-- Material form contact -->

        <div class="col-md-6 col-sm-12 pb-3">
          <div class="card bg-light">
            <h4 class="card-header bg-light text-danger text-center py-4">
              <strong>REPORT FIRE</strong>
            </h4>
            <form class="col-12 py-3" action="">
              <!-- inputs -->
              <div class="form-group">
                <label for="inputTelefone">Telephone</label>
                <input type="text" class="form-control" id="inputTelefone" placeholder="Cell Phone">
              </div>

              <div class="form-group">
                <label for="">Location</label>
                <input type="text" class="form-control location-address" id="inputCPF" placeholder="Fire Location">
                <!-- <a class="btn icon-btn btn-success" href="#"><i class="material-icons bota-add-location">add_location</i>Choose</a> -->
                <div class="input-group mb-3">
                  <input type="text" class="form-control" placeholder="e.g, City, State, Country"
                    aria-label="Recipiente para nickname" aria-describedby="basic-addon2">
                  <div id="botao-geolocalizacao" class="input-group-append">
                    <span class="input-group-text" id="basic-addon2"><i
                        class="large material-icons botao-add-location">add_location</i></span>
                  </div>
                </div>
              </div>

              <div class="form-group">
                <label class="mb-3" for=""><b>Estimate Fire Severity:</b></label>

                <div class="form-row mx-0">
                  <!-- baixo -->
                  <div class="form-check form-check-inline">
                    <input class="form-check-input" type="radio" name="inlineRadioOptions" id="inlineRadio1"
                      value="option1" checked>
                    <label class="form-check-label" for="inlineRadio1">Small</label>
                  </div>
                  <!-- moderado -->
                  <div class="form-check form-check-inline">
                    <input class="form-check-input" type="radio" name="inlineRadioOptions" id="inlineRadio2"
                      value="option2">
                    <label class="form-check-label" for="inlineRadio2">Medium</label>
                  </div>

                  <!-- alto -->
                  <div class="form-check form-check-inline">
                    <input class="form-check-input" type="radio" name="inlineRadioOptions" id="inlineRadio3"
                      value="option3">
                    <label class="form-check-label" for="inlineRadio3">High</label>
                  </div>

                </div>
              </div>

              <!-- <div class="imagePreview"></div> -->

              <button class="btn btn-danger btn-rounded btn-block z-depth-0 my-4 waves-effect"
                type="submit">SEND</button>

            </form>

          </div>
        </div>
        <!-- Material form contact -->
        <div class="col-md-6 col-sm-12 pb-3">

        <div class="card bg-light" style="display: -webkit-box !important">
          
          <h4 class="card-header bg-light text-danger text-center py-4">
            <strong>LIVE FIRES</strong>
          </h4>
          <div class="google-map" :id="mapName"  style="height: 550px !important;"></div>
        </div>
        </div>

      </div>



    </div>

      <footer class="text-white pt-3">
        <div class="bg-danger text-center py-2">
          <p class="mb-0">TATA © 2019. All rights reserved.</p>
        </div>
      </footer>

  </div>

</template>

<script>
  export default {
    name: 'google-map',
    props: ['name'],
    data: function () {
      return {
        mapName: this.name + "-map",
        markerCoordinates: [{
          latitude: 51.501527,
          longitude: -0.1921837
        }, {
          latitude: 51.505874,
          longitude: -0.1838486
        }, {
          latitude: 51.4998973,
          longitude: -0.202432
        }]
      }
    },
    mounted: function () {
      const google = window.google;
      //const bounds = new google.maps.LatLngBounds();
      const element = document.getElementById(this.mapName);
      //const mapCentre = this.markerCoordinates[0];
      const options = {
        zoom: 4, //Não mexe mais. Esse zoom tá ótimo
        center: new google.maps.LatLng(-15.780076, -53.868602),
        streetViewControl: false,
      }
      const map = new google.maps.Map(element, options);

      // let src_data = '../assets/modis.kml';

      //Amazon
      let marker = new google.maps.Marker({
        position: new google.maps.LatLng(-8.544491, -66.200939),
        title: "Incendio de Proporções Astronomicas",
      });


      let marker2 = new google.maps.Marker({
        position: new google.maps.LatLng(-11.935343, -53.542230),
        title: "Incendio de Proporções Astronomicas",
      });

      let marker3 = new google.maps.Marker({
        position: new google.maps.LatLng(-8.027305, -58.181693),
        title: "Incendio de Proporções Astronomicas",
      });


      let contentString = '<div id="content">' +
        '<div id="siteNotice">' +
        '</div>' +
        '<h1 id="firstHeading" class="firstHeading">Amazon Forest</h1>' +
        '<div class="internoPin">' +
        '<label for="disabledTextInput">Location: -8.544491, -66.200939</label>' +
        '<label for="disabledTextInput">Confidence: 99%</label>' +
        '<label for="disabledTextInput">Severity: <b>HIGH</b></label>' +
        '</div>' +
        '</div>' +
        '</div>';

      let contentString2 = '<div id="content">' +
        '<div id="siteNotice">' +
        '</div>' +
        '<h1 id="firstHeading" class="firstHeading">Amazon Forest</h1>' +
        '<div class="internoPin">' +
        '<label for="disabledTextInput">Location: -11.935343,-53.542230</label>' +
        '<label for="disabledTextInput">Confidence: 84%</label>' +
        '<label for="disabledTextInput">Severity: <b>LOW</b></label>' +
        '</div>' +
        '</div>' +
        '</div>';

      let contentString3 = '<div id="content">' +
        '<div id="siteNotice">' +
        '</div>' +
        '<h1 id="firstHeading" class="firstHeading">Parque Nacional do Junqueira</h1>' +
        '<div class="internoPin">' +
        '<label for="disabledTextInput">Location: -8.027305,-58.181693</label>' +
        '<label for="disabledTextInput">Confidence: 75%</label>' +
        '<label for="disabledTextInput">Severity: <b>MEDIUM</b></label>' +
        '</div>' +
        '</div>' +
        '</div>';

      var infowindow = new google.maps.InfoWindow({
        content: contentString
      });

      var infowindow2 = new google.maps.InfoWindow({
        content: contentString2
      });

      var infowindow3 = new google.maps.InfoWindow({
        content: contentString3
      });

      marker.addListener('click', function () {
        infowindow.open(map, marker);
      });

      marker2.addListener('click', function () {
        infowindow2.open(map, marker2);
      });

      marker3.addListener('click', function () {
        infowindow3.open(map, marker3);
      });

      marker.setMap(map);
      marker2.setMap(map);
      marker3.setMap(map);

      // var kmlLayer = new google.maps.KmlLayer(src_data, {
      //       suppressInfoWindows: true,
      //       preserveViewport: false,
      //       map: map
      //     });

      // kmlLayer.addListener('click', function(event) {
      //       var content = event.featureData.infoWindowHtml;
      //       var testimonial = document.getElementById('capture');
      //       testimonial.innerHTML = content;
      //     });

      // kmlLayer.setMap(map);

    }
  };
</script>
<style>
  .google-map {
    width: auto;
    height: 550px;
    margin: 0 auto;
    background: gray;
  }

  .firstHeading .h1,
  h1 {
    font-size: 19px;
  }

  /* customizaçao classes default */
  label {
    display: flex !important;
  }

  .nav-link {
    display: flex !important;
  }

  .btn {
    display: table !important;
  }

  /* mapa */

  h1#firstHeading {
    font-size: 1.04rem !important;
  }

  .firstHeading .label {
    font-size: 1.45rem !important;
  }

  h1.texto-principal {
    color: #324A71 !important;
  }

  h1.texto-principal::after {
    content: "";
    display: block;
    width: 60px;
    height: 3px;
    background: #3d9550;
    margin: 8px auto;
  }

  .location-address {
    display: none !important;
  }

  .btn-glyphicon {
    padding: 8px;
    background: #ffffff;
    margin-right: 4px;
  }

  .icon-btn {
    padding: 1px 15px 3px 2px;
    border-radius: 50px;
  }

  .botao-add-location {
    color: white;
  }

  .add-location {
    background-color: #000000;
  }

  .border-card {
    border-radius: 20px;
  }

  .tata-nome {
    color: #163B00;
    font-weight: bold;
    font-size: 25px;
  }

  #basic-addon2 {
    background-color: #dc3545;
  }

  .img-fluid {
    height: 120px !important;
  }

  .text-danger2 {
    color: #dc3545;
  }

  .navbar {
    height: 64px;
    box-shadow: 0 2px 4px 0 rgba(0, 0, 0, .05), 0 4px 8px 0 rgba(0, 0, 0, .05);
  }

  .imagePreview {
    width: 100%;
    height: 50px !important;
    background-position: center center;
    background: url(http://cliquecities.com/assets/no-image-e3699ae23f866f6cbdf8ba2443ee5c4e.jpg);
    background-color: #fff;
    background-size: cover;
    background-repeat: no-repeat;
    display: inline-block;
    box-shadow: 0px -3px 6px 2px rgba(0, 0, 0, 0.2);
  }

  /* Somente botao upload da foto */
</style>
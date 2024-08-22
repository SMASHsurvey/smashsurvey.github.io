---
layout: page
title: SMASH CMD maps (stars)
---


<head>
    <title>SMASH Interactive Map</title>
</head>

Click on the map regions to show the color-magnitude diagram (CMD) for each of them.

<body>
    <style>
        #hess {
            display: none;
            position: absolute;
            width: 400px;
            border: solid 5px black;
        };
    </style>
    <div id="container">
        <img id="map" src="../assets/smash_map_calibration_v6.jpg"><br>
        <img id="hess" src="../assets/allv6/Field11_hess_finalv6_stars2.jpg">
        <div id="pixel"></div>
    </div>

<script>
    function get_lon_lat(pageX, pageY) {
        minX = 88;
        maxX = 954;
        minY = 15;
        maxY = 614;

        min_lon = 80;
        max_lon = -35;
        min_lat = 40;
        max_lat = -40;

        click_lon = min_lon + (pageX - minX)*(max_lon - min_lon)/(maxX - minX); 
        click_lat = min_lat + (pageY - minY)*(max_lat - min_lat)/(maxY - minY);
        return [click_lon, click_lat];

    };

    var click_centers = [
[-19.6, -13.8, "../assets/allv6/Field1_hess_finalv6_stars2.jpg"],
[-12.1, -15.0, "../assets/allv6/Field2_hess_finalv6_stars2.jpg"],
[-15.1, -13.9, "../assets/allv6/Field3_hess_finalv6_stars2.jpg"],
[-16.7, -13.4, "../assets/allv6/Field4_hess_finalv6_stars2.jpg"],
[-16.9, -11.7, "../assets/allv6/Field5_hess_finalv6_stars2.jpg"],
[-15.4, -12.3, "../assets/allv6/Field6_hess_finalv6_stars2.jpg"],
[-13.9, -12.8, "../assets/allv6/Field7_hess_finalv6_stars2.jpg"],
[-6.4, -15.3, "../assets/allv6/Field8_hess_finalv6_stars2.jpg"],
[-17.2, -10.1, "../assets/allv6/Field9_hess_finalv6_stars2.jpg"],
[-15.7, -10.6, "../assets/allv6/Field10_hess_finalv6_stars2.jpg"],
[-14.1, -11.2, "../assets/allv6/Field11_hess_finalv6_stars2.jpg"],
[-12.6, -11.7, "../assets/allv6/Field12_hess_finalv6_stars2.jpg"],
[-9.6, -12.6, "../assets/allv6/Field13_hess_finalv6_stars2.jpg"],
[-16.0, -9.0, "../assets/allv6/Field14_hess_finalv6_stars2.jpg"],
[-14.5, -9.5, "../assets/allv6/Field15_hess_finalv6_stars2.jpg"],
[-12.9, -10.0, "../assets/allv6/Field16_hess_finalv6_stars2.jpg"],
[-3.7, -14.4, "../assets/allv6/Field17_hess_finalv6_stars2.jpg"],
[-12.2, -7.1, "../assets/allv6/Field18_hess_finalv6_stars2.jpg"],
[-8.8, -9.7, "../assets/allv6/Field19_hess_finalv6_stars2.jpg"],
[-16.2, -2.9, "../assets/allv6/Field20_hess_finalv6_stars2.jpg"],
[-13.1, -3.8, "../assets/allv6/Field21_hess_finalv6_stars2.jpg"],
[-9.6, -6.3, "../assets/allv6/Field22_hess_finalv6_stars2.jpg"],
[-11.7, 0.4, "../assets/allv6/Field23_hess_finalv6_stars2.jpg"],
[-9.1, -3.3, "../assets/allv6/Field24_hess_finalv6_stars2.jpg"],
[-4.7, -9.3, "../assets/allv6/Field25_hess_finalv6_stars2.jpg"],
[-5.6, -5.8, "../assets/allv6/Field26_hess_finalv6_stars2.jpg"],
[-5.7, -1.1, "../assets/allv6/Field27_hess_finalv6_stars2.jpg"],
[-6.9, 2.3, "../assets/allv6/Field28_hess_finalv6_stars2.jpg"],
[-2.2, -3.5, "../assets/allv6/Field29_hess_finalv6_stars2.jpg"],
[-3.1, 3.0, "../assets/allv6/Field30_hess_finalv6_stars2.jpg"],
[-0.7, -8.7, "../assets/allv6/Field31_hess_finalv6_stars2.jpg"],
[-2.4, 1.3, "../assets/allv6/Field32_hess_finalv6_stars2.jpg"],
[0.0, -12.2, "../assets/allv6/Field33_hess_finalv6_stars2.jpg"],
[-1.8, -0.4, "../assets/allv6/Field34_hess_finalv6_stars2.jpg"],
[-2.27, 4.45, "../assets/allv6/Field35_hess_finalv6_stars2.jpg"],
[-1.6, 2.7, "../assets/allv6/Field36_hess_finalv6_stars2.jpg"],
[-1.5, 5.9, "../assets/allv6/Field37_hess_finalv6_stars2.jpg"],
[-1.0, 1.0, "../assets/allv6/Field38_hess_finalv6_stars2.jpg"],
[-0.8, 4.2, "../assets/allv6/Field39_hess_finalv6_stars2.jpg"],
[-0.4, -0.7, "../assets/allv6/Field40_hess_finalv6_stars2.jpg"],
[-0.1, 2.4, "../assets/allv6/Field41_hess_finalv6_stars2.jpg"],
[0.0, 5.6, "../assets/allv6/Field42_hess_finalv6_stars2.jpg"],
[0.5, 0.7, "../assets/allv6/Field43_hess_finalv6_stars2.jpg"],
[0.7, -4.2, "../assets/allv6/Field44_hess_finalv6_stars2.jpg"],
[0.7, 3.9, "../assets/allv6/Field45_hess_finalv6_stars2.jpg"],
[1.1, -1.0, "../assets/allv6/Field46_hess_finalv6_stars2.jpg"],
[1.3, 2.1, "../assets/allv6/Field47_hess_finalv6_stars2.jpg"],
[1.5, 5.3, "../assets/allv6/Field48_hess_finalv6_stars2.jpg"],
[2.0, 0.4, "../assets/allv6/Field49_hess_finalv6_stars2.jpg"],
[2.2, 3.6, "../assets/allv6/Field50_hess_finalv6_stars2.jpg"],
[2.8, 1.9, "../assets/allv6/Field51_hess_finalv6_stars2.jpg"],
[3.1, -8.0, "../assets/allv6/Field52_hess_finalv6_stars2.jpg"],
[5.9, 4.5, "../assets/allv6/Field53_hess_finalv6_stars2.jpg"],
[4.5, -3.4, "../assets/allv6/Field54_hess_finalv6_stars2.jpg"],
[5.7, 1.3, "../assets/allv6/Field55_hess_finalv6_stars2.jpg"],
[9.3, 2.3, "../assets/allv6/Field56_hess_finalv6_stars2.jpg"],
[15.3, 14.7, "../assets/allv6/Field57_hess_finalv6_stars2.jpg"],
[14.6, 9.8, "../assets/allv6/Field58_hess_finalv6_stars2.jpg"],
[12.3, 5.1, "../assets/allv6/Field59_hess_finalv6_stars2.jpg"],
[7.9, -5.7, "../assets/allv6/Field60_hess_finalv6_stars2.jpg"],
[10.5, -1.2, "../assets/allv6/Field61_hess_finalv6_stars2.jpg"],
[2.2, -16.0, "../assets/allv6/Field62_hess_finalv6_stars2.jpg"],
[13.6, 1.6, "../assets/allv6/Field63_hess_finalv6_stars2.jpg"],
[4.4, -13.3, "../assets/allv6/Field64_hess_finalv6_stars2.jpg"],
[6.4, -10.4, "../assets/allv6/Field65_hess_finalv6_stars2.jpg"],
[13.0, -5.0, "../assets/allv6/Field66_hess_finalv6_stars2.jpg"],
[16.1, -2.1, "../assets/allv6/Field67_hess_finalv6_stars2.jpg"],
[11.2, -8.0, "../assets/allv6/Field68_hess_finalv6_stars2.jpg"],
[10.7, -11.3, "../assets/allv6/Field69_hess_finalv6_stars2.jpg"],
[51.8, 18.0, "../assets/allv6/Field70_hess_finalv6_stars2.jpg"],
[50.3, 13.1, "../assets/allv6/Field71_hess_finalv6_stars2.jpg"],
[55.1, 15.9, "../assets/allv6/Field72_hess_finalv6_stars2.jpg"],
[64.6, 17.8, "../assets/allv6/Field74_hess_finalv6_stars2.jpg"],
[56.0, 12.4, "../assets/allv6/Field75_hess_finalv6_stars2.jpg"],
[59.9, 13.6, "../assets/allv6/Field76_hess_finalv6_stars2.jpg"],
[52.7, 9.5, "../assets/allv6/Field77_hess_finalv6_stars2.jpg"],
[15.0, -12.1, "../assets/allv6/Field80_hess_finalv6_stars2.jpg"],
[67.6, 10.8, "../assets/allv6/Field82_hess_finalv6_stars2.jpg"],
[7.6, -15.7, "../assets/allv6/Field83_hess_finalv6_stars2.jpg"],
[55.6, 4.1, "../assets/allv6/Field84_hess_finalv6_stars2.jpg"],
[59.3, 5.4, "../assets/allv6/Field85_hess_finalv6_stars2.jpg"],
[11.6, -14.8, "../assets/allv6/Field87_hess_finalv6_stars2.jpg"],
[60.4, 2.0, "../assets/allv6/Field90_hess_finalv6_stars2.jpg"],
[47.3, -3.5, "../assets/allv6/Field91_hess_finalv6_stars2.jpg"],
[57.3, -1.0, "../assets/allv6/Field92_hess_finalv6_stars2.jpg"],
[66.1, 1.3, "../assets/allv6/Field93_hess_finalv6_stars2.jpg"],
[54.3, -4.0, "../assets/allv6/Field94_hess_finalv6_stars2.jpg"],
[59.2, -6.1, "../assets/allv6/Field98_hess_finalv6_stars2.jpg"],
[52.0, -8.9, "../assets/allv6/Field99_hess_finalv6_stars2.jpg"],
[63.5, -6.5, "../assets/allv6/Field100_hess_finalv6_stars2.jpg"],
[68.7, -5.3, "../assets/allv6/Field101_hess_finalv6_stars2.jpg"],
[53.3, -12.3, "../assets/allv6/Field104_hess_finalv6_stars2.jpg"],
[10.9, -18.1, "../assets/allv6/Field106_hess_finalv6_stars2.jpg"],
[57.0, -14.2, "../assets/allv6/Field109_hess_finalv6_stars2.jpg"],
[65.1, -13.0, "../assets/allv6/Field110_hess_finalv6_stars2.jpg"],
[58.6, -17.5, "../assets/allv6/Field113_hess_finalv6_stars2.jpg"],
[6.9, -18.9, "../assets/allv6/Field115_hess_finalv6_stars2.jpg"],
[52.8, -20.6, "../assets/allv6/Field116_hess_finalv6_stars2.jpg"],
[57.4, -20.7, "../assets/allv6/Field117_hess_finalv6_stars2.jpg"],
[49.1, -22.1, "../assets/allv6/Field118_hess_finalv6_stars2.jpg"],
[67.8, -22.6, "../assets/allv6/Field121_hess_finalv6_stars2.jpg"],
[53.9, -25.6, "../assets/allv6/Field123_hess_finalv6_stars2.jpg"],
[55.4, -30.5, "../assets/allv6/Field127_hess_finalv6_stars2.jpg"],
[63.7, -30.5, "../assets/allv6/Field128_hess_finalv6_stars2.jpg"],
[9.0, -22.7, "../assets/allv6/Field129_hess_finalv6_stars2.jpg"],
[2.8, -19.5, "../assets/allv6/Field130_hess_finalv6_stars2.jpg"],
[4.8, -23.4, "../assets/allv6/Field131_hess_finalv6_stars2.jpg"],
[8.5, -29.5, "../assets/allv6/Field132_hess_finalv6_stars2.jpg"],
[3.8, -28.3, "../assets/allv6/Field133_hess_finalv6_stars2.jpg"],
[0.2, -22.2, "../assets/allv6/Field134_hess_finalv6_stars2.jpg"],
[-0.8, -27.0, "../assets/allv6/Field135_hess_finalv6_stars2.jpg"],
[-5.4, -27.2, "../assets/allv6/Field136_hess_finalv6_stars2.jpg"],
[-8.6, -29.5, "../assets/allv6/Field137_hess_finalv6_stars2.jpg"],
[-4.1, -22.6, "../assets/allv6/Field138_hess_finalv6_stars2.jpg"],
[-10.0, -25.6, "../assets/allv6/Field139_hess_finalv6_stars2.jpg"],
[-18.4, -29.0, "../assets/allv6/Field140_hess_finalv6_stars2.jpg"],
[-8.6, -22.8, "../assets/allv6/Field141_hess_finalv6_stars2.jpg"],
[-14.7, -25.5, "../assets/allv6/Field142_hess_finalv6_stars2.jpg"],
[-13.1, -22.8, "../assets/allv6/Field143_hess_finalv6_stars2.jpg"],
[-21.1, -24.4, "../assets/allv6/Field144_hess_finalv6_stars2.jpg"],
[-17.7, -20.9, "../assets/allv6/Field145_hess_finalv6_stars2.jpg"],
[-22.4, -20.5, "../assets/allv6/Field147_hess_finalv6_stars2.jpg"],
[-5.9, -18.7, "../assets/allv6/Field148_hess_finalv6_stars2.jpg"],
[-17.8, -17.7, "../assets/allv6/Field149_hess_finalv6_stars2.jpg"],
[-22.4, -17.4, "../assets/allv6/Field150_hess_finalv6_stars2.jpg"],
[-8.9, -17.7, "../assets/allv6/Field152_hess_finalv6_stars2.jpg"],
[19.5, 32.3, "../assets/allv6/Field153_hess_finalv6_stars2.jpg"],
[19.4, 24.7, "../assets/allv6/Field154_hess_finalv6_stars2.jpg"],
[19.2, 18.7, "../assets/allv6/Field155_hess_finalv6_stars2.jpg"],
[18.8, 12.7, "../assets/allv6/Field156_hess_finalv6_stars2.jpg"],
[16.6, 4.4, "../assets/allv6/Field157_hess_finalv6_stars2.jpg"],
[55.0, 20.5, "../assets/allv6/Field158_hess_finalv6_stars2.jpg"],
[16.1, -8.3, "../assets/allv6/Field159_hess_finalv6_stars2.jpg"],
[69.2, 15.5, "../assets/allv6/Field160_hess_finalv6_stars2.jpg"],
[51.9, 7.2, "../assets/allv6/Field161_hess_finalv6_stars2.jpg"],
[60.4, 9.4, "../assets/allv6/Field162_hess_finalv6_stars2.jpg"],
[50.7, -0.2, "../assets/allv6/Field163_hess_finalv6_stars2.jpg"],
[71.2, 3.0, "../assets/allv6/Field164_hess_finalv6_stars2.jpg"],
[49.9, -6.2, "../assets/allv6/Field165_hess_finalv6_stars2.jpg"],
[49.4, -12.2, "../assets/allv6/Field166_hess_finalv6_stars2.jpg"],
[71.0, -9.7, "../assets/allv6/Field167_hess_finalv6_stars2.jpg"],
[47.7, -18.9, "../assets/allv6/Field168_hess_finalv6_stars2.jpg"],
[62.9, -18.1, "../assets/allv6/Field169_hess_finalv6_stars2.jpg"],
[63.5, -25.6, "../assets/allv6/Field170_hess_finalv6_stars2.jpg"],
[13.1, -21.6, "../assets/allv6/Field171_hess_finalv6_stars2.jpg"],
[49.1, -31.8, "../assets/allv6/Field172_hess_finalv6_stars2.jpg"],
[65.8, -36.0, "../assets/allv6/Field173_hess_finalv6_stars2.jpg"],
[49.5, -37.9, "../assets/allv6/Field174_hess_finalv6_stars2.jpg"],
[11.3, -27.4, "../assets/allv6/Field175_hess_finalv6_stars2.jpg"],
[-20.6, -10.5, "../assets/allv6/Field176_hess_finalv6_stars2.jpg"],
[-18.9, -6.3, "../assets/allv6/Field177_hess_finalv6_stars2.jpg"],
[-15.2, -7.7, "../assets/allv6/Field178_hess_finalv6_stars2.jpg"],
[2.0, -24.4, "../assets/allv6/Field179_hess_finalv6_stars2.jpg"],
[-2.2, -30.0, "../assets/allv6/Field180_hess_finalv6_stars2.jpg"],
[-11.7, -20.1, "../assets/allv6/Field181_hess_finalv6_stars2.jpg"],
[6.6, -25.6, "../assets/allv6/Field183_hess_finalv6_stars2.jpg"],
[-5.28, 5.06, "../assets/allv6/Field184_hess_finalv6_stars2.jpg"],
[-5.41, 1.99, "../assets/allv6/Field185_hess_finalv6_stars2.jpg"],
[-6.08, 3.68, "../assets/allv6/Field186_hess_finalv6_stars2.jpg"],
[-6.27, 0.63, "../assets/allv6/Field187_hess_finalv6_stars2.jpg"],
[-3.77, 4.75, "../assets/allv6/Field188_hess_finalv6_stars2.jpg"],
[-3.91, 1.66, "../assets/allv6/Field189_hess_finalv6_stars2.jpg"],
[-4.18, -1.43, "../assets/allv6/Field190_hess_finalv6_stars2.jpg"],
[-4.51, 6.45, "../assets/allv6/Field191_hess_finalv6_stars2.jpg"],
[-4.57, 3.36, "../assets/allv6/Field192_hess_finalv6_stars2.jpg"],
[-4.77, 0.28, "../assets/allv6/Field193_hess_finalv6_stars2.jpg"],
[-2.71, -1.78, "../assets/allv6/Field195_hess_finalv6_stars2.jpg"],
[-3.12, -4.87, "../assets/allv6/Field196_hess_finalv6_stars2.jpg"],
[-3.29, -0.06, "../assets/allv6/Field198_hess_finalv6_stars2.jpg"],
[-3.63, -3.15, "../assets/allv6/Field199_hess_finalv6_stars2.jpg"],
[-1.24, -2.11, "../assets/allv6/Field201_hess_finalv6_stars2.jpg"],
[-1.66, -5.23, "../assets/allv6/Field202_hess_finalv6_stars2.jpg"],
[-2.64, -6.60, "../assets/allv6/Field204_hess_finalv6_stars2.jpg"],
[0.21, -2.44, "../assets/allv6/Field207_hess_finalv6_stars2.jpg"],
[-0.21, -5.58, "../assets/allv6/Field208_hess_finalv6_stars2.jpg"],
[-0.71, -3.84, "../assets/allv6/Field210_hess_finalv6_stars2.jpg"],
[-1.19, -6.96, "../assets/allv6/Field211_hess_finalv6_stars2.jpg"],
[1.66, -2.76, "../assets/allv6/Field214_hess_finalv6_stars2.jpg"],
[1.24, -5.92, "../assets/allv6/Field215_hess_finalv6_stars2.jpg"],
[0.26, -7.32, "../assets/allv6/Field217_hess_finalv6_stars2.jpg"],
[3.62, 3.32, "../assets/allv6/Field220_hess_finalv6_stars2.jpg"],
[3.41, 0.12, "../assets/allv6/Field221_hess_finalv6_stars2.jpg"],
[3.10, -3.07, "../assets/allv6/Field222_hess_finalv6_stars2.jpg"],
[2.68, -6.25, "../assets/allv6/Field223_hess_finalv6_stars2.jpg"],
[2.55, -1.32, "../assets/allv6/Field226_hess_finalv6_stars2.jpg"],
[2.18, -4.50, "../assets/allv6/Field227_hess_finalv6_stars2.jpg"],
[1.70, -7.66, "../assets/allv6/Field228_hess_finalv6_stars2.jpg"],
[5.17, 6.27, "../assets/allv6/Field230_hess_finalv6_stars2.jpg"],
[5.06, 3.05, "../assets/allv6/Field231_hess_finalv6_stars2.jpg"],
[4.85, -0.16, "../assets/allv6/Field232_hess_finalv6_stars2.jpg"],
[4.11, -6.57, "../assets/allv6/Field233_hess_finalv6_stars2.jpg"],
[4.41, 4.79, "../assets/allv6/Field235_hess_finalv6_stars2.jpg"],
[4.25, 1.58, "../assets/allv6/Field236_hess_finalv6_stars2.jpg"],
[3.98, -1.62, "../assets/allv6/Field237_hess_finalv6_stars2.jpg"],
[3.62, -4.82, "../assets/allv6/Field238_hess_finalv6_stars2.jpg"],
[5.41, -1.91, "../assets/allv6/Field243_hess_finalv6_stars2.jpg"],
[12.24, 18.31, "../assets/allv6/Field246_hess_finalv6_stars2.jpg"],
[15.07, 21.30, "../assets/allv6/Field247_hess_finalv6_stars2.jpg"] ];

    document.getElementById("map").addEventListener("click", function (event) {
        var contentvar = document.getElementById("map")
        var rect = contentvar.getBoundingClientRect()
        // [0].children[0]
        // console.log(contentvar.clientX);
        // console.log(contentvar.pageX);
        click_lonlat = get_lon_lat(event.clientX-rect.left, event.clientY-rect.top);
        x = event.clientX-rect.left
        y = event.clientY-rect.top
  
        out_str = x + " " + y + " " + click_lonlat[0] + " " + click_lonlat[1];
        // out_str = event.pageX-contentvar.offsetLeft + " " + event.pageY-contentvar.offsetTop + " " + click_lonlat[0] + " " + click_lonlat[1];
        // document.getElementById("pixel").innerHTML = out_str;
        // out_str = event.clientX + " " + event.clientY + " " + click_lonlat[0] + " " + click_lonlat[1];
        // document.getElementById("pixel").innerHTML = out_str;
        // console.log()

        cmd = document.getElementById("hess")
        for(var i=0; i<click_centers.length; i++) {
            target_lon = click_centers[i][0];
            target_lat = click_centers[i][1];
            target_img = click_centers[i][2];
            dist = Math.pow(click_lonlat[0] - target_lon,2) +
                Math.pow(click_lonlat[1] - target_lat,2);
            if(dist < 0.7) {

                cmd.style.display = "block";
                if(event.pageX >  20000) {
                    cmd.style.left = 40;
                } else {
                    cmd.style.left = 800;
                };
                // cmd.style.left = 1000;
                cmd.style.top = 20;
                cmd.src = target_img;
                return;
            }
        };
        // Didn't find one.
        cmd.style.display = "none";

    });
</script>
</body>



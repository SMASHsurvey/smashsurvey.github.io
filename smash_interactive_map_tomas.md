---
layout: page
title: LMC Star Formation Histories
---


<head>
    <title>SMASH Interactive Map</title>
</head>
<body>
    <style>
        #hess {
            display: none;
            position: absolute;
            width: 1000px;
            border: solid 5px black;
        };
    </style>
    <div id="container">
        <img id="map" src="../assets/sfh_lmc/html_parent_sfh.png"><br>
        <img id="hess" src="../assets/sfh_lmc/solution_1.png" width="1500" height="500" ><br>
        <div id="pixel"></div>
    </div>

<script>
    function get_lon_lat(screenX, screenY) {
        minX = 97;
        maxX = 791;
        minY = 738;
        maxY = 29;

        min_lon = 93.0;
        max_lon = 69.75;
        min_lat = -74.35;
        max_lat = -65.0;

        click_lon = min_lon + (screenX - minX)*(max_lon - min_lon)/(maxX - minX); 
        click_lat = min_lat + (screenY - minY)*(max_lat - min_lat)/(maxY - minY);
        return [click_lon, click_lat];

    };

    var click_centers = [
                            [86.19793923645537,   -71.15715194501864,  "../assets/sfh_lmc/solution_1.png"],
                            [86.25101499567377,   -70.82632639930044,  "../assets/sfh_lmc/solution_2.png"],
                            [84.75232468880438,   -71.05420330666217,  "../assets/sfh_lmc/solution_3.png"],
                            [84.82827589169337,   -70.74149093584512,  "../assets/sfh_lmc/solution_4.png"],
                            [87.84648950299007,   -71.0830663567615,  "../assets/sfh_lmc/solution_5.png"],
                            [87.9053637176595,   -70.70999121197154,  "../assets/sfh_lmc/solution_6.png"],
                            [89.94264375820094,   -70.91417202115262,  "../assets/sfh_lmc/solution_7.png"],
                            [86.49996285964365,   -70.52031786954626,  "../assets/sfh_lmc/solution_8.png"],
                            [85.13191865145632,   -70.46153330650881,  "../assets/sfh_lmc/solution_9.png"],
                            [87.92963431490301,   -70.35942222587322,  "../assets/sfh_lmc/solution_10.png"],
                            [83.63580040321243,   -70.53136884997672,  "../assets/sfh_lmc/solution_11.png"],
                            [89.67443834307767,   -70.42014998665151,  "../assets/sfh_lmc/solution_12.png"],
                            [91.54806245936338,   -70.49804811273201,  "../assets/sfh_lmc/solution_13.png"],
                            [86.50415728986977,   -70.21092696204542,  "../assets/sfh_lmc/solution_14.png"],
                            [88.79036373302269,   -70.03776846515969,  "../assets/sfh_lmc/solution_15.png"],
                            [87.18133972811437,   -69.95780531749054,  "../assets/sfh_lmc/solution_16.png"],
                            [88.39135923191523,   -69.6520128735945,  "../assets/sfh_lmc/solution_17.png"],
                            [85.0774212001396,   -70.17260625042339,  "../assets/sfh_lmc/solution_18.png"],
                            [90.95965329015758,   -69.9776283324874,  "../assets/sfh_lmc/solution_19.png"],
                            [90.40707521417315,   -69.5867724842455,  "../assets/sfh_lmc/solution_20.png"],
                            [85.65398019677772,   -69.8896586832609,  "../assets/sfh_lmc/solution_21.png"],
                            [84.05762144530472,   -69.91094901323105,  "../assets/sfh_lmc/solution_22.png"],
                            [86.5937590670065,   -69.63005192936073,  "../assets/sfh_lmc/solution_23.png"],
                            [84.98989854261796,   -69.59679494188424,  "../assets/sfh_lmc/solution_24.png"],
                            [83.52277271767687,   -70.22579562294396,  "../assets/sfh_lmc/solution_25.png"],
                            [82.16374951969655,   -70.42085072189177,  "../assets/sfh_lmc/solution_26.png"],
                            [82.42662920007675,   -69.95454056882582,  "../assets/sfh_lmc/solution_27.png"],
                            [83.46439732706843,   -69.6135739545002,  "../assets/sfh_lmc/solution_28.png"],
                            [87.08898712088325,   -69.32286609399159,  "../assets/sfh_lmc/solution_29.png"],
                            [88.64556563756057,   -69.16865993010192,  "../assets/sfh_lmc/solution_30.png"],
                            [85.59435563037992,   -69.29930471063119,  "../assets/sfh_lmc/solution_31.png"],
                            [86.59854705251755,   -69.00035904216394,  "../assets/sfh_lmc/solution_32.png"],
                            [83.39729992220533,   -70.83469296591518,  "../assets/sfh_lmc/solution_33.png"],
                            [81.97370958498078,   -69.63931083590057,  "../assets/sfh_lmc/solution_34.png"],
                            [83.98230719734438,   -69.29851258384413,  "../assets/sfh_lmc/solution_35.png"],
                            [82.3352729182854,   -69.32392839063854,  "../assets/sfh_lmc/solution_36.png"],
                            [81.3750049581373,   -70.17616279226448,  "../assets/sfh_lmc/solution_37.png"],
                            [80.5196355192248,   -70.45171590483477,  "../assets/sfh_lmc/solution_38.png"],
                            [83.43061602949513,   -71.12872571379908,  "../assets/sfh_lmc/solution_39.png"],
                            [81.99998781783701,   -70.74405105746382,  "../assets/sfh_lmc/solution_40.png"],
                            [80.62970766687725,   -70.75838501385331,  "../assets/sfh_lmc/solution_41.png"],
                            [80.74763790365459,   -69.41745965585059,  "../assets/sfh_lmc/solution_42.png"],
                            [80.7243788693573,   -69.84949406151502,  "../assets/sfh_lmc/solution_43.png"],
                            [79.78681956251555,   -70.11285751221452,  "../assets/sfh_lmc/solution_44.png"],
                            [84.74455321936874,   -68.96603661950255,  "../assets/sfh_lmc/solution_45.png"],
                            [88.02166280096776,   -68.80779196015001,  "../assets/sfh_lmc/solution_46.png"],
                            [85.89758470444514,   -68.72211939103441,  "../assets/sfh_lmc/solution_47.png"],
                            [83.14744517699292,   -68.99322081589608,  "../assets/sfh_lmc/solution_48.png"],
                            [81.71426744543096,   -69.03870340961804,  "../assets/sfh_lmc/solution_49.png"],
                            [79.64080295634623,   -69.61728338864356,  "../assets/sfh_lmc/solution_50.png"],
                            [80.33097447811075,   -69.12035557827396,  "../assets/sfh_lmc/solution_51.png"],
                            [79.07933899132705,   -70.37854046057554,  "../assets/sfh_lmc/solution_52.png"],
                            [81.97839333790395,   -71.04773949272854,  "../assets/sfh_lmc/solution_53.png"],
                            [82.32991281143656,   -71.35827042921937,  "../assets/sfh_lmc/solution_54.png"],
                            [78.64811166318931,   -69.88177025419668,  "../assets/sfh_lmc/solution_55.png"],
                            [83.70919449005098,   -68.702554900901,  "../assets/sfh_lmc/solution_56.png"],
                            [77.99491686187483,   -69.53451780635127,  "../assets/sfh_lmc/solution_57.png"],
                            [80.54399668597614,   -71.04762813009343,  "../assets/sfh_lmc/solution_58.png"],
                            [84.99491408482285,   -71.3677682030029,  "../assets/sfh_lmc/solution_59.png"],
                            [83.7241346656107,   -71.44268275240874,  "../assets/sfh_lmc/solution_60.png"],
                            [79.16228197295355,   -70.6945773145265,  "../assets/sfh_lmc/solution_61.png"],
                            [86.57935218770537,   -71.48321032753441,  "../assets/sfh_lmc/solution_62.png"],
                            [77.76930765170864,   -70.54529337260139,  "../assets/sfh_lmc/solution_63.png"],
                            [88.20722591156657,   -71.45552033737721,  "../assets/sfh_lmc/solution_64.png"],
                            [89.77282460286933,   -71.47375784064613,  "../assets/sfh_lmc/solution_65.png"],
                            [85.27514216036529,   -71.6969574026768,  "../assets/sfh_lmc/solution_66.png"],
                            [82.60887882763681,   -71.67702717179455,  "../assets/sfh_lmc/solution_67.png"],
                            [80.90179548123407,   -71.33904798346728,  "../assets/sfh_lmc/solution_68.png"],
                            [79.12880398445527,   -70.9989032964016,  "../assets/sfh_lmc/solution_69.png"],
                            [79.39371494580341,   -71.31689724265429,  "../assets/sfh_lmc/solution_70.png"],
                            [77.71048168022385,   -70.87542073087884,  "../assets/sfh_lmc/solution_71.png"],
                            [77.80719759643605,   -70.17821322632462,  "../assets/sfh_lmc/solution_72.png"],
                            [76.95132311857475,   -69.90218352496119,  "../assets/sfh_lmc/solution_73.png"],
                            [78.90458639078774,   -69.23179603869315,  "../assets/sfh_lmc/solution_74.png"],
                            [77.1172481556884,   -69.21884771529199,  "../assets/sfh_lmc/solution_75.png"],
                            [76.5140006603421,   -70.38641699940585,  "../assets/sfh_lmc/solution_76.png"],
                            [77.84062817283267,   -71.22131402130866,  "../assets/sfh_lmc/solution_77.png"],
                            [76.32753666124735,   -70.72177950492468,  "../assets/sfh_lmc/solution_78.png"],
                            [83.93709554061942,   -71.78806574933999,  "../assets/sfh_lmc/solution_79.png"],
                            [81.14940749193968,   -71.63824584254166,  "../assets/sfh_lmc/solution_80.png"],
                            [76.42575769089838,   -69.60050907421302,  "../assets/sfh_lmc/solution_81.png"],
                            [81.73854299484098,   -71.95138620839509,  "../assets/sfh_lmc/solution_82.png"],
                            [83.19935334729517,   -72.06648199325679,  "../assets/sfh_lmc/solution_83.png"],
                            [82.1553483424786,   -68.73504976293728,  "../assets/sfh_lmc/solution_84.png"],
                            [76.3600682297749,   -71.07849836179024,  "../assets/sfh_lmc/solution_85.png"],
                            [79.6207355785831,   -71.631093997419,  "../assets/sfh_lmc/solution_86.png"],
                            [80.13405175582831,   -71.95179145259897,  "../assets/sfh_lmc/solution_87.png"],
                            [75.72341547715314,   -70.11292389192215,  "../assets/sfh_lmc/solution_88.png"],
                            [74.9169521847353,   -70.4082398541081,  "../assets/sfh_lmc/solution_89.png"],
                            [80.28023304702563,   -68.81377873344084,  "../assets/sfh_lmc/solution_90.png"],
                            [74.82470202545976,   -70.72735449509392,  "../assets/sfh_lmc/solution_91.png"],
                            [81.03391032102168,   -68.57549359792237,  "../assets/sfh_lmc/solution_92.png"],
                            [82.80739400779433,   -68.44910908693909,  "../assets/sfh_lmc/solution_93.png"],
                            [78.922372402583,   -68.83289145585424,  "../assets/sfh_lmc/solution_94.png"],
                            [79.51780429438907,   -68.51513619982563,  "../assets/sfh_lmc/solution_95.png"],
                            [84.779024370549,   -68.51320539780187,  "../assets/sfh_lmc/solution_96.png"],
                            [86.5758216845692,   -68.40911042375515,  "../assets/sfh_lmc/solution_97.png"],
                            [88.17857958907658,   -68.42547398255454,  "../assets/sfh_lmc/solution_98.png"],
                            [89.52885434746682,   -68.61722687169743,  "../assets/sfh_lmc/solution_99.png"],
                            [88.57947399754407,   -68.05146062764906,  "../assets/sfh_lmc/solution_100.png"],
                            [77.3165635173735,   -68.88734944805287,  "../assets/sfh_lmc/solution_101.png"],
                            [75.71351651843257,   -68.99855758081668,  "../assets/sfh_lmc/solution_102.png"],
                            [75.60692745618806,   -69.3407439707967,  "../assets/sfh_lmc/solution_103.png"],
                            [81.56900436793546,   -68.29691590542954,  "../assets/sfh_lmc/solution_104.png"],
                            [83.96156428799185,   -68.26241684970724,  "../assets/sfh_lmc/solution_105.png"],
                            [75.13772242998006,   -69.809611954237,  "../assets/sfh_lmc/solution_106.png"],
                            [74.08615233291636,   -70.06712998768143,  "../assets/sfh_lmc/solution_107.png"],
                            [74.7605706035878,   -71.06290357235333,  "../assets/sfh_lmc/solution_108.png"],
                            [77.99735542124922,   -71.55732901131668,  "../assets/sfh_lmc/solution_109.png"],
                            [74.38753196815041,   -69.5369796876985,  "../assets/sfh_lmc/solution_110.png"],
                            [74.0961360902417,   -69.20138940293685,  "../assets/sfh_lmc/solution_111.png"],
                            [77.89911020891125,   -68.54543189569223,  "../assets/sfh_lmc/solution_112.png"],
                            [80.15122528347901,   -68.2466715472495,  "../assets/sfh_lmc/solution_113.png"],
                            [78.58348648789509,   -68.23975289689098,  "../assets/sfh_lmc/solution_114.png"],
                            [74.24844667566272,   -68.88098428354148,  "../assets/sfh_lmc/solution_115.png"],
                            [81.08640797943764,   -67.98334942780878,  "../assets/sfh_lmc/solution_116.png"],
                            [85.43448102470936,   -68.14636663643395,  "../assets/sfh_lmc/solution_117.png"],
                            [82.6793158437168,   -68.08809119297713,  "../assets/sfh_lmc/solution_118.png"],
                            [84.08275152752826,   -67.92618199367666,  "../assets/sfh_lmc/solution_119.png"],
                            [73.3214100708862,   -70.35855848005234,  "../assets/sfh_lmc/solution_120.png"],
                            [76.3507983829457,   -68.60762376605568,  "../assets/sfh_lmc/solution_121.png"],
                            [75.02782536977466,   -68.64625071577359,  "../assets/sfh_lmc/solution_122.png"],
                            [73.22900782449803,   -69.78422820843737,  "../assets/sfh_lmc/solution_123.png"],
                            [72.74581586806963,   -69.42824649678191,  "../assets/sfh_lmc/solution_124.png"],
                            [78.37455196799925,   -71.91356470151817,  "../assets/sfh_lmc/solution_125.png"],
                            [76.28468920424768,   -71.44076685372393,  "../assets/sfh_lmc/solution_126.png"],
                            [76.52124952657493,   -71.81895110079722,  "../assets/sfh_lmc/solution_127.png"],
                            [73.09892257310062,   -70.71152424144418,  "../assets/sfh_lmc/solution_128.png"],
                            [71.51571258756015,   -70.52253607063344,  "../assets/sfh_lmc/solution_129.png"],
                            [76.85560296629372,   -68.28469971629542,  "../assets/sfh_lmc/solution_130.png"],
                            [72.2905985140159,   -69.11930904589381,  "../assets/sfh_lmc/solution_131.png"],
                            [82.27897600977809,   -67.77428140340443,  "../assets/sfh_lmc/solution_132.png"],
                            [77.50505380378503,   -68.01208816944823,  "../assets/sfh_lmc/solution_133.png"],
                            [72.17547341451873,   -70.0921042616164,  "../assets/sfh_lmc/solution_134.png"],
                            [71.59404121038625,   -69.51025413227664,  "../assets/sfh_lmc/solution_135.png"],
                            [74.369826486185,   -71.43042930473484,  "../assets/sfh_lmc/solution_136.png"],
                            [74.71323310878911,   -71.83493128420936,  "../assets/sfh_lmc/solution_137.png"],
                            [73.10683633877764,   -71.13450095224624,  "../assets/sfh_lmc/solution_138.png"],
                            [71.82830587062986,   -71.0341619746885,  "../assets/sfh_lmc/solution_139.png"],
                            [81.01840746117597,   -72.28627889077289,  "../assets/sfh_lmc/solution_140.png"],
                            [79.45791796170944,   -67.95454344606888,  "../assets/sfh_lmc/solution_141.png"],
                            [72.84851593246064,   -68.78149461245478,  "../assets/sfh_lmc/solution_142.png"],
                            [71.01040408085832,   -68.9785069025343,  "../assets/sfh_lmc/solution_143.png"],
                            [75.3261844808072,   -68.28843473238332,  "../assets/sfh_lmc/solution_144.png"],
                            [80.3916543417766,   -67.69384047344606,  "../assets/sfh_lmc/solution_145.png"],
                            [73.92758133719258,   -68.40680043657088,  "../assets/sfh_lmc/solution_146.png"],
                            [72.43032455973986,   -68.49145019149756,  "../assets/sfh_lmc/solution_147.png"],
                            [85.72417549051484,   -67.7997195989743,  "../assets/sfh_lmc/solution_148.png"],
                            [78.33216616843048,   -67.78091050095551,  "../assets/sfh_lmc/solution_149.png"],
                            [87.02482995339716,   -67.95885032527585,  "../assets/sfh_lmc/solution_150.png"],
                            [83.685021864316,   -67.62995829460638,  "../assets/sfh_lmc/solution_151.png"],
                            [75.94397676345669,   -67.996911406982,  "../assets/sfh_lmc/solution_152.png"],
                            [76.73424340664546,   -67.72750277607335,  "../assets/sfh_lmc/solution_153.png"],
                            [81.47259507448285,   -67.49520789391349,  "../assets/sfh_lmc/solution_154.png"],
                            [70.79949605294574,   -68.64956706042133,  "../assets/sfh_lmc/solution_155.png"],
                            [73.02352333925033,   -71.7808012210565,  "../assets/sfh_lmc/solution_156.png"],
                            [79.0536216782919,   -72.285146986298,  "../assets/sfh_lmc/solution_157.png"],
                            [76.99464811284314,   -72.21397941352504,  "../assets/sfh_lmc/solution_158.png"],
                            [82.7200279272118,   -72.4054701620757,  "../assets/sfh_lmc/solution_159.png"],
                            [74.9310312433156,   -72.23792748951412,  "../assets/sfh_lmc/solution_160.png"],
                            [86.95647571929285,   -71.84810154110987,  "../assets/sfh_lmc/solution_161.png"],
                            [85.18256253898791,   -72.0511097035588,  "../assets/sfh_lmc/solution_162.png"],
                            [88.71115317976253,   -71.93627603638552,  "../assets/sfh_lmc/solution_163.png"],
                            [86.87861784395913,   -72.35007477351418,  "../assets/sfh_lmc/solution_164.png"],
                            [84.5471441950247,   -72.3933365250849,  "../assets/sfh_lmc/solution_165.png"],
                            [81.29691913987735,   -72.70212793415644,  "../assets/sfh_lmc/solution_166.png"],
                            [89.07899851857033,   -72.30424943853984,  "../assets/sfh_lmc/solution_167.png"],
                            [79.34108965492342,   -72.668270260901,  "../assets/sfh_lmc/solution_168.png"],
                            [77.20163306041286,   -72.62950003419112,  "../assets/sfh_lmc/solution_169.png"],
                            [75.12197557484646,   -72.69116000636902,  "../assets/sfh_lmc/solution_170.png"],
                            [72.4680607713136,   -72.25374736483727,  "../assets/sfh_lmc/solution_171.png"],
                            [74.05039098895897,   -68.060930781384,  "../assets/sfh_lmc/solution_172.png"],
                            [74.77543120453296,   -67.82704539559408,  "../assets/sfh_lmc/solution_173.png"],
                            [79.13102020926823,   -67.52571756948909,  "../assets/sfh_lmc/solution_174.png"],
                            [80.19941419571714,   -67.2954299407898,  "../assets/sfh_lmc/solution_175.png"],
                            [77.59280001931772,   -67.47631706588777,  "../assets/sfh_lmc/solution_176.png"],
                            [72.71469050732851,   -68.15708389229202,  "../assets/sfh_lmc/solution_177.png"],
                            [85.17821134114575,   -67.49922819458868,  "../assets/sfh_lmc/solution_178.png"],
                            [82.81268252018752,   -67.33415701653335,  "../assets/sfh_lmc/solution_179.png"],
                            [75.47880642746519,   -67.56969927490232,  "../assets/sfh_lmc/solution_180.png"],
                            [81.58896138007759,   -67.11875384072873,  "../assets/sfh_lmc/solution_181.png"],
                            [78.56499972066695,   -67.2139833663391,  "../assets/sfh_lmc/solution_182.png"],
                            [71.55989601753389,   -68.12545434168224,  "../assets/sfh_lmc/solution_183.png"],
                            [73.67932028750232,   -67.6234677423916,  "../assets/sfh_lmc/solution_184.png"],
                            [87.24198871951799,   -67.52826123411693,  "../assets/sfh_lmc/solution_185.png"],
                            [76.33648155967047,   -67.31980288947527,  "../assets/sfh_lmc/solution_186.png"],
                            [86.02045877184122,   -67.20154810330452,  "../assets/sfh_lmc/solution_187.png"],
                            [84.23240138878745,   -67.19859730795619,  "../assets/sfh_lmc/solution_188.png"],
                            [85.04389978262685,   -66.85884788952221,  "../assets/sfh_lmc/solution_189.png"],
                            [74.81086587534185,   -67.27395668009426,  "../assets/sfh_lmc/solution_190.png"],
                            [80.01643428826208,   -66.94598066239902,  "../assets/sfh_lmc/solution_191.png"],
                            [81.41045294150166,   -66.77855500849532,  "../assets/sfh_lmc/solution_192.png"],
                            [73.66109387739851,   -67.25430686245552,  "../assets/sfh_lmc/solution_193.png"],
                            [77.18196083879994,   -67.06548850793344,  "../assets/sfh_lmc/solution_194.png"],
                            [75.6230793829826,   -67.00675502427285,  "../assets/sfh_lmc/solution_195.png"],
                            [83.04732830763561,   -66.94241777724346,  "../assets/sfh_lmc/solution_196.png"],
                            [83.71247816669081,   -66.61930862714338,  "../assets/sfh_lmc/solution_197.png"],
                            [78.47214856790619,   -66.84843801622787,  "../assets/sfh_lmc/solution_198.png"],
                            [74.61795855166118,   -66.81169078653869,  "../assets/sfh_lmc/solution_199.png"],
                            [76.54873153970982,   -66.73841278024176,  "../assets/sfh_lmc/solution_200.png"],
                            [77.85601883827546,   -66.53136853582221,  "../assets/sfh_lmc/solution_201.png"],
                            [87.25588438473834,   -66.99674479268909,  "../assets/sfh_lmc/solution_202.png"],
                            [82.30932411943658,   -66.50606639973044,  "../assets/sfh_lmc/solution_203.png"],
                            [86.70043758165427,   -66.61672827443691,  "../assets/sfh_lmc/solution_204.png"],
                            [72.9283929644385,   -72.61626166850158,  "../assets/sfh_lmc/solution_205.png"],
                            [83.46213275082445,   -72.80892306988795,  "../assets/sfh_lmc/solution_206.png"],
                            [79.74342793096781,   -66.59722712696795,  "../assets/sfh_lmc/solution_207.png"],
                            [80.82016334961007,   -66.3569986290216,  "../assets/sfh_lmc/solution_208.png"],
                            [85.86486770224305,   -72.78043936539137,  "../assets/sfh_lmc/solution_209.png"],
                            [86.90674954502262,   -73.268091664179,  "../assets/sfh_lmc/solution_210.png"],
                            [78.95382647045072,   -66.26398170963182,  "../assets/sfh_lmc/solution_211.png"],
                            [85.09971499350998,   -66.46991584760325,  "../assets/sfh_lmc/solution_212.png"],
                            [76.33512469953723,   -66.36927793902053,  "../assets/sfh_lmc/solution_213.png"],
                            [86.29480282345634,   -66.18347378464861,  "../assets/sfh_lmc/solution_214.png"],
                            [84.54542274033936,   -66.19321943994004,  "../assets/sfh_lmc/solution_215.png"],
                            [77.51397723326622,   -66.09668860479009,  "../assets/sfh_lmc/solution_216.png"],
                            [82.63516803589341,   -66.15017632667266,  "../assets/sfh_lmc/solution_217.png"],
                            [76.2271745713442,   -65.95730824348598,  "../assets/sfh_lmc/solution_218.png"],
                            [80.32043521388017,   -65.98029576930446,  "../assets/sfh_lmc/solution_219.png"],
                            [81.94897634471342,   -65.81724436869807,  "../assets/sfh_lmc/solution_220.png"],
                            [78.65052944044487,   -65.85257276295151,  "../assets/sfh_lmc/solution_221.png"],
                            [78.21655097601624,   -73.06856317553239,  "../assets/sfh_lmc/solution_222.png"],
                            [80.49927015129767,   -73.12666733497127,  "../assets/sfh_lmc/solution_223.png"],
                            [82.74884022991814,   -73.197102705759,  "../assets/sfh_lmc/solution_224.png"],
                            [73.62018525532957,   -73.04580429778913,  "../assets/sfh_lmc/solution_225.png"],
                            [78.8156357564755,   -73.53267295136337,  "../assets/sfh_lmc/solution_226.png"],
                            [81.84840751957678,   -73.64627183718557,  "../assets/sfh_lmc/solution_227.png"],
                            [76.22621426325912,   -73.13877269330125,  "../assets/sfh_lmc/solution_228.png"],
                            [84.85317934624577,   -73.44962039397564,  "../assets/sfh_lmc/solution_229.png"],
                            [79.0214438596179,   -65.49871528753171,  "../assets/sfh_lmc/solution_230.png"],
                            [77.32903410457571,   -65.54348276315935,  "../assets/sfh_lmc/solution_231.png"],
                            [84.85667159559746,   -73.92752505339423,  "../assets/sfh_lmc/solution_232.png"] ];

    document.getElementById("map").addEventListener("click", function (event) {
        click_lonlat = get_lon_lat(event.pageX, event.pageY);

        out_str = event.pageX + " " + event.pageY + " " + click_lonlat[0] + " " + click_lonlat[1];
        document.getElementById("pixel").innerHTML = out_str;

        cmd = document.getElementById("hess")
        for(var i=0; i<click_centers.length; i++) {
            target_lon = click_centers[i][0];
            target_lat = click_centers[i][1];
            target_img = click_centers[i][2];
            dist = Math.pow(click_lonlat[0] - target_lon,2) +
                Math.pow(click_lonlat[1] - target_lat,2);
            if(dist < 0.3) {

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

<?php
// URL NodeMCU
$nodemcu_url = "http://192.168.0.102"; // Ganti dengan IP NodeMCU kamu

$sensor_data = ""; // Variabel untuk menyimpan data sensor

// Mengambil data dari NodeMCU
$response = file_get_contents($nodemcu_url);

// Memisahkan suhu dan kelembapan dari respons
if ($response !== false) {
    preg_match('/Suhu: (.*?) °C/', $response, $temp_matches);
    preg_match('/Kelembapan: (.*?) %/', $response, $humidity_matches);

    $suhu = isset($temp_matches[1]) ? (float)$temp_matches[1] : 0;
    $kelembapan = isset($humidity_matches[1]) ? (float)$humidity_matches[1] : 0;
}

if (isset($_GET['action'])) {
    if ($_GET['action'] == 'on') {
        file_get_contents($nodemcu_url . "/led/on");
    } elseif ($_GET['action'] == 'off') {
        file_get_contents($nodemcu_url . "/led/off");
    }
}
?>

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Kontrol LED dan Monitoring DHT</title>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #f4f4f4;
            color: #333;
            padding: 20px;
        }
        h1 {
            color: #333;
        }
        .button {
            padding: 10px 20px;
            margin: 10px;
            background-color: #28a745;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            text-decoration: none;
        }
        .button:hover {
            background-color: #218838;
        }
        .chart-container {
            position: relative;
            margin: auto;
            height: 40vh;
            width: 80vw;
        }
        .gauge-container {
            display: flex;
            justify-content: space-around;
            margin-top: 20px;
        }
        .gauge {
            width: 150px; /* Ukuran gauge */
            height: 150px; /* Ukuran gauge */
        }
        .sensor-data {
            font-size: 24px;
            margin-top: 20px;
        }
    </style>
</head>
<body>
    <h1>Kontrol LED dari Jarak Jauh</h1>
    <a class="button" href="?action=on">Nyalakan LED</a>
    <a class="button" href="?action=off">Matikan LED</a>
    
    <h2>Data Sensor DHT:</h2>
    <div class="sensor-data">
        <p id="suhuText">Suhu: <?php echo $suhu; ?> °C</p>
        <p id="kelembapanText">Kelembapan: <?php echo $kelembapan; ?> %</p>
    </div>
    <div class="chart-container">
        <canvas id="sensorChart"></canvas>
    </div>

    <div class="gauge-container">
        <div>
            <canvas id="temperatureGauge" class="gauge"></canvas>
            <h3>Suhu (°C)</h3>
        </div>
        <div>
            <canvas id="humidityGauge" class="gauge"></canvas>
            <h3>Kelembapan (%)</h3>
        </div>
    </div>

    <script>
        const ctx = document.getElementById('sensorChart').getContext('2d');

        // Membuat grafik garis
        const sensorChart = new Chart(ctx, {
            type: 'line',
            data: {
                labels: [], // Waktu (menit atau detik) untuk sumbu X
                datasets: [
                    {
                        label: 'Suhu (°C)',
                        data: [], // Data suhu
                        borderColor: 'rgba(54, 162, 235, 1)', // Biru
                        backgroundColor: 'rgba(54, 162, 235, 0.2)',
                        fill: true,
                        tension: 0.1
                    },
                    {
                        label: 'Kelembapan (%)',
                        data: [], // Data kelembapan
                        borderColor: 'rgba(255, 99, 132, 1)',
                        backgroundColor: 'rgba(255, 99, 132, 0.2)',
                        fill: true,
                        tension: 0.1
                    }
                ]
            },
            options: {
                responsive: true,
                scales: {
                    x: {
                        title: {
                            display: true,
                            text: 'Waktu (detik)'
                        }
                    },
                    y: {
                        title: {
                            display: true,
                            text: 'Nilai'
                        }
                    }
                }
            }
        });

        // Fungsi untuk membuat gauge
        function createGauge(ctx, value, max, title) {
            return new Chart(ctx, {
                type: 'radar',
                data: {
                    labels: [title, 'Max'],
                    datasets: [{
                        label: title,
                        data: [value, max],
                        backgroundColor: 'rgba(255, 99, 132, 0.2)',
                        borderColor: 'rgba(255, 99, 132, 1)',
                        borderWidth: 1,
                    }]
                },
                options: {
                    scales: {
                        r: {
                            min: 0,
                            max: max,
                            ticks: {
                                stepSize: 100
                            }
                        }
                    }
                }
            });
        }

        // Membuat gauge untuk suhu dan kelembapan
        const temperatureGauge = createGauge(document.getElementById('temperatureGauge').getContext('2d'), <?php echo $suhu; ?>, 500, 'Suhu');
        const humidityGauge = createGauge(document.getElementById('humidityGauge').getContext('2d'), <?php echo $kelembapan; ?>, 100, 'Kelembapan');

        // Fungsi untuk memperbarui grafik dan gauge
        function updateChartAndGauges() {
            // Menambahkan data suhu dan kelembapan
            const currentTime = sensorChart.data.labels.length; // Mendapatkan waktu saat ini
            sensorChart.data.labels.push(currentTime); // Menambahkan label waktu
            sensorChart.data.datasets[0].data.push(<?php echo $suhu; ?>); // Data suhu
            sensorChart.data.datasets[1].data.push(<?php echo $kelembapan; ?>); // Data kelembapan
            
            // Memperbarui nilai gauge
            temperatureGauge.data.datasets[0].data[0] = <?php echo $suhu; ?>; // Update suhu
            humidityGauge.data.datasets[0].data[0] = <?php echo $kelembapan; ?>; // Update kelembapan
            
            // Memperbarui teks suhu dan kelembapan
            document.getElementById('suhuText').innerText = 'Suhu: ' + <?php echo $suhu; ?> + ' °C';
            document.getElementById('kelembapanText').innerText = 'Kelembapan: ' + <?php echo $kelembapan; ?> + ' %';

            // Batasi jumlah data dalam grafik untuk menjaga kinerja
            if (sensorChart.data.labels.length > 20) {
                sensorChart.data.labels.shift(); // Menghapus label tertua
                sensorChart.data.datasets[0].data.shift(); // Menghapus data suhu tertua
                sensorChart.data.datasets[1].data.shift(); // Menghapus data kelembapan tertua
            }

            sensorChart.update(); // Memperbarui grafik
            temperatureGauge.update(); // Memperbarui gauge suhu
            humidityGauge.update(); // Memperbarui gauge kelembapan
        }

        // Memperbarui grafik dan gauge setiap 2 detik
        setInterval(() => {
            updateChartAndGauges();
        }, 2000);
    </script>
</body>
</html>

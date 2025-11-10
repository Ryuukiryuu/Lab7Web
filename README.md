**Nama   :** Wahyu Andika  
**NIM    :** 312410182  
**Kelas  :** TI.24.A2  
**Matkul :** Pemrograman Web 1  
**Dosen Pengampu :** Agung Nugroho, S.Kom., M.Kom

```<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Form Input Data Diri</title>
</head>
<body>
    <h2>Form Input Data Diri</h2>
    
    <form method="post">
        <label>Nama:</label>
        <input type="text" name="nama" required>
        <br><br>
        
        <label>Tanggal Lahir:</label>
        <input type="date" name="tanggal_lahir" required>
        <br><br>
        
        <label>Pekerjaan:</label>
        <select name="pekerjaan" required>
            <option value="">-- Pilih Pekerjaan --</option>
            <option value="Software Engineer">Software Engineer</option>
            <option value="Data Analyst">Data Analyst</option>
            <option value="Web Developer">Web Developer</option>
        </select>
        <br><br>
        
        <input type="submit" value="Kirim">
    </form>

    <?php
    if ($_SERVER["REQUEST_METHOD"] == "POST") {
        // Mengambil data dari form
        $nama = $_POST['nama'];
        $tanggal_lahir = $_POST['tanggal_lahir'];
        $pekerjaan = $_POST['pekerjaan'];
        
        // Menghitung umur
        $tgl_lahir = new DateTime($tanggal_lahir);
        $today = new DateTime();
        $umur = $today->diff($tgl_lahir)->y;
        
        // Menentukan gaji berdasarkan pekerjaan
        $gaji = 0;
        switch ($pekerjaan) {
            case 'Software Engineer':
                $gaji = 15000000;
                break;
            case 'Data Analyst':
                $gaji = 12000000;
                break;
            case 'Web Developer':
                $gaji = 10000000;
                break;
            default:
                $gaji = 0;
        }
        
        echo "<h3>Hasil Data Diri:</h3>";
        echo "Nama: " . $nama . "<br>";
        echo "Tanggal Lahir: " . $tanggal_lahir . "<br>";
        echo "Umur: " . $umur . " tahun<br>";
        echo "Pekerjaan: " . $pekerjaan . "<br>";
        echo "Gaji: Rp " . number_format($gaji, 0, ',', '.') . "<br>";
    }
    ?>
</body>
</html>
```

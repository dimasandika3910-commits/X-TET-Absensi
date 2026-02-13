# X-TET-Absensi
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Absensi Kelas Digital</title>
    <style>
        body { font-family: sans-serif; background-color: #f4f4f9; padding: 20px; }
        .container { max-width: 800px; margin: auto; background: white; padding: 20px; border-radius: 10px; shadow: 0 2px 10px rgba(0,0,0,0.1); }
        h2 { text-align: center; color: #333; }
        table { width: 100%; border-collapse: collapse; margin-top: 20px; }
        th, td { border: 1px solid #ddd; padding: 12px; text-align: left; }
        th { background-color: #007bff; color: white; }
        tr:nth-child(even) { background-color: #f9f9f9; }
        .gender-p { color: #e91e63; font-weight: bold; } /* Pink untuk Perempuan */
        .gender-l { color: #2196f3; font-weight: bold; } /* Biru untuk Laki-laki */
        select { padding: 5px; border-radius: 4px; }
    </style>
</head>
<body>

<div class="container">
    <h2>Daftar Absensi Kelas</h2>
    <p>Total Siswa: 40 (32 Laki-laki, 8 Perempuan)</p>
    
    <table>
        <thead>
            <tr>
                <th>No</th>
                <th>Nama Siswa</th>
                <th>L/P</th>
                <th>Keterangan</th>
            </tr>
        </thead>
        <tbody id="tabel-absen">
            </tbody>
    </table>
</div>

<script>
    const namaLaki = ["Ahmad", "Budi", "Candra", "Dedi", "Eko", "Fajar", "Gilang", "Hadi", "Indra", "Joko", "Kevin", "Lutfi", "Mahendra", "Naufal", "Oky", "Panji", "Rian", "Sakti", "Tio", "Umar", "Vino", "Wahyu", "Xander", "Yuda", "Zaki", "Aris", "Bagas", "Dimas", "Farhan", "Ghani", "Hafiz", "Irfan"];
    const namaPerempuan = ["Anisa", "Bella", "Citra", "Dinda", "Elena", "Fira", "Gisela", "Hana"];
    const marga = ["Pratama", "Setiawan", "Wijaya", "Kusuma", "Putra", "Putri", "Sari", "Lestari"];

    function generateNama(list, gender) {
        let hasil = [];
        list.forEach(nama => {
            let acakMarga = marga[Math.floor(Math.random() * marga.length)];
            hasil.push({ nama: `${nama} ${acakMarga}`, gender: gender });
        });
        return hasil;
    }

    // Gabungkan data
    let dataSiswa = [
        ...generateNama(namaLaki, 'L'),
        ...generateNama(namaPerempuan, 'P')
    ];

    // Acak urutan siswa agar tidak mengumpul
    dataSiswa.sort(() => Math.random() - 0.5);

    const tbody = document.getElementById('tabel-absen');

    dataSiswa.forEach((siswa, index) => {
        let row = `<tr>
            <td>${index + 1}</td>
            <td>${siswa.nama}</td>
            <td class="${siswa.gender === 'P' ? 'gender-p' : 'gender-l'}">${siswa.gender}</td>
            <td>
                <select>
                    <option value="hadir">Hadir</option>
                    <option value="izin">Izin</option>
                    <option value="sakit">Sakit</option>
                    <option value="alpa">Alpa</option>
                </select>
            </td>
        </tr>`;
        tbody.innerHTML += row;
    });
</script>

</body>
</html>

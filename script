/* =========================
   Navigasi Menu
========================= */
function showPage(id) {
  const sections = document.querySelectorAll("main section");
  sections.forEach(section => section.classList.remove("active"));

  document.getElementById(id).classList.add("active");
}

/* =========================
   Kalkulator Zakat
========================= */
document.addEventListener("DOMContentLoaded", () => {

  const kursEmas = 2321000; // Rp/gram emas

  const toggleGroup = (checkboxId, groupId) => {
    const checkbox = document.getElementById(checkboxId);
    const group = document.getElementById(groupId);
    if (!checkbox || !group) return;

    checkbox.addEventListener("change", function () {
      group.style.display = this.checked ? "block" : "none";
    });
  };

  toggleGroup("chkEmas", "emasGroup");
  toggleGroup("chkPertanian", "pertanianGroup");
  toggleGroup("chkPenghasilan", "penghasilanGroup");
  toggleGroup("chkHartaLain", "hartaLainGroup");

  // ⬇⬇⬇ TETAP SEPERTI KODE KAMU
  window.hitungZakat = function () {

    let totalZakat = 0;
    let output = "";
    let argumenText = "";

    // Zakat Emas
    if (document.getElementById("chkEmas").checked) {
      const emas = Number(document.getElementById("jumlahEmas").value);
      const haul = Number(document.getElementById("haulEmas").value);

      if (emas >= 85 && haul >= 1) {
        const zakatEmas = (emas * kursEmas) * 0.025;
        totalZakat += zakatEmas;
        output += `<p>💰 <b>Zakat Emas:</b> Rp ${zakatEmas.toLocaleString()}</p>`;
        argumenText += `Memiliki ${emas} gram emas selama ${haul} tahun.<br>`;
      } else {
        output += `<p>❌ <b>Emas</b> belum mencapai nisab atau haul.</p>`;
      }
    }

    // Zakat Pertanian
    if (document.getElementById("chkPertanian").checked) {
      const panen = Number(document.getElementById("hasilPanen").value);
      const jenis = document.getElementById("irigasi").value;
      const nisab = 520;

      if (panen >= nisab) {
        const tarif = jenis === "alami" ? 0.10 : 0.05;
        const zakatPertanian = panen * kursEmas * tarif / 10;
        totalZakat += zakatPertanian;
        output += `<p>🌾 <b>Zakat Pertanian (${jenis}):</b> Rp ${zakatPertanian.toLocaleString()}</p>`;
        argumenText += `Hasil panen ${panen} kg dengan irigasi ${jenis}.<br>`;
      } else {
        output += `<p>❌ <b>Hasil panen</b> belum mencapai nisab.</p>`;
      }
    }

    // Zakat Penghasilan
    if (document.getElementById("chkPenghasilan").checked) {
      const penghasilan = Number(document.getElementById("penghasilan").value);
      const pengeluaran = Number(document.getElementById("pengeluaran").value);
      const bersih = penghasilan - pengeluaran;
      const nisab = 85 * kursEmas;

      if (bersih * 12 >= nisab) {
        const zakatPenghasilan = bersih * 0.025;
        totalZakat += zakatPenghasilan;
        output += `<p>💼 <b>Zakat Penghasilan:</b> Rp ${zakatPenghasilan.toLocaleString()}</p>`;
        argumenText += `Penghasilan bersih Rp ${bersih.toLocaleString()} per bulan.<br>`;
      } else {
        output += `<p>❌ <b>Penghasilan</b> belum mencapai nisab tahunan.</p>`;
      }
    }

    // ✅ Zakat Harta Lain (TETAP ADA)
    if (document.getElementById("chkHartaLain").checked) {
      const perak = Number(document.getElementById("perak").value) * 13000;
      const uang = Number(document.getElementById("uang").value);
      const perniagaan = Number(document.getElementById("perniagaan").value);
      const peternakan = Number(document.getElementById("peternakan").value);
      const pertambangan = Number(document.getElementById("pertambangan").value);
      const investasi = Number(document.getElementById("investasi").value);
      const tabungan = Number(document.getElementById("tabungan").value);
      const rikaz = Number(document.getElementById("rikaz").value);

      const totalHarta =
        perak + uang + perniagaan + peternakan +
        pertambangan + investasi + tabungan + rikaz;

      const nisab = 85 * kursEmas;

      if (totalHarta >= nisab) {
        const zakatHarta =
          (perak + uang + perniagaan + investasi + tabungan) * 0.025 +
          peternakan * 0.025 +
          pertambangan * 0.025 +
          rikaz * 0.20;

        totalZakat += zakatHarta;
        output += `<p>🏦 <b>Zakat Harta Lain:</b> Rp ${zakatHarta.toLocaleString()}</p>`;
        argumenText += `Total harta Rp ${totalHarta.toLocaleString()} telah mencapai nisab.<br>`;
      } else {
        output += `<p>❌ <b>Harta lain</b> belum mencapai nisab.</p>`;
      }
    }

    output += `<hr><h3 style="color:#4f46e5;">💲 Total Zakat: Rp ${totalZakat.toLocaleString()}</h3>`;
    document.getElementById("hasil").innerHTML = output;

    document.getElementById("logika").innerHTML = `
      <strong>Hukum Logika:</strong>
      Menggunakan konjungsi (AND) dan implikasi dalam penentuan zakat.
    `;

    document.getElementById("argumen").innerHTML = `
      <strong>Argumen Logis:</strong>
      ${argumenText || "Belum ada data yang memenuhi syarat wajib zakat."}
    `;
  };

});

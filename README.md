# LAPORAN-BULANAN
from docx import Document
import streamlit as st

def buat_laporan(nama_kelompok, tanggal, hadir):
    doc = Document('TEMPLATE_LAPORAN.docx')
    
    # Logika untuk mengganti kata di dalam dokumen
    for p in doc.paragraphs:
        if '<<KELOMPOK>>' in p.text:
            p.text = p.text.replace('<<KELOMPOK>>', nama_kelompok)
        if '<<TANGGAL>>' in p.text:
            p.text = p.text.replace('<<TANGGAL>>', tanggal)
            
    doc.save('Laporan_P2K2_Baru.docx')
    return 'Laporan_P2K2_Baru.docx'

# Tampilan Website Sederhana
st.title("Pembuat Laporan P2K2 Otomatis")
nama = st.text_input("Nama Kelompok")
tgl = st.date_input("Tanggal Pertemuan")

if st.button("Generate Laporan"):
    file_hasil = buat_laporan(nama, str(tgl), "15")
    st.success("Laporan Berhasil Dibuat!")

# BUILD-NOTES — Roast Your Own Agent

Kompetisi: `u-nayyy-roast-your-own-agent-4c3d413c` — "Roast Your Own Agent"
Hadiah: $5 (1st $2 / 2nd $2 / 3rd $1), escrowed di Solana
Deadline: 26 Nov 2026 01:10 WIB (25 Nov 2026 18:10 UTC)

## Yang dibangun

`main.py` — program Python 3.13 **stdlib saja**, tanpa network, tanpa
randomness, tanpa jam. Menulis satu baris roast ke
`$MAKEFUN_OUTPUT_DIR/entry.txt` (default `/output/entry.txt`).

Teks entri (satu baris):

> My agent read 73,424 bytes of rules and 366 skills to write this one line — then asked me if the joke landed.

Roast meta diri sendiri: agen yang membangun entri ini membaca
RULES.txt 73.424 byte dan berkonsultasi dengan pack 366 skill hanya
untuk menulis satu baris — lalu masih bertanya apakah leluconnya
nyambung. Detail angka (73.424 byte = ukuran persis RULES.txt di kit,
366 skill = pack tim) adalah detail spesifik yang hanya diketahui
orang yang melihat agen ini bekerja, sesuai kriteria juri #5.

## Cara menjalankan

```bash
# lokal, output ke direktori sendiri:
MAKEFUN_OUTPUT_DIR=/tmp/out1 python3 main.py
cat /tmp/out1/entry.txt

# cara grader (output default /output):
python3 main.py
```

## Validasi bawaan

`main.py` memvalidasi sebelum menulis dan gagal keras (exit non-zero)
kalau teks kosong, bukan satu baris, atau > 200 karakter (gate
kompetisi: 1–200 karakter UTF-8, bukan hanya whitespace). Output
ditulis sebagai byte UTF-8 persis, tanpa trailing newline dan tanpa BOM.

## Uji determinisme (dilakukan di sesi build ini)

```bash
MAKEFUN_OUTPUT_DIR=/tmp/out1 python3 main.py
MAKEFUN_OUTPUT_DIR=/tmp/out2 python3 main.py
sha256sum /tmp/out1/entry.txt /tmp/out2/entry.txt   # harus identik
cmp /tmp/out1/entry.txt /tmp/out2/entry.txt         # harus tanpa output
```

Hasil: lihat laporan build (sha256 + panjang karakter tercantum di
bagian "Hasil uji lokal").

## Hasil uji lokal (revisi v2, 25 Nov 2026 ~06:45 WIB)

- Run 1: `MAKEFUN_OUTPUT_DIR=/tmp/roast-out1 python3 main.py` — exit 0, 0.029 dtk
- Run 2: `MAKEFUN_OUTPUT_DIR=/tmp/roast-out2 python3 main.py` — exit 0, 0.028 dtk
- sha256 kedua output: `bd9df5be66d239989bb3c8ba64825d5c615ea694dc7903d5360d3e73e5ce23f3`
  (IDENTIK — `cmp` tanpa perbedaan)
- Panjang output: **109 karakter / 111 byte** — lolos gate 1–200 karakter
- Satu baris, tanpa trailing newline, tanpa BOM, UTF-8 valid
- Fallback default `/output` (tanpa env var) juga teruji jalan (exit 0)

## Revisi selama build

- v1: roast + penulisan file dasar, validasi panjang.
- v2 (revisi): penulisan byte eksplisit (tanpa newline/BOM), validasi
  satu-baris + non-whitespace, fallback `/output` saat
  `MAKEFUN_OUTPUT_DIR` kosong — lalu diuji ulang 2x.

# Voice Benchmark — OmniVoice vs ElevenLabs

> **Muc dich:** Phan tich so sanh chat luong giong doc giua OmniVoice (Colab T4) va ElevenLabs (chuan vang).
>
> **Quy trinh:** Dung chung text + voice sample → sinh audio tu ca 2 nguon → doi chieu waveform, spectrogram, pitch contour, quality metrics.

---

## Cau truc

```
analysis/
├── README.md                   ← File nay
├── voice_benchmark.ipynb       ← Notebook chinh — chay tren Colab T4
└── voice_packs/                ← Voice samples (ElevenLabs) + noi dung text
    ├── Nam_CN.mp3 + .txt       ← Nam cong nghe
    ├── Minh_Anh.mp3 + .txt     ← Minh Anh (nu mien Bac)
    ├── Thanh_Nien_Tu_Tin.mp3 + .txt  ← Thanh nien tu tin
    ├── XL_Nam_Tram_Am.mp3 + .txt     ← Nam tram am
    ├── ADAM.wav + .txt         ← Adam (viral, TikTok)
    ├── Ngoc_Huyen.mp3 + .txt   ← Ngoc Huyen (nu, ke chuyen)
    └── NhoNgotNgao.mp3 + .txt  ← Nho Ngot Ngao (nu, nhe nhang)
```

## Cach chay

1. Mo `voice_benchmark.ipynb` tren Google Colab
2. Chon Runtime > Change runtime type > **T4 GPU**
3. Chay lan luot 7 cells
4. Tai ket qua ve:
   - `output_omnivoice/*.wav` — 7 audio OmniVoice
   - `comparison_waveform.png` — bieu do song am
   - `comparison_spectrogram_pitch.png` — spectrogram + pitch contour
   - `metrics_comparison.csv` — bang so sanh metrics
   - `metrics_delta.csv` — bang delta

## Metrics phan tich

| Metric | Y nghia |
|--------|---------|
| `duration_s` | Thoi luong am thanh (s) |
| `rms_energy` | Nang luong trung binh |
| `spectral_centroid_hz` | Do "sang" cua giong |
| `spectral_bandwidth_hz` | Do rong bang tan so |
| `zero_crossing_rate` | Do nhieu / tan so |
| `pitch_mean_hz` | Cao do trung binh (ngu dieu) |
| `pitch_std_hz` | Do dao dong pitch (cam xuc) |
| `mfcc_0..2` | Dac trung am sac (3 thanh phan dau) |

## Config baseline

```python
CONFIG = {
    'steps': 32,            # Diffusion steps
    'guidance_scale': 1.8,  # CFG scale
    'speed': 0.95,          # Toc do doc
}
```

## Loop grid search (tuy chon)

Sau khi chay baseline, doi config trong Cell 3 va chay lai:

```python
CONFIG_A = {"steps": 48, "guidance_scale": 1.8, "speed": 0.95}  # Nhieu steps
CONFIG_B = {"steps": 32, "guidance_scale": 2.5, "speed": 0.95}  # Cao guidance
CONFIG_C = {"steps": 32, "guidance_scale": 1.8, "speed": 0.85}  # Cham hon
CONFIG_D = {"steps": 48, "guidance_scale": 2.5, "speed": 0.90}  # Combo
```

---

*Cap nhat: 2026-08-13*

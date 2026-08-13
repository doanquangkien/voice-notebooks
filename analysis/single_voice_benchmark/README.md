# Single Voice Benchmark

So sánh chất lượng giọng đọc giữa OmniVoice và ElevenLabs với audio dài >1 phút.

## Upload files vào thư mục `voice_data/`

### 1. `elevenlabs_audio.wav`
Audio đã tạo từ ElevenLabs (WAV hoặc MP3).

### 2. `text.txt`
Text nội dung đọc (UTF-8).

## Cấu trúc thư mục

```
single_voice_benchmark/
├── README.md
├── voice_single_benchmark.ipynb
└── voice_data/
    ├── elevenlabs_audio.wav
    └── text.txt
```

## Chạy trên Colab

1. Upload 2 files vào `voice_data/`
2. Mở `voice_single_benchmark.ipynb` trên Colab
3. Chọn GPU T4: Runtime > Change runtime type > T4
4. Chạy tất cả cells

## Output

```
output/
├── {VOICE_KEY}_omnivoice.wav
├── comparison_waveform.png
├── comparison_spectrogram_pitch.png
├── metrics_comparison.csv
└── metrics_delta.csv
```

## Cấu hình

Sửa Cell 2 nếu cần thay đổi tên file:

```python
VOICE_KEY = 'srt_voice'
ELEVENLABS_AUDIO = 'voice_data/elevenlabs_audio.wav'
VOICE_TEXT_FILE = 'voice_data/text.txt'
```

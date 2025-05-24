AutoCut: Cut Videos via Subtitles

AutoCut automatically generates subtitles from your video. You then select the sentences to keep, and AutoCut will trim the corresponding video segments and save them.
No video editing software is required — you only need to edit a text file.

---

UPDATES

2024.10.05
- Support for large-v3-turbo Whisper model:
Command: autocut -t xxx --whisper-model large-v3-turbo

2024.03.10
- pip install support + Python API:
Command: pip install autocut-sub
Python usage:
from autocut import Transcribe, load_audio

2023.10.14
- Support for faster-whisper and dependency variants:
pip install .
pip install '.[faster]'
pip install '.[openai]'
pip install '.[all]'
autocut -t xxx --whisper-mode=faster
export OPENAI_API_KEY=sk-xxx
autocut -t xxx --whisper-mode=openai --openai-rpm=3

---

EXAMPLE: Process a Folder of Recordings

If your videos are saved in a folder like 2022-11-04/, run:
autocut -d 2022-11-04

This generates .md subtitle files (e.g. 11-28-18.md).
Edit them to keep only the desired lines.
AutoCut creates 11-28-18_cut.mp4 and 11-28-18_cut.md.

To merge:
1. Create a file called autocut.md listing all parts.
2. AutoCut will output autocut_merged.mp4

---

INSTALLATION

Using Python:
pip install git+https://github.com/mli/autocut.git

From source:
git clone https://github.com/mli/autocut
cd autocut
pip install .

Also install ffmpeg (on Linux/macOS/Windows depending on your OS).

---

COMMON COMMANDS

Transcribe a video:
autocut -t 22-52-00.mp4

Using a better model:
autocut -t 22-52-00.mp4 --whisper-model large

Cut with markdown and srt:
autocut -c 22-52-00.mp4 22-52-00.srt 22-52-00.md

Cut using only srt:
autocut -c 22-52-00.mp4 22-52-00.srt

Convert srt to md:
autocut -m test.srt test.mp4

---

FAQ

Encoding errors?
autocut -t video.mp4 --encoding=gbk
autocut -c video.mp4 video.srt video.md --encoding=gbk

Check GPU availability:
python -c "import torch; print(torch.cuda.is_available())"

Force CPU:
autocut -t video.mp4 --whisper-model large --device cpu

---

PROJECT STRUCTURE

autocut/
│  README.md
│  setup.py
│
└─ autocut/
   ├─ cut.py
   ├─ daemon.py
   ├─ main.py
   ├─ transcribe.py
   ├─ utils.py

---

RESOURCES

Whisper: https://github.com/openai/whisper
PyPI: https://pypi.org/project/openai-whisper/
AutoCut GitHub: https://github.com/mli/autocut

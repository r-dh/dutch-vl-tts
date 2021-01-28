# dutch-vl-tts

This dataset contains 15.000 audio fragments of a male Dutch Flemish voice, the sentences read are extracted from the [Mozilla Common Voice project](https://github.com/mozilla/common-voice/tree/master/server/data/nl). 



Dataset: [Google Drive (1.5GB)](https://drive.google.com/file/d/119YpJWcHGr4SWuh0BPdBpKRJju-ShJ7m/view?usp=sharing)

**New: the dataset is now also available for preview on [Kaggle](https://www.kaggle.com/rdheyg/spoken-belgian-dutch-audio)**



To use this dataset with [Mozilla TTS](https://github.com/mozilla/TTS), append the following fragment to `TTS/tts/datasets/preprocess.py`:

```python
def rdh_flemish(root_path, meta_file):
    txt_file = os.path.join(root_path, meta_file)
    speaker_name = "rdh_flemish"
    items = []
    with open(txt_file, 'r', encoding="utf-8") as f:
        for line in f:
            cols = line.split("|")
            text = cols[1]
            wav_file = os.path.join(root_path, cols[0] + ".wav")
            items.append([text, wav_file, speaker_name])
    return items
```



### Audio

Files in the dataset are 16-bit, 22050Hz downsampled from 44.1kHz, mono, wave.

The audio samples unfortunately may vary slightly over recording sessions.

- [De plant van de aardappel is giftig](./samples/vl00203.wav)
- [De Straat van Gibraltar is een zee-engte aan het uiteinde van de Middellandse Zee.](./samples/vl04108.wav)
- [Dat kan met betrekkelijk weinig geld.](./samples/vl09647.wav)
- [Ik geloof in deze dialoog en we zullen deze dialoog voeren.](./samples/vl12745.wav)
- [We zullen de uitkomsten op deze werkterreinen afwachten.](./samples/vl14994.wav)



### Trained models

Models with their corresponding synthesised audio samples are provided in the links below.

Original dataset:

- Tacotron DDC: [Google Drive](https://drive.google.com/drive/folders/1Ew_UGWNNqYxim8H4hhTjeApMRUAcEHZz?usp=sharing)

- Glow: [Google Drive](https://drive.google.com/drive/folders/1ndNI6ccdU3T02N1Q237236ZYZrY7ue31?usp=sharing)

Other dataset:

- Tacotron DDC with transfer learning: [Google Drive (subpar results)](https://drive.google.com/drive/folders/1SkDGmla3Ohiiaaah_syK8U3S1GsHrBq1?usp=sharing)

Due to a severe lack of quality data (4.000 noise gated fragments) the second dataset hasn't been released. The first model was used for transfer learning, although this still proved to be insufficient.

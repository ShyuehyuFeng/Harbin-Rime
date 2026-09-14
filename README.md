# Harbin-rime

A custom Rime input schema with IPA-based spelling and letter-based tones for the Harbin dialect of Northeastern Mandarin Chinese.

---

## Features

- **IPA-based spelling**: Consonants and vowels are derived from IPA, each mapped to a single ASCII letter. A letter may be mapped to variant consonants or vowels.
- **Letter tones**: Tones are typed as letters, not digits.
- **Three output modes**: Simplified, Mainland Traditional, and Taiwan Traditional, switchable on the fly.
- **Alias inputs**: Convenient shorthand for some letter clusters.
- **Word list**: Based on `luna_pinyin`.

---

## Files

| File | Description |
|------|-------------|
| `chinois.schema.yaml` | Rime schema definition |
| `chinois.dict.yaml` | Dictionary (Traditional Chinese) |

---

## Install

1. Copy `chinois.schema.yaml` and `chinois.dict.yaml` into your
   Rime user directory:
   - **Windows (Weasel)**: `%APPDATA%\Rime`
2. Redeploy Rime (right-click the tray icon → **Deploy**).
3. Press `F4` and select **Harbin**.

---

## Input Design

### Initials (consonants)

| IPA | Letter | Example |
|-----|--------|---------|
| m   | m      | ma      |
| n   | n      | na      |
| p   | b      | ba      |
| t   | d      | da      |
| k   | g      | ga      |
| pʰ  | p      | pa      |
| tʰ  | t      | ta      |
| kʰ  | k      | ka      |
| f   | f      | fa      |
| s   | s      | sa      |
| ʂ   | sh     | sha     |
| ɕ   | sh     | shi     |
| x   | h      | ha      |
| ʐ   | rh, r  | rha     |
| ʦ   | z, dz  | za      |
| tʂ  | j      | ja      |
| ʨ   | j      | ji      |
| ʦʰ  | ts, c  | tsa     |
| tʂʰ | ch     | cha     |
| ʨʰ  | ch     | chi     |
| l   | l      | la      |

### Finals (vowels)

| IPA | Letter | Row          |
|-----|--------|--------------|
| ɿ   | y      |              |
| ʅ   | y      |              |
| ɚ   | er     |              |
| a   | a      | Open mouth   |
| ɤ   | e      | Open mouth   |
| ɛ   | eh, e  | Open mouth   |
| ai  | ai     | Open mouth   |
| ei  | ei     | Open mouth   |
| au  | au     | Open mouth   |
| ou  | ou     | Open mouth   |
| an  | an     | Open mouth   |
| ən  | en     | Open mouth   |
| aŋ  | ang    | Open mouth   |
| əŋ  | eng    | Open mouth   |
| i   | i      | Even teeth   |
| ia  | ia     | Even teeth   |
| iɛ  | ieh    | Even teeth   |
| iau | iau    | Even teeth   |
| iou | iou    | Even teeth   |
| ian | ian    | Even teeth   |
| in  | in     | Even teeth   |
| iaŋ | iang   | Even teeth   |
| iŋ  | ing    | Even teeth   |
| u   | u      | Closed mouth |
| ua  | ua     | Closed mouth |
| uo  | uo     | Closed mouth |
| uai | uai    | Closed mouth |
| uei | uei    | Closed mouth |
| uan | uan    | Closed mouth |
| uən | uen    | Closed mouth |
| uaŋ | uang   | Closed mouth |
| uəŋ | ueng   | Closed mouth |
| uŋ  | ung    | Closed mouth |
| y   | yu     | Round mouth  |
| yɛ  | yueh   | Round mouth  |
| yan | yuan   | Round mouth  |
| yn  | yun    | Round mouth  |
| yŋ  | yung   | Round mouth  |

### Tones

| Tone | Letter |
|------|--------|
| 1    | v      |
| 2    | w      |
| 3    | x      |
| 5    | q      |
| 0    | v      |

---

## Alias Rules

The `speller/algebra` section defines the following shorthand rules.

| Alias input           | Equivalent to | Description |
|-----------------------|---------------|-------------|
| `c`                   | `ts`          | `c` is an alias for `ts` |
| `r`                   | `rh`          | `r` is an alias for `rh` |
| `dz`                  | `z`           | `dz` is an alias for `z` |
| `e`                   | `eh`          | `e` is an alias for `eh` |
| trailing tone dropped | any tone      | Typing without the final tone letter shows all tones |

**Notes:**

- `ch` always means `ch`. It is never interpreted as `tsh`.
- The tone-letter stripping rule means `zyv`, `zyw`, `zyx`, and `zyq`
  can all be typed as `zy`.

---

## Output Modes

Two switches in the `F4` menu control the output:

| `simplified_mode` | `taiwan_mode` | Output |
|-------------------|---------------|--------|
| 1 (SIMP)          | 0 (TRCN)      | Simplified (default) |
| 0 (TRAD)          | 0 (TRCN)      | Mainland Traditional |
| 0 (TRAD)          | 1 (TRTW)      | Taiwan Traditional |
| 1 (SIMP)          | 1 (TRTW)      | Simplified |

The dictionary is stored in Traditional Chinese. Conversion is
performed on the fly by OpenCC:

- `t2s.json` — Traditional → Simplified
- `t2tw.json` — Traditional → Taiwan Traditional

---

## License

MIT

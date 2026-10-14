# Transcript Studio

Turn a YouTube hearing, meeting, lecture, or interview into a readable **TXT transcript**, with optional timestamps. Paste a video link, choose a model and spoken language, and let the app process the audio on your Windows computer. You do not need to play the video or record your speakers.

Attach the finished TXT file to an LLM (ChatGPT, Claude, Gemini, etc.) to explore key takeaways, ask questions, and find relevant passages with conversation timestamps.

**Quick start: Download ZIP → Extract All → run `SETUP.cmd` → run `START.cmd`.**

## Before you begin

- Use **Windows 10 or 11 on a 64-bit Intel or AMD computer**. This package targets Windows x64.
- Have an internet connection for installation, YouTube audio downloads, and the first download of each transcription model.
- Allow approximately **15–20 GB of free disk space** for a full installation, installer caches, and models. This is a planning estimate; larger or additional models need more space.
- Have permission to install software. Microsoft C++ Build Tools may request administrator approval. On a managed work computer, ask your IT team if installation is restricted.
- Use a web browser to view the app. Its interface opens locally on your computer.

**You do not need to install Python, Anaconda, or Miniconda beforehand.** Setup can install the required runtime automatically. No paid transcription API or API key is required by this app.


## 1. Download and extract the app

1. Open https://github.com/rkarkee101/Transcript-Studio/.
2. Click **Transcript_Studio.zip** in the file list near the top.
3. On the next page, click the **downward-arrow download button (↓)** on the right, next to **Raw**. Its tooltip says **Download raw file**.
4. Find the downloaded ZIP in your **Downloads** folder.
5. Right-click it and choose **Extract All**.
6. Open the extracted folders until you see **SETUP.cmd** and **START.cmd**.

Run **SETUP.cmd** for the initial installation. After setup finishes, run **START.cmd** to open the app.

## 2. Install the required software

1. Double-click **`SETUP.cmd`**.
2. Leave the setup window open while it downloads and installs the required components. A fresh installation can download several GB and may take a while.
3. If Windows requests administrator approval for **Microsoft C++ Build Tools**, approve it if you are authorized to install software on this computer.
4. If setup reports **`3010`** or **restart required**, save your work, restart Windows, return to the extracted app folder, and run **`SETUP.cmd` again**.
5. Wait until the setup window says **Setup complete**.

Setup checks for a compatible existing Buzz environment first. Otherwise, it uses an existing Conda installation or installs **Miniforge**, a lightweight Conda distribution. It then creates a separate environment containing Python 3.12, FFmpeg, and the transcription libraries. It also installs Microsoft C++ Build Tools if needed.

The app's own installation files and settings normally go under `%LOCALAPPDATA%\TranscriptStudio`. A compatible existing environment may be reused instead. You do not need to open Anaconda PowerShell or type commands for normal installation and use.

## 3. Open Transcript Studio

1. Double-click **`START.cmd`** in the extracted app folder, or use the **Transcript Studio** desktop shortcut created by setup.
2. The interface opens in your default browser.
3. Wait for **Local engine ready** near the top of the page.

An address beginning with `http://127.0.0.1:` is expected: the interface is running on your own computer. Keep the extracted app folder because the launcher and desktop shortcut use its files.

For later sessions, use **`START.cmd`**. You normally run setup only for the initial installation or when repairing a failed installation.

## 4. Create a transcript

1. **Paste the YouTube link.** Use a link to a single public video. Playback is not required.
2. **Choose a model type.** Start with **Faster Whisper**.
3. **Choose a model size.** Start with **Small**. Smaller models generally need less time and memory; larger models need more resources. Accuracy varies with the recording and language.
4. **Choose the spoken language.** Select the language spoken in the recording, such as **English**, or choose **Auto-detect**.
5. **Choose whether to include timestamps.** See the timestamp options below.
6. **Choose an output folder.** Use **Browse…** or enter a folder path under **Save transcripts to**.
7. Click **Create transcript**.
8. Keep the computer awake while the app downloads the audio and transcribes it. The first use of a model also downloads that model's files.
9. When finished, click **Open transcript**, **Download TXT**, or **Open folder**.



The chosen output folder receives only the final **`.txt`** transcript. It includes the video title and source link, selected transcription settings, creation time, and optional timestamps. Temporary audio is used during processing; model downloads are cached separately for reuse.

### Suggested starting settings

| Setting | Starting choice |
| --- | --- |
| Model type | Faster Whisper |
| Model size | Small |
| Spoken language | The recording's language |
| Include timestamps | Enabled |
| Timestamp spacing | About every 30 seconds |

Other model types are **Whisper**, **Whisper.cpp**, and **Hugging Face**. Hugging Face is an advanced option requiring a compatible public speech recognition model ID. These alternatives may download different model files or have additional requirements.

### Timestamp options

**Include timestamps** is enabled by default. Choose:

- **About every 30 seconds:** groups speech into readable timestamped paragraphs.
- **About every 60 seconds:** creates fewer timestamped paragraphs.
- **At every speech segment:** adds a timestamp for each speech segment returned by the model.

Uncheck **Include timestamps** to create text without timestamps.

For example, `[01:23:45]` means approximately **1 hour, 23 minutes, and 45 seconds from the start of the recording**. It is not the time of day. Paragraph spacing follows available speech segments, so the intervals are approximate.

### While transcription is running

- The app shows the current stage and elapsed time. A percentage appears when the backend provides one; model loading may have no reliable percentage.
- Long recordings can take substantial time. Processing time depends on the computer, model, and amount of speech.
- The app processes one transcription job at a time.
- Use **Cancel** to stop a job. Canceled jobs must be started again.
- Closing the browser tab does **not** stop transcription. Use **START.cmd** to reopen the interface.
- Use **Quit app** to stop the app. Quitting during a job cancels it. Jobs do not resume automatically after a restart.
- **Completed this session** lists files from the current app session. Previously saved TXT files remain in the output folder.

## 5. Explore the transcript with an LLM

1. Open your preferred LLM, such as **ChatGPT, Claude, or Gemini**.
2. Attach the generated **TXT file** using that service's file attachment feature.
3. Ask for a summary, questions, comparisons, or relevant passages.
4. If you want time references, enable timestamps when creating the transcript and ask the LLM to cite the timestamps already in the file.

Example prompt:

> Read the attached transcript. Summarize the main topics and key takeaways, identify decisions or proposals, and list important unanswered questions. Cite the timestamps already provided in the transcript for each major point so I can find the conversation in the recording. Separate what speakers said from your own interpretation. If the file has no timestamps, say so rather than inventing them.

The app creates the transcript; LLM analysis is a separate step. Uploading the file to an LLM shares it with the provider you choose. Review the file before uploading it. If the service cannot accept the whole file, split it into chronological sections while retaining the original timestamps.

### Check details you plan to rely on

Automatic transcripts can mishear **names** (people, companies, projects, or technical terms) and **numbers** (dollar amounts, dates, percentages, or quantities). For example, “15 MW” and “50 MW” have very different meanings.

Use the timestamps to check important details and quotations against the recording. The text and timings are approximate, and the app does not identify speakers by their real names or produce a certified transcript.

## Troubleshooting

| Problem | What to do |
| --- | --- |
| The page says **Setup required** | Close the app, run `SETUP.cmd`, wait for **Setup complete**, then run `START.cmd`. |
| Setup reports **3010** or **restart required** | Restart Windows, then run `SETUP.cmd` again. |
| Setup reports a Microsoft C++ compiler error | Rerun `SETUP.cmd`, allow the Build Tools installation, and follow any restart instructions. |
| A GPU or CUDA error appears | Under **More options**, enable **Use CPU only** and try again. |
| A model will not load or memory runs out | Try **Faster Whisper / Small** or a smaller model. Confirm that the model download has internet access. |
| The video cannot be downloaded | Check the link and confirm the video is publicly accessible. Private videos, sign-in requirements, rate limits, or network restrictions may prevent downloads. The app does not extract browser cookies. |
| The app appears slow during the first run | Allow time for model downloading and loading. Keep the computer awake. |
| The browser says **Disconnected** | Run `START.cmd` again and use the complete address opened by the launcher. |
| A saved file is absent from the session list | Use **Open folder** or File Explorer. The in-app list covers only the current app session. |

For other errors, expand **Technical details** in the interface. Setup and app logs normally appear under `%LOCALAPPDATA%\TranscriptStudio\logs`. Review logs before sharing them because they may include video links and file paths.

## Privacy and sharing

Speech recognition runs locally. Internet access is used to download audio, models, and installation dependencies. The app does not automatically upload transcripts to an LLM.

You may share the original package ZIP or its GitHub Release link. Each recipient installs the required software on their own computer. Share the supplied source package rather than your installed environment, model cache, logs, or personal transcripts.

## Current validation and limits

The interface and job handling passed 17 automated tests. Faster Whisper / Small / English completed a real 20-second speech test on CPU. This does not establish performance for an entire long recording.

A complete installation on a clean second Windows computer still needs a pilot test. Other model types, GPU configurations, and every language have not each been tested. See [VALIDATION.txt](VALIDATION.txt) for details.

This is a source package with setup scripts. It requires dependency downloads and is not a signed, standalone executable or an offline installation bundle.

Uninstall Transcript Studio

The current version uses manual removal; it has no dedicated Transcript Studio uninstaller.

1. Open the app and click **Quit app**, then close its browser tab. Allow any setup or transcription process to finish stopping. If Windows says files are in use later, restart Windows and leave Transcript Studio closed.
2. **Keep any TXT transcripts you want.** The default `Documents\YouTubeTranscripts` folder is separate from the app. If you chose an output folder inside the extracted app folder or `%LOCALAPPDATA%\TranscriptStudio`, move those TXT files elsewhere before continuing.
3. Press **Windows + R**, enter **`%LOCALAPPDATA%\TranscriptStudio`**, and press **Enter**. If the folder does not exist, continue to step 5.
4. If this folder contains **`miniforge3`**, open that subfolder and run its **Miniforge uninstaller** (the file whose name begins with `Uninstall-` and ends with `.exe`). Follow its prompts and wait for it to finish. This removes the Miniforge copy installed inside Transcript Studio's folder. If there is no `miniforge3` subfolder, skip this step. If you use other Conda installations, leave any options for removing shared user configuration or shared caches unchecked. [About the Windows Conda uninstaller](https://conda.github.io/constructor/howto/).
5. In File Explorer, open **`%LOCALAPPDATA%`** and delete only the **`TranscriptStudio`** folder, if it remains. This removes the app's settings, logs, installer downloads, model files, and separate Python environment stored there. If you deliberately configured a different app-data location, use that location instead.
6. Delete the **Transcript Studio** desktop shortcut and the extracted app folder containing `START.cmd` and `SETUP.cmd`. You can also delete the downloaded ZIP if you no longer need it.

Keep your existing **Anaconda, Miniconda, Miniforge, or Buzz environment** if setup reused it. Existing Buzz model caches outside the Transcript Studio folder also remain available to Buzz. Do not delete shared `.conda`, `.condarc`, or general model-cache folders as part of these steps.

### Optional: remove Microsoft C++ Build Tools

If you installed **Visual Studio 2022 Build Tools** only for this app and no other projects need it, open **Visual Studio Installer**, find **Build Tools 2022**, and choose **More → Uninstall**. Follow the prompts. Otherwise, leave Build Tools installed. See [Microsoft's uninstall instructions](https://learn.microsoft.com/en-us/visualstudio/install/uninstall-visual-studio?view=vs-2022).

Deleting the app files does not delete transcripts saved outside those folders. Delete unwanted TXT files separately from the output folder you selected.


## License

The original app code is available under the [MIT license](LICENSE.txt). Third-party tools and models retain their own licenses and terms;

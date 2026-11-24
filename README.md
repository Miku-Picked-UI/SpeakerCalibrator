# Speaker Calibrator

Measures a speaker with the phone's microphone, or looks up the published measurements of your headphones, earbuds or speaker, and makes an [AxionFx](https://github.com/Miku-Picked-UI) preset in the sound style you pick (Studio, Warm, Big party, Bass head, Vocal, Like speakerheadphone).

- **Look up a model:** type the model and pick it. Headphones and earbuds come from [AutoEq](https://github.com/jaakkopasanen/AutoEq) (the raw curve and the target it was measured against), speakers from [spinorama.org](https://www.spinorama.org) (the inverse of its automatic EQ plus the bass extension). The model list is downloaded once and kept for 14 days; nothing is bundled.
- Headphones get their own version of each style: sub-bass on the FIR EQ's 25/40 Hz bands, and gentler highs since they play right at the ear (peaks are cut, dips only nudged).

- Plays an exponential sine sweep to the media output and records it, then deconvolves it (Farina) into the speaker's response.
- Runs 1, 3 or 5 tests, with a countdown between them so you can move the phone a little. The tests are averaged to smooth out noise and the room.
- Choose the bottom mic, the top (earpiece) mic, or both.
- Solves the Equalizer app's 9 bands against exact models of AxionFx's EQs, and cuts the FIR EQ below what the speaker can play.
- Saves `Download/AxionFx/<name> <style>.json`. Import it in AxionFx → Presets → Import.

Part of Miku-Picked UI (`vendor/miku/picked/speaker_cal`), where it builds as `PickedSpeakerCal`.

## Download

Get the APK from [Releases](../../releases). Android 11+.

## Build

- In a ROM tree: `Android.bp` (`android_app` PickedSpeakerCal).
- Standalone: `./build-apk.sh out.apk`. This needs Android SDK build-tools 36, a JDK and an `android.jar` (set `ANDROID_SDK`, `JDK`, `ANDROID_JAR`).

## License

Apache-2.0. Measurement data is fetched at runtime from AutoEq (MIT) and spinorama.org (CC BY-NC-SA 4.0) and stays theirs.

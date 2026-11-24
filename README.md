# Speaker Calibrator

Measures a speaker with the phone's microphone and makes an [AxionFx](https://github.com/Miku-Picked-UI) preset in the sound style you pick (Studio, Warm, Big party, Bass head, Vocal).

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

Apache-2.0

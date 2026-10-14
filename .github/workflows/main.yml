name: Flutter APK Derleme
on: [push]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Proje Klasorlerini Otomatik Olustur
        run: |
          mkdir -p lib
          cat << 'EOF' > pubspec.yaml
          name: ai_video_editor
          description: 4 Dk AI Video Editor
          version: 1.0.0+1
          environment:
            sdk: '>=3.0.0 <4.0.0'
          dependencies:
            flutter:
              sdk: flutter
            ffmpeg_kit_flutter_new: ^4.6.7
            file_picker: ^8.0.0
            path_provider: ^2.1.1
            video_player: ^2.8.2
          EOF
          if [ -f main.dart ]; then
            mv main.dart lib/main.dart
          fi
      - uses: subosito/flutter-action@v2
        with:
          channel: 'stable'
      - run: flutter pub get
      - run: flutter build apk --release --no-pub
      - name: APK'yı Yuklenebilir Dosya Yap
        uses: actions/upload-artifact@v3
        with:
          name: ai-video-editor-apk
          path: build/app/outputs/flutter-apk/app-release.apk

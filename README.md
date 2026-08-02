[README.md](https://github.com/user-attachments/files/30640590/README.md)
# bgmsiteconvert
bgmsiteconvert
# BGM JSON Converter

YouTube BGM Manager와 TRPG Watch의 JSON 내보내기 파일을 브라우저에서 양방향 변환하는 정적 웹사이트입니다.

## 기능

- JSON 파일 업로드 또는 직접 붙여넣기
- 입력 형식 자동 감지
- YouTube BGM Manager → TRPG Watch
- TRPG Watch → YouTube BGM Manager
- 변환 결과 복사 및 다운로드
- 서버 전송 없이 브라우저에서만 처리
- GitHub Pages 배포 가능

## 변환 기준

### YouTube BGM Manager → TRPG Watch

- `folders` → `scenarios`
- `songs[].youtube_url` → `scenarios[].bgm[].id`
- `songs[].title` → `bgm[].title`
- `songs[].memo` → `bgm[].memo`
- 한 곡이 여러 폴더에 속하면 각 시나리오에 복제
- 태그, 썸네일, 원본 URL, 폴더 경로는 선택 시 메모 속 메타데이터로 보존

### TRPG Watch → YouTube BGM Manager

- `scenarios` → `folders`
- `bgm[].id` → YouTube URL 및 썸네일 URL
- 같은 영상 ID가 여러 시나리오에 있으면 한 곡의 여러 `folder_paths`로 병합 가능
- `loop`, `sfx` 정보는 선택 시 태그 및 메모 속 메타데이터로 보존

## GitHub Pages 배포

1. GitHub에서 새 저장소를 만듭니다.
2. 이 폴더의 `index.html`과 `README.md`를 저장소 루트에 올립니다.
3. 저장소의 **Settings → Pages**로 이동합니다.
4. **Deploy from a branch**를 선택합니다.
5. Branch를 `main`, 폴더를 `/ (root)`로 선택하고 저장합니다.
6. 잠시 후 표시되는 Pages 주소로 접속합니다.

## 주의

두 앱의 JSON 스키마는 완전히 같지 않습니다. 상대 형식에 없는 값은 `[[BGM-CONVERTER-META]]`로 시작하는 메모 줄에 저장하여 재변환 시 최대한 복원합니다.

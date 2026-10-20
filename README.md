# Jehun Lee — Research Homepage

Jehun Lee의 VLSI Design 및 Efficient AI 연구를 소개하는 영문 홈페이지입니다.
GitHub Pages와 Jekyll Minimal 테마를 사용합니다.

사이트 주소: <https://jhlee2314.github.io/>

## 파일 구성

| 파일 | 내용 |
| --- | --- |
| `_config.yml` | 사이트 제목, 설명, URL, 테마 설정 |
| `index.md` | 소개, 연구 관심사, 대표 논문, 설계·측정 경험 |
| `publications.md` | 학회 논문 7편과 저널 논문 1편 |
| `cv.md` | 학력, 연구 기여, 장학금, 활동 |
| `assets/css/style.scss` | 글꼴, 링크, 모바일 화면 스타일 |

페이지 내용은 `jehun-lee-github-pages-guide.md`를 기준으로 작성했습니다.
안내서, `AGENTS.md`, 원본 `photo.jpg`는 사이트 빌드에서 제외됩니다.

## GitHub Pages 배포

저장소의 **Settings → Pages**에서 **Deploy from a branch**, **main**, **/(root)**를 선택합니다.
사이트 파일을 `main`에 커밋하고 푸시하면 Pages 빌드가 실행됩니다.
**Actions**에서 성공 여부를 확인한 뒤 Home, Publications, CV 페이지를 확인하세요.
Jekyll을 사용하므로 `.nojekyll` 파일을 추가하지 않습니다.

## 로컬 빌드 및 미리보기

Docker가 설치되어 있으면 GitHub 공식 Pages 빌드 이미지로 검증할 수 있습니다.

```sh
docker run --rm \
  --user "$(id -u):$(id -g)" \
  --entrypoint bundle \
  -e BUNDLE_GEMFILE=/Gemfile \
  -e JEKYLL_ENV=production \
  -v "$PWD:/site" -w /site \
  ghcr.io/actions/jekyll-build-pages:v1.0.13 \
  exec jekyll build --source /site --destination /site/_site

python3 -m http.server 4000 --bind 127.0.0.1 --directory _site
```

브라우저에서 <http://127.0.0.1:4000>을 열어 확인합니다.
수정 후에는 빌드를 다시 실행합니다. `_site/`는 자동 생성되며 Git에 포함하지 않습니다.

## 콘텐츠 수정

논문 제목, 저자 순서, 학력, 기여 내용은 확인된 자료를 기준으로 수정하세요.
PRESTE의 발표 상태를 바꿀 때는 `index.md`와 `publications.md`를 함께 갱신합니다.
현재 사진과 다운로드용 CV PDF는 연결하지 않았습니다.

사진을 추가할 때는 `assets/images/profile.jpg`에 저장하고 `_config.yml`에 다음 설정을 추가합니다.

```yaml
logo: /assets/images/profile.jpg
```

CV PDF는 실제 파일을 `assets/files/jehun-lee-cv.pdf`에 추가한 뒤 `cv.md`에서 연결합니다.

## 확인 항목

- Home, Publications, CV 사이의 메뉴 이동
- 이메일, Google Scholar, DOI 링크 대상
- 논문 8편과 CV의 내용 및 날짜
- 데스크톱과 모바일에서 긴 제목·링크의 줄바꿈
- 사진이나 PDF를 추가한 경우 표시 및 다운로드

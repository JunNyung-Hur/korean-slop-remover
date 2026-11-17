# korean-slop-remover

AI로 글을 쓰다 보면 문법은 맞는데 읽자마자 "AI가 썼구나" 싶은 글이 자주 나옵니다. 굵은 한 줄 슬로건, "~하고 ~하고 ~하고" 같은 나열, 긴 하이픈, 번역투, 독자가 궁금하지도 않은 내부 동작 설명 같은 것들입니다.

이 스킬은 그런 글을 걷어내고, 사람이 그 자리에서 실제로 쓸 법한 한국어 글을 쓰도록 돕기 위해 만들었습니다. README나 공지, 릴리즈 노트를 쓸 때는 물론이고, 이슈 댓글이나 커밋 메시지, 화면 문구, 평소 대화 답변에도 같은 기준이 적용됩니다.

## 예시

글의 종류별로 고치기 전과 후를 하나씩 골랐습니다.

| 글의 종류 | 고치기 전 | 고친 후 |
|---|---|---|
| 화면 문구 | 방금 이 창을 새로고침했거나 닫았다면 잠시 기다려 주세요. 20초쯤 뒤에 이어서 녹음할 수 있는 화면으로 바뀌어요. | 실수로 새로고침했다면 20초만 기다려주세요. 이어서 녹음할 수 있습니다. |
| 사용 안내 | 이 안내가 보인 뒤에는 창을 닫으셔도 회의록 준비가 계속 진행됩니다. | 이 안내가 보인 뒤에는 창을 닫으셔도 안전합니다. |
| 이슈 | 지금은 첨부 파일 크기를 프론트엔드에서만 확인한다. 그런데 서버는 따로 확인하지 않는다. 그래서 API를 직접 부르면 큰 파일도 올라간다. | 첨부 파일 크기는 지금 프론트엔드에서만 확인하고 서버는 따로 확인하지 않아서, API를 직접 부르면 몇 GB짜리 파일도 그대로 올라간다. |
| 기술 문서 | 문서를 조각으로 자른 뒤 뜻 벡터로 바꿔 서랍에 넣어 둔다. | 문서를 청크로 나눠 임베딩한 뒤 벡터 DB에 저장한다. |
| 대화 답변 | README를 수정했습니다. 요청하신 대로 3번 섹션을 분리하고 사진마다 설명을 추가했습니다. 변경 내용은 다음과 같습니다. | 3번을 "회의록 확인"과 "공유"로 나눴고, 사진마다 바로 아래에 그 화면에서 볼 것을 적었습니다. |

왜 그렇게 고쳤는지까지 적은 예시 28개는 [examples.md](skills/korean-slop-remover/references/examples.md)에 있습니다.

## 설치

Claude Code에서 플러그인으로 설치하시려면 아래 두 명령을 차례로 실행하시면 됩니다.

```
/plugin marketplace add JunNyung-Hur/korean-slop-remover
/plugin install korean-slop-remover@junnyung-hur
```

Codex, Cursor 같은 다른 에이전트에서도 쓰고 싶으시다면 터미널에서 아래 명령으로 설치하실 수 있습니다. 설치할 에이전트를 고르는 안내가 함께 나옵니다.

```
npx skills add JunNyung-Hur/korean-slop-remover
```

## 사용법

설치한 뒤에는 한국어 글을 쓰거나 다듬어 달라고 하면 자동으로 적용됩니다.

직접 부르고 싶으시면 "korean-slop-remover로 이 글 다듬어 줘"처럼 말씀하시면 됩니다.

## 수정 기준

[이슈](skills/korean-slop-remover/references/types/issue.md), [PR](skills/korean-slop-remover/references/types/pr.md), [README](skills/korean-slop-remover/references/types/readme.md), [릴리즈 노트](skills/korean-slop-remover/references/types/release-notes.md), [블로그](skills/korean-slop-remover/references/types/blog.md), [기고문](skills/korean-slop-remover/references/types/column.md), [뉴스](skills/korean-slop-remover/references/types/news.md), [발표 장표](skills/korean-slop-remover/references/types/presentation.md), [연구 보고서](skills/korean-slop-remover/references/types/research.md)는 구성과 말투가 서로 달라서 문서 종류별 기준을 따로 정리해 두었습니다.

글의 종류와 상관없이 공통으로 보는 기준은 [SKILL.md](skills/korean-slop-remover/SKILL.md)에 있습니다.

## 의견 제보

이 스킬은 실제로 글을 고치면서 받은 지적을 모아 만들었습니다.

쓰시다가 어색한 결과가 나오면 고치기 전 문장과 원하는 문장을 이슈로 남겨 주세요. 기준과 예시에 반영하겠습니다.

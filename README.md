# WebFFT

웹에서 가장 빠른 푸리에 변환 라이브러리!

[체험하기](https://webfft.com/)
[문서](https://webfft.com/docs)

GitHub 이슈와 PR을 통해 피드백을 환영합니다!

------

## 개요

**WebFFT**는 JavaScript와 WebAssembly 기반의 다양한 FFT(Fast Fourier Transform) 라이브러리를 포함하는 메타 라이브러리입니다. 이들을 "서브 라이브러리"라고 칭합니다.
기본적으로 특정 서브 라이브러리가 사용되지만, 아래 명령어를 실행하면:

```
javascript코드 복사import webfft from "webfft";
const fft = new webfft(1024);
fft.profile(); // (선택적) 프로파일링 시간을 초 단위로 설정 가능
```

모든 서브 라이브러리를 벤치마킹하고, 이후 가장 효율적인 서브 라이브러리를 선택하여 호출에 사용합니다.
라이브러리를 임포트할 때 WebAssembly(Wasm)가 지원되는지 확인하므로, 프로파일러와 기본 라이브러리는 이에 따라 사용할 풀(pool)을 결정합니다.

------

## 기본 사용법

```
javascript코드 복사const webfft = require('webfft');

// FFT 인스턴스 생성
const fftsize = 1024; // 2의 제곱수여야 함
const fft = new webfft(fftsize);

// 프로파일링
const profileResults = fft.profile(); // 결과 객체로 벤치마크 시각화 가능

// 입력 데이터 생성
const input = new Float32Array(2048); // 복소수 배열 (IQIQIQIQ...), 크기는 두 배여야 함
input.fill(0);

// FFT 실행
const out = fft.fft(input); // 결과는 크기 2048의 Float32Array 반환
// 또는
const out = fft.fft(input, 'kissWasm');

fft.dispose(); // Wasm 메모리 해제
```

------

## 2D FFT 지원

WebFFT는 2D FFT도 지원합니다.
입력 데이터는 배열의 배열 형태로 구성되며, 내부 배열 길이는 `2 * size`이고 외부 배열 길이는 2의 제곱수여야 하지만, 내부 배열 길이와 일치할 필요는 없습니다.

```
javascript코드 복사import webfft from "webfft";

const fftsize = 1024;
const outterSize = 128;
const fft = new webfft(fftsize);
let inputArr = [];
for (let j = 0; j < outterSize; j++) {
  const subArray = new Float32Array(fftsize * 2);
  for (let i = 0; i < fftsize * 2; i++) {
    subArray[i] = i * j * 1.12312312; // 임의의 값
  }
  inputArr.push(subArray); // 내부 배열 추가
}
const out = fft.fft2d(inputArr);

fft.dispose(); // Wasm 정리
```

------

## 기타 참고사항

- 사이트 배포는 `cd site && npm run deploy`를 실행하고, GitHub Pages 설정에서 "deploy from a branch" 옵션을 선택한 후 `gh-pages` 브랜치를 지정해야 합니다.
  `npm run deploy`는 gh-pages 명령을 실행하며, 기본적으로 사이트를 `gh-pages` 브랜치에 게시합니다.
- 실수형 입력 데이터를 다룰 때는 `fftr()`를 사용하십시오. 결과는 여전히 복소수이지만, 양수 주파수만 반환됩니다.

------

궁금한 점이 있다면 말씀해주세요!
[WebFFT 공식 웹사이트](https://webfft.com/)를 방문하세요.

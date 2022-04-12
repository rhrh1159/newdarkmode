# DArkMode 제작하기

## Prettier 설정하기
root폴더에 `.prettierrc`파일을 생성한다.
```
{
    "arrowParens": "always",
    "semi": true,
    "singleQuote": false,
    "trailingComma": "all",
    "tabWidth": 2,
    "printWidth": 80
}
```

## Json파일을 활용하여 import 설정하기
root폴더에 `jsconfig.json`
```
{
    "compilerOptions": {
        "target": "es6",
        "baseUrl": "src"
    },
    "include": ["src"]
}
```
## src폴더 내에 `index.css`에서 폰트 설정 및 여백 설정을 한다.
```
@import url('https://fonts.googleapis.com/css2?family=Jua&family=Nanum+Gothic:wght@400;700&display=swap');
body {
  margin: 0;
  padding: 0;
  font-family: 'Jua', sans-serif;

  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
*{
  margin: 0;
  padding: 0;
  box-sizing: inherit; /*상속받겠다 (부모요소로부터)*/
}
```

## src폴더 내에 'theme'

```
export const lighTheme = {
    bgColol : "#fff",
    textColor : "#000",
    headerColor : "#000",
    headerTextColor : "#fff"
}

export const darkTheme = {
    bgColol : "#000",
    textColor : "#fff",
    headerColor : "#fff",
    headerTextColor : "#000"
}
```
## ThemeProvider를 이용하여 테마를 전체 감싸서 다크모드 효과 적용
상단에 import
```
import { ThemeProvider } from 'styled-components';
```
```
    <ThemeProvider theme={toggle ? darkTheme : lightTheme}>
      <DarkMode onToggle={onToggle} toggle={toggle}/>
    </ThemeProvider>
  );
```

## 스타일컴포넌트 작성시 태그 이회의 스타일을 적용 시켜줄 때는 소괄호를 사용
```
//html 태그 이외의 스타일을 꾸며줄 때 소괄호()로 묶어서 사용
const DarkButton = styled(MdDarkMode)`
    cursor: pointer;
    color: ${(props) => props.theme.headerTextColor};
    font-size: 30px;
`;
const LightButton = styled(MdOutlineDarkMode)`
    cursor: pointer;
    color: ${(props) => props.theme.headerTextColor};
    font-size: 30px;
`;


```


# 지하댐 설치 효과 정량적 평가 프로그램

1. 기저 유량 분리 프로그램(baseflow)의 EXCEL VBA 구현

2. 지하댐 설치 효과 정량적 평가 프로그램 (한국농어촌공사 농어촌연구원) (EXCEL VBA)

   

## 프로그램 설명

### 프로그램 구현목적

#### 1. baseflow 프로그램

this program estimates groundwater contributions from USGS streamflow records.  It uses a recursive filter technique to seperate base flow and also calculates the streamflow recession constant (alpha)

#### 2. 지하댐 설치효과 평가 프로그램

지하댐 사업 초기 제안 과정에서 개략적인 지하댐 설치 효과 분석을 위해 개발 

### 주요 매개 변수

#### 1. baseflow

- `NDMin` As Long:  (days) minimum number of days for alpha calculation
- `NDMax` As Long:  (days) maximum number of days for alpha calculation
- `Dates()` As Date: 날짜
- `NDays` As Long:-  number of days of flow data
- `StrFlow()` As Double: Baseflow 연산의 입력에 사용되는 유량(CMS). 
- `BaseQ()` As Double: (CMS) 기저유출. BaseQ(pass, :)는 각 pass에 해당.
- `BFlw_fr1` As Double: fraction of streamflow that is base flow estimated by first pass
- `BFlw_fr2` As Double: fraction of streamflow that is base flow estimated by second pass
- `BFlw_fr3` As Double: fraction of streamflow that is base flow estimated by third pass
- `NPR` As Long: total number of base flow recessions (all the recessions are combined to compute the master recession curve)
- `AlF` As Double: alpha factor for groundwater recharge
- `BfD` As Double: baseflow days for groundwater recharge

#### 2. 지하댐 설치효과 평가 프로그램

- `SelectedBaseflowPass` As Integer: baseflow pass 선택
- `EnvArea` As Double: (km^2) 환경부 유량관측소 유역면적
- `SDamArea` As Double: (km^2) 지하댐 유역면적
- `SDAMAreaRatio` As Double: 유역 면적비 (지하댐 상부의 유역면적 / 하류 관측점 상부의 유역면적)
- `SDamHeight` As Double: (m) 지하댐 제고
- `SDamLength` As Double: (m) 지하댐 제장
- `SDamSlopeInP` As Double: (%) 지하댐 하상경사
- `SDamSlopeInD` As Double: (°) 지하댐 하상경사
- `Precp()` As Double: 강수량(mm)
- `isQNA()` As Boolean: 일계열 관측 유출량이 NA 자료인지의 여부. 기본값(=false= not NA).
- `SDamTEffLength` As Double: (km) 지하댐 영향거리(이론)
- `SDamREffLength` As Double: (km) 지하댐 영향거리(실제)
- `SDAMEffLengthRatio` As Double: 영향거리비 (경험치로 적용함)
- `SDAMGWLDelta` As Double: (m) 실제지하수위변화
- `SDAMEffArea` As Double: (m^2) 영향면적
- `SDAMEffVolume` As Double: (m^3) 영향체적
- `SDAMEffVolumeDelta` As Double: (cu.m) 영향체적변동
- `SDAMGWLRaiseRatio` As Double: (%) 지하수위 상승률

### 참조

+ Arnold, J.G., P.M. Allen, R. Muttiah, and G. Bernhardt. 1995. Automated base flow separation and recession analysis techniques. Ground Water 33(6): 1010-1018.

+ Arnold, J.G. and P.M. Allen. 1999. Automated methods for estimating baseflow and ground water recharge from streamflow records. Journal of the American Water Resources Association 35(2): 411-424.

+ (주)에스디엠이앤씨, 2020, 지하댐설치효과 정량적 프로그램 개발(한국농어촌공사 농어촌연구원)



## Project Info

### Version

- Last updated Nov. 2020

### Dev Tools

+ Microsoft Excel / VBA

### Environments

+ Test Environment

    + Microsoft Windows 10 (x64)
    
+ Dependencies / 3rd-party package(s)

    + None



## License

![CCBYNCND](https://i.creativecommons.org/l/by-nc-nd/3.0/88x31.png) 이 저작물은 <a rel="license" href="http://creativecommons.org/licenses/by-nc-nd/3.0/deed.ko">크리에이티브 커먼즈 저작자표시-비영리-변경금지 3.0 Unported 라이선스</a>에 따라 이용할 수 있습니다.

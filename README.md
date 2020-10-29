# 지하댐 설치 효과 정량적 평가 프로그램

1. *기저 유량 분리 프로그램 (baseflow[^1]의 VBA 구현)*



   *(FORTRAN to VBA)*

1. *지하댐 설치 효과 정량적 평가 프로그램*



## BASEFLOW

### 참조
> + Arnold, J.G., P.M. Allen, R. Muttiah, and G. Bernhardt. 1995. Automated base flow separation and recession analysis techniques. Ground Water 33(6): 1010-1018.
> + Arnold, J.G. and P.M. Allen. 1999. Automated methods for estimating baseflow and ground water recharge from streamflow records. Journal of the American Water Resources Association 35(2): 411-424.

### 프로그램 구현 목적
this program estimates groundwater contributions from USGS streamflow records.  It uses a recursive filter technique to seperate base flow and also calculates the streamflow recession constant (alpha)

### 주요 변수 설명 (변수명 / 단위 / 설명)
- `alf` / none / alpha factor for groundwater recharge
- `alpha(:)` / none / slope of the baseflow recession
- `amn` / cms / minimum flow in recession
- `aveflo(:)` / cms / average flow during the computation of the master recession curve; these values are used to fill in any ranges of flow that are not contained in any of the recession curves
- `baseq(:,:)` / cms / base flow
  - `baseq(1,:)` / cms / base flow calculated in first pass
  - `baseq(2,:)` / cms / base flow calculated in second pass
  - `baseq(3,:)` / cms / base flow calculated in third pass
- `bfd` / days / baseflow days for groundwater recharge
- `bfdd(:)` / days / baseflow days for a recession
- `bflw_fr1` / none / fraction of streamflow that is base flow estimated by first pass
- `bflw_fr2` / none / fraction of streamflow that is base flow estimated by second pass
- `bflw_fr3` / none / fraction of streamflow that is base flow estimated by third pass
- `date_` / none / date as a string YYYYMMDD
- `eof_` / none / end of file flag: -1 (not 0 in VBA) when end of file is reached
- `eof1_` / none / end of file flag: -1 (not 0 in VBA) when end of file is reached
- `f1` / none / equation coefficient
- `f2` / none / equation coefficient
- `florec(:,:)` / cms / flow rates during the base flow recession. argument 1 is the day within the recession. argument 2 is the recession number
- `flwfile` / NA / name of file containing USGS flow data
- `flwfileo` / NA / name of output file for daily baseflow values
- `i` / none / counter
- `icount(:)` / none / keeps track of where the smallest flow recession curve falls on the x axis (day line)
- `idone(:)` / none / used to identify the recession curve with the lowest flow value
- `iday(:)` / none / day in month of flow record
- `igap` / none / variable to skip/perform calcs for gaps in flow
- `iprint` / none / daily printout code: 0 do not print daily values, 1 print daily values
- `isumd` / none / number of records processed
- `iyr(:)` / none / year of flow record
- `j` / none / counter
- `jday(:)` / none / julian date of flow record
- `k` / none / store array location value
- `leapyr` / none / leap year flay (0 is leap year/1 isn't leap year)
- `mon(:)` / none / month of flow record
- `nd` / days / number of days in current recession analysis
- `ndays` / none / number of days of data in USGS flow file
- `ndmax` / days / maximum number of days for alpha calculation
- `ndmin` / days / minimum number of days for alpha calculation
- `ndreg(:)` / days / number of days during base flow recession number i
- `now_` / none / array location in florec of the smallest flow
- `np` / none / number of recessions used to calculate alpha and y intercept
- `npr` / none / total number of base flow recessions (all the recessions are combined to compute the master recession curve)
- `npreg(:)` / none / number of points on the master recession curve
- `nregmx` / none / number of baseflow recessions per year that are used in the master recession curve regression
- `qaveln(:)` / cms / Log(average flow) for a recession
- `q0(:)` / cms / flow at start of the base flow recession
- `q10(:)` / cms / flow at the end of the base flow recession
- `sflow` / cms / USGS streamflow value for record
- `slope` / none / slope of baseflow recession curve
- `ssxx` / none / intermediate calc.
- `ssxy` / none / intermediate calc.
- `strflow(:)` / cms / USGS streamflow value for record
- `sumbf1` / cms / sum of baseflow values calculated by pass 1 for entire period of record
- `sumbf2` / cms / sum of baseflow values calculated by pass 2 for entire period of record
- `sumbf3` / cms / sum of baseflow values calculated by pass 3 for entire period of record
- `sumstrf` / cms / sum of streamflow values for period of record
- `sumx` / none / intermediate calc.
- `sumx2` / none / intermediate calc.
- `sumxy` / none / intermediate calc.
- `sumy` / none / intermediate calc.
- `surfq(:)` / cms / streamflow from surface runoff
- `titldum` / NA / variable used to process unimportant lines
- `x` / none / icount value expressed as real number
- `yint` / none / y intercept for baseflow regression curve 



## Project Info

### Version

- Last updated Oct. 2020

### Dev Tools

+ Microsoft Excel / VBA

### Environments

+ Test Environment

    + Microsoft Windows 10 (x64)
    
+ Dependencies / 3rd-party package(s)

    + None



## License

+ MIT License



[^1]: 111
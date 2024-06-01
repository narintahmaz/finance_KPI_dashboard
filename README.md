# finance_KPI_dashboard

https://github.com/narintahmaz/finance_KPI_dashboard/assets/136226603/eeb8ed88-efab-4f66-aca8-e0f3d2b03054

   Vizuallaşdıracağım malliyyə məlumatları 4 müxtəlif cədvəldən gəlir .Bunlardan biri hər satıcının hər ay nə qədər satış etdiyini göstərən  cədvəldir .Digər cədvəl isə hər işçinin hər ay üçün  çatmalı olduqları satış hədəfinin miqdarını göstərən cədvəldir .
   Bu 2 əsas cədvəldən başqa  2 dimension cədvəl də var ki , bu cədvəllərdən biri “calendar” cədvəlidir burada müvafiq aylar göstərilib .Digər cədvəl isə satış komandası ilə bağlı məlumatları əks etdirir.
  “ Clustered column chart” tipində yaratdığım qrafikdə hər ay üzrə edilmiş satışın ümumi miqdarı və  satış hədəfinin ümumi miqdarı müqayisə edilir.Bu qrafikdən görünür ki, digər aylara nibətən daha çox  2023-cü ilin  Mart və İyul aylarında edilmiş satış miqdarı  qarşıya qoyulmuş hədəf satış miqdarını keçib .
  Table tipində olan ikinci qrafikdə isə hər satıcının etdiyi ümumi satış ,ümumi hədəf satışı və bu satışlar arasındakı fərqi göstərir.
   Slicer(new) tipində olan üçüncü qrafikdə isə satış komandalarını əlavə etmişəm. 





İstifadə etdiyim dax hesablamaları 
1) Total Sales Actual = Sum(Actual[Sales]) 
2) Total Sales Target = sum(Targets[Sales]) 
3) Variance = [Total Sales Actual]-[Total Sales Target]
4) Variance % = DIVIDE([Variance],[Total Sales Target]) 
5) Variance Pct Label = 
var up="🟢"
var down="🔴"
var  formatted_var_pct= FORMAT(ABS([Variance %]),"0.0%")
RETURN
formatted_var_pct& " " & IF([Variance %]>0,up,down)




6) Trend Chart Title = 
   var month_count=COUNTROWS('Calendar')
   return 
   "We met targets for " &[Month Target Reached]& "out of" & month_count & "months"

7) Month Target Reached = 
Var month_target_reached=Filter('Calendar',[Variance]>0)
RETURN
COUNTROWS(month_target_reached)





### <a name="null-coalescer-values-are-not-visible-in-debugger-until-one-step-later"></a>Null coalescer değerleri daha sonra bir adıma kadar hata ayıklayıcıda görünür değildir

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.5 hatada Framework'ün 64 bit sürümünde çalıştırırken atama işlemi hemen yürütüldükten sonra hata ayıklayıcısı'ndaki görünür olmasını kümesi null bir birleştirmesi işlemi değerleri neden olur.|
|Öneri|Hata ayıklayıcı ek bir kerelik atlama doğru güncelleştirilmesi yerel/alanın değerini neden olur. Ayrıca, bu sorun .NET Framework 4.6 düzeltilmiştir; Framework'ün bu sürüme yükseltme sorunu çözecektir.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|Çalışma zamanı|


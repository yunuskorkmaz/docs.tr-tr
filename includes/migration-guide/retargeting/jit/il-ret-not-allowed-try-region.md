### <a name="il-ret-not-allowed-in-a-try-region"></a>IL ret bir try bölgede izin verilmiyor

|   |   |
|---|---|
|Ayrıntılar|JIT64 tam zamanı derleyici bir IL ret bir try bölgede yönergesi (.NET 4.6 kullanılır) RyuJIT izin vermiyor. Try bölgesinden döndürme ECMA-335 belirtimi tarafından izin verilmeyen ve bu tür IL bilinen hiçbir yönetilen derleyici oluşturur. Ancak, yansıma kullanarak oluşturulursa JIT64 derleyici böyle IL yürütecek yayma.|
|Öneri|Bir uygulama bir try bölgede ret opcode içeren IL oluşturuyorsa, uygulamanın eski JIT kullanın ve bu sonu önlemek için .NET 4.5 hedefleyebilir. Alternatif olarak, oluşturulan IL deneyin bölge sonra dönmek için güncelleştirilebilir.|
|Kapsam|Kenar|
|Sürüm|4.6|
|Tür|Yeniden hedefleme|


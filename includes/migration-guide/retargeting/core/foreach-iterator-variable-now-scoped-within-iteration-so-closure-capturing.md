### <a name="foreach-iterator-variable-is-now-scoped-within-the-iteration-so-closure-capturing-semantics-are-different-in-c5"></a>Kapanış yakalama semantiği (C# 5'te) farklı olduğundan Foreach yineleyici değişkeni artık yineleme içinde kapsamı

|   |   |
|---|---|
|Ayrıntılar|C# 5 (Visual Studio 2012),'ten itibaren <code>foreach</code> yineleyici değişkenleri yineleme içinde kapsanır. Kod içinde dahil edilmemesi için değişkenleri daha önce bağlı, bunu sonu neden olabilir <code>foreach</code>kullanıcının thisanahtar. Bu değişikliğin bir temsilciye iletilen bir yineleyici değişkeni temsilci çağrıldığı zaman sahip değer yerine temsilci zaman sahip değer oluşturulur olarak kabul edilir belirtisidir.|
|Öneri|İdeal olarak, kodu yeni derleyici davranışı beklediğiniz şekilde güncelleştirilmesi gerekir. Eski semantiği gerekiyorsa, yineleyici değişkeni döngü kapsamı dışında açıkça yerleştirilir, ayrı bir değişken ile değiştirilebilir.|
|Kapsam|Büyük|
|Sürüm|4,5|
|Tür|Yeniden hedefleme|


### <a name="foreach-iterator-variable-is-now-scoped-within-the-iteration-so-closure-capturing-semantics-are-different-in-c5"></a>Kapatma yakalama semantiği (C# 5'te) farklı şekilde Foreach yineleyici değişken yineleme içinde artık kapsamlıdır

|   |   |
|---|---|
|Ayrıntılar|C# 5 (Visual Studio 2012 için), başlangıç <code>foreach</code> yineleyici değişkenler içinde yineleme kapsamına. Kodu önceden dahil edilmesini değil değişkenleri bağlı olarak, bu sonları neden olabilir <code>foreach</code>kullanıcının thisanahtar. Bu değişiklik temsilciye geçirilen bir yineleyici değişkeni temsilci aynı anda sahip değeri temsilci çağrılır aynı anda sahip değer yerine oluşturulur olarak kabul edilir belirtisidir.|
|Öneri|İdeal olarak, yeni derleyici davranış beklenir kod güncelleştirilmesi gerekir. Eski semantiğini gerekirse, yineleyici değişken döngünün kapsamı dışında açıkça yerleştirilen ayrı bir değişken ile değiştirilebilir.|
|Kapsam|Ana|
|Sürüm|4,5|
|Tür|Yeniden hedefleme|


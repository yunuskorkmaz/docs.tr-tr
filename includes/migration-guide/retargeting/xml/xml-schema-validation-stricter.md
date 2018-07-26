### <a name="xml-schema-validation-is-stricter"></a>XML şema doğrulama daha sıkı

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.5, XML şema doğrulama daha katıdır. mailto protokolü gibi bir URI öğesini doğrulamak için xsd:anyURI kullanıyorsanız, URI öğesinde boşluklar olduğundan doğrulama başarısız olur. .NET Framework'ün önceki sürümlerinde doğrulama başarılı oldu. Bu değişiklik, .NET Framework 4.5 hedefleyen yalnızca uygulamaları etkiler.|
|Öneri|Bazı .NET Framework 4.0 doğrulama gerekli değilse, doğrulama uygulama .NET Framework 4.0 sürümünü hedefleyebilirsiniz. Ancak, .NET Framework 4.5 olarak yeniden hedefleme, kod gözden geçirme (boşluk ile) geçersiz bir URI'leri beklenmiyordu, öznitelik değeri olarak anyURI veri türüne sahip olduğundan emin olmak için yapılmalıdır.|
|Kapsam|Küçük|
|Sürüm|4,5|
|Tür|Yeniden hedefleme|


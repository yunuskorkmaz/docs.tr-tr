### <a name="xml-schema-validation-is-stricter"></a>XML şema doğrulaması katı

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.5 XML şema doğrulaması daha katı. mailto protokolü gibi bir URI öğesini doğrulamak için xsd:anyURI kullanıyorsanız, URI öğesinde boşluklar olduğundan doğrulama başarısız olur. .NET Framework'ün önceki sürümlerinde doğrulama başarılı oldu. Değişiklik hedefleyen .NET Framework 4.5 yalnızca uygulamaları etkiler.|
|Öneri|Bazı .NET Framework 4.0 doğrulama gerekli olursa, doğrulama uygulama .NET Framework 4.0 sürümünü hedefleyebilirsiniz. Ancak, .NET 4.5 yeniden hedefleme, kod incelemesi (boşluklu) geçersiz bir URI değil beklenir, öznitelik değerleri anyURI veri türüne sahip olduğundan emin olmak için yapılmalıdır.|
|Kapsam|Küçük|
|Sürüm|4,5|
|Tür|Yeniden hedefleme|


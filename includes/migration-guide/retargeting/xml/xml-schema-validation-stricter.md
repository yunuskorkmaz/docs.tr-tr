### <a name="xml-schema-validation-is-stricter"></a>XML şema doğrulaması daha katı

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.5’te XML şema doğrulaması daha katıdır. mailto protokolü gibi bir URI öğesini doğrulamak için xsd:anyURI kullanıyorsanız, URI öğesinde boşluklar olduğundan doğrulama başarısız olur. .NET Framework'ün önceki sürümlerinde doğrulama başarılı oldu. Değişiklik yalnızca .NET Framework 4.5’i hedefleyen uygulamaları etkiler.|
|Öneri|Daha esnek .NET Framework 4.0 doğrulaması gerekiyorsa, doğrulanan uygulama .NET Framework 4.0 sürümünü hedefleyebilir. Ancak .NET Framework 4.5 yeniden hedeflenirken, geçersiz URI’lerin (boşluk içeren) anyURI veri türüne sahip öznitelik değerleri olarak beklenmediğinden emin olmak için kod incelemesi yapılmalıdır.|
|Kapsam|İkincil|
|Sürüm|4,5|
|Tür|Yeniden Hedefleme|


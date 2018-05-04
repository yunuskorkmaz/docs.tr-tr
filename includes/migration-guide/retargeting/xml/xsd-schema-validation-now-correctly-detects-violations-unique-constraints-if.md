### <a name="xsd-schema-validation-now-correctly-detects-violations-of-unique-constraints-if-compound-keys-are-used-and-one-key-is-empty"></a>XSD şema doğrulaması artık doğru bileşik anahtarlar kullanılır ve bir anahtar boşsa, benzersiz kısıtlamalar ihlalleri algılar

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6 önce sürümlerini anahtarlarından birini boşsa bileşik anahtarlar benzersiz kısıtlamalar algılamak değil XSD doğrulaması nedeniyle bir hata oluştu. .NET Framework 4.6 Bu sorun düzeltilmiştir. Bu daha doğru doğrulama neden olacak, ancak daha önce sahip doğrulanıyor olmayan bazı XML'de sonuçlanabilir.|
|Öneri|Bazı .NET Framework 4.0 doğrulama gerekli olursa, doğrulama uygulama sürüm 4.5 (veya öncesi) hedefleyebilirsiniz .NET Framework'ün. Ancak, .NET Framework 4.6 yeniden hedefleme, kod incelemesi yinelenen bileşik anahtarlar (Bu sorunun açıklamasında açıklandığı gibi) doğrulama beklenmez olduğundan emin olmak için yapılmalıdır.|
|Kapsam|Kenar|
|Sürüm|4.6|
|Tür|Yeniden hedefleme|


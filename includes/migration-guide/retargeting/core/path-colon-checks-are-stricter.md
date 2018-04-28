### <a name="path-colon-checks-are-stricter"></a>Yol iki nokta üst üste denetimleri katı

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6.2, daha önce desteklenmeyen yolları (hem uzunluğu ve biçim) desteklemek için birkaç değişiklik yapıldı. Uygun sürücü ayırıcı (iki nokta üst üste) sözdizimi denetimlerinin, bunlar kabul edileceği kullanıldığı birkaç select yolu API'lerde bazı URI yolları engelleme yan etkisi olan daha doğru yapıldı.|
|Öneri|Bir URI etkilenen API'lerine geçirilirse, geçerli bir yol ilk olarak dizesini değiştirin.<ul><li>Düzen URL'lerden el ile kaldırın (örneğin kaldırmak <code>file://</code> URL'lerden)</li><li>URI geçirmek <xref:System.Uri> sınıfı ve kullanma <xref:System.Uri.LocalPath></li></ul>Alternatif olarak, ayarlayarak dışında yeni yol normalleştirme tercih edebilirsiniz <code>Switch.System.IO.UseLegacyPathHandling</code> AppContext anahtar true.|
|Kapsam|Kenar|
|Sürüm|4.6.2|
|Tür|Yeniden hedefleme|
|Etkilenen API'leri|<ul><li><xref:System.IO.Path.GetDirectoryName(System.String)?displayProperty=nameWithType></li><li><xref:System.IO.Path.GetPathRoot(System.String)?displayProperty=nameWithType></li></ul>|


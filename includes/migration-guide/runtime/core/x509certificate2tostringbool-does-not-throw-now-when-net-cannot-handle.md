### <a name="x509certificate2tostringbool-does-not-throw-now-when-net-cannot-handle-the-certificate"></a>X509Certificate2.ToString(bool) şimdi .NET sertifika ne zaman işleyemiyor throw

|   |   |
|---|---|
|Ayrıntılar|Daha önce bu yöntem, throw <code>true</code> ayrıntılı parametresi için geçirilen ve vardı yüklü olan ve .NET Framework tarafından desteklenen doğru sertifikalar. Şimdi, yöntem başarılı ve sertifika erişilemez bölümlerini atlar geçerli bir dize döndürür.|
|Öneri|Bağlı olarak kod <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)> döndürülen dize bazı sertifika verileri (örneğin, ortak anahtar, özel anahtarı ve uzantıları) dışarıda bırakılabilir, API daha önce oluşturulan bazı durumlarda beklenir güncelleştirilmesi.|
|Kapsam|Kenar|
|Sürüm|4.6|
|Tür|Çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType></li></ul>|


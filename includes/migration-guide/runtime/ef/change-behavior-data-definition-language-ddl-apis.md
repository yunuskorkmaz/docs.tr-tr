### <a name="change-in-behavior-in-data-definition-language-ddl-apis"></a>Davranış veri tanımlama dili (DDL) API'leri olarak değiştirme

|   |   |
|---|---|
|Ayrıntılar|DDL AttachDBFilename belirtildiğinde API'leri davranışını aşağıdaki gibi değişmiştir:<ul><li>Bağlantı dizeleri bir ilk katalog değerinin belirtmeniz gerekmiyor. Daha önce AttachDBFilename ve ilk katalog gerekiyordu.</li><li>AttachDBFilename ve ilk katalog belirtilir ve verilen MDF dosyası, varsa <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A> yöntemi döndürür <code>true</code>. Daha önce döndürülen <code>false</code>.</li><li>AttachDBFilename ve ilk katalog belirtilir ve verilen MDF dosyası, arama varsa <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A> yöntemi dosyaları siler.</li><li>Varsa <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A> AttachDBFilename değer mevcut olmayan bir MDF ile bağlantı dizesini belirtir ve bir ilk mevcut olmayan katalog, yöntem adlı bir <xref:System.InvalidOperationException> özel durum. Daha önce belirtti bir <xref:System.Data.SqlClient.SqlException> özel durum.</li></ul>|
|Öneri|Bu değişiklikler, DDL API'larını kullanan araçlar ve uygulamalar oluşturmayı kolaylaştırır. Bu değişiklikler, aşağıdaki senaryolarda uygulama uyumluluğunu etkileyebilir:<ul><li>Kullanıcı yürütülen kodu Yazar bir <code>DROP DATABASE</code> doğrudan çağırmak yerine komutunu <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A> varsa <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A> döndürür <code>true</code>. Bu, veritabanı bağlı olmadığında, ancak MDF dosyası mevcut olduğunda mevcut kodu kırar.</li><li>Kullanıcı bekliyor kod yazar <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A> throw yöntemi bir <xref:System.Data.SqlClient.SqlException> yerine bir <xref:System.InvalidOperationException> zaman yok ilk katalog ve MDF dosyası yok.</li></ul>|
|Kapsam|Küçük|
|Sürüm|4,5|
|Tür|Çalışma zamanı|


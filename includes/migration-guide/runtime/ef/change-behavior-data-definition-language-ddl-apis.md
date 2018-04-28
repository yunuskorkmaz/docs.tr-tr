### <a name="change-in-behavior-in-data-definition-language-ddl-apis"></a>Davranış veri tanımlama dili (DDL) API'leri olarak değiştirme

|   |   |
|---|---|
|Ayrıntılar|DDL AttachDBFilename belirtildiğinde API'leri davranışını aşağıdaki gibi değişmiştir:<ul><li>Bağlantı dizeleri bir ilk katalog değerinin belirtmeniz gerekmiyor. Daha önce AttachDBFilename ve ilk katalog gerekiyordu.</li><li>Verilen MDF dosyası AttachDBFilename ve ilk katalog belirtilir ve varsa ObjectContext.DatabaseExists yöntemi true değerini döndürür. Daha önce false döndürdü.</li><li>AttachDBFilename ve ilk katalog belirtilir ve verilen MDF dosyası varsa ObjectContext.DeleteDatabase yöntemini çağırarak dosyaları siler.</li><li>Bağlantı dizesi, mevcut olmayan bir MDF ve mevcut olmayan bir ilk katalog AttachDBFilename değeri belirttiğinde ObjectContext.DeleteDatabase çağrılırsa, yöntemi bir InvalidOperationException özel durum oluşturur. Daha önce bir SqlException özel durum oluşturdu.</li></ul>|
|Öneri|Bu değişiklikler, DDL API'larını kullanan araçlar ve uygulamalar oluşturmayı kolaylaştırır. Bu değişiklikler, aşağıdaki senaryolarda uygulama uyumluluğunu etkileyebilir:<ul><li>Kullanıcı ObjectContext.DatabaseExists true değerini döndürür, DROP DATABASE komutu doğrudan çağıran ObjectContext.DeleteDatabase yerine yürütülen kodu yazar. Bu, veritabanı bağlı olmadığında, ancak MDF dosyası mevcut olduğunda mevcut kodu kırar.</li><li>Kullanıcı ilk katalog ve MDF dosyası yok varken bir InvalidOperationException özel yerine bir SqlException özel durum için ObjectContext.DeleteDatabase yöntemi bekliyor kod yazar.</li></ul>|
|Kapsam|Küçük|
|Sürüm|4,5|
|Tür|Çalışma zamanı|


---
title: SQL Server’da Secure Dynamic SQL Yazma
ms.date: 03/30/2017
ms.assetid: df5512b0-c249-40d2-82f9-f9a2ce6665bc
ms.openlocfilehash: 236fd925740d37c2cccabfcebfb7fcb46361489d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61757722"
---
# <a name="writing-secure-dynamic-sql-in-sql-server"></a>SQL Server’da Secure Dynamic SQL Yazma
SQL ekleme, kötü niyetli bir kullanıcının geçerli giriş yerine Transact-SQL deyimleriyle girer işlemidir. Girişi doğrulanması gereken olmadan doğrudan sunucuya iletilmezse ve uygulama yanlışlıkla eklenen kodu yürütür, saldırı zarar verebilecek veya verileri yok olasılığına sahiptir.  
  
 SQL Server sözdizimsel olarak geçerli olan aldığı tüm sorguları yürüttüğü için SQL deyimleri oluşturan her türlü yordam, ekleme güvenlik açıklarına karşı gözden geçirilmelidir. Hatta parametreli veri nitelikli ve belirlenen bir saldırgan tarafından işlenebilir. Dinamik SQL kullanırsanız, Komutlarınızın Parametreleştirme emin olun ve hiçbir zaman doğrudan sorgu dizesine parametre değerlerini içerir.  
  
## <a name="anatomy-of-a-sql-injection-attack"></a>SQL ekleme saldırısına anatomisi  
 Ekleme işlemi, beklenenden önce bir metin dizesi sonlandırılması ve yeni bir komut ekleme çalışır. Eklenen komut çalıştırılmadan önce eklenmiş ek dizeleri olabileceğinden, eklenen bir açıklama işareti dizesiyle malefactor sonlandırır "--". Yürütme sırasında sonraki metin göz ardı edilir. Noktalı virgül (;) kullanarak birden çok komut eklenebilir sınırlayıcı.  
  
 Eklenen SQL kodunun sözdizimsel olarak doğru olduğu sürece, kurcalama program aracılığıyla algılanamıyor. Bu nedenle, tüm kullanıcı girişini ve dikkatli bir şekilde kullanmakta olduğunuz sunucuda yapılandırılmış SQL komutlarını yürüten gözden geçirme kod doğrulamanız gerekir. Hiçbir zaman doğrulanmazsa kullanıcı girişi art arda ekler. Dize birleştirme birincil betik ekleme için giriş noktasıdır.  
  
 Bazı faydalı yönergeleri aşağıda verilmiştir:  
  
- Hiçbir zaman doğrudan kullanıcı girişi Transact-SQL deyimlerini oluşturmak; saklı yordamlar, kullanıcı girişini doğrulamak için kullanın.  
  
- Kullanıcı girişi türü, uzunluğu, biçimi ve aralığı test ederek doğrulayın. Sistem adlarını veya REPLACE() işlevi bir dizedeki herhangi bir karakter kaçış kaçış için Transact-SQL QUOTENAME() işlevini kullanın.  
  
- Uygulamanızın her katmanında birden çok katman doğrulama uygulayın.  
  
- Giriş boyutu ve veri türü test ve uygun sınırlarını zorlayın. Bu, bilinçli arabellek taşmalarını önleme yardımcı olabilir.  
  
- Dize değişkenleri içeriğini test edin ve yalnızca beklenen değerleri kabul edin. İkili verileri, kaçış dizileri ve yorum karakterleri içeren girdileri reddeder.  
  
- XML belgelerle çalışırken girildiği gibi tüm veri şemasına karşı doğrulayın.  
  
- Çok katmanlı ortamlar tüm verilerin güvenli bölgeye giriş önce doğrulanması gerekir.  
  
- Dosya adları oluşturulabilir alanları aşağıdaki dizeleri kabul: YEDEK, $, COM8, CON, yapılandırma yoluyla COM1 $, LPT8, NUL ve PRN, LPT1 saat.  
  
- Kullanım <xref:System.Data.SqlClient.SqlParameter> saklı yordamlar ve tür denetimi ve uzunluğu doğrulama sağlamak için komutları nesneleri.  
  
- Kullanım <xref:System.Text.RegularExpressions.Regex> geçersiz karakterler filtrelemek için istemci kodu ifadeler.  
  
## <a name="dynamic-sql-strategies"></a>Dinamik SQL stratejileri  
 Dinamik olarak yürütülen SQL deyimleri neden SQL Server'ın dinamik SQL tarafından erişilen nesneler karşı çağıranın izinlerini kontrol etmek sahiplik zinciri, yordam kodu sonlarını oluşturuldu.  
  
 SQL Server saklı yordamları ve kullanıcı tanımlı işlevleri, dinamik SQL yürütme kullanarak verilere kullanıcıların erişim için yöntemleri vardır.  
  
- Kimliğe bürünme kullanma Transact-SQL EXECUTE AS yan tümcesi içinde açıklandığı [ile SQL Server'da kimliğe bürünme izinlerini özelleştirme](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md).  
  
- Sertifikalar, saklı yordamlarda açıklandığı imzalama [SQL Server'da saklı yordam imzalama](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md).  
  
### <a name="execute-as"></a>EXECUTE AS  
 Arayanın izinleri, kullanıcı ile belirtilen EXECUTE AS yan tümcesi değiştirir olarak yürütme yan tümcesi. İç içe geçmiş saklı yordamları ve Tetikleyicileri Ara sunucu kullanıcı güvenlik bağlamı altında çalıştırmak. Bu, satır düzeyi güvenlik veya denetleme gerektiren uygulamalar bozabilir. Kullanıcının kimliğini döndüren bazı işlevler EXECUTE AS belirtilen kullanıcı döndürür yan tümcesi, özgün çağırana. Yürütme bağlamı yalnızca yürütme yordamın veya geri DÖNDÜRME deyimi verildiğinde sonra özgün çağırana döndürülür.  
  
### <a name="certificate-signing"></a>Sertifika İmzalama  
 Bir sertifika ile imzalanmış bir saklı yordam yürütüldüğünde, arayanın olanlar sertifika kullanıcıya verilen izinler birleştirilir. Yürütme bağlamı aynı kalır; Sertifika kullanıcı çağıranın kimliğine bürünüp değil. Saklı yordam imzalama uygulamak için birkaç adım gerektirir. Yordamı değiştirilir, her zaman yeniden imzalanması gerekir.  
  
### <a name="cross-database-access"></a>Çapraz veritabanı erişimi  
 Veritabanları arası sahiplik zinciri, dinamik olarak oluşturulan SQL deyimleri yürütüldüğü durumlarda çalışmaz. Başka bir veritabanındaki verilere erişen bir saklı yordam oluşturarak ve yordamı hem veritabanlarınızda var olan bir sertifika imzalama SQL Server'da bu sorunu çalışabilir. Bu kullanıcılar veritabanı erişimi veya izinleri vermeden yordamı tarafından kullanılan veritabanı kaynaklarına erişmenizi sağlar.  
  
## <a name="external-resources"></a>Dış Kaynaklar  
 Daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[Saklı yordamları](/sql/relational-databases/stored-procedures/stored-procedures-database-engine) ve [SQL ekleme](/sql/relational-databases/security/sql-injection) SQL Server Çevrimiçi Kitapları'nda|Konular, saklı yordamlar oluşturma ve SQL ekleme nasıl çalıştığını açıklar.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET Uygulamalarının Güvenliğini Sağlama](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [SQL Server Güvenliğine Genel Bakış](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)
- [SQL Server'da Uygulama Güvenliği Senaryoları](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [SQL Server'da Saklı Yordam İzinlerini Yönetme](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)
- [SQL Server'da Saklı Yordam İmzalama](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md)
- [SQL Server'da Kimliğe Bürünme İzinlerini Özelleştirme](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)

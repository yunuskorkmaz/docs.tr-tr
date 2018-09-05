---
title: SQL Server'da saklı yordam imzalama
ms.date: 01/05/2018
ms.assetid: eeed752c-0084-48e5-9dca-381353007a0d
ms.openlocfilehash: c24edd59992c246c33944e6693ff5ac69311886a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43555170"
---
# <a name="signing-stored-procedures-in-sql-server"></a>SQL Server'da saklı yordam imzalama
 İmzalayan özel anahtarla şifrelenmiş veri Özet bir dijital imzadır. Özel anahtar, dijital imza, taşıyıcı veya sahibi benzersiz olmasını sağlar. Saklı yordamları, işlevleri (satır içi tablo değerli işlevler dışında) tetikleyiciler ve derlemeleri oturum açabilirsiniz.  
  
 Bir saklı yordam bir sertifika veya asimetrik anahtar ile oturum açabilirsiniz. Sahiplik zinciri aracılığıyla izinleri devralınamaz veya sahiplik zinciri, dinamik SQL gibi ihlal edildiğinde bu senaryoları için tasarlanmıştır. Bir kullanıcı sertifikası için eşlenmiş saklı yordamı erişmesi nesnelerinde kullanıcı izinlerini sertifika verme sonra oluşturabilirsiniz.  

 Ayrıca aynı sertifikayı, eşlenmiş bir oturum oluşturur ve ardından oturum açma için gerekli tüm sunucu düzeyi izinleri veya oturumu bir veya daha fazla sabit sunucu rollerini ekleyin. Bu etkinleştirme önlemek üzere tasarlanmış `TRUSTWORTHY` veritabanı ayarı senaryoları daha yüksek bir düzeyinde izinler gereklidir.  
  
 Saklı yordam yürütüldüğünde, SQL Server arayanın olanlar sertifika kullanıcı ve/veya oturum açma izinleri birleştirir. Farklı `EXECUTE AS` yan tümcesi, yordam yürütme bağlamı değiştirmez. Yerleşik işlevler dönüş oturum açma ve kullanıcı adları sertifika kullanıcı adına değil arayan adını döndürür.  
  
## <a name="creating-certificates"></a>Sertifikaları oluşturma  
 Oturum açtığınızda bir saklı yordam bir sertifika veya asimetrik anahtar, saklı yordam kodu yürütme birlikte şifrelenmiş karması oluşan bir veri özeti-kullanıcı olarak, özel anahtarı kullanarak oluşturulur. Çalışma zamanında veri Özet ortak anahtarla şifresi ve saklı yordam karma değeriyle karşılaştırılır. Yürütme değiştirme-karma değeri, dijital imza artık eşleşmesi kullanıcı geçersiz kılmaları gibi. Saklı yordam değiştirme imza tamamen saklı yordamının kodunu değiştirmesini özel anahtarına erişimi yok birisi önleyen bırakır. Her iki durumda da, yordam kodu veya yürütme değiştirdiğiniz her durumda yeniden imzalamanız gerekir-kullanıcı olarak.  
  
 Bir modül oturum açarken kullanılan iki gereken adımlar vardır:  
  
1.  Transact-SQL kullanarak bir sertifika oluşturmak `CREATE CERTIFICATE [certificateName]` deyimi. Bu deyim bir başlangıç ve bitiş tarihi ve bir parola ayarlamak için birkaç seçenek vardır. Varsayılan sona erme tarihi bir yıldır.  
  
1.  Yordamı Transact-SQL kullanarak bir sertifika ile oturum `ADD SIGNATURE TO [procedureName] BY CERTIFICATE [certificateName]` deyimi.  

Modül imzalandıktan sonra sertifika ile ilişkilendirilmesi gereken ek izinler tutmak için oluşturulacak bir veya daha fazla sorumluları gerekir.  

Ek veritabanı düzeyi izinler modülü ihtiyacı varsa:  
  
1.  Transact-SQL kullanarak bu sertifikayla ilişkili bir veritabanı kullanıcısı oluşturun `CREATE USER [userName] FROM CERTIFICATE [certificateName]` deyimi. Bu kullanıcı, yalnızca veritabanında var ve bir oturum açma, o aynı sertifikadan oluşturuldu sürece oturum açma kimliğiyle ilişkili değil.  
  
1.  Sertifika kullanıcı gerekli veritabanı düzeyinde izinleri verin.  
  
Ek sunucu düzeyi izinleri modülü ihtiyacı varsa:  
  
1.  Sertifikayı kopyalayın `master` veritabanı.  
 
1.  Transact-SQL kullanarak bu sertifikayla ilişkili bir oturum açma oluşturma `CREATE LOGIN [userName] FROM CERTIFICATE [certificateName]` deyimi.  
  
1.  Sertifika oturum açma, gerekli sunucu düzeyi izinleri verin.  
  
> [!NOTE]  
>  Bir sertifika verme deyimi kullanarak iptal edilen izinleri olan bir kullanıcıya verilemiyor. REDDET her zaman izin ver sertifika kullanıcıya verilen izinleri devralmasını çağıran önleme önceliklidir.  
  
## <a name="external-resources"></a>Dış Kaynaklar  
 Daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[İmzalama Modülü](https://go.microsoft.com/fwlink/?LinkId=98590) SQL Server Çevrimiçi Kitapları'nda|İmzalama, bir örnek senaryo ve ilgili Transact-SQL konulara bağlantılar sağlayan modülü açıklar.|  
|[Saklı yordamlarla bir sertifika imzalama](/sql/relational-databases/tutorial-signing-stored-procedures-with-a-certificate) SQL Server Çevrimiçi Kitapları'nda|Bir saklı yordam bir sertifika ile imzalamak için bir öğretici sağlar.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET Uygulamalarının Güvenliğini Sağlama](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [SQL Server Güvenliğine Genel Bakış](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [SQL Server'da Uygulama Güvenliği Senaryoları](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [SQL Server'da Saklı Yordam İzinlerini Yönetme](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)  
 [SQL Server’da Secure Dynamic SQL Yazma](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)  
 [SQL Server'da Kimliğe Bürünme İzinlerini Özelleştirme](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md)  
 [Saklı Yordamlarla Verileri Değiştirme](../../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)  
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)

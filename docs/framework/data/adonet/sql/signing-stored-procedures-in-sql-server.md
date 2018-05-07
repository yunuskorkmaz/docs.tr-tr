---
title: Saklı yordamlar SQL Server'daki imzalama
ms.date: 01/05/2018
ms.assetid: eeed752c-0084-48e5-9dca-381353007a0d
ms.openlocfilehash: 98dfaa6d5293cb1ad85f70be3388fb333daef373
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="signing-stored-procedures-in-sql-server"></a>Saklı yordamlar SQL Server'daki imzalama
 Dijital imza imzalayan özel anahtar ile şifrelenmiş veri Özet ' dir. Özel anahtar dijital imza, taşıyıcı veya sahibi benzersiz olmasını sağlar. Saklı yordamlar, işlevleri (dışında satır içi tablo değerli işlevler), tetikleyiciler ve derlemeler oturum açabilir.  
  
 Saklı yordam bir sertifika veya asimetrik anahtar ile oturum açabilir. Sahiplik zincirleme aracılığıyla izinleri devralınan olamaz veya sahiplik zinciri, dinamik SQL gibi bozuk olduğunda bu senaryoları için tasarlanmıştır. Saklı yordam erişmesi nesneler üzerinde kullanıcı izinlerini sertifika verme daha sonra sertifikayı, eşlenen bir kullanıcı oluşturabilirsiniz.  

 Ayrıca aynı sertifikayla eşleştirilmiş bir oturumu oluşturmak ve ardından o oturum açmak için gereken tüm sunucu düzeyi izinleri verin veya oturumu bir veya daha fazla sabit sunucu rollerini ekleyin. Bu etkinleştirme önlemek üzere tasarlanmış `TRUSTWORTHY` veritabanı ayarı senaryolarında daha yüksek düzey izinleri gerekiyor.  
  
 Saklı yordam çalıştırıldığında, SQL Server çağıran olanlar sertifika kullanıcı ve/veya oturum açma izinleri birleştirir. Farklı `EXECUTE AS` yan tümcesi, yordam yürütme bağlamı değiştirmez. Bu dönüş oturum açma yerleşik işlevler ve kullanıcı adları sertifika kullanıcı adı değil arayan adını döndürür.  
  
## <a name="creating-certificates"></a>Sertifikaları oluşturma  
 Bir sertifika veya asimetrik anahtar, saklı yordam kodu yürütme birlikte şifrelenmiş karmasını oluşan bir veri özeti olan bir saklı yordam kaydolduğunuzda-kullanıcı olarak, özel anahtarı kullanılarak oluşturulur. Çalışma zamanında veri Özet ortak anahtarla şifresi ve saklı yordam karma değeriyle karşılaştırılır. Execute değiştirme-kullanıcı, böylece dijital imza artık eşleşir, karma değeri geçersiz kılmaları gibi. Saklı yordam değiştirme imza tamamen saklı yordam kodunu değiştirme Access'ten özel anahtara sahip olmayan birisi önleyen bırakır. Her iki durumda da, yordam kodu veya yürütme değiştirdiğinizde yeniden oturum açmanız gerekir-kullanıcı olarak.  
  
 Bir modül oturum açma dahil iki gereken adımlar şunlardır:  
  
1.  Transact-SQL kullanarak bir sertifika oluşturmak `CREATE CERTIFICATE [certificateName]` deyimi. Bu deyim bir başlangıç ve bitiş tarihi ve bir parola ayarlamak için birkaç seçenek vardır. Varsayılan sona erme tarihi, bir yıl de.  
  
1.  Yordam Transact-SQL kullanarak sertifika ile oturum `ADD SIGNATURE TO [procedureName] BY CERTIFICATE [certificateName]` deyimi.  

Modül oturum sonra bir veya daha fazla sorumluları sertifika ile ilişkilendirilmesi gereken ek izinler tutmak için oluşturulması gerekiyor.  

Modül ek veritabanı düzeyi izinler gerekirse:  
  
1.  Transact-SQL kullanarak bu sertifikayla ilişkili bir veritabanı kullanıcısı oluşturmalıdır `CREATE USER [userName] FROM CERTIFICATE [certificateName]` deyimi. Bu kullanıcı yalnızca veritabanında var ve bir oturum açma, o aynı sertifika oluşturuldu sürece bir oturum ile ilişkili değil.  
  
1.  Sertifika kullanıcı gerekli veritabanı düzeyi izinleri verin.  
  
Modül ek sunucu düzeyi izinleri gerekirse:  
  
1.  Sertifikayı kopyalamak `master` veritabanı.  
 
1.  Transact-SQL kullanarak bu sertifikayla ilişkili bir oturumu oluşturmak `CREATE LOGIN [userName] FROM CERTIFICATE [certificateName]` deyimi.  
  
1.  Sertifika oturum açma gerekli sunucu düzeyi izinleri verin.  
  
> [!NOTE]  
>  Bir sertifika verme deyimi kullanarak iptal izinleri olan bir kullanıcı için izinleri olamaz. REDDETME her zaman izin ver çağıran sertifika kullanıcıya verilen izinler devralmayı engelleme önceliklidir.  
  
## <a name="external-resources"></a>Dış Kaynaklar  
 Daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[İmzalama Modülü](http://go.microsoft.com/fwlink/?LinkId=98590) SQL Server Çevrimiçi Kitapları'nda|İmzalama, bir örnek senaryo ve ilgili Transact-SQL konulara bağlantılar sağlayan modülü açıklar.|  
|[Saklı yordamlar bir sertifika ile imzalama](http://msdn.microsoft.com/library/bb283630.aspx) SQL Server Çevrimiçi Kitapları'nda|Saklı yordam bir sertifika ile imzalamak için bir öğretici sağlar.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET Uygulamalarının Güvenliğini Sağlama](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [SQL Server Güvenliğine Genel Bakış](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [SQL Server'da Uygulama Güvenliği Senaryoları](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [SQL Server'da Saklı Yordam İzinlerini Yönetme](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)  
 [SQL Server’da Secure Dynamic SQL Yazma](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)  
 [SQL Server'da Kimliğe Bürünme İzinlerini Özelleştirme](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md)  
 [Saklı Yordamlarla Verileri Değiştirme](../../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)

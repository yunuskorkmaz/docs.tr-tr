---
title: "Saklı yordamlar SQL Server'daki imzalama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eeed752c-0084-48e5-9dca-381353007a0d
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 86c2a6c3f2c84c931df15e4809980a76cb6d826c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="signing-stored-procedures-in-sql-server"></a>Saklı yordamlar SQL Server'daki imzalama
Saklı yordam bir sertifika veya asimetrik anahtar ile oturum açabilir. Sahiplik zincirleme aracılığıyla izinleri devralınan olamaz veya sahiplik zinciri, dinamik SQL gibi bozuk olduğunda bu senaryoları için tasarlanmıştır. Sonra sertifikayı kullanıcı saklı yordamı erişmesi nesneleri izin verme sertifikayla eşleştirilmiş bir kullanıcı oluşturun.  
  
 Saklı yordam çalıştırıldığında, SQL Server çağıran olanlar sertifika kullanıcının izinleriyle birleştirir. Aksine EXECUTE AS yan TÜMCESİNİ yordamı yürütme bağlamı değişmez. Bu dönüş oturum açma yerleşik işlevler ve kullanıcı adları sertifika kullanıcı adı değil arayan adını döndürür.  
  
 Dijital imza imzalayan özel anahtar ile şifrelenmiş veri Özet ' dir. Özel anahtar dijital imza, taşıyıcı veya sahibi benzersiz olmasını sağlar. Saklı yordamlar, fonksiyon veya tetikleyici imzalayabilirsiniz.  
  
> [!NOTE]
>  Sunucu düzeyi izinleri vermek için ana veritabanında bir sertifika oluşturabilirsiniz.  
  
## <a name="creating-certificates"></a>Sertifikaları oluşturma  
 Saklı yordam bir sertifika ile oturum açtığınızda, saklı yordam kod şifrelenmiş karmasını oluşan bir veri özeti özel anahtarı kullanılarak oluşturulur. Çalışma zamanında veri Özet ortak anahtarla şifresi ve saklı yordam karma değeriyle karşılaştırılır. Böylece dijital imza artık eşleşir saklı yordamı değiştirme karma değerini geçersiz kılar. Bu saklı yordam kodunu değiştirme Access'ten özel anahtara sahip olmayan birisi önler. Bu nedenle, yordam her değiştirdiğinizde yeniden oturum açmanız gerekir.  
  
 Bir modül oturum açma dahil edilen dört adım vardır:  
  
1.  Transact-SQL kullanarak bir sertifika oluşturmak `CREATE CERTIFICATE [certificateName]` deyimi. Bu deyim bir başlangıç ve bitiş tarihi ve bir parola ayarlamak için birkaç seçenek vardır. Bir yıl varsayılan sona erme tarihi olan  
  
2.  Transact-SQL kullanarak bu sertifikayla ilişkili bir veritabanı kullanıcısı oluşturmalıdır `CREATE USER [userName] FROM CERTIFICATE [certificateName]` deyimi. Bu kullanıcı yalnızca veritabanında var ve bir oturum ile ilişkili değil.  
  
3.  Sertifika kullanıcı veritabanı nesneleri üzerinde gerekli izinleri verin.  
  
> [!NOTE]
>  Bir sertifika verme deyimi kullanarak iptal izinleri olan bir kullanıcı için izinleri olamaz. REDDETME her zaman izin ver çağıran sertifika kullanıcıya verilen izinler devralmayı engelleme önceliklidir.  
  
1.  Yordam Transact-SQL kullanarak sertifika ile oturum `ADD SIGNATURE TO [procedureName] BY CERTIFICATE [certificateName]` deyimi.  
  
## <a name="external-resources"></a>Dış Kaynaklar  
 Daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[İmzalama Modülü](http://go.microsoft.com/fwlink/?LinkId=98590) SQL Server Çevrimiçi Kitapları'nda|İmzalama, bir örnek senaryo ve ilgili Transact-SQL konulara bağlantılar sağlayan modülü açıklar.|  
|[Saklı yordamlar bir sertifika ile imzalama](http://msdn.microsoft.com/library/bb283630.aspx) SQL Server Çevrimiçi Kitapları'nda|Saklı yordam bir sertifika ile imzalamak için bir öğretici sağlar.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET uygulamalarının güvenliğini sağlama](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [SQL Server güvenlik genel bakış](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [SQL Server'daki uygulama güvenlik senaryoları](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [Saklı yordamlar SQL Server'daki izinlerle yönetme](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)  
 [SQL Server'da güvenli dinamik SQL yazma](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)  
 [Kimliğe bürünme SQL Server'daki izinlerle özelleştirme](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md)  
 [Saklı yordamlar verilerle değiştirme](../../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)

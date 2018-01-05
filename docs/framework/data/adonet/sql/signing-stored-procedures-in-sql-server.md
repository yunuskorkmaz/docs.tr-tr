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
ms.workload: dotnet
ms.openlocfilehash: b3d90579e28fde40d461bdb511d797e5d7f6f179
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
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
 [ADO.NET Uygulamalarının Güvenliğini Sağlama](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [SQL Server Güvenliğine Genel Bakış](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [SQL Server'da Uygulama Güvenliği Senaryoları](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [SQL Server'da Saklı Yordam İzinlerini Yönetme](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)  
 [SQL Server’da Secure Dynamic SQL Yazma](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)  
 [SQL Server'da Kimliğe Bürünme İzinlerini Özelleştirme](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md)  
 [Saklı Yordamlarla Verileri Değiştirme](../../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)

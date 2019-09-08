---
title: SQL Server Güvenliğine Genel Bakış
ms.date: 03/30/2017
ms.assetid: ae66dd75-5c16-4cc0-9e12-774dd26d3fb9
ms.openlocfilehash: adc1ce661d49c468de09552ea36a2cd58d6343f1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780943"
---
# <a name="overview-of-sql-server-security"></a>SQL Server Güvenliğine Genel Bakış
Çakışan güvenlik katmanlarında derinlemesine savunma stratejisi, güvenlik tehditlerini sayaca yönelik en iyi yoldur. SQL Server, veritabanı yöneticilerinin ve geliştiricilerin güvenli veritabanı uygulamaları ve sayaç tehditleri oluşturmalarına olanak tanımak için tasarlanan bir güvenlik mimarisi sağlar. SQL Server her sürümü, yeni özellikler ve işlevlerin kullanıma sunulmasıyla önceki SQL Server sürümlerinde geliştirilmiştir. Ancak, güvenlik kutuya teslim edilmez. Her uygulama güvenlik gereksinimlerinde benzersizdir. Geliştiricilerin, bilinen tehditler ve gelecekte ortaya çıkabilecek tehditleri tahmin etmek için hangi özellik ve işlevsellik bileşiminin en uygun olduğunu anlaması gerekir.  
  
 Bir SQL Server örnek, sunucudan itibaren hiyerarşik bir varlık koleksiyonu içerir. Her bir sunucu birden çok veritabanı içerir ve her veritabanı güvenli kılınabilir nesnelerin bir koleksiyonunu içerir. Her SQL Server güvenli hale getirilebilen, bir bireyin, Grup veya işlem SQL Server erişim izni verilen bir *sorumlu*için verilebilecek ilişkili *izinleri* vardır. SQL Server güvenlik çerçevesi, *kimlik doğrulama* ve *Yetkilendirme*aracılığıyla güvenli kılınabilir varlıklara erişimi yönetir.  
  
- Kimlik doğrulaması, bir sorumlunun sunucu tarafından değerlendirilen kimlik bilgilerini göndererek erişim isteği yaptığı SQL Server oturum açma işlemidir. Kimlik doğrulaması, kimliği doğrulanmış kullanıcının veya işlemin kimliğini belirler.  
  
- Yetkilendirme, bir sorumlu tarafından hangi güvenli kılınabilir kaynakların erişebileceğini ve bu kaynaklar için hangi işlemlere izin verileceğini belirleme işlemidir.  
  
 Bu bölümdeki konularda, SQL Server Books Online 'ın ilgili sürümündeki tüm belgelere bağlantılar sağlayan SQL Server güvenlik temelleri ele alınmaktadır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [SQL Server’da Kimlik Doğrulaması](authentication-in-sql-server.md)  
 SQL Server oturum açma ve kimlik doğrulamasını açıklar ve ek kaynaklara bağlantılar sağlar.  
  
 [SQL Server’da Sunucu ve Veritabanı Rolleri](server-and-database-roles-in-sql-server.md)  
 Sabit sunucu ve veritabanı rollerini, özel veritabanı rollerini ve yerleşik hesapları açıklar ve ek kaynaklara bağlantılar sağlar.  
  
 [SQL Server'da Sahiplik ve Kullanıcı Şeması Ayrımı](ownership-and-user-schema-separation-in-sql-server.md)  
 Nesne sahipliğini ve Kullanıcı şeması ayırmayı açıklar ve ek kaynaklara bağlantılar sağlar.  
  
 [SQL Server’da Yetkilendirme ve İzinler](authorization-and-permissions-in-sql-server.md)  
 En az ayrıcalık ilkesini kullanarak izin vermeyi açıklar ve ek kaynaklara bağlantılar sağlar.  
  
 [SQL Server’da Veri Şifreleme](data-encryption-in-sql-server.md)  
 SQL Server 'daki veri şifreleme seçeneklerini açıklar ve ek kaynaklara bağlantılar sağlar.  
  
 [SQL Server’da CLR Tümleştirme Güvenliği](clr-integration-security-in-sql-server.md)  
 CLR tümleştirme güvenlik kaynaklarına bağlantılar sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET Uygulamalarının Güvenliğini Sağlama](../securing-ado-net-applications.md)
- [SQL Server Güvenliği](sql-server-security.md)
- [SQL Server'da Uygulama Güvenliği Senaryoları](application-security-scenarios-in-sql-server.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)

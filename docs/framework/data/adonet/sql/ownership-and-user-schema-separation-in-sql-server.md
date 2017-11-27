---
title: "Sahipliği ve SQL Server'daki kullanıcı şema ayırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 242830c1-31b5-4427-828c-cc22ff339f30
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 168eaf9bc0bbac80cbd1e2bb0538aab89d262a49
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ownership-and-user-schema-separation-in-sql-server"></a>Sahipliği ve SQL Server'daki kullanıcı şema ayırma
SQL Server güvenlik çekirdek kavramı nesne sahipleri değiştirilemeyen bunları yönetme izni olmasıdır. Bir nesne sahibinden ayrıcalıkları kaldırılamıyor ve içindeki nesneleri sahipseniz kullanıcıların veritabanından bırakılamıyor.  
  
## <a name="user-schema-separation"></a>Kullanıcı şema ayırma  
 Kullanıcı şema ayrımı veritabanı nesne izinleri yönetme daha fazla esneklik sağlar. A *şema* ayrı ad alanında Grup nesnelerine sağlayan bir adlandırılmış veritabanı nesneleri için kapsayıcıdır. Örneğin, AdventureWorks örnek veritabanı şemaları, üretim, satış ve İnsanKaynakları içerir.  
  
 Nesnelere başvurma için dört bölümden oluşan sözdizimini şema adını belirtir.  
  
```  
Server.Database.DatabaseSchema.DatabaseObject  
```  
  
### <a name="schema-owners-and-permissions"></a>Şema sahipleri ve izinleri  
 Şemalar tarafından herhangi bir veritabanı asıl sahip olabilir ve tek bir sorumlusu birden çok şema sahip olabilir. Güvenlik kuralları şemadaki tüm nesneler tarafından alınan bir bir şemaya uygulayabilirsiniz. Bir şema için erişim izinleri ayarladıktan sonra yeni nesneler şemaya eklendikçe bu izinleri otomatik olarak uygulanır. Kullanıcıların varsayılan şema atanabilir ve birden çok veritabanı kullanıcıları aynı şema paylaşabilirsiniz.  
  
 Geliştiriciler bir şemada bulunan nesneler oluşturduğunuzda varsayılan olarak şema, geliştirici sahibi güvenlik sorumlusu tarafından nesneleri sahibi olur. Nesne sahipliği YETKİLENDİRME Transact-SQL ALTER deyimiyle aktarılabilir. İzinleri yönetme için karmaşıklık ekler bu önerilmez çünkü rağmen bir şema, farklı kullanıcılara ait ve şeması için atanan'den daha ayrıntılı izinlere sahip nesneleri de içerebilir. Nesneleri Şemalar arasında taşınabilir ve Şema sahipliğini sorumluları arasında aktarılabilir. Veritabanı kullanıcıları şemaları etkilemeden bırakılabilir.  
  
### <a name="built-in-schemas"></a>Yerleşik şemaları  
 SQL Server yerleşik veritabanı kullanıcıları ve rolleri olarak aynı ada sahip on önceden tanımlanmış şemalar ile birlikte gelir. Bunlar çoğunlukla geriye dönük uyumluluk için mevcut. Bunları gerekmiyorsa sabit veritabanı rollerinin aynı adları olan şemaları düşürebilir. Şu şemalardan bırakılamıyor:  
  
-   `dbo`  
  
-   `guest`  
  
-   `sys`  
  
-   `INFORMATION_SCHEMA`  
  
 Modeli veritabanından bırakın, yeni veritabanları görünmez.  
  
> [!NOTE]
>  `sys` Ve `INFORMATION_SCHEMA` şemaları sistem nesneleri için ayrılmıştır. Bu şemalarda nesneler oluşturamaz ve bunları bırakılamıyor.  
  
#### <a name="the-dbo-schema"></a>Şema dbo  
 `dbo` Schema yeni oluşturulan bir veritabanı için varsayılan şema'dır. `dbo` Şema sahibi tarafından `dbo` kullanıcı hesabı. Varsayılan olarak, bu CREATE kullanıcı Transact-SQL komutuyla oluşturulan kullanıcınız `dbo` kendi varsayılan şema olarak.  
  
 Atanan kullanıcıların `dbo` şema devralmaz izinlerini `dbo` kullanıcı hesabı. Hiçbir izinler şemadan kullanıcılar tarafından devralınır; Şema izinlerini şemasında bulunan veritabanı nesneleri tarafından devralınır.  
  
> [!NOTE]
>  Veritabanı nesneleri, bir bölüm adı kullanarak başvurduğunda SQL Server kullanıcının varsayılan şemasında İlk bakar. Nesne var. bulunamadı, SQL Server İleri'durur `dbo` şema. Nesne içinde değilse `dbo` şeması, bir hata döndürülür.  
  
## <a name="external-resources"></a>Dış Kaynaklar  
 Nesne sahipliği ve şemaları hakkında daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[Kullanıcı şema ayrımı](http://msdn.microsoft.com/library/ms190387.aspx) SQL Server Çevrimiçi Kitapları'nda|Kullanıcı şema ayırma tarafından sunulan değişiklikler açıklanmaktadır. Yeni davranış, sahipliği, Katalog görünümleri ve izinleri üzerindeki etkisini içerir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET uygulamalarının güvenliğini sağlama](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [SQL Server'daki uygulama güvenlik senaryoları](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [SQL Server kimlik doğrulaması](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)  
 [Sunucusu ve SQL Server veritabanı rolleri](../../../../../docs/framework/data/adonet/sql/server-and-database-roles-in-sql-server.md)  
 [Yetkilendirme ve SQL Server'daki izinleri](../../../../../docs/framework/data/adonet/sql/authorization-and-permissions-in-sql-server.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)

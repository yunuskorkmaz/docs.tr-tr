---
title: SQL Server'da Sahiplik ve Kullanıcı Şeması Ayrımı
ms.date: 03/30/2017
ms.assetid: 242830c1-31b5-4427-828c-cc22ff339f30
ms.openlocfilehash: b56a2c6f1211a11d2aa55de0cc101f6b90f7f83d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59221866"
---
# <a name="ownership-and-user-schema-separation-in-sql-server"></a>SQL Server'da Sahiplik ve Kullanıcı Şeması Ayrımı
Bir SQL Server güvenlik kavramının sahipleri nesnelerin Dönülmez bunları yönetme izni olmasıdır. Bir nesne sahibinden ayrıcalıkları kaldıramazsınız ve sahip oldukları nesneleri da, kullanıcıların bir veritabanından bırakılamıyor.  
  
## <a name="user-schema-separation"></a>Kullanıcı şeması ayrımı  
 Kullanıcı şeması ayrımı veritabanı nesne izinleri yönetiminde daha fazla esneklik sağlar. A *şema* ayrı ad alanında Grup nesnelerine e sağlayan bir adlandırılmış veritabanı nesneleri için kapsayıcıdır. Örneğin, AdventureWorks örnek veritabanı şemaları, üretim, satış ve İnsanKaynakları içerir.  
  
 Nesnelere başvuran için dört kısımlı sözdizimini şema adını belirtir.  
  
```  
Server.Database.DatabaseSchema.DatabaseObject  
```  
  
### <a name="schema-owners-and-permissions"></a>Şema sahipleri ve izinleri  
 Şemaları herhangi bir veritabanı sorumlusu tarafından sahiplenilebilir ve tek bir asıl birden çok şema sahip olabilir. Güvenlik kuralları, şemadaki tüm nesneleri tarafından devralınmış bir bir şemaya uygulayabilirsiniz. Bir şema için erişim izinleri ayarladıktan sonra yeni nesneler için şema eklendikçe Bu izinler otomatik olarak uygulanır. Varsayılan şema kullanıcılara atanabilir ve aynı şemaya birden çok veritabanı kullanıcıları paylaşabilirsiniz.  
  
 Geliştiriciler bir şemada bulunan nesneler oluşturduğunuzda varsayılan olarak, geliştirici şemanın sahibi güvenlik sorumlusu tarafından nesneleri sahibi olur. Nesne sahipliği YETKİLENDİRME Transact-SQL ALTER deyimiyle aktarılabilir. İzinlerinin yönetilmesi için karmaşıklık ekler nedeniyle bu önerilmez olsa da bir şema ayrıca farklı kullanıcılara ait ve daha ayrıntılı izinler, şema atanmış olan nesneleri içerebilir. Nesneleri şemaları arasında taşınabilir ve şema sahiplik arasında sorumluları aktarılabilir. Veritabanı kullanıcısı, şemaları etkilemeden bırakılabilir.  
  
### <a name="built-in-schemas"></a>Yerleşik şemaları  
 SQL Server rolleri ve yerleşik veritabanı kullanıcısı olarak aynı ada sahip on önceden tanımlanmış şemalar ile birlikte gelir. Bu, çoğunlukla geriye dönük uyumluluk için mevcut. Bunları gerekmiyorsa, sabit veritabanı rollerine olarak aynı adlara sahip şemaları bırakabilirsiniz. Şu şemalardan bırakılamıyor:  
  
-   `dbo`  
  
-   `guest`  
  
-   `sys`  
  
-   `INFORMATION_SCHEMA`  
  
 Veritabanından bırakın, yeni veritabanları görünmez.  
  
> [!NOTE]
>  `sys` Ve `INFORMATION_SCHEMA` şemaları sistem nesneleri için ayrılmıştır. Bu şemaları nesneler oluşturamaz ve bunları bırakılamıyor.  
  
#### <a name="the-dbo-schema"></a>Dbo Schema  
 `dbo` Şemadır yeni oluşturulan bir veritabanı için varsayılan şema. `dbo` Şema tarafından sahipli `dbo` kullanıcı hesabı. Varsayılan olarak, bu CREATE kullanıcı Transact-SQL komutuyla oluşturulan kullanıcınız `dbo` kendi varsayılan şema olarak.  
  
 Atanmış kullanıcılar `dbo` şema izinleri devralmaz `dbo` kullanıcı hesabı. İzin yok bir şema kullanıcılar tarafından devralınır; Şema izinlerini şemasında bulunan nesneleri tarafından devralınır.  
  
> [!NOTE]
>  Veritabanı nesneleri bir bölüm adı kullanılarak başvurulur, SQL Server önce kullanıcının varsayılan şema içinde arar. Nesne var. bulunmazsa, SQL Server İleri'arar `dbo` şema. Nesne içinde değilse `dbo` şema, bir hata döndürülür.  
  
## <a name="external-resources"></a>Dış Kaynaklar  
 Nesne sahipliği ve şemaları hakkında daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[Kullanıcı şeması ayrımı](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms190387(v=sql.105))|Kullanıcı şeması ayrımı tarafından yapılan değişiklikleri açıklar. Yeni davranış, etkileri sahipliği, Katalog görünümleri ve izinleri içerir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET Uygulamalarının Güvenliğini Sağlama](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [SQL Server'da Uygulama Güvenliği Senaryoları](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [SQL Server’da Kimlik Doğrulaması](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)
- [SQL Server’da Sunucu ve Veritabanı Rolleri](../../../../../docs/framework/data/adonet/sql/server-and-database-roles-in-sql-server.md)
- [SQL Server’da Yetkilendirme ve İzinler](../../../../../docs/framework/data/adonet/sql/authorization-and-permissions-in-sql-server.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)

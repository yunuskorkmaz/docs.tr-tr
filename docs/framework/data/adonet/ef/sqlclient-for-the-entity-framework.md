---
title: Entity Framework için SqlClient
ms.date: 03/30/2017
ms.assetid: 9a5d6d39-d955-43a5-a5c2-931c239398f1
ms.openlocfilehash: 7f3a1d4bbd18977bbb1dc9ce65140428ea6fe2f8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156543"
---
# <a name="sqlclient-for-the-entity-framework"></a>Entity Framework için SqlClient

Bu bölümde, Entity Framework Microsoft SQL Server üzerinde çalışmasını sağlayan SQL Server (SqlClient) için .NET Framework Veri Sağlayıcısı açıklanmaktadır.  
  
## <a name="provider-schema-attribute"></a>Sağlayıcı şeması özniteliği  

 `Provider` , `Schema` depo şeması tanım dili (ssdl) içindeki bir öğenin özniteliğidir.  
  
 SqlClient kullanmak için, "System. Data. SqlClient" dizesini `Provider` öğesinin özniteliğine atayın `Schema` .  
  
## <a name="providermanifesttoken-schema-attribute"></a>ProviderManifestToken şema özniteliği  

 `ProviderManifestToken` , `Schema` SSDL içindeki öğesinin gerekli bir özniteliğidir. Bu belirteç, çevrimdışı senaryolar için sağlayıcı bildirimini yüklemek üzere kullanılır. Özniteliği hakkında daha fazla bilgi için `ProviderManifestToken` bkz. [şema Öğesı (ssdl)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl).  
  
 SqlClient, farklı SQL Server sürümleri için veri sağlayıcısı olarak kullanılabilir. Bu sürümlerin farklı özellikleri vardır. Örneğin, SQL Server 2000 desteklemez `varchar(max)` ve `nvarchar(max)` SQL Server 2005 ile tanıtılan türler desteklenmez.  
  
 SqlClient farklı SQL Server sürümleri için aşağıdaki sağlayıcı bildirim belirteçlerini üretir ve kabul eder.  
  
|SQL Server 2000|SQL Server 2005|SQL Server 2008|  
|-|-|-|  
|2000|2005|2008|  
  
> [!NOTE]
> Visual Studio 2010 ' den itibaren, [ADO.NET varlık veri modeli araçları](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)) SQL Server 2000 ' yi desteklemez.  
  
## <a name="provider-namespace-name"></a>Sağlayıcı ad alanı adı  

 Tüm sağlayıcıların bir ad alanı belirtmesi gerekir. Bu özellik, sağlayıcı tarafından türler ve işlevler gibi belirli yapılar için kullanılan önek Entity Framework söyler. SqlClient sağlayıcı bildirimleri için ad alanı `SqlServer` . Ad alanları hakkında daha fazla bilgi için bkz. [ad alanları](./language-reference/namespaces-entity-sql.md).  
  
## <a name="types"></a>Türler  

 Entity Framework için SqlClient sağlayıcısı, kavramsal model türleri ve SQL Server türleri arasında eşleme bilgileri sağlar. Daha fazla bilgi için bkz. [Entity FrameworkTypes Için SqlClient](sqlclient-for-ef-types.md).  
  
## <a name="functions"></a>İşlevler  

 Entity Framework için SqlClient sağlayıcısı, sağlayıcı tarafından desteklenen işlevlerin listesini tanımlar. Desteklenen işlevlerin listesi için bkz. [Entity Framework işlevleri Için SqlClient](sqlclient-for-ef-functions.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  

 [Entity Framework için SqlClient İşlevleri](sqlclient-for-ef-functions.md)  
  
 [Entity FrameworkTypes için SqlClient](sqlclient-for-ef-types.md)  
  
 [Entity Framework için SqlClient’ta Bilinen Sorunlar](known-issues-in-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Dili](./language-reference/entity-sql-language.md)
- [Dil başvurusu](./language-reference/index.md)
- [Entity Framework için SqlClient sağlayıcısında bilinen sorunlar](sqlclient-for-the-entity-framework.md)

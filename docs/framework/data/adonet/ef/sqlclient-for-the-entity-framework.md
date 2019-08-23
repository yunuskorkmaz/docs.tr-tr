---
title: Entity Framework için SqlClient
ms.date: 03/30/2017
ms.assetid: 9a5d6d39-d955-43a5-a5c2-931c239398f1
ms.openlocfilehash: ec67637c416f2560c1f5d0a9fd0e856703820a84
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69954963"
---
# <a name="sqlclient-for-the-entity-framework"></a>Entity Framework için SqlClient
Bu bölümde, Entity Framework Microsoft SQL Server üzerinde çalışmasını sağlayan SQL Server (SqlClient) için .NET Framework Veri Sağlayıcısı açıklanmaktadır.  
  
## <a name="provider-schema-attribute"></a>Sağlayıcı şeması özniteliği  
 `Provider`, depo şeması tanım dili `Schema` (ssdl) içindeki bir öğenin özniteliğidir.  
  
 SqlClient kullanmak için, "System. Data. SqlClient" `Provider` dizesini `Schema` öğesinin özniteliğine atayın.  
  
## <a name="providermanifesttoken-schema-attribute"></a>ProviderManifestToken şema özniteliği  
 `ProviderManifestToken`, SSDL içindeki `Schema` öğesinin gerekli bir özniteliğidir. Bu belirteç, çevrimdışı senaryolar için sağlayıcı bildirimini yüklemek üzere kullanılır. Özniteliği hakkında `ProviderManifestToken` daha fazla bilgi için bkz. [şema öğesi (ssdl)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl).  
  
 SqlClient, farklı SQL Server sürümleri için veri sağlayıcısı olarak kullanılabilir. Bu sürümlerin farklı özellikleri vardır. Örneğin, SQL Server 2000 desteklemez `varchar(max)` ve `nvarchar(max)` SQL Server 2005 ile tanıtılan türler desteklenmez.  
  
 SqlClient farklı SQL Server sürümleri için aşağıdaki sağlayıcı bildirim belirteçlerini üretir ve kabul eder.  
  
|SQL Server 2000|SQL Server 2005|SQL Server 2008|  
|-|-|-|  
|2000|2005|2008|  
  
> [!NOTE]
> Visual Studio 2010 ' den itibaren, [ADO.NET varlık veri modeli araçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)) SQL Server 2000 ' yi desteklemez.  
  
## <a name="provider-namespace-name"></a>Sağlayıcı ad alanı adı  
 Tüm sağlayıcıların bir ad alanı belirtmesi gerekir. Bu özellik, sağlayıcı tarafından türler ve işlevler gibi belirli yapılar için kullanılan önek Entity Framework söyler. SqlClient sağlayıcı bildirimleri `SqlServer`için ad alanı. Ad alanları hakkında daha fazla bilgi için bkz. [ad alanları](../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md).  
  
## <a name="types"></a>Türler  
 Entity Framework için SqlClient sağlayıcısı, kavramsal model türleri ve SQL Server türleri arasında eşleme bilgileri sağlar. Daha fazla bilgi için bkz. [Entity FrameworkTypes Için SqlClient](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md).  
  
## <a name="functions"></a>İşlevler  
 Entity Framework için SqlClient sağlayıcısı, sağlayıcı tarafından desteklenen işlevlerin listesini tanımlar. Desteklenen işlevlerin listesi için bkz. [Entity Framework işlevleri Için SqlClient](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Entity Framework için SqlClient İşlevleri](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)  
  
 [Entity FrameworkTypes için SqlClient](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md)  
  
 [Entity Framework için SqlClient’ta Bilinen Sorunlar](../../../../../docs/framework/data/adonet/ef/known-issues-in-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Dili](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
- [Dil Başvurusu](../../../../../docs/framework/data/adonet/ef/language-reference/index.md)
- [Entity Framework için SqlClient sağlayıcısında bilinen sorunlar](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md)

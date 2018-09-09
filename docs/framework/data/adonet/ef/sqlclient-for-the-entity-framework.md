---
title: Entity Framework için SqlClient
ms.date: 03/30/2017
ms.assetid: 9a5d6d39-d955-43a5-a5c2-931c239398f1
ms.openlocfilehash: 430e0e143519f97802c8cef4eee658b482a81880
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44252596"
---
# <a name="sqlclient-for-the-entity-framework"></a>Entity Framework için SqlClient
Bu bölümde, .NET Framework veri sağlayıcısı için Entity Framework, Microsoft SQL Server üzerinde çalışacak şekilde etkinleştirir SQL Server'nin (SqlClient) açıklanmaktadır.  
  
## <a name="provider-schema-attribute"></a>Sağlayıcı şema özniteliği  
 `Provider` bir özniteliğidir `Schema` depo şeması tanım dili (SSDL) öğesi.  
  
 SqlClient kullanmak için "System.Data.SqlClient" dize atamak `Provider` özniteliği `Schema` öğesi.  
  
## <a name="providermanifesttoken-schema-attribute"></a>ProviderManifestToken şema özniteliği  
 `ProviderManifestToken` gerekli bir özniteliktir `Schema` SSDL öğesinde. Bu belirteç sağlayıcı bildirimi çevrimdışı senaryolar için yüklemek için kullanılır. Hakkında daha fazla bilgi için `ProviderManifestToken` özniteliği için bkz: [şema öğesi (SSDL)](https://msdn.microsoft.com/library/fec75ae4-7f16-4421-9265-9dac61509222).  
  
 SqlClient farklı SQL Server sürümleri için veri sağlayıcısı olarak kullanılabilir. Bu sürümleri, farklı özelliklere sahip. Örneğin, [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)] desteklemediği `varchar(max)` ve `nvarchar(max)` ile sunulan türleri [!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)].  
  
 SqlClient oluşturur ve SQL Server'ın farklı sürümlerinin aşağıdaki sağlayıcısı bildirimi belirteçleri kabul eder.  
  
|SQL Server 2000|SQL Server 2005|SQL Server 2008|  
|-|-|-|  
|2000|2005|2008|  
  
> [!NOTE]
>  Visual Studio 2010 ile başlayarak [ADO.NET varlık veri modeli Araçları](https://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527) SQL Server 2000 desteklemez.  
  
## <a name="provider-namespace-name"></a>Sağlayıcı Namespace adı  
 Tüm sağlayıcılar, bir ad belirtmeniz gerekir. Bu özellik, hangi önekin türleri ve işlevleri gibi belirli yapılar için sağlayıcı tarafından kullanılan Entity Framework söyler. Ad alanı için SqlClient sağlayıcısı bildirimleri `SqlServer`. Ad alanları hakkında daha fazla bilgi için bkz. [ad alanları](../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md).  
  
## <a name="types"></a>Türler  
 Entity Framework için SqlClient sağlayıcısı kavramsal model türleri ve SQL Server türleri arasında eşleme bilgilerini sağlar. Daha fazla bilgi için [Entity FrameworkTypes için SqlClient](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md).  
  
## <a name="functions"></a>İşlevler  
 Entity Framework için SqlClient sağlayıcısı sağlayıcı tarafından desteklenen işlevlerin listesi tanımlar. Desteklenen işlevlerin bir listesi için bkz. [Entity Framework işlevleri için SqlClient](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Entity Framework için SqlClient İşlevleri](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)  
  
 [Entity FrameworkTypes için SqlClient](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md)  
  
 [Entity Framework için SqlClient’ta Bilinen Sorunlar](../../../../../docs/framework/data/adonet/ef/known-issues-in-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity SQL Dili](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)  
 [Dil Başvurusu](../../../../../docs/framework/data/adonet/ef/language-reference/index.md)  
 [Entity Framework için SqlClient sağlayıcısı bilinen](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md)

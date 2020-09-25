---
title: Veri hizmetleri sağlayıcıları (WCF Veri Hizmetleri)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: a0160b1b-3d9c-4cc8-8391-cb0986a60a41
ms.openlocfilehash: dcca6023349148ac7f65f97028d876514ef31163
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91182841"
---
# <a name="data-services-providers-wcf-data-services"></a>Veri hizmetleri sağlayıcıları (WCF Veri Hizmetleri)

WCF Veri Hizmetleri, verileri açık veri Protokolü (OData) akışı olarak ortaya çıkarmak için birden çok sağlayıcı modelini destekler. Bu konuda, veri kaynağınız için en iyi WCF Veri Hizmetleri sağlayıcıyı seçmenizi sağlayan bilgiler sağlanmaktadır.  
  
## <a name="data-source-providers"></a>Veri kaynağı sağlayıcıları  

 WCF Veri Hizmetleri, bir veri hizmetinin veri modelini tanımlamaya yönelik aşağıdaki sağlayıcıları destekler.  
  
|Sağlayıcı|Açıklama|  
|--------------|-----------------|  
|Entity Framework sağlayıcı|Bu sağlayıcı, ilişkisel verilerle eşleşen bir veri modeli tanımlayarak bir veri hizmeti ile ilişkisel verileri kullanmanıza olanak tanımak için ADO.NET Entity Framework kullanır. Veri kaynağınız, Entity Framework için üçüncü taraf sağlayıcı desteğiyle SQL Server veya başka bir veri kaynağı olabilir. SQL Server veritabanı gibi bir ilişkisel veri kaynağınız varsa Entity Framework sağlayıcıyı kullanmanız gerekir. Daha fazla bilgi için bkz. [Entity Framework sağlayıcısı](entity-framework-provider-wcf-data-services.md).|  
|Yansıma sağlayıcısı|Bu sağlayıcı, arabirimin örnekleri olarak açığa çıkarılacalanmış mevcut veri sınıflarına dayalı bir veri modeli tanımlamanızı sağlamak için yansıma kullanır <xref:System.Linq.IQueryable%601> . Güncelleştirme, arabirimi uygulayarak etkinleştirilir <xref:System.Data.Services.IUpdatable> . LINQ to SQL tarafından oluşturulan veya türü belirlenmiş bir veri kümesi tarafından tanımlanan bir çalışma zamanında tanımlanan statik veri sınıflarınız varsa, bu sağlayıcıyı kullanmanız gerekir. Daha fazla bilgi için bkz. [yansıma sağlayıcısı](reflection-provider-wcf-data-services.md).|  
|Özel Veri Hizmeti Sağlayıcıları|WCF Veri Hizmetleri, veri modelini geç bağlanan veri türlerine göre dinamik olarak tanımlamanızı sağlayan bir sağlayıcılar kümesi içerir. Bu arabirimleri, ortaya çıkarmakta olan veriler uygulama tasarlanmakta olduğunda veya Entity Framework ya da yansıma sağlayıcıları yeterli olmadığında uygulamanız gerekir. Daha fazla bilgi için bkz. [özel veri hizmeti sağlayıcıları](custom-data-service-providers-wcf-data-services.md).|  
  
## <a name="other-data-service-providers"></a>Diğer veri hizmeti sağlayıcıları  

 WCF Veri Hizmetleri, diğer sağlayıcılardan birini kullanarak tanımlanan bir veri kaynağının performansını geliştiren aşağıdaki ek veri hizmeti sağlayıcısına sahiptir.  
  
|Sağlayıcı|Açıklama|  
|--------------|-----------------|  
|Akış sağlayıcısı|Bu sağlayıcı, WCF Veri Hizmetleri kullanarak ikili büyük nesne veri türlerini kullanıma sunmanızı sağlar. Bir akış sağlayıcısı, arabirimi uygulayarak oluşturulur <xref:System.Data.Services.Providers.IDataServiceStreamProvider> . Bu sağlayıcı, herhangi bir veri kaynağı sağlayıcısıyla birlikte uygulanabilir. Daha fazla bilgi için bkz. [Akış sağlayıcısı](streaming-provider-wcf-data-services.md).|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetlerini Tanımlama](defining-wcf-data-services.md)
- [Veri Hizmeti Yapılandırma](configuring-the-data-service-wcf-data-services.md)
- [Veri Hizmeti Barındırma](hosting-the-data-service-wcf-data-services.md)

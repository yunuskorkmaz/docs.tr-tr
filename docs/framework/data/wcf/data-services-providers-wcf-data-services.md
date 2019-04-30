---
title: Veri Hizmetleri sağlayıcıları (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: a0160b1b-3d9c-4cc8-8391-cb0986a60a41
ms.openlocfilehash: 7a870eb0c85fa6ed208341a3ac10dce8bb0724bc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61765706"
---
# <a name="data-services-providers-wcf-data-services"></a>Veri Hizmetleri sağlayıcıları (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] verileri olarak açığa çıkarmak için birden çok sağlayıcı modelini destekler bir [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] akış. Bu konu, en iyi sağlamak için bilgi sağlamaktadır [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] veri kaynağınız için sağlayıcı.  
  
## <a name="data-source-providers"></a>Veri kaynak sağlayıcıları  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Veri hizmetinin veri modeli tanımlamak için aşağıdaki sağlayıcılarını destekler.  
  
|Sağlayıcı|Açıklama|  
|--------------|-----------------|  
|Entity Framework sağlayıcısı|Bu sağlayıcı ADO.NET varlık çerçevesi ilişkisel verileri bir veri hizmeti ile ilişkisel verilere eşleyen bir veri modeli tanımlayarak kullanmanızı sağlamak için kullanır. Veri kaynağınız, SQL Server veya üçüncü taraf sağlayıcı desteği için Entity Framework ile başka bir veri kaynağı olabilir. SQL Server veritabanı gibi bir ilişkisel veri kaynağına sahip olduğunuzda, Entity Framework sağlayıcısı kullanmanız gerekir. Daha fazla bilgi için [Entity Framework sağlayıcısı](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md).|  
|Yansıma sağlayıcısı|Bu sağlayıcı örnekleri olarak kullanıma sunulabilir var olan veri sınıfları dayalı bir veri modeli tanımlamanızı etkinleştirmek için yansıtma kullanır <xref:System.Linq.IQueryable%601> arabirimi. Güncelleştirmeleri uygulayarak etkin <xref:System.Data.Services.IUpdatable> arabirimi. Bu LINQ to SQL tarafından oluşturulan veya türü belirtilmiş veri kümesi tarafından tanımlandığı gibi çalışma zamanında tanımlanan statik veri sınıfları varsa, bu sağlayıcı kullanmanız gerekir. Daha fazla bilgi için [yansıma sağlayıcısı](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md).|  
|Özel Veri Hizmeti Sağlayıcıları|[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] dinamik olarak geç bağlanan veri türlerine göre bir veri modeli tanımlamanızı sağlayan sağlayıcıları kümesini içerir. Bu arabirimler uygulama tasarlandığında açıklanmasını veri bilinmiyor veya Entity Framework veya yansıma sağlayıcısı yeterli olmadığında uygulamalıdır. Daha fazla bilgi için [özel veri hizmeti sağlayıcılarını](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md).|  
  
## <a name="other-data-service-providers"></a>Diğer veri hizmeti sağlayıcıları  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] tanımlanan diğer sağlayıcılardan birini kullanarak bir veri kaynağının performansını geliştiren aşağıdaki ek veri hizmeti sağlayıcısı sahip.  
  
|Sağlayıcı|Açıklama|  
|--------------|-----------------|  
|Akış sağlayıcısı|Bu sağlayıcı kullanarak ikili büyük nesne veri türlerini kullanıma sunmanıza olanak sağlayan [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Akış sağlayıcısı uygulayarak oluşturulur <xref:System.Data.Services.Providers.IDataServiceStreamProvider> arabirimi. Bu sağlayıcı hiçbir veri kaynağı sağlayıcı ile birlikte uygulanır. Daha fazla bilgi için [Akış sağlayıcısı](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md).|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetlerini Tanımlama](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
- [Veri Hizmeti Yapılandırma](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)
- [Veri Hizmeti Barındırma](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md)

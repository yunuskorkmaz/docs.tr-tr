---
title: "Bir hizmet (WCF Veri Hizmetleri) olarak verilerinizi gösterme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, configuring
- getting started, WCF Data Services
- WCF Data Services, getting started
ms.assetid: df0bbcee-f66f-4a88-abb4-4e73c8b9c908
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 55e0bc058b92540c9b11965854d38e8d124e205c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="exposing-your-data-as-a-service-wcf-data-services"></a>Bir hizmet (WCF Veri Hizmetleri) olarak verilerinizi gösterme
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]Verilerinizi olarak kullanıma sunmak için hizmetleri daha kolay tanımlamak etkinleştirmek için Visual Studio ile tümleşir [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] akışları. Veri hizmeti oluşturma kullanıma sunan bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akış aşağıdaki temel adımları içerir:  
  
1.  **Tanımlamak** **veri modeli**. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]yerel olarak temel alan veri modelleri destekleyen [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md). Daha fazla bilgi için bkz: [nasıl yapılır: bir ADO.NET Entity Framework veri kaynağına veri kullanarak hizmet oluşturma](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md).  
  
     [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]Ayrıca bir örneğini döndüren ortak dil çalışma zamanı (CLR) nesnelere bağlı veri modelleri destekler <xref:System.Linq.IQueryable%601> arabirimi. Bu, listeler, dizileri ve .NET Framework koleksiyonlarda temelinde Veri Hizmetleri dağıtmanıza olanak tanır. Etkinleştirmek için oluşturma, güncelleştirme ve silme işlemleri de uygulamalıdır bu veri yapıları <xref:System.Data.Services.IUpdatable> arabirimi. Daha fazla bilgi için bkz: [nasıl yapılır: yansıma sağlayıcı veri kullanarak hizmet oluşturma](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md).  
  
     Daha Gelişmiş senaryolar için [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] geç bağlama veri türlerine bağlı bir veri modeli tanımlamanıza olanak sağlayan sağlayıcıları kümesi içerir. Daha fazla bilgi için bkz: [özel veri hizmeti sağlayıcıları](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md).  
  
2.  **Veri Hizmeti oluşturun.** Öğesinden devralınan bir sınıf en temel veri hizmeti sunan <xref:System.Data.Services.DataService%601> sınıfının bir türü `T` olan ad alanı tam varlık kapsayıcısının adı. Daha fazla bilgi için bkz: [tanımlayan WCF Veri Hizmetleri](../../../../docs/framework/data/wcf/defining-wcf-data-services.md).  
  
3.  **Veri Hizmeti yapılandırın.** Varsayılan olarak, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] bir varlık kapsayıcısı tarafından sunulan kaynaklara erişimi devre dışı bırakır. <xref:System.Data.Services.DataServiceConfiguration> Arabirimi kaynaklarına erişimi yapılandırmak ve işlemleri hizmet, desteklenen bir sürümü olanak tanır [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]ve davranışları veya yapabilirsiniz varlıkların sayısı toplu işleme gibi diğer hizmet geneli davranışları tanımlamak için tek bir yanıtta döndürülen. Daha fazla bilgi için bkz: [veri hizmeti yapılandırma](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).  
  
 Northwind örnek veritabanını temel alan bir basit veri hizmet oluşturma örneği için bkz: [Hızlı Başlangıç](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Başlarken](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)  
 [Genel bakış](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)

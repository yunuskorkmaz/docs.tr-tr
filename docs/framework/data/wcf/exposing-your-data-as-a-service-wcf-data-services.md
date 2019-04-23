---
title: Verilerinizi (WCF Veri Hizmetleri) hizmet kullanıma sunma
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
- getting started, WCF Data Services
- WCF Data Services, getting started
ms.assetid: df0bbcee-f66f-4a88-abb4-4e73c8b9c908
ms.openlocfilehash: 3c0763f21940831f401194356dc25b0d99c8d6f2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59308542"
---
# <a name="expose-your-data-as-a-service-wcf-data-services"></a>Verilerinizi (WCF Veri Hizmetleri) hizmet olarak kullanıma sunma

WCF Veri Hizmetleri tümleştirir, hizmetler, veri olarak kullanıma sunmak için daha kolay tanımlamak sağlamak için Visual Studio ile [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] akışları. Bir OData akışına kullanıma sunan bir veri hizmeti oluşturma aşağıdaki temel adımları içerir:

1. **Veri modelini tanımlar.** WCF Veri Hizmetleri temel alan veri modellerini yerel olarak destekleyen [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md). Daha fazla bilgi için [nasıl yapılır: Bir ADO.NET varlık çerçevesi veri kaynağı kullanarak veri hizmeti oluşturma](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md).

     WCF Data Services örneği döndüren ortak dil çalışma zamanı (CLR) nesnelerine dayalı veri modelleri de destekler <xref:System.Linq.IQueryable%601> arabirimi. Bu listeler, diziler ve Koleksiyonlar .NET Framework'teki temel alan veri hizmetlerini dağıtmanızı sağlar. Etkinleştirmek için oluşturma, güncelleştirme ve silme işlemleri bu veri yapıları üzerinde ayrıca uygulamalıdır <xref:System.Data.Services.IUpdatable> arabirimi. Daha fazla bilgi için [nasıl yapılır: Yansıma sağlayıcısını kullanarak veri hizmeti oluşturma](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md).

     Daha Gelişmiş senaryolar için WCF Veri Hizmetleri, geç bağlanan veri türlerine göre bir veri modeli tanımlamanızı sağlayan sağlayıcıları kümesini içerir. Daha fazla bilgi için [özel veri hizmeti sağlayıcılarını](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md).

2. **Veri Hizmeti oluşturun.** En temel veri hizmeti devralınan bir sınıfı gösterir <xref:System.Data.Services.DataService%601> türüne sahip bir sınıf `T` varlık kapsayıcısının yani ad alanıyla nitelenen adı. Daha fazla bilgi için [Defining WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md).

3. **Veri hizmetini yapılandırın.** Varsayılan olarak, WCF Veri Hizmetleri bir varlık kapsayıcısı tarafından kullanılan kaynaklara erişimi devre dışı bırakır. <xref:System.Data.Services.DataServiceConfiguration> Arabirimi, kaynaklara erişimi yapılandırma ve hizmet işlemlerine, desteklenen OData sürümü belirtin ve döndürülebilecek varlık davranışları veya en büyük toplu işleme gibi diğer hizmet kapsamındaki davranışları tanımlamanızı sağlar tek bir yanıtta. Daha fazla bilgi için [veri hizmeti yapılandırma](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).

Northwind örnek veritabanını temel alan bir basit veri hizmeti oluşturma örneği için bkz: [hızlı](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Başlarken](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)
- [Genel bakış](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)
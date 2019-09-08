---
title: Verilerinizi hizmet olarak gösterme (WCF Veri Hizmetleri)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
- getting started, WCF Data Services
- WCF Data Services, getting started
ms.assetid: df0bbcee-f66f-4a88-abb4-4e73c8b9c908
ms.openlocfilehash: 1dc1f0ec12c50c4c97b141a34b468e3367ead75e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780305"
---
# <a name="expose-your-data-as-a-service-wcf-data-services"></a>Verilerinizi hizmet olarak kullanıma sunma (WCF Veri Hizmetleri)

WCF veri Hizmetleri, verilerinizi akışlar olarak [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] kullanıma sunmak için daha kolay bir şekilde Hizmetleri tanımlamanızı sağlamak üzere Visual Studio ile tümleşir. OData akışını kullanıma sunan bir veri hizmeti oluşturmak aşağıdaki temel adımları içerir:

1. **Veri modelini tanımlayın.** WCF Veri Hizmetleri yerel olarak [ADO.NET Entity Framework](../adonet/ef/index.md)dayalı veri modellerini destekler. Daha fazla bilgi için [nasıl yapılır: Bir ADO.NET Entity Framework veri kaynağı](create-a-data-service-using-an-adonet-ef-data-wcf.md)kullanarak veri hizmeti oluşturun.

     WCF veri Hizmetleri ayrıca, <xref:System.Linq.IQueryable%601> arabirimin bir örneğini döndüren ortak dil çalışma zamanı (CLR) nesnelerini temel alan veri modellerini destekler. Bu, .NET Framework listeleri, dizileri ve koleksiyonları temel alan veri hizmetlerini dağıtmanıza olanak sağlar. Bu veri yapıları üzerinde oluşturma, güncelleştirme ve silme işlemlerini etkinleştirmek için <xref:System.Data.Services.IUpdatable> arabirimi de uygulamanız gerekir. Daha fazla bilgi için [nasıl yapılır: Yansıma sağlayıcısını](create-a-data-service-using-rp-wcf-data-services.md)kullanarak bir veri hizmeti oluşturun.

     Daha gelişmiş senaryolar için WCF Veri Hizmetleri, geç bağlanan veri türlerine göre bir veri modeli tanımlamanızı sağlayan bir sağlayıcılar kümesi içerir. Daha fazla bilgi için bkz. [özel veri hizmeti sağlayıcıları](custom-data-service-providers-wcf-data-services.md).

2. **Veri hizmetini oluşturun.** En temel veri hizmeti, varlık kapsayıcısının ad alanı nitelikli adı olan <xref:System.Data.Services.DataService%601> bir tür `T` ile sınıfından devralan bir sınıfı kullanıma sunar. Daha fazla bilgi için bkz. [tanımlama WCF veri Hizmetleri](defining-wcf-data-services.md).

3. **Veri hizmetini yapılandırın.** Varsayılan olarak, WCF Veri Hizmetleri bir varlık kapsayıcısı tarafından açığa çıkarılan kaynaklara erişimi devre dışı bırakır. <xref:System.Data.Services.DataServiceConfiguration> Arabirim, kaynaklara ve hizmet işlemlerine erişimi yapılandırmanıza, desteklenen OData sürümünü belirtmenize ve toplu işlem davranışları ya da döndürülebilecek en fazla varlık sayısı gibi diğer hizmet genelinde davranışları tanımlamanızı sağlar tek bir yanıtta. Daha fazla bilgi için bkz. [veri hizmetini yapılandırma](configuring-the-data-service-wcf-data-services.md).

Northwind örnek veritabanına dayalı basit bir veri hizmetinin nasıl oluşturulacağı hakkında bir örnek için bkz. [hızlı başlangıç](quickstart-wcf-data-services.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Başlarken](getting-started-with-wcf-data-services.md)
- [Genel bakış](wcf-data-services-overview.md)

---
title: Verilerinizi hizmet olarak gösterme (WCF Veri Hizmetleri)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
- getting started, WCF Data Services
- WCF Data Services, getting started
ms.assetid: df0bbcee-f66f-4a88-abb4-4e73c8b9c908
ms.openlocfilehash: 71f26d7d41d112e13e6a77f0927c61d51b176b27
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975302"
---
# <a name="expose-your-data-as-a-service-wcf-data-services"></a>Verilerinizi hizmet olarak kullanıma sunma (WCF Veri Hizmetleri)

WCF Veri Hizmetleri, verilerinizi açık veri Protokolü (OData) akışları olarak kullanıma sunmak için daha kolay bir şekilde tanımlamanızı sağlamak üzere Visual Studio ile tümleşir. OData akışını kullanıma sunan bir veri hizmeti oluşturmak aşağıdaki temel adımları içerir:

1. **Veri modelini tanımlayın.** WCF Veri Hizmetleri yerel olarak [ADO.NET Entity Framework](../adonet/ef/index.md)dayalı veri modellerini destekler. Daha fazla bilgi için bkz. [nasıl yapılır: ADO.NET Entity Framework veri kaynağı kullanarak veri hizmeti oluşturma](create-a-data-service-using-an-adonet-ef-data-wcf.md).

     WCF Veri Hizmetleri ayrıca, <xref:System.Linq.IQueryable%601> arabiriminin bir örneğini döndüren ortak dil çalışma zamanı (CLR) nesnelerini temel alan veri modellerini destekler. Bu, .NET Framework listeleri, dizileri ve koleksiyonları temel alan veri hizmetlerini dağıtmanıza olanak sağlar. Bu veri yapıları üzerinde oluşturma, güncelleştirme ve silme işlemlerini etkinleştirmek için <xref:System.Data.Services.IUpdatable> arabirimini de uygulamanız gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: yansıma sağlayıcısını kullanarak veri hizmeti oluşturma](create-a-data-service-using-rp-wcf-data-services.md).

     Daha gelişmiş senaryolar için WCF Veri Hizmetleri, geç bağlanan veri türlerine göre bir veri modeli tanımlamanızı sağlayan bir sağlayıcılar kümesi içerir. Daha fazla bilgi için bkz. [özel veri hizmeti sağlayıcıları](custom-data-service-providers-wcf-data-services.md).

2. **Veri hizmetini oluşturun.** En temel veri hizmeti, varlık kapsayıcısının ad alanı nitelenmiş adı `T` bir tür olan <xref:System.Data.Services.DataService%601> sınıfından devralan bir sınıf sunar. Daha fazla bilgi için bkz. [tanımlama WCF veri Hizmetleri](defining-wcf-data-services.md).

3. **Veri hizmetini yapılandırın.** Varsayılan olarak, WCF Veri Hizmetleri bir varlık kapsayıcısı tarafından açığa çıkarılan kaynaklara erişimi devre dışı bırakır. <xref:System.Data.Services.DataServiceConfiguration> arabirimi, kaynaklara ve hizmet işlemlerine erişimi yapılandırmanıza, desteklenen OData sürümünü belirtmenize ve toplu işlem davranışları ya da tek bir yanıtta döndürülebilecek maksimum varlık sayısı gibi diğer hizmet genelindeki davranışları tanımlamanızı sağlar. Daha fazla bilgi için bkz. [veri hizmetini yapılandırma](configuring-the-data-service-wcf-data-services.md).

Northwind örnek veritabanına dayalı basit bir veri hizmetinin nasıl oluşturulacağı hakkında bir örnek için bkz. [hızlı başlangıç](quickstart-wcf-data-services.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Başlarken](getting-started-with-wcf-data-services.md)
- [Genel bakış](wcf-data-services-overview.md)

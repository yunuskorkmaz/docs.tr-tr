---
title: WCF Veri Hizmetleri 4.5
ms.date: 03/30/2017
helpviewer_keywords:
- Astoria
- WCF Data Services, getting started
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
ms.openlocfilehash: 9ece2fe051855d0fd39556f56a4343ead2c437bc
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45616739"
---
# <a name="wcf-data-services-45"></a>WCF Veri Hizmetleri 4.5

WCF Veri Hizmetleri (eski adıyla "ADO.NET Data Services" da bilinir) kullanan hizmetler oluşturmanıza olanak tanıyan .NET Framework'ün bir bileşenidir [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] semantiği kullanarak Web veya intranet üzerinden verileri kullanır ve [ temsili durum aktarımı (REST)](https://go.microsoft.com/fwlink/?LinkId=113919). OData veri tarafından bir URI'leri adreslenebilir kaynakları olarak kullanıma sunar. Veri erişim ve GET, PUT, POST ve DELETE, standart HTTP fiillerini kullanarak değiştirildi. OData varlık ilişkisi kuralları kullanan [varlık veri modeli](../../../../docs/framework/data/adonet/entity-data-model.md) kaynakları ilişkilendirmeleri ilgili varlık kümeleri olarak kullanıma sunmak için.

Adresleme ve kaynaklar güncelleştiriliyor, WCF Veri Hizmetleri OData protokolünü kullanır. Bu şekilde, OData destekleyen herhangi bir istemciden Bu hizmetlere erişebilirsiniz. OData istek ve iyi bilinen aktarma biçimleri kullanarak veri kaynaklarına yazma olanak tanır: Atom, bir dizi değişimi ve veri XML ve JavaScript nesne gösterimi (JSON) güncelleştirmek için standartları AJAX içinde yaygın olarak kullanılan bir metin tabanlı veri exchange biçimi uygulama.

WCF Veri Hizmetleri OData akışları olarak, çeşitli kaynaklardan veri kaynağı verilerini açığa çıkarabilir. Visual Studio Araçları bir ADO.NET varlık çerçevesi veri modelini kullanarak bir OData tabanlı bir hizmet oluşturmak için kolaylaştırır. Ortak dil çalışma zamanı (CLR) sınıflar ve hatta geç bağlanan veya türsüz veriler temel alınarak OData akışları da oluşturabilirsiniz.

WCF Veri Hizmetleri, bir dizi istemci kitaplıkları, genel .NET Framework istemci uygulamaları için diğeri Silverlight tabanlı uygulamalar için özellikle de içerir. Bir OData akışına gibi .NET Framework ve Silverlight ortamlarından eriştiğinizde bu istemci kitaplıklarının nesne tabanlı programlama modeli sağlar.

## <a name="where-should-i-start"></a>Nereden başlamalıyım?

Alanlarınızı bağlı olarak aşağıdaki konulardan birindeki WCF Data Services ile çalışmaya başlama göz önünde bulundurun.

Hemen istediğiniz...

-   [Hızlı başlangıç](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)

-   [Başlarken](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)

-   [Silverlight hızlı başlangıç](https://go.microsoft.com/fwlink/?LinkID=192782)

-   [Windows Phone geliştirme için Silverlight hızlı başlangıç](https://go.microsoft.com/fwlink/?LinkID=214535)

Yalnızca bazı kod göster...

-   [Hızlı başlangıç](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)

-   [Nasıl yapılır: Veri Hizmeti Sorguları Yürütme](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)

-   [Nasıl yapılır: Windows Presentation Foundation Öğelerine Veri Bağlama](../../../../docs/framework/data/wcf/bind-data-to-wpf-elements-wcf-data-services.md)

OData hakkında daha fazla bilgi edinmek istiyorsanız...

 -   [Teknik İnceleme: OData ile tanışın](https://go.microsoft.com/fwlink/?LinkId=220867)

-   [Açık Veri Protokolü Web sitesi](https://go.microsoft.com/fwlink/?LinkID=184554)

-   [OData: SDK'sı](https://go.microsoft.com/fwlink/?LinkID=185248)

-   [OData: Sık sorulan sorular](https://go.microsoft.com/fwlink/?LinkId=185867)

Bazı videoları izlemek istediğiniz...

-   [WCF Veri Hizmetleri için Başlangıç Kılavuzu](https://go.microsoft.com/fwlink/?LinkId=220864)

-   [Geliştirici videoları WCF Veri Hizmetleri](https://go.microsoft.com/fwlink/?LinkId=220861)

-   [OData: Geliştiriciler Web sitesi](https://go.microsoft.com/fwlink/?LinkId=185866)

Uçtan uca örnekler görmek istiyorsanız...

-   [WCF Veri Hizmetleri belgeleri örnekleri MSDN Örnekler Galerisi](https://go.microsoft.com/fwlink/?LinkID=220865)

-   [MSDN Örnekler Galerisi örnekleri diğer WCF Veri Hizmetleri](https://go.microsoft.com/fwlink/?LinkId=220866)

-   [OData: SDK'sı](https://go.microsoft.com/fwlink/?LinkID=185248)

Bu Visual Studio ile nasıl tümleştirilir?

-   [Veri Hizmeti İstemci Kitaplığı Oluşturma](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)

-   [Veri Hizmeti Oluşturma](../../../../docs/framework/data/wcf/creating-the-data-service.md)

-   [Entity Framework Sağlayıcısı](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)

İle neler yapabilirim?

-   [Genel bakış](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)

-   [Teknik İnceleme: OData ile tanışın](https://go.microsoft.com/fwlink/?LinkId=220867)

-   [Uygulama Senaryoları](../../../../docs/framework/data/wcf/application-scenarios-wcf-data-services.md)

Silverlight kullanmak istediğiniz...

-   [Silverlight hızlı başlangıç](https://go.microsoft.com/fwlink/?LinkID=192782)

-   [WCF Veri Hizmetleri (Silverlight)](https://go.microsoft.com/fwlink/?LinkID=143149)

-   [Silverlight ile çalışmaya başlama](https://go.microsoft.com/fwlink/?LinkId=148366)

LINQ kullanmak istediğiniz...

-   [Veri Hizmetini Sorgulama](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)

-   [LINQ Konuları](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md)

-   [Nasıl yapılır: Veri Hizmeti Sorguları Yürütme](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)

Yine de bazı ek bilgiler ihtiyacım...

-   [WCF Veri Hizmetleri ekibi blogu](https://go.microsoft.com/fwlink/?LinkID=150511)

-   [Kaynaklar](../../../../docs/framework/data/wcf/wcf-data-services-resources.md)

-   [WCF Veri Hizmetleri Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=220868)

-   [Açık Veri Protokolü Web sitesi](https://go.microsoft.com/fwlink/?LinkID=184554)

## <a name="in-this-section"></a>Bu Bölümde

 [Genel bakış](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)

 WCF veri hizmetlerinde kullanılabilen işlevler ve özellikler hakkında genel bir bakış sağlar.

 [WCF veri hizmetlerinde yenilikler nelerdir?](https://msdn.microsoft.com/library/cf22cad5-b8d9-472b-8d7c-b863b64eaae8)

 WCF Veri Hizmetleri ve yeni OData özellikleri için destek yeni işlevler açıklanmaktadır.

 [Başlarken](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)

 Kullanıma sunma ve WCF veri hizmetlerini kullanarak OData akışları kullanma açıklar.

 [WCF Veri Hizmetlerini Tanımlama](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)

 Oluşturma ve OData akışları kullanıma sunan bir veri hizmeti yapılandırma açıklanır.

 [WCF Veri Hizmetleri İstemci Kitaplığı](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)

 Bir .NET Framework istemci uygulamasından OData akışları kullanmak için istemci kitaplıkları kullanmayı açıklar.

## <a name="see-also"></a>Ayrıca Bkz.

- [Temsili durum aktarımı (REST)](https://go.microsoft.com/fwlink/?LinkId=113919)

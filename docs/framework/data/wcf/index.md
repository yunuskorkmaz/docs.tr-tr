---
title: WCF Veri Hizmetleri 4.5
ms.date: 03/30/2017
helpviewer_keywords:
- Astoria
- WCF Data Services, getting started
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
ms.openlocfilehash: 017fe2177cf824d461b4c51ea805f75b6ddbe064
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70779994"
---
# <a name="wcf-data-services-45"></a>WCF Veri Hizmetleri 4.5

WCF veri Hizmetleri (eskiden "ADO.NET Data Services" olarak bilinirdi), [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] [temsili durumunun semantiğini kullanarak Web veya intranet üzerinden veri sergilemek ve kullanmak için kullanan hizmetler oluşturmanıza olanak sağlayan bir .NET Framework bileşenidir. Aktarım (REST)](https://go.microsoft.com/fwlink/?LinkId=113919). OData, verileri URI 'Ler tarafından adreslenebilir kaynaklar olarak kullanıma sunar. Al, koy, POST ve DELETE için standart HTTP fiilleri kullanılarak verilere erişilir ve değiştirilir. OData, kaynakları ilişkilendirmeler ile ilgili varlık kümeleri olarak göstermek için [varlık veri modeli](../adonet/entity-data-model.md) varlık ilişkisi kurallarını kullanır.

WCF Veri Hizmetleri, kaynakları adresleme ve güncelleştirme için OData protokolünü kullanır. Bu şekilde, bu hizmetlere OData destekleyen herhangi bir istemciden erişebilirsiniz. OData, iyi bilinen aktarım biçimlerini kullanarak kaynaklara veri yazmanızı ve bunları yazmanızı sağlar: Atom, veri değişimi ve güncelleştirme için bir standartlar kümesi JavaScript Nesne Gösterimi ve AJAX uygulamalarında yaygın olarak kullanılan metin tabanlı bir veri değişim biçimidir.

WCF Veri Hizmetleri, çeşitli kaynaklardan kaynaklanan verileri OData akışları olarak kullanıma sunar. Visual Studio Araçları, bir ADO.NET Entity Framework veri modeli kullanarak OData tabanlı bir hizmet oluşturmanızı kolaylaştırır. Ayrıca, ortak dil çalışma zamanı (CLR) sınıflarını ve hatta geç bağlı veya yazılmamış verileri temel alan OData akışları da oluşturabilirsiniz.

WCF Veri Hizmetleri ayrıca, biri genel .NET Framework istemci uygulamaları ve özel olarak Silverlight tabanlı uygulamalar için başka bir istemci kitaplıkları kümesi de içerir. Bu istemci kitaplıkları, .NET Framework ve Silverlight gibi ortamlardan bir OData akışına eriştiğinizde nesne tabanlı bir programlama modeli sağlar.

## <a name="where-should-i-start"></a>Nereden başlamalıyım?

İlgi alanlarınıza bağlı olarak, aşağıdaki konulardan birinde WCF Veri Hizmetleri kullanmaya başlayın.

Hemen hızlı bir şekilde geçmek istiyorum...

- [Hızlı başlangıç](quickstart-wcf-data-services.md)

- [Başlarken](getting-started-with-wcf-data-services.md)

- [Silverlight hızlı başlangıç](https://go.microsoft.com/fwlink/?LinkID=192782)

- [Windows Phone geliştirme için Silverlight hızlı başlangıcı](https://go.microsoft.com/fwlink/?LinkID=214535)

Yalnızca bana bir kod göster...

- [Hızlı başlangıç](quickstart-wcf-data-services.md)

- [Nasıl yapılır: Veri hizmeti sorgularını yürütme](how-to-execute-data-service-queries-wcf-data-services.md)

- [Nasıl yapılır: Windows Presentation Foundation öğelerine veri bağlama](bind-data-to-wpf-elements-wcf-data-services.md)

OData hakkında daha fazla bilgi edinmek istiyorum...

- [İncelemesi OData 'e giriş](https://go.microsoft.com/fwlink/?LinkId=220867)

- [Veri Protokolü Web sitesini aç](https://go.microsoft.com/fwlink/?LinkID=184554)

- [OData 'SININ](https://go.microsoft.com/fwlink/?LinkID=185248)

- [OData Sık Sorulan Sorular](https://go.microsoft.com/fwlink/?LinkId=185867)

Bazı videoları izlemek istiyorum...

- [WCF Veri Hizmetleri için başlangıç kılavuzu](https://go.microsoft.com/fwlink/?LinkId=220864)

- [Geliştirici videolarını WCF Veri Hizmetleri](https://go.microsoft.com/fwlink/?LinkId=220861)

- [OData Geliştirici Web sitesi](https://go.microsoft.com/fwlink/?LinkId=185866)

Uçtan uca örnekleri görmek istiyorum...

- [MSDN örnekleri galerisinde WCF Veri Hizmetleri belge örnekleri](https://go.microsoft.com/fwlink/?LinkID=220865)

- [MSDN örnekleri galerisinde diğer WCF Veri Hizmetleri örnekleri](https://go.microsoft.com/fwlink/?LinkId=220866)

- [OData 'SININ](https://go.microsoft.com/fwlink/?LinkID=185248)

Visual Studio ile nasıl tümleştirilir?

- [Veri Hizmeti İstemci Kitaplığı Oluşturma](generating-the-data-service-client-library-wcf-data-services.md)

- [Veri Hizmeti Oluşturma](creating-the-data-service.md)

- [Entity Framework Sağlayıcısı](entity-framework-provider-wcf-data-services.md)

Bununla ne yapabilirim?

- [Genel bakış](wcf-data-services-overview.md)

- [İncelemesi OData 'e giriş](https://go.microsoft.com/fwlink/?LinkId=220867)

- [Uygulama Senaryoları](application-scenarios-wcf-data-services.md)

Silverlight kullanmak istiyorum...

- [Silverlight hızlı başlangıç](https://go.microsoft.com/fwlink/?LinkID=192782)

- [WCF Veri Hizmetleri (Silverlight)](https://go.microsoft.com/fwlink/?LinkID=143149)

- [Silverlight 'ı kullanmaya başlama](https://go.microsoft.com/fwlink/?LinkId=148366)

LINQ kullanmak istiyorum...

- [Veri Hizmetini Sorgulama](querying-the-data-service-wcf-data-services.md)

- [LINQ Konuları](linq-considerations-wcf-data-services.md)

- [Nasıl yapılır: Veri hizmeti sorgularını yürütme](how-to-execute-data-service-queries-wcf-data-services.md)

Hala daha fazla bilgi gerekiyor...

- [Ekip Blogu WCF Veri Hizmetleri](https://go.microsoft.com/fwlink/?LinkID=150511)

- [Kaynaklar](wcf-data-services-resources.md)

- [WCF Veri Hizmetleri Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=220868)

- [Veri Protokolü Web sitesini aç](https://go.microsoft.com/fwlink/?LinkID=184554)

## <a name="in-this-section"></a>Bu Bölümde

[Genel bakış](wcf-data-services-overview.md)

WCF Veri Hizmetleri ' de kullanılabilen özellikler ve işlevlere genel bir bakış sağlar.

[WCF Veri Hizmetleri 5,0 ' deki yenilikler](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))

WCF Veri Hizmetleri yeni işlevleri ve yeni OData özellikleri desteğini açıklar.

[Başlarken](getting-started-with-wcf-data-services.md)

WCF Veri Hizmetleri kullanarak OData akışlarını kullanıma sunma ve kullanma açıklanmaktadır.

[WCF Veri Hizmetlerini Tanımlama](defining-wcf-data-services.md)

OData akışlarını kullanıma sunan bir veri hizmetinin nasıl oluşturulduğunu ve yapılandırılacağını açıklar.

[WCF Veri Hizmetleri İstemci Kitaplığı](wcf-data-services-client-library.md)

İstemci kitaplıklarının, bir .NET Framework istemci uygulamasından OData akışlarını kullanmak için nasıl kullanılacağını açıklar.

## <a name="see-also"></a>Ayrıca bkz.

- [Temsili durum aktarımı (REST)](https://go.microsoft.com/fwlink/?LinkId=113919)

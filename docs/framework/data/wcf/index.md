---
title: WCF Veri Hizmetleri 4.5
description: REST semantiğini kullanarak verileri kullanıma sunmak ve kullanmak için hizmetleri destekleyen bir .NET Framework bileşeni olan WCF Veri Hizmetleri hakkında bilgi edinin.
ms.date: 03/30/2017
helpviewer_keywords:
- Astoria
- WCF Data Services, getting started
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
ms.openlocfilehash: ca6b196e8c910f97ead6d1df5b6c0dd6c49c68a4
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247758"
---
# <a name="wcf-data-services-45"></a>WCF Veri Hizmetleri 4.5

WCF Veri Hizmetleri (eskiden "ADO.NET Data Services" olarak bilinirdi), [temsili durum aktarımı (REST)](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm)semantiğini kullanarak Web veya intranet üzerinden veri sunmak ve kullanmak Için açık veri Protokolü 'Nü (OData) kullanan hizmetler oluşturmanızı sağlayan bir .NET Framework bileşenidir. OData, verileri URI 'Ler tarafından adreslenebilir kaynaklar olarak kullanıma sunar. Al, koy, POST ve DELETE için standart HTTP fiilleri kullanılarak verilere erişilir ve değiştirilir. OData, kaynakları ilişkilendirmeler ile ilgili varlık kümeleri olarak göstermek için [varlık veri modeli](../adonet/entity-data-model.md) varlık ilişkisi kurallarını kullanır.

WCF Veri Hizmetleri, kaynakları adresleme ve güncelleştirme için OData protokolünü kullanır. Bu şekilde, bu hizmetlere OData destekleyen herhangi bir istemciden erişebilirsiniz. OData, iyi bilinen aktarım biçimlerini kullanarak kaynaklara istek yapmanızı ve veri yazmanızı sağlar: Atom, verileri XML olarak değiştirme ve güncelleştirme için bir standartlar kümesi ve AJAX uygulamalarında yaygın olarak kullanılan metin tabanlı veri değişim biçimi JavaScript Nesne Gösterimi (JSON).

WCF Veri Hizmetleri, çeşitli kaynaklardan kaynaklanan verileri OData akışları olarak kullanıma sunar. Visual Studio Araçları, bir ADO.NET Entity Framework veri modeli kullanarak OData tabanlı bir hizmet oluşturmanızı kolaylaştırır. Ayrıca, ortak dil çalışma zamanı (CLR) sınıflarını ve hatta geç bağlı veya yazılmamış verileri temel alan OData akışları da oluşturabilirsiniz.

WCF Veri Hizmetleri ayrıca, biri genel .NET Framework istemci uygulamaları ve özel olarak Silverlight tabanlı uygulamalar için başka bir istemci kitaplıkları kümesi de içerir. Bu istemci kitaplıkları, .NET Framework ve Silverlight gibi ortamlardan bir OData akışına eriştiğinizde nesne tabanlı bir programlama modeli sağlar.

## <a name="where-should-i-start"></a>Nereden başlamalıyım?

İlgi alanlarınıza bağlı olarak, aşağıdaki konulardan birinde WCF Veri Hizmetleri kullanmaya başlayın.

Hemen hızlı bir şekilde geçmek istiyorum...

- [Hızlı Başlangıç](quickstart-wcf-data-services.md)

- [Başlarken](getting-started-with-wcf-data-services.md)

Yalnızca bana bir kod göster...

- [Hızlı Başlangıç](quickstart-wcf-data-services.md)

- [Nasıl yapılır: Veri Hizmeti Sorguları Yürütme](how-to-execute-data-service-queries-wcf-data-services.md)

- [Nasıl yapılır: Windows Presentation Foundation Öğelerine Veri Bağlama](bind-data-to-wpf-elements-wcf-data-services.md)

OData hakkında daha fazla bilgi edinmek istiyorum...

- [Teknik İnceleme: OData 'e giriş](https://download.microsoft.com/download/E/5/A/E5A59052-EE48-4D64-897B-5F7C608165B8/IntroducingOData.pdf)
- [Veri Protokolü Web sitesini aç](https://www.odata.org/)
- [OData: SDK](https://www.odata.org/ecosystem/)

Uçtan uca örnekleri görmek istiyorum...

- [Hızlı başlangıç WCF Veri Hizmetleri](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client))
- [OData SDK-örnek kod](https://www.odata.org/ecosystem/#sdk)

Visual Studio ile nasıl tümleştirilir?

- [Veri Hizmeti İstemci Kitaplığı Oluşturma](generating-the-data-service-client-library-wcf-data-services.md)

- [Veri Hizmeti Oluşturma](creating-the-data-service.md)

- [Entity Framework Sağlayıcısı](entity-framework-provider-wcf-data-services.md)

Bununla ne yapabilirim?

- [Genel Bakış](wcf-data-services-overview.md)

- [Uygulama senaryoları](application-scenarios-wcf-data-services.md)

LINQ kullanmak istiyorum...

- [Veri Hizmetini Sorgulama](querying-the-data-service-wcf-data-services.md)

- [LINQ Konuları](linq-considerations-wcf-data-services.md)

- [Nasıl yapılır: Veri Hizmeti Sorguları Yürütme](how-to-execute-data-service-queries-wcf-data-services.md)

Hala daha fazla bilgi gerekiyor...

- [Ekip Blogu WCF Veri Hizmetleri](https://docs.microsoft.com/archive/blogs/astoriateam/)

- [Kaynaklar](wcf-data-services-resources.md)

## <a name="in-this-section"></a>Bu Bölümde

[Genel Bakış](wcf-data-services-overview.md)

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

- [Temsili durum aktarımı (REST)](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm)

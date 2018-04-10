---
title: WCF Data Services 4.5
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Astoria
- WCF Data Services, getting started
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b5b27a51dcec17f72b86e77a7ee2ab773aec1dc3
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="wcf-data-services-45"></a>WCF Data Services 4.5
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)](eski adıyla "ADO.NET Veri Hizmetleri") kullanan hizmetler oluşturmanızı sağlayan .NET Framework'ün bir bileşen olan [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] semantiği kullanarak Web veya intranet üzerinden verileri kullanmak ve kullanıma sunmak için [temsili durum Transfer (REST)](http://go.microsoft.com/fwlink/?LinkId=113919). [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]Veri URI tarafından adreslenebilir kaynakları olarak kullanıma sunar. Veriler erişilen ve GET, PUT, POST ve DELETE standart HTTP fiillerini kullanarak değiştirildi. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]Varlık ilişkisi kuralları kullanan [varlık veri modeli](../../../../docs/framework/data/adonet/entity-data-model.md) kaynaklara göre ilişkileri ilişkili varlık kümesi olarak kullanıma sunmak için.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]kullanan [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] adresleme ve kaynakları güncelleştirmek için protokol. Bu şekilde, bu hizmetleri destekleyen herhangi bir istemciden erişebilirsiniz [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]İstek ve bilinen aktarımı biçimlerini kullanarak veri kaynaklarına yazma sağlar: Atom, değişim ve verileri XML ve JavaScript nesne gösterimi (JSON) güncelleştirme standartlarını kümesi AJAX uygulamada yaygın olarak kullanılan metin tabanlı veri exchange biçimi.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]çeşitli kaynaklardan kaynaklanan veri getirebilir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akışları. Visual Studio Araçları kolaylaştırmak oluşturmak için bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-bir ADO.NET Entity Framework veri modeli kullanarak hizmet tabanlı. Ayrıca oluşturabilirsiniz [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] ortak dil çalışma zamanı (CLR) sınıfları ve hatta geç bağlama veya türsüz veri akışları bağlı.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]Ayrıca istemci kitaplıkları, biri genel .NET Framework istemci uygulamaları için diğeri Silverlight tabanlı uygulamalar için özel olarak bir dizi içerir. Siz eriştiğinizde, bu istemci kitaplıkları, nesne tabanlı programlama modeli sağlar. bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] .NET Framework ve Silverlight gibi ortamlarından akış.  
  
## <a name="where-should-i-start"></a>Nereden başlamalıyım?  
 İle çalışmaya başlama alanlarınızı bağlı olarak göz önünde bulundurun [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] aşağıdaki konulardan birindeki.  
  
 Hemen istediğiniz...  
 -   [Hızlı başlangıç](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)  
  
-   [Başlarken](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)  
  
-   [Silverlight hızlı başlangıç](http://go.microsoft.com/fwlink/?LinkID=192782)  
  
-   [Windows Phone geliştirme için Silverlight hızlı başlangıç](http://go.microsoft.com/fwlink/?LinkID=214535)  
  
 Yalnızca bazı kodlar göster...  
 -   [Hızlı başlangıç](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)  
  
-   [Nasıl yapılır: Veri Hizmeti Sorguları Yürütme](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)  
  
-   [Nasıl yapılır: Windows Presentation Foundation Öğelerine Veri Bağlama](../../../../docs/framework/data/wcf/bind-data-to-wpf-elements-wcf-data-services.md)  
  
 Daha fazla bilgi almak istiyorum [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]...  
 -   [Teknik İnceleme: OData Tanıtımı](http://go.microsoft.com/fwlink/?LinkId=220867)  
  
-   [Açık Veri Protokolü Web sitesi](http://go.microsoft.com/fwlink/?LinkID=184554)  
  
-   [OData: SDK'sı](http://go.microsoft.com/fwlink/?LinkID=185248)  
  
-   [OData: Sık sorulan sorular](http://go.microsoft.com/fwlink/?LinkId=185867)  
  
 Bazı videolar izlemek istediğiniz...  
 -   [WCF Veri Hizmetleri için Başlangıç Kılavuzu](http://go.microsoft.com/fwlink/?LinkId=220864)  
  
-   [Geliştirici videolar WCF Veri Hizmetleri](http://go.microsoft.com/fwlink/?LinkId=220861)  
  
-   [OData: Geliştiricilerin Web sitesi](http://go.microsoft.com/fwlink/?LinkId=185866)  
  
 Uçtan uca örnekleri görmek istiyorum  
 -   [MSDN Örnekler Galerisi belgelerine örnekleri WCF Veri Hizmetleri](http://go.microsoft.com/fwlink/?LinkID=220865)  
  
-   [MSDN Örnekler Galerisi örnekleri diğer WCF Veri Hizmetleri](http://go.microsoft.com/fwlink/?LinkId=220866)  
  
-   [OData: SDK'sı](http://go.microsoft.com/fwlink/?LinkID=185248)  
  
 Bu Visual Studio ile nasıl tümleştiriliyor?  
 -   [Veri Hizmeti İstemci Kitaplığı Oluşturma](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)  
  
-   [Veri Hizmeti Oluşturma](../../../../docs/framework/data/wcf/creating-the-data-service.md)  
  
-   [Entity Framework Sağlayıcısı](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)  
  
 Bununla ne yapabilirim?  
 -   [Genel bakış](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)  
  
-   [Teknik İnceleme: OData Tanıtımı](http://go.microsoft.com/fwlink/?LinkId=220867)  
  
-   [Uygulama Senaryoları](../../../../docs/framework/data/wcf/application-scenarios-wcf-data-services.md)  
  
 Silverlight kullanmak istediğiniz...  
 -   [Silverlight hızlı başlangıç](http://go.microsoft.com/fwlink/?LinkID=192782)  
  
-   [WCF Veri Hizmetleri (Silverlight)](http://go.microsoft.com/fwlink/?LinkID=143149)  
  
-   [Silverlight ile çalışmaya başlama](http://go.microsoft.com/fwlink/?LinkId=148366)  
  
 Bir Windows Phone uygulaması oluşturmak istediğiniz...  
 -   [Windows Phone geliştirme için Silverlight hızlı başlangıç](http://go.microsoft.com/fwlink/?LinkID=214535)  
  
-   [Windows Phone için açık veri Protokolü (OData) istemcisi](http://go.microsoft.com/fwlink/?LinkID=208749)  
  
 LINQ kullanmak istediğiniz...  
 -   [Veri Hizmetini Sorgulama](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)  
  
-   [LINQ Konuları](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md)  
  
-   [Nasıl yapılır: Veri Hizmeti Sorguları Yürütme](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)  
  
 Hala bazı ek bilgiler ihtiyacım...  
 -   [WCF Veri Hizmetleri ekibi Web günlüğü](http://go.microsoft.com/fwlink/?LinkID=150511)  
  
-   [Kaynaklar](../../../../docs/framework/data/wcf/wcf-data-services-resources.md)  
  
-   [WCF Veri Hizmetleri Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=220868)  
  
-   [Açık Veri Protokolü Web sitesi](http://go.microsoft.com/fwlink/?LinkID=184554)  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Genel bakış](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)  
 Özellikleri ve işlevleri kullanılabilen genel bir bakış sağlar [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].  
  
 [WCF Veri Hizmetleri yenilikleri](http://msdn.microsoft.com/library/cf22cad5-b8d9-472b-8d7c-b863b64eaae8)  
 Yeni işlevsellik açıklanmaktadır [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] ve yeni desteği [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] özellikleri.  
  
 [Başlarken](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)  
 Kullanıma ve kullanmayı açıklar [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akışları kullanarak [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].  
  
 [WCF Veri Hizmetlerini Tanımlama](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 Oluşturma ve kullanıma sunan bir veri hizmeti yapılandırma açıklanır [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akışları.  
  
 [WCF Veri Hizmetleri İstemci Kitaplığı](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)  
 Kullanmak için istemci kitaplıkları kullanmayı açıklar [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akışları bir .NET Framework istemci uygulamasından.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Temsili durum aktarımı (REST)](http://go.microsoft.com/fwlink/?LinkId=113919)

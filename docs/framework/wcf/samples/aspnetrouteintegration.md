---
title: AspNetRouteIntegration
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0638ce0e-d053-47df-a447-688e447a03fb
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bf4f96116e8a4e687e7818796fa4b95e1b9b171a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="aspnetrouteintegration"></a>AspNetRouteIntegration
Bu örnek barındırmak gösterilmiştir bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ASP.NET kullanarak REST hizmeti yönlendirir. [Temel kaynak hizmeti](../../../../docs/framework/wcf/samples/basic-resource-service.md) örnek bu senaryo kendini barındıran bir sürümünü gösterir ve hizmet uygulaması derinlemesine anlatılmaktadır. Bu konu ASP.NET tümleştirme özelliğini odaklanır. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Bkz: ASP.NET yönlendirmesi <xref:System.Web.Routing>.  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hizmeti bir kaynak-yönelimli/REST şekilde müşteriler koleksiyonu kullanıma sunar. Olduğu gibi SOAP tabanlı [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet, hizmet .svc dosyasını kullanarak ASP.NET barındırılan. Hizmeti için URL .svc bulundurmak gerektirdiğinden ancak, bu HTTP senaryoları için tercih edilen çoğunlukla değildir. Ayrıca, hizmet kitaplığı birlikte .svc dosya dağıtılması gerekir. Bu örnekte gösterildiği gibi ASP.NET yolları kullanarak hizmet barındırma tarafından sınırlamalara önlenebilir.  
  
 Örnek ASP.NET hizmetinde ekleyerek barındıran bir <xref:System.ServiceModel.Activation.ServiceRoute> Global.asax dosyasındaki. <xref:System.ServiceModel.Activation.ServiceRoute> ('Service' Bu durumda), hizmet türünü belirtir. hizmeti için kullanacağınız hizmet ana bilgisayar üreteci türü (<xref:System.ServiceModel.Activation.WebServiceHostFactory> bu durumda) ve hizmet adresini temel HTTP ('~ / müşterilerin bu durumda).  
  
 Buna ek olarak, örnek ekler Web.config içeren <xref:System.Web.Routing.UrlRoutingModule> (ASP.NET yollara açmak için) ve hizmet için yapılandırmayı içerir. Özellikle, yapılandırma yapılandırır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] varsayılan hizmet <xref:System.ServiceModel.Description.WebHttpEndpoint> olan <xref:System.ServiceModel.Description.WebHttpEndpoint.HelpEnabled%2A> ayarını `true`. Sonuç olarak, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] altyapıyı oluşturur otomatik bir HTML tabanlı yardım sayfasına `http://localhost/Customers/help` sağlayan HTTP oluşturmak hakkında bilgi, nasıl bir örneği hizmeti ve hizmetin HTTP yanıtı – örneği için erişim istekleri Müşteri ayrıntıları XML ve JSON temsil edilir.  
  
 Müşteri koleksiyonu gösterme (ve daha genel olarak, herhangi bir kaynağa) bu şekilde URI'ler ve HTTP kullanmanın tek bir yolla bir hizmetiyle etkileşim bir istemcinin verir `GET`, `PUT`, `DELETE` ve `POST`.  
  
 İstemci projesindeki program.cs gösteren böyle bir istemci nasıl olabilir kullanılarak yazılan <xref:System.Net.HttpWebRequest>. Bu yalnızca bir erişmek için yolu olduğuna dikkat edin bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet. Diğer .NET Framework sınıfları gibi kullanarak hizmete erişmek mümkündür [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kanal fabrikası ve <xref:System.Net.WebClient>. SDK'sındaki diğer örnekleri (gibi [temel HTTP hizmeti](../../../../docs/framework/wcf/samples/basic-http-service.md) örnek ve [Otomatik Biçim Seçimi](../../../../docs/framework/wcf/samples/automatic-format-selection.md) örnek) ile iletişim kurmak için bu sınıfları kullanmayı gösteren bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet.  
  
 Bu örnek 3 projelerin oluşur:  
  
 Hizmet  
 ASP.NET barındırılan bir WCF HTTP hizmeti içeren bir Web uygulaması projesi.  
  
 İstemci  
 Hizmet çağrılar konsol uygulama projesi.  
  
 Ortak  
 İçeren paylaşılan bir kitaplık `Customer` istemci ve hizmet tarafından kullanılan türü. İstemci konsol uygulaması çalışırken, istemci hizmete istek yaptığında ve konsol penceresine yanıtlardan bilgileri yazar.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  ASP.NET yollar tümleştirme örnek çözümü açın [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
3.  Zaten açık değilse, "CTRL + W, S" tuşlarına basın açmak için **Çözüm Gezgini** penceresi.  
  
4.  Gelen **Çözüm Gezgini** sağ tıklatın, windows **hizmet** proje ve imleci üzerine getirin **hata ayıklama** bağlam menüsü seçeneğini böylece **Başlat Yeni örnek** bağlam menüsü görüntülenir ve seçin **Başlat yeni örnek**.  Bu hizmeti barındıran ASP.NET geliştirme sunucusu başlatır.  
  
5.  Gelen **Çözüm Gezgini** sağ tıklatın, windows **istemci** proje ve imleci üzerine getirin **hata ayıklama** bağlam menüsü seçeneğini böylece **yeni Başlat Örnek** bağlam menüsü görüntülenir ve seçin **Başlat yeni örnek**.  
  
6.  İstemci konsol penceresi görüntülenir ve çalışan hizmetin URI sağlar ve URI HTML sayfası çalışan hizmetin için yardımcı olur. Herhangi bir noktada, HTML Yardım sayfasına bir tarayıcıda yardım sayfasına URI'sini yazarak görüntüleyebilirsiniz. Örnek çalışırken, istemcinin geçerli etkinlik durumunu yazar.  
  
7.  İstemci konsol uygulaması sonlandırmak için herhangi bir tuşa basın.  
  
8.  Hata ayıklama hizmetini durdurmak için Shift + F5'e basın ve Windows bildirim alanında ASP.NET Geliştirme Sunucusu simgesini sağ tıklatın ve seçin **durdurmak** ve bağlam menüsünden.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AspNetRouteIntegration`  
  
## <a name="see-also"></a>Ayrıca Bkz.

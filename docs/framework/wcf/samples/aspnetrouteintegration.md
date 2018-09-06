---
title: AspNetRouteIntegration
ms.date: 03/30/2017
ms.assetid: 0638ce0e-d053-47df-a447-688e447a03fb
ms.openlocfilehash: 8d9a0710e5106cbc3d02a06e81f4f8ed9ae3e03b
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43788817"
---
# <a name="aspnetrouteintegration"></a>AspNetRouteIntegration
Bu örnek, ASP.NET yollar kullanarak bir Windows Communication Foundation (WCF) REST hizmeti barındırmak nasıl gösterir. [Temel kaynak hizmeti](../../../../docs/framework/wcf/samples/basic-resource-service.md) örnek bu senaryo, şirket içinde barındırılan bir sürümü göstermektedir ve hizmet uygulaması derinlemesine açıklanır. Bu konu ASP.NET tümleştirme özelliğini odaklanır. ASP.NET yönlendirme hakkında daha fazla bilgi için bkz: <xref:System.Web.Routing>.  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 WCF hizmeti, müşteriler topluluğu kaynak odaklı/BEKLEYEN bir biçimde sunar. Yalnızca bir SOAP tabanlı WCF hizmeti gibi hizmet .svc dosyasını kullanarak ASP.NET barındırılabilir. Hizmet URL'sini .svc olması gerektiğinden ancak HTTP senaryoları için tercih edilen budur değildir. Ayrıca, hizmet kitaplığı ile birlikte bir .svc dosyasını dağıtma gerektirir. Bu sınırlamalar, bu örnekte gösterildiği gibi ASP.NET yollar kullanarak hizmeti barındırarak önlenebilir.  
  
 Örnek ASP.NET hizmetinde ekleyerek barındıran bir <xref:System.ServiceModel.Activation.ServiceRoute> Global.asax dosyasındaki. <xref:System.ServiceModel.Activation.ServiceRoute> ('Hizmet' Bu durumda), hizmet türünü belirten hizmeti için kullanacağınız hizmet ana bilgisayar üreteci türünü (<xref:System.ServiceModel.Activation.WebServiceHostFactory> bu durumda) ve temel adresi hizmeti için HTTP ('~ / müşterilerin bu durumda).  
  
 Buna ek olarak, örnek ekleyen bir Web.config içerir <xref:System.Web.Routing.UrlRoutingModule> (ASP.NET yollara açmak için) ve hizmet yapılandırmasını içerir. Özellikle, WCF hizmeti yapılandırma ile bir varsayılan yapılandırır <xref:System.ServiceModel.Description.WebHttpEndpoint> olan <xref:System.ServiceModel.Description.WebHttpEndpoint.HelpEnabled%2A> ayarını `true`. Sonuç olarak, WCF altyapısı bir otomatik dayalı HTML Yardım sayfası oluşturur `http://localhost/Customers/help` sağlayan HTTP oluşturmak hakkında bilgi ilişkin bir örnek hizmeti ve hizmetin HTTP yanıtı – örneği için erişimi nasıl ister müşteri Ayrıntılar, XML ve JSON temsil edilir.  
  
 Müşteri koleksiyonunun gösterme (ve daha genel olarak, herhangi bir kaynak) bu şekilde URI ve HTTP kullanmanın tek bir yolla bir hizmetle etkileşim kurmak bir istemci izin veren `GET`, `PUT`, `DELETE` ve `POST`.  
  
 İstemci projesindeki program.cs gösterir böyle bir istemci nasıl olabileceğini kullanılarak yazılan <xref:System.Net.HttpWebRequest>. Bir WCF Hizmeti erişmek için yalnızca bir yol olduğunu unutmayın. WCF kanal fabrikası gibi diğer .NET Framework sınıflarını kullanarak hizmete erişmek mümkündür ve <xref:System.Net.WebClient>. SDK diğer örnekleri (gibi [temel HTTP hizmeti](../../../../docs/framework/wcf/samples/basic-http-service.md) örnek ve [Otomatik Biçim Seçimi](../../../../docs/framework/wcf/samples/automatic-format-selection.md) örnek) bir WCF Hizmeti ile iletişim kurmak için bu sınıflar kullanma işlemi gösterilmektedir.  
  
 Bu örnek 3 projelerini oluşur:  
  
 Hizmet  
 ASP.NET'te barındırılan bir WCF HTTP hizmeti içeren bir Web uygulama projesi.  
  
 İstemci  
 Hizmet çağrıları yapan bir konsol uygulama projesi.  
  
 Ortak  
 İçeren bir paylaşılan kitaplık `Customer` istemci ve hizmet tarafından kullanılan tür. İstemci konsol uygulaması çalışırken istemci hizmete isteği yapan ve konsol penceresine yanıtlardan bilgileri yazar.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  ASP.NET yollar tümleştirme örnekte çözümü açın [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
3.  Zaten açık değilse, "CTRL + W, S" tuşuna basın. açmak için **Çözüm Gezgini** penceresi.  
  
4.  Gelen **Çözüm Gezgini** sağ tıklatın, windows **hizmet** üzerine imleci getirin ve proje **hata ayıklama** bağlam menüsü seçeneği böylece **Başlat Yeni örnek** bağlam menüsü görüntülenir ve seçin **yeni örnek Başlat**.  Bu, hizmeti barındıran ASP.NET geliştirme sunucusu başlatır.  
  
5.  Gelen **Çözüm Gezgini** sağ tıklatın, windows **istemci** üzerine imleci getirin ve proje **hata ayıklama** bağlam menüsü seçeneği böylece **yeni Başlat Örnek** bağlam menüsü görüntülenir ve seçin **yeni örnek Başlat**.  
  
6.  İstemci konsol penceresi görünür ve çalışan hizmetin URI sağlar ve URI HTML Yardım sayfası çalışan hizmeti. Herhangi bir noktada HTML Yardım sayfası URI Yardım sayfasının bir tarayıcıda yazarak görüntüleyebilirsiniz. Örnek çalışırken, istemcinin geçerli etkinlik durumunu yazar.  
  
7.  İstemci Konsolu uygulamayı sonlandırmak için herhangi bir tuşa basın.  
  
8.  Hizmet hata ayıklamayı durdurmak için Shift + F5 tuşlarına basın ve Windows bildirim alanında ASP.NET Geliştirme Sunucusu simgesine sağ tıklayıp **Durdur** bağlam menüsünden.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AspNetRouteIntegration`  
  
## <a name="see-also"></a>Ayrıca Bkz.

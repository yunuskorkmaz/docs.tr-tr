---
title: Keşif Proxy Örneği
ms.date: 03/30/2017
ms.assetid: 1dfa02df-15b1-4e97-9c8e-f5f2772711b0
ms.openlocfilehash: 6fc0680bc6b61a6fe1b4b141c8b1e5081df5a124
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43393027"
---
# <a name="discovery-proxy-sample"></a>Keşif Proxy Örneği
Bu örnek, mevcut hizmetler hakkında bilgi depolamak için bir keşif proxy'si uygulaması oluşturma ve istemciler bilgi Ara sunucunun nasıl sorgulayabilir gösterir. Bu örnek, üç projelerin oluşur:  
  
-   **Hizmet**: kendi keşif proxy'sine basit bir Windows Communication Foundation (WCF) hesaplayıcı hizmeti.  
  
-   **Keşif proxy'si**: keşif proxy'si hizmeti uygulaması.  
  
-   **İstemci**: keşif proxy'sini aranacak Hizmetleri çağıran bir WCF istemci uygulaması.  
  
## <a name="demonstrates"></a>Gösteriler  
 Keşif proxy'si uygulama  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryProxy`  
  
## <a name="discoveryproxy"></a>DiscoveryProxy  
 İçinde `Main` yöntemi Program.cs dosyasının örnek gösterir türünde bir hizmetin nasıl <xref:System.ServiceModel.Discovery.DiscoveryProxy> barındırılır. Türünde iki uç kullanıma sunduğu <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> ve başka türdeki <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>. Uç noktalar her ikisi de TCP Aktarım olarak kullanın. <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> Tarafından belirtilen URI'de dinleme `probeEndpointAddress` parametresi, istemciler, proxy için verileri sorgulamak için araştırma iletileri burada gönderebilir budur. <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> Tarafından belirtilen URI'de dinleme `announcementEndpointAddress` parametresi. Burada proxy için Duyurular dinleyen budur. Çevrimiçi bir duyuru alındığında proxy hizmeti, önbelleğe ekler. ve çevrimdışı duyuru alındığında hizmet önbelleğinden kaldırır.  
  
 Uygulamasını DiscoveryProxy.cs içerir <xref:System.ServiceModel.Discovery.DiscoveryProxy>. Proxy devralmalıdır <xref:System.Object> uygulaması gerektirir ve sınıf <xref:System.Runtime.Remoting.Messaging.AsyncResult>. Oluşturma sırasında yeni bir Proxy oluşturur <xref:System.Collections.Generic.Dictionary%602>, bilir hakkında öğelerini depolamak için kullandığı.  
  
 Dosya Proxy önbellek yöntemleri ve keşif proxy'si uygulama olmak üzere iki bölgeleri ayrılmıştır. Proxy önbellek yöntemleri bölge güncelleştirmek için kullanılan yöntemleri içeren <xref:System.Collections.Generic.Dictionary%602>, sorguları gerçekleştirmek <xref:System.Collections.Generic.Dictionary%602>ve kullanıcı verilerini yazdırın. Keşif proxy'si uygulama bölge duyuru ve araştırma işlevleri için gereken geçersiz kılınan yöntemler içerir. Bunlar, çevrimiçi bir duyuru, çevrimdışı duyuru veya araştırma iletisini aldıktan sonra bir ara sunucu tarafından gerçekleştirilecek eylemleri tanımlayın.  
  
## <a name="service"></a>Hizmet  
 Hizmeti projesindeki Program.cs dosyasında aynı URI keşif proxy'si, duyuru uç noktası için kullanılır. Proxy almak için kullandığı sırada duyuruları göndermek için hizmet uç noktası kullanıyor olmasıdır. Hizmeti kullandığı <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> ve bir duyuru uç nokta ekler.  
  
## <a name="client"></a>İstemci  
 İstemci projesi aynı URI, araştırma uç noktası için Proxy olarak kullanır. Bu senaryoda araştırmaları ayrıca Proxy'yi kullanılabilir uç nokta için özel olarak tek noktaya yayın gönderildiğini olmasıdır. İstemci bu iyi bilinen adresine bağlanır ve ardından hizmet için sorgular. Bir kez ona bağlanan hizmet buldu.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Proje çözümde yük [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] ve projeyi derleyin.  
  
2.  [Çözüm temel dizini] \DiscoveryProxy\bin\debug içinde oluşturulan keşif proxy'si uygulama çalıştırın. TCP duyuru uç noktaları, duyuruları göndermek için hizmet kayıtlı olması gerektiğinden keşif proxy'sini ilk kez çalıştırmanız gerekir.  
  
3.  İkinci olarak, [çözüm temel dizini] \Service\bin\debug içinde oluşturulan hizmet uygulaması çalıştırın. Başlatma, hizmetin bir duyuru keşif proxy'si Duyurunun bitiş noktasına gönderir ve proxy Önbelleği'nde kayıtlı.  
  
4.  Ardından, [çözüm temel dizini] \Client\bin\debug içinde oluşturulan istemci uygulamasını çalıştırın. İstemci proxy sorgular hizmeti adresi alır ve ardından hizmete bağlanır.  
  
5.  Son olarak, istemci, hizmet ve ardından proxy sonlandırın. Proxy hizmet çevrimdışı duyuru almak için çalıştırmalıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.

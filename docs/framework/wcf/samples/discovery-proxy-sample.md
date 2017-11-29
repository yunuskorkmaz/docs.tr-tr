---
title: "Keşif Proxy Örneği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1dfa02df-15b1-4e97-9c8e-f5f2772711b0
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f16cf2ffc9e03308ce3b8a5e967c29e624ffd1af
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="discovery-proxy-sample"></a>Keşif Proxy Örneği
Bu örnek, mevcut hizmetler hakkında bilgi depolamak için bir keşif proxy'si uygulaması oluşturma ve istemciler için bilgi proxy nasıl sorgulayabilir gösterir. Bu örnek üç projelerin oluşur:  
  
-   **Hizmet**: basit bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] kendisini keşif proxy'sine kayıtlı hesaplayıcı hizmet.  
  
-   **Keşif proxy'si**: keşif proxy hizmeti uygulamasıdır.  
  
-   **İstemci**: aramak için keşif proxy'si için Hizmetleri çağıran bir WCF İstemcisi uygulaması.  
  
## <a name="demonstrates"></a>Gösteriler  
 Keşif proxy'si uygulama  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryProxy`  
  
## <a name="discoveryproxy"></a>DiscoveryProxy  
 İçinde `Main` yöntemi Program.cs dosyasının örnek göstermektedir türünde bir hizmetin nasıl <xref:System.ServiceModel.Discovery.DiscoveryProxy> barındırılır. Türünde iki uç sunan <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> ve başka tür <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>. Uç noktaları her ikisi de TCP bir taşıma olarak kullanın. <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> Tarafından belirtilen URI'sine dinleme `probeEndpointAddress` parametresi, istemciler kendi veri proxy sorgulamak için araştırma iletileri burada gönderebilir budur. <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> Tarafından belirtilen URI'sine dinleme `announcementEndpointAddress` parametresi. Burada proxy duyurularını dinler budur. Çevrimiçi duyuru alındığında proxy hizmeti, önbelleğe ekler. ve çevrimdışı duyuru alındığında, önbelleğe alınan hizmet kaldırır.  
  
 Uygulamasını DiscoveryProxy.cs içerir <xref:System.ServiceModel.Discovery.DiscoveryProxy>. Proxy öğesinden devralmalıdır <xref:System.Object> sınıfı ve uygulaması gerektirir <xref:System.Runtime.Remoting.Messaging.AsyncResult>. Örnek oluşturma sırasında yeni bir Proxy oluşturur <xref:System.Collections.Generic.Dictionary%602>, hangi bilir hakkında öğeleri depolamak için kullanır.  
  
 Dosya Proxy önbellek yöntemleri ve bulma Proxy uygulaması olmak üzere iki bölgede ayrılmıştır. Proxy önbellek yöntemleri bölge güncelleştirmek için kullanılan yöntemleri içeren <xref:System.Collections.Generic.Dictionary%602>, sorguları gerçekleştirmek <xref:System.Collections.Generic.Dictionary%602>ve kullanıcı verilerini yazdırın. Keşif Proxy uygulaması bölge Duyurusu ve araştırma işlevleri için gereken geçersiz kılınan yöntemler içerir. Bunlar, çevrimiçi duyuru, çevrimdışı duyuru veya bir yoklama iletisi aldıktan sonra bir proxy tarafından gerçekleştirilen eylemleri tanımlayın.  
  
## <a name="service"></a>Hizmet  
 Hizmeti projesindeki Program.cs dosyasında aynı URI kendi duyuru uç noktası için keşif proxy'si olarak kullanılır. Hizmeti uç noktası proxy almak için kullandığı sırada duyuruları göndermek için kullandığı budur. Hizmet kullandığı <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> ve bir duyuru uç nokta ekler.  
  
## <a name="client"></a>İstemci  
 İstemci projesi aynı URI, araştırma uç noktası için Proxy olarak kullanır. Bu senaryoda araştırmalar da proxy'de kullanılabilir uç nokta için özel olarak tek noktaya yayın yükleniyor olmasıdır. İstemci bu iyi bilinen adresine bağlanır ve hizmet için sorgular. Ona bağlanan hizmet bulduktan sonra.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Proje çözümde yük [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] ve projeyi oluşturun.  
  
2.  İlk [çözüm temel dizin] \DiscoveryProxy\bin\debug oluşturulan keşif proxy'si uygulamayı çalıştırın. TCP duyuru uç noktaları, duyuruları göndermek için hizmet kaydınızı olması gerektiğinden keşif proxy'si önce çalıştırmanız gerekir.  
  
3.  İkinci olarak, [çözüm temel dizin] \Service\bin\debug oluşturulan hizmet uygulaması çalıştırın. Başlatma, hizmet duyuru keşif proxy'si duyuru uç noktasına gönderir ve proxy'nin Önbelleği'nde kayıtlı.  
  
4.  Ardından, [çözüm temel dizin] \Client\bin\debug oluşturulan istemci uygulaması çalıştırın. İstemci proxy sorgular, hizmeti adresi alır ve ardından hizmetine bağlanır.  
  
5.  Son olarak, istemci, hizmet ve ardından proxy sonlanır. Proxy için hizmetin çevrimdışı duyuru almaya çalıştırıyor olmalıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.

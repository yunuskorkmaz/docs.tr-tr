---
title: "Nasıl yapılır: Keşif Proxy'sini Test Etme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d96e3fa2-3c42-4e5d-8244-2694081bdc32
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e6494a96f5e7e3a420c8443eff767b0e86d3bc25
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-test-the-discovery-proxy"></a>Nasıl yapılır: Keşif Proxy'sini Test Etme
Keşif proxy'si uygulama gösteren dördüncü dört konuların budur. Önceki konusunda [nasıl yapılır: hizmet bulmak için keşif proxy'si kullanan bir istemci uygulaması yürütürsünüz](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md), uygulanan bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet bulmak için keşif proxy'si kullanan ve daha sonra çağırır istemci uygulaması hizmet. Bu konu, Keşif proxy'si, hizmet ve istemci uygulaması iş beklendiği gibi doğrulayın açıklar.  
  
### <a name="run-the-discovery-proxy"></a>Keşif proxy'si çalıştırın  
  
1.  Komut istemini yönetici olarak açın.  
  
2.  Bildiren bir iletişim kutusu görebilirsiniz: Windows Güvenlik Duvarı, bu programın bazı özellikler engelledi. Bu iletiyi görürseniz, tıklatın **Engellemeyi Kaldır** düğmesi.  
  
3.  Komut istemi içinde keşif proxy'si, DiscoveryProxy.exe çalıştırın.  
  
4.  Uygulama aşağıdaki metni görüntülenmelidir: `Proxy started. Hit Enter to exit`.  
  
### <a name="run-the-discoverable-service"></a>Bulunabilir hizmet çalıştırın  
  
1.  Komut istemini yönetici olarak açın.  
  
2.  Komut istemi içinde Service.exe bulunabilir hizmet çalıştırın.  
  
3.  Aşağıdaki metni DiscoveryProxy.exe görüntülenmelidir: `******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******` .  
  
### <a name="run-the-client-application"></a>İstemci uygulaması çalıştırın  
  
1.  Bir komut istemi açın.  
  
2.  Komut istemi içinde client.exe uygulamayı çalıştırın.  
  
3.  Birkaç saniye sonra istemci uygulaması aşağıdaki metni görüntüler: [hizmet uç noktası] bağlanma.  
  
4.  Service.exe sonra aşağıdaki metni görüntülenmelidir: isteği alındı selamlama, ı yanıt verir.  
  
5.  Client.exe sonra aşağıdaki metni görüntülenmelidir: Hello istemci!  
  
### <a name="shut-down-the-applications"></a>Uygulamaları kapatın  
  
1.  İstemci uygulamasını kapatın.  
  
2.  Hizmetini kapatın. Aşağıdaki metin keşif proxy'si görüntüler: `******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******`.  
  
3.  Keşif proxy'si kapatın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Bulmaya Genel Bakış](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
 [Nasıl yapılır: Keşif Proxy'si Uygulama](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)  
 [Nasıl yapılır: Keşif Proxy'sine Kayıtlı Bir Bulunabilir Hizmet Ekleme](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)  
 [Nasıl yapılır: Hizmet Bulmak için Keşif Proxy'si Kullanan Bir İstemci Uygulaması Kullanma](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)

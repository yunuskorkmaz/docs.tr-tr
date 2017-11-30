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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f9c721a0ef357feeb4df540cb5b7b74d067dc807
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [WCF keşif genel bakış](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
 [Nasıl yapılır: keşif proxy'si uygulama](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)  
 [Nasıl yapılır: keşif proxy'sine kayıtlı bir bulunabilir hizmet ekleme](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)  
 [Nasıl yapılır: hizmet bulmak için keşif proxy'si kullanan bir istemci uygulaması kullanma](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)

---
title: "Nasıl yapılır: Keşif proxy'sini test etme"
ms.date: 03/30/2017
ms.assetid: d96e3fa2-3c42-4e5d-8244-2694081bdc32
ms.openlocfilehash: 3c159481813266386706b34d172bbf9614a8253d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54590519"
---
# <a name="how-to-test-the-discovery-proxy"></a>Nasıl yapılır: Keşif proxy'sini test etme
Keşif proxy'si uygulama gösteren dördüncü dört konuları budur. Önceki konu [nasıl yapılır: Bir hizmet bulmak için keşif proxy'sini kullanan bir istemci uygulaması yürütürsünüz](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md), Keşif proxy'si hizmet bulmak için kullanır ve ardından hizmeti çağıran bir WCF istemci uygulaması uygulanır. Bu konu, beklendiği gibi keşif proxy'si, hizmet ve istemci uygulama iş doğrulamak açıklar.  
  
### <a name="run-the-discovery-proxy"></a>Keşif proxy'si çalıştırın  
  
1.  Yönetici olarak bir komut istemi açın.  
  
2.  Bildiren bir iletişim kutusu görebilirsiniz: Windows Güvenlik Duvarı, bazı özellikler bu programın engelledi. Bu iletiyi görüyorsanız tıklayın **Engellemeyi Kaldır** düğmesi.  
  
3.  İçinde komut isteminde, Keşif proxy'si DiscoveryProxy.exe çalıştırın.  
  
4.  Uygulama aşağıdaki metni görüntülenmelidir: `Proxy started. Hit Enter to exit`.  
  
### <a name="run-the-discoverable-service"></a>Bulunabilir hizmet çalıştırma  
  
1.  Yönetici olarak bir komut istemi açın.  
  
2.  İçinde komut isteminde, Service.exe bulunabilir hizmet çalıştırın.  
  
3.  Aşağıdaki metni DiscoveryProxy.exe görüntülenmelidir: `******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******` .  
  
### <a name="run-the-client-application"></a>İstemci uygulamasını çalıştırın  
  
1.  Bir komut istemi açın.  
  
2.  Komut istemi içinde client.exe uygulamayı çalıştırın.  
  
3.  Birkaç saniye sonra istemci uygulama, aşağıdaki metni görüntüler: [Hizmet uç noktası için] bağlanılıyor.  
  
4.  Service.exe, ardından aşağıdaki metni görüntülenmelidir: Alınan istek Karşılama, ı yanıt verir.  
  
5.  Client.exe sonra aşağıdaki metni görüntülenir: İstemci Merhaba!  
  
### <a name="shut-down-the-applications"></a>Uygulamaları kapatın  
  
1.  İstemci uygulamayı kapatın.  
  
2.  Hizmeti kapat. Keşif proxy'si aşağıdaki metni görüntüler: `******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******`.  
  
3.  Keşif proxy'si kapatın.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [WCF Bulmaya Genel Bakış](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)
- [Nasıl yapılır: Keşif proxy'si uygulama](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)
- [Nasıl yapılır: Keşif proxy'sine bir bulunabilir hizmet ekleme](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)
- [Nasıl yapılır: Bir hizmet bulmak için keşif proxy'sini kullanan bir istemci uygulama](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)

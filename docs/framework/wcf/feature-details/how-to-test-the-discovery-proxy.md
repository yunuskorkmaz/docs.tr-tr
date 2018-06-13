---
title: "Nasıl yapılır: Keşif Proxy'sini Test Etme"
ms.date: 03/30/2017
ms.assetid: d96e3fa2-3c42-4e5d-8244-2694081bdc32
ms.openlocfilehash: 35edbd03e912ae2d9c491afb28dee1c4a3055d14
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33491228"
---
# <a name="how-to-test-the-discovery-proxy"></a>Nasıl yapılır: Keşif Proxy'sini Test Etme
Keşif proxy'si uygulama gösteren dördüncü dört konuların budur. Önceki konusunda [nasıl yapılır: hizmet bulmak için keşif proxy'si kullanan bir istemci uygulaması kullanma](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md), hizmet bulmak için keşif proxy'si kullanan ve hizmet çağıran bir WCF istemci uygulaması uygulanmadı. Bu konu, Keşif proxy'si, hizmet ve istemci uygulaması iş beklendiği gibi doğrulayın açıklar.  
  
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

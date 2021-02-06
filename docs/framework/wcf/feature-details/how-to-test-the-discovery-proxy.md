---
description: "Hakkında daha fazla bilgi edinin: nasıl yapılır: keşif proxy 'sini test etme"
title: "Nasıl yapılır: Keşif Proxy'sini Test Etme"
ms.date: 03/30/2017
ms.assetid: d96e3fa2-3c42-4e5d-8244-2694081bdc32
ms.openlocfilehash: 32360fd1f3724f2a557182ce2e11d346ba5c959d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99643117"
---
# <a name="how-to-test-the-discovery-proxy"></a>Nasıl yapılır: Keşif Proxy'sini Test Etme

Bu, bulma proxy 'sinin nasıl uygulanacağını gösteren dört konulardan oluşan dördüncü bir değer. Önceki konu başlığında [nasıl yapılır: bir hizmeti bulmak Için keşif proxy 'Si kullanan bir Istemci uygulaması](client-app-discovery-proxy-to-find-a-service.md)uygulama bir hizmet bulmak için keşif proxy 'si kullanan bir WCF istemci uygulaması uyguladıysanız ve ardından hizmeti çağırır. Bu konu, bulma proxy 'sinin, hizmetin ve istemci uygulamanın beklendiği gibi çalıştığını nasıl doğrulayabileceğinizi açıklar.  
  
### <a name="run-the-discovery-proxy"></a>Keşif proxy 'sini çalıştırma  
  
1. Yönetici olarak bir komut istemi açın.  
  
2. Şöyle bir iletişim kutusu görebilirsiniz: Windows Güvenlik Duvarı 'nın bu programın bazı özelliklerini engellediği. Bu iletiyi görürseniz, **Engellemeyi kaldır** düğmesine tıklayın.  
  
3. Komut istemi içinde, DiscoveryProxy.exe bulma proxy 'sini çalıştırın.  
  
4. Uygulama şu metni görüntülemelidir: `Proxy started. Hit Enter to exit` .  
  
### <a name="run-the-discoverable-service"></a>Keşfedilebilir hizmeti çalıştırın  
  
1. Yönetici olarak bir komut istemi açın.  
  
2. Komut istemi içinde Service.exe bulunabilir hizmeti çalıştırın.  
  
3. DiscoveryProxy.exe şu metni görüntülemelidir: `******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******` .  
  
### <a name="run-the-client-application"></a>Istemci uygulamasını çalıştırma  
  
1. Bir komut istemi açın.  
  
2. Komut istemi içinde client.exe uygulamasını çalıştırın.  
  
3. Birkaç saniye sonra istemci uygulaması şu metni görüntüler: [hizmet uç noktası] bağlantısı.  
  
4. service.exe aşağıdaki metni görüntülemelidir: karşılama isteği alındı, yanıt vereceğim.  
  
5. client.exe aşağıdaki metni görüntülemelidir: Merhaba Istemci!  
  
### <a name="shut-down-the-applications"></a>Uygulamaları kapatma  
  
1. İstemci uygulamasını kapatın.  
  
2. Hizmeti kapatın. Bulma proxy 'si şu metni görüntüler: `******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******` .  
  
3. Keşif proxy 'sini kapatın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Keşif Genel Bakış](wcf-discovery-overview.md)
- [Nasıl yapılır: Keşif Proxy'si Uygulama](how-to-implement-a-discovery-proxy.md)
- [Nasıl yapılır: Keşif Proxy'sine Kayıtlı Bir Bulunabilir Hizmet Ekleme](discoverable-service-that-registers-with-the-discovery-proxy.md)
- [Nasıl yapılır: Hizmet Bulmak için Keşif Proxy'si Kullanan Bir İstemci Uygulaması Kullanma](client-app-discovery-proxy-to-find-a-service.md)

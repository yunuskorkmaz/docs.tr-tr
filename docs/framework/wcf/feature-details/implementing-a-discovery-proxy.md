---
title: Keşif Proxy'si Ekleme
ms.date: 03/30/2017
ms.assetid: dda20e79-8df3-438e-a281-69d779d978ec
ms.openlocfilehash: 5d9296d8ba70d4c9e8d8339fa3a032d9c4c62826
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59141012"
---
# <a name="implementing-a-discovery-proxy"></a>Keşif Proxy'si Ekleme
Bu bölümde, Keşif proxy'si uygulama için gereken adımlar açıklanmaktadır. Keşif proxy'si bir depo hizmetleri içeren tek başına bir hizmettir. İstemciler, proxy farkındadır bulunabilirlik Hizmetleri bulmak için keşif proxy'si sorgulayabilir. Bir ara sunucu hizmetleri ile nasıl doldurulur kadar uygulayan olur. Örneğin, Keşif proxy'si mevcut bir hizmet depoya bağlanmak ve bu bilgileri bulunabilir, yönetici yönetim API'si için bir proxy bulunabilir hizmet eklemek için kullanabilirsiniz veya keşif proxy'si duyuru işlevini kullanabilirsiniz yapın İç önbelleğini güncelleştirin.  
  
 WCF uygulaması, bir proxy kolayca oluşturmanıza olanak tanıyan temel sınıfları sağlar. Keşif proxy'si mevcut deponuzda üzerine oluşturmak için bu API'leri kullanabilir.  
  
 Ayrıca keşif proxy'si bulunabilir olmasını sağlayın ve kendi uç bulun istemciniz burada uygulanan keşif proxy'si diğer WCF hizmetleri gibi olmamasıdır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: Keşif proxy'si uygulama](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)  
 Keşif proxy'si uygulama açıklar.  
  
 [Nasıl yapılır: Keşif proxy'sine bir bulunabilir hizmet ekleme](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)  
 Keşif proxy'sine kayıtlı bir bulunabilir WCF hizmet uygulanacağını açıklar.  
  
 [Nasıl yapılır: Bir hizmet bulmak için keşif proxy'sini kullanan bir istemci uygulama](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)  
 Bir hizmet için aranacak keşif proxy'sini kullanan bir WCF istemci uygulamanın nasıl uygulanacağını açıklar.  
  
 [Nasıl yapılır: Keşif proxy'sini test etme](../../../../docs/framework/wcf/feature-details/how-to-test-the-discovery-proxy.md)  
 Önceki üç konularındaki yazılmış kodu test açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Bulma](../../../../docs/framework/wcf/feature-details/wcf-discovery.md)
- [Nasıl yapılır: Bir WCF hizmeti ve istemci programlı bir şekilde Keşfedilebilirlik ekleme](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)

---
title: Keşif Proxy'si Ekleme
ms.date: 03/30/2017
ms.assetid: dda20e79-8df3-438e-a281-69d779d978ec
ms.openlocfilehash: 0c7086e0eecea6cc2d7494d6afda0abf056ba758
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33492225"
---
# <a name="implementing-a-discovery-proxy"></a>Keşif Proxy'si Ekleme
Bu bölüm, Keşif proxy'si uygulamak için gereken adımları açıklar. Keşif proxy'si bir depo hizmetleri içeren bir tek başına hizmetidir. İstemciler, proxy farkındadır bulunabilirlik Hizmetleri bulmak için keşif proxy'si sorgulayabilir. Bir proxy sunucu hizmetleri ile nasıl doldurulur kadar uygulayan olur. Örneğin, Keşif proxy'si var olan bir hizmet deposuna bağlanmak ve bu bilgileri bulunabilir, yönetici bir proxy bulunabilir hizmet eklemek için yönetim API'si kullanabilir ya da keşif proxy'si duyuru işlevselliği kullanabilirsiniz yapın İç önbelleğini güncelleştirin.  
  
 WCF uygulaması, bir proxy kolayca oluşturmanıza olanak tanıyan temel sınıfları sağlar. Varolan deponuz üstünde keşif proxy'si oluşturmak için bu API'leri kullanabilir.  
  
 Ayrıca keşif proxy'si bulunabilir yapmak ve bitiş noktaları bulun istemcilerinin burada uygulandığı keşif proxy'si diğer WCF hizmetleri gibi olmamasıdır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: Keşif Proxy'si Uygulama](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)  
 Keşif proxy'si uygulama açıklar.  
  
 [Nasıl yapılır: Keşif Proxy'sine Kayıtlı Bir Bulunabilir Hizmet Ekleme](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)  
 Keşif proxy'sine kayıtlı bir bulunabilir WCF hizmet uygulamak açıklar.  
  
 [Nasıl yapılır: Hizmet Bulmak için Keşif Proxy'si Kullanan Bir İstemci Uygulaması Kullanma](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)  
 Bir hizmet için aramak için keşif proxy'si kullanan bir WCF istemci uygulamasını gerçekleştirme açıklar.  
  
 [Nasıl yapılır: Keşif Proxy'sini Test Etme](../../../../docs/framework/wcf/feature-details/how-to-test-the-discovery-proxy.md)  
 Önceki üç konularındaki yazılmış kodun test edileceğini açıklar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Bulma](../../../../docs/framework/wcf/feature-details/wcf-discovery.md)  
 [Nasıl yapılır: Bir WCF Hizmeti ve İstemcisine Programlı Bir Şekilde Keşfedilebilirlik Ekleme](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)

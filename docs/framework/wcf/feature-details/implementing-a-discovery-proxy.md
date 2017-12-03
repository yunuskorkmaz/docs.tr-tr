---
title: "Keşif Proxy'si Ekleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dda20e79-8df3-438e-a281-69d779d978ec
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 98affacf611ad31c7c3f8a93ff5793279a42a128
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="implementing-a-discovery-proxy"></a>Keşif Proxy'si Ekleme
Bu bölüm, Keşif proxy'si uygulamak için gereken adımları açıklar. Keşif proxy'si bir depo hizmetleri içeren bir tek başına hizmetidir. İstemciler, proxy farkındadır bulunabilirlik Hizmetleri bulmak için keşif proxy'si sorgulayabilir. Bir proxy sunucu hizmetleri ile nasıl doldurulur kadar uygulayan olur. Örneğin, Keşif proxy'si var olan bir hizmet deposuna bağlanmak ve bu bilgileri bulunabilir, yönetici bir proxy bulunabilir hizmet eklemek için yönetim API'si kullanabilir ya da keşif proxy'si duyuru işlevselliği kullanabilirsiniz yapın İç önbelleğini güncelleştirin.  
  
 WCF uygulaması, bir proxy kolayca oluşturmanıza olanak tanıyan temel sınıfları sağlar. Varolan deponuz üstünde keşif proxy'si oluşturmak için bu API'leri kullanabilir.  
  
 Ayrıca keşif proxy'si bulunabilir yapmak ve bitiş noktaları bulun istemcilerinin burada uygulandığı keşif proxy'si diğer WCF hizmetleri gibi olmamasıdır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: keşif proxy'si uygulama](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)  
 Keşif proxy'si uygulama açıklar.  
  
 [Nasıl yapılır: keşif proxy'sine kayıtlı bir bulunabilir hizmet ekleme](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)  
 Bir bulunabilirlik uygulamak açıklar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] keşif proxy'sine kayıtlı hizmet.  
  
 [Nasıl yapılır: hizmet bulmak için keşif proxy'si kullanan bir istemci uygulaması kullanma](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)  
 Nasıl uygulandığı açıklanır bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aramak için bir hizmet için keşif proxy'si kullanan istemci uygulaması.  
  
 [Nasıl yapılır: keşif proxy'sini test etme](../../../../docs/framework/wcf/feature-details/how-to-test-the-discovery-proxy.md)  
 Önceki üç konularındaki yazılmış kodun test edileceğini açıklar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF keşfetme](../../../../docs/framework/wcf/feature-details/wcf-discovery.md)  
 [Nasıl yapılır: program aracılığıyla bir WCF hizmeti ve istemci Keşfedilebilirlik ekleme](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)

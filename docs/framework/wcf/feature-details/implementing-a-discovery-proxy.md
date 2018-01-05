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
ms.workload: dotnet
ms.openlocfilehash: 2996eb07c883947210c48471a2c60ba49495566d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-a-discovery-proxy"></a>Keşif Proxy'si Ekleme
Bu bölüm, Keşif proxy'si uygulamak için gereken adımları açıklar. Keşif proxy'si bir depo hizmetleri içeren bir tek başına hizmetidir. İstemciler, proxy farkındadır bulunabilirlik Hizmetleri bulmak için keşif proxy'si sorgulayabilir. Bir proxy sunucu hizmetleri ile nasıl doldurulur kadar uygulayan olur. Örneğin, Keşif proxy'si var olan bir hizmet deposuna bağlanmak ve bu bilgileri bulunabilir, yönetici bir proxy bulunabilir hizmet eklemek için yönetim API'si kullanabilir ya da keşif proxy'si duyuru işlevselliği kullanabilirsiniz yapın İç önbelleğini güncelleştirin.  
  
 WCF uygulaması, bir proxy kolayca oluşturmanıza olanak tanıyan temel sınıfları sağlar. Varolan deponuz üstünde keşif proxy'si oluşturmak için bu API'leri kullanabilir.  
  
 Ayrıca keşif proxy'si bulunabilir yapmak ve bitiş noktaları bulun istemcilerinin burada uygulandığı keşif proxy'si diğer WCF hizmetleri gibi olmamasıdır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: Keşif Proxy'si Uygulama](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)  
 Keşif proxy'si uygulama açıklar.  
  
 [Nasıl yapılır: Keşif Proxy'sine Kayıtlı Bir Bulunabilir Hizmet Ekleme](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)  
 Bir bulunabilirlik uygulamak açıklar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] keşif proxy'sine kayıtlı hizmet.  
  
 [Nasıl yapılır: Hizmet Bulmak için Keşif Proxy'si Kullanan Bir İstemci Uygulaması Kullanma](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)  
 Nasıl uygulandığı açıklanır bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aramak için bir hizmet için keşif proxy'si kullanan istemci uygulaması.  
  
 [Nasıl yapılır: Keşif Proxy'sini Test Etme](../../../../docs/framework/wcf/feature-details/how-to-test-the-discovery-proxy.md)  
 Önceki üç konularındaki yazılmış kodun test edileceğini açıklar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Bulma](../../../../docs/framework/wcf/feature-details/wcf-discovery.md)  
 [Nasıl yapılır: Bir WCF Hizmeti ve İstemcisine Programlı Bir Şekilde Keşfedilebilirlik Ekleme](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)

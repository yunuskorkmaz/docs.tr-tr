---
title: Bir WCF Hizmeti Bir Web Grubunda Barındırıldığında Yeniden Yürütme Saldırılarını Önleme
ms.date: 03/30/2017
ms.assetid: 1c2ed695-7a31-4257-92bd-9e9731b886a5
ms.openlocfilehash: 8b49b46e56d07dcd2f1eaf6afca964ddfe7dd740
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33492277"
---
# <a name="preventing-replay-attacks-when-a-wcf-service-is-hosted-in-a-web-farm"></a>Bir WCF Hizmeti Bir Web Grubunda Barındırıldığında Yeniden Yürütme Saldırılarını Önleme
Ne zaman ileti güvenliği WCF engel yeniden yürütme saldırılarını gelen ileti dışında NONCE oluşturma ve iç denetimi `InMemoryNonceCache` oluşturulan NONCE mevcut olup olmadığını görmek için. İse, ileti yeniden yürütme atılır. Ne zaman bir WCF Hizmeti barındırılan bir web grubunda beri `InMemoryNonceCache` paylaşılmayan web grubundaki düğümleri arasında hizmet yeniden yürütme saldırılarına karşı savunmasızdır.  Bu senaryo azaltmak için WCF 4.5 soyut sınıftan sınıf türetme tarafından paylaşılan kendi NONCE önbellek uygulamak izin veren bir genişletilebilirlik noktasıdır <xref:System.ServiceModel.Security.NonceCache>.  
  
## <a name="noncecache-implementation"></a>NonceCache uygulama  
 Kendi paylaşılan NONCE önbellek uygulamak için öğesinden bir sınıf türetin <xref:System.ServiceModel.Security.NonceCache> ve geçersiz kılma <xref:System.ServiceModel.Security.NonceCache.CheckNonce%2A> ve <xref:System.ServiceModel.Security.NonceCache.TryAddNonce%2A> yöntemleri. <xref:System.ServiceModel.Security.NonceCache.CheckNonce%2A> Belirtilen NONCE önbellekte olup olmadığını kontrol eder. <xref:System.ServiceModel.Security.NonceCache.TryAddNonce%2A> NONCE önbelleğe eklemeye çalışır. Sınıfı uygulandıktan sonra onu bir örneği başlatmasını ve kendisine atayarak takma <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.NonceCache%2A> için istemci tarafı yeniden yürütme algılaması ve <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NonceCache%2A> için sunucu tarafı yeniden yürütme algılaması. Bu özellik kutusunu yapılandırma desteği yok dışı yoktur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İleti Güvenliği](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)  
 [SymmetricSecurityBindingElement](../../../../docs/framework/wcf/diagnostics/wmi/symmetricsecuritybindingelement.md)

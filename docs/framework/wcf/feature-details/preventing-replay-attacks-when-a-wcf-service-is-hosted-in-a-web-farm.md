---
title: Bir WCF Hizmeti Bir Web Grubunda Barındırıldığında Yeniden Yürütme Saldırılarını Önleme
ms.date: 03/30/2017
ms.assetid: 1c2ed695-7a31-4257-92bd-9e9731b886a5
ms.openlocfilehash: 07743795effd3da9a241fd778756dd92d99d78f6
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596792"
---
# <a name="preventing-replay-attacks-when-a-wcf-service-is-hosted-in-a-web-farm"></a>Bir WCF Hizmeti Bir Web Grubunda Barındırıldığında Yeniden Yürütme Saldırılarını Önleme
İleti güvenliği WCF kullanırken, gelen iletiden bir kerelik anahtar oluşturarak ve `InMemoryNonceCache` oluşturulan nonce 'nin mevcut olup olmadığını görmek için iç kontrol ederek yeniden yürütme saldırıları önlenir. Eğer ise, ileti yeniden yürütme olarak atılır. Bir WCF hizmeti bir Web grubunda barındırıldığında, bu, `InMemoryNonceCache` Web grubundaki düğümler arasında paylaşılmadığından, hizmet yeniden yürütme saldırılarına karşı savunmasız kalır.  Bu senaryoyu azaltmak için WCF 4,5, soyut sınıftan bir sınıf türeterek kendi paylaşılan NONCE önbelleğinizi uygulamanıza olanak tanıyan bir genişletilebilirlik noktası sağlar <xref:System.ServiceModel.Security.NonceCache> .  
  
## <a name="noncecache-implementation"></a>Cecache olmayan uygulama  
 Kendi paylaşılan NONCE önbelleğinizi uygulamak için, ' dan bir sınıf türetirsiniz ve <xref:System.ServiceModel.Security.NonceCache> <xref:System.ServiceModel.Security.NonceCache.CheckNonce%2A> ve <xref:System.ServiceModel.Security.NonceCache.TryAddNonce%2A> yöntemlerini geçersiz kılın. <xref:System.ServiceModel.Security.NonceCache.CheckNonce%2A>Belirtilen NONCE 'ın önbellekte olup olmadığını kontrol eder. <xref:System.ServiceModel.Security.NonceCache.TryAddNonce%2A>önbelleğe bir kerelik anahtar eklemeyi dener. Sınıf uygulandıktan sonra, bir örneği örnekleyerek ve <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.NonceCache%2A> istemci tarafı yeniden yürütme algılaması ve sunucu tarafı yeniden yürütme algılaması için öğesine atayarak bu işlemi gerçekleştirebilirsiniz <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NonceCache%2A> . Bu özellik için en çok Box yapılandırma desteği yok.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İleti Güvenliği](message-security-in-wcf.md)
- [SymmetricSecurityBindingElement](../diagnostics/wmi/symmetricsecuritybindingelement.md)

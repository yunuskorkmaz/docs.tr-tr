---
title: Bir WCF Hizmeti Bir Web Grubunda Barındırıldığında Yeniden Yürütme Saldırılarını Önleme
ms.date: 03/30/2017
ms.assetid: 1c2ed695-7a31-4257-92bd-9e9731b886a5
ms.openlocfilehash: e27a85d42268df107b26d3bd24af15a639bb1836
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59072929"
---
# <a name="preventing-replay-attacks-when-a-wcf-service-is-hosted-in-a-web-farm"></a>Bir WCF Hizmeti Bir Web Grubunda Barındırıldığında Yeniden Yürütme Saldırılarını Önleme
Ne zaman WCF ileti güvenliğini engel yeniden yürütme saldırıları gelen ileti dışında bir geçici öğe oluşturma ve iç denetleyerek `InMemoryNonceCache` oluşturulan NONCE mevcut olup olmadığını görmek için. İse, ileti bir yeniden yürütme atılır. Ne zaman bir WCF Hizmeti barındırılan bir web grubunda beri `InMemoryNonceCache` paylaşılmayan web grubundaki düğümleri arasında yeniden yürütme saldırılarına karşı savunmasız hizmetidir.  Bu senaryo azaltmak için WCF 4.5 soyut sınıfından bir sınıf türetilerek, kendi paylaşılan NONCE önbellek uygulamak izin veren bir genişletilebilirlik noktası sağlar <xref:System.ServiceModel.Security.NonceCache>.  
  
## <a name="noncecache-implementation"></a>NonceCache uygulama  
 Kendi paylaşılan NONCE önbellek uygulamak için öğesinden bir sınıf türetin <xref:System.ServiceModel.Security.NonceCache> ve geçersiz kılma <xref:System.ServiceModel.Security.NonceCache.CheckNonce%2A> ve <xref:System.ServiceModel.Security.NonceCache.TryAddNonce%2A> yöntemleri. <xref:System.ServiceModel.Security.NonceCache.CheckNonce%2A> Belirtilen NONCE önbellekte olup olmadığını denetler. <xref:System.ServiceModel.Security.NonceCache.TryAddNonce%2A> önbelleğe bir geçici öğe ekleme girişiminde bulunur. Sınıf uygulandıktan sonra bu örneği örnekleme ve giderek takma <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.NonceCache%2A> için istemci tarafı yeniden yürütme algılaması ve <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NonceCache%2A> yeniden yürütme algılaması için sunucu tarafı. Bu özellik hazır yapılandırma desteği, hiçbir çıkış yok.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İleti Güvenliği](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)
- [SymmetricSecurityBindingElement](../../../../docs/framework/wcf/diagnostics/wmi/symmetricsecuritybindingelement.md)

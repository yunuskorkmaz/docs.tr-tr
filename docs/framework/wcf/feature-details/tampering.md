---
title: İzinsiz Değişiklik
ms.date: 03/30/2017
ms.assetid: 3bad93be-60bb-4f89-96ab-a1c3dc7c0fad
ms.openlocfilehash: 7a4265c30a6713f9557de2b3d1e99c87b7dd3e58
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107893"
---
# <a name="tampering"></a>İzinsiz Değişiklik
*İzinsiz* bir ileti ya da ileti teslimini değiştirme ve ne için tasarlanmıştı dışında bir amaç için değiştirilmiş bir iletiyi kullanarak, işlemidir.  
  
## <a name="do-not-disable-ws-addressing"></a>WS-Addressing devre dışı bırakmayın  
 WS-Addressing belirtimi, bir ileti alıcı, iletiyi gönderenin doğrulamak izin verme her ileti üzerinde adres üst bilgileri sağlar. Ayarlayarak bu özelliği devre dışı bırakabilirsiniz <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> özelliğini <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.  
  
 İleti güvenlik modunu ayarlandığında ve WS-Addressing devre dışı bırakılırsa, bir saldırgan, bir istemciden bir isteğin tamamlanması ve başka bir hizmete göndermek ve ikinci hizmet iletiyi özgün istemciden gelen algılama hiçbir yolu yoktur. Aslında, ikinci hizmete konuşurken bir istemci olduğunu ilk hizmeti anlatabilirsiniz.  
  
 Bunu azaltmak için hiçbir zaman ayarlamak <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> özelliğini <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>ve kullanmaktan kaçının <xref:System.ServiceModel.Channels.MessageVersion>, statik gibi <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> ayarlar özelliği <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> özelliğini <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenlik Değerlendirmeleri](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)
- [Bilgileri Açıklama](../../../../docs/framework/wcf/feature-details/information-disclosure.md)
- [Ayrıcalık Yükseltme](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)
- [Hizmet Reddi](../../../../docs/framework/wcf/feature-details/denial-of-service.md)
- [Desteklenmeyen Senaryolar](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
- [Yeniden Yürütme Saldırıları](../../../../docs/framework/wcf/feature-details/replay-attacks.md)

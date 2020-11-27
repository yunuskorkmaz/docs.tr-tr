---
title: Tampering (Kurcalama)
ms.date: 03/30/2017
ms.assetid: 3bad93be-60bb-4f89-96ab-a1c3dc7c0fad
ms.openlocfilehash: c2b0cae1dc57fac486122ca17fc8109ffe62f77d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96249806"
---
# <a name="tampering"></a>Tampering (Kurcalama)

*Izinsiz değişiklik* , bir iletiyi değiştirme veya bir iletinin teslim etme veya değiştirilmiş iletiyi amaçlanan bir amaç dışında bir amaç için kullanma işlemidir.  
  
## <a name="do-not-disable-ws-addressing"></a>WS-Addressing devre dışı bırakma  

 WS-Addressing belirtimi her ileti üzerinde adres üst bilgileri sağlar ve ileti alıcısının ileti gönderisini doğrulamasına izin verir. Özelliğini olarak ayarlayarak bu özelliği devre dışı bırakabilirsiniz <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> <xref:System.ServiceModel.Channels.AddressingVersion.None%2A> .  
  
 Güvenlik modu Ileti olarak ayarlandığında ve WS-Addressing devre dışı bırakılmışsa, bir saldırgan istemciden bir istek alabilir ve başka bir hizmete gönderebilir ve ikinci hizmet, iletinin özgün istemciden geldiğini algılamaktır. Aslında, ilk hizmet ikinci hizmetle görüşülürken istemci olduğunu önedebilir.  
  
 Bunu azaltmak için, <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> özelliğini hiçbir şekilde ayarlayın <xref:System.ServiceModel.Channels.AddressingVersion.None%2A> ve <xref:System.ServiceModel.Channels.MessageVersion> özelliğini ' a ayarlayan static özelliği gibi ' i kullanmaktan kaçının <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> <xref:System.ServiceModel.Channels.AddressingVersion.None%2A> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenlik konuları](security-considerations-in-wcf.md)
- [Bilgilerin Açığa Çıkması](information-disclosure.md)
- [Ayrıcalık Yükseltme](elevation-of-privilege.md)
- [Hizmet Reddi](denial-of-service.md)
- [Desteklenmeyen Senaryolar](unsupported-scenarios.md)
- [Yeniden Yürütme Saldırıları](replay-attacks.md)

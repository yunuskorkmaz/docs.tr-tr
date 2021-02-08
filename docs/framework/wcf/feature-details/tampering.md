---
description: 'Daha fazla bilgi edinin: değişiklik'
title: Tampering (Kurcalama)
ms.date: 03/30/2017
ms.assetid: 3bad93be-60bb-4f89-96ab-a1c3dc7c0fad
ms.openlocfilehash: 3b14fef66e5c98737d8d2f6a8b889f16c83020f9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793330"
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

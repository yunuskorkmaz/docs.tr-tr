---
title: İzinsiz Değişiklik
ms.date: 03/30/2017
ms.assetid: 3bad93be-60bb-4f89-96ab-a1c3dc7c0fad
ms.openlocfilehash: e618ab369a46d403aa8db26c4b472e2be3634785
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600717"
---
# <a name="tampering"></a>İzinsiz Değişiklik
*Izinsiz değişiklik* , bir iletiyi değiştirme veya bir iletinin teslim etme veya değiştirilmiş iletiyi amaçlanan bir amaç dışında bir amaç için kullanma işlemidir.  
  
## <a name="do-not-disable-ws-addressing"></a>WS-Addressing ' i devre dışı bırakma  
 WS-Addressing belirtimi, her ileti için adres üst bilgileri sağlar ve ileti alıcısının iletiyi göndereni doğrulamasına izin verir. Özelliğini olarak ayarlayarak bu özelliği devre dışı bırakabilirsiniz <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> <xref:System.ServiceModel.Channels.AddressingVersion.None%2A> .  
  
 Güvenlik modu Ileti olarak ayarlandığında ve WS-Addressing devre dışıysa saldırgan bir istemciden bir istek alabilir ve bu hizmeti başka bir hizmete gönderebilir ve ikinci hizmette iletinin özgün istemciden geldiğini algılamaktan bir yolu yoktur. Aslında, ilk hizmet ikinci hizmetle görüşülürken istemci olduğunu önedebilir.  
  
 Bunu azaltmak için, <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> özelliğini hiçbir şekilde ayarlayın <xref:System.ServiceModel.Channels.AddressingVersion.None%2A> ve <xref:System.ServiceModel.Channels.MessageVersion> özelliğini ' a ayarlayan static özelliği gibi ' i kullanmaktan kaçının <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> <xref:System.ServiceModel.Channels.AddressingVersion.None%2A> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenlik konuları](security-considerations-in-wcf.md)
- [Bilgileri Açıklama](information-disclosure.md)
- [Ayrıcalıkların Yükseltilmesi](elevation-of-privilege.md)
- [Hizmet Reddi](denial-of-service.md)
- [Desteklenmeyen Senaryolar](unsupported-scenarios.md)
- [Yeniden Yürütme Saldırıları](replay-attacks.md)

---
title: "İzinsiz Değişiklik"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3bad93be-60bb-4f89-96ab-a1c3dc7c0fad
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d8852c4d19c48af2beee598f4ddfae7b775a025f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="tampering"></a>İzinsiz Değişiklik
*İzinsiz* bir ileti ya da ileti teslimini değiştirmeyi ve ne için tasarlanmıştır dışında bir amaç için değiştirilmiş iletiyi kullanarak, işlemidir.  
  
## <a name="do-not-disable-ws-addressing"></a>WS-adresleme devre dışı bırakmayın  
 WS-adresleme belirtimi, iletiyi gönderenin doğrulamak bir ileti alıcısı izin vererek her ileti için adres üstbilgileri sağlar. Ayarlayarak bu özelliği devre dışı bırakabilirsiniz <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> özelliğine <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.  
  
 Güvenlik modu iletiye ayarlandığında ve WS adresleme devre dışı bırakılırsa, bir saldırgan, bir istemciden bir isteğin tamamlanması ve başka bir hizmete göndermek ve ikinci hizmet özgün istemciden gelen ileti algılama hiçbir yolu yoktur. Gerçekte, ilk hizmet, ikinci hizmete konuşurken istemci olduğunu içeriğini.  
  
 Bu durumu iyileştirmek için hiçbir zaman ayarlamak <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> özelliğine <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>ve kullanmaktan kaçının <xref:System.ServiceModel.Channels.MessageVersion>, statik gibi <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> ayarlar özelliği <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> özelliğine <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Güvenlik konuları](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [Bilgilerin açığa çıkmasına](../../../../docs/framework/wcf/feature-details/information-disclosure.md)  
 [Ayrıcalık yükseltme](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)  
 [Hizmet reddi](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 [Desteklenmeyen senaryolar](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)  
 [Yeniden yürütme saldırıları](../../../../docs/framework/wcf/feature-details/replay-attacks.md)

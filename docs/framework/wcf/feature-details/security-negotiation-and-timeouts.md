---
description: 'Daha fazla bilgi edinin: güvenlik anlaşması ve zaman aşımları'
title: Güvenlik Görüşmeleri ve Zaman Aşımları
ms.date: 03/30/2017
ms.assetid: 02a428f1-84e5-4d28-a11f-53ce31d63196
ms.openlocfilehash: 50055698f9a9946d0c0110a964cf9ce5b9f4fa28
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99632444"
---
# <a name="security-negotiation-and-timeouts"></a>Güvenlik Görüşmeleri ve Zaman Aşımları

İstemciler ve hizmetler kimlik doğrulaması yaparken, Windows Communication Foundation (WCF) kimlik doğrulamasının bir parçası olarak hizmet kimlik bilgisinin üzerinde anlaşıldığı bir modu destekler. Bu tür senaryolarda, istemci ile hizmet kimlik bilgisini istemciye yaymak için bir çok aşamalı değişim meydana gelir. <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A>Özelliği, birden çok bacak değişim işleminin ne kadar sürdüğünü denetler. Ancak, bu zaman aşımı yalnızca Exchange aslında tek bir istek yanıtı için daha fazla sürerse geçerlidir. Anlaşmanın tek bir gidiş yolculuğa göre tamamlandığı durumlarda zaman aşımı uygulanmaz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- [Nasıl yapılır: Maksimum Saat Eğriltme Ayarlama](how-to-set-a-max-clock-skew.md)

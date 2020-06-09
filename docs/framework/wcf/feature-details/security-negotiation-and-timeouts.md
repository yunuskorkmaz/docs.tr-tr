---
title: Güvenlik Görüşmeleri ve Zaman Aşımları
ms.date: 03/30/2017
ms.assetid: 02a428f1-84e5-4d28-a11f-53ce31d63196
ms.openlocfilehash: 1b5fb15b4ea00ba33b741c96bcb423aefe9890fa
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601003"
---
# <a name="security-negotiation-and-timeouts"></a>Güvenlik Görüşmeleri ve Zaman Aşımları
İstemciler ve hizmetler kimlik doğrulaması yaparken, Windows Communication Foundation (WCF) kimlik doğrulamasının bir parçası olarak hizmet kimlik bilgisinin üzerinde anlaşıldığı bir modu destekler. Bu tür senaryolarda, istemci ile hizmet kimlik bilgisini istemciye yaymak için bir çok aşamalı değişim meydana gelir. <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A>Özelliği, birden çok bacak değişim işleminin ne kadar sürdüğünü denetler. Ancak, bu zaman aşımı yalnızca Exchange aslında tek bir istek yanıtı için daha fazla sürerse geçerlidir. Anlaşmanın tek bir gidiş yolculuğa göre tamamlandığı durumlarda zaman aşımı uygulanmaz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- [Nasıl yapılır: Maksimum Saat Eğriltme Ayarlama](how-to-set-a-max-clock-skew.md)

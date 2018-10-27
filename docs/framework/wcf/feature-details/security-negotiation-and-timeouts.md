---
title: Güvenlik Görüşmeleri ve Zaman Aşımları
ms.date: 03/30/2017
ms.assetid: 02a428f1-84e5-4d28-a11f-53ce31d63196
ms.openlocfilehash: dfabdb05c7658e3cf9eb5b325597360bbc0bb588
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50037804"
---
# <a name="security-negotiation-and-timeouts"></a>Güvenlik Görüşmeleri ve Zaman Aşımları
İstemciler ve hizmetler kimlik doğrulaması sırasında Windows Communication Foundation (WCF) hizmet kimlik bilgisi kimlik doğrulaması bir parçası olarak nerede anlaşılan bir modu destekler. Böyle senaryolarda, büyük olasılıkla çok oluşturan exchange istemci ve hizmet için hizmet kimlik bilgilerini istemci yayılması arasında gerçekleşir. <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> Özellik denetler çok oluşturan exchange tamamlanması ne kadar sürebilir. Exchange gerçekten daha fazla sürer ancak, bu zaman aşımı yalnızca geçerlidir, tek bir istek-yanıt. Burada anlaşma tek bir gidiş dönüş tamamlandıktan durumlarda, zaman aşımı geçerli değildir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 [Nasıl yapılır: Maksimum Saat Eğriltme Ayarlama](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)

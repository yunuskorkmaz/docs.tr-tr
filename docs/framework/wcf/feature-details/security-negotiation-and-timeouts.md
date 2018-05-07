---
title: Güvenlik Görüşmeleri ve Zaman Aşımları
ms.date: 03/30/2017
ms.assetid: 02a428f1-84e5-4d28-a11f-53ce31d63196
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 508d648acf148f13076327bb312d0a0b08471ac1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="security-negotiation-and-timeouts"></a>Güvenlik Görüşmeleri ve Zaman Aşımları
İstemcileri ve Hizmetleri kimlik doğrulaması sırasında Windows Communication Foundation (WCF) hizmet kimlik bilgilerini kimlik doğrulaması bir parçası olarak burada anlaşılan bir modu destekler. Bu senaryolarda, potansiyel olarak çok leg exchange istemciye hizmet kimlik bilgilerini yaymak için istemci ve hizmet arasında oluşur. <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> Özelliği denetler çok leg exchange tamamlamak için ne kadar sürebilir. Exchange gerçekten daha fazla sürerse, ancak bu zaman aşımı yalnızca geçerlidir, tek bir istek-yanıt. Tek bir anlaşma'burada gidiş dönüş tamamlandıktan durumlarda, zaman aşımı geçerli değildir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 [Nasıl yapılır: Maksimum Saat Eğriltme Ayarlama](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)

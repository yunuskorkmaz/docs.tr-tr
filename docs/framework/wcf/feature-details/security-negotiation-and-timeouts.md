---
title: "Güvenlik Görüşmeleri ve Zaman Aşımları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 02a428f1-84e5-4d28-a11f-53ce31d63196
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: b4d0b2953a91040c37afe88d9499fd4be1970f31
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="security-negotiation-and-timeouts"></a>Güvenlik Görüşmeleri ve Zaman Aşımları
İstemcileri ve Hizmetleri kimlik doğrulaması sırasında [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] nerede hizmet kimlik bilgilerini anlaşılan kimlik doğrulaması bir parçası olarak bir modu destekler. Bu senaryolarda, potansiyel olarak çok leg exchange istemciye hizmet kimlik bilgilerini yaymak için istemci ve hizmet arasında oluşur. <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> Özelliği denetler çok leg exchange tamamlamak için ne kadar sürebilir. Exchange gerçekten daha fazla sürerse, ancak bu zaman aşımı yalnızca geçerlidir, tek bir istek-yanıt. Tek bir anlaşma'burada gidiş dönüş tamamlandıktan durumlarda, zaman aşımı geçerli değildir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 [Nasıl yapılır: maksimum saat eğriltme ayarlama](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)

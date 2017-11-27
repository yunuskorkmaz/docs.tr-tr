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
# <a name="security-negotiation-and-timeouts"></a><span data-ttu-id="96b32-102">Güvenlik Görüşmeleri ve Zaman Aşımları</span><span class="sxs-lookup"><span data-stu-id="96b32-102">Security Negotiation and Timeouts</span></span>
<span data-ttu-id="96b32-103">İstemcileri ve Hizmetleri kimlik doğrulaması sırasında [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] nerede hizmet kimlik bilgilerini anlaşılan kimlik doğrulaması bir parçası olarak bir modu destekler.</span><span class="sxs-lookup"><span data-stu-id="96b32-103">When clients and services authenticate, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] supports a mode where the service credential is negotiated as part of authentication.</span></span> <span data-ttu-id="96b32-104">Bu senaryolarda, potansiyel olarak çok leg exchange istemciye hizmet kimlik bilgilerini yaymak için istemci ve hizmet arasında oluşur.</span><span class="sxs-lookup"><span data-stu-id="96b32-104">In such scenarios, a potentially multi-leg exchange occurs between the client and the service to propagate the service credential to the client.</span></span> <span data-ttu-id="96b32-105"><xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> Özelliği denetler çok leg exchange tamamlamak için ne kadar sürebilir.</span><span class="sxs-lookup"><span data-stu-id="96b32-105">The <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property controls how long the multi-leg exchange can take to complete.</span></span> <span data-ttu-id="96b32-106">Exchange gerçekten daha fazla sürerse, ancak bu zaman aşımı yalnızca geçerlidir, tek bir istek-yanıt.</span><span class="sxs-lookup"><span data-stu-id="96b32-106">However, this timeout only applies if the exchange actually takes more that a single request-response.</span></span> <span data-ttu-id="96b32-107">Tek bir anlaşma'burada gidiş dönüş tamamlandıktan durumlarda, zaman aşımı geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="96b32-107">In cases where the negotiation completes in a single round trip, the timeout does not apply.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96b32-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="96b32-108">See Also</span></span>  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 [<span data-ttu-id="96b32-109">Nasıl yapılır: maksimum saat eğriltme ayarlama</span><span class="sxs-lookup"><span data-stu-id="96b32-109">How to: Set a Max Clock Skew</span></span>](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)

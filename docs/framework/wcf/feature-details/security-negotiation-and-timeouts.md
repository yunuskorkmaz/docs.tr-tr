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
# <a name="security-negotiation-and-timeouts"></a><span data-ttu-id="4a3d6-103">Güvenlik Görüşmeleri ve Zaman Aşımları</span><span class="sxs-lookup"><span data-stu-id="4a3d6-103">Security Negotiation and Timeouts</span></span>

<span data-ttu-id="4a3d6-104">İstemciler ve hizmetler kimlik doğrulaması yaparken, Windows Communication Foundation (WCF) kimlik doğrulamasının bir parçası olarak hizmet kimlik bilgisinin üzerinde anlaşıldığı bir modu destekler.</span><span class="sxs-lookup"><span data-stu-id="4a3d6-104">When clients and services authenticate, Windows Communication Foundation (WCF) supports a mode where the service credential is negotiated as part of authentication.</span></span> <span data-ttu-id="4a3d6-105">Bu tür senaryolarda, istemci ile hizmet kimlik bilgisini istemciye yaymak için bir çok aşamalı değişim meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="4a3d6-105">In such scenarios, a potentially multi-leg exchange occurs between the client and the service to propagate the service credential to the client.</span></span> <span data-ttu-id="4a3d6-106"><xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A>Özelliği, birden çok bacak değişim işleminin ne kadar sürdüğünü denetler.</span><span class="sxs-lookup"><span data-stu-id="4a3d6-106">The <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property controls how long the multi-leg exchange can take to complete.</span></span> <span data-ttu-id="4a3d6-107">Ancak, bu zaman aşımı yalnızca Exchange aslında tek bir istek yanıtı için daha fazla sürerse geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="4a3d6-107">However, this timeout only applies if the exchange actually takes more that a single request-response.</span></span> <span data-ttu-id="4a3d6-108">Anlaşmanın tek bir gidiş yolculuğa göre tamamlandığı durumlarda zaman aşımı uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="4a3d6-108">In cases where the negotiation completes in a single round trip, the timeout does not apply.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a3d6-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4a3d6-109">See also</span></span>

- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- [<span data-ttu-id="4a3d6-110">Nasıl yapılır: Maksimum Saat Eğriltme Ayarlama</span><span class="sxs-lookup"><span data-stu-id="4a3d6-110">How to: Set a Max Clock Skew</span></span>](how-to-set-a-max-clock-skew.md)

---
title: Güvenlik Görüşmeleri ve Zaman Aşımları
ms.date: 03/30/2017
ms.assetid: 02a428f1-84e5-4d28-a11f-53ce31d63196
ms.openlocfilehash: 4ccc7e5539b1a772be6f9edb5a4cb4d94a8d1c1b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275989"
---
# <a name="security-negotiation-and-timeouts"></a><span data-ttu-id="d1a87-102">Güvenlik Görüşmeleri ve Zaman Aşımları</span><span class="sxs-lookup"><span data-stu-id="d1a87-102">Security Negotiation and Timeouts</span></span>

<span data-ttu-id="d1a87-103">İstemciler ve hizmetler kimlik doğrulaması yaparken, Windows Communication Foundation (WCF) kimlik doğrulamasının bir parçası olarak hizmet kimlik bilgisinin üzerinde anlaşıldığı bir modu destekler.</span><span class="sxs-lookup"><span data-stu-id="d1a87-103">When clients and services authenticate, Windows Communication Foundation (WCF) supports a mode where the service credential is negotiated as part of authentication.</span></span> <span data-ttu-id="d1a87-104">Bu tür senaryolarda, istemci ile hizmet kimlik bilgisini istemciye yaymak için bir çok aşamalı değişim meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="d1a87-104">In such scenarios, a potentially multi-leg exchange occurs between the client and the service to propagate the service credential to the client.</span></span> <span data-ttu-id="d1a87-105"><xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A>Özelliği, birden çok bacak değişim işleminin ne kadar sürdüğünü denetler.</span><span class="sxs-lookup"><span data-stu-id="d1a87-105">The <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property controls how long the multi-leg exchange can take to complete.</span></span> <span data-ttu-id="d1a87-106">Ancak, bu zaman aşımı yalnızca Exchange aslında tek bir istek yanıtı için daha fazla sürerse geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="d1a87-106">However, this timeout only applies if the exchange actually takes more that a single request-response.</span></span> <span data-ttu-id="d1a87-107">Anlaşmanın tek bir gidiş yolculuğa göre tamamlandığı durumlarda zaman aşımı uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="d1a87-107">In cases where the negotiation completes in a single round trip, the timeout does not apply.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1a87-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d1a87-108">See also</span></span>

- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- [<span data-ttu-id="d1a87-109">Nasıl yapılır: Maksimum Saat Eğriltme Ayarlama</span><span class="sxs-lookup"><span data-stu-id="d1a87-109">How to: Set a Max Clock Skew</span></span>](how-to-set-a-max-clock-skew.md)

---
title: Güvenlik Görüşmeleri ve Zaman Aşımları
ms.date: 03/30/2017
ms.assetid: 02a428f1-84e5-4d28-a11f-53ce31d63196
ms.openlocfilehash: 38dce9bd6587850a5e3327600bb8bc13c48b93e1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54592620"
---
# <a name="security-negotiation-and-timeouts"></a><span data-ttu-id="eb6de-102">Güvenlik Görüşmeleri ve Zaman Aşımları</span><span class="sxs-lookup"><span data-stu-id="eb6de-102">Security Negotiation and Timeouts</span></span>
<span data-ttu-id="eb6de-103">İstemciler ve hizmetler kimlik doğrulaması sırasında Windows Communication Foundation (WCF) hizmet kimlik bilgisi kimlik doğrulaması bir parçası olarak nerede anlaşılan bir modu destekler.</span><span class="sxs-lookup"><span data-stu-id="eb6de-103">When clients and services authenticate, Windows Communication Foundation (WCF) supports a mode where the service credential is negotiated as part of authentication.</span></span> <span data-ttu-id="eb6de-104">Böyle senaryolarda, büyük olasılıkla çok oluşturan exchange istemci ve hizmet için hizmet kimlik bilgilerini istemci yayılması arasında gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="eb6de-104">In such scenarios, a potentially multi-leg exchange occurs between the client and the service to propagate the service credential to the client.</span></span> <span data-ttu-id="eb6de-105"><xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> Özellik denetler çok oluşturan exchange tamamlanması ne kadar sürebilir.</span><span class="sxs-lookup"><span data-stu-id="eb6de-105">The <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property controls how long the multi-leg exchange can take to complete.</span></span> <span data-ttu-id="eb6de-106">Exchange gerçekten daha fazla sürer ancak, bu zaman aşımı yalnızca geçerlidir, tek bir istek-yanıt.</span><span class="sxs-lookup"><span data-stu-id="eb6de-106">However, this timeout only applies if the exchange actually takes more that a single request-response.</span></span> <span data-ttu-id="eb6de-107">Burada anlaşma tek bir gidiş dönüş tamamlandıktan durumlarda, zaman aşımı geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="eb6de-107">In cases where the negotiation completes in a single round trip, the timeout does not apply.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb6de-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb6de-108">See also</span></span>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- [<span data-ttu-id="eb6de-109">Nasıl yapılır: Maksimum saat eğriltme ayarlama</span><span class="sxs-lookup"><span data-stu-id="eb6de-109">How to: Set a Max Clock Skew</span></span>](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)

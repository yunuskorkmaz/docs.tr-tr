---
title: WCF'de Güvenlik Değerlendirmeleri
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF]
- Windows Communication Foundation, security
- WCF, security
ms.assetid: 42055ee0-6d0c-443d-9d89-788dfc345d6d
author: BrucePerlerMS
ms.openlocfilehash: f26369a567e89fc502f777383c22e74b96fe503c
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47198045"
---
# <a name="security-considerations-in-wcf"></a><span data-ttu-id="3eecc-102">WCF'de Güvenlik Değerlendirmeleri</span><span class="sxs-lookup"><span data-stu-id="3eecc-102">Security Considerations in WCF</span></span>
<span data-ttu-id="3eecc-103">Bu bölümdeki konularda, Windows Communication Foundation (WCF) bir uygulama tasarlanırken dikkate alınması gereken çeşitli güvenlikle ilgili öğeleri listelenir.</span><span class="sxs-lookup"><span data-stu-id="3eecc-103">The topics in this section list various security-related items to consider when designing a Windows Communication Foundation (WCF) application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3eecc-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="3eecc-104">In This Section</span></span>  
 [<span data-ttu-id="3eecc-105">Bilgilerin Açığa Çıkması</span><span class="sxs-lookup"><span data-stu-id="3eecc-105">Information Disclosure</span></span>](../../../../docs/framework/wcf/feature-details/information-disclosure.md)  
 <span data-ttu-id="3eecc-106">Çeşitli yollarla bilgi ifşa veya Saldırıya uğrayan dikkat ve bunu azaltmak nasıl ele alır.</span><span class="sxs-lookup"><span data-stu-id="3eecc-106">Discusses the various ways that information can be disclosed or attacked, and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="3eecc-107">Ayrıcalıkların Yükseltilmesi</span><span class="sxs-lookup"><span data-stu-id="3eecc-107">Elevation of Privilege</span></span>](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)  
 <span data-ttu-id="3eecc-108">Başlangıçta verilen ötesinde bir saldırgan yetkilendirme izni ve bunu azaltmak nasıl etkilerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="3eecc-108">Discusses the effects of giving an attacker authorization permissions beyond those initially granted and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="3eecc-109">Hizmet Reddi</span><span class="sxs-lookup"><span data-stu-id="3eecc-109">Denial of Service</span></span>](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 <span data-ttu-id="3eecc-110">Ne olacağını açıklar bir sistemde iletilerin uygun şekilde işleyemedi olduğunda ve nasıl önlenebileceğini.</span><span class="sxs-lookup"><span data-stu-id="3eecc-110">Discusses what happens when a system is unable to process messages appropriately and how to mitigate it.</span></span>  
  
 [<span data-ttu-id="3eecc-111">İzinsiz Değişiklik</span><span class="sxs-lookup"><span data-stu-id="3eecc-111">Tampering</span></span>](../../../../docs/framework/wcf/feature-details/tampering.md)  
 <span data-ttu-id="3eecc-112">İletileri veya iletileri ve nasıl önlenebileceğini teslimini değiştirmeyi anlatır.</span><span class="sxs-lookup"><span data-stu-id="3eecc-112">Discusses the altering of messages or the delivery of messages and how to mitigate it.</span></span>  
  
 [<span data-ttu-id="3eecc-113">Yeniden Yürütme Saldırıları</span><span class="sxs-lookup"><span data-stu-id="3eecc-113">Replay Attacks</span></span>](../../../../docs/framework/wcf/feature-details/replay-attacks.md)  
 <span data-ttu-id="3eecc-114">Bir saldırganın kopyalarken arasında iki ileti akışı taraflarla ve bir veya daha fazla taraflar akışa başlayarak yeniden oynatılır ne olur ve bu durumu iyileştirmek nasıl ele alır.</span><span class="sxs-lookup"><span data-stu-id="3eecc-114">Discusses what happens when an attacker copies a stream of messages between two parties and replays the stream to one or more of the parties, and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="3eecc-115">Güvenli Oturumlar için Güvenlikle İlgili Önemli Noktalar</span><span class="sxs-lookup"><span data-stu-id="3eecc-115">Security Considerations for Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md)  
 <span data-ttu-id="3eecc-116">Güvenli oturumlar uygularken güvenliğini etkileyen aşağıdaki öğeleri açıklanır.</span><span class="sxs-lookup"><span data-stu-id="3eecc-116">Discusses the following items that affect security when implementing secure sessions.</span></span>  
  
 [<span data-ttu-id="3eecc-117">Desteklenmeyen Senaryolar</span><span class="sxs-lookup"><span data-stu-id="3eecc-117">Unsupported Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)  
 <span data-ttu-id="3eecc-118">Belirli bir güvenlik durumuyla desteklemez ve önlenmiş veya kabul çeşitli senaryolar listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="3eecc-118">Lists various scenarios that do not support a particular aspect of security and should be avoided or considered.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="3eecc-119">Başvuru</span><span class="sxs-lookup"><span data-stu-id="3eecc-119">Reference</span></span>  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="3eecc-120">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="3eecc-120">Related Sections</span></span>  
 [<span data-ttu-id="3eecc-121">Güvenlik Kılavuzu ve En İyi Uygulamalar</span><span class="sxs-lookup"><span data-stu-id="3eecc-121">Security Guidance and Best Practices</span></span>](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)  
  
## <a name="see-also"></a><span data-ttu-id="3eecc-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3eecc-122">See Also</span></span>  
 [<span data-ttu-id="3eecc-123">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="3eecc-123">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)

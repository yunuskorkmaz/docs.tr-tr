---
title: Güvenli Oturumlar
ms.date: 03/30/2017
ms.assetid: 7b50602f-d7b5-42e9-8e92-1f0413df0d8b
ms.openlocfilehash: 8f5cf9a965951bcc1049c2e96ae6cfa80b0113ba
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59084985"
---
# <a name="secure-sessions"></a><span data-ttu-id="258df-102">Güvenli Oturumlar</span><span class="sxs-lookup"><span data-stu-id="258df-102">Secure Sessions</span></span>
<span data-ttu-id="258df-103">Bir Windows Communication Foundation (WCF) iletiler gönderildikleri sırayla alınır garanti güvenilir oturumlar özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="258df-103">A feature of Windows Communication Foundation (WCF) is reliable sessions that guarantee messages are received in the order they were sent.</span></span> <span data-ttu-id="258df-104">Bu bölümdeki konular, bir güvenilir oturum oluştururken dikkate alınması gereken güvenlikle ilgili etkileri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="258df-104">The topics in this section discuss the security implications to consider when creating a reliable session.</span></span> <span data-ttu-id="258df-105">Güvenilir oturumlar hakkında daha fazla bilgi için bkz: [oturumları kullanarak](../../../../docs/framework/wcf/using-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="258df-105">For more information about reliable sessions, see [Using Sessions](../../../../docs/framework/wcf/using-sessions.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="258df-106">Kimliğe bürünme Windows XP'de gerektiğinde bir durum bilgisi olan güvenlik bağlamı belirteci (SCT) olmadan güvenli bir oturum kullanın.</span><span class="sxs-lookup"><span data-stu-id="258df-106">When impersonation is required on Windows XP, use a secure session without a stateful security context token (SCT).</span></span> <span data-ttu-id="258df-107">Durum bilgisi olan SCTs kimliğe bürünme ile kullanıldığında bir <xref:System.InvalidOperationException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="258df-107">When stateful SCTs are used with impersonation, an <xref:System.InvalidOperationException> is thrown.</span></span> <span data-ttu-id="258df-108">Daha fazla bilgi için [desteklenmeyen senaryolar](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="258df-108">For more information, see [Unsupported Scenarios](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="258df-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="258df-109">In This Section</span></span>  
  
|||  
|-|-|  
|[<span data-ttu-id="258df-110">Güvenli İletişimler ve Güvenli Oturumlar</span><span class="sxs-lookup"><span data-stu-id="258df-110">Secure Conversations and Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)|<span data-ttu-id="258df-111">Güvenli konuşma ve güvenli oturumlar eşanlamlıdır.</span><span class="sxs-lookup"><span data-stu-id="258df-111">Secure conversations and secure sessions are synonymous.</span></span> <span data-ttu-id="258df-112">Bu konu, güvenli konuşma, nasıl işlediğini gösteren açıklar ve ne zaman ve neden bu düzeni kullanın.</span><span class="sxs-lookup"><span data-stu-id="258df-112">This topic explains the way a secure conversation works, and when and why to use the pattern.</span></span>|  
|[<span data-ttu-id="258df-113">Nasıl yapılır: Güvenli Oturum Oluşturma</span><span class="sxs-lookup"><span data-stu-id="258df-113">How to: Create a Secure Session</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-secure-session.md)|<span data-ttu-id="258df-114">Güvenli oturum oluşturma hakkındaki temel bilgileri adım adım açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="258df-114">Walks through of the basics of creating a secure session.</span></span>|  
|[<span data-ttu-id="258df-115">Nasıl yapılır: Güvenli Bir Oturum için Güvenlik Bağlamı Belirteci Oluşturma</span><span class="sxs-lookup"><span data-stu-id="258df-115">How to: Create a Security Context Token for a Secure Session</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)|<span data-ttu-id="258df-116">Durum ve istemcilerle oturumları tutacaktır bir Web grubu oluşturma adımlarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="258df-116">Walks through the steps of creating a Web farm that will maintain state and sessions with clients.</span></span>|  
|[<span data-ttu-id="258df-117">Güvenli Oturumlar için Güvenlikli İlgili Önemli Noktalar</span><span class="sxs-lookup"><span data-stu-id="258df-117">Security Considerations for Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md)|<span data-ttu-id="258df-118">Güvenli oturumlar için özel hususlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="258df-118">Describes special considerations for secure sessions.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="258df-119">Başvuru</span><span class="sxs-lookup"><span data-stu-id="258df-119">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
## <a name="related-sections"></a><span data-ttu-id="258df-120">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="258df-120">Related Sections</span></span>  
 [<span data-ttu-id="258df-121">Oturumlar, Örnek Oluşturma ve Eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="258df-121">Sessions, Instancing, and Concurrency</span></span>](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
  
 [<span data-ttu-id="258df-122">Hizmetleri Tasarlama ve Uygulama</span><span class="sxs-lookup"><span data-stu-id="258df-122">Designing and Implementing Services</span></span>](../../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="258df-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="258df-123">See also</span></span>

- [<span data-ttu-id="258df-124">Nasıl yapılır: İleti Yeniden Yürütme Algılamayı Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="258df-124">How to: Enable Message Replay Detection</span></span>](../../../../docs/framework/wcf/feature-details/how-to-enable-message-replay-detection.md)
- [<span data-ttu-id="258df-125">Yeniden Yürütme Saldırıları</span><span class="sxs-lookup"><span data-stu-id="258df-125">Replay Attacks</span></span>](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
- [<span data-ttu-id="258df-126">Nasıl yapılır: Oturum Gerektiren Bir Hizmet Oluşturma</span><span class="sxs-lookup"><span data-stu-id="258df-126">How to: Create a Service That Requires Sessions</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)

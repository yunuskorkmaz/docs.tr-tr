---
title: Güvenli Oturumlar
ms.date: 03/30/2017
ms.assetid: 7b50602f-d7b5-42e9-8e92-1f0413df0d8b
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 1c7229fba8e30632f08834eb36c1fb177de7a294
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33497548"
---
# <a name="secure-sessions"></a><span data-ttu-id="651e6-102">Güvenli Oturumlar</span><span class="sxs-lookup"><span data-stu-id="651e6-102">Secure Sessions</span></span>
<span data-ttu-id="651e6-103">Bir Windows Communication Foundation (WCF) ileti gönderildikleri sırayla alınır garanti güvenilir oturumlar özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="651e6-103">A feature of Windows Communication Foundation (WCF) is reliable sessions that guarantee messages are received in the order they were sent.</span></span> <span data-ttu-id="651e6-104">Bu bölümdeki konular, güvenilir bir oturum oluştururken dikkate alınması gereken güvenlik uygulamalarını tartışın.</span><span class="sxs-lookup"><span data-stu-id="651e6-104">The topics in this section discuss the security implications to consider when creating a reliable session.</span></span> <span data-ttu-id="651e6-105">Güvenilir oturumlar hakkında daha fazla bilgi için bkz: [kullanarak oturumları](../../../../docs/framework/wcf/using-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="651e6-105">For more information about reliable sessions, see [Using Sessions](../../../../docs/framework/wcf/using-sessions.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="651e6-106">Kimliğe bürünme Windows XP'de gerektiğinde bir durum bilgisi olan güvenlik bağlamı belirteci (SCT) olmadan güvenli bir oturum kullanın.</span><span class="sxs-lookup"><span data-stu-id="651e6-106">When impersonation is required on Windows XP, use a secure session without a stateful security context token (SCT).</span></span> <span data-ttu-id="651e6-107">Durum bilgisi olan SCTs kimliğe bürünme ile kullanıldığında bir <xref:System.InvalidOperationException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="651e6-107">When stateful SCTs are used with impersonation, an <xref:System.InvalidOperationException> is thrown.</span></span> <span data-ttu-id="651e6-108">Daha fazla bilgi için bkz: [desteklenmeyen senaryolar](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="651e6-108">For more information, see [Unsupported Scenarios](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="651e6-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="651e6-109">In This Section</span></span>  
  
|||  
|-|-|  
|[<span data-ttu-id="651e6-110">Güvenli İletişimler ve Güvenli Oturumlar</span><span class="sxs-lookup"><span data-stu-id="651e6-110">Secure Conversations and Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)|<span data-ttu-id="651e6-111">Güvenli görüşmeler ve güvenli oturumlar eşanlamlıdır.</span><span class="sxs-lookup"><span data-stu-id="651e6-111">Secure conversations and secure sessions are synonymous.</span></span> <span data-ttu-id="651e6-112">Bu konuda, güvenli bir konuşma çalışır, şekilde açıklanmıştır ve dosyası, ne zaman ve neden deseni kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="651e6-112">This topic explains the way a secure conversation works, and when and why to use the pattern.</span></span>|  
|[<span data-ttu-id="651e6-113">Nasıl yapılır: Güvenli Oturum Oluşturma</span><span class="sxs-lookup"><span data-stu-id="651e6-113">How to: Create a Secure Session</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-secure-session.md)|<span data-ttu-id="651e6-114">Güvenli oturum oluşturma temelleri adım adım açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="651e6-114">Walks through of the basics of creating a secure session.</span></span>|  
|[<span data-ttu-id="651e6-115">Nasıl yapılır: Güvenli Bir Oturum için Güvenlik Bağlamı Belirteci Oluşturma</span><span class="sxs-lookup"><span data-stu-id="651e6-115">How to: Create a Security Context Token for a Secure Session</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)|<span data-ttu-id="651e6-116">Durum ve oturumlar istemcilerle tutacağı bir Web grubu oluşturma adımları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="651e6-116">Walks through the steps of creating a Web farm that will maintain state and sessions with clients.</span></span>|  
|[<span data-ttu-id="651e6-117">Güvenli Oturumlar için Güvenlikle İlgili Önemli Noktalar</span><span class="sxs-lookup"><span data-stu-id="651e6-117">Security Considerations for Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md)|<span data-ttu-id="651e6-118">Güvenli oturumlar için özel hususlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="651e6-118">Describes special considerations for secure sessions.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="651e6-119">Başvuru</span><span class="sxs-lookup"><span data-stu-id="651e6-119">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
## <a name="related-sections"></a><span data-ttu-id="651e6-120">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="651e6-120">Related Sections</span></span>  
 [<span data-ttu-id="651e6-121">Oturumlar, Örnek Oluşturma ve Eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="651e6-121">Sessions, Instancing, and Concurrency</span></span>](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
  
 [<span data-ttu-id="651e6-122">Hizmetleri Tasarlama ve Uygulama</span><span class="sxs-lookup"><span data-stu-id="651e6-122">Designing and Implementing Services</span></span>](../../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="651e6-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="651e6-123">See Also</span></span>  
 [<span data-ttu-id="651e6-124">Nasıl yapılır: İleti Yeniden Yürütme Algılamayı Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="651e6-124">How to: Enable Message Replay Detection</span></span>](../../../../docs/framework/wcf/feature-details/how-to-enable-message-replay-detection.md)  
 [<span data-ttu-id="651e6-125">Yeniden Yürütme Saldırıları</span><span class="sxs-lookup"><span data-stu-id="651e6-125">Replay Attacks</span></span>](../../../../docs/framework/wcf/feature-details/replay-attacks.md)  
 [<span data-ttu-id="651e6-126">Nasıl yapılır: Oturum Gerektiren Bir Hizmet Oluşturma</span><span class="sxs-lookup"><span data-stu-id="651e6-126">How to: Create a Service That Requires Sessions</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)

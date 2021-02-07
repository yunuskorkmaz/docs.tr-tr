---
description: 'Daha fazla bilgi edinin: güvenli oturumlar'
title: Güvenli Oturumlar
ms.date: 03/30/2017
ms.assetid: 7b50602f-d7b5-42e9-8e92-1f0413df0d8b
ms.openlocfilehash: 8a4a2d23d5a27f5066bd5f004582829e499f714c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99733079"
---
# <a name="secure-sessions"></a><span data-ttu-id="1c4c2-103">Güvenli Oturumlar</span><span class="sxs-lookup"><span data-stu-id="1c4c2-103">Secure Sessions</span></span>

<span data-ttu-id="1c4c2-104">Windows Communication Foundation (WCF) özelliği, iletilerin gönderildikleri sırada alınabileceğini garanti eden güvenilir oturumlardır.</span><span class="sxs-lookup"><span data-stu-id="1c4c2-104">A feature of Windows Communication Foundation (WCF) is reliable sessions that guarantee messages are received in the order they were sent.</span></span> <span data-ttu-id="1c4c2-105">Bu bölümdeki konularda, güvenilir bir oturum oluştururken dikkate alınması gereken güvenlik etkileri ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1c4c2-105">The topics in this section discuss the security implications to consider when creating a reliable session.</span></span> <span data-ttu-id="1c4c2-106">Güvenilir oturumlar hakkında daha fazla bilgi için bkz. [oturumları kullanma](../using-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="1c4c2-106">For more information about reliable sessions, see [Using Sessions](../using-sessions.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1c4c2-107">Windows XP 'de kimliğe bürünme özelliği gerekli olduğunda, durum bilgisi olan güvenlik bağlamı belirteci (SCT) olmadan güvenli bir oturum kullanın.</span><span class="sxs-lookup"><span data-stu-id="1c4c2-107">When impersonation is required on Windows XP, use a secure session without a stateful security context token (SCT).</span></span> <span data-ttu-id="1c4c2-108">Durum bilgisi olan SCN 'ler kimliğe bürünme ile kullanıldığında bir oluşturulur <xref:System.InvalidOperationException> .</span><span class="sxs-lookup"><span data-stu-id="1c4c2-108">When stateful SCTs are used with impersonation, an <xref:System.InvalidOperationException> is thrown.</span></span> <span data-ttu-id="1c4c2-109">Daha fazla bilgi için bkz. [desteklenmeyen senaryolar](unsupported-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="1c4c2-109">For more information, see [Unsupported Scenarios](unsupported-scenarios.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1c4c2-110">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="1c4c2-110">In This Section</span></span>  
  
|||  
|-|-|  
|[<span data-ttu-id="1c4c2-111">Güvenli İletişimler ve Güvenli Oturumlar</span><span class="sxs-lookup"><span data-stu-id="1c4c2-111">Secure Conversations and Secure Sessions</span></span>](secure-conversations-and-secure-sessions.md)|<span data-ttu-id="1c4c2-112">Güvenli konuşmalar ve güvenli oturumlar eşanlamlı olarak anlamlıdır.</span><span class="sxs-lookup"><span data-stu-id="1c4c2-112">Secure conversations and secure sessions are synonymous.</span></span> <span data-ttu-id="1c4c2-113">Bu konuda, güvenli bir konuşmanın çalışma şekli ve düzenin ne zaman ve neden kullanıldığı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1c4c2-113">This topic explains the way a secure conversation works, and when and why to use the pattern.</span></span>|  
|[<span data-ttu-id="1c4c2-114">Nasıl yapılır: Güvenli Oturum Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1c4c2-114">How to: Create a Secure Session</span></span>](how-to-create-a-secure-session.md)|<span data-ttu-id="1c4c2-115">Güvenli bir oturum oluşturma hakkındaki temel bilgileri adım adım açıklar.</span><span class="sxs-lookup"><span data-stu-id="1c4c2-115">Walks through of the basics of creating a secure session.</span></span>|  
|[<span data-ttu-id="1c4c2-116">Nasıl yapılır: Güvenli Bir Oturum için Güvenlik Bağlamı Belirteci Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1c4c2-116">How to: Create a Security Context Token for a Secure Session</span></span>](how-to-create-a-security-context-token-for-a-secure-session.md)|<span data-ttu-id="1c4c2-117">İstemcilerle durum ve oturumları koruyacak bir Web grubu oluşturma adımlarında size yol gösterir.</span><span class="sxs-lookup"><span data-stu-id="1c4c2-117">Walks through the steps of creating a Web farm that will maintain state and sessions with clients.</span></span>|  
|[<span data-ttu-id="1c4c2-118">Güvenli Oturumlar için Güvenlikli İlgili Önemli Noktalar</span><span class="sxs-lookup"><span data-stu-id="1c4c2-118">Security Considerations for Secure Sessions</span></span>](security-considerations-for-secure-sessions.md)|<span data-ttu-id="1c4c2-119">Güvenli oturumlar için özel konuları açıklar.</span><span class="sxs-lookup"><span data-stu-id="1c4c2-119">Describes special considerations for secure sessions.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="1c4c2-120">Başvuru</span><span class="sxs-lookup"><span data-stu-id="1c4c2-120">Reference</span></span>  

 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
## <a name="related-sections"></a><span data-ttu-id="1c4c2-121">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="1c4c2-121">Related Sections</span></span>  

 [<span data-ttu-id="1c4c2-122">Oturumlar, Örnek Oluşturma ve Eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="1c4c2-122">Sessions, Instancing, and Concurrency</span></span>](sessions-instancing-and-concurrency.md)  
  
 [<span data-ttu-id="1c4c2-123">Hizmetleri Tasarlama ve Uygulama</span><span class="sxs-lookup"><span data-stu-id="1c4c2-123">Designing and Implementing Services</span></span>](../designing-and-implementing-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="1c4c2-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c4c2-124">See also</span></span>

- [<span data-ttu-id="1c4c2-125">Nasıl yapılır: İleti Yeniden Yürütme Algılamayı Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="1c4c2-125">How to: Enable Message Replay Detection</span></span>](how-to-enable-message-replay-detection.md)
- [<span data-ttu-id="1c4c2-126">Yeniden Yürütme Saldırıları</span><span class="sxs-lookup"><span data-stu-id="1c4c2-126">Replay Attacks</span></span>](replay-attacks.md)
- [<span data-ttu-id="1c4c2-127">Nasıl yapılır: Oturum Gerektiren Bir Hizmet Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1c4c2-127">How to: Create a Service That Requires Sessions</span></span>](how-to-create-a-service-that-requires-sessions.md)

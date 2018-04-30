---
title: Güvenli Oturumlar
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b50602f-d7b5-42e9-8e92-1f0413df0d8b
caps.latest.revision: 14
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 068615510d7e1d73ae260441ccef6536ee6ff317
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="secure-sessions"></a><span data-ttu-id="45d85-102">Güvenli Oturumlar</span><span class="sxs-lookup"><span data-stu-id="45d85-102">Secure Sessions</span></span>
<span data-ttu-id="45d85-103">Bir özellik olan [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] iletileri gönderildiği adres sıraya alınan garanti güvenilir oturumdur.</span><span class="sxs-lookup"><span data-stu-id="45d85-103">A feature of [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] is reliable sessions that guarantee messages are received in the order they were sent.</span></span> <span data-ttu-id="45d85-104">Bu bölümdeki konular, güvenilir bir oturum oluştururken dikkate alınması gereken güvenlik uygulamalarını tartışın.</span><span class="sxs-lookup"><span data-stu-id="45d85-104">The topics in this section discuss the security implications to consider when creating a reliable session.</span></span> <span data-ttu-id="45d85-105">Güvenilir oturumlar hakkında daha fazla bilgi için bkz: [kullanarak oturumları](../../../../docs/framework/wcf/using-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="45d85-105">For more information about reliable sessions, see [Using Sessions](../../../../docs/framework/wcf/using-sessions.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="45d85-106">Kimliğe bürünme Windows XP'de gerektiğinde bir durum bilgisi olan güvenlik bağlamı belirteci (SCT) olmadan güvenli bir oturum kullanın.</span><span class="sxs-lookup"><span data-stu-id="45d85-106">When impersonation is required on Windows XP, use a secure session without a stateful security context token (SCT).</span></span> <span data-ttu-id="45d85-107">Durum bilgisi olan SCTs kimliğe bürünme ile kullanıldığında bir <xref:System.InvalidOperationException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="45d85-107">When stateful SCTs are used with impersonation, an <xref:System.InvalidOperationException> is thrown.</span></span> <span data-ttu-id="45d85-108">Daha fazla bilgi için bkz: [desteklenmeyen senaryolar](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="45d85-108">For more information, see [Unsupported Scenarios](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="45d85-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="45d85-109">In This Section</span></span>  
  
|||  
|-|-|  
|[<span data-ttu-id="45d85-110">Güvenli İletişimler ve Güvenli Oturumlar</span><span class="sxs-lookup"><span data-stu-id="45d85-110">Secure Conversations and Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)|<span data-ttu-id="45d85-111">Güvenli görüşmeler ve güvenli oturumlar eşanlamlıdır.</span><span class="sxs-lookup"><span data-stu-id="45d85-111">Secure conversations and secure sessions are synonymous.</span></span> <span data-ttu-id="45d85-112">Bu konuda, güvenli bir konuşma çalışır, şekilde açıklanmıştır ve dosyası, ne zaman ve neden deseni kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="45d85-112">This topic explains the way a secure conversation works, and when and why to use the pattern.</span></span>|  
|[<span data-ttu-id="45d85-113">Nasıl yapılır: Güvenli Oturum Oluşturma</span><span class="sxs-lookup"><span data-stu-id="45d85-113">How to: Create a Secure Session</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-secure-session.md)|<span data-ttu-id="45d85-114">Güvenli oturum oluşturma temelleri adım adım açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="45d85-114">Walks through of the basics of creating a secure session.</span></span>|  
|[<span data-ttu-id="45d85-115">Nasıl yapılır: Güvenli Bir Oturum için Güvenlik Bağlamı Belirteci Oluşturma</span><span class="sxs-lookup"><span data-stu-id="45d85-115">How to: Create a Security Context Token for a Secure Session</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)|<span data-ttu-id="45d85-116">Durum ve oturumlar istemcilerle tutacağı bir Web grubu oluşturma adımları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="45d85-116">Walks through the steps of creating a Web farm that will maintain state and sessions with clients.</span></span>|  
|[<span data-ttu-id="45d85-117">Güvenli Oturumlar için Güvenlikle İlgili Önemli Noktalar</span><span class="sxs-lookup"><span data-stu-id="45d85-117">Security Considerations for Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md)|<span data-ttu-id="45d85-118">Güvenli oturumlar için özel hususlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="45d85-118">Describes special considerations for secure sessions.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="45d85-119">Başvuru</span><span class="sxs-lookup"><span data-stu-id="45d85-119">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
## <a name="related-sections"></a><span data-ttu-id="45d85-120">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="45d85-120">Related Sections</span></span>  
 [<span data-ttu-id="45d85-121">Oturumlar, Örnek Oluşturma ve Eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="45d85-121">Sessions, Instancing, and Concurrency</span></span>](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
  
 [<span data-ttu-id="45d85-122">Hizmetleri Tasarlama ve Uygulama</span><span class="sxs-lookup"><span data-stu-id="45d85-122">Designing and Implementing Services</span></span>](../../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="45d85-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="45d85-123">See Also</span></span>  
 [<span data-ttu-id="45d85-124">Nasıl yapılır: İleti Yeniden Yürütme Algılamayı Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="45d85-124">How to: Enable Message Replay Detection</span></span>](../../../../docs/framework/wcf/feature-details/how-to-enable-message-replay-detection.md)  
 [<span data-ttu-id="45d85-125">Yeniden Yürütme Saldırıları</span><span class="sxs-lookup"><span data-stu-id="45d85-125">Replay Attacks</span></span>](../../../../docs/framework/wcf/feature-details/replay-attacks.md)  
 [<span data-ttu-id="45d85-126">Nasıl yapılır: Oturum Gerektiren Bir Hizmet Oluşturma</span><span class="sxs-lookup"><span data-stu-id="45d85-126">How to: Create a Service That Requires Sessions</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)

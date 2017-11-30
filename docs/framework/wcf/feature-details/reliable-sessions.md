---
title: "Güvenilir oturumlar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Windows Communication Foundation, sessions and instances
- WCF, sessions and instances
- sessions and instances [WCF]
helpviewer_keywords:
- instances [WCF]
- sessions [WCF]
ms.assetid: 143951b3-3aa0-4540-b4b7-d33e77e874a1
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 659309ff5560480c423fc9b0adab5e93eac05ce5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="reliable-sessions"></a><span data-ttu-id="737da-102">Güvenilir oturumlar</span><span class="sxs-lookup"><span data-stu-id="737da-102">Reliable Sessions</span></span>

<span data-ttu-id="737da-103">Bu bölümde açıklanmaktadır bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] güvenilir oturum olduğundan, ne, nasıl kullanıldığı ve ne zaman kullanmak için hangi bağlama yapılandırmaları destekliyorsa ve işaretçilerde en iyi uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="737da-103">This section describes what a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] reliable session is, what it's used for, how and when to use one, what binding configurations support it, and pointers on best practices.</span></span> <span data-ttu-id="737da-104">Önemli noktaları ve bu bölümdeki ilgili konular hakkında ayrıntılar aşağıdaki tabloda özetlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="737da-104">The following table summarizes details about the essential points and related topics in this section.</span></span>

<span data-ttu-id="737da-105">Güvenilir oturum [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uç noktaları arasında gönderilen iletileri SOAP veya taşıma aracılar aktarılır ve yalnızca bir kez ve isteğe bağlı olarak, bunlar gönderildiği adres aynı sırayla teslim sağlayarak featrues sağlar.</span><span class="sxs-lookup"><span data-stu-id="737da-105">The reliable session [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides featrues ensuring that messages sent between endpoints are transferred across SOAP or transport intermediaries and are delivered only once and, optionally, in the same order in which they were sent.</span></span>

<span data-ttu-id="737da-106">Güvenilir bir oturum ile kullanmak için bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulamanın, aşağıdakilerden birini kullanın sistem tarafından sağlanan bağlamalar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] , varsayılan olarak veya bir seçenek olarak güvenilir oturum desteklemek veya oturumu destekler, kendi özel bağlama oluşturma.</span><span class="sxs-lookup"><span data-stu-id="737da-106">To use a reliable session with a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application, either use one of the system-provided bindings in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] that support a reliable session by default or as an option, or create your own custom binding that supports the session.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="737da-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="737da-107">In This Section</span></span>

<span data-ttu-id="737da-108">[Güvenilir oturumlar genel bakış](../../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md) </span><span class="sxs-lookup"><span data-stu-id="737da-108">[Reliable Sessions Overview](../../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md) </span></span>  
<span data-ttu-id="737da-109">Güvenilir oturumlar açıklar bunların güvenilir oturumlar destek farklı bağlamaları ne zaman kullanılacağı ve nasıl çalışırlar.</span><span class="sxs-lookup"><span data-stu-id="737da-109">Describes reliable sessions, when to use them, the different bindings that support reliable sessions, and how they work.</span></span>

<span data-ttu-id="737da-110">[Nasıl yapılır: bir güvenilir oturum içinde iletileri Exchange](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md) </span><span class="sxs-lookup"><span data-stu-id="737da-110">[How to: Exchange Messages Within a Reliable Session](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md) </span></span>  
<span data-ttu-id="737da-111">Yapılandırmada belirtilen özel bağlama kullanma HTTP üzerinden bir güvenilir oturum oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="737da-111">Describes how to create a reliable session over HTTP using a custom binding specified in the configuration.</span></span>

<span data-ttu-id="737da-112">[Nasıl yapılır: oturumlarla iletileri güvenli](../../../../docs/framework/wcf/feature-details/how-to-secure-messages-within-reliable-sessions.md) </span><span class="sxs-lookup"><span data-stu-id="737da-112">[How to: Secure Messages within Reliable Sessions](../../../../docs/framework/wcf/feature-details/how-to-secure-messages-within-reliable-sessions.md) </span></span>  
<span data-ttu-id="737da-113">Güvenilir oturum güvenli açıklar.</span><span class="sxs-lookup"><span data-stu-id="737da-113">Describes how to secure a reliable session.</span></span>

<span data-ttu-id="737da-114">[Nasıl yapılır: HTTPS ile özel bir güvenilir oturum bağlama oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md) </span><span class="sxs-lookup"><span data-stu-id="737da-114">[How to: Create a Custom Reliable Session Binding with HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md) </span></span>  
<span data-ttu-id="737da-115">HTTPS üzerinden güvenli bir oturum oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="737da-115">Describes how to create a reliable session over HTTPS.</span></span>

<span data-ttu-id="737da-116">[Güvenilir oturumlar için en iyi yöntemler](../../../../docs/framework/wcf/feature-details/best-practices-for-reliable-sessions.md) </span><span class="sxs-lookup"><span data-stu-id="737da-116">[Best Practices for Reliable Sessions](../../../../docs/framework/wcf/feature-details/best-practices-for-reliable-sessions.md) </span></span>  
<span data-ttu-id="737da-117">Güvenilir oturum kullanmayla ilişkili en iyi uygulamaları bazıları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="737da-117">Describes some of the best practices associated with using a reliable session.</span></span>

## <a name="reference"></a><span data-ttu-id="737da-118">Başvuru</span><span class="sxs-lookup"><span data-stu-id="737da-118">Reference</span></span>

<xref:System.ServiceModel.ReliableSession>

## <a name="see-also"></a><span data-ttu-id="737da-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="737da-119">See Also</span></span>

<span data-ttu-id="737da-120">[Kuyruklar ve güvenilir oturumlar](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md) </span><span class="sxs-lookup"><span data-stu-id="737da-120">[Queues and Reliable Sessions](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md) </span></span>  
[<span data-ttu-id="737da-121">Oturumlar, örnek oluşturma ve eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="737da-121">Sessions, Instancing, and Concurrency</span></span>](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)

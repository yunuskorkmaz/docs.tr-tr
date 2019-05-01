---
title: Güvenilir oturumlar
ms.date: 03/30/2017
f1_keywords:
- Windows Communication Foundation, sessions and instances
- WCF, sessions and instances
- sessions and instances [WCF]
helpviewer_keywords:
- instances [WCF]
- sessions [WCF]
ms.assetid: 143951b3-3aa0-4540-b4b7-d33e77e874a1
ms.openlocfilehash: 9a2cd06c4c5a73d9fb5c4c7f09632e10c3eb0d87
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991165"
---
# <a name="reliable-sessions"></a><span data-ttu-id="d73e9-102">Güvenilir oturumlar</span><span class="sxs-lookup"><span data-stu-id="d73e9-102">Reliable Sessions</span></span>

<span data-ttu-id="d73e9-103">Bu bölümde, hangi bir Windows Communication Foundation (güvenilir oturum WCF), ne, nasıl kullanıldığı ve ne zaman kullanmak için hangi bağlama yapılandırmaları destekliyorsa ve işaretçilerde en iyi uygulamalar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d73e9-103">This section describes what a Windows Communication Foundation (WCF) reliable session is, what it's used for, how and when to use one, what binding configurations support it, and pointers on best practices.</span></span> <span data-ttu-id="d73e9-104">Önemli noktaları ve bu bölümdeki ilgili konular hakkında ayrıntıları aşağıdaki tabloda özetlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="d73e9-104">The following table summarizes details about the essential points and related topics in this section.</span></span>

<span data-ttu-id="d73e9-105">Güvenilir oturum WCF uç noktaları arasında gönderilen iletilerin SOAP veya aktarım aracılar arasında aktarılır ve yalnızca bir kez ve isteğe bağlı olarak, hangi gönderildikleri sırayla teslim sağlama özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="d73e9-105">The reliable session WCF provides features ensuring that messages sent between endpoints are transferred across SOAP or transport intermediaries and are delivered only once and, optionally, in the same order in which they were sent.</span></span>

<span data-ttu-id="d73e9-106">Güvenilir oturum WCF uygulamayla kullanmak için varsayılan olarak veya isteğe bağlı olarak bir güvenilir oturum destekleyen sistem tarafından sağlanan bağlamalar wcf'de birini kullanın veya oturumu destekler, kendi özel bağlama oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d73e9-106">To use a reliable session with a WCF application, either use one of the system-provided bindings in WCF that support a reliable session by default or as an option, or create your own custom binding that supports the session.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="d73e9-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="d73e9-107">In This Section</span></span>

<span data-ttu-id="d73e9-108">[Güvenilir oturumlar genel bakış](../../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md) güvenilir oturumlar açıklar bunların güvenilir oturumları destekleyen farklı bağlamaları ne zaman kullanılacağı ve nasıl çalıştıkları.</span><span class="sxs-lookup"><span data-stu-id="d73e9-108">[Reliable Sessions Overview](../../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md) Describes reliable sessions, when to use them, the different bindings that support reliable sessions, and how they work.</span></span>

<span data-ttu-id="d73e9-109">[Nasıl yapılır: Exchange ileti içinde bir güvenilir oturum](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md) yapılandırmasında belirtilen özel bir bağlama kullanarak HTTP üzerinden bir güvenilir oturum oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="d73e9-109">[How to: Exchange Messages Within a Reliable Session](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md) Describes how to create a reliable session over HTTP using a custom binding specified in the configuration.</span></span>

<span data-ttu-id="d73e9-110">[Nasıl yapılır: Güvenilir oturumlar iletilerinde güvenli](../../../../docs/framework/wcf/feature-details/how-to-secure-messages-within-reliable-sessions.md) güvenilir oturum güvenliğinin nasıl sağlanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="d73e9-110">[How to: Secure Messages within Reliable Sessions](../../../../docs/framework/wcf/feature-details/how-to-secure-messages-within-reliable-sessions.md) Describes how to secure a reliable session.</span></span>

<span data-ttu-id="d73e9-111">[Nasıl yapılır: HTTPS ile özel güvenilir oturum bağlama oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md) HTTPS üzerinden bir güvenilir oturum oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="d73e9-111">[How to: Create a Custom Reliable Session Binding with HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md) Describes how to create a reliable session over HTTPS.</span></span>

<span data-ttu-id="d73e9-112">[En iyi uygulamalar için güvenilir oturumlar](../../../../docs/framework/wcf/feature-details/best-practices-for-reliable-sessions.md) bazı güvenilir oturum kullanmayla ilişkili en iyi uygulamalar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d73e9-112">[Best Practices for Reliable Sessions](../../../../docs/framework/wcf/feature-details/best-practices-for-reliable-sessions.md) Describes some of the best practices associated with using a reliable session.</span></span>

## <a name="reference"></a><span data-ttu-id="d73e9-113">Başvuru</span><span class="sxs-lookup"><span data-stu-id="d73e9-113">Reference</span></span>

<xref:System.ServiceModel.ReliableSession>

## <a name="see-also"></a><span data-ttu-id="d73e9-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d73e9-114">See also</span></span>

- [<span data-ttu-id="d73e9-115">Kuyruklar ve Güvenilir Oturumlar</span><span class="sxs-lookup"><span data-stu-id="d73e9-115">Queues and Reliable Sessions</span></span>](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)
- [<span data-ttu-id="d73e9-116">Oturumlar, Örnek Oluşturma ve Eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="d73e9-116">Sessions, Instancing, and Concurrency</span></span>](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)

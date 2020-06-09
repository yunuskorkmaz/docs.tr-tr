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
ms.openlocfilehash: 910ad952192243c6aa8a79417ad711d8c2a4ba2e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84590546"
---
# <a name="reliable-sessions"></a><span data-ttu-id="9b693-102">Güvenilir oturumlar</span><span class="sxs-lookup"><span data-stu-id="9b693-102">Reliable Sessions</span></span>

<span data-ttu-id="9b693-103">Bu bölümde, bir Windows Communication Foundation (WCF) güvenilir oturumunun ne olduğu, ne için kullanıldığı, ne zaman ve nasıl kullanılacağı, hangi bağlama yapılandırmalarının desteklediği ve en iyi yöntemlere yönelik işaretçiler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9b693-103">This section describes what a Windows Communication Foundation (WCF) reliable session is, what it's used for, how and when to use one, what binding configurations support it, and pointers on best practices.</span></span> <span data-ttu-id="9b693-104">Aşağıdaki tabloda, bu bölümdeki temel noktalara ve ilgili konulara ilişkin ayrıntılar özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="9b693-104">The following table summarizes details about the essential points and related topics in this section.</span></span>

<span data-ttu-id="9b693-105">Güvenilir oturum WCF, uç noktalar arasında gönderilen iletilerin SOAP veya aktarım aracıları arasında aktarılmasını ve yalnızca bir kez ve isteğe bağlı olarak, gönderildikleri sırada gönderilmesini sağlayan özellikler sunar.</span><span class="sxs-lookup"><span data-stu-id="9b693-105">The reliable session WCF provides features ensuring that messages sent between endpoints are transferred across SOAP or transport intermediaries and are delivered only once and, optionally, in the same order in which they were sent.</span></span>

<span data-ttu-id="9b693-106">WCF uygulamasıyla güvenilir bir oturum kullanmak için, varsayılan olarak veya bir seçenek olarak güvenilir bir oturumu destekleyen WCF 'de sistem tarafından belirtilen bağlamalardan birini kullanın veya oturumu destekleyen kendi özel bağlamalarınızı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9b693-106">To use a reliable session with a WCF application, either use one of the system-provided bindings in WCF that support a reliable session by default or as an option, or create your own custom binding that supports the session.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="9b693-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="9b693-107">In This Section</span></span>

<span data-ttu-id="9b693-108">[Güvenilir oturumlara genel bakış](reliable-sessions-overview.md) Güvenilir oturumları, ne zaman kullanılacağını, güvenilir oturumları destekleyen farklı bağlamaları ve bunların nasıl çalıştığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="9b693-108">[Reliable Sessions Overview](reliable-sessions-overview.md) Describes reliable sessions, when to use them, the different bindings that support reliable sessions, and how they work.</span></span>

<span data-ttu-id="9b693-109">[Nasıl yapılır: güvenilir bir oturum Içindeki Iletileri değiştirme](how-to-exchange-messages-within-a-reliable-session.md) Yapılandırmada belirtilen özel bir bağlama kullanılarak HTTP üzerinden güvenilir bir oturumun nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="9b693-109">[How to: Exchange Messages Within a Reliable Session](how-to-exchange-messages-within-a-reliable-session.md) Describes how to create a reliable session over HTTP using a custom binding specified in the configuration.</span></span>

<span data-ttu-id="9b693-110">[Nasıl yapılır: güvenilir oturumlarda Iletileri güvenli hale getirme](how-to-secure-messages-within-reliable-sessions.md) Güvenilir bir oturumun nasıl güvence altına alınacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="9b693-110">[How to: Secure Messages within Reliable Sessions](how-to-secure-messages-within-reliable-sessions.md) Describes how to secure a reliable session.</span></span>

<span data-ttu-id="9b693-111">[Nasıl yapılır: https Ile özel bir güvenilir oturum bağlama oluşturma](how-to-create-a-custom-reliable-session-binding-with-https.md) HTTPS üzerinden güvenilir bir oturumun nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="9b693-111">[How to: Create a Custom Reliable Session Binding with HTTPS](how-to-create-a-custom-reliable-session-binding-with-https.md) Describes how to create a reliable session over HTTPS.</span></span>

<span data-ttu-id="9b693-112">[Güvenilir Oturumlar Için En Iyi uygulamalar](best-practices-for-reliable-sessions.md) Güvenilir bir oturum kullanımıyla ilişkili en iyi uygulamalardan bazılarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="9b693-112">[Best Practices for Reliable Sessions](best-practices-for-reliable-sessions.md) Describes some of the best practices associated with using a reliable session.</span></span>

## <a name="reference"></a><span data-ttu-id="9b693-113">Başvuru</span><span class="sxs-lookup"><span data-stu-id="9b693-113">Reference</span></span>

<xref:System.ServiceModel.ReliableSession>

## <a name="see-also"></a><span data-ttu-id="9b693-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9b693-114">See also</span></span>

- [<span data-ttu-id="9b693-115">Kuyruklar ve Güvenilir Oturumlar</span><span class="sxs-lookup"><span data-stu-id="9b693-115">Queues and Reliable Sessions</span></span>](queues-and-reliable-sessions.md)
- [<span data-ttu-id="9b693-116">Oturumlar, Örnek Oluşturma ve Eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="9b693-116">Sessions, Instancing, and Concurrency</span></span>](sessions-instancing-and-concurrency.md)

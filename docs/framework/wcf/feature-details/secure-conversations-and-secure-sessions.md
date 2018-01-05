---
title: "Güvenli İletişimler ve Güvenli Oturumlar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48cb104a-532d-40ae-aa57-769dae103fda
caps.latest.revision: "13"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: d519640c40daf248a01a19f0450f3aea8de6cc04
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="secure-conversations-and-secure-sessions"></a><span data-ttu-id="cf7de-102">Güvenli İletişimler ve Güvenli Oturumlar</span><span class="sxs-lookup"><span data-stu-id="cf7de-102">Secure Conversations and Secure Sessions</span></span>
<span data-ttu-id="cf7de-103">Bir özellik olan [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] birbirinin kimliğini doğrular ve bir şifreleme ve dijital imza işlemi sırasında kabul iki uç noktalar arasında güvenli oturumları yeteneğidir.</span><span class="sxs-lookup"><span data-stu-id="cf7de-103">A feature of [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] is the ability to establish secure sessions between two endpoints that authenticate each other and agree upon an encryption and digital signature process.</span></span> <span data-ttu-id="cf7de-104">Örneğin, hizmet uç noktası kimlik doğrulaması için bir X.509 sertifikası bağlı bir güvenlik belirteci göndermek için bir istemci uç noktası gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="cf7de-104">For example, the service endpoint might require a client endpoint to send a security token based upon an X.509 certificate for authentication.</span></span> <span data-ttu-id="cf7de-105">İstemci kimlik doğrulaması gerçekleştikten sonra hizmet uç noktası bir güvenlik bağlamı belirteci (SCT) sonra oturum içinde tüm sonraki iletileri güvenli hale getirmek için kullanılan istemciye geri döndürür.</span><span class="sxs-lookup"><span data-stu-id="cf7de-105">Once the client is authenticated, the service endpoint returns a security context token (SCT) back to the client that is then used to secure all subsequent messages within the session.</span></span> <span data-ttu-id="cf7de-106">Bu güvenli oturum oluşturma, bir simetrik anahtar SCT sahip olduğundan daha verimli olmasını iki uç noktaları arasında alınıp verilen iletileri kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="cf7de-106">Establishing this secure session enables the set of messages that are exchanged between the two endpoints to be more efficient, because the SCT has a symmetric key.</span></span> <span data-ttu-id="cf7de-107">Asimetrik anahtarlar, hangi X.509 sertifikaları dayalı olarak, simetrik ne zaman anahtarları daha önemli ölçüde daha fazla hesaplama gücüne gerektiren bir dijital imza oluşturulurken veya veri kümesi şifreleme.</span><span class="sxs-lookup"><span data-stu-id="cf7de-107">Asymmetric keys, which X.509 certificates are based upon, require significantly more computational power than symmetric keys when generating a digital signature or encrypting a set of data.</span></span>  
  
 <span data-ttu-id="cf7de-108">Önyükleme İlkesi (bölümünü 6.2.7 tanımlanan [WS-SecurityPolicy](http://go.microsoft.com/fwlink/?LinkId=99817) standart) güvenli kanal ve RST/SCT ve RSTR/SCT exchange önce istemci kimlik doğrulaması için kullanılan ileti güvenlik onayı içeriyor.</span><span class="sxs-lookup"><span data-stu-id="cf7de-108">The bootstrap policy (defined in section 6.2.7 of the [WS-SecurityPolicy](http://go.microsoft.com/fwlink/?LinkId=99817) standard) contains the message security assertions used to secure the channel and authenticate the client prior to the RST/SCT and RSTR/SCT exchange.</span></span> <span data-ttu-id="cf7de-109">Belirli [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] standart bağlamaları sahip bir `Security.Message.EstablishSecurityContext` hangi denetimlerin olup güvenli konuşma özelliği kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cf7de-109">Certain [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] standard bindings have a `Security.Message.EstablishSecurityContext` property which controls whether secure conversation is used.</span></span> <span data-ttu-id="cf7de-110">Özel bağlamalar kullanırken önyükleme iç içe güvenlik bağlama öğeleri, yoluyla belirtilir [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) yapılandırma dosyasında ya da çağırarak <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%2A> kod.</span><span class="sxs-lookup"><span data-stu-id="cf7de-110">When using custom bindings the bootstrap is indicated by nesting security binding elements, either through [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) in the configuration file, or by calling <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%2A> in code.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="cf7de-111">oturumları, bkz: [kullanarak oturumları](../../../../docs/framework/wcf/using-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="cf7de-111"> sessions, see [Using Sessions](../../../../docs/framework/wcf/using-sessions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf7de-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cf7de-112">See Also</span></span>  
 [<span data-ttu-id="cf7de-113">Oturumlar, Örnek Oluşturma ve Eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="cf7de-113">Sessions, Instancing, and Concurrency</span></span>](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
 [<span data-ttu-id="cf7de-114">Nasıl yapılır: Oturum Gerektiren Bir Hizmet Oluşturma</span><span class="sxs-lookup"><span data-stu-id="cf7de-114">How to: Create a Service That Requires Sessions</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)

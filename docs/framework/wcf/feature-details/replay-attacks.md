---
title: Yeniden Yürütme Saldırıları
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7a17e040-93cd-4432-81b9-9f62fec78c8f
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4e827c51378b9f75835b9b98280b4995d2cae2fc
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="replay-attacks"></a><span data-ttu-id="99c39-102">Yeniden Yürütme Saldırıları</span><span class="sxs-lookup"><span data-stu-id="99c39-102">Replay Attacks</span></span>
<span data-ttu-id="99c39-103">A *tekrarlama saldırı* bir saldırgan, iki taraf arasında ileti akışı kopyalar ve bir veya daha fazla tarafların akışa başlayarak yeniden oynatılır oluşur.</span><span class="sxs-lookup"><span data-stu-id="99c39-103">A *replay attack* occurs when an attacker copies a stream of messages between two parties and replays the stream to one or more of the parties.</span></span> <span data-ttu-id="99c39-104">Azaltıldığından sürece, bilgisayarlar saldırı tabi akış yasal iletileri, bir öğenin yedekli siparişleri gibi hatalı sonuçları aralığında kaynaklanan olarak işler.</span><span class="sxs-lookup"><span data-stu-id="99c39-104">Unless mitigated, the computers subject to the attack process the stream as legitimate messages, resulting in a range of bad consequences, such as redundant orders of an item.</span></span>  
  
## <a name="bindings-may-be-subject-to-reflection-attacks"></a><span data-ttu-id="99c39-105">Yansıma saldırılarına maruz bağlamaları olabilir</span><span class="sxs-lookup"><span data-stu-id="99c39-105">Bindings May Be Subject to Reflection Attacks</span></span>  
 <span data-ttu-id="99c39-106">*Yansıma saldırıları* alıcısı yanıt olarak geldiği gibi iletileri gönderen dön yürütmelerini demektir.</span><span class="sxs-lookup"><span data-stu-id="99c39-106">*Reflection attacks* are replays of messages back to a sender as if they came from the receiver as the reply.</span></span> <span data-ttu-id="99c39-107">Standart *yeniden yürütme algılaması* içinde [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] mekanizması otomatik olarak işlemiyor bu.</span><span class="sxs-lookup"><span data-stu-id="99c39-107">The standard *replay detection* in the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] mechanism does not automatically handle this.</span></span>  
  
 <span data-ttu-id="99c39-108">Yansıma saldırıları için varsayılan olarak azaltıldığından [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet modeli imzalı ileti kimliği istek iletilerini ekler ve bir imzalı bekliyor `relates-to` üstbilgisi yanıt iletileri.</span><span class="sxs-lookup"><span data-stu-id="99c39-108">Reflection attacks are mitigated by default because the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service model adds a signed message ID to request messages and expects a signed `relates-to` header on response messages.</span></span> <span data-ttu-id="99c39-109">Sonuç olarak, isteğine yanıt olarak yeniden olamaz.</span><span class="sxs-lookup"><span data-stu-id="99c39-109">Consequently, the request message cannot be replayed as a response.</span></span> <span data-ttu-id="99c39-110">Güvenli güvenilir ileti (RM) senaryolarında yansıma saldırıları çünkü azaltıldığından:</span><span class="sxs-lookup"><span data-stu-id="99c39-110">In secure reliable message (RM) scenarios, reflection attacks are mitigated because:</span></span>  
  
-   <span data-ttu-id="99c39-111">Oluşturma sırası ve Oluşturma sırası yanıt iletisi şemaları farklıdır.</span><span class="sxs-lookup"><span data-stu-id="99c39-111">The create sequence and create sequence response message schemas are different.</span></span>  
  
-   <span data-ttu-id="99c39-112">İstemci bu türden iletilere anlayamıyor çünkü tek yönlü sıraları için istemci gönderir sırası iletilerinin yeniden yeniden yürütülmesi olamaz.</span><span class="sxs-lookup"><span data-stu-id="99c39-112">For simplex sequences, sequence messages the client sends cannot be replayed back to it because the client cannot understand such messages.</span></span>  
  
-   <span data-ttu-id="99c39-113">Çift yönlü sıraları için iki sırası kimliklerinin benzersiz olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="99c39-113">For duplex sequences, the two sequence IDs must be unique.</span></span> <span data-ttu-id="99c39-114">Bu nedenle, bir giden sırası iletisi (tüm dizisi üstbilgi ve gövdelerini, çok imzalanmış) geri gelen sırası iletisi yeniden olamaz.</span><span class="sxs-lookup"><span data-stu-id="99c39-114">Thus, an outgoing sequence message cannot be replayed back as an incoming sequence message (all sequence headers and bodies are signed, too).</span></span>  
  
 <span data-ttu-id="99c39-115">Yansıma saldırılarına yalnızca bağlamaları WS adresleme olmadan olanlardır: WS adresleme-devre dışı olması ve simetrik anahtar tabanlı güvenlik kullanan özel bağlamalar.</span><span class="sxs-lookup"><span data-stu-id="99c39-115">The only bindings that are susceptible to reflection attacks are those without WS-Addressing: custom bindings that have WS-Addressing disabled and use the symmetric key-based security.</span></span> <span data-ttu-id="99c39-116"><xref:System.ServiceModel.BasicHttpBinding> Kullanılmıyor WS adresleme varsayılan olarak yapar, ancak bunu simetrik anahtar tabanlı güvenlik, bu saldırıya karşı savunmasız izin veren şekilde kullanmıyor.</span><span class="sxs-lookup"><span data-stu-id="99c39-116">The <xref:System.ServiceModel.BasicHttpBinding> does not use WS-Addressing by default, but it does not use symmetric key-based security in a way that allows it to be vulnerable to this attack.</span></span>  
  
 <span data-ttu-id="99c39-117">Özel bağlamalar azaltma güvenlik bağlamı kurmak değil veya WS adresleme üstbilgileri gerektirecek şekilde kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="99c39-117">The mitigation for custom bindings is to not establish security context or to require WS-Addressing headers.</span></span>  
  
## <a name="web-farm-attacker-replays-request-to-multiple-nodes"></a><span data-ttu-id="99c39-118">Web grubu: Saldırgan yürütmelerini isteği birden çok düğüme</span><span class="sxs-lookup"><span data-stu-id="99c39-118">Web Farm: Attacker Replays Request to Multiple Nodes</span></span>  
 <span data-ttu-id="99c39-119">Bir istemci bir Web grubuna uygulanan bir hizmet kullanır.</span><span class="sxs-lookup"><span data-stu-id="99c39-119">A client uses a service that is implemented on a Web farm.</span></span> <span data-ttu-id="99c39-120">Bir saldırgan gruptaki başka bir düğüme gruptaki bir düğüm için gönderilen bir istek başlayarak yeniden oynatılır.</span><span class="sxs-lookup"><span data-stu-id="99c39-120">An attacker replays a request that was sent to one node in the farm to another node in the farm.</span></span> <span data-ttu-id="99c39-121">Bir hizmeti yeniden başlatılırsa, ayrıca, tekrar yürütme önbelleğine, isteği yeniden göndermek bir saldırgan izin vererek temizlenir.</span><span class="sxs-lookup"><span data-stu-id="99c39-121">In addition, if a service is restarted, the replay cache is flushed, allowing an attacker to replay the request.</span></span> <span data-ttu-id="99c39-122">(Önbellek kullanılan, daha önce görülen ileti imzası değerler içeriyor ve bu imzaların yalnızca bir kez kullanılabilmesi için yürütmelerini önler.</span><span class="sxs-lookup"><span data-stu-id="99c39-122">(The cache contains used, previously seen message signature values and prevents replays so those signatures can be used only once.</span></span> <span data-ttu-id="99c39-123">Yeniden yürütme önbellekleri bir Web grubu arasında paylaşılmaz.)</span><span class="sxs-lookup"><span data-stu-id="99c39-123">Replay caches are not shared across a Web farm.)</span></span>  
  
 <span data-ttu-id="99c39-124">Azaltıcı Etkenler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="99c39-124">Mitigations include:</span></span>  
  
-   <span data-ttu-id="99c39-125">İleti modu güvenlik durum bilgisi olan güvenlik bağlamı belirteçleri (ile veya etkin güvenli konuşma olmadan) kullanın.</span><span class="sxs-lookup"><span data-stu-id="99c39-125">Use message mode security with stateful security context tokens (with or without secure conversation enabled).</span></span> <span data-ttu-id="99c39-126">Daha fazla bilgi için bkz: [nasıl yapılır: güvenli oturum açmak için bir güvenlik bağlamı belirteci oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span><span class="sxs-lookup"><span data-stu-id="99c39-126">For more information, see [How to: Create a Security Context Token for a Secure Session](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span></span>  
  
-   <span data-ttu-id="99c39-127">Hizmetini aktarım düzeyinde güvenlik kullanacak şekilde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="99c39-127">Configure the service to use transport-level security.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99c39-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="99c39-128">See Also</span></span>  
 [<span data-ttu-id="99c39-129">Güvenlik Konuları</span><span class="sxs-lookup"><span data-stu-id="99c39-129">Security Considerations</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [<span data-ttu-id="99c39-130">Bilgilerin Açığa Çıkması</span><span class="sxs-lookup"><span data-stu-id="99c39-130">Information Disclosure</span></span>](../../../../docs/framework/wcf/feature-details/information-disclosure.md)  
 [<span data-ttu-id="99c39-131">Ayrıcalıkların Yükseltilmesi</span><span class="sxs-lookup"><span data-stu-id="99c39-131">Elevation of Privilege</span></span>](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)  
 [<span data-ttu-id="99c39-132">Hizmet Reddi</span><span class="sxs-lookup"><span data-stu-id="99c39-132">Denial of Service</span></span>](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 [<span data-ttu-id="99c39-133">İzinsiz Değişiklik</span><span class="sxs-lookup"><span data-stu-id="99c39-133">Tampering</span></span>](../../../../docs/framework/wcf/feature-details/tampering.md)  
 [<span data-ttu-id="99c39-134">Desteklenmeyen Senaryolar</span><span class="sxs-lookup"><span data-stu-id="99c39-134">Unsupported Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)

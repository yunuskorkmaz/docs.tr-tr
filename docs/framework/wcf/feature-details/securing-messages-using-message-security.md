---
description: 'Hakkında daha fazla bilgi edinin: Ileti güvenliği kullanarak Iletilerin güvenliğini sağlama'
title: İleti Güveliği Kullanarak İletileri Güvenli Hale Getirme
ms.date: 03/30/2017
ms.assetid: a17ebe67-836b-4c52-9a81-2c3d58e225ee
ms.openlocfilehash: 006caa232ef0ae92dfd27b03d7a20af3f4174c81
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99733066"
---
# <a name="securing-messages-using-message-security"></a><span data-ttu-id="8979e-103">İleti Güveliği Kullanarak İletileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="8979e-103">Securing Messages Using Message Security</span></span>

<span data-ttu-id="8979e-104">Bu bölümde kullanırken WCF ileti güvenliği ele alınmaktadır <xref:System.ServiceModel.NetMsmqBinding> .</span><span class="sxs-lookup"><span data-stu-id="8979e-104">This section discusses WCF message security when using <xref:System.ServiceModel.NetMsmqBinding>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8979e-105">Bu konuyu okumadan önce [güvenlik kavramlarını](security-concepts.md)okumanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="8979e-105">Before reading through this topic, it is recommended that you read [Security Concepts](security-concepts.md).</span></span>  
  
 <span data-ttu-id="8979e-106">Aşağıdaki çizimde, WCF kullanılarak sıraya alınmış iletişimin kavramsal bir modeli verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8979e-106">The following illustration provides a conceptual model of queued communication using WCF.</span></span> <span data-ttu-id="8979e-107">Bu çizim ve terminoloji açıklamak için kullanılır</span><span class="sxs-lookup"><span data-stu-id="8979e-107">This illustration and terminology are used to explain</span></span>  
  
 <span data-ttu-id="8979e-108">taşıma güvenlik kavramları.</span><span class="sxs-lookup"><span data-stu-id="8979e-108">transport security concepts.</span></span>  
  
 <span data-ttu-id="8979e-109">![Kuyruğa alınmış uygulama diyagramı](media/distributed-queue-figure.jpg "Dağıtılmış kuyruk-şekil")</span><span class="sxs-lookup"><span data-stu-id="8979e-109">![Queued Application Diagram](media/distributed-queue-figure.jpg "Distributed-Queue-Figure")</span></span>  
  
 <span data-ttu-id="8979e-110">WCF kullanarak sıraya alınan iletileri gönderirken WCF iletisi Message Queuing (MSMQ) iletisinin bir gövdesi olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="8979e-110">When sending queued messages using WCF, the WCF message is attached as a body of the Message Queuing (MSMQ) message.</span></span> <span data-ttu-id="8979e-111">Taşıma güvenliği tüm MSMQ iletisinin güvenliğini sağlarken, ileti (veya SOAP) güvenliği yalnızca MSMQ iletisinin gövdesine güvenlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="8979e-111">While transport security secures the entire MSMQ message, message (or SOAP) security only secures the body of the MSMQ message.</span></span>  
  
 <span data-ttu-id="8979e-112">İleti güvenliği kavramı, istemcinin hedef sıranın iletisini güvenlik altına aldığı aktarım güvenliği aksine, istemci alıcı uygulama (hizmet) için iletiyi güvenlik altına almadır.</span><span class="sxs-lookup"><span data-stu-id="8979e-112">The key concept of message security is that the client secures the message for the receiving application (service), unlike transport security where the client secures the message for the Target Queue.</span></span> <span data-ttu-id="8979e-113">Bu nedenle, MSMQ ileti güvenliği kullanılarak WCF iletisini güvenli hale getirirken hiçbir bölüm vermez.</span><span class="sxs-lookup"><span data-stu-id="8979e-113">As such, MSMQ plays no part when securing the WCF message using message security.</span></span>  
  
 <span data-ttu-id="8979e-114">WCF ileti güvenliği, bir sertifika veya Kerberos protokolü gibi mevcut güvenlik altyapılarıyla tümleştirilen WCF iletisine güvenlik üstbilgileri ekler.</span><span class="sxs-lookup"><span data-stu-id="8979e-114">WCF message security adds security headers to the WCF message that integrate with existing security infrastructures, such as a certificate or the Kerberos protocol.</span></span>  
  
## <a name="message-credential-type"></a><span data-ttu-id="8979e-115">İleti kimlik bilgisi türü</span><span class="sxs-lookup"><span data-stu-id="8979e-115">Message Credential Type</span></span>  

 <span data-ttu-id="8979e-116">Hizmet ve istemci, ileti güvenliğini kullanarak birbirlerinin kimliğini doğrulamak için kimlik bilgilerini sunabilir.</span><span class="sxs-lookup"><span data-stu-id="8979e-116">Using message security, the service and client can present credentials to authenticate each another.</span></span> <span data-ttu-id="8979e-117">Modu veya olarak ayarlayarak ileti güvenliği seçebilirsiniz <xref:System.ServiceModel.NetMsmqBinding.Security%2A> `Message` `Both` (yani, hem aktarım güvenliği hem de ileti güvenliği kullanın).</span><span class="sxs-lookup"><span data-stu-id="8979e-117">You can select message security by setting the <xref:System.ServiceModel.NetMsmqBinding.Security%2A> mode to `Message` or `Both` (that is, use both transport security and message security).</span></span>  
  
 <span data-ttu-id="8979e-118">Hizmet, <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> istemcinin kimliğini doğrulamak için kullanılan kimlik bilgilerini incelemek için özelliğini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="8979e-118">The service can use the <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> property to inspect the credential used to authenticate the client.</span></span> <span data-ttu-id="8979e-119">Bu, hizmetin uygulamayı seçtiği daha fazla yetkilendirme denetimi için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8979e-119">This can also be used for further authorization checks that the service chooses to implement.</span></span>  
  
 <span data-ttu-id="8979e-120">Bu bölümde farklı kimlik bilgisi türleri ve kuyrukların nasıl kullanılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8979e-120">This section explains the different credential types and how to use them with queues.</span></span>  
  
### <a name="certificate"></a><span data-ttu-id="8979e-121">Sertifika</span><span class="sxs-lookup"><span data-stu-id="8979e-121">Certificate</span></span>  

 <span data-ttu-id="8979e-122">Sertifika kimlik bilgileri türü bir X. 509.440 sertifikası kullanarak hizmeti ve istemciyi belirler.</span><span class="sxs-lookup"><span data-stu-id="8979e-122">The certificate credential type uses an X.509 certificate to identify the service and the client.</span></span>  
  
 <span data-ttu-id="8979e-123">Tipik bir senaryoda, istemci ve hizmet güvenilen bir sertifika yetkilisi tarafından geçerli bir sertifika verilir.</span><span class="sxs-lookup"><span data-stu-id="8979e-123">In a typical scenario, the client and the service are issued a valid certificate by a trusted certification authority.</span></span> <span data-ttu-id="8979e-124">Sonra bağlantı oluşturulur, istemci hizmete güvenip güvenmeyeceğine karar vermek için hizmetin sertifikasını kullanarak hizmetin geçerliliğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="8979e-124">Then the connection is established, the client authenticates the validity of the service using the service's certificate to decide whether it can trust the service.</span></span> <span data-ttu-id="8979e-125">Benzer şekilde, hizmet istemci güvenini doğrulamak için istemcinin sertifikasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="8979e-125">Similarly, the service uses the client's certificate to validate the client trust.</span></span>  
  
 <span data-ttu-id="8979e-126">Kuyrukların bağlantısı kesilen doğası gereği, istemci ve hizmet aynı anda çevrimiçi olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="8979e-126">Given the disconnected nature of queues, the client and the service may not be online at the same time.</span></span> <span data-ttu-id="8979e-127">Bu nedenle, istemci ve hizmetin sertifikaları bant dışı olarak alışverişi gerekir.</span><span class="sxs-lookup"><span data-stu-id="8979e-127">As such, the client and service have to exchange certificates out-of-band.</span></span> <span data-ttu-id="8979e-128">Özellikle, güvenilen depodaki hizmetin sertifikasını (bir sertifika yetkilisine zincirlenebilir) tutan istemci sanallaştırılan istemci, doğru hizmetle iletişim kurduğu güvenmelidir.</span><span class="sxs-lookup"><span data-stu-id="8979e-128">In particular, the client, by virtue of holding the service's certificate (which can be chained to a certification authority) in its trusted store, must trust that it is communicating with the correct service.</span></span> <span data-ttu-id="8979e-129">İstemcinin kimliğini doğrulamak için hizmet, istemciyle birlikte gelen X. 509.440 sertifikasını kullanarak istemcinin orijinalliğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="8979e-129">For authenticating the client, the service uses the X.509 certificate attached with the message to matches it with the certificate in its store to verify the authenticity of the client.</span></span> <span data-ttu-id="8979e-130">Yeniden, sertifikanın bir sertifika yetkilisine zincirleme olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8979e-130">Again, the certificate must be chained to a certification authority.</span></span>  
  
 <span data-ttu-id="8979e-131">Windows çalıştıran bir bilgisayarda, sertifikalar çeşitli türlerde depolarda tutulur.</span><span class="sxs-lookup"><span data-stu-id="8979e-131">On a computer running Windows, certificates are held in several kinds of stores.</span></span> <span data-ttu-id="8979e-132">Farklı mağazalar hakkında daha fazla bilgi için bkz. [sertifika depoları](/previous-versions/windows/it-pro/windows-server-2003/cc757138(v=ws.10)).</span><span class="sxs-lookup"><span data-stu-id="8979e-132">For more information about the different stores, see [Certificate stores](/previous-versions/windows/it-pro/windows-server-2003/cc757138(v=ws.10)).</span></span>  
  
### <a name="windows"></a><span data-ttu-id="8979e-133">Windows</span><span class="sxs-lookup"><span data-stu-id="8979e-133">Windows</span></span>  

 <span data-ttu-id="8979e-134">Windows ileti kimlik bilgisi türü Kerberos protokolünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="8979e-134">Windows message credential type uses the Kerberos protocol.</span></span>  
  
 <span data-ttu-id="8979e-135">Kerberos protokolü, bir etki alanındaki kullanıcıların kimliğini doğrulayan ve kimliği doğrulanmış kullanıcıların bir etki alanındaki diğer varlıklarla güvenli bağlamlar kurmasını sağlayan bir güvenlik mekanizmasıdır.</span><span class="sxs-lookup"><span data-stu-id="8979e-135">The Kerberos protocol is a security mechanism that authenticates users on a domain and allows the authenticated users to establish secure contexts with other entities on a domain.</span></span>  
  
 <span data-ttu-id="8979e-136">Sıraya alınan iletişim için Kerberos protokolünü kullanmayla ilgili sorun, Anahtar Dağıtım Merkezi (KDC) tarafından dağıtılan istemci kimliğini içeren anahtarların görece kısa ömürlü olduğundan emin olur.</span><span class="sxs-lookup"><span data-stu-id="8979e-136">The problem with using the Kerberos protocol for queued communication is that the tickets that contain client identity that the Key Distribution Center (KDC) distributes are relatively short-lived.</span></span> <span data-ttu-id="8979e-137">Bir *yaşam süresi* , Bilet geçerliliğini gösteren Kerberos bileti ile ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="8979e-137">A *lifetime* is associated with the Kerberos ticket that indicates the validity of the ticket.</span></span> <span data-ttu-id="8979e-138">Bu nedenle, yüksek gecikme süresi verilen, belirtecin istemcinin kimliğini doğrulayan hizmet için hala geçerli olduğundan emin olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8979e-138">As such, given high latency, you cannot be sure that the token is still valid for the service that authenticates the client.</span></span>  
  
 <span data-ttu-id="8979e-139">Bu kimlik bilgisi türü kullanılırken hizmetin HIZMET hesabı altında çalışıyor olması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8979e-139">Note that when using this credential type, the service must be running under the SERVICE account.</span></span>  
  
 <span data-ttu-id="8979e-140">İleti kimlik bilgisi seçerken Kerberos protokolü varsayılan olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8979e-140">The Kerberos protocol is used by default when choosing message credential.</span></span>
  
### <a name="username-password"></a><span data-ttu-id="8979e-141">Kullanıcı adı parolası</span><span class="sxs-lookup"><span data-stu-id="8979e-141">Username Password</span></span>  

 <span data-ttu-id="8979e-142">Bu özelliği kullanarak istemci, iletinin güvenlik üstbilgisinde bir Kullanıcı adı parolası kullanarak sunucuda kimlik doğrulaması yapabilir.</span><span class="sxs-lookup"><span data-stu-id="8979e-142">Using this property, the client can authenticate to the server using a username password in the security header of the message.</span></span>  
  
### <a name="issuedtoken"></a><span data-ttu-id="8979e-143">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="8979e-143">IssuedToken</span></span>  

 <span data-ttu-id="8979e-144">İstemci, istemcinin kimliğini doğrulamak üzere hizmetin iletisine iliştirilebilecek bir belirteç vermek için güvenlik belirteci hizmetini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="8979e-144">The client can use the security token service to issue a token that can then be attached to the message for the service to authenticate the client.</span></span>  
  
## <a name="using-transport-and-message-security"></a><span data-ttu-id="8979e-145">Aktarım ve Ileti güvenliğini kullanma</span><span class="sxs-lookup"><span data-stu-id="8979e-145">Using Transport and Message Security</span></span>  

 <span data-ttu-id="8979e-146">Hem aktarım güvenliği hem de ileti güvenliği kullanılırken, iletiyi hem aktarımda hem de SOAP ileti düzeyinde güvenli hale getirmek için kullanılan sertifikanın aynı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8979e-146">When using both transport security and message security, the certificate used to secure the message both at the transport and the SOAP message level must be the same.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8979e-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8979e-147">See also</span></span>

- [<span data-ttu-id="8979e-148">Taşıma Güveliği Kullanarak İletileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="8979e-148">Securing Messages Using Transport Security</span></span>](securing-messages-using-transport-security.md)
- [<span data-ttu-id="8979e-149">İleti Kuyruğa Alma ile İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="8979e-149">Message Security over Message Queuing</span></span>](../samples/message-security-over-message-queuing.md)
- [<span data-ttu-id="8979e-150">Güvenlik Kavramları</span><span class="sxs-lookup"><span data-stu-id="8979e-150">Security Concepts</span></span>](security-concepts.md)
- [<span data-ttu-id="8979e-151">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="8979e-151">Securing Services and Clients</span></span>](securing-services-and-clients.md)

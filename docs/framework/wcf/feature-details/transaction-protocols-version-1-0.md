---
title: İşlem Protokolleri sürüm 1.0
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 034679af-0002-402e-98a8-ef73dcd71bb6
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 60867daa7b8519f745c37371604807c51aa1cbb9
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="transaction-protocols-version-10"></a><span data-ttu-id="deb93-102">İşlem Protokolleri sürüm 1.0</span><span class="sxs-lookup"><span data-stu-id="deb93-102">Transaction Protocols version 1.0</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="deb93-103"> Sürüm 1, sürüm 1.0 WS-Atomic işlemleri ve Web Hizmetleri koordinasyonu kurallarının uygular.</span><span class="sxs-lookup"><span data-stu-id="deb93-103"> version 1 implements version 1.0 of the WS-Atomic Transaction and WS-Coordination protocols.</span></span> <span data-ttu-id="deb93-104">Sürüm 1.1 hakkında daha fazla bilgi için bkz: [işlem protokolleri](../../../../docs/framework/wcf/feature-details/transaction-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="deb93-104">For more information about version 1.1, see [Transaction Protocols](../../../../docs/framework/wcf/feature-details/transaction-protocols.md).</span></span>  
  
|<span data-ttu-id="deb93-105">Belirtim/belgesi</span><span class="sxs-lookup"><span data-stu-id="deb93-105">Specification/Document</span></span>|<span data-ttu-id="deb93-106">Bağlantı</span><span class="sxs-lookup"><span data-stu-id="deb93-106">Link</span></span>|  
|-----------------------------|----------|  
|<span data-ttu-id="deb93-107">WS-düzenleme</span><span class="sxs-lookup"><span data-stu-id="deb93-107">WS-Coordination</span></span>|http://msdn.microsoft.com/ws/2005/08/ws-coordination/|  
|<span data-ttu-id="deb93-108">WS-AtomicTransaction</span><span class="sxs-lookup"><span data-stu-id="deb93-108">WS-AtomicTransaction</span></span>|http://msdn.microsoft.com/ws/2005/08/ws-atomictransaction/|  
  
 <span data-ttu-id="deb93-109">Bu protokol belirtimleri üzerinde birlikte çalışabilirlik iki düzeyde gereklidir: uygulamalar arasında arasında işlem yöneticileri (Aşağıdaki şekle bakın).</span><span class="sxs-lookup"><span data-stu-id="deb93-109">Interoperability on these protocol specifications is required at two levels: between applications and between transaction managers (see the following figure).</span></span> <span data-ttu-id="deb93-110">İletisi ve ileti formatları için her iki birlikte çalışabilirlik düzeylerini exchange harika ayrıntılı özellikleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="deb93-110">Specifications describe in great detail the message formats and message exchange for both interoperability levels.</span></span> <span data-ttu-id="deb93-111">Normal uygulama exchange için yaptığınız gibi belirli güvenlik, güvenilirlik ve kodlamaları uygulama uygulaması exchange için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="deb93-111">Certain security, reliability, and encodings for application-to-application exchange apply as they do for regular application exchange.</span></span> <span data-ttu-id="deb93-112">Ancak, kullanıcı tarafından genellikle yapılandırılmadığı için işlem yöneticileri başarılı işlerliği belirli bağlama anlaşmasında gerektirir.</span><span class="sxs-lookup"><span data-stu-id="deb93-112">However, successful interoperability between transaction managers requires agreement on the particular binding, because it is usually not configured by the user.</span></span>  
  
 <span data-ttu-id="deb93-113">Bu konu, WS-Atomic işlem (WS-AT) belirtimi bileşimi ile güvenliği açıklar ve işlem yöneticileri arasındaki iletişim için kullanılan güvenli bağlama açıklar.</span><span class="sxs-lookup"><span data-stu-id="deb93-113">This topic describes a composition of the WS-Atomic Transaction (WS-AT) specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="deb93-114">Bu belgede açıklanan yaklaşım başarıyla WS-AT ve Web Hizmetleri koordinasyonu diğer uygulamaları ile test edilmiştir IBM, IONA, Sun Microsystems ve diğerleri de dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="deb93-114">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination including IBM, IONA, Sun Microsystems, and others.</span></span>  
  
 <span data-ttu-id="deb93-115">Aşağıdaki şekil, İşlem Yöneticisi 1 ve işlem yöneticisi 2, iki işlem yöneticileri ve uygulama 1 ve uygulama 2 iki uygulama arasındaki birlikte çalışabilirlik gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="deb93-115">The following figure depicts the interoperability between two transaction managers, Transaction Manager 1 and Transaction Manager 2, and two applications, Application 1 and Application 2.</span></span>  
  
 <span data-ttu-id="deb93-116">![İşlem protokolleri](../../../../docs/framework/wcf/feature-details/media/transactionmanagers.gif "TransactionManagers")</span><span class="sxs-lookup"><span data-stu-id="deb93-116">![Transaction Protocols](../../../../docs/framework/wcf/feature-details/media/transactionmanagers.gif "TransactionManagers")</span></span>  
  
 <span data-ttu-id="deb93-117">Bir başlatıcı (ı) ve bir katılımcı (P) tipik bir WS-düzenleme/WS-Atomic işlem senaryoyu göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="deb93-117">Consider a typical WS-Coordination/WS-Atomic Transaction scenario with one Initiator (I) and one Participant (P).</span></span> <span data-ttu-id="deb93-118">Hem Başlatıcı hem de katılımcı olan işlem yöneticileri (ITM ve PTM, sırasıyla).</span><span class="sxs-lookup"><span data-stu-id="deb93-118">Both Initiator and Participant have Transaction Managers, (ITM and PTM, respectively).</span></span> <span data-ttu-id="deb93-119">İki aşamalı yürütme için bu konudaki 2PC olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="deb93-119">Two-phase commit is referred to as 2PC in this topic.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="deb93-120">1. CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="deb93-120">1. CreateCoordinationContext</span></span>|<span data-ttu-id="deb93-121">12. Uygulama ileti yanıtı</span><span class="sxs-lookup"><span data-stu-id="deb93-121">12. Application Message Response</span></span>|  
|<span data-ttu-id="deb93-122">2. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="deb93-122">2. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="deb93-123">13. Yürütme (tamamlanma)</span><span class="sxs-lookup"><span data-stu-id="deb93-123">13. Commit (Completion)</span></span>|  
|<span data-ttu-id="deb93-124">3. YAZMAÇ (tamamlanma)</span><span class="sxs-lookup"><span data-stu-id="deb93-124">3. Register (Completion)</span></span>|<span data-ttu-id="deb93-125">14. (2PC) hazırlama</span><span class="sxs-lookup"><span data-stu-id="deb93-125">14. Prepare (2PC)</span></span>|  
|<span data-ttu-id="deb93-126">4. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="deb93-126">4. RegisterResponse</span></span>|<span data-ttu-id="deb93-127">15. (2PC) hazırlama</span><span class="sxs-lookup"><span data-stu-id="deb93-127">15. Prepare (2PC)</span></span>|  
|<span data-ttu-id="deb93-128">5. Uygulama iletisi</span><span class="sxs-lookup"><span data-stu-id="deb93-128">5. Application Message</span></span>|<span data-ttu-id="deb93-129">16. Hazırlanan (2PC)</span><span class="sxs-lookup"><span data-stu-id="deb93-129">16. Prepared (2PC)</span></span>|  
|<span data-ttu-id="deb93-130">6. Bağlamına sahip CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="deb93-130">6. CreateCoordinationContext with Context</span></span>|<span data-ttu-id="deb93-131">17. Hazırlanan (2PC)</span><span class="sxs-lookup"><span data-stu-id="deb93-131">17. Prepared (2PC)</span></span>|  
|<span data-ttu-id="deb93-132">7. YAZMAÇ (dayanıklı)</span><span class="sxs-lookup"><span data-stu-id="deb93-132">7. Register (Durable)</span></span>|<span data-ttu-id="deb93-133">18. Kaydedilmiş (tamamlanma)</span><span class="sxs-lookup"><span data-stu-id="deb93-133">18. Committed (Completion)</span></span>|  
|<span data-ttu-id="deb93-134">8. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="deb93-134">8. RegisterResponse</span></span>|<span data-ttu-id="deb93-135">19. Kayıt (2PC)</span><span class="sxs-lookup"><span data-stu-id="deb93-135">19. Commit (2PC)</span></span>|  
|<span data-ttu-id="deb93-136">9. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="deb93-136">9. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="deb93-137">20. Kayıt (2PC)</span><span class="sxs-lookup"><span data-stu-id="deb93-137">20. Commit (2PC)</span></span>|  
|<span data-ttu-id="deb93-138">10. YAZMAÇ (dayanıklı)</span><span class="sxs-lookup"><span data-stu-id="deb93-138">10. Register (Durable)</span></span>|<span data-ttu-id="deb93-139">21. Kaydedilmiş (2PC)</span><span class="sxs-lookup"><span data-stu-id="deb93-139">21. Committed (2PC)</span></span>|  
|<span data-ttu-id="deb93-140">11. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="deb93-140">11. RegisterResponse</span></span>|<span data-ttu-id="deb93-141">22. Kaydedilmiş (2PC)</span><span class="sxs-lookup"><span data-stu-id="deb93-141">22. Committed (2PC)</span></span>|  
  
 <span data-ttu-id="deb93-142">Bu belge WS-AtomicTransaction belirtiminin bir birleşim ile güvenliği açıklar ve işlem yöneticileri arasındaki iletişim için kullanılan güvenli bağlama açıklar.</span><span class="sxs-lookup"><span data-stu-id="deb93-142">This document describes a composition of the WS-AtomicTransaction specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="deb93-143">Bu belgede açıklanan yaklaşım başarıyla WS-AT ve Web Hizmetleri koordinasyonu diğer uygulamaları ile test edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="deb93-143">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination.</span></span>  
  
 <span data-ttu-id="deb93-144">Şekil ve tabloda güvenlik görüş iletilerden dört sınıflarını gösterir:</span><span class="sxs-lookup"><span data-stu-id="deb93-144">The figure and table illustrate four classes of messages from the viewpoint of security:</span></span>  
  
-   <span data-ttu-id="deb93-145">Etkinleştirme iletileri (CreateCoordinationContext ve CreateCoordinationContextResponse).</span><span class="sxs-lookup"><span data-stu-id="deb93-145">Activation messages (CreateCoordinationContext and CreateCoordinationContextResponse).</span></span>  
  
-   <span data-ttu-id="deb93-146">Kayıt iletiler (kaydetme ve RegisterResponse)</span><span class="sxs-lookup"><span data-stu-id="deb93-146">Registration messages (Register and RegisterResponse)</span></span>  
  
-   <span data-ttu-id="deb93-147">Protokol iletileri (hazırlama, geri alma, kaydetme, iptal edildi vb.).</span><span class="sxs-lookup"><span data-stu-id="deb93-147">Protocol messages (Prepare, Rollback, Commit, Aborted, and so on).</span></span>  
  
-   <span data-ttu-id="deb93-148">Uygulama iletileri.</span><span class="sxs-lookup"><span data-stu-id="deb93-148">Application messages.</span></span>  
  
 <span data-ttu-id="deb93-149">İlk üç ileti sınıfları işlem yöneticisi iletileri kabul edilir ve bağlama yapılandırmalarını "Uygulama ileti değişimi" Bu konunun ilerleyen bölümlerinde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="deb93-149">The first three message classes are considered Transaction Manager messages and their binding configuration is described in the "Application Message Exchange" later in this topic.</span></span> <span data-ttu-id="deb93-150">İletinin dördüncü sınıfını uygulamaya iletileri ve bu konunun devamındaki "İletisi örnekler" bölümünde açıklanan.</span><span class="sxs-lookup"><span data-stu-id="deb93-150">The fourth class of message is application to application messages and is described in the "Message Examples" section later in this topic.</span></span> <span data-ttu-id="deb93-151">Bu bölümde tarafından bu sınıfların her biri için kullanılan protokolü bağlamaları açıklanmaktadır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="deb93-151">This section describes the protocol bindings used for each of these classes by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 <span data-ttu-id="deb93-152">Aşağıdaki XML ad alanları ve ilişkili önekleri bu belge boyunca kullanılır.</span><span class="sxs-lookup"><span data-stu-id="deb93-152">The following XML Namespaces and associated prefixes are used throughout this document.</span></span>  
  
|<span data-ttu-id="deb93-153">önek</span><span class="sxs-lookup"><span data-stu-id="deb93-153">Prefix</span></span>|<span data-ttu-id="deb93-154">Namespace URI</span><span class="sxs-lookup"><span data-stu-id="deb93-154">Namespace URI</span></span>|  
|------------|-------------------|  
|<span data-ttu-id="deb93-155">s11</span><span class="sxs-lookup"><span data-stu-id="deb93-155">s11</span></span>|http://schemas.xmlsoap.org/soap/envelope|  
|<span data-ttu-id="deb93-156">wsa</span><span class="sxs-lookup"><span data-stu-id="deb93-156">wsa</span></span>|http://www.w3.org/2004/08/addressing|  
|<span data-ttu-id="deb93-157">wscoor</span><span class="sxs-lookup"><span data-stu-id="deb93-157">wscoor</span></span>|http://schemas.xmlsoap.org/ws/2004/10/wscoor|  
|<span data-ttu-id="deb93-158">WSAT</span><span class="sxs-lookup"><span data-stu-id="deb93-158">wsat</span></span>|http://schemas.xmlsoap.org/ws/2004/10/wsat|  
|<span data-ttu-id="deb93-159">t</span><span class="sxs-lookup"><span data-stu-id="deb93-159">t</span></span>|http://schemas.xmlsoap.org/ws/2005/02/trust|  
|<span data-ttu-id="deb93-160">o</span><span class="sxs-lookup"><span data-stu-id="deb93-160">o</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd|  
|<span data-ttu-id="deb93-161">XSD</span><span class="sxs-lookup"><span data-stu-id="deb93-161">xsd</span></span>|http://www.w3.org/2001/XMLSchema|  
  
## <a name="transaction-manager-bindings"></a><span data-ttu-id="deb93-162">İşlem Yöneticisi bağlamaları</span><span class="sxs-lookup"><span data-stu-id="deb93-162">Transaction Manager Bindings</span></span>  
 <span data-ttu-id="deb93-163">R1001: İşlem yöneticileri SOAP 1.1 ve WS adresleme 2004/08 WS-Atomic işlemleri ve Web Hizmetleri koordinasyonu ileti alışverişlerinde için kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="deb93-163">R1001: Transaction Managers must use SOAP 1.1 and WS-Addressing 2004/08 for WS-Atomic Transaction and WS-Coordination message exchanges.</span></span>  
  
 <span data-ttu-id="deb93-164">Uygulama iletileri bu bağlamaların kısıtlı değildir ve daha sonra açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="deb93-164">Application messages are not constrained to these bindings and are described later.</span></span>  
  
### <a name="transaction-manager-https-binding"></a><span data-ttu-id="deb93-165">İşlem Yöneticisi HTTPS bağlama</span><span class="sxs-lookup"><span data-stu-id="deb93-165">Transaction Manager HTTPS Binding</span></span>  
 <span data-ttu-id="deb93-166">İşlem Yöneticisi HTTPS bağlamasını güvenliği sağlamak ve işlem ağacında her gönderenin alıcı çifti arasında güven oluşturmak için yalnızca taşıma güvenliği kullanır.</span><span class="sxs-lookup"><span data-stu-id="deb93-166">The transaction manager HTTPS binding relies solely on transport security to achieve security and establish trust between each sender-receiver pair in the transaction tree.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="deb93-167">HTTPS taşıma yapılandırması</span><span class="sxs-lookup"><span data-stu-id="deb93-167">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="deb93-168">X.509 sertifikaları işlem yöneticisi kimliğini oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="deb93-168">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="deb93-169">İstemci/sunucu kimlik doğrulaması gerekli değildir ve istemci/sunucu yetkilendirme uygulama ayrıntı olarak kalır:</span><span class="sxs-lookup"><span data-stu-id="deb93-169">Client/server authentication is required, and client/server authorization is left as an implementation detail:</span></span>  
  
-   <span data-ttu-id="deb93-170">R1111: kablo üzerinden sunulan X.509 sertifikaları kaynak makinenin tam etki alanı adını (FQDN) ile eşleşen bir konu adına sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="deb93-170">R1111: X.509 certificates presented over the wire must have a subject name that matches the fully qualified domain name (FQDN) of the originating machine.</span></span>  
  
-   <span data-ttu-id="deb93-171">B1112: DNS başarılı olması için her gönderenin alıcı çifti arasında X.509 konu adı denetimleri için sistemdeki işlevsel olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="deb93-171">B1112: DNS must be functional between each sender-receiver pair in the system for X.509 subject name checks to succeed.</span></span>  
  
#### <a name="activation-and-registration-binding-configuration"></a><span data-ttu-id="deb93-172">Etkinleştirme ve yapılandırma bağlama kayıt</span><span class="sxs-lookup"><span data-stu-id="deb93-172">Activation and Registration Binding Configuration</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="deb93-173"> İstek/yanıt çift yönlü bağıntı bağlamayla HTTPS üzerinden gerektirir.</span><span class="sxs-lookup"><span data-stu-id="deb93-173"> requires request/reply duplex binding with correlation over HTTPS.</span></span> <span data-ttu-id="deb93-174">(WS-Atomic işlemleri, Bölüm 8 bağıntı ve istek/yanıt iletisi exchange desenleri açıklamalarını hakkında daha fazla bilgi için bkz.)</span><span class="sxs-lookup"><span data-stu-id="deb93-174">(For more information about correlation and descriptions of the request/reply message exchange patterns, see WS-Atomic Transaction, Section 8.)</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="deb93-175">2PC Protokolü bağlama yapılandırması</span><span class="sxs-lookup"><span data-stu-id="deb93-175">2PC Protocol Binding Configuration</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="deb93-176"> tek yönlü (datagram) iletileri HTTPS üzerinden destekler.</span><span class="sxs-lookup"><span data-stu-id="deb93-176"> supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="deb93-177">Bağıntı iletileri arasında bir uygulama ayrıntı olarak kalır.</span><span class="sxs-lookup"><span data-stu-id="deb93-177">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="deb93-178">B2131: Uygulamaları desteklemelidir `wsa:ReferenceParameters` WS-bağıntı elde etmek için adresleme içinde açıklandığı gibi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]'s 2PC iletileri.</span><span class="sxs-lookup"><span data-stu-id="deb93-178">B2131: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]’s 2PC messages.</span></span>  
  
### <a name="transaction-manager-mixed-security-binding"></a><span data-ttu-id="deb93-179">İşlem Yöneticisi güvenlik bağlama karma</span><span class="sxs-lookup"><span data-stu-id="deb93-179">Transaction Manager Mixed Security Binding</span></span>  
 <span data-ttu-id="deb93-180">Bu kimlik kurulması amacıyla Web Hizmetleri koordinasyonu verilen belirteç modeli ile birlikte bu kullanımları taşıma güvenliği bağlama bir alternatif (karma mod) olur.</span><span class="sxs-lookup"><span data-stu-id="deb93-180">This is an alternate (mixed mode) binding that uses transport security combined with the  WS-Coordination Issued Token model for identity establishment purposes.</span></span>  <span data-ttu-id="deb93-181">Etkinleştirme ve kayıt arasında iki bağlamaları farklı yalnızca öğelerdir.</span><span class="sxs-lookup"><span data-stu-id="deb93-181">Activation and Registration are the only elements that differ between the two bindings.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="deb93-182">HTTPS taşıma yapılandırması</span><span class="sxs-lookup"><span data-stu-id="deb93-182">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="deb93-183">X.509 sertifikaları işlem yöneticisi kimliğini oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="deb93-183">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="deb93-184">İstemci/sunucu kimlik doğrulaması gerekli değildir ve istemci/sunucu yetkilendirme uygulama ayrıntı olarak kalır.</span><span class="sxs-lookup"><span data-stu-id="deb93-184">Client/Server authentication is required, and client/server authorization is left as an implementation detail.</span></span>  
  
#### <a name="activation-message-binding-configuration"></a><span data-ttu-id="deb93-185">Etkinleştirme ileti bağlama yapılandırması</span><span class="sxs-lookup"><span data-stu-id="deb93-185">Activation Message Binding Configuration</span></span>  
 <span data-ttu-id="deb93-186">Genellikle bir uygulama ve onun yerel işlem yöneticisi arasında gerçekleştirildiği için etkinleştirme iletiler birlikte çalışabilirlik genellikle katılma.</span><span class="sxs-lookup"><span data-stu-id="deb93-186">Activation Messages usually do not participate in interoperability because they typically occur between an application and its local Transaction Manager.</span></span>  
  
 <span data-ttu-id="deb93-187">B1221: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] çift yönlü HTTPS bağlamasını kullanır (açıklanan [Mesajlaşma protokolleri](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) etkinleştirme iletileri için.</span><span class="sxs-lookup"><span data-stu-id="deb93-187">B1221: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) for Activation messages.</span></span> <span data-ttu-id="deb93-188">İstek ve yanıt iletileri WS adresleme 2004/08 kullanılarak bağıntılı olan.</span><span class="sxs-lookup"><span data-stu-id="deb93-188">Request and Reply messages are correlated using WS-Addressing 2004/08.</span></span>  
  
 <span data-ttu-id="deb93-189">WS-Atomic işlem belirtimi, Bölüm 8, Ayrıntılar bağıntı ve ileti exchange desenleri hakkında daha fazla açıklar.</span><span class="sxs-lookup"><span data-stu-id="deb93-189">WS-Atomic Transaction specification, Section 8, describes further details about correlation and the message exchange patterns.</span></span>  
  
-   <span data-ttu-id="deb93-190">R1222: temel alarak bir `CreateCoordinationContext`, düzenleyici dağıtmalı bir `SecurityContextToken` ile ilişkili gizli `STx`.</span><span class="sxs-lookup"><span data-stu-id="deb93-190">R1222: Upon receiving a `CreateCoordinationContext`, the Coordinator must issue a `SecurityContextToken` with associated secret `STx`.</span></span> <span data-ttu-id="deb93-191">Bu belirteç içinde döndürülen bir `t:IssuedTokens` WS-Trust belirtimine aşağıdaki üstbilgi.</span><span class="sxs-lookup"><span data-stu-id="deb93-191">This token is returned inside a `t:IssuedTokens` header following WS-Trust specification.</span></span>  
  
-   <span data-ttu-id="deb93-192">R1223: Etkinleştirme var olan bir düzenleme bağlamı içinde ortaya çıkarsa `t:IssuedTokens` üstbilgiyle `SecurityContextToken` var olan ilişkili gerekir içerik akışını `CreateCoordinationContext` ileti.</span><span class="sxs-lookup"><span data-stu-id="deb93-192">R1223: If Activation occurs within an existing Coordination Context, the `t:IssuedTokens` header with the `SecurityContextToken` associated with existing Context must flow on the `CreateCoordinationContext` message.</span></span>  
  
 <span data-ttu-id="deb93-193">Yeni bir `t:IssuedTokens` giden eklemek için üstbilgi oluşturulacağı `wscoor:CreateCoordinationContextResponse` ileti.</span><span class="sxs-lookup"><span data-stu-id="deb93-193">A new `t:IssuedTokens` header should be generated for attaching to the outgoing `wscoor:CreateCoordinationContextResponse` message.</span></span>  
  
#### <a name="registration-message-binding-configuration"></a><span data-ttu-id="deb93-194">Kayıt iletisi bağlama yapılandırması</span><span class="sxs-lookup"><span data-stu-id="deb93-194">Registration Message Binding Configuration</span></span>  
 <span data-ttu-id="deb93-195">B1231: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] çift yönlü HTTPS bağlamasını kullanır (açıklanan [Mesajlaşma protokolleri](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)).</span><span class="sxs-lookup"><span data-stu-id="deb93-195">B1231: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)).</span></span> <span data-ttu-id="deb93-196">İstek ve yanıt iletileri WS adresleme 2004/08 kullanılarak bağıntılı olan.</span><span class="sxs-lookup"><span data-stu-id="deb93-196">Request and Reply messages are correlated using WS-Addressing 2004/08.</span></span>  
  
 <span data-ttu-id="deb93-197">WS-AtomicTransaction, Bölüm 8, açıklar daha fazla ayrıntı bağıntı ve ileti exchange desenleri açıklamalarını hakkında.</span><span class="sxs-lookup"><span data-stu-id="deb93-197">WS-AtomicTransaction, Section 8, describes further details about correlation and descriptions of the message exchange patterns.</span></span>  
  
 <span data-ttu-id="deb93-198">R1232: Giden `wscoor:Register` iletileri kullanmalıdır `IssuedTokenOverTransport` kimlik doğrulama modu açıklanan [güvenlik protokolleri](../../../../docs/framework/wcf/feature-details/security-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="deb93-198">R1232: Outgoing `wscoor:Register` messages must use the `IssuedTokenOverTransport` authentication mode described in [Security Protocols](../../../../docs/framework/wcf/feature-details/security-protocols.md).</span></span>  
  
 <span data-ttu-id="deb93-199">`wsse:Timestamp` Öğesi kullanılarak imzalanmalıdır `SecurityContextToken``STx` verilmiş.</span><span class="sxs-lookup"><span data-stu-id="deb93-199">The `wsse:Timestamp` element must be signed using the `SecurityContextToken``STx` issued.</span></span> <span data-ttu-id="deb93-200">Bu imza belirli işlemle ilişkili belirtecinin kanıtını olup işlemde kaydetme katılımcı kimliğini doğrulamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="deb93-200">This signature is a proof of possession of the token associated with particular transaction and is used to authenticate a participant enlisting in the transaction.</span></span> <span data-ttu-id="deb93-201">RegistrationResponse ileti HTTPS üzerinden gönderilir.</span><span class="sxs-lookup"><span data-stu-id="deb93-201">The RegistrationResponse message is sent back over HTTPS.</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="deb93-202">2PC Protokolü bağlama yapılandırması</span><span class="sxs-lookup"><span data-stu-id="deb93-202">2PC Protocol Binding Configuration</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="deb93-203"> tek yönlü (datagram) iletileri HTTPS üzerinden destekler.</span><span class="sxs-lookup"><span data-stu-id="deb93-203"> supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="deb93-204">Bağıntı iletileri arasında bir uygulama ayrıntı olarak kalır.</span><span class="sxs-lookup"><span data-stu-id="deb93-204">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="deb93-205">B2131: Uygulamaları desteklemelidir `wsa:ReferenceParameters` WS-bağıntı elde etmek için adresleme içinde açıklandığı gibi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]'s 2PC iletileri.</span><span class="sxs-lookup"><span data-stu-id="deb93-205">B2131: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]’s 2PC messages.</span></span>  
  
## <a name="application-message-exchange"></a><span data-ttu-id="deb93-206">Uygulama ileti değişimi</span><span class="sxs-lookup"><span data-stu-id="deb93-206">Application Message Exchange</span></span>  
 <span data-ttu-id="deb93-207">Uygulamaları bağlama aşağıdaki güvenlik gereksinimlerini karşılayan sürece herhangi belirli uygulama uygulaması iletileri için bu bağlamayı kullanmak boş şunlardır:</span><span class="sxs-lookup"><span data-stu-id="deb93-207">Applications are free to use any particular binding for application-to-application messages, as long as the binding meets the following security requirements:</span></span>  
  
-   <span data-ttu-id="deb93-208">R2001: Uygulama uygulaması iletileri akış gerekir `t:IssuedTokens` başlığı ile birlikte `CoordinationContext` ileti üstbilgisinde.</span><span class="sxs-lookup"><span data-stu-id="deb93-208">R2001: Application-to-application messages must flow the `t:IssuedTokens` header along with the `CoordinationContext` in the header of the message.</span></span>  
  
-   <span data-ttu-id="deb93-209">R2002: Bütünlüğü ve gizliliği `t:IssuedToken` sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="deb93-209">R2002: Integrity and confidentiality of `t:IssuedToken` must be provided.</span></span>  
  
 <span data-ttu-id="deb93-210">`CoordinationContext` Üst bilgiyi içeren `wscoor:Identifier`.</span><span class="sxs-lookup"><span data-stu-id="deb93-210">The `CoordinationContext` header contains `wscoor:Identifier`.</span></span> <span data-ttu-id="deb93-211">While tanımını `xsd:AnyURI` mutlak veya göreli URI, kullanılmasına [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] yalnızca destekler `wscoor:Identifiers`, mutlak URI olduğu.</span><span class="sxs-lookup"><span data-stu-id="deb93-211">While the definition of `xsd:AnyURI` allows the use of both absolute and relative URIs, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] supports only `wscoor:Identifiers`, which are absolute URIs.</span></span>  
  
 <span data-ttu-id="deb93-212">Varsa `wscoor:Identifier` , `wscoor:CoordinationContext` göreli bir URI hataları döndürülecek gelen işlem [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hizmetleri.</span><span class="sxs-lookup"><span data-stu-id="deb93-212">If the `wscoor:Identifier` of the `wscoor:CoordinationContext` is a relative URI, faults will be returned from transactional [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services.</span></span>  
  
## <a name="message-examples"></a><span data-ttu-id="deb93-213">İleti örnekleri</span><span class="sxs-lookup"><span data-stu-id="deb93-213">Message Examples</span></span>  
  
### <a name="createcoordinationcontext-requestresponse-messages"></a><span data-ttu-id="deb93-214">CreateCoordinationContext istek/yanıt iletilerini</span><span class="sxs-lookup"><span data-stu-id="deb93-214">CreateCoordinationContext Request/Response Messages</span></span>  
 <span data-ttu-id="deb93-215">Aşağıdaki ileti, bir istek/yanıt yol izler.</span><span class="sxs-lookup"><span data-stu-id="deb93-215">The following messages follow a request/response pattern.</span></span>  
  
#### <a name="createcoordinationcontext"></a><span data-ttu-id="deb93-216">CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="deb93-216">CreateCoordinationContext</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>http://.../ws/2004/10/wscoor/CreateCoordinationContext</Action>  
    <a:MessageID>urn:uuid:069f5104-fd88-4264-9f99-60032a82854e</MessageID>  
    <a:ReplyTo>  
      <Address>https://...</a:Address>  
    </a:ReplyTo>  
    <a:To>https://...</a:To>  
    <wsse:Security>  
      <u:Timestamp>  
        <wsu:Created>2005-12-15T23:36:09.921Z</u:Created>  
        <wsu:Expires>2005-12-15T23:41:09.921Z</u:Expires>  
      </u:Timestamp>  
    </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wscoor:CreateCoordinationContext>  
      <wscoor:CoordinationType>...</wscoor:CoordinationType>  
    </wscoor:CreateCoordinationContext>  
  </s:Body>  
</s11:Envelope>  
```  
  
#### <a name="createcoordinationcontextresponse"></a><span data-ttu-id="deb93-217">CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="deb93-217">CreateCoordinationContextResponse</span></span>  
  
```xml  
<s:Envelope>  
  <!-- Data below is shown in the clear for  
       illustration purposes only. -->  
  <s:Header>  
    <a:Action>./ws/2004/10/wscoor/CreateCoordinationContextResponse </a:Action>  
    <a:RelatesTo>urn:uuid:069f5104-fd88-4264-9f99-60032a82854e</a:RelatesTo>  
    <a:To s:mustUnderstand="1">https://... </a:To>  
    <t:IssuedTokens>  
 <wst:RequestSecurityTokenResponse     
    xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
    xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd"   
    xmlns:wst="http://schemas.xmlsoap.org/ws/2005/02/trust"  
    xmlns:wsc="http://schemas.xmlsoap.org/ws/2005/02/sc"  
    xmlns:wsp="http://schemas.xmlsoap.org/ws/2004/09/policy">  
    <wst:TokenType>http://schemas.xmlsoap.org/ws/2005/02/sc/sct</wst:TokenType>  
    <wst:RequestedSecurityToken>  
      <wsc:SecurityContextToken>  
        <wssu:Identifier>  
          http://fabrikam123.com/SCTi  
        </wssu:Identifier>  
      </wsc:SecurityContextToken>   
    </wst:RequestedSecurityToken>  
    <wsp:AppliesTo>  
        http://fabrikam123.com/CCi  
    </wsp:AppliesTo>    
    <wst:RequestedAttachedReference>  
      <wsse:SecurityTokenReference >  
        <wsse:Reference   
           ValueType="http://schemas.xmlsoap.org/ws/2005/02/sc/sct"  
           URI="http://fabrikam123.com/SCTi"/>  
      </wsse:SecurityTokenReference>  
    </wst:RequestedAttachedReference>  
    <wst:RequestedUnattachedReference>  
      <wsse:SecurityTokenReference>  
        <wsse:Reference   
          ValueType="http://schemas.xmlsoap.org/ws/2005/02/sc/sct"  
          URI="http://fabrikam123.com/SCTi"/>  
      </wsse:SecurityTokenReference>  
    </wst:RequestedUnattachedReference>  
    <wst:RequestedProofToken>  
      <wst:BinarySecret   
        Type="http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey">  
        <!-- base64 encoded value -->  
      </wst:BinarySecret>  
    </wst:RequestedProofToken>  
    <wst:Lifetime>  
      <wssu:Created>2005-10-24T20:19:26.526Z</wssu:Created>  
      <wssu:Expires>2005-10-25T06:24:26.526Z</wssu:Expires>  
    </wst:Lifetime>  
    <wst:KeySize>256</wst:KeySize>  
</wst:RequestSecurityTokenResponse>  
    </t:IssuedTokens>  
    <o:Security xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">  
      <u:Timestamp u:Id="_0">  
        <u:Created>2005-12-15T23:36:12.015Z</u:Created>  
        <u:Expires>2005-12-15T23:41:12.015Z</u:Expires>  
      </u:Timestamp>  
    </o:Security>  
  </s:Header>  
  <s:Body>  
    <wscoor:CreateCoordinationContextResponse>  
      <wscoor:CoordinationContext>  
        <wscoor:Identifier>  
     http://fabrikam123.com/CCi  
      </wscoor:Identifier>  
        <wscoor:Expires>...</wscoor:Expires>  
        <wscoor:CoordinationType>...</wscoor:CoordinationType>  
        <wscoor:RegistrationService>  
          <a:Address>https://...</a:Address>  
          <a:ReferenceParameters>  
             ...  
          </a:ReferenceParameters>  
        </wscoor:RegistrationService>  
      </wscoor:CoordinationContext>  
    </wscoor:CreateCoordinationContextResponse>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="registration-messages"></a><span data-ttu-id="deb93-218">Kayıt iletileri</span><span class="sxs-lookup"><span data-stu-id="deb93-218">Registration Messages</span></span>  
 <span data-ttu-id="deb93-219">Aşağıdaki iletileri kayıt iletileri edilir.</span><span class="sxs-lookup"><span data-stu-id="deb93-219">The following messages are registration messages.</span></span>  
  
#### <a name="register"></a><span data-ttu-id="deb93-220">Yazmaç</span><span class="sxs-lookup"><span data-stu-id="deb93-220">Register</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>http://schemas.xmlsoap.org/ws/2004/10/wscoor/Register</a:Action>  
    <a:MessageID>urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088e</a:MessageID>  
    <a:ReplyTo>  
      <a:Address>https://...</a:Address>        
    </a:ReplyTo>  
    <a:To>https://...</a:To>  
    <wsse:Security   
      s:mustUnderstand="1"   
      xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
      xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
      <wssu:Timestamp wssu:Id="_0" >  
        <wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
        <wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
      </wssu:Timestamp>  
      <wsc:SecurityContextToken>  
      <wssu:Identifier>  
          http://fabrikam123.com/SCTi  
      </wssu:Identifier>  
      </wsc:SecurityContextToken>  
      <!-- supporting signature over the timestamp -->  
      <wsse:Signature xmlns:ds="http://www.w3.org/2000/09/xmldsig#">  
        <ds:SignedInfo>  
          <ds:CanonicalizationMethod Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"/>  
          <ds:SignatureMethod Algorithm="http://www.w3.org/2000/09/xmldsig#hmac-sha1"/>  
          <ds:Reference URI="#_0">  
            <ds:Transforms>  
              <ds:Transform Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"/>  
            </ds:Transforms>  
            <ds:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1"/>  
            <ds:DigestValue>  
              alRzyhjLgoUOYoh8cx4n75eTcUk=  
            </ds:DigestValue>  
          </ds:Reference>  
        </ds:SignedInfo>  
        <ds:SignatureValue>YZYjnVvSOVasAQqQxaaviTSWtqI=</ds:SignatureValue>  
        <ds:KeyInfo>  
          <wsse:SecurityTokenReference  
            xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">  
            <wsse:Reference   
              URI="http://fabrikam123.com/SCTi"/>  
          </wsse:SecurityTokenReference>  
        </ds:KeyInfo>  
      </wsse:Signature>  
    </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wscoor:Register>  
      <wscoor:ProtocolIdentifier>...</wscoor:ProtocolIdentifier>  
      <wscoor:ParticipantProtocolService>  
        <a:Address>https://... </a:Address>  
      </wscoor:ParticipantProtocolService>  
    </wscoor:Register>  
  </s:Body>  
</s:Envelope>  
```  
  
#### <a name="register-response"></a><span data-ttu-id="deb93-221">Yanıt kaydetme</span><span class="sxs-lookup"><span data-stu-id="deb93-221">Register Response</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>  
      http://schemas.xmlsoap.org/ws/2004/10/wscoor/RegisterResponse  
    </a:Action>  
    <a:MessageID>urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088d</a:MessageID>  
    <a:RelatesTo>  
      urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088e        
    </a:RelatesTo>  
    <a:To>https://...</a:To>  
    <wsse:Security   
      s:mustUnderstand="1"   
      xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
      xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
      <wssu:Timestamp>  
        <wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
        <wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
      </wssu:Timestamp>  
    </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wscoor:RegisterResponse>  
      <wscoor:CoordinatorProtocolService>  
        <a:Address>https://...</a:Address>  
        <a:ReferenceParameters>  
          ...  
        </a:ReferenceParameters>  
      </wscoor:CoordinatorProtocolService>  
    </wscoor:RegisterResponse>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="two-phase-commit-protocol-messages"></a><span data-ttu-id="deb93-222">İki aşama yürütme Protokolü iletileri</span><span class="sxs-lookup"><span data-stu-id="deb93-222">Two Phase Commit Protocol Messages</span></span>  
 <span data-ttu-id="deb93-223">Aşağıdaki ileti iki aşamalı kayıt (2PC) protokolüne ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="deb93-223">The following message relates to the two-phase commit (2PC) protocol.</span></span>  
  
#### <a name="commit"></a><span data-ttu-id="deb93-224">Tamamlama</span><span class="sxs-lookup"><span data-stu-id="deb93-224">Commit</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>http://.../ws/2004/10/wsat/Commit</a:Action>  
    <a:To>https://...</a:To>  
    <wsse:Security   
      s:mustUnderstand="1"   
      xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
      xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
      <wssu:Timestamp wssu:Id="_0" >  
        <wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
        <wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
      </wssu:Timestamp>  
   </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wsat:Commit />  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="application-messages"></a><span data-ttu-id="deb93-225">Uygulama iletileri</span><span class="sxs-lookup"><span data-stu-id="deb93-225">Application Messages</span></span>  
 <span data-ttu-id="deb93-226">Aşağıdaki iletileri uygulama iletileri edilir.</span><span class="sxs-lookup"><span data-stu-id="deb93-226">The following messages are application messages.</span></span>  
  
#### <a name="application-message-request"></a><span data-ttu-id="deb93-227">Uygulama iletiyi-isteği</span><span class="sxs-lookup"><span data-stu-id="deb93-227">Application message-Request</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
<!-- Addressing headers, all signed-->  
    <wsse:Security s:mustUnderstand="1">  
      <wssu:Timestamp wssu:Id="timestamp">   
        <wssu:Created>2005-10-25T06:29:18.703Z</wssu:Created>  
        <wssu:Expires>2005-10-25T06:34:18.703Z</wssu:Expires>  
      </wssu:Timestamp>  
      <wsse:BinarySecurityToken   
          wssu:Id="IA_Certificate"   
          ValueType="...#X509v3"   
          EncodingType="...#Base64Binary">  
        <!-- IA certificate -->  
      </wsse:BinarySecurityToken>  
      <e:EncryptedKey Id="encrypted_key">  
            <!-- ephemeral key encrypted for PA certificate -->    
        <e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#">  
          <e:DataReference URI="#encrypted_body"/>  
          <e:DataReference URI="#encrypted_CCi"/>  
          <e:DataReference URI="#encrypted_issuedtokens"/>  
        </e:ReferenceList>  
      </e:EncryptedKey>  
      <Signature xmlns="http://www.w3.org/2000/09/xmldsig#">  
        <!-- signature over Addressing headers, Timestamp, and Body -->  
      </Signature>  
    </wsse:Security>  
    <wsse11:EncryptedHeader >  
     <!-- encrypted wscoor:CoordinationContext header containing CCi -->  
    </wsse11:EncryptedHeader>  
    <wsse11:EncryptedHeader   
      <!-- encrypted wst:IssuedTokens header containing SCTi -->  
      <!-- wst:IssuedTokens header is taken verbatim from message #2 above, omitted for brevity -->  
    </wsse11:EncryptedHeader>  
  </s:Header>  
  <s:Body wssu:Id="body">  
    <!-- encrypted content of the Body element of the application message -->      
    <e:EncryptedData Id="encrypted_body"   
           Type="http://www.w3.org/2001/04/xmlenc#Content"   
           xmlns:e="http://www.w3.org/2001/04/xmlenc#">  
...  
    </e:EncryptedData>  
  </s:Body>  
</s:Envelope>  
```

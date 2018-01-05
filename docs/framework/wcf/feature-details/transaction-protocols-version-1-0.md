---
title: "İşlem Protokolleri sürüm 1.0"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 034679af-0002-402e-98a8-ef73dcd71bb6
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e616f989416fcee77caa9b9a5d87cfa6812eab32
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="transaction-protocols-version-10"></a><span data-ttu-id="8dd9e-102">İşlem Protokolleri sürüm 1.0</span><span class="sxs-lookup"><span data-stu-id="8dd9e-102">Transaction Protocols version 1.0</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="8dd9e-103">Sürüm 1, sürüm 1.0 WS-Atomic işlemleri ve Web Hizmetleri koordinasyonu kurallarının uygular.</span><span class="sxs-lookup"><span data-stu-id="8dd9e-103"> version 1 implements version 1.0 of the WS-Atomic Transaction and WS-Coordination protocols.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="8dd9e-104">Sürüm 1.1 bkz [işlem protokolleri](../../../../docs/framework/wcf/feature-details/transaction-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="8dd9e-104"> version 1.1, see [Transaction Protocols](../../../../docs/framework/wcf/feature-details/transaction-protocols.md).</span></span>  
  
|<span data-ttu-id="8dd9e-105">Belirtim/belgesi</span><span class="sxs-lookup"><span data-stu-id="8dd9e-105">Specification/Document</span></span>|<span data-ttu-id="8dd9e-106">Bağlantı</span><span class="sxs-lookup"><span data-stu-id="8dd9e-106">Link</span></span>|  
|-----------------------------|----------|  
|<span data-ttu-id="8dd9e-107">WS-düzenleme</span><span class="sxs-lookup"><span data-stu-id="8dd9e-107">WS-Coordination</span></span>|<span data-ttu-id="8dd9e-108">http://msdn.microsoft.com/ws/2005/08/ws-Coordination/</span><span class="sxs-lookup"><span data-stu-id="8dd9e-108">http://msdn.microsoft.com/ws/2005/08/ws-coordination/</span></span>|  
|<span data-ttu-id="8dd9e-109">WS-AtomicTransaction</span><span class="sxs-lookup"><span data-stu-id="8dd9e-109">WS-AtomicTransaction</span></span>|<span data-ttu-id="8dd9e-110">http://msdn.microsoft.com/ws/2005/08/WS-AtomicTransaction/</span><span class="sxs-lookup"><span data-stu-id="8dd9e-110">http://msdn.microsoft.com/ws/2005/08/ws-atomictransaction/</span></span>|  
  
 <span data-ttu-id="8dd9e-111">Bu protokol belirtimleri üzerinde birlikte çalışabilirlik iki düzeyde gereklidir: uygulamalar arasında arasında işlem yöneticileri (Aşağıdaki şekle bakın).</span><span class="sxs-lookup"><span data-stu-id="8dd9e-111">Interoperability on these protocol specifications is required at two levels: between applications and between transaction managers (see the following figure).</span></span> <span data-ttu-id="8dd9e-112">İletisi ve ileti formatları için her iki birlikte çalışabilirlik düzeylerini exchange harika ayrıntılı özellikleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8dd9e-112">Specifications describe in great detail the message formats and message exchange for both interoperability levels.</span></span> <span data-ttu-id="8dd9e-113">Normal uygulama exchange için yaptığınız gibi belirli güvenlik, güvenilirlik ve kodlamaları uygulama uygulaması exchange için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="8dd9e-113">Certain security, reliability, and encodings for application-to-application exchange apply as they do for regular application exchange.</span></span> <span data-ttu-id="8dd9e-114">Ancak, kullanıcı tarafından genellikle yapılandırılmadığı için işlem yöneticileri başarılı işlerliği belirli bağlama anlaşmasında gerektirir.</span><span class="sxs-lookup"><span data-stu-id="8dd9e-114">However, successful interoperability between transaction managers requires agreement on the particular binding, because it is usually not configured by the user.</span></span>  
  
 <span data-ttu-id="8dd9e-115">Bu konu, WS-Atomic işlem (WS-AT) belirtimi bileşimi ile güvenliği açıklar ve işlem yöneticileri arasındaki iletişim için kullanılan güvenli bağlama açıklar.</span><span class="sxs-lookup"><span data-stu-id="8dd9e-115">This topic describes a composition of the WS-Atomic Transaction (WS-AT) specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="8dd9e-116">Bu belgede açıklanan yaklaşım başarıyla WS-AT ve Web Hizmetleri koordinasyonu diğer uygulamaları ile test edilmiştir IBM, IONA, Sun Microsystems ve diğerleri de dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="8dd9e-116">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination including IBM, IONA, Sun Microsystems, and others.</span></span>  
  
 <span data-ttu-id="8dd9e-117">Aşağıdaki şekil, İşlem Yöneticisi 1 ve işlem yöneticisi 2, iki işlem yöneticileri ve uygulama 1 ve uygulama 2 iki uygulama arasındaki birlikte çalışabilirlik gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8dd9e-117">The following figure depicts the interoperability between two transaction managers, Transaction Manager 1 and Transaction Manager 2, and two applications, Application 1 and Application 2.</span></span>  
  
 <span data-ttu-id="8dd9e-118">![İşlem protokolleri](../../../../docs/framework/wcf/feature-details/media/transactionmanagers.gif "TransactionManagers")</span><span class="sxs-lookup"><span data-stu-id="8dd9e-118">![Transaction Protocols](../../../../docs/framework/wcf/feature-details/media/transactionmanagers.gif "TransactionManagers")</span></span>  
  
 <span data-ttu-id="8dd9e-119">Bir başlatıcı (ı) ve bir katılımcı (P) tipik bir WS-düzenleme/WS-Atomic işlem senaryoyu göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="8dd9e-119">Consider a typical WS-Coordination/WS-Atomic Transaction scenario with one Initiator (I) and one Participant (P).</span></span> <span data-ttu-id="8dd9e-120">Hem Başlatıcı hem de katılımcı olan işlem yöneticileri (ITM ve PTM, sırasıyla).</span><span class="sxs-lookup"><span data-stu-id="8dd9e-120">Both Initiator and Participant have Transaction Managers, (ITM and PTM, respectively).</span></span> <span data-ttu-id="8dd9e-121">İki aşamalı yürütme için bu konudaki 2PC olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="8dd9e-121">Two-phase commit is referred to as 2PC in this topic.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8dd9e-122">1. CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="8dd9e-122">1. CreateCoordinationContext</span></span>|<span data-ttu-id="8dd9e-123">12. Uygulama ileti yanıtı</span><span class="sxs-lookup"><span data-stu-id="8dd9e-123">12. Application Message Response</span></span>|  
|<span data-ttu-id="8dd9e-124">2. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="8dd9e-124">2. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="8dd9e-125">13. Yürütme (tamamlanma)</span><span class="sxs-lookup"><span data-stu-id="8dd9e-125">13. Commit (Completion)</span></span>|  
|<span data-ttu-id="8dd9e-126">3. YAZMAÇ (tamamlanma)</span><span class="sxs-lookup"><span data-stu-id="8dd9e-126">3. Register (Completion)</span></span>|<span data-ttu-id="8dd9e-127">14. (2PC) hazırlama</span><span class="sxs-lookup"><span data-stu-id="8dd9e-127">14. Prepare (2PC)</span></span>|  
|<span data-ttu-id="8dd9e-128">4. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="8dd9e-128">4. RegisterResponse</span></span>|<span data-ttu-id="8dd9e-129">15. (2PC) hazırlama</span><span class="sxs-lookup"><span data-stu-id="8dd9e-129">15. Prepare (2PC)</span></span>|  
|<span data-ttu-id="8dd9e-130">5. Uygulama iletisi</span><span class="sxs-lookup"><span data-stu-id="8dd9e-130">5. Application Message</span></span>|<span data-ttu-id="8dd9e-131">16. Hazırlanan (2PC)</span><span class="sxs-lookup"><span data-stu-id="8dd9e-131">16. Prepared (2PC)</span></span>|  
|<span data-ttu-id="8dd9e-132">6. Bağlamına sahip CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="8dd9e-132">6. CreateCoordinationContext with Context</span></span>|<span data-ttu-id="8dd9e-133">17. Hazırlanan (2PC)</span><span class="sxs-lookup"><span data-stu-id="8dd9e-133">17. Prepared (2PC)</span></span>|  
|<span data-ttu-id="8dd9e-134">7. YAZMAÇ (dayanıklı)</span><span class="sxs-lookup"><span data-stu-id="8dd9e-134">7. Register (Durable)</span></span>|<span data-ttu-id="8dd9e-135">18. Kaydedilmiş (tamamlanma)</span><span class="sxs-lookup"><span data-stu-id="8dd9e-135">18. Committed (Completion)</span></span>|  
|<span data-ttu-id="8dd9e-136">8. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="8dd9e-136">8. RegisterResponse</span></span>|<span data-ttu-id="8dd9e-137">19. Kayıt (2PC)</span><span class="sxs-lookup"><span data-stu-id="8dd9e-137">19. Commit (2PC)</span></span>|  
|<span data-ttu-id="8dd9e-138">9. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="8dd9e-138">9. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="8dd9e-139">20. Kayıt (2PC)</span><span class="sxs-lookup"><span data-stu-id="8dd9e-139">20. Commit (2PC)</span></span>|  
|<span data-ttu-id="8dd9e-140">10. YAZMAÇ (dayanıklı)</span><span class="sxs-lookup"><span data-stu-id="8dd9e-140">10. Register (Durable)</span></span>|<span data-ttu-id="8dd9e-141">21. Kaydedilmiş (2PC)</span><span class="sxs-lookup"><span data-stu-id="8dd9e-141">21. Committed (2PC)</span></span>|  
|<span data-ttu-id="8dd9e-142">11. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="8dd9e-142">11. RegisterResponse</span></span>|<span data-ttu-id="8dd9e-143">22. Kaydedilmiş (2PC)</span><span class="sxs-lookup"><span data-stu-id="8dd9e-143">22. Committed (2PC)</span></span>|  
  
 <span data-ttu-id="8dd9e-144">Bu belge WS-AtomicTransaction belirtiminin bir birleşim ile güvenliği açıklar ve işlem yöneticileri arasındaki iletişim için kullanılan güvenli bağlama açıklar.</span><span class="sxs-lookup"><span data-stu-id="8dd9e-144">This document describes a composition of the WS-AtomicTransaction specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="8dd9e-145">Bu belgede açıklanan yaklaşım başarıyla WS-AT ve Web Hizmetleri koordinasyonu diğer uygulamaları ile test edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8dd9e-145">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination.</span></span>  
  
 <span data-ttu-id="8dd9e-146">Şekil ve tabloda güvenlik görüş iletilerden dört sınıflarını gösterir:</span><span class="sxs-lookup"><span data-stu-id="8dd9e-146">The figure and table illustrate four classes of messages from the viewpoint of security:</span></span>  
  
-   <span data-ttu-id="8dd9e-147">Etkinleştirme iletileri (CreateCoordinationContext ve CreateCoordinationContextResponse).</span><span class="sxs-lookup"><span data-stu-id="8dd9e-147">Activation messages (CreateCoordinationContext and CreateCoordinationContextResponse).</span></span>  
  
-   <span data-ttu-id="8dd9e-148">Kayıt iletiler (kaydetme ve RegisterResponse)</span><span class="sxs-lookup"><span data-stu-id="8dd9e-148">Registration messages (Register and RegisterResponse)</span></span>  
  
-   <span data-ttu-id="8dd9e-149">Protokol iletileri (hazırlama, geri alma, kaydetme, iptal edildi vb.).</span><span class="sxs-lookup"><span data-stu-id="8dd9e-149">Protocol messages (Prepare, Rollback, Commit, Aborted, and so on).</span></span>  
  
-   <span data-ttu-id="8dd9e-150">Uygulama iletileri.</span><span class="sxs-lookup"><span data-stu-id="8dd9e-150">Application messages.</span></span>  
  
 <span data-ttu-id="8dd9e-151">İlk üç ileti sınıfları işlem yöneticisi iletileri kabul edilir ve bağlama yapılandırmalarını "Uygulama ileti değişimi" Bu konunun ilerleyen bölümlerinde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="8dd9e-151">The first three message classes are considered Transaction Manager messages and their binding configuration is described in the "Application Message Exchange" later in this topic.</span></span> <span data-ttu-id="8dd9e-152">İletinin dördüncü sınıfını uygulamaya iletileri ve bu konunun devamındaki "İletisi örnekler" bölümünde açıklanan.</span><span class="sxs-lookup"><span data-stu-id="8dd9e-152">The fourth class of message is application to application messages and is described in the "Message Examples" section later in this topic.</span></span> <span data-ttu-id="8dd9e-153">Bu bölümde tarafından bu sınıfların her biri için kullanılan protokolü bağlamaları açıklanmaktadır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8dd9e-153">This section describes the protocol bindings used for each of these classes by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 <span data-ttu-id="8dd9e-154">Aşağıdaki XML ad alanları ve ilişkili önekleri bu belge boyunca kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8dd9e-154">The following XML Namespaces and associated prefixes are used throughout this document.</span></span>  
  
|<span data-ttu-id="8dd9e-155">önek</span><span class="sxs-lookup"><span data-stu-id="8dd9e-155">Prefix</span></span>|<span data-ttu-id="8dd9e-156">Namespace URI</span><span class="sxs-lookup"><span data-stu-id="8dd9e-156">Namespace URI</span></span>|  
|------------|-------------------|  
|<span data-ttu-id="8dd9e-157">S11</span><span class="sxs-lookup"><span data-stu-id="8dd9e-157">s11</span></span>|<span data-ttu-id="8dd9e-158">http://schemas.xmlsoap.org/SOAP/Envelope</span><span class="sxs-lookup"><span data-stu-id="8dd9e-158">http://schemas.xmlsoap.org/soap/envelope</span></span>|  
|<span data-ttu-id="8dd9e-159">wsa</span><span class="sxs-lookup"><span data-stu-id="8dd9e-159">wsa</span></span>|<span data-ttu-id="8dd9e-160">http://www.w3.org/2004/08/Addressing</span><span class="sxs-lookup"><span data-stu-id="8dd9e-160">http://www.w3.org/2004/08/addressing</span></span>|  
|<span data-ttu-id="8dd9e-161">wscoor</span><span class="sxs-lookup"><span data-stu-id="8dd9e-161">wscoor</span></span>|<span data-ttu-id="8dd9e-162">http://schemas.xmlsoap.org/ws/2004/10/wscoor</span><span class="sxs-lookup"><span data-stu-id="8dd9e-162">http://schemas.xmlsoap.org/ws/2004/10/wscoor</span></span>|  
|<span data-ttu-id="8dd9e-163">WSAT</span><span class="sxs-lookup"><span data-stu-id="8dd9e-163">wsat</span></span>|<span data-ttu-id="8dd9e-164">http://schemas.xmlsoap.org/ws/2004/10/WSAT</span><span class="sxs-lookup"><span data-stu-id="8dd9e-164">http://schemas.xmlsoap.org/ws/2004/10/wsat</span></span>|  
|<span data-ttu-id="8dd9e-165">t</span><span class="sxs-lookup"><span data-stu-id="8dd9e-165">t</span></span>|<span data-ttu-id="8dd9e-166">http://schemas.xmlsoap.org/ws/2005/02/Trust</span><span class="sxs-lookup"><span data-stu-id="8dd9e-166">http://schemas.xmlsoap.org/ws/2005/02/trust</span></span>|  
|<span data-ttu-id="8dd9e-167">O</span><span class="sxs-lookup"><span data-stu-id="8dd9e-167">o</span></span>|<span data-ttu-id="8dd9e-168">http://docs.oasis-Open.org/WSS/2004/01/oasis-200401-WSS-wssecurity-secext-1.0.xsd</span><span class="sxs-lookup"><span data-stu-id="8dd9e-168">http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd</span></span>|  
|<span data-ttu-id="8dd9e-169">XSD</span><span class="sxs-lookup"><span data-stu-id="8dd9e-169">xsd</span></span>|<span data-ttu-id="8dd9e-170">http://www.w3.org/2001/XMLSchema</span><span class="sxs-lookup"><span data-stu-id="8dd9e-170">http://www.w3.org/2001/XMLSchema</span></span>|  
  
## <a name="transaction-manager-bindings"></a><span data-ttu-id="8dd9e-171">İşlem Yöneticisi bağlamaları</span><span class="sxs-lookup"><span data-stu-id="8dd9e-171">Transaction Manager Bindings</span></span>  
 <span data-ttu-id="8dd9e-172">R1001: İşlem yöneticileri SOAP 1.1 ve WS adresleme 2004/08 WS-Atomic işlemleri ve Web Hizmetleri koordinasyonu ileti alışverişlerinde için kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8dd9e-172">R1001: Transaction Managers must use SOAP 1.1 and WS-Addressing 2004/08 for WS-Atomic Transaction and WS-Coordination message exchanges.</span></span>  
  
 <span data-ttu-id="8dd9e-173">Uygulama iletileri bu bağlamaların kısıtlı değildir ve daha sonra açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8dd9e-173">Application messages are not constrained to these bindings and are described later.</span></span>  
  
### <a name="transaction-manager-https-binding"></a><span data-ttu-id="8dd9e-174">İşlem Yöneticisi HTTPS bağlama</span><span class="sxs-lookup"><span data-stu-id="8dd9e-174">Transaction Manager HTTPS Binding</span></span>  
 <span data-ttu-id="8dd9e-175">İşlem Yöneticisi HTTPS bağlamasını güvenliği sağlamak ve işlem ağacında her gönderenin alıcı çifti arasında güven oluşturmak için yalnızca taşıma güvenliği kullanır.</span><span class="sxs-lookup"><span data-stu-id="8dd9e-175">The transaction manager HTTPS binding relies solely on transport security to achieve security and establish trust between each sender-receiver pair in the transaction tree.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="8dd9e-176">HTTPS taşıma yapılandırması</span><span class="sxs-lookup"><span data-stu-id="8dd9e-176">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="8dd9e-177">X.509 sertifikaları işlem yöneticisi kimliğini oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8dd9e-177">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="8dd9e-178">İstemci/sunucu kimlik doğrulaması gerekli değildir ve istemci/sunucu yetkilendirme uygulama ayrıntı olarak kalır:</span><span class="sxs-lookup"><span data-stu-id="8dd9e-178">Client/server authentication is required, and client/server authorization is left as an implementation detail:</span></span>  
  
-   <span data-ttu-id="8dd9e-179">R1111: kablo üzerinden sunulan X.509 sertifikaları kaynak makinenin tam etki alanı adını (FQDN) ile eşleşen bir konu adına sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8dd9e-179">R1111: X.509 certificates presented over the wire must have a subject name that matches the fully qualified domain name (FQDN) of the originating machine.</span></span>  
  
-   <span data-ttu-id="8dd9e-180">B1112: DNS başarılı olması için her gönderenin alıcı çifti arasında X.509 konu adı denetimleri için sistemdeki işlevsel olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8dd9e-180">B1112: DNS must be functional between each sender-receiver pair in the system for X.509 subject name checks to succeed.</span></span>  
  
#### <a name="activation-and-registration-binding-configuration"></a><span data-ttu-id="8dd9e-181">Etkinleştirme ve yapılandırma bağlama kayıt</span><span class="sxs-lookup"><span data-stu-id="8dd9e-181">Activation and Registration Binding Configuration</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="8dd9e-182">İstek/yanıt çift yönlü bağıntı bağlamayla HTTPS üzerinden gerektirir.</span><span class="sxs-lookup"><span data-stu-id="8dd9e-182"> requires request/reply duplex binding with correlation over HTTPS.</span></span> <span data-ttu-id="8dd9e-183">(WS-Atomic işlemleri, Bölüm 8 bağıntı ve istek/yanıt iletisi exchange desenleri açıklamalarını hakkında daha fazla bilgi için bkz.)</span><span class="sxs-lookup"><span data-stu-id="8dd9e-183">(For more information about correlation and descriptions of the request/reply message exchange patterns, see WS-Atomic Transaction, Section 8.)</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="8dd9e-184">2PC Protokolü bağlama yapılandırması</span><span class="sxs-lookup"><span data-stu-id="8dd9e-184">2PC Protocol Binding Configuration</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="8dd9e-185">tek yönlü (datagram) iletileri HTTPS üzerinden destekler.</span><span class="sxs-lookup"><span data-stu-id="8dd9e-185"> supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="8dd9e-186">Bağıntı iletileri arasında bir uygulama ayrıntı olarak kalır.</span><span class="sxs-lookup"><span data-stu-id="8dd9e-186">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="8dd9e-187">B2131: Uygulamaları desteklemelidir `wsa:ReferenceParameters` WS-bağıntı elde etmek için adresleme içinde açıklandığı gibi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]'s 2PC iletileri.</span><span class="sxs-lookup"><span data-stu-id="8dd9e-187">B2131: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]’s 2PC messages.</span></span>  
  
### <a name="transaction-manager-mixed-security-binding"></a><span data-ttu-id="8dd9e-188">İşlem Yöneticisi güvenlik bağlama karma</span><span class="sxs-lookup"><span data-stu-id="8dd9e-188">Transaction Manager Mixed Security Binding</span></span>  
 <span data-ttu-id="8dd9e-189">Bu kimlik kurulması amacıyla Web Hizmetleri koordinasyonu verilen belirteç modeli ile birlikte bu kullanımları taşıma güvenliği bağlama bir alternatif (karma mod) olur.</span><span class="sxs-lookup"><span data-stu-id="8dd9e-189">This is an alternate (mixed mode) binding that uses transport security combined with the  WS-Coordination Issued Token model for identity establishment purposes.</span></span>  <span data-ttu-id="8dd9e-190">Etkinleştirme ve kayıt arasında iki bağlamaları farklı yalnızca öğelerdir.</span><span class="sxs-lookup"><span data-stu-id="8dd9e-190">Activation and Registration are the only elements that differ between the two bindings.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="8dd9e-191">HTTPS taşıma yapılandırması</span><span class="sxs-lookup"><span data-stu-id="8dd9e-191">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="8dd9e-192">X.509 sertifikaları işlem yöneticisi kimliğini oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8dd9e-192">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="8dd9e-193">İstemci/sunucu kimlik doğrulaması gerekli değildir ve istemci/sunucu yetkilendirme uygulama ayrıntı olarak kalır.</span><span class="sxs-lookup"><span data-stu-id="8dd9e-193">Client/Server authentication is required, and client/server authorization is left as an implementation detail.</span></span>  
  
#### <a name="activation-message-binding-configuration"></a><span data-ttu-id="8dd9e-194">Etkinleştirme ileti bağlama yapılandırması</span><span class="sxs-lookup"><span data-stu-id="8dd9e-194">Activation Message Binding Configuration</span></span>  
 <span data-ttu-id="8dd9e-195">Genellikle bir uygulama ve onun yerel işlem yöneticisi arasında gerçekleştirildiği için etkinleştirme iletiler birlikte çalışabilirlik genellikle katılma.</span><span class="sxs-lookup"><span data-stu-id="8dd9e-195">Activation Messages usually do not participate in interoperability because they typically occur between an application and its local Transaction Manager.</span></span>  
  
 <span data-ttu-id="8dd9e-196">B1221: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] çift yönlü HTTPS bağlamasını kullanır (açıklanan [Mesajlaşma protokolleri](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) etkinleştirme iletileri için.</span><span class="sxs-lookup"><span data-stu-id="8dd9e-196">B1221: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) for Activation messages.</span></span> <span data-ttu-id="8dd9e-197">İstek ve yanıt iletileri WS adresleme 2004/08 kullanılarak bağıntılı olan.</span><span class="sxs-lookup"><span data-stu-id="8dd9e-197">Request and Reply messages are correlated using WS-Addressing 2004/08.</span></span>  
  
 <span data-ttu-id="8dd9e-198">WS-Atomic işlem belirtimi, Bölüm 8, Ayrıntılar bağıntı ve ileti exchange desenleri hakkında daha fazla açıklar.</span><span class="sxs-lookup"><span data-stu-id="8dd9e-198">WS-Atomic Transaction specification, Section 8, describes further details about correlation and the message exchange patterns.</span></span>  
  
-   <span data-ttu-id="8dd9e-199">R1222: temel alarak bir `CreateCoordinationContext`, düzenleyici dağıtmalı bir `SecurityContextToken` ile ilişkili gizli `STx`.</span><span class="sxs-lookup"><span data-stu-id="8dd9e-199">R1222: Upon receiving a `CreateCoordinationContext`, the Coordinator must issue a `SecurityContextToken` with associated secret `STx`.</span></span> <span data-ttu-id="8dd9e-200">Bu belirteç içinde döndürülen bir `t:IssuedTokens` WS-Trust belirtimine aşağıdaki üstbilgi.</span><span class="sxs-lookup"><span data-stu-id="8dd9e-200">This token is returned inside a `t:IssuedTokens` header following WS-Trust specification.</span></span>  
  
-   <span data-ttu-id="8dd9e-201">R1223: Etkinleştirme var olan bir düzenleme bağlamı içinde ortaya çıkarsa `t:IssuedTokens` üstbilgiyle `SecurityContextToken` var olan ilişkili gerekir içerik akışını `CreateCoordinationContext` ileti.</span><span class="sxs-lookup"><span data-stu-id="8dd9e-201">R1223: If Activation occurs within an existing Coordination Context, the `t:IssuedTokens` header with the `SecurityContextToken` associated with existing Context must flow on the `CreateCoordinationContext` message.</span></span>  
  
 <span data-ttu-id="8dd9e-202">Yeni bir `t:IssuedTokens` giden eklemek için üstbilgi oluşturulacağı `wscoor:CreateCoordinationContextResponse` ileti.</span><span class="sxs-lookup"><span data-stu-id="8dd9e-202">A new `t:IssuedTokens` header should be generated for attaching to the outgoing `wscoor:CreateCoordinationContextResponse` message.</span></span>  
  
#### <a name="registration-message-binding-configuration"></a><span data-ttu-id="8dd9e-203">Kayıt iletisi bağlama yapılandırması</span><span class="sxs-lookup"><span data-stu-id="8dd9e-203">Registration Message Binding Configuration</span></span>  
 <span data-ttu-id="8dd9e-204">B1231: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] çift yönlü HTTPS bağlamasını kullanır (açıklanan [Mesajlaşma protokolleri](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)).</span><span class="sxs-lookup"><span data-stu-id="8dd9e-204">B1231: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)).</span></span> <span data-ttu-id="8dd9e-205">İstek ve yanıt iletileri WS adresleme 2004/08 kullanılarak bağıntılı olan.</span><span class="sxs-lookup"><span data-stu-id="8dd9e-205">Request and Reply messages are correlated using WS-Addressing 2004/08.</span></span>  
  
 <span data-ttu-id="8dd9e-206">WS-AtomicTransaction, Bölüm 8, açıklar daha fazla ayrıntı bağıntı ve ileti exchange desenleri açıklamalarını hakkında.</span><span class="sxs-lookup"><span data-stu-id="8dd9e-206">WS-AtomicTransaction, Section 8, describes further details about correlation and descriptions of the message exchange patterns.</span></span>  
  
 <span data-ttu-id="8dd9e-207">R1232: Giden `wscoor:Register` iletileri kullanmalıdır `IssuedTokenOverTransport` kimlik doğrulama modu açıklanan [güvenlik protokolleri](../../../../docs/framework/wcf/feature-details/security-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="8dd9e-207">R1232: Outgoing `wscoor:Register` messages must use the `IssuedTokenOverTransport` authentication mode described in [Security Protocols](../../../../docs/framework/wcf/feature-details/security-protocols.md).</span></span>  
  
 <span data-ttu-id="8dd9e-208">`wsse:Timestamp` Öğesi kullanılarak imzalanmalıdır `SecurityContextToken``STx` verilmiş.</span><span class="sxs-lookup"><span data-stu-id="8dd9e-208">The `wsse:Timestamp` element must be signed using the `SecurityContextToken``STx` issued.</span></span> <span data-ttu-id="8dd9e-209">Bu imza belirli işlemle ilişkili belirtecinin kanıtını olup işlemde kaydetme katılımcı kimliğini doğrulamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8dd9e-209">This signature is a proof of possession of the token associated with particular transaction and is used to authenticate a participant enlisting in the transaction.</span></span> <span data-ttu-id="8dd9e-210">RegistrationResponse ileti HTTPS üzerinden gönderilir.</span><span class="sxs-lookup"><span data-stu-id="8dd9e-210">The RegistrationResponse message is sent back over HTTPS.</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="8dd9e-211">2PC Protokolü bağlama yapılandırması</span><span class="sxs-lookup"><span data-stu-id="8dd9e-211">2PC Protocol Binding Configuration</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="8dd9e-212">tek yönlü (datagram) iletileri HTTPS üzerinden destekler.</span><span class="sxs-lookup"><span data-stu-id="8dd9e-212"> supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="8dd9e-213">Bağıntı iletileri arasında bir uygulama ayrıntı olarak kalır.</span><span class="sxs-lookup"><span data-stu-id="8dd9e-213">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="8dd9e-214">B2131: Uygulamaları desteklemelidir `wsa:ReferenceParameters` WS-bağıntı elde etmek için adresleme içinde açıklandığı gibi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]'s 2PC iletileri.</span><span class="sxs-lookup"><span data-stu-id="8dd9e-214">B2131: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]’s 2PC messages.</span></span>  
  
## <a name="application-message-exchange"></a><span data-ttu-id="8dd9e-215">Uygulama ileti değişimi</span><span class="sxs-lookup"><span data-stu-id="8dd9e-215">Application Message Exchange</span></span>  
 <span data-ttu-id="8dd9e-216">Uygulamaları bağlama aşağıdaki güvenlik gereksinimlerini karşılayan sürece herhangi belirli uygulama uygulaması iletileri için bu bağlamayı kullanmak boş şunlardır:</span><span class="sxs-lookup"><span data-stu-id="8dd9e-216">Applications are free to use any particular binding for application-to-application messages, as long as the binding meets the following security requirements:</span></span>  
  
-   <span data-ttu-id="8dd9e-217">R2001: Uygulama uygulaması iletileri akış gerekir `t:IssuedTokens` başlığı ile birlikte `CoordinationContext` ileti üstbilgisinde.</span><span class="sxs-lookup"><span data-stu-id="8dd9e-217">R2001: Application-to-application messages must flow the `t:IssuedTokens` header along with the `CoordinationContext` in the header of the message.</span></span>  
  
-   <span data-ttu-id="8dd9e-218">R2002: Bütünlüğü ve gizliliği `t:IssuedToken` sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8dd9e-218">R2002: Integrity and confidentiality of `t:IssuedToken` must be provided.</span></span>  
  
 <span data-ttu-id="8dd9e-219">`CoordinationContext` Üst bilgiyi içeren `wscoor:Identifier`.</span><span class="sxs-lookup"><span data-stu-id="8dd9e-219">The `CoordinationContext` header contains `wscoor:Identifier`.</span></span> <span data-ttu-id="8dd9e-220">While tanımını `xsd:AnyURI` mutlak veya göreli URI, kullanılmasına [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] yalnızca destekler `wscoor:Identifiers`, mutlak URI olduğu.</span><span class="sxs-lookup"><span data-stu-id="8dd9e-220">While the definition of `xsd:AnyURI` allows the use of both absolute and relative URIs, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] supports only `wscoor:Identifiers`, which are absolute URIs.</span></span>  
  
 <span data-ttu-id="8dd9e-221">Varsa `wscoor:Identifier` , `wscoor:CoordinationContext` göreli bir URI hataları döndürülecek gelen işlem [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hizmetleri.</span><span class="sxs-lookup"><span data-stu-id="8dd9e-221">If the `wscoor:Identifier` of the `wscoor:CoordinationContext` is a relative URI, faults will be returned from transactional [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services.</span></span>  
  
## <a name="message-examples"></a><span data-ttu-id="8dd9e-222">İleti örnekleri</span><span class="sxs-lookup"><span data-stu-id="8dd9e-222">Message Examples</span></span>  
  
### <a name="createcoordinationcontext-requestresponse-messages"></a><span data-ttu-id="8dd9e-223">CreateCoordinationContext istek/yanıt iletilerini</span><span class="sxs-lookup"><span data-stu-id="8dd9e-223">CreateCoordinationContext Request/Response Messages</span></span>  
 <span data-ttu-id="8dd9e-224">Aşağıdaki ileti, bir istek/yanıt yol izler.</span><span class="sxs-lookup"><span data-stu-id="8dd9e-224">The following messages follow a request/response pattern.</span></span>  
  
#### <a name="createcoordinationcontext"></a><span data-ttu-id="8dd9e-225">CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="8dd9e-225">CreateCoordinationContext</span></span>  
  
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
  
#### <a name="createcoordinationcontextresponse"></a><span data-ttu-id="8dd9e-226">CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="8dd9e-226">CreateCoordinationContextResponse</span></span>  
  
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
  
### <a name="registration-messages"></a><span data-ttu-id="8dd9e-227">Kayıt iletileri</span><span class="sxs-lookup"><span data-stu-id="8dd9e-227">Registration Messages</span></span>  
 <span data-ttu-id="8dd9e-228">Aşağıdaki iletileri kayıt iletileri edilir.</span><span class="sxs-lookup"><span data-stu-id="8dd9e-228">The following messages are registration messages.</span></span>  
  
#### <a name="register"></a><span data-ttu-id="8dd9e-229">Yazmaç</span><span class="sxs-lookup"><span data-stu-id="8dd9e-229">Register</span></span>  
  
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
  
#### <a name="register-response"></a><span data-ttu-id="8dd9e-230">Yanıt kaydetme</span><span class="sxs-lookup"><span data-stu-id="8dd9e-230">Register Response</span></span>  
  
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
  
### <a name="two-phase-commit-protocol-messages"></a><span data-ttu-id="8dd9e-231">İki aşama yürütme Protokolü iletileri</span><span class="sxs-lookup"><span data-stu-id="8dd9e-231">Two Phase Commit Protocol Messages</span></span>  
 <span data-ttu-id="8dd9e-232">Aşağıdaki ileti iki aşamalı kayıt (2PC) protokolüne ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="8dd9e-232">The following message relates to the two-phase commit (2PC) protocol.</span></span>  
  
#### <a name="commit"></a><span data-ttu-id="8dd9e-233">Tamamlama</span><span class="sxs-lookup"><span data-stu-id="8dd9e-233">Commit</span></span>  
  
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
  
### <a name="application-messages"></a><span data-ttu-id="8dd9e-234">Uygulama iletileri</span><span class="sxs-lookup"><span data-stu-id="8dd9e-234">Application Messages</span></span>  
 <span data-ttu-id="8dd9e-235">Aşağıdaki iletileri uygulama iletileri edilir.</span><span class="sxs-lookup"><span data-stu-id="8dd9e-235">The following messages are application messages.</span></span>  
  
#### <a name="application-message-request"></a><span data-ttu-id="8dd9e-236">Uygulama iletiyi-isteği</span><span class="sxs-lookup"><span data-stu-id="8dd9e-236">Application message-Request</span></span>  
  
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

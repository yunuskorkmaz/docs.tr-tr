---
title: İşlem Protokolleri sürüm 1.0
ms.date: 03/30/2017
ms.assetid: 034679af-0002-402e-98a8-ef73dcd71bb6
ms.openlocfilehash: 5ca0210c15afd6a3fc2e05bc3b9016a1fcd929b7
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460279"
---
# <a name="transaction-protocols-version-10"></a><span data-ttu-id="faf16-102">İşlem Protokolleri sürüm 1.0</span><span class="sxs-lookup"><span data-stu-id="faf16-102">Transaction Protocols version 1.0</span></span>
<span data-ttu-id="faf16-103">Windows Communication Foundation (WCF) sürüm 1, WS Atomik Işlem ve WS-koordinasyon protokollerinin 1,0 sürümünü uygular.</span><span class="sxs-lookup"><span data-stu-id="faf16-103">Windows Communication Foundation (WCF) version 1 implements version 1.0 of the WS-Atomic Transaction and WS-Coordination protocols.</span></span> <span data-ttu-id="faf16-104">Sürüm 1,1 hakkında daha fazla bilgi için bkz. [Işlem protokolleri](../../../../docs/framework/wcf/feature-details/transaction-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="faf16-104">For more information about version 1.1, see [Transaction Protocols](../../../../docs/framework/wcf/feature-details/transaction-protocols.md).</span></span>  
  
|<span data-ttu-id="faf16-105">Belirtim/belge</span><span class="sxs-lookup"><span data-stu-id="faf16-105">Specification/Document</span></span>|<span data-ttu-id="faf16-106">Bağlantı</span><span class="sxs-lookup"><span data-stu-id="faf16-106">Link</span></span>|  
|-----------------------------|----------|  
|<span data-ttu-id="faf16-107">WS koordinasyonu</span><span class="sxs-lookup"><span data-stu-id="faf16-107">WS-Coordination</span></span>|<https://specs.xmlsoap.org/ws/2004/10/wscoor/wscoor.pdf>|  
|<span data-ttu-id="faf16-108">WS-AtomicTransaction</span><span class="sxs-lookup"><span data-stu-id="faf16-108">WS-AtomicTransaction</span></span>|<https://specs.xmlsoap.org/ws/2004/10/wsat/wsat.pdf>|  
  
 <span data-ttu-id="faf16-109">Bu protokol belirtimlerinde birlikte çalışabilirlik iki düzeyde gereklidir: uygulamalar arasında ve işlem yöneticileri arasında (aşağıdaki şekle bakın).</span><span class="sxs-lookup"><span data-stu-id="faf16-109">Interoperability on these protocol specifications is required at two levels: between applications and between transaction managers (see the following figure).</span></span> <span data-ttu-id="faf16-110">Özellikler, her iki birlikte çalışabilirlik düzeyi için İleti biçimlerini ve ileti değişimini harika ayrıntılarla anlatmaktadır.</span><span class="sxs-lookup"><span data-stu-id="faf16-110">Specifications describe in great detail the message formats and message exchange for both interoperability levels.</span></span> <span data-ttu-id="faf16-111">Uygulamadan uygulamaya Exchange 'e yönelik belirli güvenlik, güvenilirlik ve kodlamalar, düzenli uygulama alışverişi için olduğu gibi uygulanır.</span><span class="sxs-lookup"><span data-stu-id="faf16-111">Certain security, reliability, and encodings for application-to-application exchange apply as they do for regular application exchange.</span></span> <span data-ttu-id="faf16-112">Ancak, işlem yöneticileri arasında başarılı birlikte çalışabilirlik, genellikle kullanıcı tarafından yapılandırılmadığı için belirli bir bağlamada anlaşma gerektirir.</span><span class="sxs-lookup"><span data-stu-id="faf16-112">However, successful interoperability between transaction managers requires agreement on the particular binding, because it is usually not configured by the user.</span></span>  
  
 <span data-ttu-id="faf16-113">Bu konu, güvenlik ile WS Atomik Işlem (WS-AT) belirtiminin bir oluşumunu açıklar ve işlem yöneticileri arasında iletişim için kullanılan güvenli bağlamayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="faf16-113">This topic describes a composition of the WS-Atomic Transaction (WS-AT) specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="faf16-114">Bu belgede açıklanan yaklaşım IBM, ıLONA, Sun Microsystems ve diğerleri dahil olmak üzere WS-AT ve WS-koordinasyon uygulamalarıyla başarıyla test edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="faf16-114">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination including IBM, IONA, Sun Microsystems, and others.</span></span>  
  
 <span data-ttu-id="faf16-115">Aşağıdaki şekilde iki işlem yöneticisi, Işlem Yöneticisi 1 ve Işlem yöneticisi 2 ile iki uygulama, uygulama 1 ve uygulama 2 arasındaki birlikte çalışabilirlik gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="faf16-115">The following figure depicts the interoperability between two transaction managers, Transaction Manager 1 and Transaction Manager 2, and two applications, Application 1 and Application 2:</span></span>  
  
 ![İşlem yöneticileri arasındaki etkileşimi gösteren ekran görüntüsü.](./media/transaction-protocols/transaction-managers-flow.gif)  
  
 <span data-ttu-id="faf16-117">Tek bir başlatıcı (I) ve bir katılımcı (P) ile tipik bir WS-koordinasyon/WS-Atomik Işlem senaryosu düşünün.</span><span class="sxs-lookup"><span data-stu-id="faf16-117">Consider a typical WS-Coordination/WS-Atomic Transaction scenario with one Initiator (I) and one Participant (P).</span></span> <span data-ttu-id="faf16-118">Hem Başlatıcı hem de katılımcı Işlem yöneticilerine (sırasıyla ıSTREAM ve PTM) sahiptir.</span><span class="sxs-lookup"><span data-stu-id="faf16-118">Both Initiator and Participant have Transaction Managers, (ITM and PTM, respectively).</span></span> <span data-ttu-id="faf16-119">İki aşamalı yürütmeye bu konuda 2PC adı verilir.</span><span class="sxs-lookup"><span data-stu-id="faf16-119">Two-phase commit is referred to as 2PC in this topic.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="faf16-120">1. Createkoordinattioncontext</span><span class="sxs-lookup"><span data-stu-id="faf16-120">1. CreateCoordinationContext</span></span>|<span data-ttu-id="faf16-121">12. uygulama Iletisi yanıtı</span><span class="sxs-lookup"><span data-stu-id="faf16-121">12. Application Message Response</span></span>|  
|<span data-ttu-id="faf16-122">2. Createkoordinattioncontextresponse</span><span class="sxs-lookup"><span data-stu-id="faf16-122">2. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="faf16-123">13. COMMIT (tamamlama)</span><span class="sxs-lookup"><span data-stu-id="faf16-123">13. Commit (Completion)</span></span>|  
|<span data-ttu-id="faf16-124">3. yazmaç (tamamlama)</span><span class="sxs-lookup"><span data-stu-id="faf16-124">3. Register (Completion)</span></span>|<span data-ttu-id="faf16-125">14. Prepare (2PC)</span><span class="sxs-lookup"><span data-stu-id="faf16-125">14. Prepare (2PC)</span></span>|  
|<span data-ttu-id="faf16-126">4. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="faf16-126">4. RegisterResponse</span></span>|<span data-ttu-id="faf16-127">15. hazırlama (2PC)</span><span class="sxs-lookup"><span data-stu-id="faf16-127">15. Prepare (2PC)</span></span>|  
|<span data-ttu-id="faf16-128">5. uygulama Iletisi</span><span class="sxs-lookup"><span data-stu-id="faf16-128">5. Application Message</span></span>|<span data-ttu-id="faf16-129">16. hazırlandı (2PC)</span><span class="sxs-lookup"><span data-stu-id="faf16-129">16. Prepared (2PC)</span></span>|  
|<span data-ttu-id="faf16-130">6. Createkoordinattioncontext WITH bağlamı</span><span class="sxs-lookup"><span data-stu-id="faf16-130">6. CreateCoordinationContext with Context</span></span>|<span data-ttu-id="faf16-131">17. hazırlandı (2PC)</span><span class="sxs-lookup"><span data-stu-id="faf16-131">17. Prepared (2PC)</span></span>|  
|<span data-ttu-id="faf16-132">7. Kayıt (dayanıklı)</span><span class="sxs-lookup"><span data-stu-id="faf16-132">7. Register (Durable)</span></span>|<span data-ttu-id="faf16-133">18. taahhüt (tamamlama)</span><span class="sxs-lookup"><span data-stu-id="faf16-133">18. Committed (Completion)</span></span>|  
|<span data-ttu-id="faf16-134">8. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="faf16-134">8. RegisterResponse</span></span>|<span data-ttu-id="faf16-135">19. COMMIT (2PC)</span><span class="sxs-lookup"><span data-stu-id="faf16-135">19. Commit (2PC)</span></span>|  
|<span data-ttu-id="faf16-136">9. Createkoordinattioncontextresponse</span><span class="sxs-lookup"><span data-stu-id="faf16-136">9. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="faf16-137">20. COMMIT (2PC)</span><span class="sxs-lookup"><span data-stu-id="faf16-137">20. Commit (2PC)</span></span>|  
|<span data-ttu-id="faf16-138">10. Kayıt (dayanıklı)</span><span class="sxs-lookup"><span data-stu-id="faf16-138">10. Register (Durable)</span></span>|<span data-ttu-id="faf16-139">21. taahhüt (2PC)</span><span class="sxs-lookup"><span data-stu-id="faf16-139">21. Committed (2PC)</span></span>|  
|<span data-ttu-id="faf16-140">11. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="faf16-140">11. RegisterResponse</span></span>|<span data-ttu-id="faf16-141">22. taahhüt (2PC)</span><span class="sxs-lookup"><span data-stu-id="faf16-141">22. Committed (2PC)</span></span>|  
  
 <span data-ttu-id="faf16-142">Bu belge, güvenlik ile WS-AtomicTransaction belirtiminin bir oluşumunu açıklar ve işlem yöneticileri arasında iletişim için kullanılan güvenli bağlamayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="faf16-142">This document describes a composition of the WS-AtomicTransaction specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="faf16-143">Bu belgede açıklanan yaklaşım, WS-AT ve WS-koordinasyonun diğer uygulamalarıyla başarıyla test edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="faf16-143">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination.</span></span>  
  
 <span data-ttu-id="faf16-144">Şekil ve tablo, güvenlik açısından görüş açısından dört ileti sınıfını gösterir:</span><span class="sxs-lookup"><span data-stu-id="faf16-144">The figure and table illustrate four classes of messages from the viewpoint of security:</span></span>  
  
- <span data-ttu-id="faf16-145">Etkinleştirme iletileri (Createkoordinattioncontext ve Createkoordinattioncontextresponse).</span><span class="sxs-lookup"><span data-stu-id="faf16-145">Activation messages (CreateCoordinationContext and CreateCoordinationContextResponse).</span></span>  
  
- <span data-ttu-id="faf16-146">Kayıt iletileri (Register ve RegisterResponse)</span><span class="sxs-lookup"><span data-stu-id="faf16-146">Registration messages (Register and RegisterResponse)</span></span>  
  
- <span data-ttu-id="faf16-147">Protokol iletileri (hazırlama, geri alma, tamamlama, Iptal etme vb.).</span><span class="sxs-lookup"><span data-stu-id="faf16-147">Protocol messages (Prepare, Rollback, Commit, Aborted, and so on).</span></span>  
  
- <span data-ttu-id="faf16-148">Uygulama iletileri.</span><span class="sxs-lookup"><span data-stu-id="faf16-148">Application messages.</span></span>  
  
 <span data-ttu-id="faf16-149">İlk üç ileti sınıfı, Işlem yöneticisi iletileri olarak kabul edilir ve bağlama yapılandırması bu konunun ilerleyen kısımlarında "uygulama Ileti değişimi" bölümünde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="faf16-149">The first three message classes are considered Transaction Manager messages and their binding configuration is described in the "Application Message Exchange" later in this topic.</span></span> <span data-ttu-id="faf16-150">Dördüncü ileti sınıfı, uygulama iletileri için uygulamadır ve bu konunun ilerleyen kısımlarında "Ileti örnekleri" bölümünde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="faf16-150">The fourth class of message is application to application messages and is described in the "Message Examples" section later in this topic.</span></span> <span data-ttu-id="faf16-151">Bu bölümde, bu sınıfların her biri için WCF tarafından kullanılan protokol bağlamaları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="faf16-151">This section describes the protocol bindings used for each of these classes by WCF.</span></span>  
  
 <span data-ttu-id="faf16-152">Aşağıdaki XML ad alanları ve ilişkili ön ekler Bu belge boyunca kullanılır.</span><span class="sxs-lookup"><span data-stu-id="faf16-152">The following XML Namespaces and associated prefixes are used throughout this document.</span></span>  
  
|<span data-ttu-id="faf16-153">koy</span><span class="sxs-lookup"><span data-stu-id="faf16-153">Prefix</span></span>|<span data-ttu-id="faf16-154">Ad alanı URI 'SI</span><span class="sxs-lookup"><span data-stu-id="faf16-154">Namespace URI</span></span>|  
|------------|-------------------|  
|<span data-ttu-id="faf16-155">s11</span><span class="sxs-lookup"><span data-stu-id="faf16-155">s11</span></span>|http://schemas.xmlsoap.org/soap/envelope|  
|<span data-ttu-id="faf16-156">WSA</span><span class="sxs-lookup"><span data-stu-id="faf16-156">wsa</span></span>|http://www.w3.org/2004/08/addressing|  
|<span data-ttu-id="faf16-157">wscoor</span><span class="sxs-lookup"><span data-stu-id="faf16-157">wscoor</span></span>|http://schemas.xmlsoap.org/ws/2004/10/wscoor|  
|<span data-ttu-id="faf16-158">WSAT</span><span class="sxs-lookup"><span data-stu-id="faf16-158">wsat</span></span>|http://schemas.xmlsoap.org/ws/2004/10/wsat|  
|<span data-ttu-id="faf16-159">t</span><span class="sxs-lookup"><span data-stu-id="faf16-159">t</span></span>|http://schemas.xmlsoap.org/ws/2005/02/trust|  
|<span data-ttu-id="faf16-160">Gelirken</span><span class="sxs-lookup"><span data-stu-id="faf16-160">o</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd|  
|<span data-ttu-id="faf16-161">yapamadı</span><span class="sxs-lookup"><span data-stu-id="faf16-161">xsd</span></span>|http://www.w3.org/2001/XMLSchema|  
  
## <a name="transaction-manager-bindings"></a><span data-ttu-id="faf16-162">İşlem Yöneticisi bağlamaları</span><span class="sxs-lookup"><span data-stu-id="faf16-162">Transaction Manager Bindings</span></span>  
 <span data-ttu-id="faf16-163">R1001: Işlem yöneticileri WS-Atomik Işlem ve WS-koordinasyon ileti alışverişi için SOAP 1,1 ve WS-Addressing 2004/08 kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="faf16-163">R1001: Transaction Managers must use SOAP 1.1 and WS-Addressing 2004/08 for WS-Atomic Transaction and WS-Coordination message exchanges.</span></span>  
  
 <span data-ttu-id="faf16-164">Uygulama iletileri bu bağlamalarla sınırlı değildir ve daha sonra açıklanır.</span><span class="sxs-lookup"><span data-stu-id="faf16-164">Application messages are not constrained to these bindings and are described later.</span></span>  
  
### <a name="transaction-manager-https-binding"></a><span data-ttu-id="faf16-165">İşlem Yöneticisi HTTPS bağlama</span><span class="sxs-lookup"><span data-stu-id="faf16-165">Transaction Manager HTTPS Binding</span></span>  
 <span data-ttu-id="faf16-166">İşlem Yöneticisi HTTPS bağlaması, güvenlik elde etmek ve işlem ağacındaki her gönderici alıcısı çifti arasında güven sağlamak için yalnızca taşıma güvenliğine dayanır.</span><span class="sxs-lookup"><span data-stu-id="faf16-166">The transaction manager HTTPS binding relies solely on transport security to achieve security and establish trust between each sender-receiver pair in the transaction tree.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="faf16-167">HTTPS aktarım yapılandırması</span><span class="sxs-lookup"><span data-stu-id="faf16-167">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="faf16-168">X. 509.440 sertifikaları, Işlem yöneticisi kimliğini oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="faf16-168">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="faf16-169">İstemci/sunucu kimlik doğrulaması gereklidir ve istemci/sunucu yetkilendirmesi uygulama ayrıntısı olarak bırakılır:</span><span class="sxs-lookup"><span data-stu-id="faf16-169">Client/server authentication is required, and client/server authorization is left as an implementation detail:</span></span>  
  
- <span data-ttu-id="faf16-170">R1111: tel üzerinden sunulan X. 509.440 sertifikalarının, kaynak makinenin tam etki alanı adı (FQDN) ile eşleşen bir konu adı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="faf16-170">R1111: X.509 certificates presented over the wire must have a subject name that matches the fully qualified domain name (FQDN) of the originating machine.</span></span>  
  
- <span data-ttu-id="faf16-171">B1112: X. 509.440 konu adı denetimlerinin başarılı olması için sistemdeki her gönderici alıcısı çifti arasında DNS işlevsel olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="faf16-171">B1112: DNS must be functional between each sender-receiver pair in the system for X.509 subject name checks to succeed.</span></span>  
  
#### <a name="activation-and-registration-binding-configuration"></a><span data-ttu-id="faf16-172">Etkinleştirme ve kayıt bağlama yapılandırması</span><span class="sxs-lookup"><span data-stu-id="faf16-172">Activation and Registration Binding Configuration</span></span>  
 <span data-ttu-id="faf16-173">WCF, HTTPS üzerinden bağıntı ile istek/yanıt çift yönlü bağlamayı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="faf16-173">WCF requires request/reply duplex binding with correlation over HTTPS.</span></span> <span data-ttu-id="faf16-174">(İstek/yanıt iletisi değişim desenlerinin bağıntısı ve açıklamaları hakkında daha fazla bilgi için bkz. WS Atomik Işlem, Bölüm 8.)</span><span class="sxs-lookup"><span data-stu-id="faf16-174">(For more information about correlation and descriptions of the request/reply message exchange patterns, see WS-Atomic Transaction, Section 8.)</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="faf16-175">2PC protokol bağlama yapılandırması</span><span class="sxs-lookup"><span data-stu-id="faf16-175">2PC Protocol Binding Configuration</span></span>  
 <span data-ttu-id="faf16-176">WCF, HTTPS üzerinden tek yönlü (Datagram) iletileri destekler.</span><span class="sxs-lookup"><span data-stu-id="faf16-176">WCF supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="faf16-177">İletiler arasındaki bağıntı uygulama ayrıntısı olarak kalır.</span><span class="sxs-lookup"><span data-stu-id="faf16-177">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="faf16-178">B2131: uygulamalar, WCF 2PC iletilerinin bağıntısını elde etmek için WS-Addressing bölümünde açıklandığı gibi `wsa:ReferenceParameters` desteklemelidir.</span><span class="sxs-lookup"><span data-stu-id="faf16-178">B2131: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of WCF’s 2PC messages.</span></span>  
  
### <a name="transaction-manager-mixed-security-binding"></a><span data-ttu-id="faf16-179">Transaction Manager karışık güvenlik bağlama</span><span class="sxs-lookup"><span data-stu-id="faf16-179">Transaction Manager Mixed Security Binding</span></span>  
 <span data-ttu-id="faf16-180">Bu, kimlik oluşturma amacıyla WS koordinasyonu verilen belirteç modeliyle birleştirilmiş aktarım güvenliği kullanan alternatif (karışık mod) bağlamadır.</span><span class="sxs-lookup"><span data-stu-id="faf16-180">This is an alternate (mixed mode) binding that uses transport security combined with the  WS-Coordination Issued Token model for identity establishment purposes.</span></span>  <span data-ttu-id="faf16-181">Etkinleştirme ve kayıt, iki bağlama arasında farklı olan tek öğelerdir.</span><span class="sxs-lookup"><span data-stu-id="faf16-181">Activation and Registration are the only elements that differ between the two bindings.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="faf16-182">HTTPS aktarım yapılandırması</span><span class="sxs-lookup"><span data-stu-id="faf16-182">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="faf16-183">X. 509.440 sertifikaları, Işlem yöneticisi kimliğini oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="faf16-183">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="faf16-184">İstemci/sunucu kimlik doğrulaması gereklidir ve istemci/sunucu yetkilendirmesi uygulama ayrıntısı olarak bırakılır.</span><span class="sxs-lookup"><span data-stu-id="faf16-184">Client/Server authentication is required, and client/server authorization is left as an implementation detail.</span></span>  
  
#### <a name="activation-message-binding-configuration"></a><span data-ttu-id="faf16-185">Etkinleştirme Iletisi bağlama yapılandırması</span><span class="sxs-lookup"><span data-stu-id="faf16-185">Activation Message Binding Configuration</span></span>  
 <span data-ttu-id="faf16-186">Etkinleştirme Iletileri genellikle bir uygulama ve kendi yerel Işlem yöneticisi arasında gerçekleştiğinden birlikte çalışabilirliğe katılmaz.</span><span class="sxs-lookup"><span data-stu-id="faf16-186">Activation Messages usually do not participate in interoperability because they typically occur between an application and its local Transaction Manager.</span></span>  
  
 <span data-ttu-id="faf16-187">B1221: WCF etkinleştirme iletileri için çift yönlü HTTPS bağlamasını ( [mesajlaşma protokollerinde](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)açıklanmıştır) kullanır.</span><span class="sxs-lookup"><span data-stu-id="faf16-187">B1221: WCF uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) for Activation messages.</span></span> <span data-ttu-id="faf16-188">İstek ve yanıt iletisi, WS-Addressing 2004/08 kullanılarak bağıntılı.</span><span class="sxs-lookup"><span data-stu-id="faf16-188">Request and Reply messages are correlated using WS-Addressing 2004/08.</span></span>  
  
 <span data-ttu-id="faf16-189">WS Atomik Işlem belirtimi, Bölüm 8, bağıntı ve ileti değişimi desenleri hakkında daha fazla ayrıntı açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="faf16-189">WS-Atomic Transaction specification, Section 8, describes further details about correlation and the message exchange patterns.</span></span>  
  
- <span data-ttu-id="faf16-190">R1222: `CreateCoordinationContext`aldıktan sonra, düzenleyicinin ilişkili gizli dizi `STx`bir `SecurityContextToken` vermesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="faf16-190">R1222: Upon receiving a `CreateCoordinationContext`, the Coordinator must issue a `SecurityContextToken` with associated secret `STx`.</span></span> <span data-ttu-id="faf16-191">Bu belirteç, WS-Trust belirtimindeki bir `t:IssuedTokens` üst bilgisi içinde döndürülür.</span><span class="sxs-lookup"><span data-stu-id="faf16-191">This token is returned inside a `t:IssuedTokens` header following WS-Trust specification.</span></span>  
  
- <span data-ttu-id="faf16-192">R1223: etkinleştirme mevcut bir düzenleme bağlamında gerçekleşirse, var olan bağlamla ilişkili `SecurityContextToken` olan `t:IssuedTokens` üst bilgisinin `CreateCoordinationContext` iletisinde akışı gerekir.</span><span class="sxs-lookup"><span data-stu-id="faf16-192">R1223: If Activation occurs within an existing Coordination Context, the `t:IssuedTokens` header with the `SecurityContextToken` associated with existing Context must flow on the `CreateCoordinationContext` message.</span></span>  
  
 <span data-ttu-id="faf16-193">Giden `wscoor:CreateCoordinationContextResponse` iletisine eklemek için yeni bir `t:IssuedTokens` üst bilgisi oluşturulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="faf16-193">A new `t:IssuedTokens` header should be generated for attaching to the outgoing `wscoor:CreateCoordinationContextResponse` message.</span></span>  
  
#### <a name="registration-message-binding-configuration"></a><span data-ttu-id="faf16-194">Kayıt Iletisi bağlama yapılandırması</span><span class="sxs-lookup"><span data-stu-id="faf16-194">Registration Message Binding Configuration</span></span>  
 <span data-ttu-id="faf16-195">B1231: WCF çift yönlü HTTPS bağlamasını kullanır ( [mesajlaşma protokollerinde](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)açıklanmıştır).</span><span class="sxs-lookup"><span data-stu-id="faf16-195">B1231: WCF uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)).</span></span> <span data-ttu-id="faf16-196">İstek ve yanıt iletisi, WS-Addressing 2004/08 kullanılarak bağıntılı.</span><span class="sxs-lookup"><span data-stu-id="faf16-196">Request and Reply messages are correlated using WS-Addressing 2004/08.</span></span>  
  
 <span data-ttu-id="faf16-197">WS-AtomicTransaction, Bölüm 8, ileti değişim desenlerinin bağıntı ve açıklamaları hakkında daha fazla ayrıntı açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="faf16-197">WS-AtomicTransaction, Section 8, describes further details about correlation and descriptions of the message exchange patterns.</span></span>  
  
 <span data-ttu-id="faf16-198">R1232: giden `wscoor:Register` iletileri, [Güvenlik protokollerinde](../../../../docs/framework/wcf/feature-details/security-protocols.md)açıklanan `IssuedTokenOverTransport` kimlik doğrulama modunu kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="faf16-198">R1232: Outgoing `wscoor:Register` messages must use the `IssuedTokenOverTransport` authentication mode described in [Security Protocols](../../../../docs/framework/wcf/feature-details/security-protocols.md).</span></span>  
  
 <span data-ttu-id="faf16-199">`wsse:Timestamp` öğesi, verilen `SecurityContextToken STx` kullanılarak imzalanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="faf16-199">The `wsse:Timestamp` element must be signed using the `SecurityContextToken STx` issued.</span></span> <span data-ttu-id="faf16-200">Bu imza, belirli bir işlemle ilişkili belirtecin bir kanıtıdır ve işlemde bir katılımcı listesini doğrulamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="faf16-200">This signature is a proof of possession of the token associated with particular transaction and is used to authenticate a participant enlisting in the transaction.</span></span> <span data-ttu-id="faf16-201">RegistrationResponse iletisi HTTPS üzerinden geri gönderilir.</span><span class="sxs-lookup"><span data-stu-id="faf16-201">The RegistrationResponse message is sent back over HTTPS.</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="faf16-202">2PC protokol bağlama yapılandırması</span><span class="sxs-lookup"><span data-stu-id="faf16-202">2PC Protocol Binding Configuration</span></span>  
 <span data-ttu-id="faf16-203">WCF, HTTPS üzerinden tek yönlü (Datagram) iletileri destekler.</span><span class="sxs-lookup"><span data-stu-id="faf16-203">WCF supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="faf16-204">İletiler arasındaki bağıntı uygulama ayrıntısı olarak kalır.</span><span class="sxs-lookup"><span data-stu-id="faf16-204">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="faf16-205">B2131: uygulamalar, WCF 2PC iletilerinin bağıntısını elde etmek için WS-Addressing bölümünde açıklandığı gibi `wsa:ReferenceParameters` desteklemelidir.</span><span class="sxs-lookup"><span data-stu-id="faf16-205">B2131: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of WCF’s 2PC messages.</span></span>  
  
## <a name="application-message-exchange"></a><span data-ttu-id="faf16-206">Uygulama Iletisi değişimi</span><span class="sxs-lookup"><span data-stu-id="faf16-206">Application Message Exchange</span></span>  
 <span data-ttu-id="faf16-207">Bağlama aşağıdaki güvenlik gereksinimlerini karşıladığı sürece, uygulamalar uygulamadan uygulamaya iletiler için herhangi bir bağlamayı kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="faf16-207">Applications are free to use any particular binding for application-to-application messages, as long as the binding meets the following security requirements:</span></span>  
  
- <span data-ttu-id="faf16-208">R2001: uygulamadan uygulamaya iletileri ileti üstbilgisindeki `CoordinationContext` birlikte `t:IssuedTokens` üst bilgisini Flow olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="faf16-208">R2001: Application-to-application messages must flow the `t:IssuedTokens` header along with the `CoordinationContext` in the header of the message.</span></span>  
  
- <span data-ttu-id="faf16-209">R2002: `t:IssuedToken` bütünlük ve gizliliği sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="faf16-209">R2002: Integrity and confidentiality of `t:IssuedToken` must be provided.</span></span>  
  
 <span data-ttu-id="faf16-210">`CoordinationContext` üst bilgisi `wscoor:Identifier`içerir.</span><span class="sxs-lookup"><span data-stu-id="faf16-210">The `CoordinationContext` header contains `wscoor:Identifier`.</span></span> <span data-ttu-id="faf16-211">`xsd:AnyURI` tanımı hem mutlak hem de göreli URI 'lerin kullanılmasına izin verdiğinden, WCF yalnızca, mutlak URI 'Ler olan `wscoor:Identifiers`destekler.</span><span class="sxs-lookup"><span data-stu-id="faf16-211">While the definition of `xsd:AnyURI` allows the use of both absolute and relative URIs, WCF supports only `wscoor:Identifiers`, which are absolute URIs.</span></span>  
  
 <span data-ttu-id="faf16-212">`wscoor:CoordinationContext` `wscoor:Identifier` göreli bir URI ise, hatalar işlem WCF hizmetlerinden döndürülür.</span><span class="sxs-lookup"><span data-stu-id="faf16-212">If the `wscoor:Identifier` of the `wscoor:CoordinationContext` is a relative URI, faults will be returned from transactional WCF services.</span></span>  
  
## <a name="message-examples"></a><span data-ttu-id="faf16-213">İleti örnekleri</span><span class="sxs-lookup"><span data-stu-id="faf16-213">Message Examples</span></span>  
  
### <a name="createcoordinationcontext-requestresponse-messages"></a><span data-ttu-id="faf16-214">Createkoordinattioncontext Isteği/yanıt Iletileri</span><span class="sxs-lookup"><span data-stu-id="faf16-214">CreateCoordinationContext Request/Response Messages</span></span>  
 <span data-ttu-id="faf16-215">Aşağıdaki iletiler bir istek/yanıt modelini izler.</span><span class="sxs-lookup"><span data-stu-id="faf16-215">The following messages follow a request/response pattern.</span></span>  
  
#### <a name="createcoordinationcontext"></a><span data-ttu-id="faf16-216">Createkoordinattioncontext</span><span class="sxs-lookup"><span data-stu-id="faf16-216">CreateCoordinationContext</span></span>  
  
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
  
#### <a name="createcoordinationcontextresponse"></a><span data-ttu-id="faf16-217">Createkoordinattioncontextresponse</span><span class="sxs-lookup"><span data-stu-id="faf16-217">CreateCoordinationContextResponse</span></span>  
  
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
  
### <a name="registration-messages"></a><span data-ttu-id="faf16-218">Kayıt Iletileri</span><span class="sxs-lookup"><span data-stu-id="faf16-218">Registration Messages</span></span>  
 <span data-ttu-id="faf16-219">Aşağıdaki iletiler kayıt mesajlardır.</span><span class="sxs-lookup"><span data-stu-id="faf16-219">The following messages are registration messages.</span></span>  
  
#### <a name="register"></a><span data-ttu-id="faf16-220">Yazmaç</span><span class="sxs-lookup"><span data-stu-id="faf16-220">Register</span></span>  
  
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
  
#### <a name="register-response"></a><span data-ttu-id="faf16-221">Yanıtı Kaydet</span><span class="sxs-lookup"><span data-stu-id="faf16-221">Register Response</span></span>  
  
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
  
### <a name="two-phase-commit-protocol-messages"></a><span data-ttu-id="faf16-222">İki aşamalı tamamlama Protokolü Iletisi</span><span class="sxs-lookup"><span data-stu-id="faf16-222">Two Phase Commit Protocol Messages</span></span>  
 <span data-ttu-id="faf16-223">Aşağıdaki ileti, iki aşamalı tamamlama (2PC) protokolüyle ilişkilidir.</span><span class="sxs-lookup"><span data-stu-id="faf16-223">The following message relates to the two-phase commit (2PC) protocol.</span></span>  
  
#### <a name="commit"></a><span data-ttu-id="faf16-224">Uygulayın</span><span class="sxs-lookup"><span data-stu-id="faf16-224">Commit</span></span>  
  
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
  
### <a name="application-messages"></a><span data-ttu-id="faf16-225">Uygulama Iletileri</span><span class="sxs-lookup"><span data-stu-id="faf16-225">Application Messages</span></span>  
 <span data-ttu-id="faf16-226">Aşağıdaki iletiler uygulama mesajlardır.</span><span class="sxs-lookup"><span data-stu-id="faf16-226">The following messages are application messages.</span></span>  
  
#### <a name="application-message-request"></a><span data-ttu-id="faf16-227">Uygulama iletisi-Istek</span><span class="sxs-lookup"><span data-stu-id="faf16-227">Application message-Request</span></span>  
  
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

---
title: İşlem Protokolleri
ms.date: 03/30/2017
ms.assetid: 2820b0ec-2f32-430c-b299-1f0e95e1f2dc
ms.openlocfilehash: 32c5da24eb7b23145d79c33a9ca1f5e5bcc22c06
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742719"
---
# <a name="transaction-protocols"></a><span data-ttu-id="2b195-102">İşlem Protokolleri</span><span class="sxs-lookup"><span data-stu-id="2b195-102">Transaction Protocols</span></span>
<span data-ttu-id="2b195-103">Windows Communication Foundation (WCF), WS Atomik Işlem ve WS-koordinasyon protokolleri uygular.</span><span class="sxs-lookup"><span data-stu-id="2b195-103">Windows Communication Foundation (WCF) implements WS-Atomic Transaction and WS-Coordination protocols.</span></span>  
  
|<span data-ttu-id="2b195-104">Belirtim/belge</span><span class="sxs-lookup"><span data-stu-id="2b195-104">Specification/Document</span></span>|<span data-ttu-id="2b195-105">Sürüm</span><span class="sxs-lookup"><span data-stu-id="2b195-105">Version</span></span>|<span data-ttu-id="2b195-106">Bağlantı</span><span class="sxs-lookup"><span data-stu-id="2b195-106">Link</span></span>|  
|-----------------------------|-------------|----------|  
|<span data-ttu-id="2b195-107">WS koordinasyonu</span><span class="sxs-lookup"><span data-stu-id="2b195-107">WS-Coordination</span></span>|<span data-ttu-id="2b195-108">1.0</span><span class="sxs-lookup"><span data-stu-id="2b195-108">1.0</span></span><br /><br /> <span data-ttu-id="2b195-109">1.1</span><span class="sxs-lookup"><span data-stu-id="2b195-109">1.1</span></span>|<http://schemas.xmlsoap.org/ws/2004/10/wscoor/><br /><br /> <https://docs.oasis-open.org/ws-tx/wscoor/2006/06>|  
|<span data-ttu-id="2b195-110">WS-AtomicTransaction</span><span class="sxs-lookup"><span data-stu-id="2b195-110">WS-AtomicTransaction</span></span>|<span data-ttu-id="2b195-111">1.0</span><span class="sxs-lookup"><span data-stu-id="2b195-111">1.0</span></span><br /><br /> <span data-ttu-id="2b195-112">1.1</span><span class="sxs-lookup"><span data-stu-id="2b195-112">1.1</span></span>|<http://schemas.xmlsoap.org/ws/2004/10/wsat/><br /><br /> <https://docs.oasis-open.org/ws-tx/wsat/2006/06>|  
  
 <span data-ttu-id="2b195-113">Bu protokol belirtimlerinde birlikte çalışabilirlik iki düzeyde gereklidir: uygulamalar arasında ve işlem yöneticileri arasında (aşağıdaki şekle bakın).</span><span class="sxs-lookup"><span data-stu-id="2b195-113">Interoperability on these protocol specifications is required at two levels: between applications and between transaction managers (see the following figure).</span></span> <span data-ttu-id="2b195-114">Özellikler, her iki birlikte çalışabilirlik düzeyi için İleti biçimlerini ve ileti değişimini harika ayrıntılarla anlatmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2b195-114">Specifications describe in great detail the message formats and message exchange for both interoperability levels.</span></span> <span data-ttu-id="2b195-115">Uygulamadan uygulamaya Exchange 'e yönelik belirli güvenlik, güvenilirlik ve kodlamalar, düzenli uygulama alışverişi için olduğu gibi uygulanır.</span><span class="sxs-lookup"><span data-stu-id="2b195-115">Certain security, reliability, and encodings for application-to-application exchange apply as they do for regular application exchange.</span></span> <span data-ttu-id="2b195-116">Ancak, işlem yöneticileri arasında başarılı birlikte çalışabilirlik, genellikle kullanıcı tarafından yapılandırılmadığı için belirli bir bağlamada anlaşma gerektirir.</span><span class="sxs-lookup"><span data-stu-id="2b195-116">However, successful interoperability between transaction managers requires agreement on the particular binding, because it is usually not configured by the user.</span></span>  
  
 <span data-ttu-id="2b195-117">Bu konu, güvenlik ile WS Atomik Işlem (WS-AT) belirtiminin bir oluşumunu açıklar ve işlem yöneticileri arasında iletişim için kullanılan güvenli bağlamayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="2b195-117">This topic describes a composition of the WS-Atomic Transaction (WS-AT) specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="2b195-118">Bu belgede açıklanan yaklaşım IBM, ıLONA, Sun Microsystems ve diğerleri dahil olmak üzere WS-AT ve WS-koordinasyon uygulamalarıyla başarıyla test edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2b195-118">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination including IBM, IONA, Sun Microsystems, and others.</span></span>  
  
 <span data-ttu-id="2b195-119">Aşağıdaki şekilde iki işlem yöneticisi, Işlem Yöneticisi 1 ve Işlem yöneticisi 2 ile iki uygulama, uygulama 1 ve uygulama 2 arasındaki birlikte çalışabilirlik gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="2b195-119">The following figure depicts the interoperability between two transaction managers, Transaction Manager 1 and Transaction Manager 2, and two applications, Application 1 and Application 2:</span></span>  
  
 ![İşlem yöneticileri arasındaki etkileşimi gösteren ekran görüntüsü.](./media/transaction-protocols/transaction-managers-flow.gif)  
  
 <span data-ttu-id="2b195-121">Tek bir başlatıcı (I) ve bir katılımcı (P) ile tipik bir WS-koordinasyon/WS-Atomik Işlem senaryosu düşünün.</span><span class="sxs-lookup"><span data-stu-id="2b195-121">Consider a typical WS-Coordination/WS-Atomic Transaction scenario with one Initiator (I) and one Participant (P).</span></span> <span data-ttu-id="2b195-122">Hem Başlatıcı hem de katılımcı Işlem yöneticilerine (sırasıyla ıSTREAM ve PTM) sahiptir.</span><span class="sxs-lookup"><span data-stu-id="2b195-122">Both Initiator and Participant have Transaction Managers, (ITM and PTM, respectively).</span></span> <span data-ttu-id="2b195-123">İki aşamalı yürütmeye bu konuda 2PC adı verilir.</span><span class="sxs-lookup"><span data-stu-id="2b195-123">Two-phase commit is referred to as 2PC in this topic.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2b195-124">1. Createkoordinattioncontext</span><span class="sxs-lookup"><span data-stu-id="2b195-124">1. CreateCoordinationContext</span></span>|<span data-ttu-id="2b195-125">12. uygulama Iletisi yanıtı</span><span class="sxs-lookup"><span data-stu-id="2b195-125">12. Application Message Response</span></span>|  
|<span data-ttu-id="2b195-126">2. Createkoordinattioncontextresponse</span><span class="sxs-lookup"><span data-stu-id="2b195-126">2. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="2b195-127">13. COMMIT (tamamlama)</span><span class="sxs-lookup"><span data-stu-id="2b195-127">13. Commit (Completion)</span></span>|  
|<span data-ttu-id="2b195-128">3. yazmaç (tamamlama)</span><span class="sxs-lookup"><span data-stu-id="2b195-128">3. Register (Completion)</span></span>|<span data-ttu-id="2b195-129">14. Prepare (2PC)</span><span class="sxs-lookup"><span data-stu-id="2b195-129">14. Prepare (2PC)</span></span>|  
|<span data-ttu-id="2b195-130">4. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="2b195-130">4. RegisterResponse</span></span>|<span data-ttu-id="2b195-131">15. hazırlama (2PC)</span><span class="sxs-lookup"><span data-stu-id="2b195-131">15. Prepare (2PC)</span></span>|  
|<span data-ttu-id="2b195-132">5. uygulama Iletisi</span><span class="sxs-lookup"><span data-stu-id="2b195-132">5. Application Message</span></span>|<span data-ttu-id="2b195-133">16. hazırlandı (2PC)</span><span class="sxs-lookup"><span data-stu-id="2b195-133">16. Prepared (2PC)</span></span>|  
|<span data-ttu-id="2b195-134">6. Createkoordinattioncontext WITH bağlamı</span><span class="sxs-lookup"><span data-stu-id="2b195-134">6. CreateCoordinationContext with Context</span></span>|<span data-ttu-id="2b195-135">17. hazırlandı (2PC)</span><span class="sxs-lookup"><span data-stu-id="2b195-135">17. Prepared (2PC)</span></span>|  
|<span data-ttu-id="2b195-136">7. Kayıt (dayanıklı)</span><span class="sxs-lookup"><span data-stu-id="2b195-136">7. Register (Durable)</span></span>|<span data-ttu-id="2b195-137">18. taahhüt (tamamlama)</span><span class="sxs-lookup"><span data-stu-id="2b195-137">18. Committed (Completion)</span></span>|  
|<span data-ttu-id="2b195-138">8. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="2b195-138">8. RegisterResponse</span></span>|<span data-ttu-id="2b195-139">19. COMMIT (2PC)</span><span class="sxs-lookup"><span data-stu-id="2b195-139">19. Commit (2PC)</span></span>|  
|<span data-ttu-id="2b195-140">9. Createkoordinattioncontextresponse</span><span class="sxs-lookup"><span data-stu-id="2b195-140">9. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="2b195-141">20. COMMIT (2PC)</span><span class="sxs-lookup"><span data-stu-id="2b195-141">20. Commit (2PC)</span></span>|  
|<span data-ttu-id="2b195-142">10. Kayıt (dayanıklı)</span><span class="sxs-lookup"><span data-stu-id="2b195-142">10. Register (Durable)</span></span>|<span data-ttu-id="2b195-143">21. taahhüt (2PC)</span><span class="sxs-lookup"><span data-stu-id="2b195-143">21. Committed (2PC)</span></span>|  
|<span data-ttu-id="2b195-144">11. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="2b195-144">11. RegisterResponse</span></span>|<span data-ttu-id="2b195-145">22. taahhüt (2PC)</span><span class="sxs-lookup"><span data-stu-id="2b195-145">22. Committed (2PC)</span></span>|  
  
 <span data-ttu-id="2b195-146">Bu belge, güvenlik ile WS-AtomicTransaction belirtiminin bir oluşumunu açıklar ve işlem yöneticileri arasında iletişim için kullanılan güvenli bağlamayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="2b195-146">This document describes a composition of the WS-AtomicTransaction specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="2b195-147">Bu belgede açıklanan yaklaşım, WS-AT ve WS-koordinasyonun diğer uygulamalarıyla başarıyla test edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2b195-147">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination.</span></span>  
  
 <span data-ttu-id="2b195-148">Şekil ve tablo, güvenlik açısından görüş açısından dört ileti sınıfını gösterir:</span><span class="sxs-lookup"><span data-stu-id="2b195-148">The figure and table illustrate four classes of messages from the viewpoint of security:</span></span>  
  
- <span data-ttu-id="2b195-149">Etkinleştirme iletileri (Createkoordinattioncontext ve Createkoordinattioncontextresponse).</span><span class="sxs-lookup"><span data-stu-id="2b195-149">Activation messages (CreateCoordinationContext and CreateCoordinationContextResponse).</span></span>  
  
- <span data-ttu-id="2b195-150">Kayıt iletileri (Register ve RegisterResponse)</span><span class="sxs-lookup"><span data-stu-id="2b195-150">Registration messages (Register and RegisterResponse)</span></span>  
  
- <span data-ttu-id="2b195-151">Protokol iletileri (hazırlama, geri alma, tamamlama, Iptal etme vb.).</span><span class="sxs-lookup"><span data-stu-id="2b195-151">Protocol messages (Prepare, Rollback, Commit, Aborted, and so on).</span></span>  
  
- <span data-ttu-id="2b195-152">Uygulama iletileri.</span><span class="sxs-lookup"><span data-stu-id="2b195-152">Application messages.</span></span>  
  
 <span data-ttu-id="2b195-153">İlk üç ileti sınıfı, Işlem yöneticisi iletileri olarak kabul edilir ve bağlama yapılandırması bu konunun ilerleyen kısımlarında "uygulama Ileti değişimi" bölümünde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2b195-153">The first three message classes are considered Transaction Manager messages and their binding configuration is described in the "Application Message Exchange" later in this topic.</span></span> <span data-ttu-id="2b195-154">Dördüncü ileti sınıfı, uygulama iletileri için uygulamadır ve bu konunun ilerleyen kısımlarında "Ileti örnekleri" bölümünde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2b195-154">The fourth class of message is application to application messages and is described in the "Message Examples" section later in this topic.</span></span> <span data-ttu-id="2b195-155">Bu bölümde, bu sınıfların her biri için WCF tarafından kullanılan protokol bağlamaları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2b195-155">This section describes the protocol bindings used for each of these classes by WCF.</span></span>  
  
 <span data-ttu-id="2b195-156">Aşağıdaki XML ad alanları ve ilişkili ön ekler Bu belge boyunca kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2b195-156">The following XML Namespaces and associated prefixes are used throughout this document.</span></span>  
  
|<span data-ttu-id="2b195-157">Prefix</span><span class="sxs-lookup"><span data-stu-id="2b195-157">Prefix</span></span>|<span data-ttu-id="2b195-158">Sürüm</span><span class="sxs-lookup"><span data-stu-id="2b195-158">Version</span></span>|<span data-ttu-id="2b195-159">Ad alanı URI 'SI</span><span class="sxs-lookup"><span data-stu-id="2b195-159">Namespace URI</span></span>|  
|------------|-------------|-------------------|  
|<span data-ttu-id="2b195-160">s11</span><span class="sxs-lookup"><span data-stu-id="2b195-160">s11</span></span>||<https://schemas.xmlsoap.org/soap/envelope/>|  
|<span data-ttu-id="2b195-161">WSA</span><span class="sxs-lookup"><span data-stu-id="2b195-161">wsa</span></span>|<span data-ttu-id="2b195-162">1,0 öncesi</span><span class="sxs-lookup"><span data-stu-id="2b195-162">Pre-1.0</span></span><br /><br /> <span data-ttu-id="2b195-163">1.0</span><span class="sxs-lookup"><span data-stu-id="2b195-163">1.0</span></span>|`http://www.w3.org/2004/08/addressing`<br /><br /> <https://www.w3.org/2005/08/addressing/>|  
|<span data-ttu-id="2b195-164">wscoor</span><span class="sxs-lookup"><span data-stu-id="2b195-164">wscoor</span></span>|<span data-ttu-id="2b195-165">1.0</span><span class="sxs-lookup"><span data-stu-id="2b195-165">1.0</span></span><br /><br /> <span data-ttu-id="2b195-166">1.1</span><span class="sxs-lookup"><span data-stu-id="2b195-166">1.1</span></span>|<http://schemas.xmlsoap.org/ws/2004/10/wscoor/><br /><br /> <https://docs.oasis-open.org/ws-tx/wscoor/2006/06>|  
|<span data-ttu-id="2b195-167">WSAT</span><span class="sxs-lookup"><span data-stu-id="2b195-167">wsat</span></span>|<span data-ttu-id="2b195-168">1.0</span><span class="sxs-lookup"><span data-stu-id="2b195-168">1.0</span></span><br /><br /> <span data-ttu-id="2b195-169">1.1</span><span class="sxs-lookup"><span data-stu-id="2b195-169">1.1</span></span>|<http://schemas.xmlsoap.org/ws/2004/10/wsat/><br /><br /> <https://docs.oasis-open.org/ws-tx/wsat/2006/06>|  
|<span data-ttu-id="2b195-170">t</span><span class="sxs-lookup"><span data-stu-id="2b195-170">t</span></span>|<span data-ttu-id="2b195-171">1,3 öncesi</span><span class="sxs-lookup"><span data-stu-id="2b195-171">Pre-1.3</span></span><br /><br /> <span data-ttu-id="2b195-172">1.3</span><span class="sxs-lookup"><span data-stu-id="2b195-172">1.3</span></span>|<http://schemas.xmlsoap.org/ws/2005/02/trust/><br /><br /> <https://docs.oasis-open.org/ws-sx/ws-trust/200512>|  
|<span data-ttu-id="2b195-173">o</span><span class="sxs-lookup"><span data-stu-id="2b195-173">o</span></span>||<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd>|  
|<span data-ttu-id="2b195-174">yapamadı</span><span class="sxs-lookup"><span data-stu-id="2b195-174">xsd</span></span>||<https://www.w3.org/2001/XMLSchema>|  
  
## <a name="transaction-manager-bindings"></a><span data-ttu-id="2b195-175">İşlem Yöneticisi bağlamaları</span><span class="sxs-lookup"><span data-stu-id="2b195-175">Transaction Manager Bindings</span></span>  
 <span data-ttu-id="2b195-176">R1001: WS-AT 1,0 işlemine katılan Işlem yöneticileri, WS-Atomik Işlem ve WS-koordinasyon ileti alışverişi için SOAP 1,1 ve WS-Addressing 2004/08 kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2b195-176">R1001: Transaction Managers participating in a WS-AT 1.0 transaction must use SOAP 1.1 and WS-Addressing 2004/08 for WS-Atomic Transaction and WS-Coordination message exchanges.</span></span>  
  
 <span data-ttu-id="2b195-177">R1002: WS-AT 1,1 işlemine katılan Işlem yöneticileri, WS-Atomik Işlem ve WS-koordinasyon ileti alışverişi için SOAP 1,1 ve WS-Addressing 2005/08 kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2b195-177">R1002: Transaction Managers participating in a WS-AT 1.1 transaction must use SOAP 1.1 and WS-Addressing 2005/08 for WS-Atomic Transaction and WS-Coordination message exchanges.</span></span>  
  
 <span data-ttu-id="2b195-178">Uygulama iletileri bu bağlamalarla sınırlı değildir ve daha sonra açıklanır.</span><span class="sxs-lookup"><span data-stu-id="2b195-178">Application messages are not constrained to these bindings and are described later.</span></span>  
  
### <a name="transaction-manager-https-binding"></a><span data-ttu-id="2b195-179">İşlem Yöneticisi HTTPS bağlama</span><span class="sxs-lookup"><span data-stu-id="2b195-179">Transaction Manager HTTPS Binding</span></span>  
 <span data-ttu-id="2b195-180">İşlem Yöneticisi HTTPS bağlaması, güvenlik elde etmek ve işlem ağacındaki her gönderici alıcısı çifti arasında güven sağlamak için yalnızca taşıma güvenliğine dayanır.</span><span class="sxs-lookup"><span data-stu-id="2b195-180">The transaction manager HTTPS binding relies solely on transport security to achieve security and establish trust between each sender-receiver pair in the transaction tree.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="2b195-181">HTTPS aktarım yapılandırması</span><span class="sxs-lookup"><span data-stu-id="2b195-181">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="2b195-182">X. 509.440 sertifikaları, Işlem yöneticisi kimliğini oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2b195-182">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="2b195-183">İstemci/sunucu kimlik doğrulaması gereklidir ve istemci/sunucu yetkilendirmesi uygulama ayrıntısı olarak bırakılır:</span><span class="sxs-lookup"><span data-stu-id="2b195-183">Client/server authentication is required, and client/server authorization is left as an implementation detail:</span></span>  
  
- <span data-ttu-id="2b195-184">R1111: tel üzerinden sunulan X. 509.440 sertifikalarının, kaynak makinenin tam etki alanı adı (FQDN) ile eşleşen bir konu adı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2b195-184">R1111: X.509 certificates presented over the wire must have a subject name that matches the fully qualified domain name (FQDN) of the originating machine.</span></span>  
  
- <span data-ttu-id="2b195-185">B1112: X. 509.440 konu adı denetimlerinin başarılı olması için sistemdeki her gönderici alıcısı çifti arasında DNS işlevsel olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2b195-185">B1112: DNS must be functional between each sender-receiver pair in the system for X.509 subject name checks to succeed.</span></span>  
  
#### <a name="activation-and-registration-binding-configuration"></a><span data-ttu-id="2b195-186">Etkinleştirme ve kayıt bağlama yapılandırması</span><span class="sxs-lookup"><span data-stu-id="2b195-186">Activation and Registration Binding Configuration</span></span>  
 <span data-ttu-id="2b195-187">WCF, HTTPS üzerinden bağıntı ile istek/yanıt çift yönlü bağlamayı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="2b195-187">WCF requires request/reply duplex binding with correlation over HTTPS.</span></span> <span data-ttu-id="2b195-188">(İstek/yanıt iletisi değişim desenlerinin bağıntısı ve açıklamaları hakkında daha fazla bilgi için bkz. WS Atomik Işlem, Bölüm 8.)</span><span class="sxs-lookup"><span data-stu-id="2b195-188">(For more information about correlation and descriptions of the request/reply message exchange patterns, see WS-Atomic Transaction, Section 8.)</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="2b195-189">2PC protokol bağlama yapılandırması</span><span class="sxs-lookup"><span data-stu-id="2b195-189">2PC Protocol Binding Configuration</span></span>  
 <span data-ttu-id="2b195-190">WCF, HTTPS üzerinden tek yönlü (Datagram) iletileri destekler.</span><span class="sxs-lookup"><span data-stu-id="2b195-190">WCF supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="2b195-191">İletiler arasındaki bağıntı uygulama ayrıntısı olarak kalır.</span><span class="sxs-lookup"><span data-stu-id="2b195-191">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="2b195-192">B1131: uygulamalar, WCF 2PC iletilerinin bağıntısını elde etmek için WS-Addressing bölümünde açıklandığı gibi `wsa:ReferenceParameters` desteklemelidir.</span><span class="sxs-lookup"><span data-stu-id="2b195-192">B1131: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of WCF’s 2PC messages.</span></span>  
  
### <a name="transaction-manager-mixed-security-binding"></a><span data-ttu-id="2b195-193">Transaction Manager karışık güvenlik bağlama</span><span class="sxs-lookup"><span data-stu-id="2b195-193">Transaction Manager Mixed Security Binding</span></span>  
 <span data-ttu-id="2b195-194">Bu, kimlik oluşturma amacıyla WS koordinasyonu verilen belirteç modeliyle birleştirilmiş aktarım güvenliği kullanan alternatif (karışık mod) bağlamadır.</span><span class="sxs-lookup"><span data-stu-id="2b195-194">This is an alternate (mixed mode) binding that uses transport security combined with the WS-Coordination Issued Token model for identity establishment purposes.</span></span> <span data-ttu-id="2b195-195">Etkinleştirme ve kayıt, iki bağlama arasında farklı olan tek öğelerdir.</span><span class="sxs-lookup"><span data-stu-id="2b195-195">Activation and Registration are the only elements that differ between the two bindings.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="2b195-196">HTTPS aktarım yapılandırması</span><span class="sxs-lookup"><span data-stu-id="2b195-196">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="2b195-197">X. 509.440 sertifikaları, Işlem yöneticisi kimliğini oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2b195-197">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="2b195-198">İstemci/sunucu kimlik doğrulaması gereklidir ve istemci/sunucu yetkilendirmesi uygulama ayrıntısı olarak bırakılır.</span><span class="sxs-lookup"><span data-stu-id="2b195-198">Client/Server authentication is required, and client/server authorization is left as an implementation detail.</span></span>  
  
#### <a name="activation-message-binding-configuration"></a><span data-ttu-id="2b195-199">Etkinleştirme Iletisi bağlama yapılandırması</span><span class="sxs-lookup"><span data-stu-id="2b195-199">Activation Message Binding Configuration</span></span>  
 <span data-ttu-id="2b195-200">Etkinleştirme Iletileri genellikle bir uygulama ve kendi yerel Işlem yöneticisi arasında gerçekleştiğinden birlikte çalışabilirliğe katılmaz.</span><span class="sxs-lookup"><span data-stu-id="2b195-200">Activation Messages usually do not participate in interoperability because they typically occur between an application and its local Transaction Manager.</span></span>  
  
 <span data-ttu-id="2b195-201">B1221: WCF etkinleştirme iletileri için çift yönlü HTTPS bağlamasını ( [mesajlaşma protokollerinde](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)açıklanmıştır) kullanır.</span><span class="sxs-lookup"><span data-stu-id="2b195-201">B1221: WCF uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) for Activation messages.</span></span> <span data-ttu-id="2b195-202">İstek ve yanıt iletileri WS-AT 1,0 için ws-Addressing 2004/08 ve WS-AT 1,1 için ws-Addressing 2005/08 kullanılarak bağıntılı.</span><span class="sxs-lookup"><span data-stu-id="2b195-202">Request and Reply messages are correlated using WS-Addressing 2004/08 for WS-AT 1.0 and WS-Addressing 2005/08 for WS-AT 1.1.</span></span>  
  
 <span data-ttu-id="2b195-203">WS Atomik Işlem belirtimi, Bölüm 8, bağıntı ve ileti değişimi desenleri hakkında daha fazla ayrıntı açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="2b195-203">WS-Atomic Transaction specification, Section 8, describes further details about correlation and the message exchange patterns.</span></span>  
  
- <span data-ttu-id="2b195-204">R1222: `CreateCoordinationContext`aldıktan sonra, düzenleyicinin ilişkili gizli dizi `STx`bir `SecurityContextToken` vermesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="2b195-204">R1222: Upon receiving a `CreateCoordinationContext`, the Coordinator must issue a `SecurityContextToken` with associated secret `STx`.</span></span> <span data-ttu-id="2b195-205">Bu belirteç, WS-Trust belirtimindeki bir `t:IssuedTokens` üst bilgisi içinde döndürülür.</span><span class="sxs-lookup"><span data-stu-id="2b195-205">This token is returned inside a `t:IssuedTokens` header following WS-Trust specification.</span></span>  
  
- <span data-ttu-id="2b195-206">R1223: etkinleştirme mevcut bir düzenleme bağlamında gerçekleşirse, var olan bağlamla ilişkili `SecurityContextToken` olan `t:IssuedTokens` üst bilgisinin `CreateCoordinationContext` iletisinde akışı gerekir.</span><span class="sxs-lookup"><span data-stu-id="2b195-206">R1223: If Activation occurs within an existing Coordination Context, the `t:IssuedTokens` header with the `SecurityContextToken` associated with existing Context must flow on the `CreateCoordinationContext` message.</span></span>  
  
 <span data-ttu-id="2b195-207">Giden `wscoor:CreateCoordinationContextResponse` iletisine eklemek için yeni bir `t:IssuedTokens` üst bilgisi oluşturulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2b195-207">A new `t:IssuedTokens` header should be generated for attaching to the outgoing `wscoor:CreateCoordinationContextResponse` message.</span></span>  
  
#### <a name="registration-message-binding-configuration"></a><span data-ttu-id="2b195-208">Kayıt Iletisi bağlama yapılandırması</span><span class="sxs-lookup"><span data-stu-id="2b195-208">Registration Message Binding Configuration</span></span>  
 <span data-ttu-id="2b195-209">B1231: WCF çift yönlü HTTPS bağlamasını kullanır ( [mesajlaşma protokollerinde](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)açıklanmıştır).</span><span class="sxs-lookup"><span data-stu-id="2b195-209">B1231: WCF uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)).</span></span> <span data-ttu-id="2b195-210">İstek ve yanıt iletileri WS-AT 1,0 için ws-Addressing 2004/08 ve WS-AT 1,1 için ws-Addressing 2005/08 kullanılarak bağıntılı.</span><span class="sxs-lookup"><span data-stu-id="2b195-210">Request and Reply messages are correlated using WS-Addressing 2004/08 for WS-AT 1.0 and WS-Addressing 2005/08 for WS-AT 1.1.</span></span>  
  
 <span data-ttu-id="2b195-211">WS-AtomicTransaction, Bölüm 8, ileti değişim desenlerinin bağıntı ve açıklamaları hakkında daha fazla ayrıntı açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="2b195-211">WS-AtomicTransaction, Section 8, describes further details about correlation and descriptions of the message exchange patterns.</span></span>  
  
 <span data-ttu-id="2b195-212">R1232: giden `wscoor:Register` iletileri, [Güvenlik protokollerinde](../../../../docs/framework/wcf/feature-details/security-protocols.md)açıklanan `IssuedTokenOverTransport` kimlik doğrulama modunu kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2b195-212">R1232: Outgoing `wscoor:Register` messages must use the `IssuedTokenOverTransport` authentication mode described in [Security Protocols](../../../../docs/framework/wcf/feature-details/security-protocols.md).</span></span>  
  
 <span data-ttu-id="2b195-213">`wsse:Timestamp` öğesi, verilen `SecurityContextToken STx` kullanılarak imzalanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2b195-213">The `wsse:Timestamp` element must be signed using the `SecurityContextToken STx` issued.</span></span> <span data-ttu-id="2b195-214">Bu imza, belirli bir işlemle ilişkili belirtecin bir kanıtıdır ve işlemde bir katılımcı listesini doğrulamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2b195-214">This signature is a proof of possession of the token associated with particular transaction and is used to authenticate a participant enlisting in the transaction.</span></span> <span data-ttu-id="2b195-215">RegistrationResponse iletisi HTTPS üzerinden geri gönderilir.</span><span class="sxs-lookup"><span data-stu-id="2b195-215">The RegistrationResponse message is sent back over HTTPS.</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="2b195-216">2PC protokol bağlama yapılandırması</span><span class="sxs-lookup"><span data-stu-id="2b195-216">2PC Protocol Binding Configuration</span></span>  
 <span data-ttu-id="2b195-217">WCF, HTTPS üzerinden tek yönlü (Datagram) iletileri destekler.</span><span class="sxs-lookup"><span data-stu-id="2b195-217">WCF supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="2b195-218">İletiler arasındaki bağıntı uygulama ayrıntısı olarak kalır.</span><span class="sxs-lookup"><span data-stu-id="2b195-218">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="2b195-219">B1241: uygulamalar, WCF 2PC iletilerinin bağıntısını elde etmek için WS-Addressing bölümünde açıklandığı gibi `wsa:ReferenceParameters` desteklemelidir.</span><span class="sxs-lookup"><span data-stu-id="2b195-219">B1241: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of WCF’s 2PC messages.</span></span>  
  
## <a name="application-message-exchange"></a><span data-ttu-id="2b195-220">Uygulama Iletisi değişimi</span><span class="sxs-lookup"><span data-stu-id="2b195-220">Application Message Exchange</span></span>  
 <span data-ttu-id="2b195-221">Bağlama aşağıdaki güvenlik gereksinimlerini karşıladığı sürece, uygulamalar uygulamadan uygulamaya iletiler için herhangi bir bağlamayı kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="2b195-221">Applications are free to use any particular binding for application-to-application messages, as long as the binding meets the following security requirements:</span></span>  
  
- <span data-ttu-id="2b195-222">R2001: uygulamadan uygulamaya iletileri ileti üstbilgisindeki `CoordinationContext` birlikte `t:IssuedTokens` üst bilgisini Flow olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2b195-222">R2001: Application-to-application messages must flow the `t:IssuedTokens` header along with the `CoordinationContext` in the header of the message.</span></span>  
  
- <span data-ttu-id="2b195-223">R2002: `t:IssuedToken` bütünlük ve gizliliği sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2b195-223">R2002: Integrity and confidentiality of `t:IssuedToken` must be provided.</span></span>  
  
 <span data-ttu-id="2b195-224">`CoordinationContext` üst bilgisi `wscoor:Identifier`içerir.</span><span class="sxs-lookup"><span data-stu-id="2b195-224">The `CoordinationContext` header contains `wscoor:Identifier`.</span></span> <span data-ttu-id="2b195-225">`xsd:AnyURI` tanımı hem mutlak hem de göreli URI 'lerin kullanılmasına izin verdiğinden, WCF yalnızca, mutlak URI 'Ler olan `wscoor:Identifiers`destekler.</span><span class="sxs-lookup"><span data-stu-id="2b195-225">While the definition of `xsd:AnyURI` allows the use of both absolute and relative URIs, WCF supports only `wscoor:Identifiers`, which are absolute URIs.</span></span>  
  
 <span data-ttu-id="2b195-226">B2003: `wscoor:CoordinationContext` `wscoor:Identifier` göreli bir URI ise, hatalar işlem WCF hizmetlerinden döndürülür.</span><span class="sxs-lookup"><span data-stu-id="2b195-226">B2003: If the `wscoor:Identifier` of the `wscoor:CoordinationContext` is a relative URI, faults will be returned from transactional WCF services.</span></span>  
  
## <a name="message-examples"></a><span data-ttu-id="2b195-227">İleti örnekleri</span><span class="sxs-lookup"><span data-stu-id="2b195-227">Message Examples</span></span>  
  
### <a name="createcoordinationcontext-requestresponse-messages"></a><span data-ttu-id="2b195-228">Createkoordinattioncontext Isteği/yanıt Iletileri</span><span class="sxs-lookup"><span data-stu-id="2b195-228">CreateCoordinationContext Request/Response Messages</span></span>  
 <span data-ttu-id="2b195-229">Aşağıdaki iletiler bir istek/yanıt modelini izler.</span><span class="sxs-lookup"><span data-stu-id="2b195-229">The following messages follow a request/response pattern.</span></span>  
  
#### <a name="createcoordinationcontext-with-wscoor-10"></a><span data-ttu-id="2b195-230">WSCoor 1,0 ile Createkoordinattioncontext</span><span class="sxs-lookup"><span data-stu-id="2b195-230">CreateCoordinationContext with WSCoor 1.0</span></span>  
  
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
  
#### <a name="createcoordinationcontext-with-wscoor-11"></a><span data-ttu-id="2b195-231">WSCoor 1,1 ile Createkoordinattioncontext</span><span class="sxs-lookup"><span data-stu-id="2b195-231">CreateCoordinationContext with WSCoor 1.1</span></span>  
  
```xml  
<s:Envelope>   
<s:Header>  
<a:Action>http://docs.oasis-open.org/ws-tx/wscoor/2006/06/CreateCoordinationContext</Action>  
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
  
#### <a name="createcoordinationcontextresponse-with-trust-pre-13-and-wscoor-10"></a><span data-ttu-id="2b195-232">Trust-1,3 ve Wscoveya 1,0 ile Createkoordinattioncontextresponse</span><span class="sxs-lookup"><span data-stu-id="2b195-232">CreateCoordinationContextResponse with Trust Pre-1.3 and WSCoor 1.0</span></span>  
  
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
  
#### <a name="createcoordinationcontextresponse-with-trust-13-and-wscoor-11"></a><span data-ttu-id="2b195-233">Trust 1,3 ve WSCoor 1,1 ile Createkoordinattioncontextresponse</span><span class="sxs-lookup"><span data-stu-id="2b195-233">CreateCoordinationContextResponse with Trust 1.3 and WSCoor 1.1</span></span>  
  
```xml  
<s:Envelope>  
<!-- Data below is shown in the clear for illustration purposes only. -->   
<s:Header>   
<a:Action>http://docs.oasis-open.org/ws-tx/wscoor/2006/06/CreateCoordinationContextResponse </a:Action>  
<a:RelatesTo>urn:uuid:069f5104-fd88-4264-9f99-60032a82854e</a:RelatesTo>  
<a:To s:mustUnderstand="1">https://... </a:To>   
<t:IssuedTokens>   
<wst:RequestSecurityTokenResponse   
xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"   
xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd"   
xmlns:wst="http://docs.oasis-open.org/ws-sx/ws-trust/200512"  
xmlns:wsc="http://schemas.xmlsoap.org/ws/2005/02/sc"  
xmlns:wsp="http://schemas.xmlsoap.org/ws/2004/09/policy">  
<wst:TokenType>http://schemas.xmlsoap.org/ws/2005/02/sc/sct</wst:TokenType>  
<wst:RequestedSecurityToken>   
<wsc:SecurityContextToken>   
<wssu:Identifier> http://fabrikam123.com/SCTi  
</wssu:Identifier>   
</wsc:SecurityContextToken>   
</wst:RequestedSecurityToken>   
<wsp:AppliesTo> http://fabrikam123.com/CCi </wsp:AppliesTo>  
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
  Type="http://docs.oasis-open.org/ws-sx/ws-trust/200512/SymmetricKey">  
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
<wscoor:Identifier> http://fabrikam123.com/CCi  
</wscoor:Identifier>   
<wscoor:Expires>...</wscoor:Expires>  
<wscoor:CoordinationType>...</wscoor:CoordinationType>  
<wscoor:RegistrationService>   
<a:Address>https://...</a:Address>  
<a:ReferenceParameters> ...  
</a:ReferenceParameters>  
</wscoor:RegistrationService>   
</wscoor:CoordinationContext>   
</wscoor:CreateCoordinationContextResponse>   
</s:Body>   
</s:Envelope>  
```  
  
### <a name="registration-messages"></a><span data-ttu-id="2b195-234">Kayıt Iletileri</span><span class="sxs-lookup"><span data-stu-id="2b195-234">Registration Messages</span></span>  
 <span data-ttu-id="2b195-235">Aşağıdaki iletiler kayıt mesajlardır.</span><span class="sxs-lookup"><span data-stu-id="2b195-235">The following messages are registration messages.</span></span>  
  
#### <a name="register-with-wscoor-10"></a><span data-ttu-id="2b195-236">WSCoor 1,0 ile kaydolun</span><span class="sxs-lookup"><span data-stu-id="2b195-236">Register with WSCoor 1.0</span></span>  
  
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
  
#### <a name="register-with-wscoor-11"></a><span data-ttu-id="2b195-237">WSCoor 1,1 ile kaydolun</span><span class="sxs-lookup"><span data-stu-id="2b195-237">Register with WSCoor 1.1</span></span>  
  
```xml  
<s:Envelope>  
<s:Header>   
<a:Action>http://docs.oasis-open.org/ws-tx/wscoor/2006/06/Register</a:Action>   
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
<wssu:Identifier> http://fabrikam123.com/SCTi  
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
<ds:DigestMethod  
Algorithm="http://www.w3.org/2000/09/xmldsig#sha1"/>   
<ds:DigestValue> alRzyhjLgoUOYoh8cx4n75eTcUk=  
</ds:DigestValue>   
</ds:Reference>   
</ds:SignedInfo>  
<ds:SignatureValue>YZYjnVvSOVasAQqQxaaviTSWtqI=  
</ds:SignatureValue>  
<ds:KeyInfo>   
<wsse:SecurityTokenReference xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">  
  <wsse:Reference URI="http://fabrikam123.com/SCTi"/>  
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
  
#### <a name="register-response-with-wscoor-10"></a><span data-ttu-id="2b195-238">WSCoor 1,0 ile yanıtı kaydetme</span><span class="sxs-lookup"><span data-stu-id="2b195-238">Register Response with WSCoor 1.0</span></span>  
  
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
  
#### <a name="register-response-with-wscoor-11"></a><span data-ttu-id="2b195-239">WSCoor 1,1 ile yanıtı kaydetme</span><span class="sxs-lookup"><span data-stu-id="2b195-239">Register Response with WSCoor 1.1</span></span>  
  
```xml  
<s:Envelope>  
<s:Header>   
<a:Action> http://docs.oasis-open.org/ws-tx/wscoor/2006/06/RegisterResponse  
</a:Action>   
<a:MessageID>urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088d</a:MessageID>  
<a:RelatesTo> urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088e </a:RelatesTo>  
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
<a:ReferenceParameters> ... </a:ReferenceParameters>  
</wscoor:CoordinatorProtocolService>   
</wscoor:RegisterResponse>   
</s:Body>   
</s:Envelope>  
```  
  
### <a name="two-phase-commit-protocol-messages"></a><span data-ttu-id="2b195-240">İki aşamalı tamamlama Protokolü Iletisi</span><span class="sxs-lookup"><span data-stu-id="2b195-240">Two Phase Commit Protocol Messages</span></span>  
 <span data-ttu-id="2b195-241">Aşağıdaki ileti, iki aşamalı tamamlama (2PC) protokolüyle ilişkilidir.</span><span class="sxs-lookup"><span data-stu-id="2b195-241">The following message relates to the two-phase commit (2PC) protocol.</span></span>  
  
#### <a name="commit-with-wsat-10"></a><span data-ttu-id="2b195-242">WSAT 1,0 ile Yürüt</span><span class="sxs-lookup"><span data-stu-id="2b195-242">Commit with WSAT 1.0</span></span>  
  
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
  
#### <a name="commit-with-wsat-11"></a><span data-ttu-id="2b195-243">WSAT 1,1 ile Yürüt</span><span class="sxs-lookup"><span data-stu-id="2b195-243">Commit with WSAT 1.1</span></span>  
  
```xml  
<s:Envelope>  
<s:Header>   
<a:Action>http://docs.oasis-open.org/ws-tx/wsat/2006/06</a:Action>  
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
  
### <a name="application-messages"></a><span data-ttu-id="2b195-244">Uygulama Iletileri</span><span class="sxs-lookup"><span data-stu-id="2b195-244">Application Messages</span></span>  
 <span data-ttu-id="2b195-245">Aşağıdaki iletiler uygulama mesajlardır.</span><span class="sxs-lookup"><span data-stu-id="2b195-245">The following messages are application messages.</span></span>  
  
#### <a name="application-message-request"></a><span data-ttu-id="2b195-246">Uygulama iletisi-Istek</span><span class="sxs-lookup"><span data-stu-id="2b195-246">Application message-Request</span></span>  
  
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

---
title: İşlem Protokolleri sürüm 1.0
ms.date: 03/30/2017
ms.assetid: 034679af-0002-402e-98a8-ef73dcd71bb6
ms.openlocfilehash: a1501bbd5364773359f9b62602ba4bb684f076ba
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61764638"
---
# <a name="transaction-protocols-version-10"></a><span data-ttu-id="e7a62-102">İşlem Protokolleri sürüm 1.0</span><span class="sxs-lookup"><span data-stu-id="e7a62-102">Transaction Protocols version 1.0</span></span>
<span data-ttu-id="e7a62-103">Windows Communication Foundation (WCF) sürüm 1 WS-Atomic işlem ve WS-koordinasyon protokolleri sürüm 1.0 uygular.</span><span class="sxs-lookup"><span data-stu-id="e7a62-103">Windows Communication Foundation (WCF) version 1 implements version 1.0 of the WS-Atomic Transaction and WS-Coordination protocols.</span></span> <span data-ttu-id="e7a62-104">Sürüm 1.1 hakkında daha fazla bilgi için bkz: [işlem protokolleri](../../../../docs/framework/wcf/feature-details/transaction-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="e7a62-104">For more information about version 1.1, see [Transaction Protocols](../../../../docs/framework/wcf/feature-details/transaction-protocols.md).</span></span>  
  
|<span data-ttu-id="e7a62-105">Belirtimi/belge</span><span class="sxs-lookup"><span data-stu-id="e7a62-105">Specification/Document</span></span>|<span data-ttu-id="e7a62-106">Bağlantı</span><span class="sxs-lookup"><span data-stu-id="e7a62-106">Link</span></span>|  
|-----------------------------|----------|  
|<span data-ttu-id="e7a62-107">WS-düzenleme</span><span class="sxs-lookup"><span data-stu-id="e7a62-107">WS-Coordination</span></span>|<http://specs.xmlsoap.org/ws/2004/10/wscoor/wscoor.pdf>|  
|<span data-ttu-id="e7a62-108">WS-AtomicTransaction</span><span class="sxs-lookup"><span data-stu-id="e7a62-108">WS-AtomicTransaction</span></span>|<http://specs.xmlsoap.org/ws/2004/10/wsat/wsat.pdf>|  
  
 <span data-ttu-id="e7a62-109">Bu protokol belirtimleri üzerinde birlikte çalışabilirlik iki düzeyde gereklidir: uygulamalar arasında arasında işlem yöneticileri (aşağıdaki şekilde bakın).</span><span class="sxs-lookup"><span data-stu-id="e7a62-109">Interoperability on these protocol specifications is required at two levels: between applications and between transaction managers (see the following figure).</span></span> <span data-ttu-id="e7a62-110">Her iki birlikte çalışabilirlik düzeyleri için exchange ileti biçimleri ve ileti ayrıntılarını özellikleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e7a62-110">Specifications describe in great detail the message formats and message exchange for both interoperability levels.</span></span> <span data-ttu-id="e7a62-111">Normal uygulama exchange gibi belirli güvenlik, güvenilirlik ve kodlamaları uygulama uygulaması exchange için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="e7a62-111">Certain security, reliability, and encodings for application-to-application exchange apply as they do for regular application exchange.</span></span> <span data-ttu-id="e7a62-112">Ancak, kullanıcı tarafından genellikle yapılandırılmamış olduğundan işlem yöneticileri başarılı birlikte çalışabilirliği belirli bağlama üzerinde sözleşmesi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e7a62-112">However, successful interoperability between transaction managers requires agreement on the particular binding, because it is usually not configured by the user.</span></span>  
  
 <span data-ttu-id="e7a62-113">Bu konu, WS-Atomic işlem (WS-AT) belirtimi bileşimi ile güvenlik açıklar ve işlem yöneticileri arasındaki iletişim için kullanılan güvenli bir bağlama tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e7a62-113">This topic describes a composition of the WS-Atomic Transaction (WS-AT) specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="e7a62-114">Bu belgede açıklanan yaklaşımı başarıyla WS-AT ve WS-koordinasyon diğer uygulamaları ile test edilmiştir IBM, IONA, Sun Microsystems ve diğerleri gibi.</span><span class="sxs-lookup"><span data-stu-id="e7a62-114">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination including IBM, IONA, Sun Microsystems, and others.</span></span>  
  
 <span data-ttu-id="e7a62-115">Aşağıdaki şekil, hareket yöneticisi 1 ve hareket yöneticisi 2, iki işlem yöneticileri ve uygulama 1 ve 2 uygulama olmak üzere iki uygulama arasında birlikte çalışabilirliği gösterir:</span><span class="sxs-lookup"><span data-stu-id="e7a62-115">The following figure depicts the interoperability between two transaction managers, Transaction Manager 1 and Transaction Manager 2, and two applications, Application 1 and Application 2:</span></span>  
  
 ![Yöneticileri işlem arasındaki etkileşimi gösteren ekran görüntüsü.](./media/transaction-protocols/transaction-managers-flow.gif)  
  
 <span data-ttu-id="e7a62-117">Bir başlatıcı (ı) ve bir katılımcı (P) tipik bir WS-koordinasyon/WS-Atomic işlem senaryoyu ele alalım.</span><span class="sxs-lookup"><span data-stu-id="e7a62-117">Consider a typical WS-Coordination/WS-Atomic Transaction scenario with one Initiator (I) and one Participant (P).</span></span> <span data-ttu-id="e7a62-118">Hem Başlatıcı hem de katılımcı sahip işlem yöneticileri (ITM ve PTM, sırasıyla).</span><span class="sxs-lookup"><span data-stu-id="e7a62-118">Both Initiator and Participant have Transaction Managers, (ITM and PTM, respectively).</span></span> <span data-ttu-id="e7a62-119">İki aşamalı tamamlama bu konudaki 2PC olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="e7a62-119">Two-phase commit is referred to as 2PC in this topic.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e7a62-120">1. CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="e7a62-120">1. CreateCoordinationContext</span></span>|<span data-ttu-id="e7a62-121">12. Uygulama ileti yanıtı</span><span class="sxs-lookup"><span data-stu-id="e7a62-121">12. Application Message Response</span></span>|  
|<span data-ttu-id="e7a62-122">2. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="e7a62-122">2. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="e7a62-123">13. İşleme (tamamlama)</span><span class="sxs-lookup"><span data-stu-id="e7a62-123">13. Commit (Completion)</span></span>|  
|<span data-ttu-id="e7a62-124">3. Kayıt (tamamlama)</span><span class="sxs-lookup"><span data-stu-id="e7a62-124">3. Register (Completion)</span></span>|<span data-ttu-id="e7a62-125">14. (2PC) hazırlama</span><span class="sxs-lookup"><span data-stu-id="e7a62-125">14. Prepare (2PC)</span></span>|  
|<span data-ttu-id="e7a62-126">4. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="e7a62-126">4. RegisterResponse</span></span>|<span data-ttu-id="e7a62-127">15. (2PC) hazırlama</span><span class="sxs-lookup"><span data-stu-id="e7a62-127">15. Prepare (2PC)</span></span>|  
|<span data-ttu-id="e7a62-128">5. Uygulama iletisi</span><span class="sxs-lookup"><span data-stu-id="e7a62-128">5. Application Message</span></span>|<span data-ttu-id="e7a62-129">16. Hazırlanan (2PC)</span><span class="sxs-lookup"><span data-stu-id="e7a62-129">16. Prepared (2PC)</span></span>|  
|<span data-ttu-id="e7a62-130">6. Bağlamla CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="e7a62-130">6. CreateCoordinationContext with Context</span></span>|<span data-ttu-id="e7a62-131">17. Hazırlanan (2PC)</span><span class="sxs-lookup"><span data-stu-id="e7a62-131">17. Prepared (2PC)</span></span>|  
|<span data-ttu-id="e7a62-132">7. Kayıt (Durable)</span><span class="sxs-lookup"><span data-stu-id="e7a62-132">7. Register (Durable)</span></span>|<span data-ttu-id="e7a62-133">18. Taahhüt edilen (tamamlama)</span><span class="sxs-lookup"><span data-stu-id="e7a62-133">18. Committed (Completion)</span></span>|  
|<span data-ttu-id="e7a62-134">8. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="e7a62-134">8. RegisterResponse</span></span>|<span data-ttu-id="e7a62-135">19. Kayıt (2PC)</span><span class="sxs-lookup"><span data-stu-id="e7a62-135">19. Commit (2PC)</span></span>|  
|<span data-ttu-id="e7a62-136">9. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="e7a62-136">9. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="e7a62-137">20. Kayıt (2PC)</span><span class="sxs-lookup"><span data-stu-id="e7a62-137">20. Commit (2PC)</span></span>|  
|<span data-ttu-id="e7a62-138">10. Kayıt (Durable)</span><span class="sxs-lookup"><span data-stu-id="e7a62-138">10. Register (Durable)</span></span>|<span data-ttu-id="e7a62-139">21. Taahhüt edilen (2PC)</span><span class="sxs-lookup"><span data-stu-id="e7a62-139">21. Committed (2PC)</span></span>|  
|<span data-ttu-id="e7a62-140">11. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="e7a62-140">11. RegisterResponse</span></span>|<span data-ttu-id="e7a62-141">22. Taahhüt edilen (2PC)</span><span class="sxs-lookup"><span data-stu-id="e7a62-141">22. Committed (2PC)</span></span>|  
  
 <span data-ttu-id="e7a62-142">Bu belge, güvenlik ile WS-AtomicTransaction belirtiminin bir bileşim açıklar ve işlem yöneticileri arasındaki iletişim için kullanılan güvenli bir bağlama tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e7a62-142">This document describes a composition of the WS-AtomicTransaction specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="e7a62-143">Bu belgede açıklanan yaklaşımı başarıyla WS-AT ve WS-koordinasyon diğer uygulamaları ile test edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e7a62-143">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination.</span></span>  
  
 <span data-ttu-id="e7a62-144">Şekil ve tabloda dört güvenlik görüş iletilerden sınıflarını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="e7a62-144">The figure and table illustrate four classes of messages from the viewpoint of security:</span></span>  
  
- <span data-ttu-id="e7a62-145">Etkinleştirme iletileri (CreateCoordinationContext ve CreateCoordinationContextResponse).</span><span class="sxs-lookup"><span data-stu-id="e7a62-145">Activation messages (CreateCoordinationContext and CreateCoordinationContextResponse).</span></span>  
  
- <span data-ttu-id="e7a62-146">Kayıt iletileri (kayıt ve RegisterResponse)</span><span class="sxs-lookup"><span data-stu-id="e7a62-146">Registration messages (Register and RegisterResponse)</span></span>  
  
- <span data-ttu-id="e7a62-147">Protokol iletileri (hazırlama, geri alma, işleme, iptal edildi ve benzeri).</span><span class="sxs-lookup"><span data-stu-id="e7a62-147">Protocol messages (Prepare, Rollback, Commit, Aborted, and so on).</span></span>  
  
- <span data-ttu-id="e7a62-148">Uygulama iletileri.</span><span class="sxs-lookup"><span data-stu-id="e7a62-148">Application messages.</span></span>  
  
 <span data-ttu-id="e7a62-149">İlk üç ileti sınıflarını hareket yöneticisi iletileri kabul edilir ve bunların bağlama yapılandırması "Uygulama ileti değişimi" Bu konunun ilerleyen bölümlerinde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="e7a62-149">The first three message classes are considered Transaction Manager messages and their binding configuration is described in the "Application Message Exchange" later in this topic.</span></span> <span data-ttu-id="e7a62-150">İletinin dördüncü sınıfını uygulamaya ileti ve "İleti örnekler" bölümünde bu konunun ilerleyen bölümlerinde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="e7a62-150">The fourth class of message is application to application messages and is described in the "Message Examples" section later in this topic.</span></span> <span data-ttu-id="e7a62-151">Bu bölümde, bu sınıfların her biri için WCF tarafından kullanılan protokolü bağlamalarını açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e7a62-151">This section describes the protocol bindings used for each of these classes by WCF.</span></span>  
  
 <span data-ttu-id="e7a62-152">Aşağıdaki XML ad alanları ve ilişkili ön ekleri, bu belge boyunca kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e7a62-152">The following XML Namespaces and associated prefixes are used throughout this document.</span></span>  
  
|<span data-ttu-id="e7a62-153">Ön eki</span><span class="sxs-lookup"><span data-stu-id="e7a62-153">Prefix</span></span>|<span data-ttu-id="e7a62-154">Namespace URI'si</span><span class="sxs-lookup"><span data-stu-id="e7a62-154">Namespace URI</span></span>|  
|------------|-------------------|  
|<span data-ttu-id="e7a62-155">s11</span><span class="sxs-lookup"><span data-stu-id="e7a62-155">s11</span></span>|http://schemas.xmlsoap.org/soap/envelope|  
|<span data-ttu-id="e7a62-156">wsa</span><span class="sxs-lookup"><span data-stu-id="e7a62-156">wsa</span></span>|http://www.w3.org/2004/08/addressing|  
|<span data-ttu-id="e7a62-157">wscoor</span><span class="sxs-lookup"><span data-stu-id="e7a62-157">wscoor</span></span>|http://schemas.xmlsoap.org/ws/2004/10/wscoor|  
|<span data-ttu-id="e7a62-158">wsat</span><span class="sxs-lookup"><span data-stu-id="e7a62-158">wsat</span></span>|http://schemas.xmlsoap.org/ws/2004/10/wsat|  
|<span data-ttu-id="e7a62-159">t</span><span class="sxs-lookup"><span data-stu-id="e7a62-159">t</span></span>|http://schemas.xmlsoap.org/ws/2005/02/trust|  
|<span data-ttu-id="e7a62-160">o</span><span class="sxs-lookup"><span data-stu-id="e7a62-160">o</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd|  
|<span data-ttu-id="e7a62-161">xsd</span><span class="sxs-lookup"><span data-stu-id="e7a62-161">xsd</span></span>|http://www.w3.org/2001/XMLSchema|  
  
## <a name="transaction-manager-bindings"></a><span data-ttu-id="e7a62-162">İşlem Yöneticisi bağlamaları</span><span class="sxs-lookup"><span data-stu-id="e7a62-162">Transaction Manager Bindings</span></span>  
 <span data-ttu-id="e7a62-163">R1001: İşlem yöneticileri, WS-Atomic işlem ve WS-koordinasyon ileti alışverişlerinde SOAP 1.1 ve WS-Addressing 2004/08 kullanmalısınız.</span><span class="sxs-lookup"><span data-stu-id="e7a62-163">R1001: Transaction Managers must use SOAP 1.1 and WS-Addressing 2004/08 for WS-Atomic Transaction and WS-Coordination message exchanges.</span></span>  
  
 <span data-ttu-id="e7a62-164">Uygulama iletileri, bu bağlamaları için kısıtlı değildir ve daha sonra açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="e7a62-164">Application messages are not constrained to these bindings and are described later.</span></span>  
  
### <a name="transaction-manager-https-binding"></a><span data-ttu-id="e7a62-165">İşlem Yöneticisi HTTPS bağlama</span><span class="sxs-lookup"><span data-stu-id="e7a62-165">Transaction Manager HTTPS Binding</span></span>  
 <span data-ttu-id="e7a62-166">İşlem Yöneticisi HTTPS bağlaması güvenliği sağlamak ve işlem ağacında her gönderenin alıcı çifti arasında güven oluşturma için yalnızca Aktarım güvenliği kullanır.</span><span class="sxs-lookup"><span data-stu-id="e7a62-166">The transaction manager HTTPS binding relies solely on transport security to achieve security and establish trust between each sender-receiver pair in the transaction tree.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="e7a62-167">HTTPS aktarımı yapılandırması</span><span class="sxs-lookup"><span data-stu-id="e7a62-167">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="e7a62-168">X.509 sertifikaları, hareket yöneticisi kimliğini oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e7a62-168">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="e7a62-169">İstemci/sunucu kimlik doğrulaması ve yetkilendirme istemci/sunucu uygulama ayrıntısı bırakılır:</span><span class="sxs-lookup"><span data-stu-id="e7a62-169">Client/server authentication is required, and client/server authorization is left as an implementation detail:</span></span>  
  
- <span data-ttu-id="e7a62-170">R1111: Kablo üzerinden sunulan X.509 sertifikaları, kaynak makinenin tam etki alanı adını (FQDN) eşleşen bir konu adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e7a62-170">R1111: X.509 certificates presented over the wire must have a subject name that matches the fully qualified domain name (FQDN) of the originating machine.</span></span>  
  
- <span data-ttu-id="e7a62-171">B1112: DNS başarılı olması için her gönderenin alıcı çifti arasında X.509 konu adı denetimleri için sistemdeki işlevsel olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e7a62-171">B1112: DNS must be functional between each sender-receiver pair in the system for X.509 subject name checks to succeed.</span></span>  
  
#### <a name="activation-and-registration-binding-configuration"></a><span data-ttu-id="e7a62-172">Etkinleştirme ve yapılandırma bağlama kaydı</span><span class="sxs-lookup"><span data-stu-id="e7a62-172">Activation and Registration Binding Configuration</span></span>  
 <span data-ttu-id="e7a62-173">WCF HTTPS üzerinden istek/yanıt bağıntısı ile çift yönlü bağlama gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e7a62-173">WCF requires request/reply duplex binding with correlation over HTTPS.</span></span> <span data-ttu-id="e7a62-174">(WS-Atomic işlem, Bölüm 8 bağıntı ve istek/yanıt iletisi exchange desenlerinin açıklamaları hakkında daha fazla bilgi için bkz.)</span><span class="sxs-lookup"><span data-stu-id="e7a62-174">(For more information about correlation and descriptions of the request/reply message exchange patterns, see WS-Atomic Transaction, Section 8.)</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="e7a62-175">2PC Protokolü bağlama yapılandırması</span><span class="sxs-lookup"><span data-stu-id="e7a62-175">2PC Protocol Binding Configuration</span></span>  
 <span data-ttu-id="e7a62-176">WCF HTTPS üzerinden tek yönlü (veri birimi) iletileri destekler.</span><span class="sxs-lookup"><span data-stu-id="e7a62-176">WCF supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="e7a62-177">İletileri arasında bağıntı uygulama ayrıntısı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="e7a62-177">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="e7a62-178">B2131: Uygulamaları desteklemelidir `wsa:ReferenceParameters` WS-WCF'ın 2PC iletilerinin bağıntı elde etmek için Addressing içinde açıklandığı gibi.</span><span class="sxs-lookup"><span data-stu-id="e7a62-178">B2131: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of WCF’s 2PC messages.</span></span>  
  
### <a name="transaction-manager-mixed-security-binding"></a><span data-ttu-id="e7a62-179">İşlem Yöneticisi karma güvenliği bağlama</span><span class="sxs-lookup"><span data-stu-id="e7a62-179">Transaction Manager Mixed Security Binding</span></span>  
 <span data-ttu-id="e7a62-180">Bir alternatif kimlik kurulması amacıyla WS-koordinasyon verilen belirteç modeli ile birlikte bu kullanımları aktarım güvenliği bağlama (karışık mod) budur.</span><span class="sxs-lookup"><span data-stu-id="e7a62-180">This is an alternate (mixed mode) binding that uses transport security combined with the  WS-Coordination Issued Token model for identity establishment purposes.</span></span>  <span data-ttu-id="e7a62-181">Etkinleştirme ve kayıt iki bağlaması arasında farklılık gösteren yalnızca öğelerdir.</span><span class="sxs-lookup"><span data-stu-id="e7a62-181">Activation and Registration are the only elements that differ between the two bindings.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="e7a62-182">HTTPS aktarımı yapılandırması</span><span class="sxs-lookup"><span data-stu-id="e7a62-182">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="e7a62-183">X.509 sertifikaları, hareket yöneticisi kimliğini oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e7a62-183">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="e7a62-184">İstemci/sunucu kimlik doğrulaması ve yetkilendirme istemci/sunucu uygulama ayrıntısı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="e7a62-184">Client/Server authentication is required, and client/server authorization is left as an implementation detail.</span></span>  
  
#### <a name="activation-message-binding-configuration"></a><span data-ttu-id="e7a62-185">Etkinleştirme ileti bağlama yapılandırması</span><span class="sxs-lookup"><span data-stu-id="e7a62-185">Activation Message Binding Configuration</span></span>  
 <span data-ttu-id="e7a62-186">Genellikle kendi yerel hareket yöneticisi ile bir uygulama arasında gerçekleştiği için etkinleştirme iletileri birlikte çalışabilirlik genellikle katılmaz.</span><span class="sxs-lookup"><span data-stu-id="e7a62-186">Activation Messages usually do not participate in interoperability because they typically occur between an application and its local Transaction Manager.</span></span>  
  
 <span data-ttu-id="e7a62-187">B1221: WCF çift yönlü bir HTTPS bağlama kullanır (açıklanan [Mesajlaşma protokolleri](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) etkinleştirme iletileri.</span><span class="sxs-lookup"><span data-stu-id="e7a62-187">B1221: WCF uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) for Activation messages.</span></span> <span data-ttu-id="e7a62-188">WS-Addressing 2004/08 kullanarak istek ve yanıt iletilerinin ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="e7a62-188">Request and Reply messages are correlated using WS-Addressing 2004/08.</span></span>  
  
 <span data-ttu-id="e7a62-189">WS-Atomic işlem belirtimi, Bölüm 8, bağıntı ve ileti exchange desenleri hakkında daha fazla ayrıntıları açıklanır.</span><span class="sxs-lookup"><span data-stu-id="e7a62-189">WS-Atomic Transaction specification, Section 8, describes further details about correlation and the message exchange patterns.</span></span>  
  
- <span data-ttu-id="e7a62-190">R1222: Alma bağlı bir `CreateCoordinationContext`, düzenleyici dağıtmalı bir `SecurityContextToken` ile ilişkili gizli `STx`.</span><span class="sxs-lookup"><span data-stu-id="e7a62-190">R1222: Upon receiving a `CreateCoordinationContext`, the Coordinator must issue a `SecurityContextToken` with associated secret `STx`.</span></span> <span data-ttu-id="e7a62-191">Bu belirteç içinde döndürülen bir `t:IssuedTokens` WS-Güven belirtimini takip başlığı.</span><span class="sxs-lookup"><span data-stu-id="e7a62-191">This token is returned inside a `t:IssuedTokens` header following WS-Trust specification.</span></span>  
  
- <span data-ttu-id="e7a62-192">R1223: Etkinleştirme var olan bir düzenleme bağlamı içinde ortaya çıkarsa `t:IssuedTokens` üstbilgiyle `SecurityContextToken` var olan ilişkili bağlam gerekir akışını `CreateCoordinationContext` ileti.</span><span class="sxs-lookup"><span data-stu-id="e7a62-192">R1223: If Activation occurs within an existing Coordination Context, the `t:IssuedTokens` header with the `SecurityContextToken` associated with existing Context must flow on the `CreateCoordinationContext` message.</span></span>  
  
 <span data-ttu-id="e7a62-193">Yeni bir `t:IssuedTokens` üstbilgi giden eklemek için oluşturulacak `wscoor:CreateCoordinationContextResponse` ileti.</span><span class="sxs-lookup"><span data-stu-id="e7a62-193">A new `t:IssuedTokens` header should be generated for attaching to the outgoing `wscoor:CreateCoordinationContextResponse` message.</span></span>  
  
#### <a name="registration-message-binding-configuration"></a><span data-ttu-id="e7a62-194">Kayıt iletisi bağlama yapılandırması</span><span class="sxs-lookup"><span data-stu-id="e7a62-194">Registration Message Binding Configuration</span></span>  
 <span data-ttu-id="e7a62-195">B1231: WCF çift yönlü bir HTTPS bağlama kullanır (açıklanan [Mesajlaşma protokolleri](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)).</span><span class="sxs-lookup"><span data-stu-id="e7a62-195">B1231: WCF uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)).</span></span> <span data-ttu-id="e7a62-196">WS-Addressing 2004/08 kullanarak istek ve yanıt iletilerinin ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="e7a62-196">Request and Reply messages are correlated using WS-Addressing 2004/08.</span></span>  
  
 <span data-ttu-id="e7a62-197">WS-AtomicTransaction, Bölüm 8 açıklar daha fazla ayrıntı bağıntı ve açıklamaları ileti exchange desenleri hakkında.</span><span class="sxs-lookup"><span data-stu-id="e7a62-197">WS-AtomicTransaction, Section 8, describes further details about correlation and descriptions of the message exchange patterns.</span></span>  
  
 <span data-ttu-id="e7a62-198">R1232: Giden `wscoor:Register` iletileri kullanmalıdır `IssuedTokenOverTransport` kimlik doğrulama modu açıklanan [güvenlik protokollerini](../../../../docs/framework/wcf/feature-details/security-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="e7a62-198">R1232: Outgoing `wscoor:Register` messages must use the `IssuedTokenOverTransport` authentication mode described in [Security Protocols](../../../../docs/framework/wcf/feature-details/security-protocols.md).</span></span>  
  
 <span data-ttu-id="e7a62-199">`wsse:Timestamp` Öğesi kullanılarak imzalanmalıdır `SecurityContextToken STx` verildi.</span><span class="sxs-lookup"><span data-stu-id="e7a62-199">The `wsse:Timestamp` element must be signed using the `SecurityContextToken STx` issued.</span></span> <span data-ttu-id="e7a62-200">Bu imza, belirli bir işlemle ilişkili belirtecin kanıtını olduğu ve işlemde kaydetme katılımcı kimliğini doğrulamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e7a62-200">This signature is a proof of possession of the token associated with particular transaction and is used to authenticate a participant enlisting in the transaction.</span></span> <span data-ttu-id="e7a62-201">HTTPS üzerinden RegistrationResponse ileti gönderilir.</span><span class="sxs-lookup"><span data-stu-id="e7a62-201">The RegistrationResponse message is sent back over HTTPS.</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="e7a62-202">2PC Protokolü bağlama yapılandırması</span><span class="sxs-lookup"><span data-stu-id="e7a62-202">2PC Protocol Binding Configuration</span></span>  
 <span data-ttu-id="e7a62-203">WCF HTTPS üzerinden tek yönlü (veri birimi) iletileri destekler.</span><span class="sxs-lookup"><span data-stu-id="e7a62-203">WCF supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="e7a62-204">İletileri arasında bağıntı uygulama ayrıntısı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="e7a62-204">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="e7a62-205">B2131: Uygulamaları desteklemelidir `wsa:ReferenceParameters` WS-WCF'ın 2PC iletilerinin bağıntı elde etmek için Addressing içinde açıklandığı gibi.</span><span class="sxs-lookup"><span data-stu-id="e7a62-205">B2131: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of WCF’s 2PC messages.</span></span>  
  
## <a name="application-message-exchange"></a><span data-ttu-id="e7a62-206">Uygulama ileti değişimi</span><span class="sxs-lookup"><span data-stu-id="e7a62-206">Application Message Exchange</span></span>  
 <span data-ttu-id="e7a62-207">Uygulamaları bağlama aşağıdaki güvenlik gereksinimlerini karşıladığı sürece herhangi belirli bağlama-uygulamaya iletileri için kullanılacak ücretsizdir:</span><span class="sxs-lookup"><span data-stu-id="e7a62-207">Applications are free to use any particular binding for application-to-application messages, as long as the binding meets the following security requirements:</span></span>  
  
- <span data-ttu-id="e7a62-208">R2001: Uygulama uygulama iletileri gerekir akış `t:IssuedTokens` başlığı ile birlikte `CoordinationContext` iletisinin üst bilgisindeki.</span><span class="sxs-lookup"><span data-stu-id="e7a62-208">R2001: Application-to-application messages must flow the `t:IssuedTokens` header along with the `CoordinationContext` in the header of the message.</span></span>  
  
- <span data-ttu-id="e7a62-209">R2002: Bütünlüğü ve gizliliği `t:IssuedToken` sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e7a62-209">R2002: Integrity and confidentiality of `t:IssuedToken` must be provided.</span></span>  
  
 <span data-ttu-id="e7a62-210">`CoordinationContext` Üst bilgiyi içeren `wscoor:Identifier`.</span><span class="sxs-lookup"><span data-stu-id="e7a62-210">The `CoordinationContext` header contains `wscoor:Identifier`.</span></span> <span data-ttu-id="e7a62-211">While tanımını `xsd:AnyURI` mutlak ve göreli URI'ler kullanımına izin verir WCF yalnızca destekler `wscoor:Identifiers`, mutlak bir URI'leri olduğu.</span><span class="sxs-lookup"><span data-stu-id="e7a62-211">While the definition of `xsd:AnyURI` allows the use of both absolute and relative URIs, WCF supports only `wscoor:Identifiers`, which are absolute URIs.</span></span>  
  
 <span data-ttu-id="e7a62-212">Varsa `wscoor:Identifier` , `wscoor:CoordinationContext` göreli bir URI işlem WCF hizmetlerinden hatalar döndürülür.</span><span class="sxs-lookup"><span data-stu-id="e7a62-212">If the `wscoor:Identifier` of the `wscoor:CoordinationContext` is a relative URI, faults will be returned from transactional WCF services.</span></span>  
  
## <a name="message-examples"></a><span data-ttu-id="e7a62-213">İleti örnekleri</span><span class="sxs-lookup"><span data-stu-id="e7a62-213">Message Examples</span></span>  
  
### <a name="createcoordinationcontext-requestresponse-messages"></a><span data-ttu-id="e7a62-214">CreateCoordinationContext istek/yanıt iletilerini</span><span class="sxs-lookup"><span data-stu-id="e7a62-214">CreateCoordinationContext Request/Response Messages</span></span>  
 <span data-ttu-id="e7a62-215">Aşağıdaki ileti, istek/yanıt deseni izler.</span><span class="sxs-lookup"><span data-stu-id="e7a62-215">The following messages follow a request/response pattern.</span></span>  
  
#### <a name="createcoordinationcontext"></a><span data-ttu-id="e7a62-216">CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="e7a62-216">CreateCoordinationContext</span></span>  
  
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
  
#### <a name="createcoordinationcontextresponse"></a><span data-ttu-id="e7a62-217">CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="e7a62-217">CreateCoordinationContextResponse</span></span>  
  
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
  
### <a name="registration-messages"></a><span data-ttu-id="e7a62-218">Kayıt iletileri</span><span class="sxs-lookup"><span data-stu-id="e7a62-218">Registration Messages</span></span>  
 <span data-ttu-id="e7a62-219">Aşağıdaki iletileri, kayıt iletileri edilir.</span><span class="sxs-lookup"><span data-stu-id="e7a62-219">The following messages are registration messages.</span></span>  
  
#### <a name="register"></a><span data-ttu-id="e7a62-220">Yazmaç</span><span class="sxs-lookup"><span data-stu-id="e7a62-220">Register</span></span>  
  
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
  
#### <a name="register-response"></a><span data-ttu-id="e7a62-221">Yanıtı kaydedin</span><span class="sxs-lookup"><span data-stu-id="e7a62-221">Register Response</span></span>  
  
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
  
### <a name="two-phase-commit-protocol-messages"></a><span data-ttu-id="e7a62-222">İki aşaması yürütme protokol iletileri</span><span class="sxs-lookup"><span data-stu-id="e7a62-222">Two Phase Commit Protocol Messages</span></span>  
 <span data-ttu-id="e7a62-223">Aşağıdaki ileti iki aşamalı kayıt (2PC) protokolüne ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="e7a62-223">The following message relates to the two-phase commit (2PC) protocol.</span></span>  
  
#### <a name="commit"></a><span data-ttu-id="e7a62-224">İşleme</span><span class="sxs-lookup"><span data-stu-id="e7a62-224">Commit</span></span>  
  
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
  
### <a name="application-messages"></a><span data-ttu-id="e7a62-225">Uygulama iletileri</span><span class="sxs-lookup"><span data-stu-id="e7a62-225">Application Messages</span></span>  
 <span data-ttu-id="e7a62-226">Aşağıdaki iletileri uygulama iletileri edilir.</span><span class="sxs-lookup"><span data-stu-id="e7a62-226">The following messages are application messages.</span></span>  
  
#### <a name="application-message-request"></a><span data-ttu-id="e7a62-227">Uygulama isteği iletisi</span><span class="sxs-lookup"><span data-stu-id="e7a62-227">Application message-Request</span></span>  
  
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

---
title: İşlem Protokolleri
ms.date: 03/30/2017
ms.assetid: 2820b0ec-2f32-430c-b299-1f0e95e1f2dc
ms.openlocfilehash: 8841a9cf414ae94da7e63bd7312a3c541ab6de1b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33508449"
---
# <a name="transaction-protocols"></a><span data-ttu-id="7c057-102">İşlem Protokolleri</span><span class="sxs-lookup"><span data-stu-id="7c057-102">Transaction Protocols</span></span>
<span data-ttu-id="7c057-103">Windows Communication Foundation (WCF) WS-Atomic işlemleri ve Web Hizmetleri koordinasyonu protokollerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="7c057-103">Windows Communication Foundation (WCF) implements WS-Atomic Transaction and WS-Coordination protocols.</span></span>  
  
|<span data-ttu-id="7c057-104">Belirtim/belgesi</span><span class="sxs-lookup"><span data-stu-id="7c057-104">Specification/Document</span></span>|<span data-ttu-id="7c057-105">Sürüm</span><span class="sxs-lookup"><span data-stu-id="7c057-105">Version</span></span>|<span data-ttu-id="7c057-106">Bağlantı</span><span class="sxs-lookup"><span data-stu-id="7c057-106">Link</span></span>|  
|-----------------------------|-------------|----------|  
|<span data-ttu-id="7c057-107">WS-düzenleme</span><span class="sxs-lookup"><span data-stu-id="7c057-107">WS-Coordination</span></span>|<span data-ttu-id="7c057-108">1.0</span><span class="sxs-lookup"><span data-stu-id="7c057-108">1.0</span></span><br /><br /> <span data-ttu-id="7c057-109">1.1</span><span class="sxs-lookup"><span data-stu-id="7c057-109">1.1</span></span>|[http://go.microsoft.com/fwlink/?LinkId=96104](http://go.microsoft.com/fwlink/?LinkId=96104)<br /><br /> [http://go.microsoft.com/fwlink/?LinkId=96079](http://go.microsoft.com/fwlink/?LinkId=96079)|  
|<span data-ttu-id="7c057-110">WS-AtomicTransaction</span><span class="sxs-lookup"><span data-stu-id="7c057-110">WS-AtomicTransaction</span></span>|<span data-ttu-id="7c057-111">1.0</span><span class="sxs-lookup"><span data-stu-id="7c057-111">1.0</span></span><br /><br /> <span data-ttu-id="7c057-112">1.1</span><span class="sxs-lookup"><span data-stu-id="7c057-112">1.1</span></span>|[http://go.microsoft.com/fwlink/?LinkId=96080](http://go.microsoft.com/fwlink/?LinkId=96080)<br /><br /> http://go.microsoft.com/fwlink/?LinkId=96081|  
  
 <span data-ttu-id="7c057-113">Bu protokol belirtimleri üzerinde birlikte çalışabilirlik iki düzeyde gereklidir: uygulamalar arasında arasında işlem yöneticileri (Aşağıdaki şekle bakın).</span><span class="sxs-lookup"><span data-stu-id="7c057-113">Interoperability on these protocol specifications is required at two levels: between applications and between transaction managers (see the following figure).</span></span> <span data-ttu-id="7c057-114">İletisi ve ileti formatları için her iki birlikte çalışabilirlik düzeylerini exchange harika ayrıntılı özellikleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7c057-114">Specifications describe in great detail the message formats and message exchange for both interoperability levels.</span></span> <span data-ttu-id="7c057-115">Normal uygulama exchange için yaptığınız gibi belirli güvenlik, güvenilirlik ve kodlamaları uygulama uygulaması exchange için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="7c057-115">Certain security, reliability, and encodings for application-to-application exchange apply as they do for regular application exchange.</span></span> <span data-ttu-id="7c057-116">Ancak, kullanıcı tarafından genellikle yapılandırılmadığı için işlem yöneticileri başarılı işlerliği belirli bağlama anlaşmasında gerektirir.</span><span class="sxs-lookup"><span data-stu-id="7c057-116">However, successful interoperability between transaction managers requires agreement on the particular binding, because it is usually not configured by the user.</span></span>  
  
 <span data-ttu-id="7c057-117">Bu konu, WS-Atomic işlem (WS-AT) belirtimi bileşimi ile güvenliği açıklar ve işlem yöneticileri arasındaki iletişim için kullanılan güvenli bağlama açıklar.</span><span class="sxs-lookup"><span data-stu-id="7c057-117">This topic describes a composition of the WS-Atomic Transaction (WS-AT) specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="7c057-118">Bu belgede açıklanan yaklaşım başarıyla WS-AT ve Web Hizmetleri koordinasyonu diğer uygulamaları ile test edilmiştir IBM, IONA, Sun Microsystems ve diğerleri de dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="7c057-118">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination including IBM, IONA, Sun Microsystems, and others.</span></span>  
  
 <span data-ttu-id="7c057-119">Aşağıdaki şekil, İşlem Yöneticisi 1 ve işlem yöneticisi 2, iki işlem yöneticileri ve uygulama 1 ve uygulama 2 iki uygulama arasındaki birlikte çalışabilirlik gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7c057-119">The following figure depicts the interoperability between two transaction managers, Transaction Manager 1 and Transaction Manager 2, and two applications, Application 1 and Application 2.</span></span>  
  
 <span data-ttu-id="7c057-120">![İşlem protokolleri](../../../../docs/framework/wcf/feature-details/media/transactionmanagers.gif "TransactionManagers")</span><span class="sxs-lookup"><span data-stu-id="7c057-120">![Transaction Protocols](../../../../docs/framework/wcf/feature-details/media/transactionmanagers.gif "TransactionManagers")</span></span>  
  
 <span data-ttu-id="7c057-121">Bir başlatıcı (ı) ve bir katılımcı (P) tipik bir WS-düzenleme/WS-Atomic işlem senaryoyu göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="7c057-121">Consider a typical WS-Coordination/WS-Atomic Transaction scenario with one Initiator (I) and one Participant (P).</span></span> <span data-ttu-id="7c057-122">Hem Başlatıcı hem de katılımcı olan işlem yöneticileri (ITM ve PTM, sırasıyla).</span><span class="sxs-lookup"><span data-stu-id="7c057-122">Both Initiator and Participant have Transaction Managers, (ITM and PTM, respectively).</span></span> <span data-ttu-id="7c057-123">İki aşamalı yürütme için bu konudaki 2PC olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="7c057-123">Two-phase commit is referred to as 2PC in this topic.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7c057-124">1. CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="7c057-124">1. CreateCoordinationContext</span></span>|<span data-ttu-id="7c057-125">12. Uygulama ileti yanıtı</span><span class="sxs-lookup"><span data-stu-id="7c057-125">12. Application Message Response</span></span>|  
|<span data-ttu-id="7c057-126">2. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="7c057-126">2. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="7c057-127">13. Yürütme (tamamlanma)</span><span class="sxs-lookup"><span data-stu-id="7c057-127">13. Commit (Completion)</span></span>|  
|<span data-ttu-id="7c057-128">3. YAZMAÇ (tamamlanma)</span><span class="sxs-lookup"><span data-stu-id="7c057-128">3. Register (Completion)</span></span>|<span data-ttu-id="7c057-129">14. (2PC) hazırlama</span><span class="sxs-lookup"><span data-stu-id="7c057-129">14. Prepare (2PC)</span></span>|  
|<span data-ttu-id="7c057-130">4. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="7c057-130">4. RegisterResponse</span></span>|<span data-ttu-id="7c057-131">15. (2PC) hazırlama</span><span class="sxs-lookup"><span data-stu-id="7c057-131">15. Prepare (2PC)</span></span>|  
|<span data-ttu-id="7c057-132">5. Uygulama iletisi</span><span class="sxs-lookup"><span data-stu-id="7c057-132">5. Application Message</span></span>|<span data-ttu-id="7c057-133">16. Hazırlanan (2PC)</span><span class="sxs-lookup"><span data-stu-id="7c057-133">16. Prepared (2PC)</span></span>|  
|<span data-ttu-id="7c057-134">6. Bağlamına sahip CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="7c057-134">6. CreateCoordinationContext with Context</span></span>|<span data-ttu-id="7c057-135">17. Hazırlanan (2PC)</span><span class="sxs-lookup"><span data-stu-id="7c057-135">17. Prepared (2PC)</span></span>|  
|<span data-ttu-id="7c057-136">7. YAZMAÇ (dayanıklı)</span><span class="sxs-lookup"><span data-stu-id="7c057-136">7. Register (Durable)</span></span>|<span data-ttu-id="7c057-137">18. Kaydedilmiş (tamamlanma)</span><span class="sxs-lookup"><span data-stu-id="7c057-137">18. Committed (Completion)</span></span>|  
|<span data-ttu-id="7c057-138">8. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="7c057-138">8. RegisterResponse</span></span>|<span data-ttu-id="7c057-139">19. Kayıt (2PC)</span><span class="sxs-lookup"><span data-stu-id="7c057-139">19. Commit (2PC)</span></span>|  
|<span data-ttu-id="7c057-140">9. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="7c057-140">9. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="7c057-141">20. Kayıt (2PC)</span><span class="sxs-lookup"><span data-stu-id="7c057-141">20. Commit (2PC)</span></span>|  
|<span data-ttu-id="7c057-142">10. YAZMAÇ (dayanıklı)</span><span class="sxs-lookup"><span data-stu-id="7c057-142">10. Register (Durable)</span></span>|<span data-ttu-id="7c057-143">21. Kaydedilmiş (2PC)</span><span class="sxs-lookup"><span data-stu-id="7c057-143">21. Committed (2PC)</span></span>|  
|<span data-ttu-id="7c057-144">11. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="7c057-144">11. RegisterResponse</span></span>|<span data-ttu-id="7c057-145">22. Kaydedilmiş (2PC)</span><span class="sxs-lookup"><span data-stu-id="7c057-145">22. Committed (2PC)</span></span>|  
  
 <span data-ttu-id="7c057-146">Bu belge WS-AtomicTransaction belirtiminin bir birleşim ile güvenliği açıklar ve işlem yöneticileri arasındaki iletişim için kullanılan güvenli bağlama açıklar.</span><span class="sxs-lookup"><span data-stu-id="7c057-146">This document describes a composition of the WS-AtomicTransaction specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="7c057-147">Bu belgede açıklanan yaklaşım başarıyla WS-AT ve Web Hizmetleri koordinasyonu diğer uygulamaları ile test edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7c057-147">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination.</span></span>  
  
 <span data-ttu-id="7c057-148">Şekil ve tabloda güvenlik görüş iletilerden dört sınıflarını gösterir:</span><span class="sxs-lookup"><span data-stu-id="7c057-148">The figure and table illustrate four classes of messages from the viewpoint of security:</span></span>  
  
-   <span data-ttu-id="7c057-149">Etkinleştirme iletileri (CreateCoordinationContext ve CreateCoordinationContextResponse).</span><span class="sxs-lookup"><span data-stu-id="7c057-149">Activation messages (CreateCoordinationContext and CreateCoordinationContextResponse).</span></span>  
  
-   <span data-ttu-id="7c057-150">Kayıt iletiler (kaydetme ve RegisterResponse)</span><span class="sxs-lookup"><span data-stu-id="7c057-150">Registration messages (Register and RegisterResponse)</span></span>  
  
-   <span data-ttu-id="7c057-151">Protokol iletileri (hazırlama, geri alma, kaydetme, iptal edildi vb.).</span><span class="sxs-lookup"><span data-stu-id="7c057-151">Protocol messages (Prepare, Rollback, Commit, Aborted, and so on).</span></span>  
  
-   <span data-ttu-id="7c057-152">Uygulama iletileri.</span><span class="sxs-lookup"><span data-stu-id="7c057-152">Application messages.</span></span>  
  
 <span data-ttu-id="7c057-153">İlk üç ileti sınıfları işlem yöneticisi iletileri kabul edilir ve bağlama yapılandırmalarını "Uygulama ileti değişimi" Bu konunun ilerleyen bölümlerinde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="7c057-153">The first three message classes are considered Transaction Manager messages and their binding configuration is described in the "Application Message Exchange" later in this topic.</span></span> <span data-ttu-id="7c057-154">İletinin dördüncü sınıfını uygulamaya iletileri ve bu konunun devamındaki "İletisi örnekler" bölümünde açıklanan.</span><span class="sxs-lookup"><span data-stu-id="7c057-154">The fourth class of message is application to application messages and is described in the "Message Examples" section later in this topic.</span></span> <span data-ttu-id="7c057-155">Bu bölümde bu sınıfların her biri için WCF tarafından kullanılan protokolü bağlamaları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7c057-155">This section describes the protocol bindings used for each of these classes by WCF.</span></span>  
  
 <span data-ttu-id="7c057-156">Aşağıdaki XML ad alanları ve ilişkili önekleri bu belge boyunca kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7c057-156">The following XML Namespaces and associated prefixes are used throughout this document.</span></span>  
  
|<span data-ttu-id="7c057-157">önek</span><span class="sxs-lookup"><span data-stu-id="7c057-157">Prefix</span></span>|<span data-ttu-id="7c057-158">Sürüm</span><span class="sxs-lookup"><span data-stu-id="7c057-158">Version</span></span>|<span data-ttu-id="7c057-159">Namespace URI</span><span class="sxs-lookup"><span data-stu-id="7c057-159">Namespace URI</span></span>|  
|------------|-------------|-------------------|  
|<span data-ttu-id="7c057-160">s11</span><span class="sxs-lookup"><span data-stu-id="7c057-160">s11</span></span>||[http://go.microsoft.com/fwlink/?LinkId=96014](http://go.microsoft.com/fwlink/?LinkId=96014)|  
|<span data-ttu-id="7c057-161">wsa</span><span class="sxs-lookup"><span data-stu-id="7c057-161">wsa</span></span>|<span data-ttu-id="7c057-162">Öncesi 1.0</span><span class="sxs-lookup"><span data-stu-id="7c057-162">Pre-1.0</span></span><br /><br /> <span data-ttu-id="7c057-163">1.0</span><span class="sxs-lookup"><span data-stu-id="7c057-163">1.0</span></span>|http://www.w3.org/2004/08/addressing<br /><br /> [http://go.microsoft.com/fwlink/?LinkId=96022](http://go.microsoft.com/fwlink/?LinkId=96022)|  
|<span data-ttu-id="7c057-164">wscoor</span><span class="sxs-lookup"><span data-stu-id="7c057-164">wscoor</span></span>|<span data-ttu-id="7c057-165">1.0</span><span class="sxs-lookup"><span data-stu-id="7c057-165">1.0</span></span><br /><br /> <span data-ttu-id="7c057-166">1.1</span><span class="sxs-lookup"><span data-stu-id="7c057-166">1.1</span></span>|[http://go.microsoft.com/fwlink/?LinkId=96078](http://go.microsoft.com/fwlink/?LinkId=96078)<br /><br /> [http://go.microsoft.com/fwlink/?LinkId=96079](http://go.microsoft.com/fwlink/?LinkId=96079)|  
|<span data-ttu-id="7c057-167">WSAT</span><span class="sxs-lookup"><span data-stu-id="7c057-167">wsat</span></span>|<span data-ttu-id="7c057-168">1.0</span><span class="sxs-lookup"><span data-stu-id="7c057-168">1.0</span></span><br /><br /> <span data-ttu-id="7c057-169">1.1</span><span class="sxs-lookup"><span data-stu-id="7c057-169">1.1</span></span>|[http://go.microsoft.com/fwlink/?LinkId=96080](http://go.microsoft.com/fwlink/?LinkId=96080)<br /><br /> [http://go.microsoft.com/fwlink/?LinkId=96081](http://go.microsoft.com/fwlink/?LinkId=96081)|  
|<span data-ttu-id="7c057-170">t</span><span class="sxs-lookup"><span data-stu-id="7c057-170">t</span></span>|<span data-ttu-id="7c057-171">Öncesi 1.3</span><span class="sxs-lookup"><span data-stu-id="7c057-171">Pre-1.3</span></span><br /><br /> <span data-ttu-id="7c057-172">1.3</span><span class="sxs-lookup"><span data-stu-id="7c057-172">1.3</span></span>|[http://go.microsoft.com/fwlink/?LinkId=96082](http://go.microsoft.com/fwlink/?LinkId=96082)<br /><br /> [http://go.microsoft.com/fwlink/?LinkId=96100](http://go.microsoft.com/fwlink/?LinkId=96100)|  
|<span data-ttu-id="7c057-173">o</span><span class="sxs-lookup"><span data-stu-id="7c057-173">o</span></span>||[http://go.microsoft.com/fwlink/?LinkId=96101](http://go.microsoft.com/fwlink/?LinkId=96101)|  
|<span data-ttu-id="7c057-174">XSD</span><span class="sxs-lookup"><span data-stu-id="7c057-174">xsd</span></span>||[http://go.microsoft.com/fwlink/?LinkId=96102](http://go.microsoft.com/fwlink/?LinkId=96102)|  
  
## <a name="transaction-manager-bindings"></a><span data-ttu-id="7c057-175">İşlem Yöneticisi bağlamaları</span><span class="sxs-lookup"><span data-stu-id="7c057-175">Transaction Manager Bindings</span></span>  
 <span data-ttu-id="7c057-176">R1001: WS-AT 1.0 işlemde katılan işlem yöneticileri SOAP 1.1 ve WS adresleme 2004/08 WS-Atomic işlemleri ve Web Hizmetleri koordinasyonu ileti alışverişlerinde için kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7c057-176">R1001: Transaction Managers participating in a WS-AT 1.0 transaction must use SOAP 1.1 and WS-Addressing 2004/08 for WS-Atomic Transaction and WS-Coordination message exchanges.</span></span>  
  
 <span data-ttu-id="7c057-177">R1002: WS-AT 1.1 işlemde katılan işlem yöneticileri SOAP 1.1 ve WS adresleme 2005/08 WS-Atomic işlemleri ve Web Hizmetleri koordinasyonu ileti alışverişlerinde için kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7c057-177">R1002: Transaction Managers participating in a WS-AT 1.1 transaction must use SOAP 1.1 and WS-Addressing 2005/08 for WS-Atomic Transaction and WS-Coordination message exchanges.</span></span>  
  
 <span data-ttu-id="7c057-178">Uygulama iletileri bu bağlamaların kısıtlı değildir ve daha sonra açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7c057-178">Application messages are not constrained to these bindings and are described later.</span></span>  
  
### <a name="transaction-manager-https-binding"></a><span data-ttu-id="7c057-179">İşlem Yöneticisi HTTPS bağlama</span><span class="sxs-lookup"><span data-stu-id="7c057-179">Transaction Manager HTTPS Binding</span></span>  
 <span data-ttu-id="7c057-180">İşlem Yöneticisi HTTPS bağlamasını güvenliği sağlamak ve işlem ağacında her gönderenin alıcı çifti arasında güven oluşturmak için yalnızca taşıma güvenliği kullanır.</span><span class="sxs-lookup"><span data-stu-id="7c057-180">The transaction manager HTTPS binding relies solely on transport security to achieve security and establish trust between each sender-receiver pair in the transaction tree.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="7c057-181">HTTPS taşıma yapılandırması</span><span class="sxs-lookup"><span data-stu-id="7c057-181">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="7c057-182">X.509 sertifikaları işlem yöneticisi kimliğini oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7c057-182">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="7c057-183">İstemci/sunucu kimlik doğrulaması gerekli değildir ve istemci/sunucu yetkilendirme uygulama ayrıntı olarak kalır:</span><span class="sxs-lookup"><span data-stu-id="7c057-183">Client/server authentication is required, and client/server authorization is left as an implementation detail:</span></span>  
  
-   <span data-ttu-id="7c057-184">R1111: kablo üzerinden sunulan X.509 sertifikaları kaynak makinenin tam etki alanı adını (FQDN) ile eşleşen bir konu adına sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7c057-184">R1111: X.509 certificates presented over the wire must have a subject name that matches the fully qualified domain name (FQDN) of the originating machine.</span></span>  
  
-   <span data-ttu-id="7c057-185">B1112: DNS başarılı olması için her gönderenin alıcı çifti arasında X.509 konu adı denetimleri için sistemdeki işlevsel olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7c057-185">B1112: DNS must be functional between each sender-receiver pair in the system for X.509 subject name checks to succeed.</span></span>  
  
#### <a name="activation-and-registration-binding-configuration"></a><span data-ttu-id="7c057-186">Etkinleştirme ve yapılandırma bağlama kayıt</span><span class="sxs-lookup"><span data-stu-id="7c057-186">Activation and Registration Binding Configuration</span></span>  
 <span data-ttu-id="7c057-187">WCF istek/yanıt çift yönlü bağıntı bağlamayla HTTPS üzerinden gerektirir.</span><span class="sxs-lookup"><span data-stu-id="7c057-187">WCF requires request/reply duplex binding with correlation over HTTPS.</span></span> <span data-ttu-id="7c057-188">(WS-Atomic işlemleri, Bölüm 8 bağıntı ve istek/yanıt iletisi exchange desenleri açıklamalarını hakkında daha fazla bilgi için bkz.)</span><span class="sxs-lookup"><span data-stu-id="7c057-188">(For more information about correlation and descriptions of the request/reply message exchange patterns, see WS-Atomic Transaction, Section 8.)</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="7c057-189">2PC Protokolü bağlama yapılandırması</span><span class="sxs-lookup"><span data-stu-id="7c057-189">2PC Protocol Binding Configuration</span></span>  
 <span data-ttu-id="7c057-190">WCF HTTPS üzerinden tek yönlü (datagram) iletileri destekler.</span><span class="sxs-lookup"><span data-stu-id="7c057-190">WCF supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="7c057-191">Bağıntı iletileri arasında bir uygulama ayrıntı olarak kalır.</span><span class="sxs-lookup"><span data-stu-id="7c057-191">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="7c057-192">B1131: Uygulamaları desteklemelidir `wsa:ReferenceParameters` WS-WCF'ın 2PC iletilerinin bağıntı elde etmek için adresleme içinde açıklandığı gibi.</span><span class="sxs-lookup"><span data-stu-id="7c057-192">B1131: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of WCF’s 2PC messages.</span></span>  
  
### <a name="transaction-manager-mixed-security-binding"></a><span data-ttu-id="7c057-193">İşlem Yöneticisi güvenlik bağlama karma</span><span class="sxs-lookup"><span data-stu-id="7c057-193">Transaction Manager Mixed Security Binding</span></span>  
 <span data-ttu-id="7c057-194">Bu kimlik kurulması amacıyla Web Hizmetleri koordinasyonu verilen belirteç modeli ile birlikte bu kullanımları taşıma güvenliği bağlama bir alternatif (karma mod) olur.</span><span class="sxs-lookup"><span data-stu-id="7c057-194">This is an alternate (mixed mode) binding that uses transport security combined with the WS-Coordination Issued Token model for identity establishment purposes.</span></span> <span data-ttu-id="7c057-195">Etkinleştirme ve kayıt arasında iki bağlamaları farklı yalnızca öğelerdir.</span><span class="sxs-lookup"><span data-stu-id="7c057-195">Activation and Registration are the only elements that differ between the two bindings.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="7c057-196">HTTPS taşıma yapılandırması</span><span class="sxs-lookup"><span data-stu-id="7c057-196">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="7c057-197">X.509 sertifikaları işlem yöneticisi kimliğini oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7c057-197">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="7c057-198">İstemci/sunucu kimlik doğrulaması gerekli değildir ve istemci/sunucu yetkilendirme uygulama ayrıntı olarak kalır.</span><span class="sxs-lookup"><span data-stu-id="7c057-198">Client/Server authentication is required, and client/server authorization is left as an implementation detail.</span></span>  
  
#### <a name="activation-message-binding-configuration"></a><span data-ttu-id="7c057-199">Etkinleştirme ileti bağlama yapılandırması</span><span class="sxs-lookup"><span data-stu-id="7c057-199">Activation Message Binding Configuration</span></span>  
 <span data-ttu-id="7c057-200">Genellikle bir uygulama ve onun yerel işlem yöneticisi arasında gerçekleştirildiği için etkinleştirme iletiler birlikte çalışabilirlik genellikle katılma.</span><span class="sxs-lookup"><span data-stu-id="7c057-200">Activation Messages usually do not participate in interoperability because they typically occur between an application and its local Transaction Manager.</span></span>  
  
 <span data-ttu-id="7c057-201">B1221: Çift yönlü HTTPS bağlamasını WCF kullanır (açıklanan [Mesajlaşma protokolleri](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) etkinleştirme iletileri için.</span><span class="sxs-lookup"><span data-stu-id="7c057-201">B1221: WCF uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) for Activation messages.</span></span> <span data-ttu-id="7c057-202">İstek ve yanıt iletileri için WS-AT 1.1 WS adresleme 2004/08 WS-AT 1.0 ve WS adresleme 2005/08 kullanarak bağıntılı olan.</span><span class="sxs-lookup"><span data-stu-id="7c057-202">Request and Reply messages are correlated using WS-Addressing 2004/08 for WS-AT 1.0 and WS-Addressing 2005/08 for WS-AT 1.1.</span></span>  
  
 <span data-ttu-id="7c057-203">WS-Atomic işlem belirtimi, Bölüm 8, Ayrıntılar bağıntı ve ileti exchange desenleri hakkında daha fazla açıklar.</span><span class="sxs-lookup"><span data-stu-id="7c057-203">WS-Atomic Transaction specification, Section 8, describes further details about correlation and the message exchange patterns.</span></span>  
  
-   <span data-ttu-id="7c057-204">R1222: temel alarak bir `CreateCoordinationContext`, düzenleyici dağıtmalı bir `SecurityContextToken` ile ilişkili gizli `STx`.</span><span class="sxs-lookup"><span data-stu-id="7c057-204">R1222: Upon receiving a `CreateCoordinationContext`, the Coordinator must issue a `SecurityContextToken` with associated secret `STx`.</span></span> <span data-ttu-id="7c057-205">Bu belirteç içinde döndürülen bir `t:IssuedTokens` WS-Trust belirtimine aşağıdaki üstbilgi.</span><span class="sxs-lookup"><span data-stu-id="7c057-205">This token is returned inside a `t:IssuedTokens` header following WS-Trust specification.</span></span>  
  
-   <span data-ttu-id="7c057-206">R1223: Etkinleştirme var olan bir düzenleme bağlamı içinde ortaya çıkarsa `t:IssuedTokens` üstbilgiyle `SecurityContextToken` var olan ilişkili gerekir içerik akışını `CreateCoordinationContext` ileti.</span><span class="sxs-lookup"><span data-stu-id="7c057-206">R1223: If Activation occurs within an existing Coordination Context, the `t:IssuedTokens` header with the `SecurityContextToken` associated with existing Context must flow on the `CreateCoordinationContext` message.</span></span>  
  
 <span data-ttu-id="7c057-207">Yeni bir `t:IssuedTokens` giden eklemek için üstbilgi oluşturulacağı `wscoor:CreateCoordinationContextResponse` ileti.</span><span class="sxs-lookup"><span data-stu-id="7c057-207">A new `t:IssuedTokens` header should be generated for attaching to the outgoing `wscoor:CreateCoordinationContextResponse` message.</span></span>  
  
#### <a name="registration-message-binding-configuration"></a><span data-ttu-id="7c057-208">Kayıt iletisi bağlama yapılandırması</span><span class="sxs-lookup"><span data-stu-id="7c057-208">Registration Message Binding Configuration</span></span>  
 <span data-ttu-id="7c057-209">B1231: Çift yönlü HTTPS bağlamasını WCF kullanır (açıklanan [Mesajlaşma protokolleri](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)).</span><span class="sxs-lookup"><span data-stu-id="7c057-209">B1231: WCF uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)).</span></span> <span data-ttu-id="7c057-210">İstek ve yanıt iletileri için WS-AT 1.1 WS adresleme 2004/08 WS-AT 1.0 ve WS adresleme 2005/08 kullanarak bağıntılı olan.</span><span class="sxs-lookup"><span data-stu-id="7c057-210">Request and Reply messages are correlated using WS-Addressing 2004/08 for WS-AT 1.0 and WS-Addressing 2005/08 for WS-AT 1.1.</span></span>  
  
 <span data-ttu-id="7c057-211">WS-AtomicTransaction, Bölüm 8, açıklar daha fazla ayrıntı bağıntı ve ileti exchange desenleri açıklamalarını hakkında.</span><span class="sxs-lookup"><span data-stu-id="7c057-211">WS-AtomicTransaction, Section 8, describes further details about correlation and descriptions of the message exchange patterns.</span></span>  
  
 <span data-ttu-id="7c057-212">R1232: Giden `wscoor:Register` iletileri kullanmalıdır `IssuedTokenOverTransport` kimlik doğrulama modu açıklanan [güvenlik protokolleri](../../../../docs/framework/wcf/feature-details/security-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="7c057-212">R1232: Outgoing `wscoor:Register` messages must use the `IssuedTokenOverTransport` authentication mode described in [Security Protocols](../../../../docs/framework/wcf/feature-details/security-protocols.md).</span></span>  
  
 <span data-ttu-id="7c057-213">`wsse:Timestamp` Öğesi kullanılarak imzalanmalıdır `SecurityContextToken``STx` verilmiş.</span><span class="sxs-lookup"><span data-stu-id="7c057-213">The `wsse:Timestamp` element must be signed using the `SecurityContextToken``STx` issued.</span></span> <span data-ttu-id="7c057-214">Bu imza belirli işlemle ilişkili belirtecinin kanıtını olup işlemde kaydetme katılımcı kimliğini doğrulamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7c057-214">This signature is a proof of possession of the token associated with particular transaction and is used to authenticate a participant enlisting in the transaction.</span></span> <span data-ttu-id="7c057-215">RegistrationResponse ileti HTTPS üzerinden gönderilir.</span><span class="sxs-lookup"><span data-stu-id="7c057-215">The RegistrationResponse message is sent back over HTTPS.</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="7c057-216">2PC Protokolü bağlama yapılandırması</span><span class="sxs-lookup"><span data-stu-id="7c057-216">2PC Protocol Binding Configuration</span></span>  
 <span data-ttu-id="7c057-217">WCF HTTPS üzerinden tek yönlü (datagram) iletileri destekler.</span><span class="sxs-lookup"><span data-stu-id="7c057-217">WCF supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="7c057-218">Bağıntı iletileri arasında bir uygulama ayrıntı olarak kalır.</span><span class="sxs-lookup"><span data-stu-id="7c057-218">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="7c057-219">B1241: Uygulamaları desteklemelidir `wsa:ReferenceParameters` WS-WCF'ın 2PC iletilerinin bağıntı elde etmek için adresleme içinde açıklandığı gibi.</span><span class="sxs-lookup"><span data-stu-id="7c057-219">B1241: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of WCF’s 2PC messages.</span></span>  
  
## <a name="application-message-exchange"></a><span data-ttu-id="7c057-220">Uygulama ileti değişimi</span><span class="sxs-lookup"><span data-stu-id="7c057-220">Application Message Exchange</span></span>  
 <span data-ttu-id="7c057-221">Uygulamaları bağlama aşağıdaki güvenlik gereksinimlerini karşılayan sürece herhangi belirli uygulama uygulaması iletileri için bu bağlamayı kullanmak boş şunlardır:</span><span class="sxs-lookup"><span data-stu-id="7c057-221">Applications are free to use any particular binding for application-to-application messages, as long as the binding meets the following security requirements:</span></span>  
  
-   <span data-ttu-id="7c057-222">R2001: Uygulama uygulaması iletileri akış gerekir `t:IssuedTokens` başlığı ile birlikte `CoordinationContext` ileti üstbilgisinde.</span><span class="sxs-lookup"><span data-stu-id="7c057-222">R2001: Application-to-application messages must flow the `t:IssuedTokens` header along with the `CoordinationContext` in the header of the message.</span></span>  
  
-   <span data-ttu-id="7c057-223">R2002: Bütünlüğü ve gizliliği `t:IssuedToken` sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7c057-223">R2002: Integrity and confidentiality of `t:IssuedToken` must be provided.</span></span>  
  
 <span data-ttu-id="7c057-224">`CoordinationContext` Üst bilgiyi içeren `wscoor:Identifier`.</span><span class="sxs-lookup"><span data-stu-id="7c057-224">The `CoordinationContext` header contains `wscoor:Identifier`.</span></span> <span data-ttu-id="7c057-225">While tanımını `xsd:AnyURI` mutlak ve göreli URI'ler kullanılmasına WCF yalnızca destekler `wscoor:Identifiers`, mutlak URI olduğu.</span><span class="sxs-lookup"><span data-stu-id="7c057-225">While the definition of `xsd:AnyURI` allows the use of both absolute and relative URIs, WCF supports only `wscoor:Identifiers`, which are absolute URIs.</span></span>  
  
 <span data-ttu-id="7c057-226">B2003: Varsa `wscoor:Identifier` , `wscoor:CoordinationContext` göreli bir URI hataları işlem WCF hizmetlerini döndürülecek.</span><span class="sxs-lookup"><span data-stu-id="7c057-226">B2003: If the `wscoor:Identifier` of the `wscoor:CoordinationContext` is a relative URI, faults will be returned from transactional WCF services.</span></span>  
  
## <a name="message-examples"></a><span data-ttu-id="7c057-227">İleti örnekleri</span><span class="sxs-lookup"><span data-stu-id="7c057-227">Message Examples</span></span>  
  
### <a name="createcoordinationcontext-requestresponse-messages"></a><span data-ttu-id="7c057-228">CreateCoordinationContext istek/yanıt iletilerini</span><span class="sxs-lookup"><span data-stu-id="7c057-228">CreateCoordinationContext Request/Response Messages</span></span>  
 <span data-ttu-id="7c057-229">Aşağıdaki ileti, bir istek/yanıt yol izler.</span><span class="sxs-lookup"><span data-stu-id="7c057-229">The following messages follow a request/response pattern.</span></span>  
  
#### <a name="createcoordinationcontext-with-wscoor-10"></a><span data-ttu-id="7c057-230">CreateCoordinationContext WSCoor 1.0 ile</span><span class="sxs-lookup"><span data-stu-id="7c057-230">CreateCoordinationContext with WSCoor 1.0</span></span>  
  
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
  
#### <a name="createcoordinationcontext-with-wscoor-11"></a><span data-ttu-id="7c057-231">CreateCoordinationContext WSCoor 1.1 ile</span><span class="sxs-lookup"><span data-stu-id="7c057-231">CreateCoordinationContext with WSCoor 1.1</span></span>  
  
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
  
#### <a name="createcoordinationcontextresponse-with-trust-pre-13-and-wscoor-10"></a><span data-ttu-id="7c057-232">Güven Pre-1.3 ve WSCoor 1.0 ile CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="7c057-232">CreateCoordinationContextResponse with Trust Pre-1.3 and WSCoor 1.0</span></span>  
  
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
  
#### <a name="createcoordinationcontextresponse-with-trust-13-and-wscoor-11"></a><span data-ttu-id="7c057-233">CreateCoordinationContextResponse güven 1.3 ve WSCoor 1.1</span><span class="sxs-lookup"><span data-stu-id="7c057-233">CreateCoordinationContextResponse with Trust 1.3 and WSCoor 1.1</span></span>  
  
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
xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-     wssecurity-utility-1.0.xsd"   
xmlns:wst=http://docs.oasis-open.org/ws-sx/ws-trust/200512  
xmlns:wsc=http://schemas.xmlsoap.org/ws/2005/02/sc  
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
  ValueType=http://schemas.xmlsoap.org/ws/2005/02/sc/sct  
  URI="http://fabrikam123.com/SCTi"/>  
</wsse:SecurityTokenReference>   
</wst:RequestedAttachedReference>   
<wst:RequestedUnattachedReference>   
<wsse:SecurityTokenReference>   
<wsse:Reference  
 ValueType=http://schemas.xmlsoap.org/ws/2005/02/sc/sct  
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
  
### <a name="registration-messages"></a><span data-ttu-id="7c057-234">Kayıt iletileri</span><span class="sxs-lookup"><span data-stu-id="7c057-234">Registration Messages</span></span>  
 <span data-ttu-id="7c057-235">Aşağıdaki iletileri kayıt iletileri edilir.</span><span class="sxs-lookup"><span data-stu-id="7c057-235">The following messages are registration messages.</span></span>  
  
#### <a name="register-with-wscoor-10"></a><span data-ttu-id="7c057-236">WSCoor 1.0 ile kaydetme</span><span class="sxs-lookup"><span data-stu-id="7c057-236">Register with WSCoor 1.0</span></span>  
  
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
  
#### <a name="register-with-wscoor-11"></a><span data-ttu-id="7c057-237">1.1 WSCoor ile kaydetme</span><span class="sxs-lookup"><span data-stu-id="7c057-237">Register with WSCoor 1.1</span></span>  
  
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
  
#### <a name="register-response-with-wscoor-10"></a><span data-ttu-id="7c057-238">Yanıt WSCoor 1.0 ile kaydetme</span><span class="sxs-lookup"><span data-stu-id="7c057-238">Register Response with WSCoor 1.0</span></span>  
  
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
  
#### <a name="register-response-with-wscoor-11"></a><span data-ttu-id="7c057-239">Yanıt 1.1 WSCoor ile kaydetme</span><span class="sxs-lookup"><span data-stu-id="7c057-239">Register Response with WSCoor 1.1</span></span>  
  
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
  
### <a name="two-phase-commit-protocol-messages"></a><span data-ttu-id="7c057-240">İki aşama yürütme Protokolü iletileri</span><span class="sxs-lookup"><span data-stu-id="7c057-240">Two Phase Commit Protocol Messages</span></span>  
 <span data-ttu-id="7c057-241">Aşağıdaki ileti iki aşamalı kayıt (2PC) protokolüne ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="7c057-241">The following message relates to the two-phase commit (2PC) protocol.</span></span>  
  
#### <a name="commit-with-wsat-10"></a><span data-ttu-id="7c057-242">WSAT 1.0 ile Yürüt</span><span class="sxs-lookup"><span data-stu-id="7c057-242">Commit with WSAT 1.0</span></span>  
  
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
  
#### <a name="commit-with-wsat-11"></a><span data-ttu-id="7c057-243">1.1 WSAT ile Yürüt</span><span class="sxs-lookup"><span data-stu-id="7c057-243">Commit with WSAT 1.1</span></span>  
  
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
  
### <a name="application-messages"></a><span data-ttu-id="7c057-244">Uygulama iletileri</span><span class="sxs-lookup"><span data-stu-id="7c057-244">Application Messages</span></span>  
 <span data-ttu-id="7c057-245">Aşağıdaki iletileri uygulama iletileri edilir.</span><span class="sxs-lookup"><span data-stu-id="7c057-245">The following messages are application messages.</span></span>  
  
#### <a name="application-message-request"></a><span data-ttu-id="7c057-246">Uygulama iletiyi-isteği</span><span class="sxs-lookup"><span data-stu-id="7c057-246">Application message-Request</span></span>  
  
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

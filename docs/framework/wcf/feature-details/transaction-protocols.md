---
title: İşlem Protokolleri
ms.date: 03/30/2017
ms.assetid: 2820b0ec-2f32-430c-b299-1f0e95e1f2dc
ms.openlocfilehash: 559b7ec1539a43ec27010031320be144d6f5e24b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54533773"
---
# <a name="transaction-protocols"></a><span data-ttu-id="9d1dd-102">İşlem Protokolleri</span><span class="sxs-lookup"><span data-stu-id="9d1dd-102">Transaction Protocols</span></span>
<span data-ttu-id="9d1dd-103">Windows Communication Foundation (WCF), WS-Atomic işlem ve WS-koordinasyon protokollerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="9d1dd-103">Windows Communication Foundation (WCF) implements WS-Atomic Transaction and WS-Coordination protocols.</span></span>  
  
|<span data-ttu-id="9d1dd-104">Belirtimi/belge</span><span class="sxs-lookup"><span data-stu-id="9d1dd-104">Specification/Document</span></span>|<span data-ttu-id="9d1dd-105">Sürüm</span><span class="sxs-lookup"><span data-stu-id="9d1dd-105">Version</span></span>|<span data-ttu-id="9d1dd-106">Bağlantı</span><span class="sxs-lookup"><span data-stu-id="9d1dd-106">Link</span></span>|  
|-----------------------------|-------------|----------|  
|<span data-ttu-id="9d1dd-107">WS-düzenleme</span><span class="sxs-lookup"><span data-stu-id="9d1dd-107">WS-Coordination</span></span>|<span data-ttu-id="9d1dd-108">1.0</span><span class="sxs-lookup"><span data-stu-id="9d1dd-108">1.0</span></span><br /><br /> <span data-ttu-id="9d1dd-109">1.1</span><span class="sxs-lookup"><span data-stu-id="9d1dd-109">1.1</span></span>|[https://go.microsoft.com/fwlink/?LinkId=96104](https://go.microsoft.com/fwlink/?LinkId=96104)<br /><br /> [https://go.microsoft.com/fwlink/?LinkId=96079](https://go.microsoft.com/fwlink/?LinkId=96079)|  
|<span data-ttu-id="9d1dd-110">WS-AtomicTransaction</span><span class="sxs-lookup"><span data-stu-id="9d1dd-110">WS-AtomicTransaction</span></span>|<span data-ttu-id="9d1dd-111">1.0</span><span class="sxs-lookup"><span data-stu-id="9d1dd-111">1.0</span></span><br /><br /> <span data-ttu-id="9d1dd-112">1.1</span><span class="sxs-lookup"><span data-stu-id="9d1dd-112">1.1</span></span>|[https://go.microsoft.com/fwlink/?LinkId=96080](https://go.microsoft.com/fwlink/?LinkId=96080)<br /><br /> https://go.microsoft.com/fwlink/?LinkId=96081|  
  
 <span data-ttu-id="9d1dd-113">Bu protokol belirtimleri üzerinde birlikte çalışabilirlik iki düzeyde gereklidir: uygulamalar arasında arasında işlem yöneticileri (aşağıdaki şekilde bakın).</span><span class="sxs-lookup"><span data-stu-id="9d1dd-113">Interoperability on these protocol specifications is required at two levels: between applications and between transaction managers (see the following figure).</span></span> <span data-ttu-id="9d1dd-114">Her iki birlikte çalışabilirlik düzeyleri için exchange ileti biçimleri ve ileti ayrıntılarını özellikleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9d1dd-114">Specifications describe in great detail the message formats and message exchange for both interoperability levels.</span></span> <span data-ttu-id="9d1dd-115">Normal uygulama exchange gibi belirli güvenlik, güvenilirlik ve kodlamaları uygulama uygulaması exchange için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="9d1dd-115">Certain security, reliability, and encodings for application-to-application exchange apply as they do for regular application exchange.</span></span> <span data-ttu-id="9d1dd-116">Ancak, kullanıcı tarafından genellikle yapılandırılmamış olduğundan işlem yöneticileri başarılı birlikte çalışabilirliği belirli bağlama üzerinde sözleşmesi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="9d1dd-116">However, successful interoperability between transaction managers requires agreement on the particular binding, because it is usually not configured by the user.</span></span>  
  
 <span data-ttu-id="9d1dd-117">Bu konu, WS-Atomic işlem (WS-AT) belirtimi bileşimi ile güvenlik açıklar ve işlem yöneticileri arasındaki iletişim için kullanılan güvenli bir bağlama tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9d1dd-117">This topic describes a composition of the WS-Atomic Transaction (WS-AT) specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="9d1dd-118">Bu belgede açıklanan yaklaşımı başarıyla WS-AT ve WS-koordinasyon diğer uygulamaları ile test edilmiştir IBM, IONA, Sun Microsystems ve diğerleri gibi.</span><span class="sxs-lookup"><span data-stu-id="9d1dd-118">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination including IBM, IONA, Sun Microsystems, and others.</span></span>  
  
 <span data-ttu-id="9d1dd-119">Aşağıdaki şekil, hareket yöneticisi 1 ve hareket yöneticisi 2, iki işlem yöneticileri ve uygulama 1 ve 2 uygulama olmak üzere iki uygulama arasında birlikte çalışabilirliği gösterir.</span><span class="sxs-lookup"><span data-stu-id="9d1dd-119">The following figure depicts the interoperability between two transaction managers, Transaction Manager 1 and Transaction Manager 2, and two applications, Application 1 and Application 2.</span></span>  
  
 <span data-ttu-id="9d1dd-120">![İşlem protokolleri](../../../../docs/framework/wcf/feature-details/media/transactionmanagers.gif "TransactionManagers")</span><span class="sxs-lookup"><span data-stu-id="9d1dd-120">![Transaction Protocols](../../../../docs/framework/wcf/feature-details/media/transactionmanagers.gif "TransactionManagers")</span></span>  
  
 <span data-ttu-id="9d1dd-121">Bir başlatıcı (ı) ve bir katılımcı (P) tipik bir WS-koordinasyon/WS-Atomic işlem senaryoyu ele alalım.</span><span class="sxs-lookup"><span data-stu-id="9d1dd-121">Consider a typical WS-Coordination/WS-Atomic Transaction scenario with one Initiator (I) and one Participant (P).</span></span> <span data-ttu-id="9d1dd-122">Hem Başlatıcı hem de katılımcı sahip işlem yöneticileri (ITM ve PTM, sırasıyla).</span><span class="sxs-lookup"><span data-stu-id="9d1dd-122">Both Initiator and Participant have Transaction Managers, (ITM and PTM, respectively).</span></span> <span data-ttu-id="9d1dd-123">İki aşamalı tamamlama bu konudaki 2PC olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="9d1dd-123">Two-phase commit is referred to as 2PC in this topic.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9d1dd-124">1. CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="9d1dd-124">1. CreateCoordinationContext</span></span>|<span data-ttu-id="9d1dd-125">12. Uygulama ileti yanıtı</span><span class="sxs-lookup"><span data-stu-id="9d1dd-125">12. Application Message Response</span></span>|  
|<span data-ttu-id="9d1dd-126">2. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="9d1dd-126">2. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="9d1dd-127">13. İşleme (tamamlama)</span><span class="sxs-lookup"><span data-stu-id="9d1dd-127">13. Commit (Completion)</span></span>|  
|<span data-ttu-id="9d1dd-128">3. Kayıt (tamamlama)</span><span class="sxs-lookup"><span data-stu-id="9d1dd-128">3. Register (Completion)</span></span>|<span data-ttu-id="9d1dd-129">14. (2PC) hazırlama</span><span class="sxs-lookup"><span data-stu-id="9d1dd-129">14. Prepare (2PC)</span></span>|  
|<span data-ttu-id="9d1dd-130">4. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="9d1dd-130">4. RegisterResponse</span></span>|<span data-ttu-id="9d1dd-131">15. (2PC) hazırlama</span><span class="sxs-lookup"><span data-stu-id="9d1dd-131">15. Prepare (2PC)</span></span>|  
|<span data-ttu-id="9d1dd-132">5. Uygulama iletisi</span><span class="sxs-lookup"><span data-stu-id="9d1dd-132">5. Application Message</span></span>|<span data-ttu-id="9d1dd-133">16. Hazırlanan (2PC)</span><span class="sxs-lookup"><span data-stu-id="9d1dd-133">16. Prepared (2PC)</span></span>|  
|<span data-ttu-id="9d1dd-134">6. Bağlamla CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="9d1dd-134">6. CreateCoordinationContext with Context</span></span>|<span data-ttu-id="9d1dd-135">17. Hazırlanan (2PC)</span><span class="sxs-lookup"><span data-stu-id="9d1dd-135">17. Prepared (2PC)</span></span>|  
|<span data-ttu-id="9d1dd-136">7. Kayıt (Durable)</span><span class="sxs-lookup"><span data-stu-id="9d1dd-136">7. Register (Durable)</span></span>|<span data-ttu-id="9d1dd-137">18. Taahhüt edilen (tamamlama)</span><span class="sxs-lookup"><span data-stu-id="9d1dd-137">18. Committed (Completion)</span></span>|  
|<span data-ttu-id="9d1dd-138">8. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="9d1dd-138">8. RegisterResponse</span></span>|<span data-ttu-id="9d1dd-139">19. Kayıt (2PC)</span><span class="sxs-lookup"><span data-stu-id="9d1dd-139">19. Commit (2PC)</span></span>|  
|<span data-ttu-id="9d1dd-140">9. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="9d1dd-140">9. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="9d1dd-141">20. Kayıt (2PC)</span><span class="sxs-lookup"><span data-stu-id="9d1dd-141">20. Commit (2PC)</span></span>|  
|<span data-ttu-id="9d1dd-142">10. Kayıt (Durable)</span><span class="sxs-lookup"><span data-stu-id="9d1dd-142">10. Register (Durable)</span></span>|<span data-ttu-id="9d1dd-143">21. Taahhüt edilen (2PC)</span><span class="sxs-lookup"><span data-stu-id="9d1dd-143">21. Committed (2PC)</span></span>|  
|<span data-ttu-id="9d1dd-144">11. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="9d1dd-144">11. RegisterResponse</span></span>|<span data-ttu-id="9d1dd-145">22. Taahhüt edilen (2PC)</span><span class="sxs-lookup"><span data-stu-id="9d1dd-145">22. Committed (2PC)</span></span>|  
  
 <span data-ttu-id="9d1dd-146">Bu belge, güvenlik ile WS-AtomicTransaction belirtiminin bir bileşim açıklar ve işlem yöneticileri arasındaki iletişim için kullanılan güvenli bir bağlama tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9d1dd-146">This document describes a composition of the WS-AtomicTransaction specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="9d1dd-147">Bu belgede açıklanan yaklaşımı başarıyla WS-AT ve WS-koordinasyon diğer uygulamaları ile test edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9d1dd-147">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination.</span></span>  
  
 <span data-ttu-id="9d1dd-148">Şekil ve tabloda dört güvenlik görüş iletilerden sınıflarını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="9d1dd-148">The figure and table illustrate four classes of messages from the viewpoint of security:</span></span>  
  
-   <span data-ttu-id="9d1dd-149">Etkinleştirme iletileri (CreateCoordinationContext ve CreateCoordinationContextResponse).</span><span class="sxs-lookup"><span data-stu-id="9d1dd-149">Activation messages (CreateCoordinationContext and CreateCoordinationContextResponse).</span></span>  
  
-   <span data-ttu-id="9d1dd-150">Kayıt iletileri (kayıt ve RegisterResponse)</span><span class="sxs-lookup"><span data-stu-id="9d1dd-150">Registration messages (Register and RegisterResponse)</span></span>  
  
-   <span data-ttu-id="9d1dd-151">Protokol iletileri (hazırlama, geri alma, işleme, iptal edildi ve benzeri).</span><span class="sxs-lookup"><span data-stu-id="9d1dd-151">Protocol messages (Prepare, Rollback, Commit, Aborted, and so on).</span></span>  
  
-   <span data-ttu-id="9d1dd-152">Uygulama iletileri.</span><span class="sxs-lookup"><span data-stu-id="9d1dd-152">Application messages.</span></span>  
  
 <span data-ttu-id="9d1dd-153">İlk üç ileti sınıflarını hareket yöneticisi iletileri kabul edilir ve bunların bağlama yapılandırması "Uygulama ileti değişimi" Bu konunun ilerleyen bölümlerinde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="9d1dd-153">The first three message classes are considered Transaction Manager messages and their binding configuration is described in the "Application Message Exchange" later in this topic.</span></span> <span data-ttu-id="9d1dd-154">İletinin dördüncü sınıfını uygulamaya ileti ve "İleti örnekler" bölümünde bu konunun ilerleyen bölümlerinde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="9d1dd-154">The fourth class of message is application to application messages and is described in the "Message Examples" section later in this topic.</span></span> <span data-ttu-id="9d1dd-155">Bu bölümde, bu sınıfların her biri için WCF tarafından kullanılan protokolü bağlamalarını açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9d1dd-155">This section describes the protocol bindings used for each of these classes by WCF.</span></span>  
  
 <span data-ttu-id="9d1dd-156">Aşağıdaki XML ad alanları ve ilişkili ön ekleri, bu belge boyunca kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9d1dd-156">The following XML Namespaces and associated prefixes are used throughout this document.</span></span>  
  
|<span data-ttu-id="9d1dd-157">Ön eki</span><span class="sxs-lookup"><span data-stu-id="9d1dd-157">Prefix</span></span>|<span data-ttu-id="9d1dd-158">Sürüm</span><span class="sxs-lookup"><span data-stu-id="9d1dd-158">Version</span></span>|<span data-ttu-id="9d1dd-159">Namespace URI'si</span><span class="sxs-lookup"><span data-stu-id="9d1dd-159">Namespace URI</span></span>|  
|------------|-------------|-------------------|  
|<span data-ttu-id="9d1dd-160">s11</span><span class="sxs-lookup"><span data-stu-id="9d1dd-160">s11</span></span>||[https://go.microsoft.com/fwlink/?LinkId=96014](https://go.microsoft.com/fwlink/?LinkId=96014)|  
|<span data-ttu-id="9d1dd-161">wsa</span><span class="sxs-lookup"><span data-stu-id="9d1dd-161">wsa</span></span>|<span data-ttu-id="9d1dd-162">Öncesi 1.0</span><span class="sxs-lookup"><span data-stu-id="9d1dd-162">Pre-1.0</span></span><br /><br /> <span data-ttu-id="9d1dd-163">1.0</span><span class="sxs-lookup"><span data-stu-id="9d1dd-163">1.0</span></span>|http://www.w3.org/2004/08/addressing<br /><br /> [https://go.microsoft.com/fwlink/?LinkId=96022](https://go.microsoft.com/fwlink/?LinkId=96022)|  
|<span data-ttu-id="9d1dd-164">wscoor</span><span class="sxs-lookup"><span data-stu-id="9d1dd-164">wscoor</span></span>|<span data-ttu-id="9d1dd-165">1.0</span><span class="sxs-lookup"><span data-stu-id="9d1dd-165">1.0</span></span><br /><br /> <span data-ttu-id="9d1dd-166">1.1</span><span class="sxs-lookup"><span data-stu-id="9d1dd-166">1.1</span></span>|[https://go.microsoft.com/fwlink/?LinkId=96078](https://go.microsoft.com/fwlink/?LinkId=96078)<br /><br /> [https://go.microsoft.com/fwlink/?LinkId=96079](https://go.microsoft.com/fwlink/?LinkId=96079)|  
|<span data-ttu-id="9d1dd-167">wsat</span><span class="sxs-lookup"><span data-stu-id="9d1dd-167">wsat</span></span>|<span data-ttu-id="9d1dd-168">1.0</span><span class="sxs-lookup"><span data-stu-id="9d1dd-168">1.0</span></span><br /><br /> <span data-ttu-id="9d1dd-169">1.1</span><span class="sxs-lookup"><span data-stu-id="9d1dd-169">1.1</span></span>|[https://go.microsoft.com/fwlink/?LinkId=96080](https://go.microsoft.com/fwlink/?LinkId=96080)<br /><br /> [https://go.microsoft.com/fwlink/?LinkId=96081](https://go.microsoft.com/fwlink/?LinkId=96081)|  
|<span data-ttu-id="9d1dd-170">t</span><span class="sxs-lookup"><span data-stu-id="9d1dd-170">t</span></span>|<span data-ttu-id="9d1dd-171">1.3 öncesi</span><span class="sxs-lookup"><span data-stu-id="9d1dd-171">Pre-1.3</span></span><br /><br /> <span data-ttu-id="9d1dd-172">1.3</span><span class="sxs-lookup"><span data-stu-id="9d1dd-172">1.3</span></span>|[https://go.microsoft.com/fwlink/?LinkId=96082](https://go.microsoft.com/fwlink/?LinkId=96082)<br /><br /> [https://go.microsoft.com/fwlink/?LinkId=96100](https://go.microsoft.com/fwlink/?LinkId=96100)|  
|<span data-ttu-id="9d1dd-173">o</span><span class="sxs-lookup"><span data-stu-id="9d1dd-173">o</span></span>||[https://go.microsoft.com/fwlink/?LinkId=96101](https://go.microsoft.com/fwlink/?LinkId=96101)|  
|<span data-ttu-id="9d1dd-174">xsd</span><span class="sxs-lookup"><span data-stu-id="9d1dd-174">xsd</span></span>||[https://go.microsoft.com/fwlink/?LinkId=96102](https://go.microsoft.com/fwlink/?LinkId=96102)|  
  
## <a name="transaction-manager-bindings"></a><span data-ttu-id="9d1dd-175">İşlem Yöneticisi bağlamaları</span><span class="sxs-lookup"><span data-stu-id="9d1dd-175">Transaction Manager Bindings</span></span>  
 <span data-ttu-id="9d1dd-176">R1001: İşlem yöneticileri WS-AT 1.0 işlemde katılan, WS-Atomic işlem ve WS-koordinasyon ileti alışverişlerinde SOAP 1.1 ve WS-Addressing 2004/08 kullanmalısınız.</span><span class="sxs-lookup"><span data-stu-id="9d1dd-176">R1001: Transaction Managers participating in a WS-AT 1.0 transaction must use SOAP 1.1 and WS-Addressing 2004/08 for WS-Atomic Transaction and WS-Coordination message exchanges.</span></span>  
  
 <span data-ttu-id="9d1dd-177">R1002: İşlem yöneticileri WS-AT 1.1 işlemde katılan, WS-Atomic işlem ve WS-koordinasyon ileti alışverişlerinde SOAP 1.1 ve WS-Addressing 2005/08 kullanmalısınız.</span><span class="sxs-lookup"><span data-stu-id="9d1dd-177">R1002: Transaction Managers participating in a WS-AT 1.1 transaction must use SOAP 1.1 and WS-Addressing 2005/08 for WS-Atomic Transaction and WS-Coordination message exchanges.</span></span>  
  
 <span data-ttu-id="9d1dd-178">Uygulama iletileri, bu bağlamaları için kısıtlı değildir ve daha sonra açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="9d1dd-178">Application messages are not constrained to these bindings and are described later.</span></span>  
  
### <a name="transaction-manager-https-binding"></a><span data-ttu-id="9d1dd-179">İşlem Yöneticisi HTTPS bağlama</span><span class="sxs-lookup"><span data-stu-id="9d1dd-179">Transaction Manager HTTPS Binding</span></span>  
 <span data-ttu-id="9d1dd-180">İşlem Yöneticisi HTTPS bağlaması güvenliği sağlamak ve işlem ağacında her gönderenin alıcı çifti arasında güven oluşturma için yalnızca Aktarım güvenliği kullanır.</span><span class="sxs-lookup"><span data-stu-id="9d1dd-180">The transaction manager HTTPS binding relies solely on transport security to achieve security and establish trust between each sender-receiver pair in the transaction tree.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="9d1dd-181">HTTPS aktarımı yapılandırması</span><span class="sxs-lookup"><span data-stu-id="9d1dd-181">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="9d1dd-182">X.509 sertifikaları, hareket yöneticisi kimliğini oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9d1dd-182">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="9d1dd-183">İstemci/sunucu kimlik doğrulaması ve yetkilendirme istemci/sunucu uygulama ayrıntısı bırakılır:</span><span class="sxs-lookup"><span data-stu-id="9d1dd-183">Client/server authentication is required, and client/server authorization is left as an implementation detail:</span></span>  
  
-   <span data-ttu-id="9d1dd-184">R1111: Kablo üzerinden sunulan X.509 sertifikaları, kaynak makinenin tam etki alanı adını (FQDN) eşleşen bir konu adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9d1dd-184">R1111: X.509 certificates presented over the wire must have a subject name that matches the fully qualified domain name (FQDN) of the originating machine.</span></span>  
  
-   <span data-ttu-id="9d1dd-185">B1112: DNS başarılı olması için her gönderenin alıcı çifti arasında X.509 konu adı denetimleri için sistemdeki işlevsel olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9d1dd-185">B1112: DNS must be functional between each sender-receiver pair in the system for X.509 subject name checks to succeed.</span></span>  
  
#### <a name="activation-and-registration-binding-configuration"></a><span data-ttu-id="9d1dd-186">Etkinleştirme ve yapılandırma bağlama kaydı</span><span class="sxs-lookup"><span data-stu-id="9d1dd-186">Activation and Registration Binding Configuration</span></span>  
 <span data-ttu-id="9d1dd-187">WCF HTTPS üzerinden istek/yanıt bağıntısı ile çift yönlü bağlama gerektirir.</span><span class="sxs-lookup"><span data-stu-id="9d1dd-187">WCF requires request/reply duplex binding with correlation over HTTPS.</span></span> <span data-ttu-id="9d1dd-188">(WS-Atomic işlem, Bölüm 8 bağıntı ve istek/yanıt iletisi exchange desenlerinin açıklamaları hakkında daha fazla bilgi için bkz.)</span><span class="sxs-lookup"><span data-stu-id="9d1dd-188">(For more information about correlation and descriptions of the request/reply message exchange patterns, see WS-Atomic Transaction, Section 8.)</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="9d1dd-189">2PC Protokolü bağlama yapılandırması</span><span class="sxs-lookup"><span data-stu-id="9d1dd-189">2PC Protocol Binding Configuration</span></span>  
 <span data-ttu-id="9d1dd-190">WCF HTTPS üzerinden tek yönlü (veri birimi) iletileri destekler.</span><span class="sxs-lookup"><span data-stu-id="9d1dd-190">WCF supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="9d1dd-191">İletileri arasında bağıntı uygulama ayrıntısı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="9d1dd-191">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="9d1dd-192">B1131: Uygulamaları desteklemelidir `wsa:ReferenceParameters` WS-WCF'ın 2PC iletilerinin bağıntı elde etmek için Addressing içinde açıklandığı gibi.</span><span class="sxs-lookup"><span data-stu-id="9d1dd-192">B1131: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of WCF’s 2PC messages.</span></span>  
  
### <a name="transaction-manager-mixed-security-binding"></a><span data-ttu-id="9d1dd-193">İşlem Yöneticisi karma güvenliği bağlama</span><span class="sxs-lookup"><span data-stu-id="9d1dd-193">Transaction Manager Mixed Security Binding</span></span>  
 <span data-ttu-id="9d1dd-194">Bir alternatif kimlik kurulması amacıyla WS-koordinasyon verilen belirteç modeli ile birlikte bu kullanımları aktarım güvenliği bağlama (karışık mod) budur.</span><span class="sxs-lookup"><span data-stu-id="9d1dd-194">This is an alternate (mixed mode) binding that uses transport security combined with the WS-Coordination Issued Token model for identity establishment purposes.</span></span> <span data-ttu-id="9d1dd-195">Etkinleştirme ve kayıt iki bağlaması arasında farklılık gösteren yalnızca öğelerdir.</span><span class="sxs-lookup"><span data-stu-id="9d1dd-195">Activation and Registration are the only elements that differ between the two bindings.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="9d1dd-196">HTTPS aktarımı yapılandırması</span><span class="sxs-lookup"><span data-stu-id="9d1dd-196">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="9d1dd-197">X.509 sertifikaları, hareket yöneticisi kimliğini oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9d1dd-197">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="9d1dd-198">İstemci/sunucu kimlik doğrulaması ve yetkilendirme istemci/sunucu uygulama ayrıntısı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="9d1dd-198">Client/Server authentication is required, and client/server authorization is left as an implementation detail.</span></span>  
  
#### <a name="activation-message-binding-configuration"></a><span data-ttu-id="9d1dd-199">Etkinleştirme ileti bağlama yapılandırması</span><span class="sxs-lookup"><span data-stu-id="9d1dd-199">Activation Message Binding Configuration</span></span>  
 <span data-ttu-id="9d1dd-200">Genellikle kendi yerel hareket yöneticisi ile bir uygulama arasında gerçekleştiği için etkinleştirme iletileri birlikte çalışabilirlik genellikle katılmaz.</span><span class="sxs-lookup"><span data-stu-id="9d1dd-200">Activation Messages usually do not participate in interoperability because they typically occur between an application and its local Transaction Manager.</span></span>  
  
 <span data-ttu-id="9d1dd-201">B1221: WCF çift yönlü bir HTTPS bağlama kullanır (açıklanan [Mesajlaşma protokolleri](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) etkinleştirme iletileri.</span><span class="sxs-lookup"><span data-stu-id="9d1dd-201">B1221: WCF uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) for Activation messages.</span></span> <span data-ttu-id="9d1dd-202">WS-Addressing 2004/08 WS-AT 1.0 ve WS-Addressing 2005/08 için WS-AT 1.1 kullanarak istek ve yanıt iletilerinin ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="9d1dd-202">Request and Reply messages are correlated using WS-Addressing 2004/08 for WS-AT 1.0 and WS-Addressing 2005/08 for WS-AT 1.1.</span></span>  
  
 <span data-ttu-id="9d1dd-203">WS-Atomic işlem belirtimi, Bölüm 8, bağıntı ve ileti exchange desenleri hakkında daha fazla ayrıntıları açıklanır.</span><span class="sxs-lookup"><span data-stu-id="9d1dd-203">WS-Atomic Transaction specification, Section 8, describes further details about correlation and the message exchange patterns.</span></span>  
  
-   <span data-ttu-id="9d1dd-204">R1222: Alma bağlı bir `CreateCoordinationContext`, düzenleyici dağıtmalı bir `SecurityContextToken` ile ilişkili gizli `STx`.</span><span class="sxs-lookup"><span data-stu-id="9d1dd-204">R1222: Upon receiving a `CreateCoordinationContext`, the Coordinator must issue a `SecurityContextToken` with associated secret `STx`.</span></span> <span data-ttu-id="9d1dd-205">Bu belirteç içinde döndürülen bir `t:IssuedTokens` WS-Güven belirtimini takip başlığı.</span><span class="sxs-lookup"><span data-stu-id="9d1dd-205">This token is returned inside a `t:IssuedTokens` header following WS-Trust specification.</span></span>  
  
-   <span data-ttu-id="9d1dd-206">R1223: Etkinleştirme var olan bir düzenleme bağlamı içinde ortaya çıkarsa `t:IssuedTokens` üstbilgiyle `SecurityContextToken` var olan ilişkili bağlam gerekir akışını `CreateCoordinationContext` ileti.</span><span class="sxs-lookup"><span data-stu-id="9d1dd-206">R1223: If Activation occurs within an existing Coordination Context, the `t:IssuedTokens` header with the `SecurityContextToken` associated with existing Context must flow on the `CreateCoordinationContext` message.</span></span>  
  
 <span data-ttu-id="9d1dd-207">Yeni bir `t:IssuedTokens` üstbilgi giden eklemek için oluşturulacak `wscoor:CreateCoordinationContextResponse` ileti.</span><span class="sxs-lookup"><span data-stu-id="9d1dd-207">A new `t:IssuedTokens` header should be generated for attaching to the outgoing `wscoor:CreateCoordinationContextResponse` message.</span></span>  
  
#### <a name="registration-message-binding-configuration"></a><span data-ttu-id="9d1dd-208">Kayıt iletisi bağlama yapılandırması</span><span class="sxs-lookup"><span data-stu-id="9d1dd-208">Registration Message Binding Configuration</span></span>  
 <span data-ttu-id="9d1dd-209">B1231: WCF çift yönlü bir HTTPS bağlama kullanır (açıklanan [Mesajlaşma protokolleri](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)).</span><span class="sxs-lookup"><span data-stu-id="9d1dd-209">B1231: WCF uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)).</span></span> <span data-ttu-id="9d1dd-210">WS-Addressing 2004/08 WS-AT 1.0 ve WS-Addressing 2005/08 için WS-AT 1.1 kullanarak istek ve yanıt iletilerinin ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="9d1dd-210">Request and Reply messages are correlated using WS-Addressing 2004/08 for WS-AT 1.0 and WS-Addressing 2005/08 for WS-AT 1.1.</span></span>  
  
 <span data-ttu-id="9d1dd-211">WS-AtomicTransaction, Bölüm 8 açıklar daha fazla ayrıntı bağıntı ve açıklamaları ileti exchange desenleri hakkında.</span><span class="sxs-lookup"><span data-stu-id="9d1dd-211">WS-AtomicTransaction, Section 8, describes further details about correlation and descriptions of the message exchange patterns.</span></span>  
  
 <span data-ttu-id="9d1dd-212">R1232: Giden `wscoor:Register` iletileri kullanmalıdır `IssuedTokenOverTransport` kimlik doğrulama modu açıklanan [güvenlik protokollerini](../../../../docs/framework/wcf/feature-details/security-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="9d1dd-212">R1232: Outgoing `wscoor:Register` messages must use the `IssuedTokenOverTransport` authentication mode described in [Security Protocols](../../../../docs/framework/wcf/feature-details/security-protocols.md).</span></span>  
  
 <span data-ttu-id="9d1dd-213">`wsse:Timestamp` Öğesi kullanılarak imzalanmalıdır `SecurityContextToken``STx` verildi.</span><span class="sxs-lookup"><span data-stu-id="9d1dd-213">The `wsse:Timestamp` element must be signed using the `SecurityContextToken``STx` issued.</span></span> <span data-ttu-id="9d1dd-214">Bu imza, belirli bir işlemle ilişkili belirtecin kanıtını olduğu ve işlemde kaydetme katılımcı kimliğini doğrulamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9d1dd-214">This signature is a proof of possession of the token associated with particular transaction and is used to authenticate a participant enlisting in the transaction.</span></span> <span data-ttu-id="9d1dd-215">HTTPS üzerinden RegistrationResponse ileti gönderilir.</span><span class="sxs-lookup"><span data-stu-id="9d1dd-215">The RegistrationResponse message is sent back over HTTPS.</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="9d1dd-216">2PC Protokolü bağlama yapılandırması</span><span class="sxs-lookup"><span data-stu-id="9d1dd-216">2PC Protocol Binding Configuration</span></span>  
 <span data-ttu-id="9d1dd-217">WCF HTTPS üzerinden tek yönlü (veri birimi) iletileri destekler.</span><span class="sxs-lookup"><span data-stu-id="9d1dd-217">WCF supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="9d1dd-218">İletileri arasında bağıntı uygulama ayrıntısı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="9d1dd-218">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="9d1dd-219">B1241: Uygulamaları desteklemelidir `wsa:ReferenceParameters` WS-WCF'ın 2PC iletilerinin bağıntı elde etmek için Addressing içinde açıklandığı gibi.</span><span class="sxs-lookup"><span data-stu-id="9d1dd-219">B1241: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of WCF’s 2PC messages.</span></span>  
  
## <a name="application-message-exchange"></a><span data-ttu-id="9d1dd-220">Uygulama ileti değişimi</span><span class="sxs-lookup"><span data-stu-id="9d1dd-220">Application Message Exchange</span></span>  
 <span data-ttu-id="9d1dd-221">Uygulamaları bağlama aşağıdaki güvenlik gereksinimlerini karşıladığı sürece herhangi belirli bağlama-uygulamaya iletileri için kullanılacak ücretsizdir:</span><span class="sxs-lookup"><span data-stu-id="9d1dd-221">Applications are free to use any particular binding for application-to-application messages, as long as the binding meets the following security requirements:</span></span>  
  
-   <span data-ttu-id="9d1dd-222">R2001: Uygulama uygulama iletileri gerekir akış `t:IssuedTokens` başlığı ile birlikte `CoordinationContext` iletisinin üst bilgisindeki.</span><span class="sxs-lookup"><span data-stu-id="9d1dd-222">R2001: Application-to-application messages must flow the `t:IssuedTokens` header along with the `CoordinationContext` in the header of the message.</span></span>  
  
-   <span data-ttu-id="9d1dd-223">R2002: Bütünlüğü ve gizliliği `t:IssuedToken` sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9d1dd-223">R2002: Integrity and confidentiality of `t:IssuedToken` must be provided.</span></span>  
  
 <span data-ttu-id="9d1dd-224">`CoordinationContext` Üst bilgiyi içeren `wscoor:Identifier`.</span><span class="sxs-lookup"><span data-stu-id="9d1dd-224">The `CoordinationContext` header contains `wscoor:Identifier`.</span></span> <span data-ttu-id="9d1dd-225">While tanımını `xsd:AnyURI` mutlak ve göreli URI'ler kullanımına izin verir WCF yalnızca destekler `wscoor:Identifiers`, mutlak bir URI'leri olduğu.</span><span class="sxs-lookup"><span data-stu-id="9d1dd-225">While the definition of `xsd:AnyURI` allows the use of both absolute and relative URIs, WCF supports only `wscoor:Identifiers`, which are absolute URIs.</span></span>  
  
 <span data-ttu-id="9d1dd-226">B2003: Varsa `wscoor:Identifier` , `wscoor:CoordinationContext` göreli bir URI işlem WCF hizmetlerinden hatalar döndürülür.</span><span class="sxs-lookup"><span data-stu-id="9d1dd-226">B2003: If the `wscoor:Identifier` of the `wscoor:CoordinationContext` is a relative URI, faults will be returned from transactional WCF services.</span></span>  
  
## <a name="message-examples"></a><span data-ttu-id="9d1dd-227">İleti örnekleri</span><span class="sxs-lookup"><span data-stu-id="9d1dd-227">Message Examples</span></span>  
  
### <a name="createcoordinationcontext-requestresponse-messages"></a><span data-ttu-id="9d1dd-228">CreateCoordinationContext istek/yanıt iletilerini</span><span class="sxs-lookup"><span data-stu-id="9d1dd-228">CreateCoordinationContext Request/Response Messages</span></span>  
 <span data-ttu-id="9d1dd-229">Aşağıdaki ileti, istek/yanıt deseni izler.</span><span class="sxs-lookup"><span data-stu-id="9d1dd-229">The following messages follow a request/response pattern.</span></span>  
  
#### <a name="createcoordinationcontext-with-wscoor-10"></a><span data-ttu-id="9d1dd-230">CreateCoordinationContext WSCoor 1.0 ile</span><span class="sxs-lookup"><span data-stu-id="9d1dd-230">CreateCoordinationContext with WSCoor 1.0</span></span>  
  
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
  
#### <a name="createcoordinationcontext-with-wscoor-11"></a><span data-ttu-id="9d1dd-231">CreateCoordinationContext WSCoor 1.1 ile</span><span class="sxs-lookup"><span data-stu-id="9d1dd-231">CreateCoordinationContext with WSCoor 1.1</span></span>  
  
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
  
#### <a name="createcoordinationcontextresponse-with-trust-pre-13-and-wscoor-10"></a><span data-ttu-id="9d1dd-232">Güven Pre-1.3 ve WSCoor 1.0 ile CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="9d1dd-232">CreateCoordinationContextResponse with Trust Pre-1.3 and WSCoor 1.0</span></span>  
  
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
  
#### <a name="createcoordinationcontextresponse-with-trust-13-and-wscoor-11"></a><span data-ttu-id="9d1dd-233">Güven 1.3 ve WSCoor 1.1 ile CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="9d1dd-233">CreateCoordinationContextResponse with Trust 1.3 and WSCoor 1.1</span></span>  
  
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
  
### <a name="registration-messages"></a><span data-ttu-id="9d1dd-234">Kayıt iletileri</span><span class="sxs-lookup"><span data-stu-id="9d1dd-234">Registration Messages</span></span>  
 <span data-ttu-id="9d1dd-235">Aşağıdaki iletileri, kayıt iletileri edilir.</span><span class="sxs-lookup"><span data-stu-id="9d1dd-235">The following messages are registration messages.</span></span>  
  
#### <a name="register-with-wscoor-10"></a><span data-ttu-id="9d1dd-236">WSCoor 1.0 ile kaydetme</span><span class="sxs-lookup"><span data-stu-id="9d1dd-236">Register with WSCoor 1.0</span></span>  
  
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
  
#### <a name="register-with-wscoor-11"></a><span data-ttu-id="9d1dd-237">1.1 WSCoor ile kaydetme</span><span class="sxs-lookup"><span data-stu-id="9d1dd-237">Register with WSCoor 1.1</span></span>  
  
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
  
#### <a name="register-response-with-wscoor-10"></a><span data-ttu-id="9d1dd-238">Yanıt WSCoor 1.0 ile kaydetme</span><span class="sxs-lookup"><span data-stu-id="9d1dd-238">Register Response with WSCoor 1.0</span></span>  
  
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
  
#### <a name="register-response-with-wscoor-11"></a><span data-ttu-id="9d1dd-239">Yanıt WSCoor 1.1 ile kaydetme</span><span class="sxs-lookup"><span data-stu-id="9d1dd-239">Register Response with WSCoor 1.1</span></span>  
  
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
  
### <a name="two-phase-commit-protocol-messages"></a><span data-ttu-id="9d1dd-240">İki aşaması yürütme protokol iletileri</span><span class="sxs-lookup"><span data-stu-id="9d1dd-240">Two Phase Commit Protocol Messages</span></span>  
 <span data-ttu-id="9d1dd-241">Aşağıdaki ileti iki aşamalı kayıt (2PC) protokolüne ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="9d1dd-241">The following message relates to the two-phase commit (2PC) protocol.</span></span>  
  
#### <a name="commit-with-wsat-10"></a><span data-ttu-id="9d1dd-242">WSAT 1.0 ile işleme</span><span class="sxs-lookup"><span data-stu-id="9d1dd-242">Commit with WSAT 1.0</span></span>  
  
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
  
#### <a name="commit-with-wsat-11"></a><span data-ttu-id="9d1dd-243">1.1 WSAT ile işleme</span><span class="sxs-lookup"><span data-stu-id="9d1dd-243">Commit with WSAT 1.1</span></span>  
  
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
  
### <a name="application-messages"></a><span data-ttu-id="9d1dd-244">Uygulama iletileri</span><span class="sxs-lookup"><span data-stu-id="9d1dd-244">Application Messages</span></span>  
 <span data-ttu-id="9d1dd-245">Aşağıdaki iletileri uygulama iletileri edilir.</span><span class="sxs-lookup"><span data-stu-id="9d1dd-245">The following messages are application messages.</span></span>  
  
#### <a name="application-message-request"></a><span data-ttu-id="9d1dd-246">Uygulama isteği iletisi</span><span class="sxs-lookup"><span data-stu-id="9d1dd-246">Application message-Request</span></span>  
  
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

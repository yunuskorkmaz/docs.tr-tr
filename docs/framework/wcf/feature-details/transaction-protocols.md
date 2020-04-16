---
title: İşlem Protokolleri
ms.date: 03/30/2017
ms.assetid: 2820b0ec-2f32-430c-b299-1f0e95e1f2dc
ms.openlocfilehash: 8f16f7a6c13ca557ce4160d927ef6f075a79b4c8
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464036"
---
# <a name="transaction-protocols"></a><span data-ttu-id="b51a5-102">İşlem Protokolleri</span><span class="sxs-lookup"><span data-stu-id="b51a5-102">Transaction Protocols</span></span>
<span data-ttu-id="b51a5-103">Windows Communication Foundation (WCF), WS-Atomik İşlem ve WS-Koordinasyon protokollerini uygular.</span><span class="sxs-lookup"><span data-stu-id="b51a5-103">Windows Communication Foundation (WCF) implements WS-Atomic Transaction and WS-Coordination protocols.</span></span>  
  
|<span data-ttu-id="b51a5-104">Belirtim/Belge</span><span class="sxs-lookup"><span data-stu-id="b51a5-104">Specification/Document</span></span>|<span data-ttu-id="b51a5-105">Sürüm</span><span class="sxs-lookup"><span data-stu-id="b51a5-105">Version</span></span>|<span data-ttu-id="b51a5-106">Bağlantı</span><span class="sxs-lookup"><span data-stu-id="b51a5-106">Link</span></span>|  
|-----------------------------|-------------|----------|  
|<span data-ttu-id="b51a5-107">WS-Koordinasyon</span><span class="sxs-lookup"><span data-stu-id="b51a5-107">WS-Coordination</span></span>|<span data-ttu-id="b51a5-108">1.0</span><span class="sxs-lookup"><span data-stu-id="b51a5-108">1.0</span></span><br /><br /> <span data-ttu-id="b51a5-109">1.1</span><span class="sxs-lookup"><span data-stu-id="b51a5-109">1.1</span></span>|<http://schemas.xmlsoap.org/ws/2004/10/wscoor/><br /><br /> <https://docs.oasis-open.org/ws-tx/wscoor/2006/06>|  
|<span data-ttu-id="b51a5-110">WS-AtomicTransaction</span><span class="sxs-lookup"><span data-stu-id="b51a5-110">WS-AtomicTransaction</span></span>|<span data-ttu-id="b51a5-111">1.0</span><span class="sxs-lookup"><span data-stu-id="b51a5-111">1.0</span></span><br /><br /> <span data-ttu-id="b51a5-112">1.1</span><span class="sxs-lookup"><span data-stu-id="b51a5-112">1.1</span></span>|<http://schemas.xmlsoap.org/ws/2004/10/wsat/><br /><br /> <https://docs.oasis-open.org/ws-tx/wsat/2006/06>|  
  
 <span data-ttu-id="b51a5-113">Bu protokol belirtimleri üzerinde birlikte çalışabilirlik iki düzeyde gereklidir: uygulamalar arasında ve işlem yöneticileri arasında (aşağıdaki şekilden bakın).</span><span class="sxs-lookup"><span data-stu-id="b51a5-113">Interoperability on these protocol specifications is required at two levels: between applications and between transaction managers (see the following figure).</span></span> <span data-ttu-id="b51a5-114">Belirtimler, her iki birlikte çalışabilirlik düzeyi için ileti biçimlerini ve ileti alışverişini ayrıntılı olarak açıklar.</span><span class="sxs-lookup"><span data-stu-id="b51a5-114">Specifications describe in great detail the message formats and message exchange for both interoperability levels.</span></span> <span data-ttu-id="b51a5-115">Uygulama-uygulama değişimi için belirli güvenlik, güvenilirlik ve kodlamalar, düzenli uygulama değişimi için olduğu gibi geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b51a5-115">Certain security, reliability, and encodings for application-to-application exchange apply as they do for regular application exchange.</span></span> <span data-ttu-id="b51a5-116">Ancak, işlem yöneticileri arasında başarılı birlikte çalışabilirlik, genellikle kullanıcı tarafından yapılandırılmadığından, belirli bağlama üzerinde anlaşma gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b51a5-116">However, successful interoperability between transaction managers requires agreement on the particular binding, because it is usually not configured by the user.</span></span>  
  
 <span data-ttu-id="b51a5-117">Bu konu, WS-Atomic Transaction (WS-AT) belirtiminin güvenlikle ilgili bir bileşimini açıklar ve işlem yöneticileri arasında iletişim için kullanılan güvenli bağlamayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="b51a5-117">This topic describes a composition of the WS-Atomic Transaction (WS-AT) specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="b51a5-118">Bu belgede açıklanan yaklaşım, IBM, IONA, Sun Microsystems ve diğerleri de dahil olmak üzere WS-AT ve WS-Coordination'un diğer uygulamalarıyla başarıyla test edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b51a5-118">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination including IBM, IONA, Sun Microsystems, and others.</span></span>  
  
 <span data-ttu-id="b51a5-119">Aşağıdaki şekil, iki işlem yöneticisi, İşlem Yöneticisi 1 ve İşlem Yöneticisi 2 ve iki uygulama, Uygulama 1 ve Uygulama 2 arasındaki birlikte çalışabilirliği gösterir:</span><span class="sxs-lookup"><span data-stu-id="b51a5-119">The following figure depicts the interoperability between two transaction managers, Transaction Manager 1 and Transaction Manager 2, and two applications, Application 1 and Application 2:</span></span>  
  
 ![Hareket yöneticileri arasındaki etkileşimi gösteren ekran görüntüsü.](./media/transaction-protocols/transaction-managers-flow.gif)  
  
 <span data-ttu-id="b51a5-121">Bir Başlatıcı (I) ve bir Katılımcı (P) ile tipik bir WS-Coordination/WS-Atomic Transaction senaryosudüşünün.</span><span class="sxs-lookup"><span data-stu-id="b51a5-121">Consider a typical WS-Coordination/WS-Atomic Transaction scenario with one Initiator (I) and one Participant (P).</span></span> <span data-ttu-id="b51a5-122">Hem Başlatıcı hem de Katılımcı'nın Işlem Yöneticileri (sırasıyla ITM ve PTM) vardır.</span><span class="sxs-lookup"><span data-stu-id="b51a5-122">Both Initiator and Participant have Transaction Managers, (ITM and PTM, respectively).</span></span> <span data-ttu-id="b51a5-123">İki aşamalı taahhüt bu konuda 2PC olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="b51a5-123">Two-phase commit is referred to as 2PC in this topic.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b51a5-124">1. CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="b51a5-124">1. CreateCoordinationContext</span></span>|<span data-ttu-id="b51a5-125">12. Uygulama Mesajı Yanıtı</span><span class="sxs-lookup"><span data-stu-id="b51a5-125">12. Application Message Response</span></span>|  
|<span data-ttu-id="b51a5-126">2. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="b51a5-126">2. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="b51a5-127">13. Taahhüt (Tamamlama)</span><span class="sxs-lookup"><span data-stu-id="b51a5-127">13. Commit (Completion)</span></span>|  
|<span data-ttu-id="b51a5-128">3. Kayıt (Tamamlama)</span><span class="sxs-lookup"><span data-stu-id="b51a5-128">3. Register (Completion)</span></span>|<span data-ttu-id="b51a5-129">14. Hazırlayın (2PC)</span><span class="sxs-lookup"><span data-stu-id="b51a5-129">14. Prepare (2PC)</span></span>|  
|<span data-ttu-id="b51a5-130">4. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="b51a5-130">4. RegisterResponse</span></span>|<span data-ttu-id="b51a5-131">15. Hazırlayın (2PC)</span><span class="sxs-lookup"><span data-stu-id="b51a5-131">15. Prepare (2PC)</span></span>|  
|<span data-ttu-id="b51a5-132">5. Uygulama Mesajı</span><span class="sxs-lookup"><span data-stu-id="b51a5-132">5. Application Message</span></span>|<span data-ttu-id="b51a5-133">16. Hazırlanan (2PC)</span><span class="sxs-lookup"><span data-stu-id="b51a5-133">16. Prepared (2PC)</span></span>|  
|<span data-ttu-id="b51a5-134">6. Bağlam ile Koordinasyon Bağlamı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b51a5-134">6. CreateCoordinationContext with Context</span></span>|<span data-ttu-id="b51a5-135">17. Hazırlanan (2PC)</span><span class="sxs-lookup"><span data-stu-id="b51a5-135">17. Prepared (2PC)</span></span>|  
|<span data-ttu-id="b51a5-136">7. Kayıt (Dayanıklı)</span><span class="sxs-lookup"><span data-stu-id="b51a5-136">7. Register (Durable)</span></span>|<span data-ttu-id="b51a5-137">18. Taahhüt (Tamamlama)</span><span class="sxs-lookup"><span data-stu-id="b51a5-137">18. Committed (Completion)</span></span>|  
|<span data-ttu-id="b51a5-138">8. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="b51a5-138">8. RegisterResponse</span></span>|<span data-ttu-id="b51a5-139">19. Taahhüt (2PC)</span><span class="sxs-lookup"><span data-stu-id="b51a5-139">19. Commit (2PC)</span></span>|  
|<span data-ttu-id="b51a5-140">9. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="b51a5-140">9. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="b51a5-141">20. Taahhüt (2PC)</span><span class="sxs-lookup"><span data-stu-id="b51a5-141">20. Commit (2PC)</span></span>|  
|<span data-ttu-id="b51a5-142">10. Kayıt (Dayanıklı)</span><span class="sxs-lookup"><span data-stu-id="b51a5-142">10. Register (Durable)</span></span>|<span data-ttu-id="b51a5-143">21. Taahhüt (2PC)</span><span class="sxs-lookup"><span data-stu-id="b51a5-143">21. Committed (2PC)</span></span>|  
|<span data-ttu-id="b51a5-144">11. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="b51a5-144">11. RegisterResponse</span></span>|<span data-ttu-id="b51a5-145">22. Taahhüt (2PC)</span><span class="sxs-lookup"><span data-stu-id="b51a5-145">22. Committed (2PC)</span></span>|  
  
 <span data-ttu-id="b51a5-146">Bu belge, WS-AtomicTransaction belirtiminin güvenlikle ilgili bir bileşimini açıklar ve işlem yöneticileri arasında iletişim için kullanılan güvenli bağlamayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="b51a5-146">This document describes a composition of the WS-AtomicTransaction specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="b51a5-147">Bu belgede açıklanan yaklaşım, WS-AT ve WS-Coordination'un diğer uygulamalarıyla başarıyla test edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b51a5-147">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination.</span></span>  
  
 <span data-ttu-id="b51a5-148">Şekil ve tablo, güvenlik açısından dört ileti sınıfını gösterir:</span><span class="sxs-lookup"><span data-stu-id="b51a5-148">The figure and table illustrate four classes of messages from the viewpoint of security:</span></span>  
  
- <span data-ttu-id="b51a5-149">Etkinleştirme iletileri (CreateCoordinationContext ve CreateCoordinationContextResponse).</span><span class="sxs-lookup"><span data-stu-id="b51a5-149">Activation messages (CreateCoordinationContext and CreateCoordinationContextResponse).</span></span>  
  
- <span data-ttu-id="b51a5-150">Kayıt mesajları (Kayıt ve Kayıt Yanıtı)</span><span class="sxs-lookup"><span data-stu-id="b51a5-150">Registration messages (Register and RegisterResponse)</span></span>  
  
- <span data-ttu-id="b51a5-151">Protokol iletileri (Hazırla, Geri Alma, Commit, İptal vb.)</span><span class="sxs-lookup"><span data-stu-id="b51a5-151">Protocol messages (Prepare, Rollback, Commit, Aborted, and so on).</span></span>  
  
- <span data-ttu-id="b51a5-152">Uygulama iletileri.</span><span class="sxs-lookup"><span data-stu-id="b51a5-152">Application messages.</span></span>  
  
 <span data-ttu-id="b51a5-153">İlk üç ileti sınıfı İşlem Yöneticisi iletileri olarak kabul edilir ve bağlama yapılandırmaları daha sonra bu konunun "Uygulama İletisi Değişimi"nde açıklanır.</span><span class="sxs-lookup"><span data-stu-id="b51a5-153">The first three message classes are considered Transaction Manager messages and their binding configuration is described in the "Application Message Exchange" later in this topic.</span></span> <span data-ttu-id="b51a5-154">Dördüncü sınıf ileti, uygulama iletilerine uygulamadır ve daha sonra bu konunun "İleti Örnekleri" bölümünde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="b51a5-154">The fourth class of message is application to application messages and is described in the "Message Examples" section later in this topic.</span></span> <span data-ttu-id="b51a5-155">Bu bölümde, WCF tarafından bu sınıfların her biri için kullanılan protokol bağlamaları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b51a5-155">This section describes the protocol bindings used for each of these classes by WCF.</span></span>  
  
 <span data-ttu-id="b51a5-156">Bu belge boyunca aşağıdaki XML Ad Alanları ve ilişkili önekleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b51a5-156">The following XML Namespaces and associated prefixes are used throughout this document.</span></span>  
  
|<span data-ttu-id="b51a5-157">Ön ek</span><span class="sxs-lookup"><span data-stu-id="b51a5-157">Prefix</span></span>|<span data-ttu-id="b51a5-158">Sürüm</span><span class="sxs-lookup"><span data-stu-id="b51a5-158">Version</span></span>|<span data-ttu-id="b51a5-159">Namespace URI</span><span class="sxs-lookup"><span data-stu-id="b51a5-159">Namespace URI</span></span>|  
|------------|-------------|-------------------|  
|<span data-ttu-id="b51a5-160">s11</span><span class="sxs-lookup"><span data-stu-id="b51a5-160">s11</span></span>||<https://schemas.xmlsoap.org/soap/envelope/>|  
|<span data-ttu-id="b51a5-161">Wsa</span><span class="sxs-lookup"><span data-stu-id="b51a5-161">wsa</span></span>|<span data-ttu-id="b51a5-162">1.0 Öncesi</span><span class="sxs-lookup"><span data-stu-id="b51a5-162">Pre-1.0</span></span><br /><br /> <span data-ttu-id="b51a5-163">1.0</span><span class="sxs-lookup"><span data-stu-id="b51a5-163">1.0</span></span>|`http://www.w3.org/2004/08/addressing`<br /><br /> <https://www.w3.org/2005/08/addressing/>|  
|<span data-ttu-id="b51a5-164">wscoor</span><span class="sxs-lookup"><span data-stu-id="b51a5-164">wscoor</span></span>|<span data-ttu-id="b51a5-165">1.0</span><span class="sxs-lookup"><span data-stu-id="b51a5-165">1.0</span></span><br /><br /> <span data-ttu-id="b51a5-166">1.1</span><span class="sxs-lookup"><span data-stu-id="b51a5-166">1.1</span></span>|<http://schemas.xmlsoap.org/ws/2004/10/wscoor/><br /><br /> <https://docs.oasis-open.org/ws-tx/wscoor/2006/06>|  
|<span data-ttu-id="b51a5-167">wsat</span><span class="sxs-lookup"><span data-stu-id="b51a5-167">wsat</span></span>|<span data-ttu-id="b51a5-168">1.0</span><span class="sxs-lookup"><span data-stu-id="b51a5-168">1.0</span></span><br /><br /> <span data-ttu-id="b51a5-169">1.1</span><span class="sxs-lookup"><span data-stu-id="b51a5-169">1.1</span></span>|<http://schemas.xmlsoap.org/ws/2004/10/wsat/><br /><br /> <https://docs.oasis-open.org/ws-tx/wsat/2006/06>|  
|<span data-ttu-id="b51a5-170">t</span><span class="sxs-lookup"><span data-stu-id="b51a5-170">t</span></span>|<span data-ttu-id="b51a5-171">1.3'ün öncesi</span><span class="sxs-lookup"><span data-stu-id="b51a5-171">Pre-1.3</span></span><br /><br /> <span data-ttu-id="b51a5-172">1.3</span><span class="sxs-lookup"><span data-stu-id="b51a5-172">1.3</span></span>|<http://schemas.xmlsoap.org/ws/2005/02/trust/><br /><br /> <https://docs.oasis-open.org/ws-sx/ws-trust/200512>|  
|<span data-ttu-id="b51a5-173">o</span><span class="sxs-lookup"><span data-stu-id="b51a5-173">o</span></span>||<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd>|  
|<span data-ttu-id="b51a5-174">Xsd</span><span class="sxs-lookup"><span data-stu-id="b51a5-174">xsd</span></span>||<https://www.w3.org/2001/XMLSchema>|  
  
## <a name="transaction-manager-bindings"></a><span data-ttu-id="b51a5-175">İşlem Yöneticisi Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="b51a5-175">Transaction Manager Bindings</span></span>  
 <span data-ttu-id="b51a5-176">R1001: WS-AT 1.0 işlemine katılan işlem yöneticileri, WS-Atomik İşlem ve WS-Koordinasyon ileti alışverişi için SOAP 1.1 ve WS-Addressing 2004/08'i kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b51a5-176">R1001: Transaction Managers participating in a WS-AT 1.0 transaction must use SOAP 1.1 and WS-Addressing 2004/08 for WS-Atomic Transaction and WS-Coordination message exchanges.</span></span>  
  
 <span data-ttu-id="b51a5-177">R1002: WS-AT 1.1 işlemine katılan işlem yöneticileri, WS-Atomik İşlem ve WS-Koordinasyon ileti alışverişi için SOAP 1.1 ve WS-Addressing 2005/08'i kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b51a5-177">R1002: Transaction Managers participating in a WS-AT 1.1 transaction must use SOAP 1.1 and WS-Addressing 2005/08 for WS-Atomic Transaction and WS-Coordination message exchanges.</span></span>  
  
 <span data-ttu-id="b51a5-178">Uygulama iletileri bu bağlamalarla sınırlandırılmamıştır ve daha sonra açıklanır.</span><span class="sxs-lookup"><span data-stu-id="b51a5-178">Application messages are not constrained to these bindings and are described later.</span></span>  
  
### <a name="transaction-manager-https-binding"></a><span data-ttu-id="b51a5-179">İşlem Yöneticisi HTTPS Ciltleme</span><span class="sxs-lookup"><span data-stu-id="b51a5-179">Transaction Manager HTTPS Binding</span></span>  
 <span data-ttu-id="b51a5-180">İşlem yöneticisi HTTPS bağlama, güvenliği sağlamak ve hareket ağacındaki her gönderen-alıcı çifti arasında güven oluşturmak için yalnızca aktarım güvenliğine dayanır.</span><span class="sxs-lookup"><span data-stu-id="b51a5-180">The transaction manager HTTPS binding relies solely on transport security to achieve security and establish trust between each sender-receiver pair in the transaction tree.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="b51a5-181">HTTPS Aktarım Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="b51a5-181">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="b51a5-182">X.509 sertifikaları İşlem Yöneticisi Kimliğini oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b51a5-182">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="b51a5-183">İstemci/sunucu kimlik doğrulaması gereklidir ve istemci/sunucu yetkilendirmesi bir uygulama ayrıntısı olarak bırakılır:</span><span class="sxs-lookup"><span data-stu-id="b51a5-183">Client/server authentication is required, and client/server authorization is left as an implementation detail:</span></span>  
  
- <span data-ttu-id="b51a5-184">R1111: Tel üzerinde sunulan X.509 sertifikaları, kaynak makinenin tam nitelikli alan adı (FQDN) eşleşen bir konu adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b51a5-184">R1111: X.509 certificates presented over the wire must have a subject name that matches the fully qualified domain name (FQDN) of the originating machine.</span></span>  
  
- <span data-ttu-id="b51a5-185">B1112: DNS, x.509 konu adı denetimleri için sistemdeki her gönderen-alıcı çifti arasında işlevsel olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b51a5-185">B1112: DNS must be functional between each sender-receiver pair in the system for X.509 subject name checks to succeed.</span></span>  
  
#### <a name="activation-and-registration-binding-configuration"></a><span data-ttu-id="b51a5-186">Etkinleştirme ve Kayıt Bağlama Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="b51a5-186">Activation and Registration Binding Configuration</span></span>  
 <span data-ttu-id="b51a5-187">WCF, HTTPS üzerinden korelasyon içeren istek/yanıt çift yönlü bağlama gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b51a5-187">WCF requires request/reply duplex binding with correlation over HTTPS.</span></span> <span data-ttu-id="b51a5-188">(İstek/yanıt iletisi değişim şekillerinin korelasyon ve açıklamaları hakkında daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="b51a5-188">(For more information about correlation and descriptions of the request/reply message exchange patterns, see WS-Atomic Transaction, Section 8.)</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="b51a5-189">2PC Protokol Bağlama Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="b51a5-189">2PC Protocol Binding Configuration</span></span>  
 <span data-ttu-id="b51a5-190">WCF, HTTPS üzerinden tek yönlü (datagram) iletileri destekler.</span><span class="sxs-lookup"><span data-stu-id="b51a5-190">WCF supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="b51a5-191">İletiler arasındaki korelasyon bir uygulama ayrıntısı olarak bırakılır.</span><span class="sxs-lookup"><span data-stu-id="b51a5-191">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="b51a5-192">B1131: WCF'nin 2PC iletilerinin korelasyonuna ulaşmak için uygulamalar WS-Addressing'de açıklandığı şekilde desteklenmelidir. `wsa:ReferenceParameters`</span><span class="sxs-lookup"><span data-stu-id="b51a5-192">B1131: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of WCF’s 2PC messages.</span></span>  
  
### <a name="transaction-manager-mixed-security-binding"></a><span data-ttu-id="b51a5-193">İşlem Yöneticisi Karışık Güvenlik Bağlama</span><span class="sxs-lookup"><span data-stu-id="b51a5-193">Transaction Manager Mixed Security Binding</span></span>  
 <span data-ttu-id="b51a5-194">Bu, kimlik kuruluş amaçları için WS-Koordinasyon Verilen Belirteç modeliyle birlikte taşıma güvenliğini kullanan alternatif (karma mod) bağlayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="b51a5-194">This is an alternate (mixed mode) binding that uses transport security combined with the WS-Coordination Issued Token model for identity establishment purposes.</span></span> <span data-ttu-id="b51a5-195">Etkinleştirme ve Kayıt, iki bağlama arasında farklılık gösteren tek öğelerdir.</span><span class="sxs-lookup"><span data-stu-id="b51a5-195">Activation and Registration are the only elements that differ between the two bindings.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="b51a5-196">HTTPS Aktarım Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="b51a5-196">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="b51a5-197">X.509 sertifikaları İşlem Yöneticisi Kimliğini oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b51a5-197">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="b51a5-198">İstemci/Sunucu kimlik doğrulaması gereklidir ve istemci/sunucu yetkilendirmesi bir uygulama ayrıntısı olarak bırakılır.</span><span class="sxs-lookup"><span data-stu-id="b51a5-198">Client/Server authentication is required, and client/server authorization is left as an implementation detail.</span></span>  
  
#### <a name="activation-message-binding-configuration"></a><span data-ttu-id="b51a5-199">Etkinleştirme İleti bağlama yapılandırması</span><span class="sxs-lookup"><span data-stu-id="b51a5-199">Activation Message Binding Configuration</span></span>  
 <span data-ttu-id="b51a5-200">Etkinleştirme İletileri genellikle bir uygulama ve yerel İşlem Yöneticisi arasında meydana geldiğinden, genellikle birlikte çalışabilirlik katılmaz.</span><span class="sxs-lookup"><span data-stu-id="b51a5-200">Activation Messages usually do not participate in interoperability because they typically occur between an application and its local Transaction Manager.</span></span>  
  
 <span data-ttu-id="b51a5-201">B1221: WCF, Etkinleştirme iletileri için çift yönlü HTTPS bağlama [(Mesajlaşma Protokolleri'nde](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)açıklanan) kullanır.</span><span class="sxs-lookup"><span data-stu-id="b51a5-201">B1221: WCF uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) for Activation messages.</span></span> <span data-ttu-id="b51a5-202">İstek ve Yanıt iletileri WS-At 1.0 için WS-Adresleme 2004/08 ve WS-AT 1.1 için WS-Addressing 2005/08 kullanılarak ilişkilidir.</span><span class="sxs-lookup"><span data-stu-id="b51a5-202">Request and Reply messages are correlated using WS-Addressing 2004/08 for WS-AT 1.0 and WS-Addressing 2005/08 for WS-AT 1.1.</span></span>  
  
 <span data-ttu-id="b51a5-203">WS-Atomik İşlem belirtimi, Bölüm 8, korelasyon ve ileti alışverişi desenleri hakkında daha fazla ayrıntı açıklar.</span><span class="sxs-lookup"><span data-stu-id="b51a5-203">WS-Atomic Transaction specification, Section 8, describes further details about correlation and the message exchange patterns.</span></span>  
  
- <span data-ttu-id="b51a5-204">R1222: Bir `CreateCoordinationContext`aldıktan sonra, Koordinatör `SecurityContextToken` ilişkili bir `STx`sır ile bir sorunu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b51a5-204">R1222: Upon receiving a `CreateCoordinationContext`, the Coordinator must issue a `SecurityContextToken` with associated secret `STx`.</span></span> <span data-ttu-id="b51a5-205">Bu belirteç, `t:IssuedTokens` WS-Trust belirtimini izleyen bir üstbilgi içinde döndürülür.</span><span class="sxs-lookup"><span data-stu-id="b51a5-205">This token is returned inside a `t:IssuedTokens` header following WS-Trust specification.</span></span>  
  
- <span data-ttu-id="b51a5-206">R1223: Etkinleştirme varolan bir Koordinasyon Bağlamı içinde `SecurityContextToken` gerçekleşirse, varolan `CreateCoordinationContext` Bağlam ile ilişkili `t:IssuedTokens` üstbilginin iletiüzerinde akması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b51a5-206">R1223: If Activation occurs within an existing Coordination Context, the `t:IssuedTokens` header with the `SecurityContextToken` associated with existing Context must flow on the `CreateCoordinationContext` message.</span></span>  
  
 <span data-ttu-id="b51a5-207">Giden `wscoor:CreateCoordinationContextResponse` `t:IssuedTokens` iletiye iliştirmek için yeni bir üstbilgi oluşturulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b51a5-207">A new `t:IssuedTokens` header should be generated for attaching to the outgoing `wscoor:CreateCoordinationContextResponse` message.</span></span>  
  
#### <a name="registration-message-binding-configuration"></a><span data-ttu-id="b51a5-208">Kayıt İletisi Bağlama Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="b51a5-208">Registration Message Binding Configuration</span></span>  
 <span data-ttu-id="b51a5-209">B1231: WCF çift yönlü HTTPS bağlama kullanır [(Mesajlaşma Protokolleri'nde](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)açıklanmıştır).</span><span class="sxs-lookup"><span data-stu-id="b51a5-209">B1231: WCF uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)).</span></span> <span data-ttu-id="b51a5-210">İstek ve Yanıt iletileri WS-At 1.0 için WS-Adresleme 2004/08 ve WS-AT 1.1 için WS-Addressing 2005/08 kullanılarak ilişkilidir.</span><span class="sxs-lookup"><span data-stu-id="b51a5-210">Request and Reply messages are correlated using WS-Addressing 2004/08 for WS-AT 1.0 and WS-Addressing 2005/08 for WS-AT 1.1.</span></span>  
  
 <span data-ttu-id="b51a5-211">WS-AtomicTransaction, Bölüm 8, korelasyon ve ileti alışverişi desenleri açıklamaları hakkında daha fazla bilgi açıklar.</span><span class="sxs-lookup"><span data-stu-id="b51a5-211">WS-AtomicTransaction, Section 8, describes further details about correlation and descriptions of the message exchange patterns.</span></span>  
  
 <span data-ttu-id="b51a5-212">R1232: Giden `wscoor:Register` iletiler Güvenlik `IssuedTokenOverTransport` [Protokolleri'nde](../../../../docs/framework/wcf/feature-details/security-protocols.md)açıklanan kimlik doğrulama modunu kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b51a5-212">R1232: Outgoing `wscoor:Register` messages must use the `IssuedTokenOverTransport` authentication mode described in [Security Protocols](../../../../docs/framework/wcf/feature-details/security-protocols.md).</span></span>  
  
 <span data-ttu-id="b51a5-213">`SecurityContextToken STx` Öğe, `wsse:Timestamp` verilen kullanılarak imzalanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b51a5-213">The `wsse:Timestamp` element must be signed using the `SecurityContextToken STx` issued.</span></span> <span data-ttu-id="b51a5-214">Bu imza, belirli bir işlemle ilişkili belirteç sahibi olduğunun kanıtıdır ve harekette kaydolan bir katılımcının kimliğini doğrulamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b51a5-214">This signature is a proof of possession of the token associated with particular transaction and is used to authenticate a participant enlisting in the transaction.</span></span> <span data-ttu-id="b51a5-215">RegistrationResponse iletisi HTTPS üzerinden geri gönderilir.</span><span class="sxs-lookup"><span data-stu-id="b51a5-215">The RegistrationResponse message is sent back over HTTPS.</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="b51a5-216">2PC Protokol Bağlama Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="b51a5-216">2PC Protocol Binding Configuration</span></span>  
 <span data-ttu-id="b51a5-217">WCF, HTTPS üzerinden tek yönlü (datagram) iletileri destekler.</span><span class="sxs-lookup"><span data-stu-id="b51a5-217">WCF supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="b51a5-218">İletiler arasındaki korelasyon bir uygulama ayrıntısı olarak bırakılır.</span><span class="sxs-lookup"><span data-stu-id="b51a5-218">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="b51a5-219">B1241: WCF'nin 2PC iletilerinin korelasyonuna ulaşmak için uygulamalar WS-Addressing'de açıklandığı şekilde desteklenmelidir. `wsa:ReferenceParameters`</span><span class="sxs-lookup"><span data-stu-id="b51a5-219">B1241: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of WCF’s 2PC messages.</span></span>  
  
## <a name="application-message-exchange"></a><span data-ttu-id="b51a5-220">Uygulama İletisi Değişimi</span><span class="sxs-lookup"><span data-stu-id="b51a5-220">Application Message Exchange</span></span>  
 <span data-ttu-id="b51a5-221">Uygulamalar, aşağıdaki güvenlik gereksinimlerini karşıladığı sürece, uygulamadan uygulamaya iletiler için belirli bir bağlamayı kullanmakta serbesttir:</span><span class="sxs-lookup"><span data-stu-id="b51a5-221">Applications are free to use any particular binding for application-to-application messages, as long as the binding meets the following security requirements:</span></span>  
  
- <span data-ttu-id="b51a5-222">R2001: Uygulama dan uygulama iletileri `t:IssuedTokens` üstbilgi ile `CoordinationContext` birlikte iletinin üstbilgi de akmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b51a5-222">R2001: Application-to-application messages must flow the `t:IssuedTokens` header along with the `CoordinationContext` in the header of the message.</span></span>  
  
- <span data-ttu-id="b51a5-223">R2002: Bütünlük ve gizlilik `t:IssuedToken` sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b51a5-223">R2002: Integrity and confidentiality of `t:IssuedToken` must be provided.</span></span>  
  
 <span data-ttu-id="b51a5-224">Üstbilgi. `CoordinationContext` `wscoor:Identifier`</span><span class="sxs-lookup"><span data-stu-id="b51a5-224">The `CoordinationContext` header contains `wscoor:Identifier`.</span></span> <span data-ttu-id="b51a5-225">Tanımı hem `xsd:AnyURI` mutlak hem de göreceli URI kullanımına izin `wscoor:Identifiers`verirken, WCF yalnızca mutlak URI'leri destekler.</span><span class="sxs-lookup"><span data-stu-id="b51a5-225">While the definition of `xsd:AnyURI` allows the use of both absolute and relative URIs, WCF supports only `wscoor:Identifiers`, which are absolute URIs.</span></span>  
  
 <span data-ttu-id="b51a5-226">B2003: `wscoor:Identifier` Göreceli uri `wscoor:CoordinationContext` ise, hatalar işlemsel WCF hizmetlerinden iade edilecektir.</span><span class="sxs-lookup"><span data-stu-id="b51a5-226">B2003: If the `wscoor:Identifier` of the `wscoor:CoordinationContext` is a relative URI, faults will be returned from transactional WCF services.</span></span>  
  
## <a name="message-examples"></a><span data-ttu-id="b51a5-227">İleti Örnekleri</span><span class="sxs-lookup"><span data-stu-id="b51a5-227">Message Examples</span></span>  
  
### <a name="createcoordinationcontext-requestresponse-messages"></a><span data-ttu-id="b51a5-228">CreateCoordinationContext İstek/Yanıt İletileri</span><span class="sxs-lookup"><span data-stu-id="b51a5-228">CreateCoordinationContext Request/Response Messages</span></span>  
 <span data-ttu-id="b51a5-229">Aşağıdaki iletiler bir istek/yanıt deseni izler.</span><span class="sxs-lookup"><span data-stu-id="b51a5-229">The following messages follow a request/response pattern.</span></span>  
  
#### <a name="createcoordinationcontext-with-wscoor-10"></a><span data-ttu-id="b51a5-230">WSCoor 1.0 ile CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="b51a5-230">CreateCoordinationContext with WSCoor 1.0</span></span>  
  
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
        <wsu:Created>2005-12-15T23:36:09.921Z</wsu:Created>  
        <wsu:Expires>2005-12-15T23:41:09.921Z</wsu:Expires>  
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
  
#### <a name="createcoordinationcontext-with-wscoor-11"></a><span data-ttu-id="b51a5-231">WSCoor 1.1 ile CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="b51a5-231">CreateCoordinationContext with WSCoor 1.1</span></span>  
  
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
<wsu:Created>2005-12-15T23:36:09.921Z</wsu:Created>  
<wsu:Expires>2005-12-15T23:41:09.921Z</wsu:Expires>  
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
  
#### <a name="createcoordinationcontextresponse-with-trust-pre-13-and-wscoor-10"></a><span data-ttu-id="b51a5-232">Güven Pre-1.3 ve WSCoor 1.0 ile CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="b51a5-232">CreateCoordinationContextResponse with Trust Pre-1.3 and WSCoor 1.0</span></span>  
  
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
  
#### <a name="createcoordinationcontextresponse-with-trust-13-and-wscoor-11"></a><span data-ttu-id="b51a5-233">Güven 1.3 ve WSCoor 1.1 ile KoordinasyonBağlam Yanıtı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b51a5-233">CreateCoordinationContextResponse with Trust 1.3 and WSCoor 1.1</span></span>  
  
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
  
### <a name="registration-messages"></a><span data-ttu-id="b51a5-234">Kayıt Mesajları</span><span class="sxs-lookup"><span data-stu-id="b51a5-234">Registration Messages</span></span>  
 <span data-ttu-id="b51a5-235">Aşağıdaki iletiler kayıt iletileridir.</span><span class="sxs-lookup"><span data-stu-id="b51a5-235">The following messages are registration messages.</span></span>  
  
#### <a name="register-with-wscoor-10"></a><span data-ttu-id="b51a5-236">WSCoor 1.0 ile kaydolun</span><span class="sxs-lookup"><span data-stu-id="b51a5-236">Register with WSCoor 1.0</span></span>  
  
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
  
#### <a name="register-with-wscoor-11"></a><span data-ttu-id="b51a5-237">WSCoor 1.1 ile kaydolun</span><span class="sxs-lookup"><span data-stu-id="b51a5-237">Register with WSCoor 1.1</span></span>  
  
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
  
#### <a name="register-response-with-wscoor-10"></a><span data-ttu-id="b51a5-238">WSCoor 1.0 ile Yanıt Kaydol</span><span class="sxs-lookup"><span data-stu-id="b51a5-238">Register Response with WSCoor 1.0</span></span>  
  
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
  
#### <a name="register-response-with-wscoor-11"></a><span data-ttu-id="b51a5-239">WSCoor 1.1 ile Yanıt Kaydol</span><span class="sxs-lookup"><span data-stu-id="b51a5-239">Register Response with WSCoor 1.1</span></span>  
  
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
  
### <a name="two-phase-commit-protocol-messages"></a><span data-ttu-id="b51a5-240">İki Aşamalı Commit Protokol İletileri</span><span class="sxs-lookup"><span data-stu-id="b51a5-240">Two Phase Commit Protocol Messages</span></span>  
 <span data-ttu-id="b51a5-241">Aşağıdaki ileti, iki aşamalı commit (2PC) protokolü ile ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="b51a5-241">The following message relates to the two-phase commit (2PC) protocol.</span></span>  
  
#### <a name="commit-with-wsat-10"></a><span data-ttu-id="b51a5-242">WSAT 1.0 ile işleme</span><span class="sxs-lookup"><span data-stu-id="b51a5-242">Commit with WSAT 1.0</span></span>  
  
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
  
#### <a name="commit-with-wsat-11"></a><span data-ttu-id="b51a5-243">WSAT 1.1 ile işleme</span><span class="sxs-lookup"><span data-stu-id="b51a5-243">Commit with WSAT 1.1</span></span>  
  
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
  
### <a name="application-messages"></a><span data-ttu-id="b51a5-244">Uygulama Mesajları</span><span class="sxs-lookup"><span data-stu-id="b51a5-244">Application Messages</span></span>  
 <span data-ttu-id="b51a5-245">Aşağıdaki iletiler uygulama iletileridir.</span><span class="sxs-lookup"><span data-stu-id="b51a5-245">The following messages are application messages.</span></span>  
  
#### <a name="application-message-request"></a><span data-ttu-id="b51a5-246">Uygulama mesajı-İstek</span><span class="sxs-lookup"><span data-stu-id="b51a5-246">Application message-Request</span></span>  
  
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
    <wsse11:EncryptedHeader>  
     <!-- encrypted wscoor:CoordinationContext header containing CCi -->  
    </wsse11:EncryptedHeader>  
    <wsse11:EncryptedHeader>
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

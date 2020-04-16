---
title: İşlem Protokolleri sürüm 1.0
ms.date: 03/30/2017
ms.assetid: 034679af-0002-402e-98a8-ef73dcd71bb6
ms.openlocfilehash: a775ca395e01e7ecbc676ba3ec97d19ae10b4f49
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464025"
---
# <a name="transaction-protocols-version-10"></a><span data-ttu-id="2c4c4-102">İşlem Protokolleri sürüm 1.0</span><span class="sxs-lookup"><span data-stu-id="2c4c4-102">Transaction Protocols version 1.0</span></span>
<span data-ttu-id="2c4c4-103">Windows Communication Foundation (WCF) sürüm 1, WS-Atomic Transaction ve WS-Coordination protokollerinin 1.0 sürümünü uygular.</span><span class="sxs-lookup"><span data-stu-id="2c4c4-103">Windows Communication Foundation (WCF) version 1 implements version 1.0 of the WS-Atomic Transaction and WS-Coordination protocols.</span></span> <span data-ttu-id="2c4c4-104">Sürüm 1.1 hakkında daha fazla bilgi için [İşlem Protokolleri'ne](../../../../docs/framework/wcf/feature-details/transaction-protocols.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="2c4c4-104">For more information about version 1.1, see [Transaction Protocols](../../../../docs/framework/wcf/feature-details/transaction-protocols.md).</span></span>  
  
|<span data-ttu-id="2c4c4-105">Belirtim/Belge</span><span class="sxs-lookup"><span data-stu-id="2c4c4-105">Specification/Document</span></span>|<span data-ttu-id="2c4c4-106">Bağlantı</span><span class="sxs-lookup"><span data-stu-id="2c4c4-106">Link</span></span>|  
|-----------------------------|----------|  
|<span data-ttu-id="2c4c4-107">WS-Koordinasyon</span><span class="sxs-lookup"><span data-stu-id="2c4c4-107">WS-Coordination</span></span>|<https://specs.xmlsoap.org/ws/2004/10/wscoor/wscoor.pdf>|  
|<span data-ttu-id="2c4c4-108">WS-AtomicTransaction</span><span class="sxs-lookup"><span data-stu-id="2c4c4-108">WS-AtomicTransaction</span></span>|<https://specs.xmlsoap.org/ws/2004/10/wsat/wsat.pdf>|  
  
 <span data-ttu-id="2c4c4-109">Bu protokol belirtimleri üzerinde birlikte çalışabilirlik iki düzeyde gereklidir: uygulamalar arasında ve işlem yöneticileri arasında (aşağıdaki şekilden bakın).</span><span class="sxs-lookup"><span data-stu-id="2c4c4-109">Interoperability on these protocol specifications is required at two levels: between applications and between transaction managers (see the following figure).</span></span> <span data-ttu-id="2c4c4-110">Belirtimler, her iki birlikte çalışabilirlik düzeyi için ileti biçimlerini ve ileti alışverişini ayrıntılı olarak açıklar.</span><span class="sxs-lookup"><span data-stu-id="2c4c4-110">Specifications describe in great detail the message formats and message exchange for both interoperability levels.</span></span> <span data-ttu-id="2c4c4-111">Uygulama-uygulama değişimi için belirli güvenlik, güvenilirlik ve kodlamalar, düzenli uygulama değişimi için olduğu gibi geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="2c4c4-111">Certain security, reliability, and encodings for application-to-application exchange apply as they do for regular application exchange.</span></span> <span data-ttu-id="2c4c4-112">Ancak, işlem yöneticileri arasında başarılı birlikte çalışabilirlik, genellikle kullanıcı tarafından yapılandırılmadığından, belirli bağlama üzerinde anlaşma gerektirir.</span><span class="sxs-lookup"><span data-stu-id="2c4c4-112">However, successful interoperability between transaction managers requires agreement on the particular binding, because it is usually not configured by the user.</span></span>  
  
 <span data-ttu-id="2c4c4-113">Bu konu, WS-Atomic Transaction (WS-AT) belirtiminin güvenlikle ilgili bir bileşimini açıklar ve işlem yöneticileri arasında iletişim için kullanılan güvenli bağlamayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="2c4c4-113">This topic describes a composition of the WS-Atomic Transaction (WS-AT) specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="2c4c4-114">Bu belgede açıklanan yaklaşım, IBM, IONA, Sun Microsystems ve diğerleri de dahil olmak üzere WS-AT ve WS-Coordination'un diğer uygulamalarıyla başarıyla test edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2c4c4-114">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination including IBM, IONA, Sun Microsystems, and others.</span></span>  
  
 <span data-ttu-id="2c4c4-115">Aşağıdaki şekil, iki işlem yöneticisi, İşlem Yöneticisi 1 ve İşlem Yöneticisi 2 ve iki uygulama, Uygulama 1 ve Uygulama 2 arasındaki birlikte çalışabilirliği gösterir:</span><span class="sxs-lookup"><span data-stu-id="2c4c4-115">The following figure depicts the interoperability between two transaction managers, Transaction Manager 1 and Transaction Manager 2, and two applications, Application 1 and Application 2:</span></span>  
  
 ![Hareket yöneticileri arasındaki etkileşimi gösteren ekran görüntüsü.](./media/transaction-protocols/transaction-managers-flow.gif)  
  
 <span data-ttu-id="2c4c4-117">Bir Başlatıcı (I) ve bir Katılımcı (P) ile tipik bir WS-Coordination/WS-Atomic Transaction senaryosudüşünün.</span><span class="sxs-lookup"><span data-stu-id="2c4c4-117">Consider a typical WS-Coordination/WS-Atomic Transaction scenario with one Initiator (I) and one Participant (P).</span></span> <span data-ttu-id="2c4c4-118">Hem Başlatıcı hem de Katılımcı'nın Işlem Yöneticileri (sırasıyla ITM ve PTM) vardır.</span><span class="sxs-lookup"><span data-stu-id="2c4c4-118">Both Initiator and Participant have Transaction Managers, (ITM and PTM, respectively).</span></span> <span data-ttu-id="2c4c4-119">İki aşamalı taahhüt bu konuda 2PC olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="2c4c4-119">Two-phase commit is referred to as 2PC in this topic.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2c4c4-120">1. CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="2c4c4-120">1. CreateCoordinationContext</span></span>|<span data-ttu-id="2c4c4-121">12. Uygulama Mesajı Yanıtı</span><span class="sxs-lookup"><span data-stu-id="2c4c4-121">12. Application Message Response</span></span>|  
|<span data-ttu-id="2c4c4-122">2. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="2c4c4-122">2. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="2c4c4-123">13. Taahhüt (Tamamlama)</span><span class="sxs-lookup"><span data-stu-id="2c4c4-123">13. Commit (Completion)</span></span>|  
|<span data-ttu-id="2c4c4-124">3. Kayıt (Tamamlama)</span><span class="sxs-lookup"><span data-stu-id="2c4c4-124">3. Register (Completion)</span></span>|<span data-ttu-id="2c4c4-125">14. Hazırlayın (2PC)</span><span class="sxs-lookup"><span data-stu-id="2c4c4-125">14. Prepare (2PC)</span></span>|  
|<span data-ttu-id="2c4c4-126">4. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="2c4c4-126">4. RegisterResponse</span></span>|<span data-ttu-id="2c4c4-127">15. Hazırlayın (2PC)</span><span class="sxs-lookup"><span data-stu-id="2c4c4-127">15. Prepare (2PC)</span></span>|  
|<span data-ttu-id="2c4c4-128">5. Uygulama Mesajı</span><span class="sxs-lookup"><span data-stu-id="2c4c4-128">5. Application Message</span></span>|<span data-ttu-id="2c4c4-129">16. Hazırlanan (2PC)</span><span class="sxs-lookup"><span data-stu-id="2c4c4-129">16. Prepared (2PC)</span></span>|  
|<span data-ttu-id="2c4c4-130">6. Bağlam ile Koordinasyon Bağlamı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="2c4c4-130">6. CreateCoordinationContext with Context</span></span>|<span data-ttu-id="2c4c4-131">17. Hazırlanan (2PC)</span><span class="sxs-lookup"><span data-stu-id="2c4c4-131">17. Prepared (2PC)</span></span>|  
|<span data-ttu-id="2c4c4-132">7. Kayıt (Dayanıklı)</span><span class="sxs-lookup"><span data-stu-id="2c4c4-132">7. Register (Durable)</span></span>|<span data-ttu-id="2c4c4-133">18. Taahhüt (Tamamlama)</span><span class="sxs-lookup"><span data-stu-id="2c4c4-133">18. Committed (Completion)</span></span>|  
|<span data-ttu-id="2c4c4-134">8. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="2c4c4-134">8. RegisterResponse</span></span>|<span data-ttu-id="2c4c4-135">19. Taahhüt (2PC)</span><span class="sxs-lookup"><span data-stu-id="2c4c4-135">19. Commit (2PC)</span></span>|  
|<span data-ttu-id="2c4c4-136">9. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="2c4c4-136">9. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="2c4c4-137">20. Taahhüt (2PC)</span><span class="sxs-lookup"><span data-stu-id="2c4c4-137">20. Commit (2PC)</span></span>|  
|<span data-ttu-id="2c4c4-138">10. Kayıt (Dayanıklı)</span><span class="sxs-lookup"><span data-stu-id="2c4c4-138">10. Register (Durable)</span></span>|<span data-ttu-id="2c4c4-139">21. Taahhüt (2PC)</span><span class="sxs-lookup"><span data-stu-id="2c4c4-139">21. Committed (2PC)</span></span>|  
|<span data-ttu-id="2c4c4-140">11. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="2c4c4-140">11. RegisterResponse</span></span>|<span data-ttu-id="2c4c4-141">22. Taahhüt (2PC)</span><span class="sxs-lookup"><span data-stu-id="2c4c4-141">22. Committed (2PC)</span></span>|  
  
 <span data-ttu-id="2c4c4-142">Bu belge, WS-AtomicTransaction belirtiminin güvenlikle ilgili bir bileşimini açıklar ve işlem yöneticileri arasında iletişim için kullanılan güvenli bağlamayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="2c4c4-142">This document describes a composition of the WS-AtomicTransaction specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="2c4c4-143">Bu belgede açıklanan yaklaşım, WS-AT ve WS-Coordination'un diğer uygulamalarıyla başarıyla test edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2c4c4-143">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination.</span></span>  
  
 <span data-ttu-id="2c4c4-144">Şekil ve tablo, güvenlik açısından dört ileti sınıfını gösterir:</span><span class="sxs-lookup"><span data-stu-id="2c4c4-144">The figure and table illustrate four classes of messages from the viewpoint of security:</span></span>  
  
- <span data-ttu-id="2c4c4-145">Etkinleştirme iletileri (CreateCoordinationContext ve CreateCoordinationContextResponse).</span><span class="sxs-lookup"><span data-stu-id="2c4c4-145">Activation messages (CreateCoordinationContext and CreateCoordinationContextResponse).</span></span>  
  
- <span data-ttu-id="2c4c4-146">Kayıt mesajları (Kayıt ve Kayıt Yanıtı)</span><span class="sxs-lookup"><span data-stu-id="2c4c4-146">Registration messages (Register and RegisterResponse)</span></span>  
  
- <span data-ttu-id="2c4c4-147">Protokol iletileri (Hazırla, Geri Alma, Commit, İptal vb.)</span><span class="sxs-lookup"><span data-stu-id="2c4c4-147">Protocol messages (Prepare, Rollback, Commit, Aborted, and so on).</span></span>  
  
- <span data-ttu-id="2c4c4-148">Uygulama iletileri.</span><span class="sxs-lookup"><span data-stu-id="2c4c4-148">Application messages.</span></span>  
  
 <span data-ttu-id="2c4c4-149">İlk üç ileti sınıfı İşlem Yöneticisi iletileri olarak kabul edilir ve bağlama yapılandırmaları daha sonra bu konunun "Uygulama İletisi Değişimi"nde açıklanır.</span><span class="sxs-lookup"><span data-stu-id="2c4c4-149">The first three message classes are considered Transaction Manager messages and their binding configuration is described in the "Application Message Exchange" later in this topic.</span></span> <span data-ttu-id="2c4c4-150">Dördüncü sınıf ileti, uygulama iletilerine uygulamadır ve daha sonra bu konunun "İleti Örnekleri" bölümünde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="2c4c4-150">The fourth class of message is application to application messages and is described in the "Message Examples" section later in this topic.</span></span> <span data-ttu-id="2c4c4-151">Bu bölümde, WCF tarafından bu sınıfların her biri için kullanılan protokol bağlamaları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2c4c4-151">This section describes the protocol bindings used for each of these classes by WCF.</span></span>  
  
 <span data-ttu-id="2c4c4-152">Bu belge boyunca aşağıdaki XML Ad Alanları ve ilişkili önekleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2c4c4-152">The following XML Namespaces and associated prefixes are used throughout this document.</span></span>  
  
|<span data-ttu-id="2c4c4-153">Ön ek</span><span class="sxs-lookup"><span data-stu-id="2c4c4-153">Prefix</span></span>|<span data-ttu-id="2c4c4-154">Namespace URI</span><span class="sxs-lookup"><span data-stu-id="2c4c4-154">Namespace URI</span></span>|  
|------------|-------------------|  
|<span data-ttu-id="2c4c4-155">s11</span><span class="sxs-lookup"><span data-stu-id="2c4c4-155">s11</span></span>|http://schemas.xmlsoap.org/soap/envelope|  
|<span data-ttu-id="2c4c4-156">Wsa</span><span class="sxs-lookup"><span data-stu-id="2c4c4-156">wsa</span></span>|http://www.w3.org/2004/08/addressing|  
|<span data-ttu-id="2c4c4-157">wscoor</span><span class="sxs-lookup"><span data-stu-id="2c4c4-157">wscoor</span></span>|http://schemas.xmlsoap.org/ws/2004/10/wscoor|  
|<span data-ttu-id="2c4c4-158">wsat</span><span class="sxs-lookup"><span data-stu-id="2c4c4-158">wsat</span></span>|http://schemas.xmlsoap.org/ws/2004/10/wsat|  
|<span data-ttu-id="2c4c4-159">t</span><span class="sxs-lookup"><span data-stu-id="2c4c4-159">t</span></span>|http://schemas.xmlsoap.org/ws/2005/02/trust|  
|<span data-ttu-id="2c4c4-160">o</span><span class="sxs-lookup"><span data-stu-id="2c4c4-160">o</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd|  
|<span data-ttu-id="2c4c4-161">Xsd</span><span class="sxs-lookup"><span data-stu-id="2c4c4-161">xsd</span></span>|http://www.w3.org/2001/XMLSchema|  
  
## <a name="transaction-manager-bindings"></a><span data-ttu-id="2c4c4-162">İşlem Yöneticisi Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="2c4c4-162">Transaction Manager Bindings</span></span>  
 <span data-ttu-id="2c4c4-163">R1001: İşlem Yöneticileri WS-Atomik İşlem ve WS-Koordinasyon ileti alışverişi için SOAP 1.1 ve WS-Adresleme 2004/08 kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2c4c4-163">R1001: Transaction Managers must use SOAP 1.1 and WS-Addressing 2004/08 for WS-Atomic Transaction and WS-Coordination message exchanges.</span></span>  
  
 <span data-ttu-id="2c4c4-164">Uygulama iletileri bu bağlamalarla sınırlandırılmamıştır ve daha sonra açıklanır.</span><span class="sxs-lookup"><span data-stu-id="2c4c4-164">Application messages are not constrained to these bindings and are described later.</span></span>  
  
### <a name="transaction-manager-https-binding"></a><span data-ttu-id="2c4c4-165">İşlem Yöneticisi HTTPS Ciltleme</span><span class="sxs-lookup"><span data-stu-id="2c4c4-165">Transaction Manager HTTPS Binding</span></span>  
 <span data-ttu-id="2c4c4-166">İşlem yöneticisi HTTPS bağlama, güvenliği sağlamak ve hareket ağacındaki her gönderen-alıcı çifti arasında güven oluşturmak için yalnızca aktarım güvenliğine dayanır.</span><span class="sxs-lookup"><span data-stu-id="2c4c4-166">The transaction manager HTTPS binding relies solely on transport security to achieve security and establish trust between each sender-receiver pair in the transaction tree.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="2c4c4-167">HTTPS Aktarım Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="2c4c4-167">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="2c4c4-168">X.509 sertifikaları İşlem Yöneticisi Kimliğini oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2c4c4-168">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="2c4c4-169">İstemci/sunucu kimlik doğrulaması gereklidir ve istemci/sunucu yetkilendirmesi bir uygulama ayrıntısı olarak bırakılır:</span><span class="sxs-lookup"><span data-stu-id="2c4c4-169">Client/server authentication is required, and client/server authorization is left as an implementation detail:</span></span>  
  
- <span data-ttu-id="2c4c4-170">R1111: Tel üzerinde sunulan X.509 sertifikaları, kaynak makinenin tam nitelikli alan adı (FQDN) eşleşen bir konu adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2c4c4-170">R1111: X.509 certificates presented over the wire must have a subject name that matches the fully qualified domain name (FQDN) of the originating machine.</span></span>  
  
- <span data-ttu-id="2c4c4-171">B1112: DNS, x.509 konu adı denetimleri için sistemdeki her gönderen-alıcı çifti arasında işlevsel olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2c4c4-171">B1112: DNS must be functional between each sender-receiver pair in the system for X.509 subject name checks to succeed.</span></span>  
  
#### <a name="activation-and-registration-binding-configuration"></a><span data-ttu-id="2c4c4-172">Etkinleştirme ve Kayıt Bağlama Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="2c4c4-172">Activation and Registration Binding Configuration</span></span>  
 <span data-ttu-id="2c4c4-173">WCF, HTTPS üzerinden korelasyon içeren istek/yanıt çift yönlü bağlama gerektirir.</span><span class="sxs-lookup"><span data-stu-id="2c4c4-173">WCF requires request/reply duplex binding with correlation over HTTPS.</span></span> <span data-ttu-id="2c4c4-174">(İstek/yanıt iletisi değişim şekillerinin korelasyon ve açıklamaları hakkında daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="2c4c4-174">(For more information about correlation and descriptions of the request/reply message exchange patterns, see WS-Atomic Transaction, Section 8.)</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="2c4c4-175">2PC Protokol Bağlama Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="2c4c4-175">2PC Protocol Binding Configuration</span></span>  
 <span data-ttu-id="2c4c4-176">WCF, HTTPS üzerinden tek yönlü (datagram) iletileri destekler.</span><span class="sxs-lookup"><span data-stu-id="2c4c4-176">WCF supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="2c4c4-177">İletiler arasındaki korelasyon bir uygulama ayrıntısı olarak bırakılır.</span><span class="sxs-lookup"><span data-stu-id="2c4c4-177">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="2c4c4-178">B2131: WCF'nin 2PC iletilerinin korelasyonuna ulaşmak için uygulamalar WS-Addressing'de açıklandığı şekilde desteklenmelidir. `wsa:ReferenceParameters`</span><span class="sxs-lookup"><span data-stu-id="2c4c4-178">B2131: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of WCF’s 2PC messages.</span></span>  
  
### <a name="transaction-manager-mixed-security-binding"></a><span data-ttu-id="2c4c4-179">İşlem Yöneticisi Karışık Güvenlik Bağlama</span><span class="sxs-lookup"><span data-stu-id="2c4c4-179">Transaction Manager Mixed Security Binding</span></span>  
 <span data-ttu-id="2c4c4-180">Bu, kimlik kuruluş amaçları için WS-Koordinasyon Verilen Belirteç modeliyle birlikte taşıma güvenliğini kullanan alternatif (karma mod) bağlayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="2c4c4-180">This is an alternate (mixed mode) binding that uses transport security combined with the  WS-Coordination Issued Token model for identity establishment purposes.</span></span>  <span data-ttu-id="2c4c4-181">Etkinleştirme ve Kayıt, iki bağlama arasında farklılık gösteren tek öğelerdir.</span><span class="sxs-lookup"><span data-stu-id="2c4c4-181">Activation and Registration are the only elements that differ between the two bindings.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="2c4c4-182">HTTPS Aktarım Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="2c4c4-182">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="2c4c4-183">X.509 sertifikaları İşlem Yöneticisi Kimliğini oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2c4c4-183">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="2c4c4-184">İstemci/Sunucu kimlik doğrulaması gereklidir ve istemci/sunucu yetkilendirmesi bir uygulama ayrıntısı olarak bırakılır.</span><span class="sxs-lookup"><span data-stu-id="2c4c4-184">Client/Server authentication is required, and client/server authorization is left as an implementation detail.</span></span>  
  
#### <a name="activation-message-binding-configuration"></a><span data-ttu-id="2c4c4-185">Etkinleştirme İleti bağlama yapılandırması</span><span class="sxs-lookup"><span data-stu-id="2c4c4-185">Activation Message Binding Configuration</span></span>  
 <span data-ttu-id="2c4c4-186">Etkinleştirme İletileri genellikle bir uygulama ve yerel İşlem Yöneticisi arasında meydana geldiğinden, genellikle birlikte çalışabilirlik katılmaz.</span><span class="sxs-lookup"><span data-stu-id="2c4c4-186">Activation Messages usually do not participate in interoperability because they typically occur between an application and its local Transaction Manager.</span></span>  
  
 <span data-ttu-id="2c4c4-187">B1221: WCF, Etkinleştirme iletileri için çift yönlü HTTPS bağlama [(Mesajlaşma Protokolleri'nde](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)açıklanan) kullanır.</span><span class="sxs-lookup"><span data-stu-id="2c4c4-187">B1221: WCF uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) for Activation messages.</span></span> <span data-ttu-id="2c4c4-188">İstek ve Yanıt iletileri WS-Adresleme 2004/08 kullanılarak ilişkilidir.</span><span class="sxs-lookup"><span data-stu-id="2c4c4-188">Request and Reply messages are correlated using WS-Addressing 2004/08.</span></span>  
  
 <span data-ttu-id="2c4c4-189">WS-Atomik İşlem belirtimi, Bölüm 8, korelasyon ve ileti alışverişi desenleri hakkında daha fazla ayrıntı açıklar.</span><span class="sxs-lookup"><span data-stu-id="2c4c4-189">WS-Atomic Transaction specification, Section 8, describes further details about correlation and the message exchange patterns.</span></span>  
  
- <span data-ttu-id="2c4c4-190">R1222: Bir `CreateCoordinationContext`aldıktan sonra, Koordinatör `SecurityContextToken` ilişkili bir `STx`sır ile bir sorunu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2c4c4-190">R1222: Upon receiving a `CreateCoordinationContext`, the Coordinator must issue a `SecurityContextToken` with associated secret `STx`.</span></span> <span data-ttu-id="2c4c4-191">Bu belirteç, `t:IssuedTokens` WS-Trust belirtimini izleyen bir üstbilgi içinde döndürülür.</span><span class="sxs-lookup"><span data-stu-id="2c4c4-191">This token is returned inside a `t:IssuedTokens` header following WS-Trust specification.</span></span>  
  
- <span data-ttu-id="2c4c4-192">R1223: Etkinleştirme varolan bir Koordinasyon Bağlamı içinde `SecurityContextToken` gerçekleşirse, varolan `CreateCoordinationContext` Bağlam ile ilişkili `t:IssuedTokens` üstbilginin iletiüzerinde akması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2c4c4-192">R1223: If Activation occurs within an existing Coordination Context, the `t:IssuedTokens` header with the `SecurityContextToken` associated with existing Context must flow on the `CreateCoordinationContext` message.</span></span>  
  
 <span data-ttu-id="2c4c4-193">Giden `wscoor:CreateCoordinationContextResponse` `t:IssuedTokens` iletiye iliştirmek için yeni bir üstbilgi oluşturulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2c4c4-193">A new `t:IssuedTokens` header should be generated for attaching to the outgoing `wscoor:CreateCoordinationContextResponse` message.</span></span>  
  
#### <a name="registration-message-binding-configuration"></a><span data-ttu-id="2c4c4-194">Kayıt İletisi Bağlama Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="2c4c4-194">Registration Message Binding Configuration</span></span>  
 <span data-ttu-id="2c4c4-195">B1231: WCF çift yönlü HTTPS bağlama kullanır [(Mesajlaşma Protokolleri'nde](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)açıklanmıştır).</span><span class="sxs-lookup"><span data-stu-id="2c4c4-195">B1231: WCF uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)).</span></span> <span data-ttu-id="2c4c4-196">İstek ve Yanıt iletileri WS-Adresleme 2004/08 kullanılarak ilişkilidir.</span><span class="sxs-lookup"><span data-stu-id="2c4c4-196">Request and Reply messages are correlated using WS-Addressing 2004/08.</span></span>  
  
 <span data-ttu-id="2c4c4-197">WS-AtomicTransaction, Bölüm 8, korelasyon ve ileti alışverişi desenleri açıklamaları hakkında daha fazla bilgi açıklar.</span><span class="sxs-lookup"><span data-stu-id="2c4c4-197">WS-AtomicTransaction, Section 8, describes further details about correlation and descriptions of the message exchange patterns.</span></span>  
  
 <span data-ttu-id="2c4c4-198">R1232: Giden `wscoor:Register` iletiler Güvenlik `IssuedTokenOverTransport` [Protokolleri'nde](../../../../docs/framework/wcf/feature-details/security-protocols.md)açıklanan kimlik doğrulama modunu kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2c4c4-198">R1232: Outgoing `wscoor:Register` messages must use the `IssuedTokenOverTransport` authentication mode described in [Security Protocols](../../../../docs/framework/wcf/feature-details/security-protocols.md).</span></span>  
  
 <span data-ttu-id="2c4c4-199">`SecurityContextToken STx` Öğe, `wsse:Timestamp` verilen kullanılarak imzalanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2c4c4-199">The `wsse:Timestamp` element must be signed using the `SecurityContextToken STx` issued.</span></span> <span data-ttu-id="2c4c4-200">Bu imza, belirli bir işlemle ilişkili belirteç sahibi olduğunun kanıtıdır ve harekette kaydolan bir katılımcının kimliğini doğrulamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2c4c4-200">This signature is a proof of possession of the token associated with particular transaction and is used to authenticate a participant enlisting in the transaction.</span></span> <span data-ttu-id="2c4c4-201">RegistrationResponse iletisi HTTPS üzerinden geri gönderilir.</span><span class="sxs-lookup"><span data-stu-id="2c4c4-201">The RegistrationResponse message is sent back over HTTPS.</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="2c4c4-202">2PC Protokol Bağlama Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="2c4c4-202">2PC Protocol Binding Configuration</span></span>  
 <span data-ttu-id="2c4c4-203">WCF, HTTPS üzerinden tek yönlü (datagram) iletileri destekler.</span><span class="sxs-lookup"><span data-stu-id="2c4c4-203">WCF supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="2c4c4-204">İletiler arasındaki korelasyon bir uygulama ayrıntısı olarak bırakılır.</span><span class="sxs-lookup"><span data-stu-id="2c4c4-204">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="2c4c4-205">B2131: WCF'nin 2PC iletilerinin korelasyonuna ulaşmak için uygulamalar WS-Addressing'de açıklandığı şekilde desteklenmelidir. `wsa:ReferenceParameters`</span><span class="sxs-lookup"><span data-stu-id="2c4c4-205">B2131: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of WCF’s 2PC messages.</span></span>  
  
## <a name="application-message-exchange"></a><span data-ttu-id="2c4c4-206">Uygulama İletisi Değişimi</span><span class="sxs-lookup"><span data-stu-id="2c4c4-206">Application Message Exchange</span></span>  
 <span data-ttu-id="2c4c4-207">Uygulamalar, aşağıdaki güvenlik gereksinimlerini karşıladığı sürece, uygulamadan uygulamaya iletiler için belirli bir bağlamayı kullanmakta serbesttir:</span><span class="sxs-lookup"><span data-stu-id="2c4c4-207">Applications are free to use any particular binding for application-to-application messages, as long as the binding meets the following security requirements:</span></span>  
  
- <span data-ttu-id="2c4c4-208">R2001: Uygulama dan uygulama iletileri `t:IssuedTokens` üstbilgi ile `CoordinationContext` birlikte iletinin üstbilgi de akmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2c4c4-208">R2001: Application-to-application messages must flow the `t:IssuedTokens` header along with the `CoordinationContext` in the header of the message.</span></span>  
  
- <span data-ttu-id="2c4c4-209">R2002: Bütünlük ve gizlilik `t:IssuedToken` sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2c4c4-209">R2002: Integrity and confidentiality of `t:IssuedToken` must be provided.</span></span>  
  
 <span data-ttu-id="2c4c4-210">Üstbilgi. `CoordinationContext` `wscoor:Identifier`</span><span class="sxs-lookup"><span data-stu-id="2c4c4-210">The `CoordinationContext` header contains `wscoor:Identifier`.</span></span> <span data-ttu-id="2c4c4-211">Tanımı hem `xsd:AnyURI` mutlak hem de göreceli URI kullanımına izin `wscoor:Identifiers`verirken, WCF yalnızca mutlak URI'leri destekler.</span><span class="sxs-lookup"><span data-stu-id="2c4c4-211">While the definition of `xsd:AnyURI` allows the use of both absolute and relative URIs, WCF supports only `wscoor:Identifiers`, which are absolute URIs.</span></span>  
  
 <span data-ttu-id="2c4c4-212">Göreceli `wscoor:Identifier` bir `wscoor:CoordinationContext` URI ise, hatalar işlemsel WCF hizmetlerinden döndürülür.</span><span class="sxs-lookup"><span data-stu-id="2c4c4-212">If the `wscoor:Identifier` of the `wscoor:CoordinationContext` is a relative URI, faults will be returned from transactional WCF services.</span></span>  
  
## <a name="message-examples"></a><span data-ttu-id="2c4c4-213">İleti Örnekleri</span><span class="sxs-lookup"><span data-stu-id="2c4c4-213">Message Examples</span></span>  
  
### <a name="createcoordinationcontext-requestresponse-messages"></a><span data-ttu-id="2c4c4-214">CreateCoordinationContext İstek/Yanıt İletileri</span><span class="sxs-lookup"><span data-stu-id="2c4c4-214">CreateCoordinationContext Request/Response Messages</span></span>  
 <span data-ttu-id="2c4c4-215">Aşağıdaki iletiler bir istek/yanıt deseni izler.</span><span class="sxs-lookup"><span data-stu-id="2c4c4-215">The following messages follow a request/response pattern.</span></span>  
  
#### <a name="createcoordinationcontext"></a><span data-ttu-id="2c4c4-216">CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="2c4c4-216">CreateCoordinationContext</span></span>  
  
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
  
#### <a name="createcoordinationcontextresponse"></a><span data-ttu-id="2c4c4-217">CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="2c4c4-217">CreateCoordinationContextResponse</span></span>  
  
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
  
### <a name="registration-messages"></a><span data-ttu-id="2c4c4-218">Kayıt Mesajları</span><span class="sxs-lookup"><span data-stu-id="2c4c4-218">Registration Messages</span></span>  
 <span data-ttu-id="2c4c4-219">Aşağıdaki iletiler kayıt iletileridir.</span><span class="sxs-lookup"><span data-stu-id="2c4c4-219">The following messages are registration messages.</span></span>  
  
#### <a name="register"></a><span data-ttu-id="2c4c4-220">Kaydettir</span><span class="sxs-lookup"><span data-stu-id="2c4c4-220">Register</span></span>  
  
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
  
#### <a name="register-response"></a><span data-ttu-id="2c4c4-221">Kayıt Yanıtı</span><span class="sxs-lookup"><span data-stu-id="2c4c4-221">Register Response</span></span>  
  
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
  
### <a name="two-phase-commit-protocol-messages"></a><span data-ttu-id="2c4c4-222">İki Aşamalı Commit Protokol İletileri</span><span class="sxs-lookup"><span data-stu-id="2c4c4-222">Two Phase Commit Protocol Messages</span></span>  
 <span data-ttu-id="2c4c4-223">Aşağıdaki ileti, iki aşamalı commit (2PC) protokolü ile ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="2c4c4-223">The following message relates to the two-phase commit (2PC) protocol.</span></span>  
  
#### <a name="commit"></a><span data-ttu-id="2c4c4-224">İşleme</span><span class="sxs-lookup"><span data-stu-id="2c4c4-224">Commit</span></span>  
  
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
  
### <a name="application-messages"></a><span data-ttu-id="2c4c4-225">Uygulama Mesajları</span><span class="sxs-lookup"><span data-stu-id="2c4c4-225">Application Messages</span></span>  
 <span data-ttu-id="2c4c4-226">Aşağıdaki iletiler uygulama iletileridir.</span><span class="sxs-lookup"><span data-stu-id="2c4c4-226">The following messages are application messages.</span></span>  
  
#### <a name="application-message-request"></a><span data-ttu-id="2c4c4-227">Uygulama mesajı-İstek</span><span class="sxs-lookup"><span data-stu-id="2c4c4-227">Application message-Request</span></span>  
  
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

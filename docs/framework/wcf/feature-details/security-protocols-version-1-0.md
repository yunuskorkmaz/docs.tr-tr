---
title: Güvenlik Protokolleri sürüm 1.0
ms.date: 03/30/2017
ms.assetid: ee3402d2-1076-410b-a3cb-fae0372bd7af
ms.openlocfilehash: 0b86d870350d8728134cd2b42bbeb232183535bc
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463799"
---
# <a name="security-protocols-version-10"></a><span data-ttu-id="ef812-102">Güvenlik Protokolleri sürüm 1.0</span><span class="sxs-lookup"><span data-stu-id="ef812-102">Security Protocols version 1.0</span></span>
<span data-ttu-id="ef812-103">Web Hizmetleri Güvenlik Protokolleri, varolan tüm kurumsal ileti güvenlik gereksinimlerini kapsayan Web hizmetleri güvenlik mekanizmaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="ef812-103">The Web Services Security Protocols provide Web services security mechanisms that cover all existing enterprise messaging security requirements.</span></span> <span data-ttu-id="ef812-104">Bu bölümde, aşağıdaki Web hizmetleri güvenlik protokolleri için Windows Communication <xref:System.ServiceModel.Channels.SecurityBindingElement>Foundation (WCF) sürüm 1.0 ayrıntıları (uygulandığında) açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ef812-104">This section describes the Windows Communication Foundation (WCF) version 1.0 details (implemented in the <xref:System.ServiceModel.Channels.SecurityBindingElement>) for the following Web services security protocols.</span></span>  
  
|<span data-ttu-id="ef812-105">Belirtim/Belge</span><span class="sxs-lookup"><span data-stu-id="ef812-105">Specification/Document</span></span>|<span data-ttu-id="ef812-106">Bağlantı</span><span class="sxs-lookup"><span data-stu-id="ef812-106">Link</span></span>|  
|-|-|  
|<span data-ttu-id="ef812-107">WSS: SOAP İleti Güvenliği 1.0</span><span class="sxs-lookup"><span data-stu-id="ef812-107">WSS: SOAP Message Security 1.0</span></span>|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf>|
|<span data-ttu-id="ef812-108">WSS: Kullanıcı Adı Belirteç Profili 1.0</span><span class="sxs-lookup"><span data-stu-id="ef812-108">WSS: Username Token Profile 1.0</span></span>|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf>|
|<span data-ttu-id="ef812-109">WSS: X509 Jeton Profili 1.0</span><span class="sxs-lookup"><span data-stu-id="ef812-109">WSS: X509 Token Profile 1.0</span></span>|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0.pdf>|
|<span data-ttu-id="ef812-110">WSS: SAML 1.1 Belirteç Profili 1.0</span><span class="sxs-lookup"><span data-stu-id="ef812-110">WSS: SAML 1.1 Token Profile 1.0</span></span>|<https://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.0.pdf>|
|<span data-ttu-id="ef812-111">WSS: SOAP İleti Güvenliği 1.1</span><span class="sxs-lookup"><span data-stu-id="ef812-111">WSS: SOAP Message Security 1.1</span></span>|<https://www.oasis-open.org/committees/download.php/16790/wss-v1.1-spec-os-SOAPMessageSecurity.pdf>|
|<span data-ttu-id="ef812-112">WSS Kullanıcı Adı Belirteç Profili 1.1</span><span class="sxs-lookup"><span data-stu-id="ef812-112">WSS Username Token Profile 1.1</span></span>|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf>|
|<span data-ttu-id="ef812-113">WSS: X.509 Jeton Profili 1.1</span><span class="sxs-lookup"><span data-stu-id="ef812-113">WSS: X.509 Token Profile 1.1</span></span>|<https://www.oasis-open.org/committees/download.php/16785/wss-v1.1-spec-os-x509TokenProfile.pdf>|
|<span data-ttu-id="ef812-114">WSS: Kerberos Token Profil 1.1</span><span class="sxs-lookup"><span data-stu-id="ef812-114">WSS: Kerberos Token Profile 1.1</span></span>|<https://www.oasis-open.org/committees/download.php/16788/wss-v1.1-spec-os-KerberosTokenProfile.pdf>|
|<span data-ttu-id="ef812-115">WSS: SAML 1.1 Belirteç Profili 1.1</span><span class="sxs-lookup"><span data-stu-id="ef812-115">WSS: SAML 1.1 Token Profile 1.1</span></span>|<https://www.oasis-open.org/committees/download.php/16768/wss-v1.1-spec-os-SAMLTokenProfile.pdf>|
|<span data-ttu-id="ef812-116">WS-Güvenli Konuşma</span><span class="sxs-lookup"><span data-stu-id="ef812-116">WS-Secure Conversation</span></span>|<https://specs.xmlsoap.org/ws/2005/02/sc/WS-SecureConversation.pdf>|
|<span data-ttu-id="ef812-117">WS-Güven</span><span class="sxs-lookup"><span data-stu-id="ef812-117">WS-Trust</span></span>|<https://specs.xmlsoap.org/ws/2005/02/trust/ws-trust.pdf>|
|<span data-ttu-id="ef812-118">Uygulama Notu:</span><span class="sxs-lookup"><span data-stu-id="ef812-118">Application Note:</span></span><br /><br /> <span data-ttu-id="ef812-119">TLS El Sıkışması için WS-Trust kullanma</span><span class="sxs-lookup"><span data-stu-id="ef812-119">Using WS-Trust for TLS Handshake</span></span>|<span data-ttu-id="ef812-120">Yayınlanacak</span><span class="sxs-lookup"><span data-stu-id="ef812-120">To be published</span></span>|  
|<span data-ttu-id="ef812-121">Uygulama Notu:</span><span class="sxs-lookup"><span data-stu-id="ef812-121">Application Note:</span></span><br /><br /> <span data-ttu-id="ef812-122">SPNEGO için WS-Trust'ı kullanma</span><span class="sxs-lookup"><span data-stu-id="ef812-122">Using WS-Trust for SPNEGO</span></span>|<span data-ttu-id="ef812-123">Yayınlanacak</span><span class="sxs-lookup"><span data-stu-id="ef812-123">To be published</span></span>|  
|<span data-ttu-id="ef812-124">Uygulama Notu:</span><span class="sxs-lookup"><span data-stu-id="ef812-124">Application Note:</span></span><br /><br /> <span data-ttu-id="ef812-125">Uç Nokta Referansları Ve Kimliğini Ele Veren Web Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="ef812-125">Web Services Addressing Endpoint References And Identity</span></span>|<span data-ttu-id="ef812-126">Yayınlanacak</span><span class="sxs-lookup"><span data-stu-id="ef812-126">To be published</span></span>|  
|<span data-ttu-id="ef812-127">WS-SecurityPolicy 1.1</span><span class="sxs-lookup"><span data-stu-id="ef812-127">WS-SecurityPolicy 1.1</span></span><br /><br /> <span data-ttu-id="ef812-128">(2005/07)</span><span class="sxs-lookup"><span data-stu-id="ef812-128">(2005/07)</span></span>|<https://specs.xmlsoap.org/ws/2005/07/securitypolicy/ws-securitypolicy.pdf><br /><br /> <span data-ttu-id="ef812-129">olarak OASIS WS-SX Teknik Komitesi'ne sunulan [errata](https://lists.oasis-open.org/archives/ws-sx/200512/msg00017.html) tarafından değiştirildi</span><span class="sxs-lookup"><span data-stu-id="ef812-129">as amended by [errata](https://lists.oasis-open.org/archives/ws-sx/200512/msg00017.html) submitted to OASIS WS-SX Technical Committee</span></span> |  
  
 <span data-ttu-id="ef812-130">Sürüm 1 olan WCF, Web hizmetleri güvenlik yapılandırması için temel olarak kullanılabilecek 17 kimlik doğrulama modu sağlar.</span><span class="sxs-lookup"><span data-stu-id="ef812-130">WCF, version 1, provides 17 authentication modes that can be used as the basis for Web services security configuration.</span></span> <span data-ttu-id="ef812-131">Her mod, şu gibi yaygın bir dağıtım gereksinimi kümesi için en iyi duruma getirilmiştir:</span><span class="sxs-lookup"><span data-stu-id="ef812-131">Each mode is optimized for a common set of deployment requirements, such as:</span></span>  
  
- <span data-ttu-id="ef812-132">İstemci ve hizmetin kimliğini doğrulamak için kullanılan kimlik bilgileri.</span><span class="sxs-lookup"><span data-stu-id="ef812-132">Credentials used to authenticate client and service.</span></span>  
  
- <span data-ttu-id="ef812-133">İleti veya taşıma güvenlik koruma mekanizmaları.</span><span class="sxs-lookup"><span data-stu-id="ef812-133">Message or transport security protection mechanisms.</span></span>  
  
- <span data-ttu-id="ef812-134">İleti alışverişi desenleri.</span><span class="sxs-lookup"><span data-stu-id="ef812-134">Message exchange patterns.</span></span>  
  
|<span data-ttu-id="ef812-135">Kimlik Doğrulaması Modu</span><span class="sxs-lookup"><span data-stu-id="ef812-135">Authentication Mode</span></span>|<span data-ttu-id="ef812-136">İstemci Kimlik Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="ef812-136">Client Authentication</span></span>|<span data-ttu-id="ef812-137">Sunucu Kimlik Doğrulama</span><span class="sxs-lookup"><span data-stu-id="ef812-137">Server Authentication</span></span>|<span data-ttu-id="ef812-138">Mod</span><span class="sxs-lookup"><span data-stu-id="ef812-138">Mode</span></span>|  
|-------------------------|---------------------------|---------------------------|----------|  
|<span data-ttu-id="ef812-139">Kullanıcı Adı OverTransport</span><span class="sxs-lookup"><span data-stu-id="ef812-139">UserNameOverTransport</span></span>|<span data-ttu-id="ef812-140">Kullanıcı adı/şifre</span><span class="sxs-lookup"><span data-stu-id="ef812-140">User name/password</span></span>|<span data-ttu-id="ef812-141">X509</span><span class="sxs-lookup"><span data-stu-id="ef812-141">X509</span></span>|<span data-ttu-id="ef812-142">Aktarım</span><span class="sxs-lookup"><span data-stu-id="ef812-142">Transport</span></span>|  
|<span data-ttu-id="ef812-143">SertifikaOverTransport</span><span class="sxs-lookup"><span data-stu-id="ef812-143">CertificateOverTransport</span></span>|<span data-ttu-id="ef812-144">X509</span><span class="sxs-lookup"><span data-stu-id="ef812-144">X509</span></span>|<span data-ttu-id="ef812-145">X509</span><span class="sxs-lookup"><span data-stu-id="ef812-145">X509</span></span>|<span data-ttu-id="ef812-146">Aktarım</span><span class="sxs-lookup"><span data-stu-id="ef812-146">Transport</span></span>|  
|<span data-ttu-id="ef812-147">KerberosOverTransport</span><span class="sxs-lookup"><span data-stu-id="ef812-147">KerberosOverTransport</span></span>|<span data-ttu-id="ef812-148">Windows</span><span class="sxs-lookup"><span data-stu-id="ef812-148">Windows</span></span>|<span data-ttu-id="ef812-149">X509</span><span class="sxs-lookup"><span data-stu-id="ef812-149">X509</span></span>|<span data-ttu-id="ef812-150">Aktarım</span><span class="sxs-lookup"><span data-stu-id="ef812-150">Transport</span></span>|  
|<span data-ttu-id="ef812-151">IssuedTokenOverTransport</span><span class="sxs-lookup"><span data-stu-id="ef812-151">IssuedTokenOverTransport</span></span>|<span data-ttu-id="ef812-152">Federe</span><span class="sxs-lookup"><span data-stu-id="ef812-152">Federated</span></span>|<span data-ttu-id="ef812-153">X509</span><span class="sxs-lookup"><span data-stu-id="ef812-153">X509</span></span>|<span data-ttu-id="ef812-154">Aktarım</span><span class="sxs-lookup"><span data-stu-id="ef812-154">Transport</span></span>|  
|<span data-ttu-id="ef812-155">SspiNegotiatedOverTransport</span><span class="sxs-lookup"><span data-stu-id="ef812-155">SspiNegotiatedOverTransport</span></span>|<span data-ttu-id="ef812-156">Windows Sspi Müzakere</span><span class="sxs-lookup"><span data-stu-id="ef812-156">Windows Sspi Negotiated</span></span>|<span data-ttu-id="ef812-157">Windows Sspi Müzakere</span><span class="sxs-lookup"><span data-stu-id="ef812-157">Windows Sspi Negotiated</span></span>|<span data-ttu-id="ef812-158">Aktarım</span><span class="sxs-lookup"><span data-stu-id="ef812-158">Transport</span></span>|  
|<span data-ttu-id="ef812-159">Anonim ForCertificate</span><span class="sxs-lookup"><span data-stu-id="ef812-159">AnonymousForCertificate</span></span>|<span data-ttu-id="ef812-160">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="ef812-160">None</span></span>|<span data-ttu-id="ef812-161">X509</span><span class="sxs-lookup"><span data-stu-id="ef812-161">X509</span></span>|<span data-ttu-id="ef812-162">İleti</span><span class="sxs-lookup"><span data-stu-id="ef812-162">Message</span></span>|  
|<span data-ttu-id="ef812-163">Kullanıcı AdıForCertificate</span><span class="sxs-lookup"><span data-stu-id="ef812-163">UserNameForCertificate</span></span>|<span data-ttu-id="ef812-164">Kullanıcı adı/şifre</span><span class="sxs-lookup"><span data-stu-id="ef812-164">User name/password</span></span>|<span data-ttu-id="ef812-165">X509</span><span class="sxs-lookup"><span data-stu-id="ef812-165">X509</span></span>|<span data-ttu-id="ef812-166">İleti</span><span class="sxs-lookup"><span data-stu-id="ef812-166">Message</span></span>|  
|<span data-ttu-id="ef812-167">MutualCertificate</span><span class="sxs-lookup"><span data-stu-id="ef812-167">MutualCertificate</span></span>|<span data-ttu-id="ef812-168">X509</span><span class="sxs-lookup"><span data-stu-id="ef812-168">X509</span></span>|<span data-ttu-id="ef812-169">X509</span><span class="sxs-lookup"><span data-stu-id="ef812-169">X509</span></span>|<span data-ttu-id="ef812-170">İleti</span><span class="sxs-lookup"><span data-stu-id="ef812-170">Message</span></span>|  
|<span data-ttu-id="ef812-171">MutualCertificateDuplex</span><span class="sxs-lookup"><span data-stu-id="ef812-171">MutualCertificateDuplex</span></span>|<span data-ttu-id="ef812-172">X509</span><span class="sxs-lookup"><span data-stu-id="ef812-172">X509</span></span>|<span data-ttu-id="ef812-173">X509</span><span class="sxs-lookup"><span data-stu-id="ef812-173">X509</span></span>|<span data-ttu-id="ef812-174">İleti</span><span class="sxs-lookup"><span data-stu-id="ef812-174">Message</span></span>|  
|<span data-ttu-id="ef812-175">VerilenTokenForCertificate</span><span class="sxs-lookup"><span data-stu-id="ef812-175">IssuedTokenForCertificate</span></span>|<span data-ttu-id="ef812-176">Federe</span><span class="sxs-lookup"><span data-stu-id="ef812-176">Federated</span></span>|<span data-ttu-id="ef812-177">X509</span><span class="sxs-lookup"><span data-stu-id="ef812-177">X509</span></span>|<span data-ttu-id="ef812-178">İleti</span><span class="sxs-lookup"><span data-stu-id="ef812-178">Message</span></span>|  
|<span data-ttu-id="ef812-179">Kerberos</span><span class="sxs-lookup"><span data-stu-id="ef812-179">Kerberos</span></span>|<span data-ttu-id="ef812-180">Windows</span><span class="sxs-lookup"><span data-stu-id="ef812-180">Windows</span></span>|<span data-ttu-id="ef812-181">Windows</span><span class="sxs-lookup"><span data-stu-id="ef812-181">Windows</span></span>|<span data-ttu-id="ef812-182">İleti</span><span class="sxs-lookup"><span data-stu-id="ef812-182">Message</span></span>|  
|<span data-ttu-id="ef812-183">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="ef812-183">IssuedToken</span></span>|<span data-ttu-id="ef812-184">Federe</span><span class="sxs-lookup"><span data-stu-id="ef812-184">Federated</span></span>|<span data-ttu-id="ef812-185">Federe</span><span class="sxs-lookup"><span data-stu-id="ef812-185">Federated</span></span>|<span data-ttu-id="ef812-186">İleti</span><span class="sxs-lookup"><span data-stu-id="ef812-186">Message</span></span>|  
|<span data-ttu-id="ef812-187">SspiNegotiated</span><span class="sxs-lookup"><span data-stu-id="ef812-187">SspiNegotiated</span></span>|<span data-ttu-id="ef812-188">Windows Sspi Müzakere</span><span class="sxs-lookup"><span data-stu-id="ef812-188">Windows Sspi Negotiated</span></span>|<span data-ttu-id="ef812-189">Windows Sspi Müzakere</span><span class="sxs-lookup"><span data-stu-id="ef812-189">Windows Sspi Negotiated</span></span>|<span data-ttu-id="ef812-190">İleti</span><span class="sxs-lookup"><span data-stu-id="ef812-190">Message</span></span>|  
|<span data-ttu-id="ef812-191">AnonimForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="ef812-191">AnonymousForSslNegotiated</span></span>|<span data-ttu-id="ef812-192">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="ef812-192">None</span></span>|<span data-ttu-id="ef812-193">X509, TLS-Nego</span><span class="sxs-lookup"><span data-stu-id="ef812-193">X509, TLS-Nego</span></span>|<span data-ttu-id="ef812-194">İleti</span><span class="sxs-lookup"><span data-stu-id="ef812-194">Message</span></span>|  
|<span data-ttu-id="ef812-195">Kullanıcı AdıForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="ef812-195">UserNameForSslNegotiated</span></span>|<span data-ttu-id="ef812-196">Kullanıcı adı/şifre</span><span class="sxs-lookup"><span data-stu-id="ef812-196">User name/password</span></span>|<span data-ttu-id="ef812-197">X509, TLS-Nego</span><span class="sxs-lookup"><span data-stu-id="ef812-197">X509, TLS-Nego</span></span>|<span data-ttu-id="ef812-198">İleti</span><span class="sxs-lookup"><span data-stu-id="ef812-198">Message</span></span>|  
|<span data-ttu-id="ef812-199">MutualSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="ef812-199">MutualSslNegotiated</span></span>|<span data-ttu-id="ef812-200">X509</span><span class="sxs-lookup"><span data-stu-id="ef812-200">X509</span></span>|<span data-ttu-id="ef812-201">X509, TLS-Nego</span><span class="sxs-lookup"><span data-stu-id="ef812-201">X509, TLS-Nego</span></span>|<span data-ttu-id="ef812-202">İleti</span><span class="sxs-lookup"><span data-stu-id="ef812-202">Message</span></span>|  
|<span data-ttu-id="ef812-203">IssuedTokenForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="ef812-203">IssuedTokenForSslNegotiated</span></span>|<span data-ttu-id="ef812-204">Federe</span><span class="sxs-lookup"><span data-stu-id="ef812-204">Federated</span></span>|<span data-ttu-id="ef812-205">X509, TLS-Nego</span><span class="sxs-lookup"><span data-stu-id="ef812-205">X509, TLS-Nego</span></span>|<span data-ttu-id="ef812-206">İleti</span><span class="sxs-lookup"><span data-stu-id="ef812-206">Message</span></span>|  
  
 <span data-ttu-id="ef812-207">Bu tür kimlik doğrulama modlarını kullanan uç noktalar, WS-SecurityPolicy (WS-SP) kullanarak güvenlik gereksinimlerini ifade edebilir.</span><span class="sxs-lookup"><span data-stu-id="ef812-207">Endpoints using such authentication modes can express their security requirements using WS-SecurityPolicy (WS-SP).</span></span> <span data-ttu-id="ef812-208">Bu belge, her kimlik doğrulama modu için güvenlik üstbilgive altyapı iletilerinin yapısını açıklar ve ilkeler ve iletiörnekleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="ef812-208">This document describes the structure of security header and infrastructure messages for each authentication mode and provides examples of policies and messages.</span></span>  
  
 <span data-ttu-id="ef812-209">WCF, uygulamalar arasındaki çoklu ileti alışverişini korumak için güvenli oturum desteği sağlamak için WS-SecureConversation'dan yararlanır.</span><span class="sxs-lookup"><span data-stu-id="ef812-209">WCF leverages WS-SecureConversation to provide secure sessions support to protect multi-message exchanges between applications.</span></span>  <span data-ttu-id="ef812-210">Uygulama ayrıntıları için aşağıdaki "Güvenli Oturumlar" adlı bilgiye bakın.</span><span class="sxs-lookup"><span data-stu-id="ef812-210">See "Secure Sessions" below for implementation details.</span></span>  
  
 <span data-ttu-id="ef812-211">Kimlik doğrulama modlarına ek olarak WCF, çoğu ileti güvenliği tabanlı kimlik doğrulama moduna uygulanan yaygın koruma mekanizmalarını denetlemek için ayarlar sağlar( örneğin: imza ve şifreleme işlemleri ne sırayla, algoritma paketleri, anahtar türetme ve imza onayı.</span><span class="sxs-lookup"><span data-stu-id="ef812-211">In addition to authentication modes, WCF provides settings to control common protection mechanisms that apply to most message security-based authentication modes, for example: order of signature versus encryption operations, algorithm suites, key derivation, and signature confirmation.</span></span>  
  
 <span data-ttu-id="ef812-212">Bu belgede aşağıdaki önekler ve ad alanları kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ef812-212">The following prefixes and namespaces are used in this document.</span></span>  
  
|<span data-ttu-id="ef812-213">Ön ek</span><span class="sxs-lookup"><span data-stu-id="ef812-213">Prefix</span></span>|<span data-ttu-id="ef812-214">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="ef812-214">Namespace</span></span>|  
|------------|---------------|  
|<span data-ttu-id="ef812-215">s</span><span class="sxs-lookup"><span data-stu-id="ef812-215">s</span></span>|<http://www.w3.org/2003/05/soap-envelope/>|
|<span data-ttu-id="ef812-216">sp</span><span class="sxs-lookup"><span data-stu-id="ef812-216">sp</span></span>|<http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/>|
|<span data-ttu-id="ef812-217">a</span><span class="sxs-lookup"><span data-stu-id="ef812-217">a</span></span>|<http://www.w3.org/2005/08/addressing>|  
|<span data-ttu-id="ef812-218">wsse</span><span class="sxs-lookup"><span data-stu-id="ef812-218">wsse</span></span>|<span data-ttu-id="ef812-219">TBD - OASIS WSS 1.0 URI</span><span class="sxs-lookup"><span data-stu-id="ef812-219">TBD – OASIS WSS 1.0 URI</span></span>|  
|<span data-ttu-id="ef812-220">wsse11</span><span class="sxs-lookup"><span data-stu-id="ef812-220">wsse11</span></span>|<span data-ttu-id="ef812-221">TBD - OASIS WSS 1.1 URI</span><span class="sxs-lookup"><span data-stu-id="ef812-221">TBD – OASIS WSS 1.1 URI</span></span>|  
|<span data-ttu-id="ef812-222">Wsu</span><span class="sxs-lookup"><span data-stu-id="ef812-222">wsu</span></span>|<span data-ttu-id="ef812-223">TBD - OASIS WSS 1.0 Yardımcı Program URI</span><span class="sxs-lookup"><span data-stu-id="ef812-223">TBD – OASIS WSS 1.0 Utility URI</span></span>|  
|<span data-ttu-id="ef812-224">Ds</span><span class="sxs-lookup"><span data-stu-id="ef812-224">ds</span></span>|<span data-ttu-id="ef812-225">TBD - W3C XMLDSig URI</span><span class="sxs-lookup"><span data-stu-id="ef812-225">TBD – W3C XMLDSig URI</span></span>|  
|<span data-ttu-id="ef812-226">Wst</span><span class="sxs-lookup"><span data-stu-id="ef812-226">wst</span></span>|<span data-ttu-id="ef812-227">TBD - WS-Trust 2005/02 URI</span><span class="sxs-lookup"><span data-stu-id="ef812-227">TBD – WS-Trust 2005/02 URI</span></span>|  
|<span data-ttu-id="ef812-228">wssc</span><span class="sxs-lookup"><span data-stu-id="ef812-228">wssc</span></span>|<span data-ttu-id="ef812-229">TBD - WS-SecureConversation 2005/02 URI</span><span class="sxs-lookup"><span data-stu-id="ef812-229">TBD – WS-SecureConversation 2005/02 URI</span></span>|  
|<span data-ttu-id="ef812-230">testere</span><span class="sxs-lookup"><span data-stu-id="ef812-230">wsaw</span></span>|<span data-ttu-id="ef812-231">TBD - WS adresleme ilkesi ad alanı</span><span class="sxs-lookup"><span data-stu-id="ef812-231">TBD - WS-Addressing policy namespace</span></span>|  
|<span data-ttu-id="ef812-232">wsp</span><span class="sxs-lookup"><span data-stu-id="ef812-232">wsp</span></span>|<http://schemas.xmlsoap.org/ws/2004/09/policy>|  
|<span data-ttu-id="ef812-233">mssp</span><span class="sxs-lookup"><span data-stu-id="ef812-233">mssp</span></span>|<http://schemas.xmlsoap.org/ws/2005/07/securitypolicy>|
  
## <a name="1-token-profiles"></a><span data-ttu-id="ef812-234">1. Belirteç Profilleri</span><span class="sxs-lookup"><span data-stu-id="ef812-234">1. Token Profiles</span></span>  
 <span data-ttu-id="ef812-235">Web Hizmetleri Güvenlik belirtimleri, kimlik bilgileri güvenlik belirteçleri olarak temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ef812-235">Web Services Security specifications represent credential as security tokens.</span></span> <span data-ttu-id="ef812-236">WCF aşağıdaki belirteç türlerini destekler:</span><span class="sxs-lookup"><span data-stu-id="ef812-236">WCF supports the following token types:</span></span>  
  
### <a name="11-usernametoken"></a><span data-ttu-id="ef812-237">1.1 Kullanıcı AdıToken</span><span class="sxs-lookup"><span data-stu-id="ef812-237">1.1 UsernameToken</span></span>  
 <span data-ttu-id="ef812-238">WCF aşağıdaki kısıtlamalar ile UsernameToken10 ve UsernameToken11 profilleri izler:</span><span class="sxs-lookup"><span data-stu-id="ef812-238">WCF follows UsernameToken10 and UsernameToken11 profiles with the following constraints:</span></span>  
  
 <span data-ttu-id="ef812-239">R1101 PasswordType özniteliği Üzerinde UsernameToken\Password öğesi ya atlanmalıdır ya da değeri #PasswordText (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="ef812-239">R1101 PasswordType attribute on UsernameToken\Password element MUST be either omitted or have value #PasswordText (default).</span></span>  
  
 <span data-ttu-id="ef812-240">Bir genişletilebilirlik kullanarak #PasswordDigest uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef812-240">One can implement the #PasswordDigest using extensibility.</span></span> <span data-ttu-id="ef812-241">#PasswordDigest'nin genellikle yeterince güvenli bir parola koruma mekanizması olarak karıştırıldığı gözlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="ef812-241">It has been observed that #PasswordDigest was often mistaken to be a secure enough password protection mechanism.</span></span> <span data-ttu-id="ef812-242">Ancak #PasswordDigest, Kullanıcı Adı Token'in şifrelemesinin yerini tutamaz.</span><span class="sxs-lookup"><span data-stu-id="ef812-242">But #PasswordDigest cannot serve as a substitute for encryption of the UsernameToken.</span></span> <span data-ttu-id="ef812-243">#PasswordDigest birincil amacı tekrar saldırılarına karşı korumadır.</span><span class="sxs-lookup"><span data-stu-id="ef812-243">The primary goal of #PasswordDigest is protection against replay attacks.</span></span> <span data-ttu-id="ef812-244">WCF kimlik doğrulama modlarında, ileti imzaları kullanılarak yeniden oynatma saldırı tehditleri azaltılır.</span><span class="sxs-lookup"><span data-stu-id="ef812-244">In WCF authentication modes, replay attack threats are mitigated by using message signatures.</span></span>  
  
 <span data-ttu-id="ef812-245">B1102 WCF, Kullanıcı adı Token'in Nonce ve Oluşturulan alt öğelerini asla yayar.</span><span class="sxs-lookup"><span data-stu-id="ef812-245">B1102 WCF never emits Nonce and Created sub-elements of the UsernameToken.</span></span>  
  
 <span data-ttu-id="ef812-246">Bu alt öğeler, yeniden algılamaya yardımcı olmak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="ef812-246">These sub-elements are intended to help replay detection.</span></span> <span data-ttu-id="ef812-247">WCF bunun yerine ileti imzalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="ef812-247">WCF uses message signatures instead.</span></span>  
  
 <span data-ttu-id="ef812-248">OASIS WSS SOAP Message Security Kullanıcı AdıToken Profil 1.1 (UsernameToken11) şifre özelliğinden anahtar türetme tanıttı.</span><span class="sxs-lookup"><span data-stu-id="ef812-248">OASIS WSS SOAP Message Security UsernameToken Profile 1.1 (UsernameToken11) introduced key derivation from password feature.</span></span>  
  
 <span data-ttu-id="ef812-249">B1103 Kullanıcı AdıToken şifresi anahtar türetme ve bu nedenle şifreleme işlemleri için kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="ef812-249">B1103 UsernameToken password MUST not be used for key derivation and therefore for cryptographic operations.</span></span>  
  
 <span data-ttu-id="ef812-250">Mantığı: parolalar genellikle şifreleme işlemleri için kullanılmak üzere çok zayıf olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="ef812-250">Rationale: passwords are generally considered too weak to be used for cryptographic operations.</span></span>  
  
### <a name="12-x509-token"></a><span data-ttu-id="ef812-251">1.2 X509 Jeton</span><span class="sxs-lookup"><span data-stu-id="ef812-251">1.2 X509 Token</span></span>  
 <span data-ttu-id="ef812-252">WCF, X509v3 sertifikalarını kimlik bilgisi türü olarak destekler ve X509TokenProfile1.0 ve X509TokenProfile1.1'i aşağıdaki kısıtlamalarla izler:</span><span class="sxs-lookup"><span data-stu-id="ef812-252">WCF supports X509v3 certificates as a credential type and follows X509TokenProfile1.0 and X509TokenProfile1.1 with the following constraints:</span></span>  
  
 <span data-ttu-id="ef812-253">R1201 BinarySecurityToken öğesindeki ValueType özniteliği, X509v3 sertifikası içerdiğinde değer #X509v3 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ef812-253">R1201 The ValueType attribute on the BinarySecurityToken element must have value #X509v3 when it contains an X509v3 certificate.</span></span>  
  
 <span data-ttu-id="ef812-254">WSS X509 Belirteç Profili 1.0 ve 1.1 de #X509PKIPathv1 tanımlar ve #PKCS7 değer türleri olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ef812-254">WSS X509 Token Profile 1.0 and 1.1 define also #X509PKIPathv1 and #PKCS7 as value types.</span></span> <span data-ttu-id="ef812-255">WCF bu türleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="ef812-255">WCF does not support these types.</span></span>  
  
 <span data-ttu-id="ef812-256">R1202 X509 sertifikasında SubjectKeyIdentifier (SKI) uzantısı varsa, wsSE:KeyIdentifier belirteci için dış başvurular için, ValueType özniteliği #X509SubjectKeyIdentifier ve içeriği sertifikanın SKI uzantısının temel 64 kodlanmış değeri ile birlikte kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ef812-256">R1202 If a SubjectKeyIdentifier (SKI) extension is present in an X509 certificate, wsse:KeyIdentifier should be used for external references to the token, with the ValueType attribute as #X509SubjectKeyIdentifier and its content the base64-encoded value of certificate's SKI extension.</span></span>  
  
 <span data-ttu-id="ef812-257">İsKİ referansları yaygın olarak uygulanmakta ve son derece birlikte çalışabilir bir dış referans türü olduğu kanıtlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="ef812-257">SKI references are widely implemented and proven to be a highly interoperable external reference type.</span></span>  
  
 <span data-ttu-id="ef812-258">R1203 X509 Güvenlik Jetonuna harici bir başvuru ds:X509IssuerSerial kullanmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="ef812-258">R1203 An external Reference to X509 Security Token SHOULD NOT use ds:X509IssuerSerial.</span></span>  
  
 <span data-ttu-id="ef812-259">R1204 X509TokenProfile1.1 kullanılıyorsa, X509 Güvenlik Belirteci'ne harici bir başvuru WS-Security 1.1 tarafından tanıtılan parmak izini kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ef812-259">R1204 If X509TokenProfile1.1 is in use, an external reference to X509 Security Token SHOULD use the thumbprint introduced by WS-Security 1.1.</span></span>  
  
 <span data-ttu-id="ef812-260">WCF X509IssuerSerial destekler.</span><span class="sxs-lookup"><span data-stu-id="ef812-260">WCF supports X509IssuerSerial.</span></span> <span data-ttu-id="ef812-261">Ancak X509IssuerSerial ile birlikte çalışabilirlik sorunları vardır: WCF X509IssuerSerial iki değerleri karşılaştırmak için bir dize kullanır.</span><span class="sxs-lookup"><span data-stu-id="ef812-261">However There are interoperability issues with X509IssuerSerial: WCF uses a string to compare two values of X509IssuerSerial.</span></span> <span data-ttu-id="ef812-262">Bu nedenle, bir kişi Konu Adı'nın bileşenlerini yeniden sipariş ederse ve bir WCF hizmetine bir sertifikareferansı gönderirse, bu belge bulunamayabilir.</span><span class="sxs-lookup"><span data-stu-id="ef812-262">Therefore if one reorders components of the Subject Name and sends to an WCF service a reference to a certificate, it may not be found.</span></span>  
  
### <a name="13-kerberos-token"></a><span data-ttu-id="ef812-263">1.3 Kerberos Jetonu</span><span class="sxs-lookup"><span data-stu-id="ef812-263">1.3 Kerberos Token</span></span>  
 <span data-ttu-id="ef812-264">WCF, Windows kimlik doğrulaması amacıyla Aşağıdaki kısıtlamalarla KerberosTokenProfile1.1'i destekler:</span><span class="sxs-lookup"><span data-stu-id="ef812-264">WCF supports KerberosTokenProfile1.1 for the purpose of Windows authentication with the following constraints:</span></span>  
  
 <span data-ttu-id="ef812-265">R1301 A Kerberos Belirteci, GSS_API ve Kerberos belirtiminde tanımlandığı gibi GSS sarılmış Kerberos v4 AP_REQ değerini taşımalı ve #GSS_Kerberosv5_AP_REQ değerine sahip ValueType özelliğine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ef812-265">R1301 A Kerberos Token must carry the value of a GSS wrapped Kerberos v4 AP_REQ as defined in GSS_API and the Kerberos specification, and must have the ValueType attribute with the value #GSS_Kerberosv5_AP_REQ.</span></span>  
  
 <span data-ttu-id="ef812-266">WCF GSS sarılmış Kerberos AP-REQ değil, çıplak BIR AP-REQ kullanır.</span><span class="sxs-lookup"><span data-stu-id="ef812-266">WCF uses GSS wrapped Kerberos AP-REQ, not a bare AP-REQ.</span></span> <span data-ttu-id="ef812-267">Bu bir güvenlik en iyi uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="ef812-267">This is a security best practice.</span></span>  
  
### <a name="14-saml-v11-token"></a><span data-ttu-id="ef812-268">1.4 SAML v1.1 Belirteci</span><span class="sxs-lookup"><span data-stu-id="ef812-268">1.4 SAML v1.1 Token</span></span>  
 <span data-ttu-id="ef812-269">WCF, SAML v1.1 belirteçleri için WSS SAML Token profilleri 1.0 ve 1.1'i destekler.</span><span class="sxs-lookup"><span data-stu-id="ef812-269">WCF supports WSS SAML Token profiles 1.0 and 1.1 for SAML v1.1 tokens.</span></span> <span data-ttu-id="ef812-270">SAML belirteç biçimlerinin diğer sürümlerini uygulamak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="ef812-270">It is possible to implement other versions of SAML token formats.</span></span>  
  
### <a name="15-security-context-token"></a><span data-ttu-id="ef812-271">1.5 Güvenlik Bağlam ı belirteç</span><span class="sxs-lookup"><span data-stu-id="ef812-271">1.5 Security Context Token</span></span>  
 <span data-ttu-id="ef812-272">WCF, WS-SecureConversation'da tanıtılan Güvenlik Bağlamı Belirteci'ni (SCT) destekler.</span><span class="sxs-lookup"><span data-stu-id="ef812-272">WCF supports the Security Context Token (SCT) introduced in WS-SecureConversation.</span></span> <span data-ttu-id="ef812-273">SCT, SecureConversation'da kurulan bir güvenlik bağlamını ve aşağıda açıklanan ikili müzakere protokollerini TLS ve SSPI'yi temsil etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ef812-273">SCT is used to represent a security context established in SecureConversation as well as the binary negotiation protocols TLS and SSPI, described below.</span></span>  
  
## <a name="2-common-message-security-parameters"></a><span data-ttu-id="ef812-274">2. Ortak İleti Güvenlik Parametreleri</span><span class="sxs-lookup"><span data-stu-id="ef812-274">2. Common Message Security Parameters</span></span>  
  
### <a name="21-timestamp"></a><span data-ttu-id="ef812-275">2.1 Zaman Damgası</span><span class="sxs-lookup"><span data-stu-id="ef812-275">2.1 TimeStamp</span></span>  
 <span data-ttu-id="ef812-276">Zaman damgası varlığı <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> <xref:System.ServiceModel.Channels.SecurityBindingElement> sınıfın özelliği kullanılarak denetlenir.</span><span class="sxs-lookup"><span data-stu-id="ef812-276">Timestamp presence is controlled using the <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> property of the <xref:System.ServiceModel.Channels.SecurityBindingElement> class.</span></span> <span data-ttu-id="ef812-277">WCF her zaman wsse:TimeStamp ile wsse:Created ve wsse:Expires alanları ile serihale eder.</span><span class="sxs-lookup"><span data-stu-id="ef812-277">WCF always serializes wsse:TimeStamp with wsse:Created and wsse:Expires fields.</span></span> <span data-ttu-id="ef812-278">WsSe:TimeStamp imzalandığında her zaman imzalanır.</span><span class="sxs-lookup"><span data-stu-id="ef812-278">The wsse:TimeStamp is always signed when signing is used.</span></span>  
  
### <a name="22-protection-order"></a><span data-ttu-id="ef812-279">2.2 Koruma Emri</span><span class="sxs-lookup"><span data-stu-id="ef812-279">2.2 Protection Order</span></span>  
 <span data-ttu-id="ef812-280">WCF, "Şifrelemeden Önce İmzala" ve "İmzadan Önce Şifreleme" ileti koruma emrini destekler (Güvenlik İlkesi 1.1).</span><span class="sxs-lookup"><span data-stu-id="ef812-280">WCF supports the message protection order "Sign Before Encrypt" and "Encrypt Before Sign" (Security Policy 1.1).</span></span> <span data-ttu-id="ef812-281">"Şifrelemeden Önce İmzala" gibi nedenlerle önerilir: WS-Security 1.1 SignatureConfirmation mekanizması kullanılmadığı ve şifreli içeriğe yönelik imza denetimi zorlaştırmadığı sürece İmzadan Önce Şifrele ile korunan iletiler imza ikame saldırılarına açıktır.</span><span class="sxs-lookup"><span data-stu-id="ef812-281">"Sign Before Encrypt" is recommended for reasons including: messages protected with Encrypt Before Sign are open to signature substitution attacks unless the WS-Security 1.1 SignatureConfirmation mechanism is used, and a signature over encrypted content makes auditing harder.</span></span>  
  
### <a name="23-signature-protection"></a><span data-ttu-id="ef812-282">2.3 İmza Koruması</span><span class="sxs-lookup"><span data-stu-id="ef812-282">2.3 Signature Protection</span></span>  
 <span data-ttu-id="ef812-283">İşaretten Önce Şifrele kullanıldığında, şifrelenmiş içeriği veya imzalama anahtarını tahmin etmek için kaba kuvvet saldırılarını önlemek için imzanın korunması önerilir (özellikle zayıf anahtar malzemesiyle özel bir belirteç kullanıldığında).</span><span class="sxs-lookup"><span data-stu-id="ef812-283">When Encrypt Before Sign is used, it is recommended to protect the signature to prevent brute force attacks for guessing the encrypted content or the signing key (especially when a custom token is used with weak key material).</span></span>  
  
### <a name="24-algorithm-suite"></a><span data-ttu-id="ef812-284">2.4 Algoritma Paketi</span><span class="sxs-lookup"><span data-stu-id="ef812-284">2.4 Algorithm Suite</span></span>  
 <span data-ttu-id="ef812-285">WCF, Security Policy 1.1'de listelenen tüm algoritma paketlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="ef812-285">WCF supports all algorithm suites listed in Security Policy 1.1.</span></span>  
  
### <a name="25-key-derivation"></a><span data-ttu-id="ef812-286">2.5 Anahtar Türetme</span><span class="sxs-lookup"><span data-stu-id="ef812-286">2.5 Key Derivation</span></span>  
 <span data-ttu-id="ef812-287">WCF, WS-SecureConversation'da açıklandığı gibi "Simetrik tuşlar için Anahtar Türetme"yi kullanır.</span><span class="sxs-lookup"><span data-stu-id="ef812-287">WCF uses "Key Derivation for symmetric keys" as described in WS-SecureConversation.</span></span>  
  
### <a name="26-signature-confirmation"></a><span data-ttu-id="ef812-288">2.6 İmza Onayı</span><span class="sxs-lookup"><span data-stu-id="ef812-288">2.6 Signature Confirmation</span></span>  
 <span data-ttu-id="ef812-289">İmza onayı, imza kümesini korumak için aracı insan saldırılarına karşı koruma olarak olabilir.</span><span class="sxs-lookup"><span data-stu-id="ef812-289">Signature confirmation can be as protection from middle man attacks to protect the set of signatures.</span></span>  
  
### <a name="27-security-header-layout"></a><span data-ttu-id="ef812-290">2.7 Güvenlik Üstbilgi Düzeni</span><span class="sxs-lookup"><span data-stu-id="ef812-290">2.7 Security Header Layout</span></span>  
 <span data-ttu-id="ef812-291">Her kimlik doğrulama modu, güvenlik üstbilgisi için belirli bir düzeni açıklar.</span><span class="sxs-lookup"><span data-stu-id="ef812-291">Each authentication mode describes a certain layout for the security header.</span></span> <span data-ttu-id="ef812-292">Güvenlik üstbilgisindeki öğeler yarı sıralıdır.</span><span class="sxs-lookup"><span data-stu-id="ef812-292">Elements within the security header are semi-ordered.</span></span> <span data-ttu-id="ef812-293">WS-Security İlkesi, güvenlik üstbilgi alt öğelerinin sırasını tanımlamak için aşağıdaki güvenlik üstbilgi düzeni modlarını tanımlar:</span><span class="sxs-lookup"><span data-stu-id="ef812-293">To define the order of security header child elements, WS-Security Policy defines the following security header layout modes:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ef812-294">Katı</span><span class="sxs-lookup"><span data-stu-id="ef812-294">Strict</span></span>|<span data-ttu-id="ef812-295">Öğeler, "kullanmadan önce bildir" ilkesine göre Güvenlik Politikası bölüm 7.7.1'de açıklanan numaralı düzen kurallarını izleyerek güvenlik üstbilgisine eklenir.</span><span class="sxs-lookup"><span data-stu-id="ef812-295">Items are added to the security header following the numbered layout rules described in Security Policy section 7.7.1 according to a general principle of "declare before use".</span></span>|  
|<span data-ttu-id="ef812-296">Lax</span><span class="sxs-lookup"><span data-stu-id="ef812-296">Lax</span></span>|<span data-ttu-id="ef812-297">Öğeler WSS: SOAP Message Security uygun herhangi bir sırada güvenlik üstbilgi eklenir.</span><span class="sxs-lookup"><span data-stu-id="ef812-297">Items are added to the security header in any order that conforms to WSS: SOAP Message Security.</span></span>|  
|<span data-ttu-id="ef812-298">LaxTimestampİlk</span><span class="sxs-lookup"><span data-stu-id="ef812-298">LaxTimestampFirst</span></span>|<span data-ttu-id="ef812-299">Güvenlik üstbilgisindeki ilk öğenin wsse olması dışında Lax ile aynıdır:Zaman damgası</span><span class="sxs-lookup"><span data-stu-id="ef812-299">Same as Lax except that the first item in the security header must be a wsse:Timestamp</span></span>|  
|<span data-ttu-id="ef812-300">LaxTimestampLast</span><span class="sxs-lookup"><span data-stu-id="ef812-300">LaxTimestampLast</span></span>|<span data-ttu-id="ef812-301">Güvenlik üstbilgisindeki son öğenin bir wsse olması dışında gevşek olarak aynıdır:Zaman damgası</span><span class="sxs-lookup"><span data-stu-id="ef812-301">Same as lax except that the last item in the security header must be a wsse:Timestamp</span></span>|  
  
 <span data-ttu-id="ef812-302">WCF, güvenlik üstbilgi düzeni için dört modu da destekler.</span><span class="sxs-lookup"><span data-stu-id="ef812-302">WCF supports all four modes for security header layout.</span></span> <span data-ttu-id="ef812-303">Aşağıdaki kimlik doğrulama modları için güvenlik üstbilgi yapısı ve ileti örnekleri "Katı" modunu izleyin.</span><span class="sxs-lookup"><span data-stu-id="ef812-303">Security header structure and message examples for authentication modes below follow the "Strict" mode.</span></span>  
  
## <a name="2-common-message-security-parameters"></a><span data-ttu-id="ef812-304">2. Ortak İleti Güvenlik Parametreleri</span><span class="sxs-lookup"><span data-stu-id="ef812-304">2. Common Message Security Parameters</span></span>  
 <span data-ttu-id="ef812-305">Bu bölümde, istemci ve hizmet tarafından değiştirilen iletilerde güvenlik üstbilgi yapısını gösteren örneklerle birlikte her kimlik doğrulama modu için örnek ilkeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="ef812-305">This section provides example policies for each authentication mode along with examples showing security header structure in messages exchanged by client and service.</span></span>  
  
### <a name="61-transport-protection"></a><span data-ttu-id="ef812-306">6.1 Taşıma Koruması</span><span class="sxs-lookup"><span data-stu-id="ef812-306">6.1 Transport Protection</span></span>  
 <span data-ttu-id="ef812-307">WCF, iletileri korumak için güvenli aktarım kullanan beş kimlik doğrulama modu sağlar; UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport ve SspiNegotiatedOverTransport.</span><span class="sxs-lookup"><span data-stu-id="ef812-307">WCF provides five authentication modes that use secure transport to protect messages; UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport and SspiNegotiatedOverTransport.</span></span>  
  
 <span data-ttu-id="ef812-308">Bu kimlik doğrulama modları SecurityPolicy'de açıklanan aktarım bağlama kullanılarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ef812-308">These authentication modes are constructed using the transport binding described in SecurityPolicy.</span></span> <span data-ttu-id="ef812-309">UserNameOverTransport kimlik doğrulama modu için UsernameToken imzalı destekleyici bir belirteçtir.</span><span class="sxs-lookup"><span data-stu-id="ef812-309">For the UserNameOverTransport authentication mode the UsernameToken is a signed supporting token.</span></span> <span data-ttu-id="ef812-310">Diğer kimlik doğrulama modları için belirteç imzalı bir onaylama belirteci olarak görünür.</span><span class="sxs-lookup"><span data-stu-id="ef812-310">For the other authentication modes the token appears as a signed endorsing token.</span></span> <span data-ttu-id="ef812-311">SecurityPolicy'nin Ek C.1.2 ve C.1.3 güvenlik üstbilgi düzenini ayrıntılı olarak açıklar.</span><span class="sxs-lookup"><span data-stu-id="ef812-311">Appendix C.1.2 and C.1.3 of SecurityPolicy describe the security header layout in detail.</span></span> <span data-ttu-id="ef812-312">Aşağıdaki örnek güvenlik üstbilgisi, belirli bir kimlik doğrulama modu için Sıkı düzeni gösterir.</span><span class="sxs-lookup"><span data-stu-id="ef812-312">The following example security headers show the Strict layout for a given authentication mode.</span></span>  
  
 <span data-ttu-id="ef812-313">Tüm durumlarda belirteçler için "Türemiş Anahtarlar" özelliğinin değeri "yanlış"tır.</span><span class="sxs-lookup"><span data-stu-id="ef812-313">The value of the "Derived Keys" property for the tokens in all cases is "false".</span></span>  
  
 <span data-ttu-id="ef812-314">Aktarım bağlamanın çeşitli özelliklerinin değerleri aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="ef812-314">The values of the various properties of the transport binding are as follows:</span></span>  
  
 <span data-ttu-id="ef812-315">Zaman damgası: doğru</span><span class="sxs-lookup"><span data-stu-id="ef812-315">Timestamp: true</span></span>  
  
 <span data-ttu-id="ef812-316">Güvenlik Üstbilgi Düzeni: Katı</span><span class="sxs-lookup"><span data-stu-id="ef812-316">Security Header Layout: Strict</span></span>  
  
 <span data-ttu-id="ef812-317">Algoritma Paketi: Basic256</span><span class="sxs-lookup"><span data-stu-id="ef812-317">Algorithm Suite: Basic256</span></span>  
  
#### <a name="611-usernameovertransport"></a><span data-ttu-id="ef812-318">6.1.1 Kullanıcı AdıOverTransport</span><span class="sxs-lookup"><span data-stu-id="ef812-318">6.1.1 UsernameOverTransport</span></span>  
 <span data-ttu-id="ef812-319">Bu kimlik doğrulama moduyla istemci, SOAP katmanında her zaman başlatıcıdan alıcıya gönderilen imzalı destekleyici bir belirteç olarak görünen bir Kullanıcı Adı Belirteci ile kimlik doğrulaması verir.</span><span class="sxs-lookup"><span data-stu-id="ef812-319">With this authentication mode, the client authenticates with a Username Token which appears at the SOAP layer as a signed supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="ef812-320">Hizmet, aktarım katmanında x.509 sertifikası kullanılarak doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="ef812-320">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="ef812-321">Kullanılan bağlama bir aktarım bağlayıcısidır.</span><span class="sxs-lookup"><span data-stu-id="ef812-321">The binding used is a transport binding.</span></span>  
  
 <span data-ttu-id="ef812-322">İlke</span><span class="sxs-lookup"><span data-stu-id="ef812-322">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='UsernameOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding >  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
              <sp:HttpsToken RequireClientCertificate='false' />
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:SignedSupportingTokens >  
        <wsp:Policy>  
          <sp:UsernameToken
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
            <wsp:Policy>  
              <sp:WssUsernameToken10 />
            </wsp:Policy>  
          </sp:UsernameToken>  
        </wsp:Policy>  
      </sp:SignedSupportingTokens>  
      <sp:Wss11 >  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
          <sp:MustSupportRefThumbprint />
          <sp:MustSupportRefEncryptedKey />
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10 >  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 <span data-ttu-id="ef812-323">Güvenlik Üstbilgi Düzeni</span><span class="sxs-lookup"><span data-stu-id="ef812-323">Security Header Layout</span></span>  
  
 <span data-ttu-id="ef812-324">İstek</span><span class="sxs-lookup"><span data-stu-id="ef812-324">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:UsernameToken>  
  ...  
  </wsse:UsernameToken>  
</wsse:Security>  
```  
  
 <span data-ttu-id="ef812-325">Yanıt</span><span class="sxs-lookup"><span data-stu-id="ef812-325">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="612-certificateovertransport"></a><span data-ttu-id="ef812-326">6.1.2 Taşıma Fazla Taşıma Sertifikası</span><span class="sxs-lookup"><span data-stu-id="ef812-326">6.1.2 CertificateOverTransport</span></span>  
 <span data-ttu-id="ef812-327">Bu kimlik doğrulama modu ile istemci, SOAP katmanında her zaman başlatıcıdan alıcıya gönderilen destekleyici bir belirteç olarak görünen bir X.509 sertifikası kullanarak kimlik doğrulaması verir.</span><span class="sxs-lookup"><span data-stu-id="ef812-327">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as an endorsing supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="ef812-328">Hizmet, aktarım katmanında x.509 sertifikası kullanılarak doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="ef812-328">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="ef812-329">Kullanılan bağlama bir aktarım bağlayıcısidır.</span><span class="sxs-lookup"><span data-stu-id="ef812-329">The binding used is a transport binding.</span></span>  
  
 <span data-ttu-id="ef812-330">İlke</span><span class="sxs-lookup"><span data-stu-id="ef812-330">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='CertificateOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding xmlns:sp='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy' >  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
             <sp:HttpsToken RequireClientCertificate='false' />
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:EndorsingSupportingTokens>  
        <wsp:Policy>  
          <sp:X509Token
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
            <wsp:Policy>  
              <sp:RequireThumbprintReference />
              <sp:WssX509V3Token10 />
            </wsp:Policy>  
          </sp:X509Token>  
          <sp:SignedParts>  
            <sp:Header Name='To'
Namespace='http://www.w3.org/2005/08/addressing' />
          </sp:SignedParts>  
        </wsp:Policy>  
      </sp:EndorsingSupportingTokens>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
          <sp:MustSupportRefThumbprint />
          <sp:MustSupportRefEncryptedKey />
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 <span data-ttu-id="ef812-331">Güvenlik Üstbilgi Düzeni</span><span class="sxs-lookup"><span data-stu-id="ef812-331">Security Header Layout</span></span>  
  
 <span data-ttu-id="ef812-332">İstek</span><span class="sxs-lookup"><span data-stu-id="ef812-332">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wse:Timestamp u:Id="_0">  
  ...  
  </wse:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
</wsse:Security>  
```  
  
 <span data-ttu-id="ef812-333">Yanıt</span><span class="sxs-lookup"><span data-stu-id="ef812-333">Response</span></span>  
  
```xml  
<o:Security>  
  <u:Timestamp u:Id="_0">  
  ...  
  </u:Timestamp>  
</o:Security>  
```  
  
#### <a name="613-issuedtokenovertransport"></a><span data-ttu-id="ef812-334">6.1.3 IssuedTokenOverTransport</span><span class="sxs-lookup"><span data-stu-id="ef812-334">6.1.3 IssuedTokenOverTransport</span></span>  
 <span data-ttu-id="ef812-335">Bu kimlik doğrulama modu ile istemci hizmete doğrudoğrulama yapmaz, ancak daha çok bir Güvenlik Belirteç Hizmeti (STS) tarafından verilen bir belirteç sunar ve paylaşılan bir anahtar bilgisini kanıtlıyor.</span><span class="sxs-lookup"><span data-stu-id="ef812-335">With this authentication mode the client does not authenticate to the service, as such, but rather presents a token issued by a Security Token Service (STS) and proves knowledge of a shared key.</span></span> <span data-ttu-id="ef812-336">Verilen belirteç, SABUN katmanında her zaman başlatıcıdan alıcıya gönderilen destekleyici bir belirteç olarak görünür.</span><span class="sxs-lookup"><span data-stu-id="ef812-336">The issued token appears at the SOAP layer as an endorsing supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="ef812-337">Hizmet, aktarım katmanında x.509 sertifikası kullanılarak doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="ef812-337">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="ef812-338">Bağlama bir aktarım bağlayıcısidır.</span><span class="sxs-lookup"><span data-stu-id="ef812-338">The binding is a transport binding.</span></span>  
  
 <span data-ttu-id="ef812-339">İlke</span><span class="sxs-lookup"><span data-stu-id="ef812-339">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='IssuedTokenOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding >  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
              <sp:HttpsToken RequireClientCertificate='false' />
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:EndorsingSupportingTokens>  
        <wsp:Policy>  
          <sp:IssuedToken
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
            <sp:RequestSecurityTokenTemplate>  
              <wst:KeyType>  
              http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey  
              </wst:KeyType>
            </sp:RequestSecurityTokenTemplate>  
            <wsp:Policy>  
              <sp:RequireInternalReference />
            </wsp:Policy>  
          </sp:IssuedToken>  
          <sp:SignedParts>  
            <sp:Header Name='To'
Namespace='http://www.w3.org/2005/08/addressing' />
          </sp:SignedParts>  
        </wsp:Policy>  
      </sp:EndorsingSupportingTokens>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
          <sp:MustSupportRefThumbprint />
          <sp:MustSupportRefEncryptedKey />
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 <span data-ttu-id="ef812-340">Güvenlik Üstbilgi Düzeni</span><span class="sxs-lookup"><span data-stu-id="ef812-340">Security Header Layout</span></span>  
  
 <span data-ttu-id="ef812-341">İstek</span><span class="sxs-lookup"><span data-stu-id="ef812-341">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1" >  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
</wsse:Security>  
```  
  
 <span data-ttu-id="ef812-342">Yanıt</span><span class="sxs-lookup"><span data-stu-id="ef812-342">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="614-kerberosovertransport"></a><span data-ttu-id="ef812-343">6.1.4 KerberosOverTransport</span><span class="sxs-lookup"><span data-stu-id="ef812-343">6.1.4 KerberosOverTransport</span></span>  
 <span data-ttu-id="ef812-344">Bu kimlik doğrulama modu ile istemci bir Kerberos bileti kullanarak hizmete kimlik doğrular.</span><span class="sxs-lookup"><span data-stu-id="ef812-344">With this authentication mode the client authenticates to the service using a Kerberos ticket.</span></span> <span data-ttu-id="ef812-345">Kerberos belirteci SOAP katmanında destekleyici bir belirteç olarak görünür.</span><span class="sxs-lookup"><span data-stu-id="ef812-345">The Kerberos token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="ef812-346">Hizmet, aktarım katmanında x.509 sertifikası kullanılarak doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="ef812-346">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="ef812-347">Bağlama bir aktarım bağlayıcısidır.</span><span class="sxs-lookup"><span data-stu-id="ef812-347">The binding is a transport binding.</span></span>  
  
 <span data-ttu-id="ef812-348">İlke</span><span class="sxs-lookup"><span data-stu-id="ef812-348">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='KerberosOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding>  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
              <sp:HttpsToken RequireClientCertificate='false' />
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic128 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:EndorsingSupportingTokens>  
        <wsp:Policy>  
          <sp:KerberosToken  
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/Once' >  
            <wsp:Policy>  
              <sp:WssGssKerberosV5ApReqToken11 />
            </wsp:Policy>  
          </sp:KerberosToken>  
          <sp:SignedParts>  
            <sp:Header Name='To'
Namespace='http://www.w3.org/2005/08/addressing' />
          </sp:SignedParts>  
        </wsp:Policy>  
      </sp:EndorsingSupportingTokens>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
          <sp:MustSupportRefThumbprint />
          <sp:MustSupportRefEncryptedKey />
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 <span data-ttu-id="ef812-349">Güvenlik Üstbilgi Düzeni</span><span class="sxs-lookup"><span data-stu-id="ef812-349">Security Header Layout</span></span>  
  
 <span data-ttu-id="ef812-350">İstek</span><span class="sxs-lookup"><span data-stu-id="ef812-350">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1" >  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken ValueType="...#GSS_Kerberosv5_AP_REQ">  
  ...  
  </wsse:BinarySecurityToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
</wsse:Security>  
```  
  
 <span data-ttu-id="ef812-351">Yanıt</span><span class="sxs-lookup"><span data-stu-id="ef812-351">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="615-sspinegotiatedovertransport"></a><span data-ttu-id="ef812-352">6.1.5 SspiNegotiatedOverTransport</span><span class="sxs-lookup"><span data-stu-id="ef812-352">6.1.5 SspiNegotiatedOverTransport</span></span>  
 <span data-ttu-id="ef812-353">Bu modda istemci ve sunucu kimlik doğrulaması gerçekleştirmek için bir anlaşma protokolü kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ef812-353">With this mode a negotiation protocol is used to perform client and server authentication.</span></span> <span data-ttu-id="ef812-354">Kerberos mümkünse kullanılır, aksi takdirde NTLM.</span><span class="sxs-lookup"><span data-stu-id="ef812-354">Kerberos is used if possible, otherwise NTLM.</span></span> <span data-ttu-id="ef812-355">Elde edilen Ct, SOAP katmanında her zaman başlatıcıdan alıcıya gönderilen destekleyici bir belirteç olarak görünür.</span><span class="sxs-lookup"><span data-stu-id="ef812-355">The resulting SCT appears at the SOAP layer as an endorsing supporting token that is always sent from initiator to recipient.</span></span> <span data-ttu-id="ef812-356">Hizmet ayrıca taşıma katmanında X.509 sertifikası ile doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="ef812-356">The service is additionally authenticated at the transport layer by an X.509 certificate.</span></span> <span data-ttu-id="ef812-357">Kullanılan bağlama bir aktarım bağlayıcısidır.</span><span class="sxs-lookup"><span data-stu-id="ef812-357">The binding used is a transport binding.</span></span> <span data-ttu-id="ef812-358">"SPNEGO" (müzakere) WCF WS-Trust ile SSPI ikili müzakere protokolü nasıl kullandığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="ef812-358">"SPNEGO" (negotiation) describes how WCF uses SSPI binary negotiation protocol with WS-Trust.</span></span> <span data-ttu-id="ef812-359">Bu bölümdeki güvenlik üstbilgi örnekleri, SPNEGO el sıkışması yoluyla SCT kurulduktan sonra dır.</span><span class="sxs-lookup"><span data-stu-id="ef812-359">Security header examples in this section are after the SCT has been established through the SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="ef812-360">İlke</span><span class="sxs-lookup"><span data-stu-id="ef812-360">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='SspiNegotiatedOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding>  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
              <sp:HttpsToken RequireClientCertificate='false' />
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:EndorsingSupportingTokens>  
        <wsp:Policy>  
          <sp:SpnegoContextToken
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
            <wsp:Policy />
          </sp:SpnegoContextToken>  
          <sp:SignedParts>  
            <sp:Header Name='To'
Namespace='http://www.w3.org/2005/08/addressing' />
          </sp:SignedParts>  
        </wsp:Policy>  
      </sp:EndorsingSupportingTokens>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
          <sp:MustSupportRefThumbprint />
          <sp:MustSupportRefEncryptedKey />
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples"></a><span data-ttu-id="ef812-361">Güvenlik Üstbilgi Örnekleri</span><span class="sxs-lookup"><span data-stu-id="ef812-361">Security Header Examples</span></span>  
 <span data-ttu-id="ef812-362">Güvenlik Bağlam ıken WS-Trust İkili Müzakere kullanarak SPNEGO el sıkışma yoluyla kurulduktan sonra, uygulama iletileri aşağıdaki yapıya sahip güvenlik başlıkları var.</span><span class="sxs-lookup"><span data-stu-id="ef812-362">Once the Security Context Token is established through SPNEGO handshake using WS-Trust Binary Negotiation, the application messages have security headers with the following structure.</span></span>  
  
 <span data-ttu-id="ef812-363">İstek</span><span class="sxs-lookup"><span data-stu-id="ef812-363">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:SecurityContextToken u:Id="uuid-2202746a-7725-453d-8747-809cb718dab0-29" >  
  ...  
  </wssc:SecurityContextToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
</wsse:Security>  
```  
  
 <span data-ttu-id="ef812-364">Yanıt</span><span class="sxs-lookup"><span data-stu-id="ef812-364">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
### <a name="62-using-x509-certificates-for-service-authentication"></a><span data-ttu-id="ef812-365">6.2 Hizmet Kimlik Doğrulaması için X.509 Sertifikalarının Kullanılması</span><span class="sxs-lookup"><span data-stu-id="ef812-365">6.2 Using X.509 Certificates for Service Authentication</span></span>  
 <span data-ttu-id="ef812-366">Bu bölümde aşağıdaki kimlik doğrulama modları açıklanmaktadır: MutualCertificate WSS1.0, Mutual CertificateDuplex, MutualCertificate WSS1.1, AnonymousForCertificate, UserNameForCertificate ve IssuedTokenForCertificate.</span><span class="sxs-lookup"><span data-stu-id="ef812-366">This section describes the following authentication modes: MutualCertificate WSS1.0, Mutual CertificateDuplex, MutualCertificate WSS1.1, AnonymousForCertificate, UserNameForCertificate and IssuedTokenForCertificate.</span></span>  
  
#### <a name="621-mutualcertificate-wss10"></a><span data-ttu-id="ef812-367">6.2.1 Karşılıklı Sertifika WSS1.0</span><span class="sxs-lookup"><span data-stu-id="ef812-367">6.2.1 MutualCertificate WSS1.0</span></span>  
 <span data-ttu-id="ef812-368">Bu kimlik doğrulama modu ile istemci, SOAP katmanında başlatıcı belirteci olarak görünen bir X.509 sertifikası kullanarak kimlik doğrulaması verir.</span><span class="sxs-lookup"><span data-stu-id="ef812-368">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as the initiator token.</span></span> <span data-ttu-id="ef812-369">Hizmet ayrıca X.509 sertifikası kullanılarak da doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="ef812-369">The service is also authenticated using an X.509 certificate.</span></span>  
  
 <span data-ttu-id="ef812-370">Kullanılan bağlama, aşağıdaki özellik değerleriyle asimetrik bir bağlamadır:</span><span class="sxs-lookup"><span data-stu-id="ef812-370">The binding used is an asymmetric binding with the following property values:</span></span>  
  
 <span data-ttu-id="ef812-371">Başlatıcı Belirteci: istemcinin X.509 sertifikası, dahil etme modu .../IncludeToken/AlwaysToRecipient olarak ayarlanmış</span><span class="sxs-lookup"><span data-stu-id="ef812-371">Initiator Token: the client’s X.509 certificate, with inclusion mode set to …/IncludeToken/AlwaysToRecipient</span></span>  
  
 <span data-ttu-id="ef812-372">Alıcı Belirteci: Sunucunun X.509 Sertifikası, dahil etme modu ile ayarlanır .../IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="ef812-372">Recipient Token: Server’s X.509 Certificate, with inclusion mode is set …/IncludeToken/Never</span></span>  
  
 <span data-ttu-id="ef812-373">Belirteç Koruması: False</span><span class="sxs-lookup"><span data-stu-id="ef812-373">Token Protection: False</span></span>  
  
 <span data-ttu-id="ef812-374">Tüm Üstbilgi Ve Gövde İmzaları: Doğru</span><span class="sxs-lookup"><span data-stu-id="ef812-374">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="ef812-375">Koruma Emri: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="ef812-375">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="ef812-376">İmzayı Şifrele: Doğru</span><span class="sxs-lookup"><span data-stu-id="ef812-376">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="ef812-377">İlke</span><span class="sxs-lookup"><span data-stu-id="ef812-377">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='MutualCertificate_WSS10_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:AsymmetricBinding>  
        <wsp:Policy>  
          <sp:InitiatorToken>  
            <wsp:Policy>  
              <sp:X509Token
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <wsp:Policy>  
                  <sp:WssX509V3Token10 />
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:InitiatorToken>  
          <sp:RecipientToken>  
            <wsp:Policy>  
              <sp:X509Token
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/Never' >  
                <wsp:Policy>  
                  <sp:WssX509V3Token10 />
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:RecipientToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
          <sp:EncryptSignature />
          <sp:OnlySignEntireHeadersAndBody />
        </wsp:Policy>  
      </sp:AsymmetricBinding>  
      <sp:Wss10>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
        </wsp:Policy>  
      </sp:Wss10>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="ef812-378">Güvenlik Üstbilgi Örnekleri: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="ef812-378">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="ef812-379">İstek</span><span class="sxs-lookup"><span data-stu-id="ef812-379">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedKey>  
  ...  
    <xenc:ReferenceList>  
    ...  
    </xenc:ReferenceList>  
  </xenc:EncryptedKey>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="ef812-380">Yanıt</span><span class="sxs-lookup"><span data-stu-id="ef812-380">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
    <xenc:ReferenceList>  
    ...  
    </xenc:ReferenceList>  
  </xenc:EncryptedKey>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="ef812-381">Güvenlik Üstbilgi Örnekleri: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="ef812-381">Security Header Examples: EncryptBeforeSign</span></span>  
  
 <span data-ttu-id="ef812-382">İstek</span><span class="sxs-lookup"><span data-stu-id="ef812-382">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="ef812-383">Yanıt</span><span class="sxs-lookup"><span data-stu-id="ef812-383">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="622-mutualcertificateduplex"></a><span data-ttu-id="ef812-384">6.2.2 MutualCertificateDuplex</span><span class="sxs-lookup"><span data-stu-id="ef812-384">6.2.2 MutualCertificateDuplex</span></span>  
 <span data-ttu-id="ef812-385">Bu kimlik doğrulama modu ile istemci, SOAP katmanında başlatıcı belirteci olarak görünen bir X.509 sertifikası kullanarak kimlik doğrulaması verir.</span><span class="sxs-lookup"><span data-stu-id="ef812-385">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as the initiator token.</span></span> <span data-ttu-id="ef812-386">Hizmet ayrıca X.509 sertifikası kullanılarak da doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="ef812-386">The service is also authenticated using an X.509 certificate.</span></span>  
  
 <span data-ttu-id="ef812-387">Kullanılan bağlama, aşağıdaki özellik değerleriyle asimetrik bir bağlamadır:</span><span class="sxs-lookup"><span data-stu-id="ef812-387">The binding used is an asymmetric binding with the following property values:</span></span>  
  
 <span data-ttu-id="ef812-388">Başlatıcı Belirteci: Müşterinin X509 Sertifikası, ekleme modu .../IncludeToken/AlwaysToRecipient olarak ayarlanır</span><span class="sxs-lookup"><span data-stu-id="ef812-388">Initiator Token: Client’s X509 Certificate, inclusion mode is set to …/IncludeToken/AlwaysToRecipient</span></span>  
  
 <span data-ttu-id="ef812-389">Alıcı Belirteci: Sunucunun X509 Sertifikası, ekleme modu .../IncludeToken/AlwaysToInitiator olarak ayarlanır</span><span class="sxs-lookup"><span data-stu-id="ef812-389">Recipient Token: Server’s X509 Certificate, inclusion mode is set to …/IncludeToken/AlwaysToInitiator</span></span>  
  
 <span data-ttu-id="ef812-390">Belirteç Koruması: False</span><span class="sxs-lookup"><span data-stu-id="ef812-390">Token Protection: False</span></span>  
  
 <span data-ttu-id="ef812-391">Tüm Üstbilgi Ve Gövde İmzaları: Doğru</span><span class="sxs-lookup"><span data-stu-id="ef812-391">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="ef812-392">Koruma Emri: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="ef812-392">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="ef812-393">İmzayı Şifrele: Doğru</span><span class="sxs-lookup"><span data-stu-id="ef812-393">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="ef812-394">İlke</span><span class="sxs-lookup"><span data-stu-id="ef812-394">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='MutualCertificateDuplex_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:AsymmetricBinding>  
        <wsp:Policy>  
          <sp:InitiatorToken>  
            <wsp:Policy>  
              <sp:X509Token
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <wsp:Policy>  
                  <sp:WssX509V3Token10 />
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:InitiatorToken>  
          <sp:RecipientToken>  
            <wsp:Policy>  
              <sp:X509Token
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToInitiator' >  
                <wsp:Policy>  
                  <sp:WssX509V3Token10 />
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:RecipientToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
          <sp:EncryptSignature />
          <sp:OnlySignEntireHeadersAndBody />
        </wsp:Policy>  
      </sp:AsymmetricBinding>  
      <sp:Wss10>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
        </wsp:Policy>  
      </sp:Wss10>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="ef812-395">Güvenlik Üstbilgi Örnekleri: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="ef812-395">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="ef812-396">İstek ve Yanıt</span><span class="sxs-lookup"><span data-stu-id="ef812-396">Request and Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedKey>  
  ...  
    <xenc:ReferenceList>  
    ...  
    </xenc:ReferenceList>  
  </xenc:EncryptedKey>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="ef812-397">Güvenlik Üstbilgi Örnekleri: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="ef812-397">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="ef812-398">İstek ve Yanıt</span><span class="sxs-lookup"><span data-stu-id="ef812-398">Request and Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="623-using-symmetricbinding-with-x509-service-authentication"></a><span data-ttu-id="ef812-399">6.2.3 X.509 Hizmet Kimlik Doğrulaması ile Simetrik Bağlama Kullanma</span><span class="sxs-lookup"><span data-stu-id="ef812-399">6.2.3 Using SymmetricBinding with X.509 Service Authentication</span></span>  
 <span data-ttu-id="ef812-400">"WSS10", X509 belirteçleri olan senaryolar için sınırlı destek sağladı.</span><span class="sxs-lookup"><span data-stu-id="ef812-400">"WSS10" provided limited support for scenarios with X509 tokens.</span></span> <span data-ttu-id="ef812-401">Örneğin, yalnızca Hizmet X509 belirteci kullanarak iletiler için imza ve şifreleme koruması sağlamanın bir yolu yoktu.</span><span class="sxs-lookup"><span data-stu-id="ef812-401">For example, there was no way to provide signature and encryption protection for messages using only service X509 token.</span></span> <span data-ttu-id="ef812-402">"WSS11" şifreli anahtar kullanımını simetrik bir belirteç olarak tanıttı.</span><span class="sxs-lookup"><span data-stu-id="ef812-402">"WSS11" introduced the usage of EncryptedKey as a symmetric token.</span></span> <span data-ttu-id="ef812-403">Şimdi, hizmetin X.509 sertifikası için şifrelenmiş geçici bir anahtar hem istek hem de yanıt iletileri koruması için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ef812-403">Now a temporary key encrypted for the service's X.509 certificate could be used for both request and response messages protection.</span></span> <span data-ttu-id="ef812-404">Aşağıdaki bölüm 6.4'te açıklanan kimlik doğrulama modları bu deseni kullanır.</span><span class="sxs-lookup"><span data-stu-id="ef812-404">The authentication modes described in the section 6.4 below use this pattern.</span></span>  
  
 <span data-ttu-id="ef812-405">WS-SecurityPolicy bu deseni koruma belirteci olarak X509 hizmeti ile Simetribağlayıcı kullanarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ef812-405">WS-SecurityPolicy describes this pattern using SymmetricBinding with Service X509 token as the protection token.</span></span>  
  
 <span data-ttu-id="ef812-406">Kimlik doğrulama modları AnonymousForCertificate, UsernameForCertificate, MutualCertificate WSS11 ve IssuedTokenForCertificate'un tümü benzer bir sp örneğini kullanır:Aşağıdaki özellik değerleriyle Simetrik Bağlama:</span><span class="sxs-lookup"><span data-stu-id="ef812-406">Authentication modes AnonymousForCertificate, UsernameForCertificate, MutualCertificate WSS11 and IssuedTokenForCertificate all use a similar instance of sp:SymmetricBinding with the following property values:</span></span>  
  
 <span data-ttu-id="ef812-407">Koruma Belirteci: Sunucunun X509 Sertifikası, ekleme modu .../IncludeToken/Never olarak ayarlanır</span><span class="sxs-lookup"><span data-stu-id="ef812-407">Protection Token: Server’s X509 Certificate, inclusion mode is set to .../IncludeToken/Never</span></span>  
<span data-ttu-id="ef812-408">Belirteç Koruması: False</span><span class="sxs-lookup"><span data-stu-id="ef812-408">Token Protection: False</span></span>  
  
 <span data-ttu-id="ef812-409">Tüm Üstbilgi Ve Gövde İmzaları: Doğru</span><span class="sxs-lookup"><span data-stu-id="ef812-409">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="ef812-410">Koruma Emri: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="ef812-410">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="ef812-411">İmzayı Şifrele: Doğru</span><span class="sxs-lookup"><span data-stu-id="ef812-411">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="ef812-412">Yukarıdaki kimlik doğrulama modları yalnızca kullandıkları destekleyici belirteçlere göre farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="ef812-412">The above authentication modes only differ by the supporting tokens they use.</span></span> <span data-ttu-id="ef812-413">AnonymousForCertificate herhangi bir destekleyici belirteçleri yok, MutualCertificate WSS 1.1 destekleyici belirteçleri destekleyici bir istemcinin X509 sertifikasına sahiptir, UserNameForCertificate imzalı bir destekleyici belirteç olarak bir Kullanıcı Adı Belirteci vardır ve IssuedTokenForCertificate destekleyici belirteci olarak verilen belirteç vardır.</span><span class="sxs-lookup"><span data-stu-id="ef812-413">AnonymousForCertificate does not have any supporting tokens, MutualCertificate WSS 1.1 has the client’s X509 certificate as an endorsing supporting tokens, UserNameForCertificate has a UserName Token as a signed supporting token and IssuedTokenForCertificate has the issued token as an endorsing supporting token.</span></span>  
  
 <span data-ttu-id="ef812-414">İlke</span><span class="sxs-lookup"><span data-stu-id="ef812-414">Policy</span></span>  
  
 <span data-ttu-id="ef812-415">Simetrik Bağlama</span><span class="sxs-lookup"><span data-stu-id="ef812-415">Symmetric Binding</span></span>  
  
```xml  
<wsp:Policy wsu:Id='SymmetricCert_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:X509Token
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/Never' >  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />
                  <sp:RequireThumbprintReference />
                  <sp:WssX509V3Token10 />
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
          <sp:EncryptSignature />
          <sp:OnlySignEntireHeadersAndBody />  
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <!-- Supporting Token Assertions appear here -->  
      ...  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
          <sp:MustSupportRefThumbprint />
          <sp:MustSupportRefEncryptedKey />
          <sp:RequireSignatureConfirmation />
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
#### <a name="624-anonymousforcertificate"></a><span data-ttu-id="ef812-416">6.2.4 Anonim ForCertificate</span><span class="sxs-lookup"><span data-stu-id="ef812-416">6.2.4 AnonymousForCertificate</span></span>  
 <span data-ttu-id="ef812-417">Bu kimlik doğrulama modu ile istemci anonimdir ve hizmet x.509 sertifikası kullanılarak kimlik doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="ef812-417">With this authentication mode the client is anonymous and the service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="ef812-418">Kullanılan bağlama 6.4.2'de açıklandığı gibi simetrik bağlama örneğidir.</span><span class="sxs-lookup"><span data-stu-id="ef812-418">The binding used is an instance of symmetric binding as described in 6.4.2.</span></span>  
  
 <span data-ttu-id="ef812-419">İlke</span><span class="sxs-lookup"><span data-stu-id="ef812-419">Policy</span></span>  
  
 <span data-ttu-id="ef812-420">Bağlayıcı ayrıntılar için yukarıdaki 6.2.3'teki "İlke"</span><span class="sxs-lookup"><span data-stu-id="ef812-420">See "Policy" in 6.2.3 above for binding details</span></span>  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="ef812-421">Güvenlik Üstbilgi Örnekleri: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="ef812-421">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="ef812-422">İstek</span><span class="sxs-lookup"><span data-stu-id="ef812-422">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="ef812-423">Yanıt</span><span class="sxs-lookup"><span data-stu-id="ef812-423">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="ef812-424">Güvenlik Üstbilgi Örnekleri: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="ef812-424">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="ef812-425">İstek</span><span class="sxs-lookup"><span data-stu-id="ef812-425">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="ef812-426">Yanıt</span><span class="sxs-lookup"><span data-stu-id="ef812-426">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wsse11:SignatureConfirmation />  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="625-usernameforcertificate"></a><span data-ttu-id="ef812-427">6.2.5 Kullanıcı AdıForCertificate</span><span class="sxs-lookup"><span data-stu-id="ef812-427">6.2.5 UserNameForCertificate</span></span>  
 <span data-ttu-id="ef812-428">Bu kimlik doğrulama modu ile istemci, SOAP katmanında imzalı destekleyici belirteç olarak görünen bir Kullanıcı Adı Belirteci kullanarak hizmete kimlik doğrular.</span><span class="sxs-lookup"><span data-stu-id="ef812-428">With this authentication mode the client authenticates to the service using a Username Token which appears at the SOAP layer as a signed supporting token.</span></span> <span data-ttu-id="ef812-429">Hizmet, X.509 sertifikası kullanarak istemciye kimlik doğrular.</span><span class="sxs-lookup"><span data-stu-id="ef812-429">The service authenticates to the client using an X.509 certificate.</span></span> <span data-ttu-id="ef812-430">Kullanılan bağlama, istemci tarafından oluşturulan ve hizmetin ortak anahtarıyla şifrelenmiş bir anahtar olan koruma belirteci ile simetrik bir bağlamadır.</span><span class="sxs-lookup"><span data-stu-id="ef812-430">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="ef812-431">İlke</span><span class="sxs-lookup"><span data-stu-id="ef812-431">Policy</span></span>  
  
 <span data-ttu-id="ef812-432">Bağlayıcı ayrıntılar için yukarıdaki 6.2.3'teki "İlke"</span><span class="sxs-lookup"><span data-stu-id="ef812-432">See "Policy" in 6.2.3 above for binding details</span></span>  
  
 <span data-ttu-id="ef812-433">İmzalı Destekleyici Belirteç</span><span class="sxs-lookup"><span data-stu-id="ef812-433">Signed Supporting Token</span></span>  
  
```xml  
<sp:SignedSupportingTokens>  
  <wsp:Policy>  
    <sp:UsernameToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <wsp:Policy>  
        <sp:WssUsernameToken10 />
      </wsp:Policy>  
    </sp:UsernameToken>  
  </wsp:Policy>  
</sp:SignedSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="ef812-434">Güvenlik Üstbilgi Örnekleri: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="ef812-434">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="ef812-435">İstek</span><span class="sxs-lookup"><span data-stu-id="ef812-435">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="ef812-436">Yanıt</span><span class="sxs-lookup"><span data-stu-id="ef812-436">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="ef812-437">Güvenlik Üstbilgi Örnekleri: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="ef812-437">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="ef812-438">İstek</span><span class="sxs-lookup"><span data-stu-id="ef812-438">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="ef812-439">Yanıt</span><span class="sxs-lookup"><span data-stu-id="ef812-439">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="626-mutualcertificate-wss-11"></a><span data-ttu-id="ef812-440">6.2.6 Karşılıklı Sertifika (WSS 1.1)</span><span class="sxs-lookup"><span data-stu-id="ef812-440">6.2.6 MutualCertificate (WSS 1.1)</span></span>  
 <span data-ttu-id="ef812-441">Bu kimlik doğrulama modu ile istemci, SOAP katmanında destekleyici bir belirteç olarak görünen bir X.509 sertifikası kullanarak kimlik doğrulaması verir.</span><span class="sxs-lookup"><span data-stu-id="ef812-441">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="ef812-442">Hizmet ayrıca X.509 sertifikası kullanılarak da doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="ef812-442">The service is also authenticated using an X.509 certificate.</span></span> <span data-ttu-id="ef812-443">Kullanılan bağlama, istemci tarafından oluşturulan ve hizmetin ortak anahtarıyla şifrelenmiş bir anahtar olan koruma belirteci ile simetrik bir bağlamadır.</span><span class="sxs-lookup"><span data-stu-id="ef812-443">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="ef812-444">İlke</span><span class="sxs-lookup"><span data-stu-id="ef812-444">Policy</span></span>  
  
 <span data-ttu-id="ef812-445">Bağlayıcı ayrıntılar için 6.2.3'teki Politikaya bakın</span><span class="sxs-lookup"><span data-stu-id="ef812-445">See Policy in 6.2.3 for binding details</span></span>  
  
 <span data-ttu-id="ef812-446">Destekleyici Belirteç</span><span class="sxs-lookup"><span data-stu-id="ef812-446">Endorsing Supporting Token</span></span>  
  
```xml  
<sp:EndorsingSupportingTokens>  
  <wsp:Policy>  
    <sp:X509Token sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <wsp:Policy>  
        <sp:RequireThumbprintReference />
        <sp:WssX509V3Token10 />
      </wsp:Policy>  
    </sp:X509Token>  
  </wsp:Policy>  
</sp:EndorsingSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="ef812-447">Güvenlik Üstbilgi Örnekleri: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="ef812-447">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="ef812-448">İstek</span><span class="sxs-lookup"><span data-stu-id="ef812-448">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="ef812-449">Yanıt</span><span class="sxs-lookup"><span data-stu-id="ef812-449">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="ef812-450">Güvenlik Üstbilgi Örnekleri: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="ef812-450">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="ef812-451">İstek</span><span class="sxs-lookup"><span data-stu-id="ef812-451">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="ef812-452">Yanıt</span><span class="sxs-lookup"><span data-stu-id="ef812-452">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wsse11:SignatureConfirmation />  
  <wsse11:SignatureConfirmation />  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="627-issuedtokenforcertificate"></a><span data-ttu-id="ef812-453">6.2.7 Verilen TokenForCertificate</span><span class="sxs-lookup"><span data-stu-id="ef812-453">6.2.7 IssuedTokenForCertificate</span></span>  
 <span data-ttu-id="ef812-454">Bu kimlik doğrulama modu ile istemci hizmete doğrudoğrulama yapmaz, ancak bunun yerine bir STS tarafından verilen bir belirteç sunar ve paylaşılan bir anahtar bilgisini kanıtlıyor.</span><span class="sxs-lookup"><span data-stu-id="ef812-454">With this authentication mode the client does not authenticate to the service, as such, but instead presents a token issued by a STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="ef812-455">Verilen belirteç, SOAP katmanında destekleyici bir belirteç olarak görünür.</span><span class="sxs-lookup"><span data-stu-id="ef812-455">The issued token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="ef812-456">Hizmet, X.509 sertifikası kullanarak istemciye kimlik doğrular.</span><span class="sxs-lookup"><span data-stu-id="ef812-456">The service authenticates to the client using an X.509 certificate.</span></span> <span data-ttu-id="ef812-457">Kullanılan bağlama, istemci tarafından oluşturulan ve hizmetin ortak anahtarıyla şifrelenmiş bir anahtar olan koruma belirteci ile simetrik bir bağlamadır.</span><span class="sxs-lookup"><span data-stu-id="ef812-457">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="ef812-458">İlke</span><span class="sxs-lookup"><span data-stu-id="ef812-458">Policy</span></span>  
  
 <span data-ttu-id="ef812-459">Bağlayıcı ayrıntılar için yukarıdaki 6.2.3'teki Politikaya bakın</span><span class="sxs-lookup"><span data-stu-id="ef812-459">See Policy in 6.2.3 above for binding details</span></span>  
  
 <span data-ttu-id="ef812-460">Destekleyici Belirteç</span><span class="sxs-lookup"><span data-stu-id="ef812-460">Endorsing Supporting Token</span></span>  
  
```xml  
<sp:EndorsingSupportingTokens>  
  <wsp:Policy>  
    <sp:IssuedToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <sp:RequestSecurityTokenTemplate>  
        <wst:KeyType>  
http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey  
       </wst:KeyType>  
     </sp:RequestSecurityTokenTemplate>  
     <wsp:Policy>  
       <sp:RequireDerivedKeys />
       <sp:RequireInternalReference />
     </wsp:Policy>  
   </sp:IssuedToken>  
  </wsp:Policy>  
</sp:EndorsingSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="ef812-461">Güvenlik Üstbilgi Örnekleri: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="ef812-461">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="ef812-462">İstek</span><span class="sxs-lookup"><span data-stu-id="ef812-462">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="ef812-463">Yanıt</span><span class="sxs-lookup"><span data-stu-id="ef812-463">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="ef812-464">Güvenlik Üstbilgi Örnekleri: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="ef812-464">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="ef812-465">İstek</span><span class="sxs-lookup"><span data-stu-id="ef812-465">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="ef812-466">Yanıt</span><span class="sxs-lookup"><span data-stu-id="ef812-466">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wsse11:SignatureConfirmation />  
  <wsse11:SignatureConfirmation />  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
## <a name="63-kerberos"></a><span data-ttu-id="ef812-467">6.3 Kerberos</span><span class="sxs-lookup"><span data-stu-id="ef812-467">6.3 Kerberos</span></span>  
 <span data-ttu-id="ef812-468">Bu kimlik doğrulama modu ile istemci bir Kerberos bileti kullanarak hizmete kimlik doğrular.</span><span class="sxs-lookup"><span data-stu-id="ef812-468">With this authentication mode the client authenticates to the service using a Kerberos ticket.</span></span> <span data-ttu-id="ef812-469">Aynı bilet aynı zamanda sunucu kimlik doğrulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="ef812-469">That same ticket also provides server authentication.</span></span> <span data-ttu-id="ef812-470">Kullanılan bağlama aşağıdaki özelliklere sahip simetrik bir bağlamadır;</span><span class="sxs-lookup"><span data-stu-id="ef812-470">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="ef812-471">Koruma Belirteci: Kerberos Bilet, dahil etme modu ayarlanır .../IncludeToken/Once</span><span class="sxs-lookup"><span data-stu-id="ef812-471">Protection Token: Kerberos Ticket, inclusion mode is set to .../IncludeToken/Once</span></span>  
<span data-ttu-id="ef812-472">Belirteç Koruması: False</span><span class="sxs-lookup"><span data-stu-id="ef812-472">Token Protection: False</span></span>  
  
 <span data-ttu-id="ef812-473">Tüm Üstbilgi Ve Gövde İmzaları: Doğru</span><span class="sxs-lookup"><span data-stu-id="ef812-473">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="ef812-474">Koruma Emri: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="ef812-474">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="ef812-475">İmzayı Şifrele: Doğru</span><span class="sxs-lookup"><span data-stu-id="ef812-475">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="ef812-476">İlke</span><span class="sxs-lookup"><span data-stu-id="ef812-476">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='Kerberos_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:KerberosToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/Once' >  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />
                  <sp:WssGssKerberosV5ApReqToken11 />
                </wsp:Policy>  
              </sp:KerberosToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic128 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
          <sp:EncryptSignature />
          <sp:OnlySignEntireHeadersAndBody />
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
          <sp:MustSupportRefThumbprint />
          <sp:MustSupportRefEncryptedKey />
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="ef812-477">Güvenlik Üstbilgi Örnekleri: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="ef812-477">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="ef812-478">İstek</span><span class="sxs-lookup"><span data-stu-id="ef812-478">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="ef812-479">Yanıt</span><span class="sxs-lookup"><span data-stu-id="ef812-479">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="ef812-480">Güvenlik Üstbilgi Örnekleri: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="ef812-480">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="ef812-481">İstek</span><span class="sxs-lookup"><span data-stu-id="ef812-481">Request</span></span>  
  
```xml  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
 <span data-ttu-id="ef812-482">Yanıt</span><span class="sxs-lookup"><span data-stu-id="ef812-482">Response</span></span>  
  
```xml  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
#### <a name="64-issuedtoken"></a><span data-ttu-id="ef812-483">6.4 İhraç Edilen Token</span><span class="sxs-lookup"><span data-stu-id="ef812-483">6.4 IssuedToken</span></span>  
 <span data-ttu-id="ef812-484">Bu kimlik doğrulama modu ile istemci hizmete kimlik doğrulamaz, bu nedenle, istemci bir STS tarafından verilen bir belirteç sunar ve paylaşılan bir anahtar hakkındaki bilgileri kanıtlar.</span><span class="sxs-lookup"><span data-stu-id="ef812-484">With this authentication mode the client does not authenticate to the service, as such, rather the client presents a token issued by an STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="ef812-485">Hizmet istemciye doğrulanmaz, bunun yerine STS paylaşılan anahtarı verilen belirtecinin bir parçası olarak şifreler, bu şekilde yalnızca hizmet anahtarın şifresini çözebilir.</span><span class="sxs-lookup"><span data-stu-id="ef812-485">The service is not authenticated to the client, as such, instead the STS encrypts the shared key as part of the issued token such that only the service can decrypt the key.</span></span> <span data-ttu-id="ef812-486">Kullanılan bağlama aşağıdaki özelliklere sahip simetrik bağlama olarak;</span><span class="sxs-lookup"><span data-stu-id="ef812-486">The binding used is as symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="ef812-487">Koruma Belirteci: Verilen Belirteç, dahil etme modu .../IncludeToken/AlwaysToRecipient olarak ayarlanır</span><span class="sxs-lookup"><span data-stu-id="ef812-487">Protection Token: Issued Token, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
<span data-ttu-id="ef812-488">Belirteç Koruması: False</span><span class="sxs-lookup"><span data-stu-id="ef812-488">Token Protection: False</span></span>  
  
 <span data-ttu-id="ef812-489">Tüm Üstbilgi Ve Gövde İmzaları: Doğru</span><span class="sxs-lookup"><span data-stu-id="ef812-489">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="ef812-490">Koruma Emri: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="ef812-490">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="ef812-491">İmzayı Şifrele: Doğru</span><span class="sxs-lookup"><span data-stu-id="ef812-491">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="ef812-492">İlke</span><span class="sxs-lookup"><span data-stu-id="ef812-492">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='CustomBinding_ISimple3_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:IssuedToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <sp:RequestSecurityTokenTemplate>  
                  <wst:KeyType>  
http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey  
                  </wst:KeyType>
                </sp:RequestSecurityTokenTemplate>  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />
                  <sp:RequireInternalReference />
                </wsp:Policy>  
              </sp:IssuedToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
          <sp:EncryptSignature />
          <sp:OnlySignEntireHeadersAndBody />
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
          <sp:MustSupportRefThumbprint />
          <sp:MustSupportRefEncryptedKey />
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="ef812-493">Güvenlik Üstbilgi Örnekleri: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="ef812-493">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="ef812-494">İstek</span><span class="sxs-lookup"><span data-stu-id="ef812-494">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="ef812-495">Yanıt</span><span class="sxs-lookup"><span data-stu-id="ef812-495">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="ef812-496">Güvenlik Üstbilgi Örnekleri: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="ef812-496">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="ef812-497">İstek</span><span class="sxs-lookup"><span data-stu-id="ef812-497">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="ef812-498">Yanıt</span><span class="sxs-lookup"><span data-stu-id="ef812-498">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
### <a name="65-using-sslnegotiated-for-service-authentication"></a><span data-ttu-id="ef812-499">6.5 Hizmet Kimlik Doğrulaması için SslNegotiated'i Kullanma</span><span class="sxs-lookup"><span data-stu-id="ef812-499">6.5 Using SslNegotiated for Service Authentication</span></span>  
 <span data-ttu-id="ef812-500">Bu bölümde, WS-Trust (WS-T) RST/RSTR iletileri üzerinden TLS protokolü yürütülerek anahtar değeri görüşülen WS-SecureConversation (WS-SC) başına güvenlik bağlamı belirteci olan koruma belirteci ile simetrik bir bağlama kullanan bir kimlik doğrulama modu grubu açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ef812-500">This section describes a group of authentication modes that use a symmetric binding with the protection token being a Security Context Token per WS-SecureConversation (WS-SC) whose key value is negotiated by executing the TLS protocol over WS-Trust (WS-T) RST/RSTR messages.</span></span> <span data-ttu-id="ef812-501">WS-Trust kullanılarak TLS el sıkışma uygulamasının ayrıntıları TLSNEGO'da açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="ef812-501">Details of the TLS handshake implementation using WS-Trust are described in TLSNEGO.</span></span> <span data-ttu-id="ef812-502">Burada ileti örneklerinde, ilişkili bir güvenlik bağlamına sahip ÖST'nin el sıkışma yoluyla zaten kurulduğunu varsayacağız.</span><span class="sxs-lookup"><span data-stu-id="ef812-502">Here in the message examples we will assume that SCT with an associated security context is already established through a handshake.</span></span>  
  
 <span data-ttu-id="ef812-503">Kullanılan bağlama aşağıdaki özelliklere sahip simetrik bir bağlamadır;</span><span class="sxs-lookup"><span data-stu-id="ef812-503">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="ef812-504">Koruma Belirteci: SslContextToken, ekleme modu ayarlanır .../IncludeToken/Never</span><span class="sxs-lookup"><span data-stu-id="ef812-504">Protection Token: SslContextToken, inclusion mode is set to .../IncludeToken/Never</span></span>  
<span data-ttu-id="ef812-505">Belirteç Koruması: False</span><span class="sxs-lookup"><span data-stu-id="ef812-505">Token Protection: False</span></span>  
  
 <span data-ttu-id="ef812-506">Tüm Üstbilgi Ve Gövde İmzaları: Doğru</span><span class="sxs-lookup"><span data-stu-id="ef812-506">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="ef812-507">Koruma Emri: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="ef812-507">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="ef812-508">İmzayı Şifrele: Doğru</span><span class="sxs-lookup"><span data-stu-id="ef812-508">Encrypt Signature: True</span></span>  
  
#### <a name="651-policy-for-sslnegotiated-service-authentication"></a><span data-ttu-id="ef812-509">6.5.1 SslNegotiated hizmet kimlik doğrulaması için politika</span><span class="sxs-lookup"><span data-stu-id="ef812-509">6.5.1 Policy for SslNegotiated service authentication</span></span>  
 <span data-ttu-id="ef812-510">Bu bölümdeki tüm kimlik doğrulama modları için ilke benzerdir ve yalnızca kullanılan belirli imzalı destekleyici veya destekleyici belirteçlerle farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="ef812-510">Policy for all authentication modes in this section are similar and differ only by specific signed supporting or endorsing tokens used.</span></span>  
  
```xml  
<wsp:Policy wsu:Id='SslNegotiated_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <mssp:SslContextToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient'>  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />
                </wsp:Policy>  
              </mssp:SslContextToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
          <sp:EncryptSignature />
          <sp:OnlySignEntireHeadersAndBody />
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <!-- Supporting token assertions go here -->  
      ..  
      <sp:Wss11>
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
          <sp:MustSupportRefThumbprint />
          <sp:MustSupportRefEncryptedKey />
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
#### <a name="652-anonymousforsslnegotiated"></a><span data-ttu-id="ef812-511">6.5.2 AnonimForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="ef812-511">6.5.2 AnonymousForSslNegotiated</span></span>  
 <span data-ttu-id="ef812-512">Bu kimlik doğrulama modu ile istemci anonimdir ve hizmet x.509 sertifikası kullanılarak kimlik doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="ef812-512">With this authentication mode the client is anonymous and the service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="ef812-513">Kullanılan bağlama yukarıdaki 6.5.1'de açıklandığı gibi simetrik bağlama örneğidir.</span><span class="sxs-lookup"><span data-stu-id="ef812-513">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="ef812-514">İlke</span><span class="sxs-lookup"><span data-stu-id="ef812-514">Policy</span></span>  
  
 <span data-ttu-id="ef812-515">Bağlayıcı ayrıntılar için yukarıdaki 6.5.1'deki Politika'ya bakın.</span><span class="sxs-lookup"><span data-stu-id="ef812-515">See Policy in 6.5.1 above for binding details.</span></span>  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="ef812-516">Güvenlik Üstbilgi Örnekleri: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="ef812-516">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="ef812-517">İstek</span><span class="sxs-lookup"><span data-stu-id="ef812-517">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="ef812-518">Yanıt</span><span class="sxs-lookup"><span data-stu-id="ef812-518">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="ef812-519">Güvenlik Üstbilgi Örnekleri: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="ef812-519">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="ef812-520">İstek</span><span class="sxs-lookup"><span data-stu-id="ef812-520">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="ef812-521">Yanıt</span><span class="sxs-lookup"><span data-stu-id="ef812-521">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="653-usernameforsslnegotiated"></a><span data-ttu-id="ef812-522">6.5.3 Kullanıcı AdıForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="ef812-522">6.5.3 UserNameForSslNegotiated</span></span>  
 <span data-ttu-id="ef812-523">Bu kimlik doğrulama modu ile istemci, SOAP katmanında imzalı destekleyici belirteç olarak görünen bir Kullanıcı Adı Belirteci kullanılarak kimlik doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="ef812-523">With this authentication mode the client is authenticates using a Username Token which appears at the SOAP layer as a signed supporting token.</span></span> <span data-ttu-id="ef812-524">Hizmet, X.509 sertifikası kullanılarak kimlik doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="ef812-524">The service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="ef812-525">Kullanılan bağlama 6.5.1'de açıklandığı gibi simetrik bağlama örneğidir.</span><span class="sxs-lookup"><span data-stu-id="ef812-525">The binding used is an instance of symmetric binding as described in 6.5.1.</span></span>  
  
 <span data-ttu-id="ef812-526">İlke</span><span class="sxs-lookup"><span data-stu-id="ef812-526">Policy</span></span>  
  
 <span data-ttu-id="ef812-527">Bağlayıcı ayrıntılar için yukarıdaki bölüm 6.5.1'e bakın</span><span class="sxs-lookup"><span data-stu-id="ef812-527">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="ef812-528">İmzalı Destekleyici Belirteç</span><span class="sxs-lookup"><span data-stu-id="ef812-528">Signed Supporting Token</span></span>  
  
```xml  
<sp:SignedSupportingTokens>  
  <wsp:Policy>  
    <sp:UsernameToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <wsp:Policy>  
        <sp:WssUsernameToken10 />
      </wsp:Policy>  
    </sp:UsernameToken>  
  </wsp:Policy>  
</sp:SignedSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="ef812-529">Güvenlik Üstbilgi Örnekleri: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="ef812-529">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="ef812-530">İstek</span><span class="sxs-lookup"><span data-stu-id="ef812-530">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="ef812-531">Yanıt</span><span class="sxs-lookup"><span data-stu-id="ef812-531">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="ef812-532">Güvenlik Üstbilgi Örnekleri: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="ef812-532">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="ef812-533">İstek</span><span class="sxs-lookup"><span data-stu-id="ef812-533">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="ef812-534">Yanıt</span><span class="sxs-lookup"><span data-stu-id="ef812-534">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="654-issuedtokenforsslnegotiated"></a><span data-ttu-id="ef812-535">6.5.4 VerilenTokenForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="ef812-535">6.5.4 IssuedTokenForSslNegotiated</span></span>  
 <span data-ttu-id="ef812-536">Bu kimlik doğrulama modu ile istemci hizmete doğrudoğrulama yapmaz, ancak bunun yerine bir STS tarafından verilen bir belirteç sunar ve paylaşılan bir anahtar bilgisini kanıtlıyor.</span><span class="sxs-lookup"><span data-stu-id="ef812-536">With this authentication mode the client does not authenticate to the service, as such, but instead presents a token issued by an STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="ef812-537">Verilen belirteç, SOAP katmanında destekleyici bir belirteç olarak görünür.</span><span class="sxs-lookup"><span data-stu-id="ef812-537">The issued token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="ef812-538">Hizmet, X.509 sertifikası kullanılarak kimlik doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="ef812-538">The service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="ef812-539">Kullanılan bağlama yukarıdaki 6.5.1'de açıklandığı gibi simetrik bağlama örneğidir.</span><span class="sxs-lookup"><span data-stu-id="ef812-539">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="ef812-540">İlke</span><span class="sxs-lookup"><span data-stu-id="ef812-540">Policy</span></span>  
  
 <span data-ttu-id="ef812-541">Bağlayıcı ayrıntılar için yukarıdaki bölüm 6.5.1'e bakın</span><span class="sxs-lookup"><span data-stu-id="ef812-541">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="ef812-542">Destekleyici Belirteç</span><span class="sxs-lookup"><span data-stu-id="ef812-542">Endorsing Supporting Token</span></span>  
  
```xml  
<sp:EndorsingSupportingTokens>  
  <wsp:Policy>  
    <sp:IssuedToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <sp:RequestSecurityTokenTemplate>  
        <wst:KeyType>  
http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey  
        </wst:KeyType>
      </sp:RequestSecurityTokenTemplate>  
      <wsp:Policy>  
        <sp:RequireDerivedKeys />
        <sp:RequireInternalReference />
      </wsp:Policy>  
    </sp:IssuedToken>  
  </wsp:Policy>  
</sp:EndorsingSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="ef812-543">Güvenlik Üstbilgi Örnekleri: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="ef812-543">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="ef812-544">İstek</span><span class="sxs-lookup"><span data-stu-id="ef812-544">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="ef812-545">Yanıt</span><span class="sxs-lookup"><span data-stu-id="ef812-545">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="ef812-546">Güvenlik Üstbilgi Örnekleri: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="ef812-546">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="ef812-547">İstek</span><span class="sxs-lookup"><span data-stu-id="ef812-547">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="ef812-548">Yanıt</span><span class="sxs-lookup"><span data-stu-id="ef812-548">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsse11:SignatureConfirmation />  
  <wsse11:SignatureConfirmation />  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="655-mutualsslnegotiated"></a><span data-ttu-id="ef812-549">6.5.5 KarşılıklıSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="ef812-549">6.5.5 MutualSslNegotiated</span></span>  
 <span data-ttu-id="ef812-550">Bu kimlik doğrulama modu ile istemci ve hizmet X.509 sertifikalarını kullanarak kimlik doğrulaması yapın.</span><span class="sxs-lookup"><span data-stu-id="ef812-550">With this authentication mode the client and the service authenticate using X.509 certificates.</span></span> <span data-ttu-id="ef812-551">Kullanılan bağlama yukarıdaki 6.5.1'de açıklandığı gibi simetrik bağlama örneğidir.</span><span class="sxs-lookup"><span data-stu-id="ef812-551">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="ef812-552">İlke</span><span class="sxs-lookup"><span data-stu-id="ef812-552">Policy</span></span>  
  
 <span data-ttu-id="ef812-553">Bağlayıcı ayrıntılar için yukarıdaki bölüm 6.5.1'e bakın</span><span class="sxs-lookup"><span data-stu-id="ef812-553">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="ef812-554">Destekleyici Belirteç</span><span class="sxs-lookup"><span data-stu-id="ef812-554">Endorsing Supporting Token</span></span>  
  
```xml  
<sp:EndorsingSupportingTokens>  
  <wsp:Policy>  
    <sp:X509Token sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <wsp:Policy>  
        <sp:RequireThumbprintReference />
        <sp:WssX509V3Token10 />
      </wsp:Policy>  
    </sp:X509Token>  
  </wsp:Policy>  
</sp:EndorsingSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="ef812-555">Güvenlik Üstbilgi Örnekleri: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="ef812-555">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="ef812-556">İstek</span><span class="sxs-lookup"><span data-stu-id="ef812-556">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="ef812-557">Yanıt</span><span class="sxs-lookup"><span data-stu-id="ef812-557">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="ef812-558">Güvenlik Üstbilgi Örnekleri: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="ef812-558">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="ef812-559">İstek</span><span class="sxs-lookup"><span data-stu-id="ef812-559">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="ef812-560">Yanıt</span><span class="sxs-lookup"><span data-stu-id="ef812-560">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
### <a name="66-sspinegotiated"></a><span data-ttu-id="ef812-561">6.6 SspiNegotiated</span><span class="sxs-lookup"><span data-stu-id="ef812-561">6.6 SspiNegotiated</span></span>  
 <span data-ttu-id="ef812-562">Bu kimlik doğrulama modu ile istemci ve sunucu kimlik doğrulaması gerçekleştirmek için bir anlaşma protokolü kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ef812-562">With this authentication mode a negotiation protocol is used to perform client and server authentication.</span></span> <span data-ttu-id="ef812-563">Kerberos mümkünse kullanılır, aksi takdirde NTLM.</span><span class="sxs-lookup"><span data-stu-id="ef812-563">Kerberos is used if possible, otherwise NTLM.</span></span> <span data-ttu-id="ef812-564">Kullanılan bağlama aşağıdaki özelliklere sahip simetrik bir bağlamadır;</span><span class="sxs-lookup"><span data-stu-id="ef812-564">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="ef812-565">Koruma Belirteci: SpnegoContextToken, ekleme modu ayarlanır .../IncludeToken/AlwaysToRecipient</span><span class="sxs-lookup"><span data-stu-id="ef812-565">Protection Token: SpnegoContextToken, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
<span data-ttu-id="ef812-566">Belirteç Koruması: False</span><span class="sxs-lookup"><span data-stu-id="ef812-566">Token Protection: False</span></span>  
  
 <span data-ttu-id="ef812-567">Tüm Üstbilgi Ve Gövde İmzaları: Doğru</span><span class="sxs-lookup"><span data-stu-id="ef812-567">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="ef812-568">Koruma Emri: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="ef812-568">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="ef812-569">İmzayı Şifrele: Doğru</span><span class="sxs-lookup"><span data-stu-id="ef812-569">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="ef812-570">İlke</span><span class="sxs-lookup"><span data-stu-id="ef812-570">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='CustomBinding_ISimple13_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:SpnegoContextToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />
                </wsp:Policy>  
              </sp:SpnegoContextToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
          <sp:EncryptSignature />
          <sp:OnlySignEntireHeadersAndBody />
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
          <sp:MustSupportRefThumbprint />
          <sp:MustSupportRefEncryptedKey />
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="ef812-571">Güvenlik Üstbilgi Örnekleri: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="ef812-571">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="ef812-572">İstek</span><span class="sxs-lookup"><span data-stu-id="ef812-572">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="ef812-573">Yanıt</span><span class="sxs-lookup"><span data-stu-id="ef812-573">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="ef812-574">Güvenlik Üstbilgi Örnekleri: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="ef812-574">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="ef812-575">İstek</span><span class="sxs-lookup"><span data-stu-id="ef812-575">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="ef812-576">Yanıt</span><span class="sxs-lookup"><span data-stu-id="ef812-576">Response</span></span>  
  
```xml  
<wsse:Security>  
<wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
### <a name="67-secureconversation"></a><span data-ttu-id="ef812-577">6.7 Güvenli Konuşma</span><span class="sxs-lookup"><span data-stu-id="ef812-577">6.7 SecureConversation</span></span>  
 <span data-ttu-id="ef812-578">Kullanılan bağlama, koruma belirteci ws-SecureConversation (WS-SC) başına Bir SCT olan simetrik bir bağlamadır.</span><span class="sxs-lookup"><span data-stu-id="ef812-578">The binding used is a symmetric binding with the protection token being a SCT per WS-SecureConversation (WS-SC).</span></span> <span data-ttu-id="ef812-579">SCT, kendisi bir müzakere protokolü kullanan simetrik bir bağlayıcı olan iç içe bir bağlama ya göre WS-Trust (WS-Trust) veya WS-SecureConversation (WS-SC) kullanılarak görüşülür.</span><span class="sxs-lookup"><span data-stu-id="ef812-579">The SCT is negotiated using WS-Trust (WS-Trust) or WS-SecureConversation (WS-SC) according to a nested binding, which is itself a symmetric binding that uses a negotiation protocol.</span></span> <span data-ttu-id="ef812-580">Müzakere protokolü mümkünse istemci ve sunucu kimlik doğrulaması gerçekleştirmek için Kerberos kullanır.</span><span class="sxs-lookup"><span data-stu-id="ef812-580">The negotiation protocol will use Kerberos to perform client and server authentication if possible.</span></span> <span data-ttu-id="ef812-581">Kerberos kullanılamıyorsa, NTLM'ye geri döner.</span><span class="sxs-lookup"><span data-stu-id="ef812-581">If Kerberos cannot be used, it will fall back to NTLM.</span></span>  
  
 <span data-ttu-id="ef812-582">İlke</span><span class="sxs-lookup"><span data-stu-id="ef812-582">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='SecureConversation_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:SecureConversationToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />
                  <sp:BootstrapPolicy>  
                    <wsp:Policy>  
                      <sp:SignedParts>  
                        <sp:Body />
                        <sp:Header Name='To' Namespace='http://www.w3.org/2005/08/addressing' />
                        <sp:Header Name='From' Namespace='http://www.w3.org/2005/08/addressing' />
                        <sp:Header Name='FaultTo' Namespace='http://www.w3.org/2005/08/addressing' />
                        <sp:Header Name='ReplyTo' Namespace='http://www.w3.org/2005/08/addressing' />
                        <sp:Header Name='MessageID' Namespace='http://www.w3.org/2005/08/addressing' />
                        <sp:Header Name='RelatesTo' Namespace='http://www.w3.org/2005/08/addressing' />
                        <sp:Header Name='Action' Namespace='http://www.w3.org/2005/08/addressing' />
                      </sp:SignedParts>  
                      <sp:EncryptedParts>  
                        <sp:Body />
                      </sp:EncryptedParts>  
                      <sp:SymmetricBinding>  
                        <wsp:Policy>  
                          <sp:ProtectionToken>  
                            <wsp:Policy>  
                              <sp:SpnegoContextToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                                <wsp:Policy>  
                                  <sp:RequireDerivedKeys />
                                </wsp:Policy>  
                              </sp:SpnegoContextToken>  
                            </wsp:Policy>  
                          </sp:ProtectionToken>  
                          <sp:AlgorithmSuite>  
                            <wsp:Policy>  
                              <sp:Basic256 />
                            </wsp:Policy>  
                          </sp:AlgorithmSuite>  
                          <sp:Layout>  
                            <wsp:Policy>  
                              <sp:Strict />
                            </wsp:Policy>  
                          </sp:Layout>  
                          <sp:IncludeTimestamp />
                          <sp:EncryptSignature />
                          <sp:OnlySignEntireHeadersAndBody />
                        </wsp:Policy>  
                      </sp:SymmetricBinding>  
                      <sp:Wss11>  
                        <wsp:Policy>  
                          <sp:MustSupportRefKeyIdentifier />
                          <sp:MustSupportRefIssuerSerial />
                          <sp:MustSupportRefThumbprint />
                          <sp:MustSupportRefEncryptedKey />
                        </wsp:Policy>  
                      </sp:Wss11>  
                      <sp:Trust10>  
                        <wsp:Policy>  
                          <sp:MustSupportIssuedTokens />
                          <sp:RequireClientEntropy />
                          <sp:RequireServerEntropy />
                        </wsp:Policy>  
                      </sp:Trust10>  
                    </wsp:Policy>  
                  </sp:BootstrapPolicy>  
                </wsp:Policy>  
              </sp:SecureConversationToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />
          <sp:EncryptSignature />
          <sp:OnlySignEntireHeadersAndBody />
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />
          <sp:MustSupportRefIssuerSerial />
          <sp:MustSupportRefThumbprint />
          <sp:MustSupportRefEncryptedKey />
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />
          <sp:RequireClientEntropy />
          <sp:RequireServerEntropy />
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="ef812-583">Güvenlik Üstbilgi Örnekleri: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="ef812-583">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="ef812-584">İstek</span><span class="sxs-lookup"><span data-stu-id="ef812-584">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="ef812-585">Yanıt</span><span class="sxs-lookup"><span data-stu-id="ef812-585">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="ef812-586">Güvenlik Üstbilgi Örnekleri: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="ef812-586">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="ef812-587">İstek</span><span class="sxs-lookup"><span data-stu-id="ef812-587">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="ef812-588">Yanıt</span><span class="sxs-lookup"><span data-stu-id="ef812-588">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```

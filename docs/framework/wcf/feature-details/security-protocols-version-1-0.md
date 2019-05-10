---
title: Güvenlik Protokolleri sürüm 1.0
ms.date: 03/30/2017
ms.assetid: ee3402d2-1076-410b-a3cb-fae0372bd7af
ms.openlocfilehash: 8114183109befcb77c3bf2b35fe246118da5afde
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64586883"
---
# <a name="security-protocols-version-10"></a><span data-ttu-id="99146-102">Güvenlik Protokolleri sürüm 1.0</span><span class="sxs-lookup"><span data-stu-id="99146-102">Security Protocols version 1.0</span></span>
<span data-ttu-id="99146-103">Web Hizmetleri Güvenlik protokollerini tüm var olan Kurumsal güvenlik gereksinimlerini Mesajlaşma kapsayan Web Hizmetleri güvenlik mekanizmaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="99146-103">The Web Services Security Protocols provide Web services security mechanisms that cover all existing enterprise messaging security requirements.</span></span> <span data-ttu-id="99146-104">Bu bölümde Windows Communication Foundation (WCF) sürüm 1.0 ayrıntılarını açıklar (uygulanan <xref:System.ServiceModel.Channels.SecurityBindingElement>) güvenlik protokollerini aşağıdaki Web Hizmetleri için.</span><span class="sxs-lookup"><span data-stu-id="99146-104">This section describes the Windows Communication Foundation (WCF) version 1.0 details (implemented in the <xref:System.ServiceModel.Channels.SecurityBindingElement>) for the following Web services security protocols.</span></span>  
  
|<span data-ttu-id="99146-105">Belirtimi/belge</span><span class="sxs-lookup"><span data-stu-id="99146-105">Specification/Document</span></span>|<span data-ttu-id="99146-106">Bağlantı</span><span class="sxs-lookup"><span data-stu-id="99146-106">Link</span></span>|  
|-|-|  
|<span data-ttu-id="99146-107">WSS: SOAP ileti güvenliği 1.0</span><span class="sxs-lookup"><span data-stu-id="99146-107">WSS: SOAP Message Security 1.0</span></span>|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf>|
|<span data-ttu-id="99146-108">WSS: Kullanıcı adı belirteci profili 1.0</span><span class="sxs-lookup"><span data-stu-id="99146-108">WSS: Username Token Profile 1.0</span></span>|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf>|
|<span data-ttu-id="99146-109">WSS: Profil 1.0 X509 belirteç</span><span class="sxs-lookup"><span data-stu-id="99146-109">WSS: X509 Token Profile 1.0</span></span>|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0.pdf>|
|<span data-ttu-id="99146-110">WSS: SAML 1.1 belirteç profili 1.0</span><span class="sxs-lookup"><span data-stu-id="99146-110">WSS: SAML 1.1 Token Profile 1.0</span></span>|<https://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.0.pdf>|
|<span data-ttu-id="99146-111">WSS: SOAP ileti güvenliği 1.1</span><span class="sxs-lookup"><span data-stu-id="99146-111">WSS: SOAP Message Security 1.1</span></span>|<https://www.oasis-open.org/committees/download.php/16790/wss-v1.1-spec-os-SOAPMessageSecurity.pdf>|
|<span data-ttu-id="99146-112">WSS kullanıcı adı belirteci Profil 1.1</span><span class="sxs-lookup"><span data-stu-id="99146-112">WSS Username Token Profile 1.1</span></span>|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf>|
|<span data-ttu-id="99146-113">WSS: X.509 belirteci Profil 1.1</span><span class="sxs-lookup"><span data-stu-id="99146-113">WSS: X.509 Token Profile 1.1</span></span>|<https://www.oasis-open.org/committees/download.php/16785/wss-v1.1-spec-os-x509TokenProfile.pdf>|
|<span data-ttu-id="99146-114">WSS: Kerberos belirteci Profil 1.1</span><span class="sxs-lookup"><span data-stu-id="99146-114">WSS: Kerberos Token Profile 1.1</span></span>|<https://www.oasis-open.org/committees/download.php/16788/wss-v1.1-spec-os-KerberosTokenProfile.pdf>|
|<span data-ttu-id="99146-115">WSS: SAML 1.1 belirteç Profil 1.1</span><span class="sxs-lookup"><span data-stu-id="99146-115">WSS: SAML 1.1 Token Profile 1.1</span></span>|<https://www.oasis-open.org/committees/download.php/16768/wss-v1.1-spec-os-SAMLTokenProfile.pdf>|
|<span data-ttu-id="99146-116">WS-Secure Conversation</span><span class="sxs-lookup"><span data-stu-id="99146-116">WS-Secure Conversation</span></span>|<http://specs.xmlsoap.org/ws/2005/02/sc/WS-SecureConversation.pdf>|
|<span data-ttu-id="99146-117">WS-Güven</span><span class="sxs-lookup"><span data-stu-id="99146-117">WS-Trust</span></span>|<http://specs.xmlsoap.org/ws/2005/02/trust/ws-trust.pdf>|
|<span data-ttu-id="99146-118">Uygulama Not:</span><span class="sxs-lookup"><span data-stu-id="99146-118">Application Note:</span></span><br /><br /> <span data-ttu-id="99146-119">WS-Trust TLS el sıkışma için kullanma</span><span class="sxs-lookup"><span data-stu-id="99146-119">Using WS-Trust for TLS Handshake</span></span>|<span data-ttu-id="99146-120">Yayımlanacak</span><span class="sxs-lookup"><span data-stu-id="99146-120">To be published</span></span>|  
|<span data-ttu-id="99146-121">Uygulama Not:</span><span class="sxs-lookup"><span data-stu-id="99146-121">Application Note:</span></span><br /><br /> <span data-ttu-id="99146-122">WS-Trust SPNEGO için kullanma</span><span class="sxs-lookup"><span data-stu-id="99146-122">Using WS-Trust for SPNEGO</span></span>|<span data-ttu-id="99146-123">Yayımlanacak</span><span class="sxs-lookup"><span data-stu-id="99146-123">To be published</span></span>|  
|<span data-ttu-id="99146-124">Uygulama Not:</span><span class="sxs-lookup"><span data-stu-id="99146-124">Application Note:</span></span><br /><br /> <span data-ttu-id="99146-125">Web uç noktası başvuruları adresleme ve kimlik Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="99146-125">Web Services Addressing Endpoint References And Identity</span></span>|<span data-ttu-id="99146-126">Yayımlanacak</span><span class="sxs-lookup"><span data-stu-id="99146-126">To be published</span></span>|  
|<span data-ttu-id="99146-127">WS-SecurityPolicy 1.1</span><span class="sxs-lookup"><span data-stu-id="99146-127">WS-SecurityPolicy 1.1</span></span><br /><br /> <span data-ttu-id="99146-128">(2005/07)</span><span class="sxs-lookup"><span data-stu-id="99146-128">(2005/07)</span></span>|<http://specs.xmlsoap.org/ws/2005/07/securitypolicy/ws-securitypolicy.pdf><br /><br /> <span data-ttu-id="99146-129">tarafından düzeltilir gibi [errata](https://lists.oasis-open.org/archives/ws-sx/200512/msg00017.html) OASIS WS-SX teknik komitesi gönderildi</span><span class="sxs-lookup"><span data-stu-id="99146-129">as amended by [errata](https://lists.oasis-open.org/archives/ws-sx/200512/msg00017.html) submitted to OASIS WS-SX Technical Committee</span></span> |  
  
 <span data-ttu-id="99146-130">WCF, sürüm 1, Web Hizmetleri güvenlik yapılandırması için temel olarak kullanılabilecek 17 kimlik doğrulama modları sağlar.</span><span class="sxs-lookup"><span data-stu-id="99146-130">WCF, version 1, provides 17 authentication modes that can be used as the basis for Web services security configuration.</span></span> <span data-ttu-id="99146-131">Her modu gibi dağıtım gereksinimleri, ortak bir dizi için optimize edilmiştir:</span><span class="sxs-lookup"><span data-stu-id="99146-131">Each mode is optimized for a common set of deployment requirements, such as:</span></span>  
  
- <span data-ttu-id="99146-132">Hizmet ve istemci kimlik doğrulaması için kullanılan kimlik bilgileri.</span><span class="sxs-lookup"><span data-stu-id="99146-132">Credentials used to authenticate client and service.</span></span>  
  
- <span data-ttu-id="99146-133">İleti veya aktarım güvenlik koruma mekanizması.</span><span class="sxs-lookup"><span data-stu-id="99146-133">Message or transport security protection mechanisms.</span></span>  
  
- <span data-ttu-id="99146-134">İleti exchange desenleri.</span><span class="sxs-lookup"><span data-stu-id="99146-134">Message exchange patterns.</span></span>  
  
|<span data-ttu-id="99146-135">Kimlik doğrulama modu</span><span class="sxs-lookup"><span data-stu-id="99146-135">Authentication Mode</span></span>|<span data-ttu-id="99146-136">İstemci kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="99146-136">Client Authentication</span></span>|<span data-ttu-id="99146-137">Sunucu kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="99146-137">Server Authentication</span></span>|<span data-ttu-id="99146-138">Mod</span><span class="sxs-lookup"><span data-stu-id="99146-138">Mode</span></span>|  
|-------------------------|---------------------------|---------------------------|----------|  
|<span data-ttu-id="99146-139">UserNameOverTransport</span><span class="sxs-lookup"><span data-stu-id="99146-139">UserNameOverTransport</span></span>|<span data-ttu-id="99146-140">Kullanıcı adı/parola</span><span class="sxs-lookup"><span data-stu-id="99146-140">User name/password</span></span>|<span data-ttu-id="99146-141">X509</span><span class="sxs-lookup"><span data-stu-id="99146-141">X509</span></span>|<span data-ttu-id="99146-142">Taşıma</span><span class="sxs-lookup"><span data-stu-id="99146-142">Transport</span></span>|  
|<span data-ttu-id="99146-143">CertificateOverTransport</span><span class="sxs-lookup"><span data-stu-id="99146-143">CertificateOverTransport</span></span>|<span data-ttu-id="99146-144">X509</span><span class="sxs-lookup"><span data-stu-id="99146-144">X509</span></span>|<span data-ttu-id="99146-145">X509</span><span class="sxs-lookup"><span data-stu-id="99146-145">X509</span></span>|<span data-ttu-id="99146-146">Taşıma</span><span class="sxs-lookup"><span data-stu-id="99146-146">Transport</span></span>|  
|<span data-ttu-id="99146-147">KerberosOverTransport</span><span class="sxs-lookup"><span data-stu-id="99146-147">KerberosOverTransport</span></span>|<span data-ttu-id="99146-148">Windows</span><span class="sxs-lookup"><span data-stu-id="99146-148">Windows</span></span>|<span data-ttu-id="99146-149">X509</span><span class="sxs-lookup"><span data-stu-id="99146-149">X509</span></span>|<span data-ttu-id="99146-150">Taşıma</span><span class="sxs-lookup"><span data-stu-id="99146-150">Transport</span></span>|  
|<span data-ttu-id="99146-151">IssuedTokenOverTransport</span><span class="sxs-lookup"><span data-stu-id="99146-151">IssuedTokenOverTransport</span></span>|<span data-ttu-id="99146-152">Federasyon</span><span class="sxs-lookup"><span data-stu-id="99146-152">Federated</span></span>|<span data-ttu-id="99146-153">X509</span><span class="sxs-lookup"><span data-stu-id="99146-153">X509</span></span>|<span data-ttu-id="99146-154">Taşıma</span><span class="sxs-lookup"><span data-stu-id="99146-154">Transport</span></span>|  
|<span data-ttu-id="99146-155">SspiNegotiatedOverTransport</span><span class="sxs-lookup"><span data-stu-id="99146-155">SspiNegotiatedOverTransport</span></span>|<span data-ttu-id="99146-156">Windows SSPI anlaşması</span><span class="sxs-lookup"><span data-stu-id="99146-156">Windows Sspi Negotiated</span></span>|<span data-ttu-id="99146-157">Windows SSPI anlaşması</span><span class="sxs-lookup"><span data-stu-id="99146-157">Windows Sspi Negotiated</span></span>|<span data-ttu-id="99146-158">Taşıma</span><span class="sxs-lookup"><span data-stu-id="99146-158">Transport</span></span>|  
|<span data-ttu-id="99146-159">AnonymousForCertificate</span><span class="sxs-lookup"><span data-stu-id="99146-159">AnonymousForCertificate</span></span>|<span data-ttu-id="99146-160">None</span><span class="sxs-lookup"><span data-stu-id="99146-160">None</span></span>|<span data-ttu-id="99146-161">X509</span><span class="sxs-lookup"><span data-stu-id="99146-161">X509</span></span>|<span data-ttu-id="99146-162">`Message`</span><span class="sxs-lookup"><span data-stu-id="99146-162">Message</span></span>|  
|<span data-ttu-id="99146-163">UserNameForCertificate</span><span class="sxs-lookup"><span data-stu-id="99146-163">UserNameForCertificate</span></span>|<span data-ttu-id="99146-164">Kullanıcı adı/parola</span><span class="sxs-lookup"><span data-stu-id="99146-164">User name/password</span></span>|<span data-ttu-id="99146-165">X509</span><span class="sxs-lookup"><span data-stu-id="99146-165">X509</span></span>|<span data-ttu-id="99146-166">`Message`</span><span class="sxs-lookup"><span data-stu-id="99146-166">Message</span></span>|  
|<span data-ttu-id="99146-167">MutualCertificate</span><span class="sxs-lookup"><span data-stu-id="99146-167">MutualCertificate</span></span>|<span data-ttu-id="99146-168">X509</span><span class="sxs-lookup"><span data-stu-id="99146-168">X509</span></span>|<span data-ttu-id="99146-169">X509</span><span class="sxs-lookup"><span data-stu-id="99146-169">X509</span></span>|<span data-ttu-id="99146-170">`Message`</span><span class="sxs-lookup"><span data-stu-id="99146-170">Message</span></span>|  
|<span data-ttu-id="99146-171">MutualCertificateDuplex</span><span class="sxs-lookup"><span data-stu-id="99146-171">MutualCertificateDuplex</span></span>|<span data-ttu-id="99146-172">X509</span><span class="sxs-lookup"><span data-stu-id="99146-172">X509</span></span>|<span data-ttu-id="99146-173">X509</span><span class="sxs-lookup"><span data-stu-id="99146-173">X509</span></span>|<span data-ttu-id="99146-174">`Message`</span><span class="sxs-lookup"><span data-stu-id="99146-174">Message</span></span>|  
|<span data-ttu-id="99146-175">IssuedTokenForCertificate</span><span class="sxs-lookup"><span data-stu-id="99146-175">IssuedTokenForCertificate</span></span>|<span data-ttu-id="99146-176">Federasyon</span><span class="sxs-lookup"><span data-stu-id="99146-176">Federated</span></span>|<span data-ttu-id="99146-177">X509</span><span class="sxs-lookup"><span data-stu-id="99146-177">X509</span></span>|<span data-ttu-id="99146-178">`Message`</span><span class="sxs-lookup"><span data-stu-id="99146-178">Message</span></span>|  
|<span data-ttu-id="99146-179">Kerberos</span><span class="sxs-lookup"><span data-stu-id="99146-179">Kerberos</span></span>|<span data-ttu-id="99146-180">Windows</span><span class="sxs-lookup"><span data-stu-id="99146-180">Windows</span></span>|<span data-ttu-id="99146-181">Windows</span><span class="sxs-lookup"><span data-stu-id="99146-181">Windows</span></span>|<span data-ttu-id="99146-182">`Message`</span><span class="sxs-lookup"><span data-stu-id="99146-182">Message</span></span>|  
|<span data-ttu-id="99146-183">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="99146-183">IssuedToken</span></span>|<span data-ttu-id="99146-184">Federasyon</span><span class="sxs-lookup"><span data-stu-id="99146-184">Federated</span></span>|<span data-ttu-id="99146-185">Federasyon</span><span class="sxs-lookup"><span data-stu-id="99146-185">Federated</span></span>|<span data-ttu-id="99146-186">`Message`</span><span class="sxs-lookup"><span data-stu-id="99146-186">Message</span></span>|  
|<span data-ttu-id="99146-187">SspiNegotiated</span><span class="sxs-lookup"><span data-stu-id="99146-187">SspiNegotiated</span></span>|<span data-ttu-id="99146-188">Windows SSPI anlaşması</span><span class="sxs-lookup"><span data-stu-id="99146-188">Windows Sspi Negotiated</span></span>|<span data-ttu-id="99146-189">Windows SSPI anlaşması</span><span class="sxs-lookup"><span data-stu-id="99146-189">Windows Sspi Negotiated</span></span>|<span data-ttu-id="99146-190">`Message`</span><span class="sxs-lookup"><span data-stu-id="99146-190">Message</span></span>|  
|<span data-ttu-id="99146-191">AnonymousForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="99146-191">AnonymousForSslNegotiated</span></span>|<span data-ttu-id="99146-192">None</span><span class="sxs-lookup"><span data-stu-id="99146-192">None</span></span>|<span data-ttu-id="99146-193">X509, TLS-Nego</span><span class="sxs-lookup"><span data-stu-id="99146-193">X509, TLS-Nego</span></span>|<span data-ttu-id="99146-194">`Message`</span><span class="sxs-lookup"><span data-stu-id="99146-194">Message</span></span>|  
|<span data-ttu-id="99146-195">UserNameForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="99146-195">UserNameForSslNegotiated</span></span>|<span data-ttu-id="99146-196">Kullanıcı adı/parola</span><span class="sxs-lookup"><span data-stu-id="99146-196">User name/password</span></span>|<span data-ttu-id="99146-197">X509, TLS-Nego</span><span class="sxs-lookup"><span data-stu-id="99146-197">X509, TLS-Nego</span></span>|<span data-ttu-id="99146-198">`Message`</span><span class="sxs-lookup"><span data-stu-id="99146-198">Message</span></span>|  
|<span data-ttu-id="99146-199">MutualSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="99146-199">MutualSslNegotiated</span></span>|<span data-ttu-id="99146-200">X509</span><span class="sxs-lookup"><span data-stu-id="99146-200">X509</span></span>|<span data-ttu-id="99146-201">X509, TLS-Nego</span><span class="sxs-lookup"><span data-stu-id="99146-201">X509, TLS-Nego</span></span>|<span data-ttu-id="99146-202">`Message`</span><span class="sxs-lookup"><span data-stu-id="99146-202">Message</span></span>|  
|<span data-ttu-id="99146-203">IssuedTokenForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="99146-203">IssuedTokenForSslNegotiated</span></span>|<span data-ttu-id="99146-204">Federasyon</span><span class="sxs-lookup"><span data-stu-id="99146-204">Federated</span></span>|<span data-ttu-id="99146-205">X509, TLS-Nego</span><span class="sxs-lookup"><span data-stu-id="99146-205">X509, TLS-Nego</span></span>|<span data-ttu-id="99146-206">`Message`</span><span class="sxs-lookup"><span data-stu-id="99146-206">Message</span></span>|  
  
 <span data-ttu-id="99146-207">Bu tür bir kimlik doğrulama modları kullanarak uç noktaları, WS-SecurityPolicy (WS-SP) kullanarak kendi güvenlik gereksinimleri ifade edebilir.</span><span class="sxs-lookup"><span data-stu-id="99146-207">Endpoints using such authentication modes can express their security requirements using WS-SecurityPolicy (WS-SP).</span></span> <span data-ttu-id="99146-208">Bu belge, güvenlik üstbilgi ve her kimlik doğrulama modu için altyapı iletileri yapısını açıklar ve ilkeleri ve iletileri örneklerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="99146-208">This document describes the structure of security header and infrastructure messages for each authentication mode and provides examples of policies and messages.</span></span>  
  
 <span data-ttu-id="99146-209">Güvenli oturumlar uygulamalar arasında çok ileti iletişimlerini korumak için destek sağlamak için WS-SecureConversation WCF yararlanır.</span><span class="sxs-lookup"><span data-stu-id="99146-209">WCF leverages WS-SecureConversation to provide secure sessions support to protect multi-message exchanges between applications.</span></span>  <span data-ttu-id="99146-210">"Güvenli oturumlar" aşağıdaki uygulama ayrıntıları için bkz.</span><span class="sxs-lookup"><span data-stu-id="99146-210">See "Secure Sessions" below for implementation details.</span></span>  
  
 <span data-ttu-id="99146-211">Kimlik doğrulama modları yanı sıra WCF çoğu ileti güvenlik tabanlı kimlik doğrulama modları, örneğin geçerli genel koruma mekanizması denetleyen ayarları sağlar: İmza ve şifreleme işlemleri, algoritma paketleri, anahtar türetme sırası ve imza onayı.</span><span class="sxs-lookup"><span data-stu-id="99146-211">In addition to authentication modes, WCF provides settings to control common protection mechanisms that apply to most message security-based authentication modes, for example: order of signature versus encryption operations, algorithm suites, key derivation, and signature confirmation.</span></span>  
  
 <span data-ttu-id="99146-212">Bu belgede, aşağıdaki ön ekleri ve ad alanları kullanılır.</span><span class="sxs-lookup"><span data-stu-id="99146-212">The following prefixes and namespaces are used in this document.</span></span>  
  
|<span data-ttu-id="99146-213">Ön eki</span><span class="sxs-lookup"><span data-stu-id="99146-213">Prefix</span></span>|<span data-ttu-id="99146-214">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="99146-214">Namespace</span></span>|  
|------------|---------------|  
|<span data-ttu-id="99146-215">s</span><span class="sxs-lookup"><span data-stu-id="99146-215">s</span></span>|<https://www.w3.org/2003/05/soap-envelope/>|
|<span data-ttu-id="99146-216">SP</span><span class="sxs-lookup"><span data-stu-id="99146-216">sp</span></span>|<http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/>|
|<span data-ttu-id="99146-217">a</span><span class="sxs-lookup"><span data-stu-id="99146-217">a</span></span>|<https://www.w3.org/2005/08/addressing>|  
|<span data-ttu-id="99146-218">wsse</span><span class="sxs-lookup"><span data-stu-id="99146-218">wsse</span></span>|<span data-ttu-id="99146-219">TBD – OASIS WSS 1.0 URI'Sİ</span><span class="sxs-lookup"><span data-stu-id="99146-219">TBD – OASIS WSS 1.0 URI</span></span>|  
|<span data-ttu-id="99146-220">wsse11</span><span class="sxs-lookup"><span data-stu-id="99146-220">wsse11</span></span>|<span data-ttu-id="99146-221">TBD – OASIS WSS 1.1 URI'Sİ</span><span class="sxs-lookup"><span data-stu-id="99146-221">TBD – OASIS WSS 1.1 URI</span></span>|  
|<span data-ttu-id="99146-222">wsu</span><span class="sxs-lookup"><span data-stu-id="99146-222">wsu</span></span>|<span data-ttu-id="99146-223">TBD – OASIS WSS 1.0 yardımcı programı URI'si</span><span class="sxs-lookup"><span data-stu-id="99146-223">TBD – OASIS WSS 1.0 Utility URI</span></span>|  
|<span data-ttu-id="99146-224">DS</span><span class="sxs-lookup"><span data-stu-id="99146-224">ds</span></span>|<span data-ttu-id="99146-225">TBD – W3C XMLDSig URI'si</span><span class="sxs-lookup"><span data-stu-id="99146-225">TBD – W3C XMLDSig URI</span></span>|  
|<span data-ttu-id="99146-226">WST</span><span class="sxs-lookup"><span data-stu-id="99146-226">wst</span></span>|<span data-ttu-id="99146-227">TBD – WS-Trust 2005/02 URI'si</span><span class="sxs-lookup"><span data-stu-id="99146-227">TBD – WS-Trust 2005/02 URI</span></span>|  
|<span data-ttu-id="99146-228">wssc</span><span class="sxs-lookup"><span data-stu-id="99146-228">wssc</span></span>|<span data-ttu-id="99146-229">TBD – WS-SecureConversation 2005/02 URI'si</span><span class="sxs-lookup"><span data-stu-id="99146-229">TBD – WS-SecureConversation 2005/02 URI</span></span>|  
|<span data-ttu-id="99146-230">wsaw</span><span class="sxs-lookup"><span data-stu-id="99146-230">wsaw</span></span>|<span data-ttu-id="99146-231">TBD - WS-Addressing policy ad alanı</span><span class="sxs-lookup"><span data-stu-id="99146-231">TBD - WS-Addressing policy namespace</span></span>|  
|<span data-ttu-id="99146-232">WSP</span><span class="sxs-lookup"><span data-stu-id="99146-232">wsp</span></span>|<http://schemas.xmlsoap.org/ws/2004/09/policy>|  
|<span data-ttu-id="99146-233">mssp</span><span class="sxs-lookup"><span data-stu-id="99146-233">mssp</span></span>|<http://schemas.xmlsoap.org/ws/2005/07/securitypolicy>|
  
## <a name="1-token-profiles"></a><span data-ttu-id="99146-234">1. Belirteç profilleri</span><span class="sxs-lookup"><span data-stu-id="99146-234">1. Token Profiles</span></span>  
 <span data-ttu-id="99146-235">Web Hizmetleri Güvenlik belirtimleri kimlik bilgisi güvenlik belirteçleri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="99146-235">Web Services Security specifications represent credential as security tokens.</span></span> <span data-ttu-id="99146-236">WCF aşağıdaki belirteç türlerini destekler:</span><span class="sxs-lookup"><span data-stu-id="99146-236">WCF supports the following token types:</span></span>  
  
### <a name="11-usernametoken"></a><span data-ttu-id="99146-237">1.1 UsernameToken</span><span class="sxs-lookup"><span data-stu-id="99146-237">1.1 UsernameToken</span></span>  
 <span data-ttu-id="99146-238">WCF UsernameToken10 ve UsernameToken11 profilleriyle aşağıdaki kısıtlamaları aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="99146-238">WCF follows UsernameToken10 and UsernameToken11 profiles with the following constraints:</span></span>  
  
 <span data-ttu-id="99146-239">UsernameToken\Password öğesindeki R1101 PasswordType özniteliği ya da atlanmış olabilir veya #PasswordText (varsayılan) bir değer olamaz.</span><span class="sxs-lookup"><span data-stu-id="99146-239">R1101 PasswordType attribute on UsernameToken\Password element MUST be either omitted or have value #PasswordText (default).</span></span>  
  
 <span data-ttu-id="99146-240">Bir genişletilebilirlik kullanarak #PasswordDigest uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99146-240">One can implement the #PasswordDigest using extensibility.</span></span> <span data-ttu-id="99146-241">Yeterince güvenli parola koruma mekanizması olarak #PasswordDigest genellikle mistaken gözlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="99146-241">It has been observed that #PasswordDigest was often mistaken to be a secure enough password protection mechanism.</span></span> <span data-ttu-id="99146-242">Ancak #PasswordDigest UsernameToken şifrelenmesi için bir alternatif olarak hizmet veremez.</span><span class="sxs-lookup"><span data-stu-id="99146-242">But #PasswordDigest cannot serve as a substitute for encryption of the UsernameToken.</span></span> <span data-ttu-id="99146-243">#PasswordDigest birincil amacı yeniden yürütme saldırılarına karşı bir korumadır.</span><span class="sxs-lookup"><span data-stu-id="99146-243">The primary goal of #PasswordDigest is protection against replay attacks.</span></span> <span data-ttu-id="99146-244">WCF kimlik doğrulama modları ileti imzalarını kullanarak yeniden yürütme saldırı tehditlerine azalır.</span><span class="sxs-lookup"><span data-stu-id="99146-244">In WCF authentication modes, replay attack threats are mitigated by using message signatures.</span></span>  
  
 <span data-ttu-id="99146-245">B1102 WCF UsernameToken Nonce ve oluşturulan alt öğeleri hiçbir zaman yayar.</span><span class="sxs-lookup"><span data-stu-id="99146-245">B1102 WCF never emits Nonce and Created sub-elements of the UsernameToken.</span></span>  
  
 <span data-ttu-id="99146-246">Bu alt öğeleri yeniden yürütme algılaması yardımcı olmak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="99146-246">These sub-elements are intended to help replay detection.</span></span> <span data-ttu-id="99146-247">Bunun yerine, WCF ileti imzalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="99146-247">WCF uses message signatures instead.</span></span>  
  
 <span data-ttu-id="99146-248">OASIS WSS SOAP ileti güvenlik UsernameToken Profile 1.1 (UsernameToken11) anahtar türetme parola özelliğini kullanıma sunmuştur.</span><span class="sxs-lookup"><span data-stu-id="99146-248">OASIS WSS SOAP Message Security UsernameToken Profile 1.1 (UsernameToken11) introduced key derivation from password feature.</span></span>  
  
 <span data-ttu-id="99146-249">B1103 UsernameToken parola için anahtar türetme değil kullanılmalıdır ve bu nedenle şifreleme işlemleri için.</span><span class="sxs-lookup"><span data-stu-id="99146-249">B1103 UsernameToken password MUST not be used for key derivation and therefore for cryptographic operations.</span></span>  
  
 <span data-ttu-id="99146-250">Stratejinin: parolaları genel şifreleme işlemleri için kullanılacak zayıf olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="99146-250">Rationale: passwords are generally considered too weak to be used for cryptographic operations.</span></span>  
  
### <a name="12-x509-token"></a><span data-ttu-id="99146-251">1.2 X509 Token</span><span class="sxs-lookup"><span data-stu-id="99146-251">1.2 X509 Token</span></span>  
 <span data-ttu-id="99146-252">WCF X509v3 sertifikalarını bir kimlik bilgisi türü olarak destekler ve aşağıdaki kısıtlamalarla X509TokenProfile1.0 ve X509TokenProfile1.1 izler:</span><span class="sxs-lookup"><span data-stu-id="99146-252">WCF supports X509v3 certificates as a credential type and follows X509TokenProfile1.0 and X509TokenProfile1.1 with the following constraints:</span></span>  
  
 <span data-ttu-id="99146-253">X509v3 sertifika içerdiğinde BinarySecurityToken öğesindeki R1201 ValueType özniteliği değeri #X509v3 olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="99146-253">R1201 The ValueType attribute on the BinarySecurityToken element must have value #X509v3 when it contains an X509v3 certificate.</span></span>  
  
 <span data-ttu-id="99146-254">Değer türleri WSS X509 da belirteci profili 1.0 ve 1.1 #X509PKIPathv1 ve #PKCS7 olarak tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="99146-254">WSS X509 Token Profile 1.0 and 1.1 define also #X509PKIPathv1 and #PKCS7 as value types.</span></span> <span data-ttu-id="99146-255">WCF bu türleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="99146-255">WCF does not support these types.</span></span>  
  
 <span data-ttu-id="99146-256">R1202 SubjectKeyIdentifier (KAYAK) uzantı ise x X509 içinde mevcut sertifika wsse:KeyIdentifier olmalıdır belirtecine dış başvurular için kullanılan, ValueType ile #X509SubjectKeyIdentifier ve içeriğini base64 ile kodlanmış, öznitelik değeri Sertifikanın KAYAK uzantısı.</span><span class="sxs-lookup"><span data-stu-id="99146-256">R1202 If a SubjectKeyIdentifier (SKI) extension is present in an X509 certificate, wsse:KeyIdentifier should be used for external references to the token, with the ValueType attribute as #X509SubjectKeyIdentifier and its content the base64-encoded value of certificate's SKI extension.</span></span>  
  
 <span data-ttu-id="99146-257">KAYAK başvuruları yaygın olarak uygulanan ve kendini kanıtlamış bir yüksek düzeyde birlikte çalışabilen bir dış başvuru türü olması.</span><span class="sxs-lookup"><span data-stu-id="99146-257">SKI references are widely implemented and proven to be a highly interoperable external reference type.</span></span>  
  
 <span data-ttu-id="99146-258">R1203 Dış başvuru X509 için güvenlik belirteci olmamalıdır ds:X509IssuerSerial'ı kullanın.</span><span class="sxs-lookup"><span data-stu-id="99146-258">R1203 An external Reference to X509 Security Token SHOULD NOT use ds:X509IssuerSerial.</span></span>  
  
 <span data-ttu-id="99146-259">R1204 varsa X509TokenProfile1.1, bir dış başvuru X509 güvenlik belirteci kullanmalıdır WS-güvenlik 1.1 tarafından sunulan parmak izi için kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="99146-259">R1204 If X509TokenProfile1.1 is in use, an external reference to X509 Security Token SHOULD use the thumbprint introduced by WS-Security 1.1.</span></span>  
  
 <span data-ttu-id="99146-260">WCF X509IssuerSerial destekler.</span><span class="sxs-lookup"><span data-stu-id="99146-260">WCF supports X509IssuerSerial.</span></span> <span data-ttu-id="99146-261">Ancak X509IssuerSerial ile birlikte çalışabilirlik sorunları vardır: WCF X509IssuerSerial iki değerlerini karşılaştırmak için bir dize kullanır.</span><span class="sxs-lookup"><span data-stu-id="99146-261">However There are interoperability issues with X509IssuerSerial: WCF uses a string to compare two values of X509IssuerSerial.</span></span> <span data-ttu-id="99146-262">Bir konu adı bileşenleri yeniden sıralar ve bir WCF hizmeti için bir sertifika başvuru gönderir, bu nedenle, bulunamamış olabilir.</span><span class="sxs-lookup"><span data-stu-id="99146-262">Therefore if one reorders components of the Subject Name and sends to an WCF service a reference to a certificate, it may not be found.</span></span>  
  
### <a name="13-kerberos-token"></a><span data-ttu-id="99146-263">1.3 Kerberos belirteci</span><span class="sxs-lookup"><span data-stu-id="99146-263">1.3 Kerberos Token</span></span>  
 <span data-ttu-id="99146-264">WCF KerberosTokenProfile1.1 aşağıdaki kısıtlamaları olan Windows kimlik doğrulaması amacıyla destekler:</span><span class="sxs-lookup"><span data-stu-id="99146-264">WCF supports KerberosTokenProfile1.1 for the purpose of Windows authentication with the following constraints:</span></span>  
  
 <span data-ttu-id="99146-265">R1301 bir Kerberos belirteci gerekir taşıyan bir GSS değerini Kerberos v4 AP_REQ GSS_API Kerberos belirtimi ile tanımlanan sarmalandı ve değer #GSS_Kerberosv5_AP_REQ ValueType özniteliğiyle olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="99146-265">R1301 A Kerberos Token must carry the value of a GSS wrapped Kerberos v4 AP_REQ as defined in GSS_API and the Kerberos specification, and must have the ValueType attribute with the value #GSS_Kerberosv5_AP_REQ.</span></span>  
  
 <span data-ttu-id="99146-266">WCF kullanan GSS Kerberos AP-REQ, olmayan bir çıplak AP-talep sarmalanmış</span><span class="sxs-lookup"><span data-stu-id="99146-266">WCF uses GSS wrapped Kerberos AP-REQ, not a bare AP-REQ.</span></span> <span data-ttu-id="99146-267">Bu bir güvenlik en iyi uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="99146-267">This is a security best practice.</span></span>  
  
### <a name="14-saml-v11-token"></a><span data-ttu-id="99146-268">1.4 SAML v1.1 belirteci</span><span class="sxs-lookup"><span data-stu-id="99146-268">1.4 SAML v1.1 Token</span></span>  
 <span data-ttu-id="99146-269">WCF WSS SAML belirteci profilleri 1.0 ve 1.1 için SAML v1.1 belirteçleri destekler.</span><span class="sxs-lookup"><span data-stu-id="99146-269">WCF supports WSS SAML Token profiles 1.0 and 1.1 for SAML v1.1 tokens.</span></span> <span data-ttu-id="99146-270">SAML belirteci biçimleri'nın diğer sürümlerinin uygulamak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="99146-270">It is possible to implement other versions of SAML token formats.</span></span>  
  
### <a name="15-security-context-token"></a><span data-ttu-id="99146-271">1.5 güvenlik bağlamı belirteci</span><span class="sxs-lookup"><span data-stu-id="99146-271">1.5 Security Context Token</span></span>  
 <span data-ttu-id="99146-272">WCF güvenlik bağlamı belirteci (WS-SecureCoversation sunulan SCT) destekler.</span><span class="sxs-lookup"><span data-stu-id="99146-272">WCF supports the Security Context Token (SCT) introduced in WS-SecureCoversation.</span></span> <span data-ttu-id="99146-273">SCT SecureConversation içinde de oluşturulan bir güvenlik bağlamı temsil etmek için kullanılan ikili anlaşma TLS ve SSPI protokoller olarak aşağıda açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="99146-273">SCT is used to represent a security context established in SecureConversation as well as the binary negotiation protocols TLS and SSPI, described below.</span></span>  
  
## <a name="2-common-message-security-parameters"></a><span data-ttu-id="99146-274">2. Ortak ileti güvenlik parametreleri</span><span class="sxs-lookup"><span data-stu-id="99146-274">2. Common Message Security Parameters</span></span>  
  
### <a name="21-timestamp"></a><span data-ttu-id="99146-275">2.1 zaman damgası</span><span class="sxs-lookup"><span data-stu-id="99146-275">2.1 TimeStamp</span></span>  
 <span data-ttu-id="99146-276">Zaman damgası varlığı kullanılarak denetlenir <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> özelliği <xref:System.ServiceModel.Channels.SecurityBindingElement> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="99146-276">Timestamp presence is controlled using the <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> property of the <xref:System.ServiceModel.Channels.SecurityBindingElement> class.</span></span> <span data-ttu-id="99146-277">WCF wsse:TimeStamp wsse ile her zaman serileştiren: oluşturulan ve wsse: alanları süresi dolar.</span><span class="sxs-lookup"><span data-stu-id="99146-277">WCF always serializes wsse:TimeStamp with wsse:Created and wsse:Expires fields.</span></span> <span data-ttu-id="99146-278">İmzalama kullanıldığında wsse:TimeStamp her zaman imzalanır.</span><span class="sxs-lookup"><span data-stu-id="99146-278">The wsse:TimeStamp is always signed when signing is used.</span></span>  
  
### <a name="22-protection-order"></a><span data-ttu-id="99146-279">2.2 koruma sırası</span><span class="sxs-lookup"><span data-stu-id="99146-279">2.2 Protection Order</span></span>  
 <span data-ttu-id="99146-280">WCF ileti koruma sırası "Önce oturum şifrelemek" ve "Şifrelemek önce oturumu" (Güvenlik İlkesi 1.1) destekler.</span><span class="sxs-lookup"><span data-stu-id="99146-280">WCF supports the message protection order "Sign Before Encrypt" and "Encrypt Before Sign" (Security Policy 1.1).</span></span> <span data-ttu-id="99146-281">"Şifrele önce oturum" gibi nedenlerle önerilir: WS-güvenlik 1.1 SignatureConfirmation mekanizması kullanılır ve imza şifrelenmiş içerik üzerinde yapar sürece iletileri şifrelemek önce oturum ile korunan imza değiştirme saldırılara açık daha sıkı denetim.</span><span class="sxs-lookup"><span data-stu-id="99146-281">"Sign Before Encrypt" is recommended for reasons including: messages protected with Encrypt Before Sign are open to signature substitution attacks unless the WS-Security 1.1 SignatureConfirmation mechanism is used, and a signature over encrypted content makes auditing harder.</span></span>  
  
### <a name="23-signature-protection"></a><span data-ttu-id="99146-282">2.3 imza koruma</span><span class="sxs-lookup"><span data-stu-id="99146-282">2.3 Signature Protection</span></span>  
 <span data-ttu-id="99146-283">Şifreleme önce oturum kullanıldığında, şifrelenmiş içerik veya imzalama anahtarı tahmin için (özellikle özel belirteç zayıf anahtar malzemesi ile kullanıldığında) deneme yanılma saldırıları önlemek için imza korumak için önerilir.</span><span class="sxs-lookup"><span data-stu-id="99146-283">When Encrypt Before Sign is used, it is recommended to protect the signature to prevent brute force attacks for guessing the encrypted content or the signing key (especially when a custom token is used with weak key material).</span></span>  
  
### <a name="24-algorithm-suite"></a><span data-ttu-id="99146-284">2.4 algoritması paketi</span><span class="sxs-lookup"><span data-stu-id="99146-284">2.4 Algorithm Suite</span></span>  
 <span data-ttu-id="99146-285">WCF güvenlik ilkesi 1.1 içinde listelenen tüm algoritması paketlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="99146-285">WCF supports all algorithm suites listed in Security Policy 1.1.</span></span>  
  
### <a name="25-key-derivation"></a><span data-ttu-id="99146-286">2.5 anahtar türetme</span><span class="sxs-lookup"><span data-stu-id="99146-286">2.5 Key Derivation</span></span>  
 <span data-ttu-id="99146-287">WCF "Anahtar türetme simetrik anahtarlar için" WS-SecureConversation açıklandığı gibi kullanır.</span><span class="sxs-lookup"><span data-stu-id="99146-287">WCF uses "Key Derivation for symmetric keys" as described in WS-SecureConversation.</span></span>  
  
### <a name="26-signature-confirmation"></a><span data-ttu-id="99146-288">2.6 imza onayı</span><span class="sxs-lookup"><span data-stu-id="99146-288">2.6 Signature Confirmation</span></span>  
 <span data-ttu-id="99146-289">İmza onayı imzaları kümesini korumak için ortadaki adam saldırılarına karşı koruma olarak olabilir.</span><span class="sxs-lookup"><span data-stu-id="99146-289">Signature confirmation can be as protection from middle man attacks to protect the set of signatures.</span></span>  
  
### <a name="27-security-header-layout"></a><span data-ttu-id="99146-290">2.7 güvenlik üst bilgisi düzeni</span><span class="sxs-lookup"><span data-stu-id="99146-290">2.7 Security Header Layout</span></span>  
 <span data-ttu-id="99146-291">Her kimlik doğrulama modu, güvenlik üst bilgisi için belirli bir düzen açıklar.</span><span class="sxs-lookup"><span data-stu-id="99146-291">Each authentication mode describes a certain layout for the security header.</span></span> <span data-ttu-id="99146-292">Güvenlik üst bilgisi içinde yarı sıralı öğeleridir.</span><span class="sxs-lookup"><span data-stu-id="99146-292">Elements within the security header are semi-ordered.</span></span> <span data-ttu-id="99146-293">Güvenlik üst bilgi alt öğelerin sırasını tanımlamak için aşağıdaki güvenlik üst bilgisi düzeni modları WS-Security Policy tanımlar:</span><span class="sxs-lookup"><span data-stu-id="99146-293">To define the order of security header child elements, WS-Security Policy defines the following security header layout modes:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="99146-294">Katı</span><span class="sxs-lookup"><span data-stu-id="99146-294">Strict</span></span>|<span data-ttu-id="99146-295">Öğeleri "kullanılmadan önce bildirme" ilkesi numaralı düzeni kuralları bölüme 7.7.1 genel göre Güvenlik İlkesi'nde açıklanan güvenlik üst bilgi aşağıdaki eklenir.</span><span class="sxs-lookup"><span data-stu-id="99146-295">Items are added to the security header following the numbered layout rules described in Security Policy section 7.7.1 according to a general principle of "declare before use".</span></span>|  
|<span data-ttu-id="99146-296">Belirsiz</span><span class="sxs-lookup"><span data-stu-id="99146-296">Lax</span></span>|<span data-ttu-id="99146-297">Öğeler için WSS uyan herhangi bir sırada güvenlik üstbilgisinde eklenir: SOAP ileti güvenliği.</span><span class="sxs-lookup"><span data-stu-id="99146-297">Items are added to the security header in any order that conforms to WSS: SOAP Message Security.</span></span>|  
|<span data-ttu-id="99146-298">LaxTimestampFirst</span><span class="sxs-lookup"><span data-stu-id="99146-298">LaxTimestampFirst</span></span>|<span data-ttu-id="99146-299">İlk öğe dışında güvenlik üstbilgisinde Lax bir wsse:Timestamp aynı olmalıdır</span><span class="sxs-lookup"><span data-stu-id="99146-299">Same as Lax except that the first item in the security header must be a wsse:Timestamp</span></span>|  
|<span data-ttu-id="99146-300">LaxTimestampLast</span><span class="sxs-lookup"><span data-stu-id="99146-300">LaxTimestampLast</span></span>|<span data-ttu-id="99146-301">Belirsiz bir wsse:Timestamp güvenlik üst bilgisindeki son öğe olmalıdır dışında aynı</span><span class="sxs-lookup"><span data-stu-id="99146-301">Same as lax except that the last item in the security header must be a wsse:Timestamp</span></span>|  
  
 <span data-ttu-id="99146-302">WCF güvenlik üst bilgisi düzeni için tüm dört modlarını destekler.</span><span class="sxs-lookup"><span data-stu-id="99146-302">WCF supports all four modes for security header layout.</span></span> <span data-ttu-id="99146-303">Güvenlik üst bilgisi yapısı ve ileti örnekleri aşağıdaki kimlik doğrulama modları için "Strict" modu izleyin.</span><span class="sxs-lookup"><span data-stu-id="99146-303">Security header structure and message examples for authentication modes below follow the "Strict" mode.</span></span>  
  
## <a name="2-common-message-security-parameters"></a><span data-ttu-id="99146-304">2. Ortak ileti güvenlik parametreleri</span><span class="sxs-lookup"><span data-stu-id="99146-304">2. Common Message Security Parameters</span></span>  
 <span data-ttu-id="99146-305">Bu bölümde, hizmet ve istemci tarafından alınıp verilen iletileri güvenlik üst bilgisi yapısı gösteren örneklerinin yanı sıra her bir kimlik doğrulama modu örnek ilkeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="99146-305">This section provides example policies for each authentication mode along with examples showing security header structure in messages exchanged by client and service.</span></span>  
  
### <a name="61-transport-protection"></a><span data-ttu-id="99146-306">6.1 taşıma koruma</span><span class="sxs-lookup"><span data-stu-id="99146-306">6.1 Transport Protection</span></span>  
 <span data-ttu-id="99146-307">WCF mesajlarını korumak için güvenli aktarım kullanan beş kimlik doğrulama modları sağlar. UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport ve SspiNegotiatedOverTransport.</span><span class="sxs-lookup"><span data-stu-id="99146-307">WCF provides five authentication modes that use secure transport to protect messages; UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport and SspiNegotiatedOverTransport.</span></span>  
  
 <span data-ttu-id="99146-308">Bu kimlik doğrulama modları SecurityPolicy içinde açıklanan aktarım bağlama kullanılarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="99146-308">These authentication modes are constructed using the transport binding described in SecurityPolicy.</span></span> <span data-ttu-id="99146-309">UserNameOverTransport için kimlik doğrulama modu UsernameToken imzalı destekleme belirteci ' dir.</span><span class="sxs-lookup"><span data-stu-id="99146-309">For the UserNameOverTransport authentication mode the UsernameToken is a signed supporting token.</span></span> <span data-ttu-id="99146-310">Bir kimlik doğrulama modları için belirteç imzalı ve onaylanan bir belirteç görünür.</span><span class="sxs-lookup"><span data-stu-id="99146-310">For the other authentication modes the token appears as a signed endorsing token.</span></span> <span data-ttu-id="99146-311">Ek C.1.2 ve C.1.3, SecurityPolicy ayrıntılı güvenlik üst bilgisi düzeni açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="99146-311">Appendix C.1.2 and C.1.3 of SecurityPolicy describe the security header layout in detail.</span></span> <span data-ttu-id="99146-312">Aşağıdaki örnekte güvenlik üst bilgileri bir belirli kimlik doğrulama modu katı düzenini gösterir.</span><span class="sxs-lookup"><span data-stu-id="99146-312">The following example security headers show the Strict layout for a given authentication mode.</span></span>  
  
 <span data-ttu-id="99146-313">Tüm durumlarda belirteçleri "Türetilmiş anahtarları" özelliği "false" değeridir.</span><span class="sxs-lookup"><span data-stu-id="99146-313">The value of the "Derived Keys" property for the tokens in all cases is "false".</span></span>  
  
 <span data-ttu-id="99146-314">Aktarım bağlama çeşitli özelliklerin değerlerini aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="99146-314">The values of the various properties of the transport binding are as follows:</span></span>  
  
 <span data-ttu-id="99146-315">Zaman damgası: true</span><span class="sxs-lookup"><span data-stu-id="99146-315">Timestamp: true</span></span>  
  
 <span data-ttu-id="99146-316">Güvenlik üst bilgisi düzeni: Katı</span><span class="sxs-lookup"><span data-stu-id="99146-316">Security Header Layout: Strict</span></span>  
  
 <span data-ttu-id="99146-317">Algoritma paketi: Basic256</span><span class="sxs-lookup"><span data-stu-id="99146-317">Algorithm Suite: Basic256</span></span>  
  
#### <a name="611-usernameovertransport"></a><span data-ttu-id="99146-318">6.1.1 UsernameOverTransport</span><span class="sxs-lookup"><span data-stu-id="99146-318">6.1.1 UsernameOverTransport</span></span>  
 <span data-ttu-id="99146-319">Bu kimlik doğrulama modu SOAP katmanında başlatıcıdan alıcının her zaman gönderilen imzalı destekleme belirteci olarak görüntülenen bir kullanıcı adı belirteci ile istemci kimliğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="99146-319">With this authentication mode, the client authenticates with a Username Token which appears at the SOAP layer as a signed supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="99146-320">Aktarım katmanında bir X.509 sertifikası kullanarak hizmet kimlik doğrulaması yapılır.</span><span class="sxs-lookup"><span data-stu-id="99146-320">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="99146-321">Kullanılan bağlama aktarım bağlama ' dir.</span><span class="sxs-lookup"><span data-stu-id="99146-321">The binding used is a transport binding.</span></span>  
  
 <span data-ttu-id="99146-322">İlke</span><span class="sxs-lookup"><span data-stu-id="99146-322">Policy</span></span>  
  
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
  
 <span data-ttu-id="99146-323">Güvenlik üst bilgisi düzeni</span><span class="sxs-lookup"><span data-stu-id="99146-323">Security Header Layout</span></span>  
  
 <span data-ttu-id="99146-324">İstek</span><span class="sxs-lookup"><span data-stu-id="99146-324">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:UsernameToken ... >  
  ...  
  </wsse:UsernameToken>  
</wsse:Security>  
```  
  
 <span data-ttu-id="99146-325">Yanıt</span><span class="sxs-lookup"><span data-stu-id="99146-325">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="612-certificateovertransport"></a><span data-ttu-id="99146-326">6.1.2 CertificateOverTransport</span><span class="sxs-lookup"><span data-stu-id="99146-326">6.1.2 CertificateOverTransport</span></span>  
 <span data-ttu-id="99146-327">SOAP katmanında başlatıcıdan alıcıya gönderilen her zaman bir onaylama destekleme belirteci olarak göründüğü bu kimlik doğrulama modu istemci kimlik doğrulaması kullanarak bir X.509 sertifikası.</span><span class="sxs-lookup"><span data-stu-id="99146-327">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as an endorsing supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="99146-328">Aktarım katmanında bir X.509 sertifikası kullanarak hizmet kimlik doğrulaması yapılır.</span><span class="sxs-lookup"><span data-stu-id="99146-328">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="99146-329">Kullanılan bağlama aktarım bağlama ' dir.</span><span class="sxs-lookup"><span data-stu-id="99146-329">The binding used is a transport binding.</span></span>  
  
 <span data-ttu-id="99146-330">İlke</span><span class="sxs-lookup"><span data-stu-id="99146-330">Policy</span></span>  
  
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
  
 <span data-ttu-id="99146-331">Güvenlik üst bilgisi düzeni</span><span class="sxs-lookup"><span data-stu-id="99146-331">Security Header Layout</span></span>  
  
 <span data-ttu-id="99146-332">İstek</span><span class="sxs-lookup"><span data-stu-id="99146-332">Request</span></span>  
  
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
  
 <span data-ttu-id="99146-333">Yanıt</span><span class="sxs-lookup"><span data-stu-id="99146-333">Response</span></span>  
  
```xml  
<o:Security>  
  <u:Timestamp u:Id="_0">  
  ...  
  </u:Timestamp>  
</o:Security>  
```  
  
#### <a name="613-issuedtokenovertransport"></a><span data-ttu-id="99146-334">6.1.3 IssuedTokenOverTransport</span><span class="sxs-lookup"><span data-stu-id="99146-334">6.1.3 IssuedTokenOverTransport</span></span>  
 <span data-ttu-id="99146-335">Bu kimlik doğrulama modu ile istemci hizmeti için bu nedenle, kimlik doğrulaması yapmaz ancak yerine bir güvenlik belirteci hizmeti (STS) tarafından verilmiş bir belirteç sunar ve paylaşılan anahtar bilgi kanıtlar.</span><span class="sxs-lookup"><span data-stu-id="99146-335">With this authentication mode the client does not authenticate to the service, as such, but rather presents a token issued by a Security Token Service (STS) and proves knowledge of a shared key.</span></span> <span data-ttu-id="99146-336">Verilen belirteç SOAP katmanında başlatıcıdan alıcıya gönderilen her zaman bir onaylama destekleme belirteci olarak görünür.</span><span class="sxs-lookup"><span data-stu-id="99146-336">The issued token appears at the SOAP layer as an endorsing supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="99146-337">Aktarım katmanında bir X.509 sertifikası kullanarak hizmet kimlik doğrulaması yapılır.</span><span class="sxs-lookup"><span data-stu-id="99146-337">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="99146-338">Aktarım bağlama bağlamadır.</span><span class="sxs-lookup"><span data-stu-id="99146-338">The binding is a transport binding.</span></span>  
  
 <span data-ttu-id="99146-339">İlke</span><span class="sxs-lookup"><span data-stu-id="99146-339">Policy</span></span>  
  
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
  
 <span data-ttu-id="99146-340">Güvenlik üst bilgisi düzeni</span><span class="sxs-lookup"><span data-stu-id="99146-340">Security Header Layout</span></span>  
  
 <span data-ttu-id="99146-341">İstek</span><span class="sxs-lookup"><span data-stu-id="99146-341">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1" >  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <saml:Assertion ...>  
  ...  
  </saml:Assertion>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
</wsse:Security>  
```  
  
 <span data-ttu-id="99146-342">Yanıt</span><span class="sxs-lookup"><span data-stu-id="99146-342">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="614-kerberosovertransport"></a><span data-ttu-id="99146-343">6.1.4 KerberosOverTransport</span><span class="sxs-lookup"><span data-stu-id="99146-343">6.1.4 KerberosOverTransport</span></span>  
 <span data-ttu-id="99146-344">Bu kimlik doğrulama modu ile bir Kerberos anahtarı kullanarak hizmete istemcinin kimliğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="99146-344">With this authentication mode the client authenticates to the service using a Kerberos ticket.</span></span> <span data-ttu-id="99146-345">Kerberos belirteci SOAP katmanında bir onaylama destekleme belirteci görünür.</span><span class="sxs-lookup"><span data-stu-id="99146-345">The Kerberos token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="99146-346">Aktarım katmanında bir X.509 sertifikası kullanarak hizmet kimlik doğrulaması yapılır.</span><span class="sxs-lookup"><span data-stu-id="99146-346">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="99146-347">Aktarım bağlama bağlamadır.</span><span class="sxs-lookup"><span data-stu-id="99146-347">The binding is a transport binding.</span></span>  
  
 <span data-ttu-id="99146-348">İlke</span><span class="sxs-lookup"><span data-stu-id="99146-348">Policy</span></span>  
  
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
  
 <span data-ttu-id="99146-349">Güvenlik üst bilgisi düzeni</span><span class="sxs-lookup"><span data-stu-id="99146-349">Security Header Layout</span></span>  
  
 <span data-ttu-id="99146-350">İstek</span><span class="sxs-lookup"><span data-stu-id="99146-350">Request</span></span>  
  
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
  
 <span data-ttu-id="99146-351">Yanıt</span><span class="sxs-lookup"><span data-stu-id="99146-351">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="615-sspinegotiatedovertransport"></a><span data-ttu-id="99146-352">6.1.5 SspiNegotiatedOverTransport</span><span class="sxs-lookup"><span data-stu-id="99146-352">6.1.5 SspiNegotiatedOverTransport</span></span>  
 <span data-ttu-id="99146-353">Bu modda, istemci ve sunucu kimlik doğrulaması gerçekleştirmek üzere bir anlaşma protokolü kullanılır.</span><span class="sxs-lookup"><span data-stu-id="99146-353">With this mode a negotiation protocol is used to perform client and server authentication.</span></span> <span data-ttu-id="99146-354">Kerberos Mümkünse, kullanılan aksi NTLM.</span><span class="sxs-lookup"><span data-stu-id="99146-354">Kerberos is used if possible, otherwise NTLM.</span></span> <span data-ttu-id="99146-355">Sonuçta elde edilen SCT SOAP katmanında başlatıcıdan alıcılara gönderilen her zaman bir onaylama destekleme belirteci olarak görünür.</span><span class="sxs-lookup"><span data-stu-id="99146-355">The resulting SCT appears at the SOAP layer as an endorsing supporting token that is always sent from initiator to recipient.</span></span> <span data-ttu-id="99146-356">Hizmet, ayrıca aktarım katmanında bir X.509 sertifikası tarafından doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="99146-356">The service is additionally authenticated at the transport layer by an X.509 certificate.</span></span> <span data-ttu-id="99146-357">Kullanılan bağlama aktarım bağlama ' dir.</span><span class="sxs-lookup"><span data-stu-id="99146-357">The binding used is a transport binding.</span></span> <span data-ttu-id="99146-358">"SPNEGO" (anlaşması) WCF SSPI ikili anlaşma protokolü WS-Trust ile nasıl kullandığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="99146-358">"SPNEGO" (negotiation) describes how WCF uses SSPI binary negotiation protocol with WS-Trust.</span></span> <span data-ttu-id="99146-359">SCT SPNEGO anlaşma oluşturulduktan sonra güvenlik üst bilgisi bu bölümdeki verilebilir.</span><span class="sxs-lookup"><span data-stu-id="99146-359">Security header examples in this section are after the SCT has been established through the SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="99146-360">İlke</span><span class="sxs-lookup"><span data-stu-id="99146-360">Policy</span></span>  
  
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
  
### <a name="security-header-examples"></a><span data-ttu-id="99146-361">Güvenlik üstbilgi örnekler</span><span class="sxs-lookup"><span data-stu-id="99146-361">Security Header Examples</span></span>  
 <span data-ttu-id="99146-362">Güvenlik bağlamı belirteci SPNEGO el sıkışması WS-Trust ikili anlaşması kullanılarak kurulduktan sonra uygulama iletileri güvenlik üst bilgileri aşağıdaki yapıya sahip olması.</span><span class="sxs-lookup"><span data-stu-id="99146-362">Once the Security Context Token is established through SPNEGO handshake using WS-Trust Binary Negotiation, the application messages have security headers with the following structure.</span></span>  
  
 <span data-ttu-id="99146-363">İstek</span><span class="sxs-lookup"><span data-stu-id="99146-363">Request</span></span>  
  
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
  
 <span data-ttu-id="99146-364">Yanıt</span><span class="sxs-lookup"><span data-stu-id="99146-364">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
### <a name="62-using-x509-certificates-for-service-authentication"></a><span data-ttu-id="99146-365">6.2 hizmet kimlik doğrulaması için X.509 sertifikaları kullanma</span><span class="sxs-lookup"><span data-stu-id="99146-365">6.2 Using X.509 Certificates for Service Authentication</span></span>  
 <span data-ttu-id="99146-366">Bu bölümde aşağıdaki kimlik doğrulama modları açıklanmaktadır: MutualCertificate WSS1.0, karşılıklı CertificateDuplex, MutualCertificate WSS1.1, AnonymousForCertificate, UserNameForCertificate ve IssuedTokenForCertificate.</span><span class="sxs-lookup"><span data-stu-id="99146-366">This section describes the following authentication modes: MutualCertificate WSS1.0, Mutual CertificateDuplex, MutualCertificate WSS1.1, AnonymousForCertificate, UserNameForCertificate and IssuedTokenForCertificate.</span></span>  
  
#### <a name="621-mutualcertificate-wss10"></a><span data-ttu-id="99146-367">6.2.1 MutualCertificate WSS1.0</span><span class="sxs-lookup"><span data-stu-id="99146-367">6.2.1 MutualCertificate WSS1.0</span></span>  
 <span data-ttu-id="99146-368">Başlatıcı belirteciyle SOAP katmanında görünen bu kimlik doğrulama modu istemci kimlik doğrulaması kullanarak bir X.509 sertifikası.</span><span class="sxs-lookup"><span data-stu-id="99146-368">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as the initiator token.</span></span> <span data-ttu-id="99146-369">Hizmet, ayrıca bir X.509 sertifikası kullanılarak kimlik doğrulaması yapılır.</span><span class="sxs-lookup"><span data-stu-id="99146-369">The service is also authenticated using an X.509 certificate.</span></span>  
  
 <span data-ttu-id="99146-370">Aşağıdaki özellik değerlerini asimetrik bir bağlamayla kullanılan bağlama şöyledir:</span><span class="sxs-lookup"><span data-stu-id="99146-370">The binding used is an asymmetric binding with the following property values:</span></span>  
  
 <span data-ttu-id="99146-371">Başlatıcı belirteci: ekleme modu ayarlamak için .../IncludeToken/AlwaysToRecipient istemcinin X.509 sertifikası</span><span class="sxs-lookup"><span data-stu-id="99146-371">Initiator Token: the client’s X.509 certificate, with inclusion mode set to …/IncludeToken/AlwaysToRecipient</span></span>  
  
 <span data-ttu-id="99146-372">Alıcı belirteci: Ekleme modu ile sunucu X.509 sertifikasının .../IncludeToken/Never ayarlanır</span><span class="sxs-lookup"><span data-stu-id="99146-372">Recipient Token: Server’s X.509 Certificate, with inclusion mode is set …/IncludeToken/Never</span></span>  
  
 <span data-ttu-id="99146-373">Belirteç koruma: False</span><span class="sxs-lookup"><span data-stu-id="99146-373">Token Protection: False</span></span>  
  
 <span data-ttu-id="99146-374">Tüm üst bilgisi ve gövdesi imza: Doğru</span><span class="sxs-lookup"><span data-stu-id="99146-374">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="99146-375">Koruma sırası: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="99146-375">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="99146-376">İmza şifrele: Doğru</span><span class="sxs-lookup"><span data-stu-id="99146-376">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="99146-377">İlke</span><span class="sxs-lookup"><span data-stu-id="99146-377">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="99146-378">Güvenlik üstbilgi örnekler: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="99146-378">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="99146-379">İstek</span><span class="sxs-lookup"><span data-stu-id="99146-379">Request</span></span>  
  
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
  
 <span data-ttu-id="99146-380">Yanıt</span><span class="sxs-lookup"><span data-stu-id="99146-380">Response</span></span>  
  
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
  
 <span data-ttu-id="99146-381">Güvenlik üstbilgi örnekler: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="99146-381">Security Header Examples: EncryptBeforeSign</span></span>  
  
 <span data-ttu-id="99146-382">İstek</span><span class="sxs-lookup"><span data-stu-id="99146-382">Request</span></span>  
  
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
  
 <span data-ttu-id="99146-383">Yanıt</span><span class="sxs-lookup"><span data-stu-id="99146-383">Response</span></span>  
  
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
  
#### <a name="622-mutualcertificateduplex"></a><span data-ttu-id="99146-384">6.2.2 MutualCertificateDuplex</span><span class="sxs-lookup"><span data-stu-id="99146-384">6.2.2 MutualCertificateDuplex</span></span>  
 <span data-ttu-id="99146-385">Başlatıcı belirteciyle SOAP katmanında görünen bu kimlik doğrulama modu istemci kimlik doğrulaması kullanarak bir X.509 sertifikası.</span><span class="sxs-lookup"><span data-stu-id="99146-385">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as the initiator token.</span></span> <span data-ttu-id="99146-386">Hizmet, ayrıca bir X.509 sertifikası kullanılarak kimlik doğrulaması yapılır.</span><span class="sxs-lookup"><span data-stu-id="99146-386">The service is also authenticated using an X.509 certificate.</span></span>  
  
 <span data-ttu-id="99146-387">Aşağıdaki özellik değerlerini asimetrik bir bağlamayla kullanılan bağlama şöyledir:</span><span class="sxs-lookup"><span data-stu-id="99146-387">The binding used is an asymmetric binding with the following property values:</span></span>  
  
 <span data-ttu-id="99146-388">Başlatıcı belirteci: İstemcinin X509 sertifikası ekleme modu için .../IncludeToken/AlwaysToRecipient ayarlanır</span><span class="sxs-lookup"><span data-stu-id="99146-388">Initiator Token: Client’s X509 Certificate, inclusion mode is set to …/IncludeToken/AlwaysToRecipient</span></span>  
  
 <span data-ttu-id="99146-389">Alıcı belirteci: Sunucunun X509 sertifikası ekleme modu için .../IncludeToken/AlwaysToInitiator ayarlanır</span><span class="sxs-lookup"><span data-stu-id="99146-389">Recipient Token: Server’s X509 Certificate, inclusion mode is set to …/IncludeToken/AlwaysToInitiator</span></span>  
  
 <span data-ttu-id="99146-390">Belirteç koruma: False</span><span class="sxs-lookup"><span data-stu-id="99146-390">Token Protection: False</span></span>  
  
 <span data-ttu-id="99146-391">Tüm üst bilgisi ve gövdesi imza: Doğru</span><span class="sxs-lookup"><span data-stu-id="99146-391">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="99146-392">Koruma sırası: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="99146-392">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="99146-393">İmza şifrele: Doğru</span><span class="sxs-lookup"><span data-stu-id="99146-393">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="99146-394">İlke</span><span class="sxs-lookup"><span data-stu-id="99146-394">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="99146-395">Güvenlik üstbilgi örnekler: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="99146-395">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="99146-396">İstek ve yanıt</span><span class="sxs-lookup"><span data-stu-id="99146-396">Request and Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="99146-397">Güvenlik üstbilgi örnekler: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="99146-397">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="99146-398">İstek ve yanıt</span><span class="sxs-lookup"><span data-stu-id="99146-398">Request and Response</span></span>  
  
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
  
#### <a name="623-using-symmetricbinding-with-x509-service-authentication"></a><span data-ttu-id="99146-399">6.2.3 SymmetricBinding X.509 hizmet kimlik doğrulamasını kullanarak.</span><span class="sxs-lookup"><span data-stu-id="99146-399">6.2.3 Using SymmetricBinding with X.509 Service Authentication</span></span>  
 <span data-ttu-id="99146-400">"WSS10" X509 senaryolarıyla için sınırlı destek sağlanmaktadır belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="99146-400">"WSS10" provided limited support for scenarios with X509 tokens.</span></span> <span data-ttu-id="99146-401">Örneğin, yalnızca hizmet X509 belirteci kullanarak iletileri için imza ve şifreleme koruma sağlamak için hiçbir yolu yoktu.</span><span class="sxs-lookup"><span data-stu-id="99146-401">For example, there was no way to provide signature and encryption protection for messages using only service X509 token.</span></span> <span data-ttu-id="99146-402">"WSS11" EncryptedKey kullanımını simetrik bir belirteç kullanıma sunuldu.</span><span class="sxs-lookup"><span data-stu-id="99146-402">"WSS11" introduced the usage of EncryptedKey as a symmetric token.</span></span> <span data-ttu-id="99146-403">Şimdi hizmetin X.509 sertifikası için şifrelenmiş geçici bir anahtar hem istek hem de yanıt iletilerini koruma için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="99146-403">Now a temporary key encrypted for the service's X.509 certificate could be used for both request and response messages protection.</span></span> <span data-ttu-id="99146-404">' % S'bölümünde 6.4 açıklanan kimlik doğrulama modları, bu düzeni kullanın.</span><span class="sxs-lookup"><span data-stu-id="99146-404">The authentication modes described in the section 6.4 below use this pattern.</span></span>  
  
 <span data-ttu-id="99146-405">WS-SecurityPolicy SymmetricBinding hizmetiyle kullanarak bu deseni açıklar X509 token koruma belirteç.</span><span class="sxs-lookup"><span data-stu-id="99146-405">WS-SecurityPolicy describes this pattern using SymmetricBinding with Service X509 token as the protection token.</span></span>  
  
 <span data-ttu-id="99146-406">Kimlik doğrulama modları AnonymousForCertificate, UsernameForCertificate MutualCertificate WSS11 ve IssuedTokenForCertificate tüm sp:SymmetricBinding benzer bir örneğini aşağıdaki özellik değerleri kullanın:</span><span class="sxs-lookup"><span data-stu-id="99146-406">Authentication modes AnonymousForCertificate, UsernameForCertificate, MutualCertificate WSS11 and IssuedTokenForCertificate all use a similar instance of sp:SymmetricBinding with the following property values:</span></span>  
  
 <span data-ttu-id="99146-407">Koruma belirteci: Sunucunun X509 sertifikası ekleme modu için .../IncludeToken/Never ayarlanır</span><span class="sxs-lookup"><span data-stu-id="99146-407">Protection Token: Server’s X509 Certificate, inclusion mode is set to .../IncludeToken/Never</span></span>  
<span data-ttu-id="99146-408">Belirteç koruma: False</span><span class="sxs-lookup"><span data-stu-id="99146-408">Token Protection: False</span></span>  
  
 <span data-ttu-id="99146-409">Tüm üst bilgisi ve gövdesi imza: Doğru</span><span class="sxs-lookup"><span data-stu-id="99146-409">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="99146-410">Koruma sırası: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="99146-410">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="99146-411">İmza şifrele: Doğru</span><span class="sxs-lookup"><span data-stu-id="99146-411">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="99146-412">Yukarıdaki kimlik doğrulama modları, yalnızca kullandıkları destek belirteçleri ile farklı.</span><span class="sxs-lookup"><span data-stu-id="99146-412">The above authentication modes only differ by the supporting tokens they use.</span></span> <span data-ttu-id="99146-413">AnonymousForCertificate destekleyici tarafından istenen belirteçleri yok, MutualCertificate WSS 1.1 sahip istemcinin X509 sertifika bir destek belirteçleri onaylama olarak, UserNameForCertificate sahip bir kullanıcı adı belirteci imzalı destekleme belirteci olarak ve IssuedTokenForCertificate verilen belirtecin bir onaylama destekleme belirteci sahiptir.</span><span class="sxs-lookup"><span data-stu-id="99146-413">AnonymousForCertificate does not have any supporting tokens, MutualCertificate WSS 1.1 has the client’s X509 certificate as an endorsing supporting tokens, UserNameForCertificate has a UserName Token as a signed supporting token and IssuedTokenForCertificate has the issued token as an endorsing supporting token.</span></span>  
  
 <span data-ttu-id="99146-414">İlke</span><span class="sxs-lookup"><span data-stu-id="99146-414">Policy</span></span>  
  
 <span data-ttu-id="99146-415">Simetrik bağlama</span><span class="sxs-lookup"><span data-stu-id="99146-415">Symmetric Binding</span></span>  
  
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
  
#### <a name="624-anonymousforcertificate"></a><span data-ttu-id="99146-416">6.2.4 AnonymousForCertificate</span><span class="sxs-lookup"><span data-stu-id="99146-416">6.2.4 AnonymousForCertificate</span></span>  
 <span data-ttu-id="99146-417">Bu kimlik doğrulama modu ile istemci anonimdir ve bir X.509 sertifikası kullanarak hizmet kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="99146-417">With this authentication mode the client is anonymous and the service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="99146-418">Kullanılan bağlama 6.4.2 içinde anlatıldığı gibi simetrik bağlama bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="99146-418">The binding used is an instance of symmetric binding as described in 6.4.2.</span></span>  
  
 <span data-ttu-id="99146-419">İlke</span><span class="sxs-lookup"><span data-stu-id="99146-419">Policy</span></span>  
  
 <span data-ttu-id="99146-420">Yukarıdaki 6.2.3 "ilke" bağlaması ayrıntıları için bkz.</span><span class="sxs-lookup"><span data-stu-id="99146-420">See "Policy" in 6.2.3 above for binding details</span></span>  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="99146-421">Güvenlik üstbilgi örnekler: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="99146-421">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="99146-422">İstek</span><span class="sxs-lookup"><span data-stu-id="99146-422">Request</span></span>  
  
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
  
 <span data-ttu-id="99146-423">Yanıt</span><span class="sxs-lookup"><span data-stu-id="99146-423">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="99146-424">Güvenlik üstbilgi örnekler: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="99146-424">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="99146-425">İstek</span><span class="sxs-lookup"><span data-stu-id="99146-425">Request</span></span>  
  
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
  
 <span data-ttu-id="99146-426">Yanıt</span><span class="sxs-lookup"><span data-stu-id="99146-426">Response</span></span>  
  
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
  
#### <a name="625-usernameforcertificate"></a><span data-ttu-id="99146-427">6.2.5 UserNameForCertificate</span><span class="sxs-lookup"><span data-stu-id="99146-427">6.2.5 UserNameForCertificate</span></span>  
 <span data-ttu-id="99146-428">Bu kimlik doğrulama modu ile görüntülenen bir kullanıcı adı belirteci SOAP katmanında imzalı destekleme belirteci kullanarak hizmete istemcinin kimliğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="99146-428">With this authentication mode the client authenticates to the service using a Username Token which appears at the SOAP layer as a signed supporting token.</span></span> <span data-ttu-id="99146-429">Hizmet bir X.509 sertifikası kullanarak istemcinin kimliğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="99146-429">The service authenticates to the client using an X.509 certificate.</span></span> <span data-ttu-id="99146-430">Kullanılan bağlama, hizmetin ortak anahtar ile şifrelenmiş bir istemci tarafından oluşturulan bir anahtarı olan koruma belirtecine sahip simetrik bir bağlamadır.</span><span class="sxs-lookup"><span data-stu-id="99146-430">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="99146-431">İlke</span><span class="sxs-lookup"><span data-stu-id="99146-431">Policy</span></span>  
  
 <span data-ttu-id="99146-432">Yukarıdaki 6.2.3 "ilke" bağlaması ayrıntıları için bkz.</span><span class="sxs-lookup"><span data-stu-id="99146-432">See "Policy" in 6.2.3 above for binding details</span></span>  
  
 <span data-ttu-id="99146-433">Destekleme belirteci imzalayan</span><span class="sxs-lookup"><span data-stu-id="99146-433">Signed Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="99146-434">Güvenlik üstbilgi örnekler: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="99146-434">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="99146-435">İstek</span><span class="sxs-lookup"><span data-stu-id="99146-435">Request</span></span>  
  
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
  
 <span data-ttu-id="99146-436">Yanıt</span><span class="sxs-lookup"><span data-stu-id="99146-436">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="99146-437">Güvenlik üstbilgi örnekler: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="99146-437">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="99146-438">İstek</span><span class="sxs-lookup"><span data-stu-id="99146-438">Request</span></span>  
  
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
  
 <span data-ttu-id="99146-439">Yanıt</span><span class="sxs-lookup"><span data-stu-id="99146-439">Response</span></span>  
  
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
  
#### <a name="626-mutualcertificate-wss-11"></a><span data-ttu-id="99146-440">6.2.6 MutualCertificate (WSS 1.1)</span><span class="sxs-lookup"><span data-stu-id="99146-440">6.2.6 MutualCertificate (WSS 1.1)</span></span>  
 <span data-ttu-id="99146-441">SOAP katmanında bir onaylama destekleme belirteci olarak görünen bu kimlik doğrulama modu istemci kimlik doğrulaması kullanarak bir X.509 sertifikası.</span><span class="sxs-lookup"><span data-stu-id="99146-441">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="99146-442">Hizmet, ayrıca bir X.509 sertifikası kullanılarak kimlik doğrulaması yapılır.</span><span class="sxs-lookup"><span data-stu-id="99146-442">The service is also authenticated using an X.509 certificate.</span></span> <span data-ttu-id="99146-443">Kullanılan bağlama, hizmetin ortak anahtar ile şifrelenmiş bir istemci tarafından oluşturulan bir anahtarı olan koruma belirtecine sahip simetrik bir bağlamadır.</span><span class="sxs-lookup"><span data-stu-id="99146-443">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="99146-444">İlke</span><span class="sxs-lookup"><span data-stu-id="99146-444">Policy</span></span>  
  
 <span data-ttu-id="99146-445">İlke 6.2.3 bağlaması ayrıntıları için bkz.</span><span class="sxs-lookup"><span data-stu-id="99146-445">See Policy in 6.2.3 for binding details</span></span>  
  
 <span data-ttu-id="99146-446">Onaylama destekleme belirteci</span><span class="sxs-lookup"><span data-stu-id="99146-446">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="99146-447">Güvenlik üstbilgi örnekler: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="99146-447">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="99146-448">İstek</span><span class="sxs-lookup"><span data-stu-id="99146-448">Request</span></span>  
  
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
  
 <span data-ttu-id="99146-449">Yanıt</span><span class="sxs-lookup"><span data-stu-id="99146-449">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="99146-450">Güvenlik üstbilgi örnekler: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="99146-450">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="99146-451">İstek</span><span class="sxs-lookup"><span data-stu-id="99146-451">Request</span></span>  
  
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
  
 <span data-ttu-id="99146-452">Yanıt</span><span class="sxs-lookup"><span data-stu-id="99146-452">Response</span></span>  
  
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
  
#### <a name="627-issuedtokenforcertificate"></a><span data-ttu-id="99146-453">6.2.7 IssuedTokenForCertificate</span><span class="sxs-lookup"><span data-stu-id="99146-453">6.2.7 IssuedTokenForCertificate</span></span>  
 <span data-ttu-id="99146-454">Bu kimlik doğrulaması ile istemci hizmete, bu nedenle, ancak bunun yerine kimlik doğrulamasını yapmaz modu STS tarafından verilen bir belirteç verir ve bir paylaşılan anahtar bilgisini kanıtlayan sorgu.</span><span class="sxs-lookup"><span data-stu-id="99146-454">With this authentication mode the client does not authenticate to the service, as such, but instead presents a token issued by a STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="99146-455">Verilen belirteç SOAP katmanında bir onaylama destekleme belirteci görünür.</span><span class="sxs-lookup"><span data-stu-id="99146-455">The issued token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="99146-456">Hizmet bir X.509 sertifikası kullanarak istemcinin kimliğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="99146-456">The service authenticates to the client using an X.509 certificate.</span></span> <span data-ttu-id="99146-457">Kullanılan bağlama, hizmetin ortak anahtar ile şifrelenmiş bir istemci tarafından oluşturulan bir anahtarı olan koruma belirtecine sahip simetrik bir bağlamadır.</span><span class="sxs-lookup"><span data-stu-id="99146-457">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="99146-458">İlke</span><span class="sxs-lookup"><span data-stu-id="99146-458">Policy</span></span>  
  
 <span data-ttu-id="99146-459">İlke 6.2.3 bağlama ayrıntıları için bkz.</span><span class="sxs-lookup"><span data-stu-id="99146-459">See Policy in 6.2.3 above for binding details</span></span>  
  
 <span data-ttu-id="99146-460">Onaylama destekleme belirteci</span><span class="sxs-lookup"><span data-stu-id="99146-460">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="99146-461">Güvenlik üstbilgi örnekler: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="99146-461">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="99146-462">İstek</span><span class="sxs-lookup"><span data-stu-id="99146-462">Request</span></span>  
  
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
  
 <span data-ttu-id="99146-463">Yanıt</span><span class="sxs-lookup"><span data-stu-id="99146-463">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="99146-464">Güvenlik üstbilgi örnekler: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="99146-464">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="99146-465">İstek</span><span class="sxs-lookup"><span data-stu-id="99146-465">Request</span></span>  
  
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
  
 <span data-ttu-id="99146-466">Yanıt</span><span class="sxs-lookup"><span data-stu-id="99146-466">Response</span></span>  
  
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
  
## <a name="63-kerberos"></a><span data-ttu-id="99146-467">6.3 Kerberos</span><span class="sxs-lookup"><span data-stu-id="99146-467">6.3 Kerberos</span></span>  
 <span data-ttu-id="99146-468">Bu kimlik doğrulama modu ile bir Kerberos anahtarı kullanarak hizmete istemcinin kimliğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="99146-468">With this authentication mode the client authenticates to the service using a Kerberos ticket.</span></span> <span data-ttu-id="99146-469">Bu aynı anahtar Ayrıca sunucu kimlik doğrulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="99146-469">That same ticket also provides server authentication.</span></span> <span data-ttu-id="99146-470">Kullanılan bağlama, aşağıdaki özelliklere sahip bir simetrik bağlamadır;</span><span class="sxs-lookup"><span data-stu-id="99146-470">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="99146-471">Koruma belirteci: Kerberos anahtarı ekleme modu .../IncludeToken/Once için ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="99146-471">Protection Token: Kerberos Ticket, inclusion mode is set to .../IncludeToken/Once</span></span>  
<span data-ttu-id="99146-472">Belirteç koruma: False</span><span class="sxs-lookup"><span data-stu-id="99146-472">Token Protection: False</span></span>  
  
 <span data-ttu-id="99146-473">Tüm üst bilgisi ve gövdesi imza: Doğru</span><span class="sxs-lookup"><span data-stu-id="99146-473">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="99146-474">Koruma sırası: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="99146-474">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="99146-475">İmza şifrele: Doğru</span><span class="sxs-lookup"><span data-stu-id="99146-475">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="99146-476">İlke</span><span class="sxs-lookup"><span data-stu-id="99146-476">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="99146-477">Güvenlik üstbilgi örnekler: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="99146-477">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="99146-478">İstek</span><span class="sxs-lookup"><span data-stu-id="99146-478">Request</span></span>  
  
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
  
 <span data-ttu-id="99146-479">Yanıt</span><span class="sxs-lookup"><span data-stu-id="99146-479">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="99146-480">Güvenlik üstbilgi örnekler: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="99146-480">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="99146-481">İstek</span><span class="sxs-lookup"><span data-stu-id="99146-481">Request</span></span>  
  
```xml  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
 <span data-ttu-id="99146-482">Yanıt</span><span class="sxs-lookup"><span data-stu-id="99146-482">Response</span></span>  
  
```xml  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
#### <a name="64-issuedtoken"></a><span data-ttu-id="99146-483">6.4 IssuedToken</span><span class="sxs-lookup"><span data-stu-id="99146-483">6.4 IssuedToken</span></span>  
 <span data-ttu-id="99146-484">İstemci hizmete kimlik doğrulaması yapmaz, bu kimlik doğrulama modu ile bu nedenle, yerine istemci STS tarafından verilen bir belirteç sunar ve paylaşılan anahtar bilgi kanıtlar.</span><span class="sxs-lookup"><span data-stu-id="99146-484">With this authentication mode the client does not authenticate to the service, as such, rather the client presents a token issued by an STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="99146-485">İstemcisini, bu nedenle hizmet kimliği, bunun yerine STS şifreler paylaşılan anahtarı verilen belirtecin bir parçası olarak yalnızca hizmet anahtarının şifresini çözüm olacak şekilde.</span><span class="sxs-lookup"><span data-stu-id="99146-485">The service is not authenticated to the client, as such, instead the STS encrypts the shared key as part of the issued token such that only the service can decrypt the key.</span></span> <span data-ttu-id="99146-486">Aşağıdaki özelliklerle simetrik bağlama kullanılan bağlama gibidir;</span><span class="sxs-lookup"><span data-stu-id="99146-486">The binding used is as symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="99146-487">Koruma belirteci: Belirteç, ekleme modu için .../IncludeToken/AlwaysToRecipient ayarlanır</span><span class="sxs-lookup"><span data-stu-id="99146-487">Protection Token: Issued Token, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
<span data-ttu-id="99146-488">Belirteç koruma: False</span><span class="sxs-lookup"><span data-stu-id="99146-488">Token Protection: False</span></span>  
  
 <span data-ttu-id="99146-489">Tüm üst bilgisi ve gövdesi imza: Doğru</span><span class="sxs-lookup"><span data-stu-id="99146-489">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="99146-490">Koruma sırası: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="99146-490">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="99146-491">İmza şifrele: Doğru</span><span class="sxs-lookup"><span data-stu-id="99146-491">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="99146-492">İlke</span><span class="sxs-lookup"><span data-stu-id="99146-492">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="99146-493">Güvenlik üstbilgi örnekler: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="99146-493">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="99146-494">İstek</span><span class="sxs-lookup"><span data-stu-id="99146-494">Request</span></span>  
  
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
  
 <span data-ttu-id="99146-495">Yanıt</span><span class="sxs-lookup"><span data-stu-id="99146-495">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="99146-496">Güvenlik üstbilgi örnekler: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="99146-496">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="99146-497">İstek</span><span class="sxs-lookup"><span data-stu-id="99146-497">Request</span></span>  
  
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
  
 <span data-ttu-id="99146-498">Yanıt</span><span class="sxs-lookup"><span data-stu-id="99146-498">Response</span></span>  
  
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
  
### <a name="65-using-sslnegotiated-for-service-authentication"></a><span data-ttu-id="99146-499">6.5 SslNegotiated hizmet kimlik doğrulaması için kullanma</span><span class="sxs-lookup"><span data-stu-id="99146-499">6.5 Using SslNegotiated for Service Authentication</span></span>  
 <span data-ttu-id="99146-500">Bu bölümde, bir grup olan bir güvenlik bağlamı belirteci başına WS-anahtar değeri, WS-Trust (WS-T) lk TLS protokolü yürüterek varılır SecureConversation (WS-SC) koruma belirtecine sahip bir simetrik bağlama kullanan kimlik doğrulama modları açıklanır / RSTR iletileri.</span><span class="sxs-lookup"><span data-stu-id="99146-500">This section describes a group of authentication modes that use a symmetric binding with the protection token being a Security Context Token per WS-SecureConversation (WS-SC) whose key value is negotiated by executing the TLS protocol over WS-Trust (WS-T) RST/RSTR messages.</span></span> <span data-ttu-id="99146-501">WS-Trust kullanarak TLS el sıkışma uygulamasının Ayrıntılar TLSNEGO içinde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="99146-501">Details of the TLS handshake implementation using WS-Trust are described in TLSNEGO.</span></span> <span data-ttu-id="99146-502">Burada ileti örneklerde SCT ilişkili güvenlik bağlamı ile zaten bir anlaşması kurulan varsayacağız.</span><span class="sxs-lookup"><span data-stu-id="99146-502">Here in the message examples we will assume that SCT with an associated security context is already established through a handshake.</span></span>  
  
 <span data-ttu-id="99146-503">Kullanılan bağlama, aşağıdaki özelliklere sahip bir simetrik bağlamadır;</span><span class="sxs-lookup"><span data-stu-id="99146-503">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="99146-504">Koruma belirteci: SslContextToken, ekleme modu .../IncludeToken/Never için ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="99146-504">Protection Token: SslContextToken, inclusion mode is set to .../IncludeToken/Never</span></span>  
<span data-ttu-id="99146-505">Belirteç koruma: False</span><span class="sxs-lookup"><span data-stu-id="99146-505">Token Protection: False</span></span>  
  
 <span data-ttu-id="99146-506">Tüm üst bilgisi ve gövdesi imza: Doğru</span><span class="sxs-lookup"><span data-stu-id="99146-506">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="99146-507">Koruma sırası: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="99146-507">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="99146-508">İmza şifrele: Doğru</span><span class="sxs-lookup"><span data-stu-id="99146-508">Encrypt Signature: True</span></span>  
  
#### <a name="651-policy-for-sslnegotiated-service-authentication"></a><span data-ttu-id="99146-509">6.5.1 SslNegotiated hizmeti kimlik doğrulama İlkesi</span><span class="sxs-lookup"><span data-stu-id="99146-509">6.5.1 Policy for SslNegotiated service authentication</span></span>  
 <span data-ttu-id="99146-510">Bu bölümdeki tüm kimlik doğrulama modları için ilke benzerdir ve yalnızca özel imzalı desteklemenin veya kullanılan belirteçleri onaylama farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="99146-510">Policy for all authentication modes in this section are similar and differ only by specific signed supporting or endorsing tokens used.</span></span>  
  
```xml  
<wsp:Policy wsu:Id='SslNegotiated_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <mssp:SslContextToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' />  
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
  
#### <a name="652-anonymousforsslnegotiated"></a><span data-ttu-id="99146-511">6.5.2 AnonymousForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="99146-511">6.5.2 AnonymousForSslNegotiated</span></span>  
 <span data-ttu-id="99146-512">Bu kimlik doğrulama modu ile istemci anonimdir ve bir X.509 sertifikası kullanarak hizmet kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="99146-512">With this authentication mode the client is anonymous and the service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="99146-513">Kullanılan bağlama 6.5.1 yukarıda açıklandığı gibi simetrik bağlama bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="99146-513">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="99146-514">İlke</span><span class="sxs-lookup"><span data-stu-id="99146-514">Policy</span></span>  
  
 <span data-ttu-id="99146-515">İlke Bağlama Ayrıntılar için 6.5.1 görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="99146-515">See Policy in 6.5.1 above for binding details.</span></span>  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="99146-516">Güvenlik üstbilgi örnekler: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="99146-516">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="99146-517">İstek</span><span class="sxs-lookup"><span data-stu-id="99146-517">Request</span></span>  
  
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
  
 <span data-ttu-id="99146-518">Yanıt</span><span class="sxs-lookup"><span data-stu-id="99146-518">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="99146-519">Güvenlik üstbilgi örnekler: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="99146-519">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="99146-520">İstek</span><span class="sxs-lookup"><span data-stu-id="99146-520">Request</span></span>  
  
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
  
 <span data-ttu-id="99146-521">Yanıt</span><span class="sxs-lookup"><span data-stu-id="99146-521">Response</span></span>  
  
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
  
#### <a name="653-usernameforsslnegotiated"></a><span data-ttu-id="99146-522">6.5.3 UserNameForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="99146-522">6.5.3 UserNameForSslNegotiated</span></span>  
 <span data-ttu-id="99146-523">Bu kimlik doğrulaması ile istemci modunda görüntülenen bir kullanıcı adı belirteci SOAP katmanında imzalı destekleme belirteci kullanarak kimliğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="99146-523">With this authentication mode the client is authenticates using a Username Token which appears at the SOAP layer as a signed supporting token.</span></span> <span data-ttu-id="99146-524">Hizmet bir X.509 sertifikası kullanılarak kimlik doğrulaması yapılır.</span><span class="sxs-lookup"><span data-stu-id="99146-524">The service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="99146-525">Kullanılan bağlama 6.5.1 içinde anlatıldığı gibi simetrik bağlama bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="99146-525">The binding used is an instance of symmetric binding as described in 6.5.1.</span></span>  
  
 <span data-ttu-id="99146-526">İlke</span><span class="sxs-lookup"><span data-stu-id="99146-526">Policy</span></span>  
  
 <span data-ttu-id="99146-527">Bağlaması ayrıntıları için yukarıdaki 6.5.1 bölümüne bakın</span><span class="sxs-lookup"><span data-stu-id="99146-527">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="99146-528">Destekleme belirteci imzalayan</span><span class="sxs-lookup"><span data-stu-id="99146-528">Signed Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="99146-529">Güvenlik üstbilgi örnekler: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="99146-529">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="99146-530">İstek</span><span class="sxs-lookup"><span data-stu-id="99146-530">Request</span></span>  
  
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
  
 <span data-ttu-id="99146-531">Yanıt</span><span class="sxs-lookup"><span data-stu-id="99146-531">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="99146-532">Güvenlik üstbilgi örnekler: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="99146-532">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="99146-533">İstek</span><span class="sxs-lookup"><span data-stu-id="99146-533">Request</span></span>  
  
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
  
 <span data-ttu-id="99146-534">Yanıt</span><span class="sxs-lookup"><span data-stu-id="99146-534">Response</span></span>  
  
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
  
#### <a name="654-issuedtokenforsslnegotiated"></a><span data-ttu-id="99146-535">6.5.4 IssuedTokenForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="99146-535">6.5.4 IssuedTokenForSslNegotiated</span></span>  
 <span data-ttu-id="99146-536">Bu kimlik doğrulaması ile istemci hizmete, bu nedenle, ancak bunun yerine kimlik doğrulamasını yapmaz modu STS tarafından verilen bir belirteç verir ve bir paylaşılan anahtar bilgisini kanıtlar.</span><span class="sxs-lookup"><span data-stu-id="99146-536">With this authentication mode the client does not authenticate to the service, as such, but instead presents a token issued by an STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="99146-537">Verilen belirteç SOAP katmanında bir onaylama destekleme belirteci görünür.</span><span class="sxs-lookup"><span data-stu-id="99146-537">The issued token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="99146-538">Hizmet bir X.509 sertifikası kullanılarak kimlik doğrulaması yapılır.</span><span class="sxs-lookup"><span data-stu-id="99146-538">The service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="99146-539">Kullanılan bağlama 6.5.1 yukarıda açıklandığı gibi simetrik bağlama bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="99146-539">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="99146-540">İlke</span><span class="sxs-lookup"><span data-stu-id="99146-540">Policy</span></span>  
  
 <span data-ttu-id="99146-541">Bağlaması ayrıntıları için yukarıdaki 6.5.1 bölümüne bakın</span><span class="sxs-lookup"><span data-stu-id="99146-541">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="99146-542">Onaylama destekleme belirteci</span><span class="sxs-lookup"><span data-stu-id="99146-542">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="99146-543">Güvenlik üstbilgi örnekler: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="99146-543">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="99146-544">İstek</span><span class="sxs-lookup"><span data-stu-id="99146-544">Request</span></span>  
  
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
  
 <span data-ttu-id="99146-545">Yanıt</span><span class="sxs-lookup"><span data-stu-id="99146-545">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="99146-546">Güvenlik üstbilgi örnekler: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="99146-546">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="99146-547">İstek</span><span class="sxs-lookup"><span data-stu-id="99146-547">Request</span></span>  
  
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
  
 <span data-ttu-id="99146-548">Yanıt</span><span class="sxs-lookup"><span data-stu-id="99146-548">Response</span></span>  
  
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
  
#### <a name="655-mutualsslnegotiated"></a><span data-ttu-id="99146-549">6.5.5 MutualSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="99146-549">6.5.5 MutualSslNegotiated</span></span>  
 <span data-ttu-id="99146-550">Bu kimlik doğrulama modu ile hizmet ve istemci X.509 sertifikaları kullanarak kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="99146-550">With this authentication mode the client and the service authenticate using X.509 certificates.</span></span> <span data-ttu-id="99146-551">Kullanılan bağlama 6.5.1 yukarıda açıklandığı gibi simetrik bağlama bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="99146-551">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="99146-552">İlke</span><span class="sxs-lookup"><span data-stu-id="99146-552">Policy</span></span>  
  
 <span data-ttu-id="99146-553">Bağlaması ayrıntıları için yukarıdaki 6.5.1 bölümüne bakın</span><span class="sxs-lookup"><span data-stu-id="99146-553">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="99146-554">Onaylama destekleme belirteci</span><span class="sxs-lookup"><span data-stu-id="99146-554">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="99146-555">Güvenlik üstbilgi örnekler: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="99146-555">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="99146-556">İstek</span><span class="sxs-lookup"><span data-stu-id="99146-556">Request</span></span>  
  
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
  
 <span data-ttu-id="99146-557">Yanıt</span><span class="sxs-lookup"><span data-stu-id="99146-557">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="99146-558">Güvenlik üstbilgi örnekler: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="99146-558">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="99146-559">İstek</span><span class="sxs-lookup"><span data-stu-id="99146-559">Request</span></span>  
  
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
  
 <span data-ttu-id="99146-560">Yanıt</span><span class="sxs-lookup"><span data-stu-id="99146-560">Response</span></span>  
  
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
  
### <a name="66-sspinegotiated"></a><span data-ttu-id="99146-561">6.6 SspiNegotiated</span><span class="sxs-lookup"><span data-stu-id="99146-561">6.6 SspiNegotiated</span></span>  
 <span data-ttu-id="99146-562">Bu kimlik doğrulama modu ile istemci ve sunucu kimlik doğrulaması gerçekleştirmek üzere bir anlaşma protokolü kullanılır.</span><span class="sxs-lookup"><span data-stu-id="99146-562">With this authentication mode a negotiation protocol is used to perform client and server authentication.</span></span> <span data-ttu-id="99146-563">Kerberos Mümkünse, kullanılan aksi NTLM.</span><span class="sxs-lookup"><span data-stu-id="99146-563">Kerberos is used if possible, otherwise NTLM.</span></span> <span data-ttu-id="99146-564">Kullanılan bağlama, aşağıdaki özelliklere sahip bir simetrik bağlamadır;</span><span class="sxs-lookup"><span data-stu-id="99146-564">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="99146-565">Koruma belirteci: SpnegoContextToken, ekleme modu .../IncludeToken/AlwaysToRecipient için ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="99146-565">Protection Token: SpnegoContextToken, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
<span data-ttu-id="99146-566">Belirteç koruma: False</span><span class="sxs-lookup"><span data-stu-id="99146-566">Token Protection: False</span></span>  
  
 <span data-ttu-id="99146-567">Tüm üst bilgisi ve gövdesi imza: Doğru</span><span class="sxs-lookup"><span data-stu-id="99146-567">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="99146-568">Koruma sırası: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="99146-568">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="99146-569">İmza şifrele: Doğru</span><span class="sxs-lookup"><span data-stu-id="99146-569">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="99146-570">İlke</span><span class="sxs-lookup"><span data-stu-id="99146-570">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="99146-571">Güvenlik üstbilgi örnekler: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="99146-571">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="99146-572">İstek</span><span class="sxs-lookup"><span data-stu-id="99146-572">Request</span></span>  
  
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
  
 <span data-ttu-id="99146-573">Yanıt</span><span class="sxs-lookup"><span data-stu-id="99146-573">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="99146-574">Güvenlik üstbilgi örnekler: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="99146-574">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="99146-575">İstek</span><span class="sxs-lookup"><span data-stu-id="99146-575">Request</span></span>  
  
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
  
 <span data-ttu-id="99146-576">Yanıt</span><span class="sxs-lookup"><span data-stu-id="99146-576">Response</span></span>  
  
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
  
### <a name="67-secureconversation"></a><span data-ttu-id="99146-577">6.7 SecureConversation</span><span class="sxs-lookup"><span data-stu-id="99146-577">6.7 SecureConversation</span></span>  
 <span data-ttu-id="99146-578">Kullanılan bağlama, WS-SecureConversation (WS-SC) başına bir SCT olan koruma belirtecine sahip simetrik bir bağlamadır.</span><span class="sxs-lookup"><span data-stu-id="99146-578">The binding used is a symmetric binding with the protection token being a SCT per WS-SecureConversation (WS-SC).</span></span> <span data-ttu-id="99146-579">SCT kendisi bir anlaşma protokolünü kullanan, simetrik bir bağlamadır bir iç içe bağlama göre WS-Trust (WS-Trust) veya WS-SecureConversation (WS-SC) kullanılarak belirlenir.</span><span class="sxs-lookup"><span data-stu-id="99146-579">The SCT is negotiated using WS-Trust (WS-Trust) or WS-SecureConversation (WS-SC) according to a nested binding, which is itself a symmetric binding that uses a negotiation protocol.</span></span> <span data-ttu-id="99146-580">Anlaşma Protokolü, mümkün olduğunda istemci ve sunucu kimlik doğrulaması gerçekleştirmek için Kerberos kullanır.</span><span class="sxs-lookup"><span data-stu-id="99146-580">The negotiation protocol will use Kerberos to perform client and server authentication if possible.</span></span> <span data-ttu-id="99146-581">Kerberos kullanılamıyorsa, NTLM olarak geri döner.</span><span class="sxs-lookup"><span data-stu-id="99146-581">If Kerberos cannot be used, it will fall back to NTLM.</span></span>  
  
 <span data-ttu-id="99146-582">İlke</span><span class="sxs-lookup"><span data-stu-id="99146-582">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="99146-583">Güvenlik üstbilgi örnekler: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="99146-583">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="99146-584">İstek</span><span class="sxs-lookup"><span data-stu-id="99146-584">Request</span></span>  
  
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
  
 <span data-ttu-id="99146-585">Yanıt</span><span class="sxs-lookup"><span data-stu-id="99146-585">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="99146-586">Güvenlik üstbilgi örnekler: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="99146-586">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="99146-587">İstek</span><span class="sxs-lookup"><span data-stu-id="99146-587">Request</span></span>  
  
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
  
 <span data-ttu-id="99146-588">Yanıt</span><span class="sxs-lookup"><span data-stu-id="99146-588">Response</span></span>  
  
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

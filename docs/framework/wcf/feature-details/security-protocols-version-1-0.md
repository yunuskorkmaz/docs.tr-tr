---
title: Güvenlik Protokolleri sürüm 1.0
ms.date: 03/30/2017
ms.assetid: ee3402d2-1076-410b-a3cb-fae0372bd7af
ms.openlocfilehash: e22150d21638cffdf804008c32285f900bb1e263
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459048"
---
# <a name="security-protocols-version-10"></a><span data-ttu-id="6b811-102">Güvenlik Protokolleri sürüm 1.0</span><span class="sxs-lookup"><span data-stu-id="6b811-102">Security Protocols version 1.0</span></span>
<span data-ttu-id="6b811-103">Web Hizmetleri Güvenliği protokolleri, mevcut tüm kurumsal mesajlaşma güvenlik gereksinimlerini kapsayan Web Hizmetleri güvenlik mekanizmaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="6b811-103">The Web Services Security Protocols provide Web services security mechanisms that cover all existing enterprise messaging security requirements.</span></span> <span data-ttu-id="6b811-104">Bu bölümde, aşağıdaki Web Hizmetleri güvenlik protokollerinin Windows Communication Foundation (WCF) sürüm 1,0 ayrıntıları (<xref:System.ServiceModel.Channels.SecurityBindingElement>uygulanır) açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6b811-104">This section describes the Windows Communication Foundation (WCF) version 1.0 details (implemented in the <xref:System.ServiceModel.Channels.SecurityBindingElement>) for the following Web services security protocols.</span></span>  
  
|<span data-ttu-id="6b811-105">Belirtim/belge</span><span class="sxs-lookup"><span data-stu-id="6b811-105">Specification/Document</span></span>|<span data-ttu-id="6b811-106">Bağlantı</span><span class="sxs-lookup"><span data-stu-id="6b811-106">Link</span></span>|  
|-|-|  
|<span data-ttu-id="6b811-107">WSS: SOAP Iletisi güvenliği 1,0</span><span class="sxs-lookup"><span data-stu-id="6b811-107">WSS: SOAP Message Security 1.0</span></span>|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf>|
|<span data-ttu-id="6b811-108">WSS: Kullanıcı adı belirteç profili 1,0</span><span class="sxs-lookup"><span data-stu-id="6b811-108">WSS: Username Token Profile 1.0</span></span>|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf>|
|<span data-ttu-id="6b811-109">WSS: x509 belirteç profili 1,0</span><span class="sxs-lookup"><span data-stu-id="6b811-109">WSS: X509 Token Profile 1.0</span></span>|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0.pdf>|
|<span data-ttu-id="6b811-110">WSS: SAML 1,1 belirteç profili 1,0</span><span class="sxs-lookup"><span data-stu-id="6b811-110">WSS: SAML 1.1 Token Profile 1.0</span></span>|<https://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.0.pdf>|
|<span data-ttu-id="6b811-111">WSS: SOAP Iletisi güvenliği 1,1</span><span class="sxs-lookup"><span data-stu-id="6b811-111">WSS: SOAP Message Security 1.1</span></span>|<https://www.oasis-open.org/committees/download.php/16790/wss-v1.1-spec-os-SOAPMessageSecurity.pdf>|
|<span data-ttu-id="6b811-112">WSS Kullanıcı adı belirteç profili 1,1</span><span class="sxs-lookup"><span data-stu-id="6b811-112">WSS Username Token Profile 1.1</span></span>|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf>|
|<span data-ttu-id="6b811-113">WSS: X. 509.440 belirteç profili 1,1</span><span class="sxs-lookup"><span data-stu-id="6b811-113">WSS: X.509 Token Profile 1.1</span></span>|<https://www.oasis-open.org/committees/download.php/16785/wss-v1.1-spec-os-x509TokenProfile.pdf>|
|<span data-ttu-id="6b811-114">WSS: Kerberos belirteç profili 1,1</span><span class="sxs-lookup"><span data-stu-id="6b811-114">WSS: Kerberos Token Profile 1.1</span></span>|<https://www.oasis-open.org/committees/download.php/16788/wss-v1.1-spec-os-KerberosTokenProfile.pdf>|
|<span data-ttu-id="6b811-115">WSS: SAML 1,1 belirteç profili 1,1</span><span class="sxs-lookup"><span data-stu-id="6b811-115">WSS: SAML 1.1 Token Profile 1.1</span></span>|<https://www.oasis-open.org/committees/download.php/16768/wss-v1.1-spec-os-SAMLTokenProfile.pdf>|
|<span data-ttu-id="6b811-116">WS-Secure konuşması</span><span class="sxs-lookup"><span data-stu-id="6b811-116">WS-Secure Conversation</span></span>|<https://specs.xmlsoap.org/ws/2005/02/sc/WS-SecureConversation.pdf>|
|<span data-ttu-id="6b811-117">WS-Trust</span><span class="sxs-lookup"><span data-stu-id="6b811-117">WS-Trust</span></span>|<https://specs.xmlsoap.org/ws/2005/02/trust/ws-trust.pdf>|
|<span data-ttu-id="6b811-118">Uygulama notunun:</span><span class="sxs-lookup"><span data-stu-id="6b811-118">Application Note:</span></span><br /><br /> <span data-ttu-id="6b811-119">TLS el sıkışması için WS-Trust kullanma</span><span class="sxs-lookup"><span data-stu-id="6b811-119">Using WS-Trust for TLS Handshake</span></span>|<span data-ttu-id="6b811-120">Yayımlanacak</span><span class="sxs-lookup"><span data-stu-id="6b811-120">To be published</span></span>|  
|<span data-ttu-id="6b811-121">Uygulama notunun:</span><span class="sxs-lookup"><span data-stu-id="6b811-121">Application Note:</span></span><br /><br /> <span data-ttu-id="6b811-122">SPNEGO için WS-Trust kullanma</span><span class="sxs-lookup"><span data-stu-id="6b811-122">Using WS-Trust for SPNEGO</span></span>|<span data-ttu-id="6b811-123">Yayımlanacak</span><span class="sxs-lookup"><span data-stu-id="6b811-123">To be published</span></span>|  
|<span data-ttu-id="6b811-124">Uygulama notunun:</span><span class="sxs-lookup"><span data-stu-id="6b811-124">Application Note:</span></span><br /><br /> <span data-ttu-id="6b811-125">Web Hizmetleri, uç nokta başvurularını ve kimliğini adresleyen</span><span class="sxs-lookup"><span data-stu-id="6b811-125">Web Services Addressing Endpoint References And Identity</span></span>|<span data-ttu-id="6b811-126">Yayımlanacak</span><span class="sxs-lookup"><span data-stu-id="6b811-126">To be published</span></span>|  
|<span data-ttu-id="6b811-127">WS-SecurityPolicy 1,1</span><span class="sxs-lookup"><span data-stu-id="6b811-127">WS-SecurityPolicy 1.1</span></span><br /><br /> <span data-ttu-id="6b811-128">(2005/07)</span><span class="sxs-lookup"><span data-stu-id="6b811-128">(2005/07)</span></span>|<https://specs.xmlsoap.org/ws/2005/07/securitypolicy/ws-securitypolicy.pdf><br /><br /> <span data-ttu-id="6b811-129">OASSıS WS-SX Technical komite 'a gönderilen [Errata](https://lists.oasis-open.org/archives/ws-sx/200512/msg00017.html) tarafından değiştirilen</span><span class="sxs-lookup"><span data-stu-id="6b811-129">as amended by [errata](https://lists.oasis-open.org/archives/ws-sx/200512/msg00017.html) submitted to OASIS WS-SX Technical Committee</span></span> |  
  
 <span data-ttu-id="6b811-130">WCF, sürüm 1, Web Hizmetleri güvenlik yapılandırması için temel olarak kullanılabilecek 17 kimlik doğrulama modu sağlar.</span><span class="sxs-lookup"><span data-stu-id="6b811-130">WCF, version 1, provides 17 authentication modes that can be used as the basis for Web services security configuration.</span></span> <span data-ttu-id="6b811-131">Her mod ortak bir dağıtım gereksinimleri kümesi için iyileştirilmiştir, örneğin:</span><span class="sxs-lookup"><span data-stu-id="6b811-131">Each mode is optimized for a common set of deployment requirements, such as:</span></span>  
  
- <span data-ttu-id="6b811-132">İstemci ve hizmetin kimliğini doğrulamak için kullanılan kimlik bilgileri.</span><span class="sxs-lookup"><span data-stu-id="6b811-132">Credentials used to authenticate client and service.</span></span>  
  
- <span data-ttu-id="6b811-133">İleti veya aktarım güvenliği koruma mekanizmaları.</span><span class="sxs-lookup"><span data-stu-id="6b811-133">Message or transport security protection mechanisms.</span></span>  
  
- <span data-ttu-id="6b811-134">İleti değişimi desenleri.</span><span class="sxs-lookup"><span data-stu-id="6b811-134">Message exchange patterns.</span></span>  
  
|<span data-ttu-id="6b811-135">Kimlik doğrulama modu</span><span class="sxs-lookup"><span data-stu-id="6b811-135">Authentication Mode</span></span>|<span data-ttu-id="6b811-136">İstemci kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="6b811-136">Client Authentication</span></span>|<span data-ttu-id="6b811-137">Sunucu kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="6b811-137">Server Authentication</span></span>|<span data-ttu-id="6b811-138">Mod</span><span class="sxs-lookup"><span data-stu-id="6b811-138">Mode</span></span>|  
|-------------------------|---------------------------|---------------------------|----------|  
|<span data-ttu-id="6b811-139">UserNameOverTransport</span><span class="sxs-lookup"><span data-stu-id="6b811-139">UserNameOverTransport</span></span>|<span data-ttu-id="6b811-140">Kullanıcı adı/parola</span><span class="sxs-lookup"><span data-stu-id="6b811-140">User name/password</span></span>|<span data-ttu-id="6b811-141">X509</span><span class="sxs-lookup"><span data-stu-id="6b811-141">X509</span></span>|<span data-ttu-id="6b811-142">Aktarım</span><span class="sxs-lookup"><span data-stu-id="6b811-142">Transport</span></span>|  
|<span data-ttu-id="6b811-143">CertificateOverTransport</span><span class="sxs-lookup"><span data-stu-id="6b811-143">CertificateOverTransport</span></span>|<span data-ttu-id="6b811-144">X509</span><span class="sxs-lookup"><span data-stu-id="6b811-144">X509</span></span>|<span data-ttu-id="6b811-145">X509</span><span class="sxs-lookup"><span data-stu-id="6b811-145">X509</span></span>|<span data-ttu-id="6b811-146">Aktarım</span><span class="sxs-lookup"><span data-stu-id="6b811-146">Transport</span></span>|  
|<span data-ttu-id="6b811-147">KerberosOverTransport</span><span class="sxs-lookup"><span data-stu-id="6b811-147">KerberosOverTransport</span></span>|<span data-ttu-id="6b811-148">Windows</span><span class="sxs-lookup"><span data-stu-id="6b811-148">Windows</span></span>|<span data-ttu-id="6b811-149">X509</span><span class="sxs-lookup"><span data-stu-id="6b811-149">X509</span></span>|<span data-ttu-id="6b811-150">Aktarım</span><span class="sxs-lookup"><span data-stu-id="6b811-150">Transport</span></span>|  
|<span data-ttu-id="6b811-151">IssuedTokenOverTransport</span><span class="sxs-lookup"><span data-stu-id="6b811-151">IssuedTokenOverTransport</span></span>|<span data-ttu-id="6b811-152">Federasyon</span><span class="sxs-lookup"><span data-stu-id="6b811-152">Federated</span></span>|<span data-ttu-id="6b811-153">X509</span><span class="sxs-lookup"><span data-stu-id="6b811-153">X509</span></span>|<span data-ttu-id="6b811-154">Aktarım</span><span class="sxs-lookup"><span data-stu-id="6b811-154">Transport</span></span>|  
|<span data-ttu-id="6b811-155">SspiNegotiatedOverTransport</span><span class="sxs-lookup"><span data-stu-id="6b811-155">SspiNegotiatedOverTransport</span></span>|<span data-ttu-id="6b811-156">Üzerinde anlaşılan Windows SSPI</span><span class="sxs-lookup"><span data-stu-id="6b811-156">Windows Sspi Negotiated</span></span>|<span data-ttu-id="6b811-157">Üzerinde anlaşılan Windows SSPI</span><span class="sxs-lookup"><span data-stu-id="6b811-157">Windows Sspi Negotiated</span></span>|<span data-ttu-id="6b811-158">Aktarım</span><span class="sxs-lookup"><span data-stu-id="6b811-158">Transport</span></span>|  
|<span data-ttu-id="6b811-159">AnonymousForCertificate</span><span class="sxs-lookup"><span data-stu-id="6b811-159">AnonymousForCertificate</span></span>|<span data-ttu-id="6b811-160">Yok.</span><span class="sxs-lookup"><span data-stu-id="6b811-160">None</span></span>|<span data-ttu-id="6b811-161">X509</span><span class="sxs-lookup"><span data-stu-id="6b811-161">X509</span></span>|<span data-ttu-id="6b811-162">İleti</span><span class="sxs-lookup"><span data-stu-id="6b811-162">Message</span></span>|  
|<span data-ttu-id="6b811-163">UserNameForCertificate</span><span class="sxs-lookup"><span data-stu-id="6b811-163">UserNameForCertificate</span></span>|<span data-ttu-id="6b811-164">Kullanıcı adı/parola</span><span class="sxs-lookup"><span data-stu-id="6b811-164">User name/password</span></span>|<span data-ttu-id="6b811-165">X509</span><span class="sxs-lookup"><span data-stu-id="6b811-165">X509</span></span>|<span data-ttu-id="6b811-166">İleti</span><span class="sxs-lookup"><span data-stu-id="6b811-166">Message</span></span>|  
|<span data-ttu-id="6b811-167">Çoklu sertifika</span><span class="sxs-lookup"><span data-stu-id="6b811-167">MutualCertificate</span></span>|<span data-ttu-id="6b811-168">X509</span><span class="sxs-lookup"><span data-stu-id="6b811-168">X509</span></span>|<span data-ttu-id="6b811-169">X509</span><span class="sxs-lookup"><span data-stu-id="6b811-169">X509</span></span>|<span data-ttu-id="6b811-170">İleti</span><span class="sxs-lookup"><span data-stu-id="6b811-170">Message</span></span>|  
|<span data-ttu-id="6b811-171">Değişken Uıalcertificateduplex</span><span class="sxs-lookup"><span data-stu-id="6b811-171">MutualCertificateDuplex</span></span>|<span data-ttu-id="6b811-172">X509</span><span class="sxs-lookup"><span data-stu-id="6b811-172">X509</span></span>|<span data-ttu-id="6b811-173">X509</span><span class="sxs-lookup"><span data-stu-id="6b811-173">X509</span></span>|<span data-ttu-id="6b811-174">İleti</span><span class="sxs-lookup"><span data-stu-id="6b811-174">Message</span></span>|  
|<span data-ttu-id="6b811-175">IssuedTokenForCertificate</span><span class="sxs-lookup"><span data-stu-id="6b811-175">IssuedTokenForCertificate</span></span>|<span data-ttu-id="6b811-176">Federasyon</span><span class="sxs-lookup"><span data-stu-id="6b811-176">Federated</span></span>|<span data-ttu-id="6b811-177">X509</span><span class="sxs-lookup"><span data-stu-id="6b811-177">X509</span></span>|<span data-ttu-id="6b811-178">İleti</span><span class="sxs-lookup"><span data-stu-id="6b811-178">Message</span></span>|  
|<span data-ttu-id="6b811-179">Kerberos</span><span class="sxs-lookup"><span data-stu-id="6b811-179">Kerberos</span></span>|<span data-ttu-id="6b811-180">Windows</span><span class="sxs-lookup"><span data-stu-id="6b811-180">Windows</span></span>|<span data-ttu-id="6b811-181">Windows</span><span class="sxs-lookup"><span data-stu-id="6b811-181">Windows</span></span>|<span data-ttu-id="6b811-182">İleti</span><span class="sxs-lookup"><span data-stu-id="6b811-182">Message</span></span>|  
|<span data-ttu-id="6b811-183">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="6b811-183">IssuedToken</span></span>|<span data-ttu-id="6b811-184">Federasyon</span><span class="sxs-lookup"><span data-stu-id="6b811-184">Federated</span></span>|<span data-ttu-id="6b811-185">Federasyon</span><span class="sxs-lookup"><span data-stu-id="6b811-185">Federated</span></span>|<span data-ttu-id="6b811-186">İleti</span><span class="sxs-lookup"><span data-stu-id="6b811-186">Message</span></span>|  
|<span data-ttu-id="6b811-187">SspiNegotiated</span><span class="sxs-lookup"><span data-stu-id="6b811-187">SspiNegotiated</span></span>|<span data-ttu-id="6b811-188">Üzerinde anlaşılan Windows SSPI</span><span class="sxs-lookup"><span data-stu-id="6b811-188">Windows Sspi Negotiated</span></span>|<span data-ttu-id="6b811-189">Üzerinde anlaşılan Windows SSPI</span><span class="sxs-lookup"><span data-stu-id="6b811-189">Windows Sspi Negotiated</span></span>|<span data-ttu-id="6b811-190">İleti</span><span class="sxs-lookup"><span data-stu-id="6b811-190">Message</span></span>|  
|<span data-ttu-id="6b811-191">Anonymousforsslanlaşmalı</span><span class="sxs-lookup"><span data-stu-id="6b811-191">AnonymousForSslNegotiated</span></span>|<span data-ttu-id="6b811-192">Yok.</span><span class="sxs-lookup"><span data-stu-id="6b811-192">None</span></span>|<span data-ttu-id="6b811-193">X509, TLS-Nego</span><span class="sxs-lookup"><span data-stu-id="6b811-193">X509, TLS-Nego</span></span>|<span data-ttu-id="6b811-194">İleti</span><span class="sxs-lookup"><span data-stu-id="6b811-194">Message</span></span>|  
|<span data-ttu-id="6b811-195">Usernameforsslanlaşmalı</span><span class="sxs-lookup"><span data-stu-id="6b811-195">UserNameForSslNegotiated</span></span>|<span data-ttu-id="6b811-196">Kullanıcı adı/parola</span><span class="sxs-lookup"><span data-stu-id="6b811-196">User name/password</span></span>|<span data-ttu-id="6b811-197">X509, TLS-Nego</span><span class="sxs-lookup"><span data-stu-id="6b811-197">X509, TLS-Nego</span></span>|<span data-ttu-id="6b811-198">İleti</span><span class="sxs-lookup"><span data-stu-id="6b811-198">Message</span></span>|  
|<span data-ttu-id="6b811-199">Değişken anlaşmalı</span><span class="sxs-lookup"><span data-stu-id="6b811-199">MutualSslNegotiated</span></span>|<span data-ttu-id="6b811-200">X509</span><span class="sxs-lookup"><span data-stu-id="6b811-200">X509</span></span>|<span data-ttu-id="6b811-201">X509, TLS-Nego</span><span class="sxs-lookup"><span data-stu-id="6b811-201">X509, TLS-Nego</span></span>|<span data-ttu-id="6b811-202">İleti</span><span class="sxs-lookup"><span data-stu-id="6b811-202">Message</span></span>|  
|<span data-ttu-id="6b811-203">Issuedtokenforsslanlaşmalı</span><span class="sxs-lookup"><span data-stu-id="6b811-203">IssuedTokenForSslNegotiated</span></span>|<span data-ttu-id="6b811-204">Federasyon</span><span class="sxs-lookup"><span data-stu-id="6b811-204">Federated</span></span>|<span data-ttu-id="6b811-205">X509, TLS-Nego</span><span class="sxs-lookup"><span data-stu-id="6b811-205">X509, TLS-Nego</span></span>|<span data-ttu-id="6b811-206">İleti</span><span class="sxs-lookup"><span data-stu-id="6b811-206">Message</span></span>|  
  
 <span data-ttu-id="6b811-207">Bu tür kimlik doğrulama modlarını kullanan uç noktalar, WS-SecurityPolicy (WS-SP) kullanarak güvenlik gereksinimlerini ifade edebilir.</span><span class="sxs-lookup"><span data-stu-id="6b811-207">Endpoints using such authentication modes can express their security requirements using WS-SecurityPolicy (WS-SP).</span></span> <span data-ttu-id="6b811-208">Bu belgede, her kimlik doğrulama modu için güvenlik üst bilgisi ve altyapı iletilerinin yapısı açıklanmakta ve ilke ve ileti örnekleri verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6b811-208">This document describes the structure of security header and infrastructure messages for each authentication mode and provides examples of policies and messages.</span></span>  
  
 <span data-ttu-id="6b811-209">WCF, uygulamalar arasında çok ileti alışverişlerini korumak için güvenli oturumlar desteği sağlamak üzere WS-SecureConversation kullanır.</span><span class="sxs-lookup"><span data-stu-id="6b811-209">WCF leverages WS-SecureConversation to provide secure sessions support to protect multi-message exchanges between applications.</span></span>  <span data-ttu-id="6b811-210">Uygulama ayrıntıları için aşağıda "güvenli oturumlar" başlığına bakın.</span><span class="sxs-lookup"><span data-stu-id="6b811-210">See "Secure Sessions" below for implementation details.</span></span>  
  
 <span data-ttu-id="6b811-211">WCF, kimlik doğrulama modlarına ek olarak, çoğu ileti güvenlik tabanlı kimlik doğrulama modu için uygulanan genel koruma mekanizmalarını denetlemek için ayarlar sağlar; örneğin: imza sırası, şifreleme işlemleri, algoritma paketleri, anahtar türetme ve imza onayı.</span><span class="sxs-lookup"><span data-stu-id="6b811-211">In addition to authentication modes, WCF provides settings to control common protection mechanisms that apply to most message security-based authentication modes, for example: order of signature versus encryption operations, algorithm suites, key derivation, and signature confirmation.</span></span>  
  
 <span data-ttu-id="6b811-212">Bu belgede aşağıdaki ön ekler ve ad alanları kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6b811-212">The following prefixes and namespaces are used in this document.</span></span>  
  
|<span data-ttu-id="6b811-213">koy</span><span class="sxs-lookup"><span data-stu-id="6b811-213">Prefix</span></span>|<span data-ttu-id="6b811-214">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="6b811-214">Namespace</span></span>|  
|------------|---------------|  
|<span data-ttu-id="6b811-215">s</span><span class="sxs-lookup"><span data-stu-id="6b811-215">s</span></span>|<http://www.w3.org/2003/05/soap-envelope/>|
|<span data-ttu-id="6b811-216">SP2</span><span class="sxs-lookup"><span data-stu-id="6b811-216">sp</span></span>|<http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/>|
|<span data-ttu-id="6b811-217">A</span><span class="sxs-lookup"><span data-stu-id="6b811-217">a</span></span>|<http://www.w3.org/2005/08/addressing>|  
|<span data-ttu-id="6b811-218">WSO</span><span class="sxs-lookup"><span data-stu-id="6b811-218">wsse</span></span>|<span data-ttu-id="6b811-219">TBD – OASSıS WSS 1,0 URI 'SI</span><span class="sxs-lookup"><span data-stu-id="6b811-219">TBD – OASIS WSS 1.0 URI</span></span>|  
|<span data-ttu-id="6b811-220">wsse11</span><span class="sxs-lookup"><span data-stu-id="6b811-220">wsse11</span></span>|<span data-ttu-id="6b811-221">TBD – OASSıS WSS 1,1 URI 'SI</span><span class="sxs-lookup"><span data-stu-id="6b811-221">TBD – OASIS WSS 1.1 URI</span></span>|  
|<span data-ttu-id="6b811-222">WSU dili</span><span class="sxs-lookup"><span data-stu-id="6b811-222">wsu</span></span>|<span data-ttu-id="6b811-223">TBD – OASSıS WSS 1,0 yardımcı programı URI 'SI</span><span class="sxs-lookup"><span data-stu-id="6b811-223">TBD – OASIS WSS 1.0 Utility URI</span></span>|  
|<span data-ttu-id="6b811-224">FID</span><span class="sxs-lookup"><span data-stu-id="6b811-224">ds</span></span>|<span data-ttu-id="6b811-225">TBD – W3C XMLDSIG URI 'SI</span><span class="sxs-lookup"><span data-stu-id="6b811-225">TBD – W3C XMLDSig URI</span></span>|  
|<span data-ttu-id="6b811-226">WST</span><span class="sxs-lookup"><span data-stu-id="6b811-226">wst</span></span>|<span data-ttu-id="6b811-227">TBD – WS-Trust 2005/02 URI</span><span class="sxs-lookup"><span data-stu-id="6b811-227">TBD – WS-Trust 2005/02 URI</span></span>|  
|<span data-ttu-id="6b811-228">wssc</span><span class="sxs-lookup"><span data-stu-id="6b811-228">wssc</span></span>|<span data-ttu-id="6b811-229">TBD – WS-SecureConversation 2005/02 URI 'SI</span><span class="sxs-lookup"><span data-stu-id="6b811-229">TBD – WS-SecureConversation 2005/02 URI</span></span>|  
|<span data-ttu-id="6b811-230">Wonu dili</span><span class="sxs-lookup"><span data-stu-id="6b811-230">wsaw</span></span>|<span data-ttu-id="6b811-231">TBD-WS-adresleme ilkesi ad alanı</span><span class="sxs-lookup"><span data-stu-id="6b811-231">TBD - WS-Addressing policy namespace</span></span>|  
|<span data-ttu-id="6b811-232">WSP</span><span class="sxs-lookup"><span data-stu-id="6b811-232">wsp</span></span>|<http://schemas.xmlsoap.org/ws/2004/09/policy>|  
|<span data-ttu-id="6b811-233">MSSP</span><span class="sxs-lookup"><span data-stu-id="6b811-233">mssp</span></span>|<http://schemas.xmlsoap.org/ws/2005/07/securitypolicy>|
  
## <a name="1-token-profiles"></a><span data-ttu-id="6b811-234">1. belirteç profilleri</span><span class="sxs-lookup"><span data-stu-id="6b811-234">1. Token Profiles</span></span>  
 <span data-ttu-id="6b811-235">Web Hizmetleri Güvenliği belirtimleri güvenlik belirteçleri olarak kimlik bilgisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6b811-235">Web Services Security specifications represent credential as security tokens.</span></span> <span data-ttu-id="6b811-236">WCF aşağıdaki belirteç türlerini destekler:</span><span class="sxs-lookup"><span data-stu-id="6b811-236">WCF supports the following token types:</span></span>  
  
### <a name="11-usernametoken"></a><span data-ttu-id="6b811-237">1,1 UsernameToken</span><span class="sxs-lookup"><span data-stu-id="6b811-237">1.1 UsernameToken</span></span>  
 <span data-ttu-id="6b811-238">WCF aşağıdaki kısıtlamalara sahip UsernameToken10 ve UsernameToken11 profillerini izler:</span><span class="sxs-lookup"><span data-stu-id="6b811-238">WCF follows UsernameToken10 and UsernameToken11 profiles with the following constraints:</span></span>  
  
 <span data-ttu-id="6b811-239">UsernameToken\Password öğesinde R1101 PasswordType özniteliği atlanmış veya değer #PasswordText (varsayılan) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6b811-239">R1101 PasswordType attribute on UsernameToken\Password element MUST be either omitted or have value #PasswordText (default).</span></span>  
  
 <span data-ttu-id="6b811-240">Bunlardan biri, genişletilebilirlik kullanarak #PasswordDigest uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="6b811-240">One can implement the #PasswordDigest using extensibility.</span></span> <span data-ttu-id="6b811-241">#PasswordDigest genellikle yeterince güvenli bir parola koruma mekanizması olması gözlemlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="6b811-241">It has been observed that #PasswordDigest was often mistaken to be a secure enough password protection mechanism.</span></span> <span data-ttu-id="6b811-242">Ancak #PasswordDigest, UsernameToken şifrelemesinin bir alternatifi olarak kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="6b811-242">But #PasswordDigest cannot serve as a substitute for encryption of the UsernameToken.</span></span> <span data-ttu-id="6b811-243">#PasswordDigest birincil amacı, yeniden yürütme saldırılarına karşı koruma sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="6b811-243">The primary goal of #PasswordDigest is protection against replay attacks.</span></span> <span data-ttu-id="6b811-244">WCF kimlik doğrulama modlarında, yeniden yürütme saldırı tehditleri ileti imzaları kullanılarak azaltıldığında.</span><span class="sxs-lookup"><span data-stu-id="6b811-244">In WCF authentication modes, replay attack threats are mitigated by using message signatures.</span></span>  
  
 <span data-ttu-id="6b811-245">B1102 WCF hiçbir şekilde hiçbir şekilde anahtar vermez ve UsernameToken alt öğelerini oluşturmuştur.</span><span class="sxs-lookup"><span data-stu-id="6b811-245">B1102 WCF never emits Nonce and Created sub-elements of the UsernameToken.</span></span>  
  
 <span data-ttu-id="6b811-246">Bu alt öğeler, yeniden yürütmeyi algılamaya yardımcı olmayı amaçlar.</span><span class="sxs-lookup"><span data-stu-id="6b811-246">These sub-elements are intended to help replay detection.</span></span> <span data-ttu-id="6b811-247">WCF bunun yerine ileti imzalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="6b811-247">WCF uses message signatures instead.</span></span>  
  
 <span data-ttu-id="6b811-248">OASSıS WSS SOAP Iletisi güvenliği UsernameToken profili 1,1 (UsernameToken11) parola özelliğinden anahtar türetme sunmuştur.</span><span class="sxs-lookup"><span data-stu-id="6b811-248">OASIS WSS SOAP Message Security UsernameToken Profile 1.1 (UsernameToken11) introduced key derivation from password feature.</span></span>  
  
 <span data-ttu-id="6b811-249">B1103 UsernameToken parolası, anahtar türetmede kullanılmamalıdır ve bu nedenle şifreleme işlemleri için kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="6b811-249">B1103 UsernameToken password MUST not be used for key derivation and therefore for cryptographic operations.</span></span>  
  
 <span data-ttu-id="6b811-250">Korale: parolalar genellikle şifreleme işlemleri için kullanılmak üzere çok zayıf kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="6b811-250">Rationale: passwords are generally considered too weak to be used for cryptographic operations.</span></span>  
  
### <a name="12-x509-token"></a><span data-ttu-id="6b811-251">1,2 x509 belirteci</span><span class="sxs-lookup"><span data-stu-id="6b811-251">1.2 X509 Token</span></span>  
 <span data-ttu-id="6b811-252">WCF, kimlik bilgisi türü olarak X509v3 sertifikalarını destekler ve aşağıdaki kısıtlamalara sahip X509TokenProfile 1.0 ve X509TokenProfile 1.1 ' i izler:</span><span class="sxs-lookup"><span data-stu-id="6b811-252">WCF supports X509v3 certificates as a credential type and follows X509TokenProfile1.0 and X509TokenProfile1.1 with the following constraints:</span></span>  
  
 <span data-ttu-id="6b811-253">R1201, BinarySecurityToken öğesindeki ValueType özniteliği bir X509v3 sertifikası içerdiğinde değer #X509v3 sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6b811-253">R1201 The ValueType attribute on the BinarySecurityToken element must have value #X509v3 when it contains an X509v3 certificate.</span></span>  
  
 <span data-ttu-id="6b811-254">WSS x509 belirteç profili 1,0 ve 1,1 de #X509PKIPathv1 ve #PKCS7 değer türleri olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6b811-254">WSS X509 Token Profile 1.0 and 1.1 define also #X509PKIPathv1 and #PKCS7 as value types.</span></span> <span data-ttu-id="6b811-255">WCF bu türleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="6b811-255">WCF does not support these types.</span></span>  
  
 <span data-ttu-id="6b811-256">R1202 bir x509 sertifikası içinde bir subjectKeyIdentifier (kayak) uzantısı varsa, ' nin ValueType özniteliğiyle birlikte #X509SubjectKeyIdentifier ve içerik Base64 kodlamalı değeri olan, belirteç için dış başvurular için anahtar tanımlayıcısı kullanılmalıdır. Sertifikanın Kayak uzantısı.</span><span class="sxs-lookup"><span data-stu-id="6b811-256">R1202 If a SubjectKeyIdentifier (SKI) extension is present in an X509 certificate, wsse:KeyIdentifier should be used for external references to the token, with the ValueType attribute as #X509SubjectKeyIdentifier and its content the base64-encoded value of certificate's SKI extension.</span></span>  
  
 <span data-ttu-id="6b811-257">Kayak başvuruları yaygın olarak uygulanırlar ve yüksek oranda çalışabilen bir dış başvuru türü olarak kanıtlanmış olur.</span><span class="sxs-lookup"><span data-stu-id="6b811-257">SKI references are widely implemented and proven to be a highly interoperable external reference type.</span></span>  
  
 <span data-ttu-id="6b811-258">R1203 x509 güvenlik belirtecine bir dış başvuru DS: X509IssuerSerial KULLANMAMALıDıR.</span><span class="sxs-lookup"><span data-stu-id="6b811-258">R1203 An external Reference to X509 Security Token SHOULD NOT use ds:X509IssuerSerial.</span></span>  
  
 <span data-ttu-id="6b811-259">R1204 X509TokenProfile 1.1 kullanılıyorsa, x509 güvenlik belirteci için bir dış başvuru, WS-Security 1,1 tarafından tanıtılan parmak izini kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6b811-259">R1204 If X509TokenProfile1.1 is in use, an external reference to X509 Security Token SHOULD use the thumbprint introduced by WS-Security 1.1.</span></span>  
  
 <span data-ttu-id="6b811-260">WCF, X509IssuerSerial destekler.</span><span class="sxs-lookup"><span data-stu-id="6b811-260">WCF supports X509IssuerSerial.</span></span> <span data-ttu-id="6b811-261">Ancak X509IssuerSerial ile birlikte çalışabilirlik sorunları vardır: WCF, X509IssuerSerial 'in iki değerini karşılaştırmak için bir dize kullanır.</span><span class="sxs-lookup"><span data-stu-id="6b811-261">However There are interoperability issues with X509IssuerSerial: WCF uses a string to compare two values of X509IssuerSerial.</span></span> <span data-ttu-id="6b811-262">Bu nedenle, konu adının bileşenlerini yeniden sipariş eden bir, bir WCF hizmetine bir sertifikaya başvuru gönderirse, bu durum bulunamamıştır.</span><span class="sxs-lookup"><span data-stu-id="6b811-262">Therefore if one reorders components of the Subject Name and sends to an WCF service a reference to a certificate, it may not be found.</span></span>  
  
### <a name="13-kerberos-token"></a><span data-ttu-id="6b811-263">1,3 Kerberos belirteci</span><span class="sxs-lookup"><span data-stu-id="6b811-263">1.3 Kerberos Token</span></span>  
 <span data-ttu-id="6b811-264">WCF, Windows kimlik doğrulaması amacıyla aşağıdaki kısıtlamalara sahip KerberosTokenProfile 1.1 'yi destekler:</span><span class="sxs-lookup"><span data-stu-id="6b811-264">WCF supports KerberosTokenProfile1.1 for the purpose of Windows authentication with the following constraints:</span></span>  
  
 <span data-ttu-id="6b811-265">R1301 bir Kerberos belirtecinin, GSS_API ve Kerberos belirtiminde tanımlanan bir GSS sarmalanmış Kerberos v4 AP_REQ değerini taşıması ve #GSS_Kerberosv5_AP_REQ değeri ile ValueType özniteliğine sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6b811-265">R1301 A Kerberos Token must carry the value of a GSS wrapped Kerberos v4 AP_REQ as defined in GSS_API and the Kerberos specification, and must have the ValueType attribute with the value #GSS_Kerberosv5_AP_REQ.</span></span>  
  
 <span data-ttu-id="6b811-266">WCF, tam bir AP-REQ değil, GSS sarmalanmış Kerberos AP-REQ kullanır.</span><span class="sxs-lookup"><span data-stu-id="6b811-266">WCF uses GSS wrapped Kerberos AP-REQ, not a bare AP-REQ.</span></span> <span data-ttu-id="6b811-267">Bu en iyi güvenlik uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="6b811-267">This is a security best practice.</span></span>  
  
### <a name="14-saml-v11-token"></a><span data-ttu-id="6b811-268">1,4 SAML v 1.1 belirteci</span><span class="sxs-lookup"><span data-stu-id="6b811-268">1.4 SAML v1.1 Token</span></span>  
 <span data-ttu-id="6b811-269">WCF, SAML v 1.1 belirteçleri için WSS SAML belirteci profilleri 1,0 ve 1,1 ' ü destekler.</span><span class="sxs-lookup"><span data-stu-id="6b811-269">WCF supports WSS SAML Token profiles 1.0 and 1.1 for SAML v1.1 tokens.</span></span> <span data-ttu-id="6b811-270">SAML belirteci biçimlerinin diğer sürümlerini uygulamak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="6b811-270">It is possible to implement other versions of SAML token formats.</span></span>  
  
### <a name="15-security-context-token"></a><span data-ttu-id="6b811-271">1,5 güvenlik bağlamı belirteci</span><span class="sxs-lookup"><span data-stu-id="6b811-271">1.5 Security Context Token</span></span>  
 <span data-ttu-id="6b811-272">WCF, WS-SecureConversation ' de tanıtılan güvenlik bağlamı belirtecini (SCT) destekler.</span><span class="sxs-lookup"><span data-stu-id="6b811-272">WCF supports the Security Context Token (SCT) introduced in WS-SecureConversation.</span></span> <span data-ttu-id="6b811-273">SCT, SecureConversation 'de kurulu bir güvenlik bağlamını ve aşağıda açıklanan ikili anlaşma protokolleri TLS ve SSPI 'yi temsil etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6b811-273">SCT is used to represent a security context established in SecureConversation as well as the binary negotiation protocols TLS and SSPI, described below.</span></span>  
  
## <a name="2-common-message-security-parameters"></a><span data-ttu-id="6b811-274">2. ortak Ileti güvenlik parametreleri</span><span class="sxs-lookup"><span data-stu-id="6b811-274">2. Common Message Security Parameters</span></span>  
  
### <a name="21-timestamp"></a><span data-ttu-id="6b811-275">2,1 zaman damgası</span><span class="sxs-lookup"><span data-stu-id="6b811-275">2.1 TimeStamp</span></span>  
 <span data-ttu-id="6b811-276">Zaman damgası varlığı, <xref:System.ServiceModel.Channels.SecurityBindingElement> sınıfının <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> özelliği kullanılarak denetlenir.</span><span class="sxs-lookup"><span data-stu-id="6b811-276">Timestamp presence is controlled using the <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> property of the <xref:System.ServiceModel.Channels.SecurityBindingElement> class.</span></span> <span data-ttu-id="6b811-277">WCF her zaman wsse: Created ve wsse: Expires alanları ile zaman damgası olarak serileştirir.</span><span class="sxs-lookup"><span data-stu-id="6b811-277">WCF always serializes wsse:TimeStamp with wsse:Created and wsse:Expires fields.</span></span> <span data-ttu-id="6b811-278">Wsse: imza kullanıldığında zaman damgası her zaman imzalanır.</span><span class="sxs-lookup"><span data-stu-id="6b811-278">The wsse:TimeStamp is always signed when signing is used.</span></span>  
  
### <a name="22-protection-order"></a><span data-ttu-id="6b811-279">2,2 koruma sırası</span><span class="sxs-lookup"><span data-stu-id="6b811-279">2.2 Protection Order</span></span>  
 <span data-ttu-id="6b811-280">WCF, "şifrelemeden önce Imzala" ve "oturum açmadan önce şifreleyin" (Güvenlik Ilkesi 1,1) ileti koruma sırasını destekler.</span><span class="sxs-lookup"><span data-stu-id="6b811-280">WCF supports the message protection order "Sign Before Encrypt" and "Encrypt Before Sign" (Security Policy 1.1).</span></span> <span data-ttu-id="6b811-281">Aşağıdakiler dahil olmak üzere "şifrelemeden önce imzala" önerilir: oturum açmadan önce şifrelemeden korunan iletiler, WS-Security 1,1 SignatureConfirmation mekanizması kullanılmadığı ve şifrelenmiş içerik üzerinde bir imza açık değilse imza değiştirme saldırılarına açık olur Denetim daha zordur.</span><span class="sxs-lookup"><span data-stu-id="6b811-281">"Sign Before Encrypt" is recommended for reasons including: messages protected with Encrypt Before Sign are open to signature substitution attacks unless the WS-Security 1.1 SignatureConfirmation mechanism is used, and a signature over encrypted content makes auditing harder.</span></span>  
  
### <a name="23-signature-protection"></a><span data-ttu-id="6b811-282">2,3 imza koruması</span><span class="sxs-lookup"><span data-stu-id="6b811-282">2.3 Signature Protection</span></span>  
 <span data-ttu-id="6b811-283">İmza kullanılmadan önce şifrelendiğinde, şifrelenmiş içeriği veya imzalama anahtarını tahmin etmeye yönelik deneme yanılma saldırılarını engellemek için imzayı korumanız önerilir (özellikle de, zayıf anahtar malzemeyle özel bir belirteç kullanıldığında).</span><span class="sxs-lookup"><span data-stu-id="6b811-283">When Encrypt Before Sign is used, it is recommended to protect the signature to prevent brute force attacks for guessing the encrypted content or the signing key (especially when a custom token is used with weak key material).</span></span>  
  
### <a name="24-algorithm-suite"></a><span data-ttu-id="6b811-284">2,4 algoritma paketi</span><span class="sxs-lookup"><span data-stu-id="6b811-284">2.4 Algorithm Suite</span></span>  
 <span data-ttu-id="6b811-285">WCF, Güvenlik Ilkesi 1,1 ' de listelenen tüm algoritma paketlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="6b811-285">WCF supports all algorithm suites listed in Security Policy 1.1.</span></span>  
  
### <a name="25-key-derivation"></a><span data-ttu-id="6b811-286">2,5 anahtar türetme</span><span class="sxs-lookup"><span data-stu-id="6b811-286">2.5 Key Derivation</span></span>  
 <span data-ttu-id="6b811-287">WCF, WS-SecureConversation bölümünde açıklandığı gibi "simetrik anahtarlar için anahtar türetme" kullanır.</span><span class="sxs-lookup"><span data-stu-id="6b811-287">WCF uses "Key Derivation for symmetric keys" as described in WS-SecureConversation.</span></span>  
  
### <a name="26-signature-confirmation"></a><span data-ttu-id="6b811-288">2,6 imza onayı</span><span class="sxs-lookup"><span data-stu-id="6b811-288">2.6 Signature Confirmation</span></span>  
 <span data-ttu-id="6b811-289">İmza onaylama, imza kümesini korumak için ortadaki adam saldırılarına karşı koruma sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="6b811-289">Signature confirmation can be as protection from middle man attacks to protect the set of signatures.</span></span>  
  
### <a name="27-security-header-layout"></a><span data-ttu-id="6b811-290">2,7 güvenlik üst bilgisi düzeni</span><span class="sxs-lookup"><span data-stu-id="6b811-290">2.7 Security Header Layout</span></span>  
 <span data-ttu-id="6b811-291">Her kimlik doğrulama modu, güvenlik üst bilgisi için belirli bir düzeni tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6b811-291">Each authentication mode describes a certain layout for the security header.</span></span> <span data-ttu-id="6b811-292">Güvenlik üst bilgisi içindeki öğeler yarı sıralanır.</span><span class="sxs-lookup"><span data-stu-id="6b811-292">Elements within the security header are semi-ordered.</span></span> <span data-ttu-id="6b811-293">Güvenlik üst bilgisi alt öğelerinin sırasını tanımlamak için, WS-Güvenlik Ilkesi aşağıdaki güvenlik üst bilgisi düzen modlarını tanımlar:</span><span class="sxs-lookup"><span data-stu-id="6b811-293">To define the order of security header child elements, WS-Security Policy defines the following security header layout modes:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6b811-294">Sert</span><span class="sxs-lookup"><span data-stu-id="6b811-294">Strict</span></span>|<span data-ttu-id="6b811-295">Öğeler, Güvenlik Ilkesi bölümünde açıklanan numaralandırılmış düzen kurallarından sonra, "kullanmadan önce bildir" genel ilkesine göre güvenlik üstbilgisine eklenir.</span><span class="sxs-lookup"><span data-stu-id="6b811-295">Items are added to the security header following the numbered layout rules described in Security Policy section 7.7.1 according to a general principle of "declare before use".</span></span>|  
|<span data-ttu-id="6b811-296">LAX</span><span class="sxs-lookup"><span data-stu-id="6b811-296">Lax</span></span>|<span data-ttu-id="6b811-297">Öğeler, WSS: SOAP Iletisi güvenliğine uyan herhangi bir sırada güvenlik başlığına eklenir.</span><span class="sxs-lookup"><span data-stu-id="6b811-297">Items are added to the security header in any order that conforms to WSS: SOAP Message Security.</span></span>|  
|<span data-ttu-id="6b811-298">Önce Laxtimestamp</span><span class="sxs-lookup"><span data-stu-id="6b811-298">LaxTimestampFirst</span></span>|<span data-ttu-id="6b811-299">Güvenlik üst bilgisindeki ilk öğenin bir WSO: Timestamp olması dışında LAX ile aynı</span><span class="sxs-lookup"><span data-stu-id="6b811-299">Same as Lax except that the first item in the security header must be a wsse:Timestamp</span></span>|  
|<span data-ttu-id="6b811-300">Laxtimestamp son</span><span class="sxs-lookup"><span data-stu-id="6b811-300">LaxTimestampLast</span></span>|<span data-ttu-id="6b811-301">Güvenlik üstbilgisindeki son öğenin bir WSO: Timestamp olması dışında LAX ile aynı</span><span class="sxs-lookup"><span data-stu-id="6b811-301">Same as lax except that the last item in the security header must be a wsse:Timestamp</span></span>|  
  
 <span data-ttu-id="6b811-302">WCF, güvenlik üst bilgisi düzeni için dört modunu destekler.</span><span class="sxs-lookup"><span data-stu-id="6b811-302">WCF supports all four modes for security header layout.</span></span> <span data-ttu-id="6b811-303">Güvenlik üst bilgisi yapısı ve aşağıdaki kimlik doğrulama modları için ileti örnekleri "katı" modunu izler.</span><span class="sxs-lookup"><span data-stu-id="6b811-303">Security header structure and message examples for authentication modes below follow the "Strict" mode.</span></span>  
  
## <a name="2-common-message-security-parameters"></a><span data-ttu-id="6b811-304">2. ortak Ileti güvenlik parametreleri</span><span class="sxs-lookup"><span data-stu-id="6b811-304">2. Common Message Security Parameters</span></span>  
 <span data-ttu-id="6b811-305">Bu bölümde, istemci ve hizmet tarafından değiştirilen iletilerde güvenlik üst bilgi yapısını gösteren örneklerle birlikte her bir kimlik doğrulama modu için örnek ilkeler sağlanır.</span><span class="sxs-lookup"><span data-stu-id="6b811-305">This section provides example policies for each authentication mode along with examples showing security header structure in messages exchanged by client and service.</span></span>  
  
### <a name="61-transport-protection"></a><span data-ttu-id="6b811-306">6,1 taşıma koruması</span><span class="sxs-lookup"><span data-stu-id="6b811-306">6.1 Transport Protection</span></span>  
 <span data-ttu-id="6b811-307">WCF, iletileri korumak için güvenli aktarım kullanan beş kimlik doğrulama modu sağlar; UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport ve SspiNegotiatedOverTransport.</span><span class="sxs-lookup"><span data-stu-id="6b811-307">WCF provides five authentication modes that use secure transport to protect messages; UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport and SspiNegotiatedOverTransport.</span></span>  
  
 <span data-ttu-id="6b811-308">Bu kimlik doğrulama modları, SecurityPolicy ' de açıklanan aktarım bağlaması kullanılarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6b811-308">These authentication modes are constructed using the transport binding described in SecurityPolicy.</span></span> <span data-ttu-id="6b811-309">UserNameOverTransport kimlik doğrulama modu için UsernameToken imzalı bir destekleme belirtecidir.</span><span class="sxs-lookup"><span data-stu-id="6b811-309">For the UserNameOverTransport authentication mode the UsernameToken is a signed supporting token.</span></span> <span data-ttu-id="6b811-310">Diğer kimlik doğrulama modlarında, belirteç imzalı bir onaylama belirteci olarak görünür.</span><span class="sxs-lookup"><span data-stu-id="6b811-310">For the other authentication modes the token appears as a signed endorsing token.</span></span> <span data-ttu-id="6b811-311">Ek C. 1.2 ve C. 1.3 SecurityPolicy, güvenlik üst bilgisi yerleşimini ayrıntılı olarak anlatmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6b811-311">Appendix C.1.2 and C.1.3 of SecurityPolicy describe the security header layout in detail.</span></span> <span data-ttu-id="6b811-312">Aşağıdaki örnek güvenlik üstbilgileri, belirli bir kimlik doğrulama modu için katı düzeni gösterir.</span><span class="sxs-lookup"><span data-stu-id="6b811-312">The following example security headers show the Strict layout for a given authentication mode.</span></span>  
  
 <span data-ttu-id="6b811-313">Her durumda belirteçlerin "türetilmiş anahtarlar" özelliğinin değeri "false" şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6b811-313">The value of the "Derived Keys" property for the tokens in all cases is "false".</span></span>  
  
 <span data-ttu-id="6b811-314">Aktarım bağlamasının çeşitli özelliklerinin değerleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="6b811-314">The values of the various properties of the transport binding are as follows:</span></span>  
  
 <span data-ttu-id="6b811-315">Zaman damgası: true</span><span class="sxs-lookup"><span data-stu-id="6b811-315">Timestamp: true</span></span>  
  
 <span data-ttu-id="6b811-316">Güvenlik üst bilgisi düzeni: katı</span><span class="sxs-lookup"><span data-stu-id="6b811-316">Security Header Layout: Strict</span></span>  
  
 <span data-ttu-id="6b811-317">Algoritma paketi: Basic256</span><span class="sxs-lookup"><span data-stu-id="6b811-317">Algorithm Suite: Basic256</span></span>  
  
#### <a name="611-usernameovertransport"></a><span data-ttu-id="6b811-318">6.1.1 UsernameOverTransport</span><span class="sxs-lookup"><span data-stu-id="6b811-318">6.1.1 UsernameOverTransport</span></span>  
 <span data-ttu-id="6b811-319">Bu kimlik doğrulama modu ile istemci, SOAP katmanında, her zaman başlatıcıdan alıcıya gönderilen imzalı bir destekleme belirteci olarak görünen bir Kullanıcı adı belirteci ile kimlik doğrular.</span><span class="sxs-lookup"><span data-stu-id="6b811-319">With this authentication mode, the client authenticates with a Username Token which appears at the SOAP layer as a signed supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="6b811-320">Hizmetin kimliği, aktarım katmanında bir X. 509.440 sertifikası kullanılarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="6b811-320">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="6b811-321">Kullanılan bağlama bir aktarım bağlamadır.</span><span class="sxs-lookup"><span data-stu-id="6b811-321">The binding used is a transport binding.</span></span>  
  
 <span data-ttu-id="6b811-322">İlke</span><span class="sxs-lookup"><span data-stu-id="6b811-322">Policy</span></span>  
  
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
  
 <span data-ttu-id="6b811-323">Güvenlik üst bilgisi düzeni</span><span class="sxs-lookup"><span data-stu-id="6b811-323">Security Header Layout</span></span>  
  
 <span data-ttu-id="6b811-324">İstek</span><span class="sxs-lookup"><span data-stu-id="6b811-324">Request</span></span>  
  
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
  
 <span data-ttu-id="6b811-325">Yanıtıyla</span><span class="sxs-lookup"><span data-stu-id="6b811-325">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="612-certificateovertransport"></a><span data-ttu-id="6b811-326">6.1.2 CertificateOverTransport</span><span class="sxs-lookup"><span data-stu-id="6b811-326">6.1.2 CertificateOverTransport</span></span>  
 <span data-ttu-id="6b811-327">Bu kimlik doğrulama modunda, istemci, her zaman başlatıcıdan alıcıya gönderilen bir onaylama destekleme belirteci olarak SOAP katmanında görünen bir X. 509.440 sertifikası kullanarak kimlik doğrular.</span><span class="sxs-lookup"><span data-stu-id="6b811-327">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as an endorsing supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="6b811-328">Hizmetin kimliği, aktarım katmanında bir X. 509.440 sertifikası kullanılarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="6b811-328">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="6b811-329">Kullanılan bağlama bir aktarım bağlamadır.</span><span class="sxs-lookup"><span data-stu-id="6b811-329">The binding used is a transport binding.</span></span>  
  
 <span data-ttu-id="6b811-330">İlke</span><span class="sxs-lookup"><span data-stu-id="6b811-330">Policy</span></span>  
  
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
  
 <span data-ttu-id="6b811-331">Güvenlik üst bilgisi düzeni</span><span class="sxs-lookup"><span data-stu-id="6b811-331">Security Header Layout</span></span>  
  
 <span data-ttu-id="6b811-332">İstek</span><span class="sxs-lookup"><span data-stu-id="6b811-332">Request</span></span>  
  
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
  
 <span data-ttu-id="6b811-333">Yanıtıyla</span><span class="sxs-lookup"><span data-stu-id="6b811-333">Response</span></span>  
  
```xml  
<o:Security>  
  <u:Timestamp u:Id="_0">  
  ...  
  </u:Timestamp>  
</o:Security>  
```  
  
#### <a name="613-issuedtokenovertransport"></a><span data-ttu-id="6b811-334">6.1.3 IssuedTokenOverTransport</span><span class="sxs-lookup"><span data-stu-id="6b811-334">6.1.3 IssuedTokenOverTransport</span></span>  
 <span data-ttu-id="6b811-335">Bu kimlik doğrulama modunda, istemci hizmette kimlik doğrulaması yapmaz, ancak bunun yerine güvenlik belirteci hizmeti (STS) tarafından verilen bir belirteç ve paylaşılan bir anahtar hakkında bilgi sahibi olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="6b811-335">With this authentication mode the client does not authenticate to the service, as such, but rather presents a token issued by a Security Token Service (STS) and proves knowledge of a shared key.</span></span> <span data-ttu-id="6b811-336">Verilen belirteç, her zaman başlatıcıdan alıcıya gönderilen bir onaylama destekleme belirteci olarak SOAP katmanında görünür.</span><span class="sxs-lookup"><span data-stu-id="6b811-336">The issued token appears at the SOAP layer as an endorsing supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="6b811-337">Hizmetin kimliği, aktarım katmanında bir X. 509.440 sertifikası kullanılarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="6b811-337">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="6b811-338">Bağlama bir aktarım bağlamadır.</span><span class="sxs-lookup"><span data-stu-id="6b811-338">The binding is a transport binding.</span></span>  
  
 <span data-ttu-id="6b811-339">İlke</span><span class="sxs-lookup"><span data-stu-id="6b811-339">Policy</span></span>  
  
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
  
 <span data-ttu-id="6b811-340">Güvenlik üst bilgisi düzeni</span><span class="sxs-lookup"><span data-stu-id="6b811-340">Security Header Layout</span></span>  
  
 <span data-ttu-id="6b811-341">İstek</span><span class="sxs-lookup"><span data-stu-id="6b811-341">Request</span></span>  
  
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
  
 <span data-ttu-id="6b811-342">Yanıtıyla</span><span class="sxs-lookup"><span data-stu-id="6b811-342">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="614-kerberosovertransport"></a><span data-ttu-id="6b811-343">6.1.4 KerberosOverTransport</span><span class="sxs-lookup"><span data-stu-id="6b811-343">6.1.4 KerberosOverTransport</span></span>  
 <span data-ttu-id="6b811-344">Bu kimlik doğrulama modunda istemci Kerberos bileti kullanarak hizmeti doğrular.</span><span class="sxs-lookup"><span data-stu-id="6b811-344">With this authentication mode the client authenticates to the service using a Kerberos ticket.</span></span> <span data-ttu-id="6b811-345">Kerberos belirteci, SOAP katmanında bir onaylama destekleme belirteci olarak görünür.</span><span class="sxs-lookup"><span data-stu-id="6b811-345">The Kerberos token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="6b811-346">Hizmetin kimliği, aktarım katmanında bir X. 509.440 sertifikası kullanılarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="6b811-346">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="6b811-347">Bağlama bir aktarım bağlamadır.</span><span class="sxs-lookup"><span data-stu-id="6b811-347">The binding is a transport binding.</span></span>  
  
 <span data-ttu-id="6b811-348">İlke</span><span class="sxs-lookup"><span data-stu-id="6b811-348">Policy</span></span>  
  
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
  
 <span data-ttu-id="6b811-349">Güvenlik üst bilgisi düzeni</span><span class="sxs-lookup"><span data-stu-id="6b811-349">Security Header Layout</span></span>  
  
 <span data-ttu-id="6b811-350">İstek</span><span class="sxs-lookup"><span data-stu-id="6b811-350">Request</span></span>  
  
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
  
 <span data-ttu-id="6b811-351">Yanıtıyla</span><span class="sxs-lookup"><span data-stu-id="6b811-351">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="615-sspinegotiatedovertransport"></a><span data-ttu-id="6b811-352">6.1.5 SspiNegotiatedOverTransport</span><span class="sxs-lookup"><span data-stu-id="6b811-352">6.1.5 SspiNegotiatedOverTransport</span></span>  
 <span data-ttu-id="6b811-353">Bu modda istemci ve sunucu kimlik doğrulamasını gerçekleştirmek için bir anlaşma protokolü kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6b811-353">With this mode a negotiation protocol is used to perform client and server authentication.</span></span> <span data-ttu-id="6b811-354">Mümkünse, Kerberos kullanılır, aksi takdirde NTLM kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6b811-354">Kerberos is used if possible, otherwise NTLM.</span></span> <span data-ttu-id="6b811-355">Elde edilen SCT, her zaman başlatıcıdan alıcıya gönderilen bir onaylama destekleme belirteci olarak SOAP katmanında görünür.</span><span class="sxs-lookup"><span data-stu-id="6b811-355">The resulting SCT appears at the SOAP layer as an endorsing supporting token that is always sent from initiator to recipient.</span></span> <span data-ttu-id="6b811-356">Ayrıca hizmet, aktarım katmanında bir X. 509.440 sertifikası tarafından da doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="6b811-356">The service is additionally authenticated at the transport layer by an X.509 certificate.</span></span> <span data-ttu-id="6b811-357">Kullanılan bağlama bir aktarım bağlamadır.</span><span class="sxs-lookup"><span data-stu-id="6b811-357">The binding used is a transport binding.</span></span> <span data-ttu-id="6b811-358">"SPNEGO" (anlaşma), WCF 'nin WS-Trust ile SSPI ikili anlaşma protokolünü nasıl kullandığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="6b811-358">"SPNEGO" (negotiation) describes how WCF uses SSPI binary negotiation protocol with WS-Trust.</span></span> <span data-ttu-id="6b811-359">Bu bölümdeki güvenlik üst bilgisi örnekleri, SPNEGO el sıkışma aracılığıyla SCT oluşturulduktan sonra verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6b811-359">Security header examples in this section are after the SCT has been established through the SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="6b811-360">İlke</span><span class="sxs-lookup"><span data-stu-id="6b811-360">Policy</span></span>  
  
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
  
### <a name="security-header-examples"></a><span data-ttu-id="6b811-361">Güvenlik üst bilgisi örnekleri</span><span class="sxs-lookup"><span data-stu-id="6b811-361">Security Header Examples</span></span>  
 <span data-ttu-id="6b811-362">Güvenlik bağlamı belirteci, WS-Trust Ikili anlaşması kullanılarak SPNEGO Handshake aracılığıyla kurulduktan sonra, uygulama iletilerinde aşağıdaki yapıyla güvenlik üst bilgileri bulunur.</span><span class="sxs-lookup"><span data-stu-id="6b811-362">Once the Security Context Token is established through SPNEGO handshake using WS-Trust Binary Negotiation, the application messages have security headers with the following structure.</span></span>  
  
 <span data-ttu-id="6b811-363">İstek</span><span class="sxs-lookup"><span data-stu-id="6b811-363">Request</span></span>  
  
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
  
 <span data-ttu-id="6b811-364">Yanıtıyla</span><span class="sxs-lookup"><span data-stu-id="6b811-364">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
### <a name="62-using-x509-certificates-for-service-authentication"></a><span data-ttu-id="6b811-365">Hizmet kimlik doğrulaması için X. 509.440 sertifikalarını kullanma 6,2</span><span class="sxs-lookup"><span data-stu-id="6b811-365">6.2 Using X.509 Certificates for Service Authentication</span></span>  
 <span data-ttu-id="6b811-366">Bu bölümde şu kimlik doğrulama modları açıklanmaktadır: Mulualcertificate WSS 1.0, karşılıklı CertificateDuplex, Mulualcertificate WSS 1.1, AnonymousForCertificate, UserNameForCertificate ve IssuedTokenForCertificate.</span><span class="sxs-lookup"><span data-stu-id="6b811-366">This section describes the following authentication modes: MutualCertificate WSS1.0, Mutual CertificateDuplex, MutualCertificate WSS1.1, AnonymousForCertificate, UserNameForCertificate and IssuedTokenForCertificate.</span></span>  
  
#### <a name="621-mutualcertificate-wss10"></a><span data-ttu-id="6b811-367">6.2.1 Mulualcertificate WSS 1.0</span><span class="sxs-lookup"><span data-stu-id="6b811-367">6.2.1 MutualCertificate WSS1.0</span></span>  
 <span data-ttu-id="6b811-368">Bu kimlik doğrulama modunda istemci, başlatıcı belirteci olarak SOAP katmanında görünen bir X. 509.440 sertifikası kullanarak kimlik doğrular.</span><span class="sxs-lookup"><span data-stu-id="6b811-368">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as the initiator token.</span></span> <span data-ttu-id="6b811-369">Ayrıca, hizmet bir X. 509.440 sertifikası kullanılarak doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="6b811-369">The service is also authenticated using an X.509 certificate.</span></span>  
  
 <span data-ttu-id="6b811-370">Kullanılan bağlama, aşağıdaki özellik değerleriyle asimetrik bir bağlamadır:</span><span class="sxs-lookup"><span data-stu-id="6b811-370">The binding used is an asymmetric binding with the following property values:</span></span>  
  
 <span data-ttu-id="6b811-371">Başlatıcı belirteci: ekleme modu. ../IncludeToken/AlwaysToRecipient olarak ayarlanan istemcinin X. 509.440 sertifikası</span><span class="sxs-lookup"><span data-stu-id="6b811-371">Initiator Token: the client’s X.509 certificate, with inclusion mode set to …/IncludeToken/AlwaysToRecipient</span></span>  
  
 <span data-ttu-id="6b811-372">Alıcı belirteci: sunucu X. 509.440 sertifikası, dahil etme modu ayarlandı. ../Includetoken/No</span><span class="sxs-lookup"><span data-stu-id="6b811-372">Recipient Token: Server’s X.509 Certificate, with inclusion mode is set …/IncludeToken/Never</span></span>  
  
 <span data-ttu-id="6b811-373">Belirteç koruması: false</span><span class="sxs-lookup"><span data-stu-id="6b811-373">Token Protection: False</span></span>  
  
 <span data-ttu-id="6b811-374">Tüm başlık ve gövde Imzaları: doğru</span><span class="sxs-lookup"><span data-stu-id="6b811-374">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="6b811-375">Koruma sırası: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="6b811-375">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="6b811-376">Imzayı şifreleyin: doğru</span><span class="sxs-lookup"><span data-stu-id="6b811-376">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="6b811-377">İlke</span><span class="sxs-lookup"><span data-stu-id="6b811-377">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="6b811-378">Güvenlik üst bilgisi örnekleri: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="6b811-378">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="6b811-379">İstek</span><span class="sxs-lookup"><span data-stu-id="6b811-379">Request</span></span>  
  
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
  
 <span data-ttu-id="6b811-380">Yanıtıyla</span><span class="sxs-lookup"><span data-stu-id="6b811-380">Response</span></span>  
  
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
  
 <span data-ttu-id="6b811-381">Güvenlik üst bilgisi örnekleri: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="6b811-381">Security Header Examples: EncryptBeforeSign</span></span>  
  
 <span data-ttu-id="6b811-382">İstek</span><span class="sxs-lookup"><span data-stu-id="6b811-382">Request</span></span>  
  
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
  
 <span data-ttu-id="6b811-383">Yanıtıyla</span><span class="sxs-lookup"><span data-stu-id="6b811-383">Response</span></span>  
  
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
  
#### <a name="622-mutualcertificateduplex"></a><span data-ttu-id="6b811-384">6.2.2 Mulualcertificateduplex</span><span class="sxs-lookup"><span data-stu-id="6b811-384">6.2.2 MutualCertificateDuplex</span></span>  
 <span data-ttu-id="6b811-385">Bu kimlik doğrulama modunda istemci, başlatıcı belirteci olarak SOAP katmanında görünen bir X. 509.440 sertifikası kullanarak kimlik doğrular.</span><span class="sxs-lookup"><span data-stu-id="6b811-385">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as the initiator token.</span></span> <span data-ttu-id="6b811-386">Ayrıca, hizmet bir X. 509.440 sertifikası kullanılarak doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="6b811-386">The service is also authenticated using an X.509 certificate.</span></span>  
  
 <span data-ttu-id="6b811-387">Kullanılan bağlama, aşağıdaki özellik değerleriyle asimetrik bir bağlamadır:</span><span class="sxs-lookup"><span data-stu-id="6b811-387">The binding used is an asymmetric binding with the following property values:</span></span>  
  
 <span data-ttu-id="6b811-388">Başlatıcı belirteci: Istemcinin x509 sertifikası, ekleme modu. ../IncludeToken/AlwaysToRecipient olarak ayarlandı</span><span class="sxs-lookup"><span data-stu-id="6b811-388">Initiator Token: Client’s X509 Certificate, inclusion mode is set to …/IncludeToken/AlwaysToRecipient</span></span>  
  
 <span data-ttu-id="6b811-389">Alıcı belirteci: sunucunun x509 sertifikası, dahil etme modu. ../ıncludetoken/AlwaysToInitiator olarak ayarlandı</span><span class="sxs-lookup"><span data-stu-id="6b811-389">Recipient Token: Server’s X509 Certificate, inclusion mode is set to …/IncludeToken/AlwaysToInitiator</span></span>  
  
 <span data-ttu-id="6b811-390">Belirteç koruması: false</span><span class="sxs-lookup"><span data-stu-id="6b811-390">Token Protection: False</span></span>  
  
 <span data-ttu-id="6b811-391">Tüm başlık ve gövde Imzaları: doğru</span><span class="sxs-lookup"><span data-stu-id="6b811-391">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="6b811-392">Koruma sırası: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="6b811-392">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="6b811-393">Imzayı şifreleyin: doğru</span><span class="sxs-lookup"><span data-stu-id="6b811-393">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="6b811-394">İlke</span><span class="sxs-lookup"><span data-stu-id="6b811-394">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="6b811-395">Güvenlik üst bilgisi örnekleri: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="6b811-395">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="6b811-396">İstek ve yanıt</span><span class="sxs-lookup"><span data-stu-id="6b811-396">Request and Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="6b811-397">Güvenlik üst bilgisi örnekleri: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="6b811-397">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="6b811-398">İstek ve yanıt</span><span class="sxs-lookup"><span data-stu-id="6b811-398">Request and Response</span></span>  
  
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
  
#### <a name="623-using-symmetricbinding-with-x509-service-authentication"></a><span data-ttu-id="6b811-399">X. 509.440 hizmeti kimlik doğrulamasıyla SymmetricBinding kullanarak 6.2.3</span><span class="sxs-lookup"><span data-stu-id="6b811-399">6.2.3 Using SymmetricBinding with X.509 Service Authentication</span></span>  
 <span data-ttu-id="6b811-400">"WSS10", x509 belirteçleri olan senaryolar için sınırlı destek sağlamıştır.</span><span class="sxs-lookup"><span data-stu-id="6b811-400">"WSS10" provided limited support for scenarios with X509 tokens.</span></span> <span data-ttu-id="6b811-401">Örneğin, yalnızca Service x509 belirtecini kullanan iletiler için imza ve şifreleme koruması sağlanması mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="6b811-401">For example, there was no way to provide signature and encryption protection for messages using only service X509 token.</span></span> <span data-ttu-id="6b811-402">"WSS11", EncryptedKey öğesinin kullanımını simetrik bir belirteç olarak getirdi.</span><span class="sxs-lookup"><span data-stu-id="6b811-402">"WSS11" introduced the usage of EncryptedKey as a symmetric token.</span></span> <span data-ttu-id="6b811-403">Artık hem istek hem de yanıt iletileri koruması için hizmetin X. 509.440 sertifikası için şifrelenmiş bir geçici anahtar kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6b811-403">Now a temporary key encrypted for the service's X.509 certificate could be used for both request and response messages protection.</span></span> <span data-ttu-id="6b811-404">Aşağıdaki 6,4 bölümünde açıklanan kimlik doğrulama modları bu kalıbı kullanır.</span><span class="sxs-lookup"><span data-stu-id="6b811-404">The authentication modes described in the section 6.4 below use this pattern.</span></span>  
  
 <span data-ttu-id="6b811-405">WS-SecurityPolicy, koruma belirteci olarak Service x509 belirteci ile SymmetricBinding kullanarak bu kalıbı açıklar.</span><span class="sxs-lookup"><span data-stu-id="6b811-405">WS-SecurityPolicy describes this pattern using SymmetricBinding with Service X509 token as the protection token.</span></span>  
  
 <span data-ttu-id="6b811-406">Kimlik doğrulama modları AnonymousForCertificate, UsernameForCertificate, Mulualcertificate WSS11 ve IssuedTokenForCertificate All, aşağıdaki özellik değerleriyle benzer bir SP: SymmetricBinding örneği kullanır:</span><span class="sxs-lookup"><span data-stu-id="6b811-406">Authentication modes AnonymousForCertificate, UsernameForCertificate, MutualCertificate WSS11 and IssuedTokenForCertificate all use a similar instance of sp:SymmetricBinding with the following property values:</span></span>  
  
 <span data-ttu-id="6b811-407">Koruma belirteci: sunucunun x509 sertifikası, içerme modu olarak ayarlandı. ../Includetoken/hiçbir</span><span class="sxs-lookup"><span data-stu-id="6b811-407">Protection Token: Server’s X509 Certificate, inclusion mode is set to .../IncludeToken/Never</span></span>  
<span data-ttu-id="6b811-408">Belirteç koruması: false</span><span class="sxs-lookup"><span data-stu-id="6b811-408">Token Protection: False</span></span>  
  
 <span data-ttu-id="6b811-409">Tüm başlık ve gövde Imzaları: doğru</span><span class="sxs-lookup"><span data-stu-id="6b811-409">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="6b811-410">Koruma sırası: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="6b811-410">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="6b811-411">Imzayı şifreleyin: doğru</span><span class="sxs-lookup"><span data-stu-id="6b811-411">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="6b811-412">Yukarıdaki kimlik doğrulama modları yalnızca kullandıkları destekleyici belirteçlere göre farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="6b811-412">The above authentication modes only differ by the supporting tokens they use.</span></span> <span data-ttu-id="6b811-413">AnonymousForCertificate içinde herhangi bir destekleme belirteci yok 1,1, çok sayıda çoklu Kullanıcı tarafından desteklenen bir destekleme belirteçleri, UserNameForCertificate, imzalı destekleyici belirteç olarak bir Kullanıcı adı belirteci içeriyor ve IssuedTokenForCertificate verilen belirteci, bir onaylama destekleme belirteci olarak içeriyor.</span><span class="sxs-lookup"><span data-stu-id="6b811-413">AnonymousForCertificate does not have any supporting tokens, MutualCertificate WSS 1.1 has the client’s X509 certificate as an endorsing supporting tokens, UserNameForCertificate has a UserName Token as a signed supporting token and IssuedTokenForCertificate has the issued token as an endorsing supporting token.</span></span>  
  
 <span data-ttu-id="6b811-414">İlke</span><span class="sxs-lookup"><span data-stu-id="6b811-414">Policy</span></span>  
  
 <span data-ttu-id="6b811-415">Simetrik bağlama</span><span class="sxs-lookup"><span data-stu-id="6b811-415">Symmetric Binding</span></span>  
  
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
  
#### <a name="624-anonymousforcertificate"></a><span data-ttu-id="6b811-416">6.2.4 AnonymousForCertificate</span><span class="sxs-lookup"><span data-stu-id="6b811-416">6.2.4 AnonymousForCertificate</span></span>  
 <span data-ttu-id="6b811-417">Bu kimlik doğrulama modunda, istemci anonimdir ve hizmetin kimliği bir X. 509.440 sertifikası kullanılarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="6b811-417">With this authentication mode the client is anonymous and the service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="6b811-418">Kullanılan bağlama, 6.4.2 içinde açıklandığı gibi simetrik bağlamanın bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="6b811-418">The binding used is an instance of symmetric binding as described in 6.4.2.</span></span>  
  
 <span data-ttu-id="6b811-419">İlke</span><span class="sxs-lookup"><span data-stu-id="6b811-419">Policy</span></span>  
  
 <span data-ttu-id="6b811-420">Bağlama ayrıntıları için yukarıdaki 6.2.3 içindeki "Ilke" başlığına bakın</span><span class="sxs-lookup"><span data-stu-id="6b811-420">See "Policy" in 6.2.3 above for binding details</span></span>  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="6b811-421">Güvenlik üst bilgisi örnekleri: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="6b811-421">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="6b811-422">İstek</span><span class="sxs-lookup"><span data-stu-id="6b811-422">Request</span></span>  
  
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
  
 <span data-ttu-id="6b811-423">Yanıtıyla</span><span class="sxs-lookup"><span data-stu-id="6b811-423">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="6b811-424">Güvenlik üst bilgisi örnekleri: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="6b811-424">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="6b811-425">İstek</span><span class="sxs-lookup"><span data-stu-id="6b811-425">Request</span></span>  
  
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
  
 <span data-ttu-id="6b811-426">Yanıtıyla</span><span class="sxs-lookup"><span data-stu-id="6b811-426">Response</span></span>  
  
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
  
#### <a name="625-usernameforcertificate"></a><span data-ttu-id="6b811-427">6.2.5 UserNameForCertificate</span><span class="sxs-lookup"><span data-stu-id="6b811-427">6.2.5 UserNameForCertificate</span></span>  
 <span data-ttu-id="6b811-428">Bu kimlik doğrulama modunda istemci, SOAP katmanında imzalı destekleyici belirteç olarak görünen bir Kullanıcı adı belirteci kullanarak hizmette kimlik doğrulaması yapar.</span><span class="sxs-lookup"><span data-stu-id="6b811-428">With this authentication mode the client authenticates to the service using a Username Token which appears at the SOAP layer as a signed supporting token.</span></span> <span data-ttu-id="6b811-429">Hizmet, bir X. 509.440 sertifikası kullanarak istemcinin kimliğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="6b811-429">The service authenticates to the client using an X.509 certificate.</span></span> <span data-ttu-id="6b811-430">Kullanılan bağlama, koruma belirtecinin istemci tarafından oluşturulan ve hizmetin ortak anahtarıyla şifrelenen bir anahtar olduğu simetrik bir bağlamadır.</span><span class="sxs-lookup"><span data-stu-id="6b811-430">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="6b811-431">İlke</span><span class="sxs-lookup"><span data-stu-id="6b811-431">Policy</span></span>  
  
 <span data-ttu-id="6b811-432">Bağlama ayrıntıları için yukarıdaki 6.2.3 içindeki "Ilke" başlığına bakın</span><span class="sxs-lookup"><span data-stu-id="6b811-432">See "Policy" in 6.2.3 above for binding details</span></span>  
  
 <span data-ttu-id="6b811-433">İmzalı destekleme belirteci</span><span class="sxs-lookup"><span data-stu-id="6b811-433">Signed Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="6b811-434">Güvenlik üst bilgisi örnekleri: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="6b811-434">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="6b811-435">İstek</span><span class="sxs-lookup"><span data-stu-id="6b811-435">Request</span></span>  
  
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
  
 <span data-ttu-id="6b811-436">Yanıtıyla</span><span class="sxs-lookup"><span data-stu-id="6b811-436">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="6b811-437">Güvenlik üst bilgisi örnekleri: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="6b811-437">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="6b811-438">İstek</span><span class="sxs-lookup"><span data-stu-id="6b811-438">Request</span></span>  
  
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
  
 <span data-ttu-id="6b811-439">Yanıtıyla</span><span class="sxs-lookup"><span data-stu-id="6b811-439">Response</span></span>  
  
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
  
#### <a name="626-mutualcertificate-wss-11"></a><span data-ttu-id="6b811-440">6.2.6 Mulualcertificate (WSS 1,1)</span><span class="sxs-lookup"><span data-stu-id="6b811-440">6.2.6 MutualCertificate (WSS 1.1)</span></span>  
 <span data-ttu-id="6b811-441">Bu kimlik doğrulama modunda istemci, SOAP katmanında bir destekleme desteği belirteci olarak görünen bir X. 509.440 sertifikası kullanarak kimlik doğrular.</span><span class="sxs-lookup"><span data-stu-id="6b811-441">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="6b811-442">Ayrıca, hizmet bir X. 509.440 sertifikası kullanılarak doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="6b811-442">The service is also authenticated using an X.509 certificate.</span></span> <span data-ttu-id="6b811-443">Kullanılan bağlama, koruma belirtecinin istemci tarafından oluşturulan ve hizmetin ortak anahtarıyla şifrelenen bir anahtar olduğu simetrik bir bağlamadır.</span><span class="sxs-lookup"><span data-stu-id="6b811-443">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="6b811-444">İlke</span><span class="sxs-lookup"><span data-stu-id="6b811-444">Policy</span></span>  
  
 <span data-ttu-id="6b811-445">Bağlama ayrıntıları için bkz. 6.2.3 içinde Ilke</span><span class="sxs-lookup"><span data-stu-id="6b811-445">See Policy in 6.2.3 for binding details</span></span>  
  
 <span data-ttu-id="6b811-446">Destekleyici belirteç onaylama</span><span class="sxs-lookup"><span data-stu-id="6b811-446">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="6b811-447">Güvenlik üst bilgisi örnekleri: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="6b811-447">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="6b811-448">İstek</span><span class="sxs-lookup"><span data-stu-id="6b811-448">Request</span></span>  
  
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
  
 <span data-ttu-id="6b811-449">Yanıtıyla</span><span class="sxs-lookup"><span data-stu-id="6b811-449">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="6b811-450">Güvenlik üst bilgisi örnekleri: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="6b811-450">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="6b811-451">İstek</span><span class="sxs-lookup"><span data-stu-id="6b811-451">Request</span></span>  
  
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
  
 <span data-ttu-id="6b811-452">Yanıtıyla</span><span class="sxs-lookup"><span data-stu-id="6b811-452">Response</span></span>  
  
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
  
#### <a name="627-issuedtokenforcertificate"></a><span data-ttu-id="6b811-453">6.2.7 IssuedTokenForCertificate</span><span class="sxs-lookup"><span data-stu-id="6b811-453">6.2.7 IssuedTokenForCertificate</span></span>  
 <span data-ttu-id="6b811-454">Bu kimlik doğrulama modunda istemci, bu şekilde hizmette kimlik doğrulaması yapmaz, ancak bunun yerine STS tarafından verilen bir belirteç ve paylaşılan anahtar hakkında bilgi sahibi olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="6b811-454">With this authentication mode the client does not authenticate to the service, as such, but instead presents a token issued by a STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="6b811-455">Verilen belirteç, SOAP katmanında bir onaylama destekleme belirteci olarak görünür.</span><span class="sxs-lookup"><span data-stu-id="6b811-455">The issued token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="6b811-456">Hizmet, bir X. 509.440 sertifikası kullanarak istemcinin kimliğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="6b811-456">The service authenticates to the client using an X.509 certificate.</span></span> <span data-ttu-id="6b811-457">Kullanılan bağlama, koruma belirtecinin istemci tarafından oluşturulan ve hizmetin ortak anahtarıyla şifrelenen bir anahtar olduğu simetrik bir bağlamadır.</span><span class="sxs-lookup"><span data-stu-id="6b811-457">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="6b811-458">İlke</span><span class="sxs-lookup"><span data-stu-id="6b811-458">Policy</span></span>  
  
 <span data-ttu-id="6b811-459">Bağlama ayrıntıları için yukarıdaki 6.2.3 içindeki Ilkeye bakın</span><span class="sxs-lookup"><span data-stu-id="6b811-459">See Policy in 6.2.3 above for binding details</span></span>  
  
 <span data-ttu-id="6b811-460">Destekleyici belirteç onaylama</span><span class="sxs-lookup"><span data-stu-id="6b811-460">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="6b811-461">Güvenlik üst bilgisi örnekleri: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="6b811-461">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="6b811-462">İstek</span><span class="sxs-lookup"><span data-stu-id="6b811-462">Request</span></span>  
  
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
  
 <span data-ttu-id="6b811-463">Yanıtıyla</span><span class="sxs-lookup"><span data-stu-id="6b811-463">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="6b811-464">Güvenlik üst bilgisi örnekleri: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="6b811-464">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="6b811-465">İstek</span><span class="sxs-lookup"><span data-stu-id="6b811-465">Request</span></span>  
  
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
  
 <span data-ttu-id="6b811-466">Yanıtıyla</span><span class="sxs-lookup"><span data-stu-id="6b811-466">Response</span></span>  
  
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
  
## <a name="63-kerberos"></a><span data-ttu-id="6b811-467">6,3 Kerberos</span><span class="sxs-lookup"><span data-stu-id="6b811-467">6.3 Kerberos</span></span>  
 <span data-ttu-id="6b811-468">Bu kimlik doğrulama modunda istemci Kerberos bileti kullanarak hizmeti doğrular.</span><span class="sxs-lookup"><span data-stu-id="6b811-468">With this authentication mode the client authenticates to the service using a Kerberos ticket.</span></span> <span data-ttu-id="6b811-469">Aynı bilet aynı zamanda sunucu kimlik doğrulaması da sağlar.</span><span class="sxs-lookup"><span data-stu-id="6b811-469">That same ticket also provides server authentication.</span></span> <span data-ttu-id="6b811-470">Kullanılan bağlama, aşağıdaki özelliklerle simetrik bir bağlamadır;</span><span class="sxs-lookup"><span data-stu-id="6b811-470">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="6b811-471">Koruma belirteci: Kerberos bileti, ekleme modu. ../IncludeToken/Once olarak ayarlandı</span><span class="sxs-lookup"><span data-stu-id="6b811-471">Protection Token: Kerberos Ticket, inclusion mode is set to .../IncludeToken/Once</span></span>  
<span data-ttu-id="6b811-472">Belirteç koruması: false</span><span class="sxs-lookup"><span data-stu-id="6b811-472">Token Protection: False</span></span>  
  
 <span data-ttu-id="6b811-473">Tüm başlık ve gövde Imzaları: doğru</span><span class="sxs-lookup"><span data-stu-id="6b811-473">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="6b811-474">Koruma sırası: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="6b811-474">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="6b811-475">Imzayı şifreleyin: doğru</span><span class="sxs-lookup"><span data-stu-id="6b811-475">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="6b811-476">İlke</span><span class="sxs-lookup"><span data-stu-id="6b811-476">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="6b811-477">Güvenlik üst bilgisi örnekleri: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="6b811-477">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="6b811-478">İstek</span><span class="sxs-lookup"><span data-stu-id="6b811-478">Request</span></span>  
  
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
  
 <span data-ttu-id="6b811-479">Yanıtıyla</span><span class="sxs-lookup"><span data-stu-id="6b811-479">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="6b811-480">Güvenlik üst bilgisi örnekleri: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="6b811-480">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="6b811-481">İstek</span><span class="sxs-lookup"><span data-stu-id="6b811-481">Request</span></span>  
  
```xml  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
 <span data-ttu-id="6b811-482">Yanıtıyla</span><span class="sxs-lookup"><span data-stu-id="6b811-482">Response</span></span>  
  
```xml  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
#### <a name="64-issuedtoken"></a><span data-ttu-id="6b811-483">6,4 IssuedToken</span><span class="sxs-lookup"><span data-stu-id="6b811-483">6.4 IssuedToken</span></span>  
 <span data-ttu-id="6b811-484">Bu kimlik doğrulama modunda, istemci hizmette kimlik doğrulaması yapmaz, bunun yerine istemci, STS tarafından verilen bir belirteç ve paylaşılan bir anahtar hakkında bilgi sahibi olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="6b811-484">With this authentication mode the client does not authenticate to the service, as such, rather the client presents a token issued by an STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="6b811-485">Bu hizmet, istemci tarafından kimlik doğrulaması değil, bu nedenle, STS, paylaşılan anahtarı yalnızca hizmetin şifresini çözebilmesini sağlayan, verilen belirtecin bir parçası olarak şifreler.</span><span class="sxs-lookup"><span data-stu-id="6b811-485">The service is not authenticated to the client, as such, instead the STS encrypts the shared key as part of the issued token such that only the service can decrypt the key.</span></span> <span data-ttu-id="6b811-486">Kullanılan bağlama, aşağıdaki özelliklerle simetrik bağlama olarak verilmiştir;</span><span class="sxs-lookup"><span data-stu-id="6b811-486">The binding used is as symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="6b811-487">Koruma belirteci: verilen belirteç, ekleme modu. ../IncludeToken/AlwaysToRecipient olarak ayarlandı</span><span class="sxs-lookup"><span data-stu-id="6b811-487">Protection Token: Issued Token, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
<span data-ttu-id="6b811-488">Belirteç koruması: false</span><span class="sxs-lookup"><span data-stu-id="6b811-488">Token Protection: False</span></span>  
  
 <span data-ttu-id="6b811-489">Tüm başlık ve gövde Imzaları: doğru</span><span class="sxs-lookup"><span data-stu-id="6b811-489">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="6b811-490">Koruma sırası: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="6b811-490">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="6b811-491">Imzayı şifreleyin: doğru</span><span class="sxs-lookup"><span data-stu-id="6b811-491">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="6b811-492">İlke</span><span class="sxs-lookup"><span data-stu-id="6b811-492">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="6b811-493">Güvenlik üst bilgisi örnekleri: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="6b811-493">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="6b811-494">İstek</span><span class="sxs-lookup"><span data-stu-id="6b811-494">Request</span></span>  
  
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
  
 <span data-ttu-id="6b811-495">Yanıtıyla</span><span class="sxs-lookup"><span data-stu-id="6b811-495">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="6b811-496">Güvenlik üst bilgisi örnekleri: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="6b811-496">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="6b811-497">İstek</span><span class="sxs-lookup"><span data-stu-id="6b811-497">Request</span></span>  
  
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
  
 <span data-ttu-id="6b811-498">Yanıtıyla</span><span class="sxs-lookup"><span data-stu-id="6b811-498">Response</span></span>  
  
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
  
### <a name="65-using-sslnegotiated-for-service-authentication"></a><span data-ttu-id="6b811-499">Hizmet kimlik doğrulaması için Sslanlaşmalı kullanma 6,5</span><span class="sxs-lookup"><span data-stu-id="6b811-499">6.5 Using SslNegotiated for Service Authentication</span></span>  
 <span data-ttu-id="6b811-500">Bu bölümde, WS-Trust (WS-T) RST/üzerinde TLS protokolünü yürüterek, anahtar değerine anlaşılan, her WS-SecureConversation (WS-SC) başına bir güvenlik bağlamı belirteci olan bir kimlik doğrulama modu grubu açıklanmaktadır. RSTR iletileri.</span><span class="sxs-lookup"><span data-stu-id="6b811-500">This section describes a group of authentication modes that use a symmetric binding with the protection token being a Security Context Token per WS-SecureConversation (WS-SC) whose key value is negotiated by executing the TLS protocol over WS-Trust (WS-T) RST/RSTR messages.</span></span> <span data-ttu-id="6b811-501">WS-Trust kullanılarak TLS el sıkışma uygulamasının ayrıntıları TLSNEGO içinde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6b811-501">Details of the TLS handshake implementation using WS-Trust are described in TLSNEGO.</span></span> <span data-ttu-id="6b811-502">Burada ileti örneklerinde, ilişkili bir güvenlik bağlamı olan SCT 'nin bir el sıkışma aracılığıyla zaten kurulduğu varsayılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6b811-502">Here in the message examples we will assume that SCT with an associated security context is already established through a handshake.</span></span>  
  
 <span data-ttu-id="6b811-503">Kullanılan bağlama, aşağıdaki özelliklerle simetrik bir bağlamadır;</span><span class="sxs-lookup"><span data-stu-id="6b811-503">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="6b811-504">Koruma belirteci: SslContextToken, ekleme modu olarak ayarlandı. ../Includetoken/hiçbir</span><span class="sxs-lookup"><span data-stu-id="6b811-504">Protection Token: SslContextToken, inclusion mode is set to .../IncludeToken/Never</span></span>  
<span data-ttu-id="6b811-505">Belirteç koruması: false</span><span class="sxs-lookup"><span data-stu-id="6b811-505">Token Protection: False</span></span>  
  
 <span data-ttu-id="6b811-506">Tüm başlık ve gövde Imzaları: doğru</span><span class="sxs-lookup"><span data-stu-id="6b811-506">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="6b811-507">Koruma sırası: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="6b811-507">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="6b811-508">Imzayı şifreleyin: doğru</span><span class="sxs-lookup"><span data-stu-id="6b811-508">Encrypt Signature: True</span></span>  
  
#### <a name="651-policy-for-sslnegotiated-service-authentication"></a><span data-ttu-id="6b811-509">Sslanlaşmalı hizmet kimlik doğrulaması için 6.5.1 ilkesi</span><span class="sxs-lookup"><span data-stu-id="6b811-509">6.5.1 Policy for SslNegotiated service authentication</span></span>  
 <span data-ttu-id="6b811-510">Bu bölümdeki tüm kimlik doğrulama modları için ilke benzerdir ve yalnızca belirli imzalı destekleyici veya onaylama belirteçlerine göre farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="6b811-510">Policy for all authentication modes in this section are similar and differ only by specific signed supporting or endorsing tokens used.</span></span>  
  
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
  
#### <a name="652-anonymousforsslnegotiated"></a><span data-ttu-id="6b811-511">6.5.2 Anonymousforsslanlaşmalı</span><span class="sxs-lookup"><span data-stu-id="6b811-511">6.5.2 AnonymousForSslNegotiated</span></span>  
 <span data-ttu-id="6b811-512">Bu kimlik doğrulama modunda, istemci anonimdir ve hizmetin kimliği bir X. 509.440 sertifikası kullanılarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="6b811-512">With this authentication mode the client is anonymous and the service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="6b811-513">Kullanılan bağlama, yukarıdaki 6.5.1 açıklanan simetrik bağlamanın bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="6b811-513">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="6b811-514">İlke</span><span class="sxs-lookup"><span data-stu-id="6b811-514">Policy</span></span>  
  
 <span data-ttu-id="6b811-515">Bağlama ayrıntıları için yukarıdaki 6.5.1 içindeki Ilkeye bakın.</span><span class="sxs-lookup"><span data-stu-id="6b811-515">See Policy in 6.5.1 above for binding details.</span></span>  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="6b811-516">Güvenlik üst bilgisi örnekleri: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="6b811-516">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="6b811-517">İstek</span><span class="sxs-lookup"><span data-stu-id="6b811-517">Request</span></span>  
  
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
  
 <span data-ttu-id="6b811-518">Yanıtıyla</span><span class="sxs-lookup"><span data-stu-id="6b811-518">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="6b811-519">Güvenlik üst bilgisi örnekleri: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="6b811-519">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="6b811-520">İstek</span><span class="sxs-lookup"><span data-stu-id="6b811-520">Request</span></span>  
  
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
  
 <span data-ttu-id="6b811-521">Yanıtıyla</span><span class="sxs-lookup"><span data-stu-id="6b811-521">Response</span></span>  
  
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
  
#### <a name="653-usernameforsslnegotiated"></a><span data-ttu-id="6b811-522">6.5.3 Usernameforsslanlaşmalı</span><span class="sxs-lookup"><span data-stu-id="6b811-522">6.5.3 UserNameForSslNegotiated</span></span>  
 <span data-ttu-id="6b811-523">Bu kimlik doğrulama modunda istemci, SOAP katmanında imzalı destekleyici belirteç olarak görünen bir Kullanıcı adı belirteci kullanarak kimlik doğrular.</span><span class="sxs-lookup"><span data-stu-id="6b811-523">With this authentication mode the client is authenticates using a Username Token which appears at the SOAP layer as a signed supporting token.</span></span> <span data-ttu-id="6b811-524">Hizmetin kimliği bir X. 509.440 sertifikası kullanılarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="6b811-524">The service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="6b811-525">Kullanılan bağlama, 6.5.1 içinde açıklandığı gibi simetrik bağlamanın bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="6b811-525">The binding used is an instance of symmetric binding as described in 6.5.1.</span></span>  
  
 <span data-ttu-id="6b811-526">İlke</span><span class="sxs-lookup"><span data-stu-id="6b811-526">Policy</span></span>  
  
 <span data-ttu-id="6b811-527">Bağlama ayrıntıları için yukarıdaki 6.5.1 bölümüne bakın</span><span class="sxs-lookup"><span data-stu-id="6b811-527">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="6b811-528">İmzalı destekleme belirteci</span><span class="sxs-lookup"><span data-stu-id="6b811-528">Signed Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="6b811-529">Güvenlik üst bilgisi örnekleri: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="6b811-529">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="6b811-530">İstek</span><span class="sxs-lookup"><span data-stu-id="6b811-530">Request</span></span>  
  
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
  
 <span data-ttu-id="6b811-531">Yanıtıyla</span><span class="sxs-lookup"><span data-stu-id="6b811-531">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="6b811-532">Güvenlik üst bilgisi örnekleri: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="6b811-532">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="6b811-533">İstek</span><span class="sxs-lookup"><span data-stu-id="6b811-533">Request</span></span>  
  
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
  
 <span data-ttu-id="6b811-534">Yanıtıyla</span><span class="sxs-lookup"><span data-stu-id="6b811-534">Response</span></span>  
  
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
  
#### <a name="654-issuedtokenforsslnegotiated"></a><span data-ttu-id="6b811-535">6.5.4 ıssuedtokenforsslanlaşmalı</span><span class="sxs-lookup"><span data-stu-id="6b811-535">6.5.4 IssuedTokenForSslNegotiated</span></span>  
 <span data-ttu-id="6b811-536">Bu kimlik doğrulama modunda istemci, bu şekilde hizmette kimlik doğrulaması yapmaz, ancak bunun yerine STS tarafından verilen bir belirteç ve paylaşılan anahtar hakkında bilgi sahibi olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="6b811-536">With this authentication mode the client does not authenticate to the service, as such, but instead presents a token issued by an STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="6b811-537">Verilen belirteç, SOAP katmanında bir onaylama destekleme belirteci olarak görünür.</span><span class="sxs-lookup"><span data-stu-id="6b811-537">The issued token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="6b811-538">Hizmetin kimliği bir X. 509.440 sertifikası kullanılarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="6b811-538">The service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="6b811-539">Kullanılan bağlama, yukarıdaki 6.5.1 açıklanan simetrik bağlamanın bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="6b811-539">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="6b811-540">İlke</span><span class="sxs-lookup"><span data-stu-id="6b811-540">Policy</span></span>  
  
 <span data-ttu-id="6b811-541">Bağlama ayrıntıları için yukarıdaki 6.5.1 bölümüne bakın</span><span class="sxs-lookup"><span data-stu-id="6b811-541">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="6b811-542">Destekleyici belirteç onaylama</span><span class="sxs-lookup"><span data-stu-id="6b811-542">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="6b811-543">Güvenlik üst bilgisi örnekleri: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="6b811-543">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="6b811-544">İstek</span><span class="sxs-lookup"><span data-stu-id="6b811-544">Request</span></span>  
  
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
  
 <span data-ttu-id="6b811-545">Yanıtıyla</span><span class="sxs-lookup"><span data-stu-id="6b811-545">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="6b811-546">Güvenlik üst bilgisi örnekleri: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="6b811-546">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="6b811-547">İstek</span><span class="sxs-lookup"><span data-stu-id="6b811-547">Request</span></span>  
  
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
  
 <span data-ttu-id="6b811-548">Yanıtıyla</span><span class="sxs-lookup"><span data-stu-id="6b811-548">Response</span></span>  
  
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
  
#### <a name="655-mutualsslnegotiated"></a><span data-ttu-id="6b811-549">6.5.5 Mulualsslanlaşmalı</span><span class="sxs-lookup"><span data-stu-id="6b811-549">6.5.5 MutualSslNegotiated</span></span>  
 <span data-ttu-id="6b811-550">Bu kimlik doğrulama moduyla, istemci ve hizmet X. 509.440 sertifikalarını kullanarak kimlik doğrular.</span><span class="sxs-lookup"><span data-stu-id="6b811-550">With this authentication mode the client and the service authenticate using X.509 certificates.</span></span> <span data-ttu-id="6b811-551">Kullanılan bağlama, yukarıdaki 6.5.1 açıklanan simetrik bağlamanın bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="6b811-551">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="6b811-552">İlke</span><span class="sxs-lookup"><span data-stu-id="6b811-552">Policy</span></span>  
  
 <span data-ttu-id="6b811-553">Bağlama ayrıntıları için yukarıdaki 6.5.1 bölümüne bakın</span><span class="sxs-lookup"><span data-stu-id="6b811-553">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="6b811-554">Destekleyici belirteç onaylama</span><span class="sxs-lookup"><span data-stu-id="6b811-554">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="6b811-555">Güvenlik üst bilgisi örnekleri: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="6b811-555">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="6b811-556">İstek</span><span class="sxs-lookup"><span data-stu-id="6b811-556">Request</span></span>  
  
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
  
 <span data-ttu-id="6b811-557">Yanıtıyla</span><span class="sxs-lookup"><span data-stu-id="6b811-557">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="6b811-558">Güvenlik üst bilgisi örnekleri: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="6b811-558">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="6b811-559">İstek</span><span class="sxs-lookup"><span data-stu-id="6b811-559">Request</span></span>  
  
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
  
 <span data-ttu-id="6b811-560">Yanıtıyla</span><span class="sxs-lookup"><span data-stu-id="6b811-560">Response</span></span>  
  
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
  
### <a name="66-sspinegotiated"></a><span data-ttu-id="6b811-561">6,6 SspiNegotiated</span><span class="sxs-lookup"><span data-stu-id="6b811-561">6.6 SspiNegotiated</span></span>  
 <span data-ttu-id="6b811-562">Bu kimlik doğrulama modunda, istemci ve sunucu kimlik doğrulamasını gerçekleştirmek için bir anlaşma protokolü kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6b811-562">With this authentication mode a negotiation protocol is used to perform client and server authentication.</span></span> <span data-ttu-id="6b811-563">Mümkünse, Kerberos kullanılır, aksi takdirde NTLM kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6b811-563">Kerberos is used if possible, otherwise NTLM.</span></span> <span data-ttu-id="6b811-564">Kullanılan bağlama, aşağıdaki özelliklerle simetrik bir bağlamadır;</span><span class="sxs-lookup"><span data-stu-id="6b811-564">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="6b811-565">Koruma belirteci: SpnegoContextToken, ekleme modu. ../ıncludetoken/AlwaysToRecipient olarak ayarlandı</span><span class="sxs-lookup"><span data-stu-id="6b811-565">Protection Token: SpnegoContextToken, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
<span data-ttu-id="6b811-566">Belirteç koruması: false</span><span class="sxs-lookup"><span data-stu-id="6b811-566">Token Protection: False</span></span>  
  
 <span data-ttu-id="6b811-567">Tüm başlık ve gövde Imzaları: doğru</span><span class="sxs-lookup"><span data-stu-id="6b811-567">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="6b811-568">Koruma sırası: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="6b811-568">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="6b811-569">Imzayı şifreleyin: doğru</span><span class="sxs-lookup"><span data-stu-id="6b811-569">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="6b811-570">İlke</span><span class="sxs-lookup"><span data-stu-id="6b811-570">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="6b811-571">Güvenlik üst bilgisi örnekleri: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="6b811-571">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="6b811-572">İstek</span><span class="sxs-lookup"><span data-stu-id="6b811-572">Request</span></span>  
  
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
  
 <span data-ttu-id="6b811-573">Yanıtıyla</span><span class="sxs-lookup"><span data-stu-id="6b811-573">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="6b811-574">Güvenlik üst bilgisi örnekleri: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="6b811-574">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="6b811-575">İstek</span><span class="sxs-lookup"><span data-stu-id="6b811-575">Request</span></span>  
  
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
  
 <span data-ttu-id="6b811-576">Yanıtıyla</span><span class="sxs-lookup"><span data-stu-id="6b811-576">Response</span></span>  
  
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
  
### <a name="67-secureconversation"></a><span data-ttu-id="6b811-577">6,7 SecureConversation</span><span class="sxs-lookup"><span data-stu-id="6b811-577">6.7 SecureConversation</span></span>  
 <span data-ttu-id="6b811-578">Kullanılan bağlama, bir WS-SecureConversation (WS-SC) başına bir SCT olan koruma belirtecine sahip simetrik bir bağlamadır.</span><span class="sxs-lookup"><span data-stu-id="6b811-578">The binding used is a symmetric binding with the protection token being a SCT per WS-SecureConversation (WS-SC).</span></span> <span data-ttu-id="6b811-579">SCT, bir anlaşma Protokolü kullanan simetrik bağlama olan, iç içe bir bağlamaya göre WS-Trust (WS-Trust) veya WS-SecureConversation (WS-SC) kullanılarak görüşülür.</span><span class="sxs-lookup"><span data-stu-id="6b811-579">The SCT is negotiated using WS-Trust (WS-Trust) or WS-SecureConversation (WS-SC) according to a nested binding, which is itself a symmetric binding that uses a negotiation protocol.</span></span> <span data-ttu-id="6b811-580">Anlaşma Protokolü, mümkünse istemci ve sunucu kimlik doğrulaması gerçekleştirmek için Kerberos kullanır.</span><span class="sxs-lookup"><span data-stu-id="6b811-580">The negotiation protocol will use Kerberos to perform client and server authentication if possible.</span></span> <span data-ttu-id="6b811-581">Kerberos kullanılmıyorsa, NTLM 'ye geri döner.</span><span class="sxs-lookup"><span data-stu-id="6b811-581">If Kerberos cannot be used, it will fall back to NTLM.</span></span>  
  
 <span data-ttu-id="6b811-582">İlke</span><span class="sxs-lookup"><span data-stu-id="6b811-582">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="6b811-583">Güvenlik üst bilgisi örnekleri: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="6b811-583">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="6b811-584">İstek</span><span class="sxs-lookup"><span data-stu-id="6b811-584">Request</span></span>  
  
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
  
 <span data-ttu-id="6b811-585">Yanıtıyla</span><span class="sxs-lookup"><span data-stu-id="6b811-585">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="6b811-586">Güvenlik üst bilgisi örnekleri: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="6b811-586">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="6b811-587">İstek</span><span class="sxs-lookup"><span data-stu-id="6b811-587">Request</span></span>  
  
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
  
 <span data-ttu-id="6b811-588">Yanıtıyla</span><span class="sxs-lookup"><span data-stu-id="6b811-588">Response</span></span>  
  
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

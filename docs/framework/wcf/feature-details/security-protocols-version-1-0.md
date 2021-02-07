---
description: 'Daha fazla bilgi edinin: güvenlik protokolleri sürüm 1,0'
title: Güvenlik Protokolleri sürüm 1.0
ms.date: 03/30/2017
ms.assetid: ee3402d2-1076-410b-a3cb-fae0372bd7af
ms.openlocfilehash: c807f0b844fb9cb861148afa63d83826a9740c98
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752736"
---
# <a name="security-protocols-version-10"></a><span data-ttu-id="4f598-103">Güvenlik Protokolleri sürüm 1.0</span><span class="sxs-lookup"><span data-stu-id="4f598-103">Security Protocols version 1.0</span></span>

<span data-ttu-id="4f598-104">Web Hizmetleri Güvenliği protokolleri, mevcut tüm kurumsal mesajlaşma güvenlik gereksinimlerini kapsayan Web Hizmetleri güvenlik mekanizmaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="4f598-104">The Web Services Security Protocols provide Web services security mechanisms that cover all existing enterprise messaging security requirements.</span></span> <span data-ttu-id="4f598-105">Bu bölümde, <xref:System.ServiceModel.Channels.SecurityBindingElement> aşağıdaki Web Hizmetleri güvenlik protokolleri için Windows Communication Foundation (WCF) sürüm 1,0 ayrıntıları (' de uygulanır) açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4f598-105">This section describes the Windows Communication Foundation (WCF) version 1.0 details (implemented in the <xref:System.ServiceModel.Channels.SecurityBindingElement>) for the following Web services security protocols.</span></span>  
  
|<span data-ttu-id="4f598-106">Belirtim/belge</span><span class="sxs-lookup"><span data-stu-id="4f598-106">Specification/Document</span></span>|<span data-ttu-id="4f598-107">Bağlantı</span><span class="sxs-lookup"><span data-stu-id="4f598-107">Link</span></span>|  
|-|-|  
|<span data-ttu-id="4f598-108">WSS: SOAP Iletisi güvenliği 1,0</span><span class="sxs-lookup"><span data-stu-id="4f598-108">WSS: SOAP Message Security 1.0</span></span>|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf>|
|<span data-ttu-id="4f598-109">WSS: Kullanıcı adı belirteç profili 1,0</span><span class="sxs-lookup"><span data-stu-id="4f598-109">WSS: Username Token Profile 1.0</span></span>|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf>|
|<span data-ttu-id="4f598-110">WSS: x509 belirteç profili 1,0</span><span class="sxs-lookup"><span data-stu-id="4f598-110">WSS: X509 Token Profile 1.0</span></span>|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0.pdf>|
|<span data-ttu-id="4f598-111">WSS: SAML 1,1 belirteç profili 1,0</span><span class="sxs-lookup"><span data-stu-id="4f598-111">WSS: SAML 1.1 Token Profile 1.0</span></span>|<https://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.0.pdf>|
|<span data-ttu-id="4f598-112">WSS: SOAP Iletisi güvenliği 1,1</span><span class="sxs-lookup"><span data-stu-id="4f598-112">WSS: SOAP Message Security 1.1</span></span>|<https://www.oasis-open.org/committees/download.php/16790/wss-v1.1-spec-os-SOAPMessageSecurity.pdf>|
|<span data-ttu-id="4f598-113">WSS Kullanıcı adı belirteç profili 1,1</span><span class="sxs-lookup"><span data-stu-id="4f598-113">WSS Username Token Profile 1.1</span></span>|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf>|
|<span data-ttu-id="4f598-114">WSS: X. 509.440 belirteç profili 1,1</span><span class="sxs-lookup"><span data-stu-id="4f598-114">WSS: X.509 Token Profile 1.1</span></span>|<https://www.oasis-open.org/committees/download.php/16785/wss-v1.1-spec-os-x509TokenProfile.pdf>|
|<span data-ttu-id="4f598-115">WSS: Kerberos belirteç profili 1,1</span><span class="sxs-lookup"><span data-stu-id="4f598-115">WSS: Kerberos Token Profile 1.1</span></span>|<https://www.oasis-open.org/committees/download.php/16788/wss-v1.1-spec-os-KerberosTokenProfile.pdf>|
|<span data-ttu-id="4f598-116">WSS: SAML 1,1 belirteç profili 1,1</span><span class="sxs-lookup"><span data-stu-id="4f598-116">WSS: SAML 1.1 Token Profile 1.1</span></span>|<https://www.oasis-open.org/committees/download.php/16768/wss-v1.1-spec-os-SAMLTokenProfile.pdf>|
|<span data-ttu-id="4f598-117">WS-Secure konuşması</span><span class="sxs-lookup"><span data-stu-id="4f598-117">WS-Secure Conversation</span></span>|<http://specs.xmlsoap.org/ws/2005/02/sc/WS-SecureConversation.pdf>|
|<span data-ttu-id="4f598-118">WS-Trust</span><span class="sxs-lookup"><span data-stu-id="4f598-118">WS-Trust</span></span>|<http://specs.xmlsoap.org/ws/2005/02/trust/ws-trust.pdf>|
|<span data-ttu-id="4f598-119">Uygulama notunun:</span><span class="sxs-lookup"><span data-stu-id="4f598-119">Application Note:</span></span><br /><br /> <span data-ttu-id="4f598-120">TLS el sıkışması için WS-Trust kullanma</span><span class="sxs-lookup"><span data-stu-id="4f598-120">Using WS-Trust for TLS Handshake</span></span>|<span data-ttu-id="4f598-121">Yayımlanacak</span><span class="sxs-lookup"><span data-stu-id="4f598-121">To be published</span></span>|  
|<span data-ttu-id="4f598-122">Uygulama notunun:</span><span class="sxs-lookup"><span data-stu-id="4f598-122">Application Note:</span></span><br /><br /> <span data-ttu-id="4f598-123">SPNEGO için WS-Trust kullanma</span><span class="sxs-lookup"><span data-stu-id="4f598-123">Using WS-Trust for SPNEGO</span></span>|<span data-ttu-id="4f598-124">Yayımlanacak</span><span class="sxs-lookup"><span data-stu-id="4f598-124">To be published</span></span>|  
|<span data-ttu-id="4f598-125">Uygulama notunun:</span><span class="sxs-lookup"><span data-stu-id="4f598-125">Application Note:</span></span><br /><br /> <span data-ttu-id="4f598-126">Web Hizmetleri, uç nokta başvurularını ve kimliğini adresleyen</span><span class="sxs-lookup"><span data-stu-id="4f598-126">Web Services Addressing Endpoint References And Identity</span></span>|<span data-ttu-id="4f598-127">Yayımlanacak</span><span class="sxs-lookup"><span data-stu-id="4f598-127">To be published</span></span>|  
|<span data-ttu-id="4f598-128">WS-SecurityPolicy 1,1</span><span class="sxs-lookup"><span data-stu-id="4f598-128">WS-SecurityPolicy 1.1</span></span><br /><br /> <span data-ttu-id="4f598-129">(2005/07)</span><span class="sxs-lookup"><span data-stu-id="4f598-129">(2005/07)</span></span>|<http://specs.xmlsoap.org/ws/2005/07/securitypolicy/ws-securitypolicy.pdf><br /><br /> <span data-ttu-id="4f598-130">OASSıS WS-SX Technical komite 'a gönderilen [Errata](https://lists.oasis-open.org/archives/ws-sx/200512/msg00017.html) tarafından değiştirilen</span><span class="sxs-lookup"><span data-stu-id="4f598-130">as amended by [errata](https://lists.oasis-open.org/archives/ws-sx/200512/msg00017.html) submitted to OASIS WS-SX Technical Committee</span></span> |  
  
 <span data-ttu-id="4f598-131">WCF, sürüm 1, Web Hizmetleri güvenlik yapılandırması için temel olarak kullanılabilecek 17 kimlik doğrulama modu sağlar.</span><span class="sxs-lookup"><span data-stu-id="4f598-131">WCF, version 1, provides 17 authentication modes that can be used as the basis for Web services security configuration.</span></span> <span data-ttu-id="4f598-132">Her mod ortak bir dağıtım gereksinimleri kümesi için iyileştirilmiştir, örneğin:</span><span class="sxs-lookup"><span data-stu-id="4f598-132">Each mode is optimized for a common set of deployment requirements, such as:</span></span>  
  
- <span data-ttu-id="4f598-133">İstemci ve hizmetin kimliğini doğrulamak için kullanılan kimlik bilgileri.</span><span class="sxs-lookup"><span data-stu-id="4f598-133">Credentials used to authenticate client and service.</span></span>  
  
- <span data-ttu-id="4f598-134">İleti veya aktarım güvenliği koruma mekanizmaları.</span><span class="sxs-lookup"><span data-stu-id="4f598-134">Message or transport security protection mechanisms.</span></span>  
  
- <span data-ttu-id="4f598-135">İleti değişimi desenleri.</span><span class="sxs-lookup"><span data-stu-id="4f598-135">Message exchange patterns.</span></span>  
  
|<span data-ttu-id="4f598-136">Kimlik Doğrulaması Modu</span><span class="sxs-lookup"><span data-stu-id="4f598-136">Authentication Mode</span></span>|<span data-ttu-id="4f598-137">İstemci Kimlik Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="4f598-137">Client Authentication</span></span>|<span data-ttu-id="4f598-138">Sunucu kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="4f598-138">Server Authentication</span></span>|<span data-ttu-id="4f598-139">Mod</span><span class="sxs-lookup"><span data-stu-id="4f598-139">Mode</span></span>|  
|-------------------------|---------------------------|---------------------------|----------|  
|<span data-ttu-id="4f598-140">UserNameOverTransport</span><span class="sxs-lookup"><span data-stu-id="4f598-140">UserNameOverTransport</span></span>|<span data-ttu-id="4f598-141">Kullanıcı adı/parola</span><span class="sxs-lookup"><span data-stu-id="4f598-141">User name/password</span></span>|<span data-ttu-id="4f598-142">X509</span><span class="sxs-lookup"><span data-stu-id="4f598-142">X509</span></span>|<span data-ttu-id="4f598-143">Aktarım</span><span class="sxs-lookup"><span data-stu-id="4f598-143">Transport</span></span>|  
|<span data-ttu-id="4f598-144">CertificateOverTransport</span><span class="sxs-lookup"><span data-stu-id="4f598-144">CertificateOverTransport</span></span>|<span data-ttu-id="4f598-145">X509</span><span class="sxs-lookup"><span data-stu-id="4f598-145">X509</span></span>|<span data-ttu-id="4f598-146">X509</span><span class="sxs-lookup"><span data-stu-id="4f598-146">X509</span></span>|<span data-ttu-id="4f598-147">Aktarım</span><span class="sxs-lookup"><span data-stu-id="4f598-147">Transport</span></span>|  
|<span data-ttu-id="4f598-148">KerberosOverTransport</span><span class="sxs-lookup"><span data-stu-id="4f598-148">KerberosOverTransport</span></span>|<span data-ttu-id="4f598-149">Windows</span><span class="sxs-lookup"><span data-stu-id="4f598-149">Windows</span></span>|<span data-ttu-id="4f598-150">X509</span><span class="sxs-lookup"><span data-stu-id="4f598-150">X509</span></span>|<span data-ttu-id="4f598-151">Aktarım</span><span class="sxs-lookup"><span data-stu-id="4f598-151">Transport</span></span>|  
|<span data-ttu-id="4f598-152">IssuedTokenOverTransport</span><span class="sxs-lookup"><span data-stu-id="4f598-152">IssuedTokenOverTransport</span></span>|<span data-ttu-id="4f598-153">Federe</span><span class="sxs-lookup"><span data-stu-id="4f598-153">Federated</span></span>|<span data-ttu-id="4f598-154">X509</span><span class="sxs-lookup"><span data-stu-id="4f598-154">X509</span></span>|<span data-ttu-id="4f598-155">Aktarım</span><span class="sxs-lookup"><span data-stu-id="4f598-155">Transport</span></span>|  
|<span data-ttu-id="4f598-156">SspiNegotiatedOverTransport</span><span class="sxs-lookup"><span data-stu-id="4f598-156">SspiNegotiatedOverTransport</span></span>|<span data-ttu-id="4f598-157">Üzerinde anlaşılan Windows SSPI</span><span class="sxs-lookup"><span data-stu-id="4f598-157">Windows Sspi Negotiated</span></span>|<span data-ttu-id="4f598-158">Üzerinde anlaşılan Windows SSPI</span><span class="sxs-lookup"><span data-stu-id="4f598-158">Windows Sspi Negotiated</span></span>|<span data-ttu-id="4f598-159">Aktarım</span><span class="sxs-lookup"><span data-stu-id="4f598-159">Transport</span></span>|  
|<span data-ttu-id="4f598-160">AnonymousForCertificate</span><span class="sxs-lookup"><span data-stu-id="4f598-160">AnonymousForCertificate</span></span>|<span data-ttu-id="4f598-161">Yok</span><span class="sxs-lookup"><span data-stu-id="4f598-161">None</span></span>|<span data-ttu-id="4f598-162">X509</span><span class="sxs-lookup"><span data-stu-id="4f598-162">X509</span></span>|<span data-ttu-id="4f598-163">İleti</span><span class="sxs-lookup"><span data-stu-id="4f598-163">Message</span></span>|  
|<span data-ttu-id="4f598-164">UserNameForCertificate</span><span class="sxs-lookup"><span data-stu-id="4f598-164">UserNameForCertificate</span></span>|<span data-ttu-id="4f598-165">Kullanıcı adı/parola</span><span class="sxs-lookup"><span data-stu-id="4f598-165">User name/password</span></span>|<span data-ttu-id="4f598-166">X509</span><span class="sxs-lookup"><span data-stu-id="4f598-166">X509</span></span>|<span data-ttu-id="4f598-167">İleti</span><span class="sxs-lookup"><span data-stu-id="4f598-167">Message</span></span>|  
|<span data-ttu-id="4f598-168">Çoklu sertifika</span><span class="sxs-lookup"><span data-stu-id="4f598-168">MutualCertificate</span></span>|<span data-ttu-id="4f598-169">X509</span><span class="sxs-lookup"><span data-stu-id="4f598-169">X509</span></span>|<span data-ttu-id="4f598-170">X509</span><span class="sxs-lookup"><span data-stu-id="4f598-170">X509</span></span>|<span data-ttu-id="4f598-171">İleti</span><span class="sxs-lookup"><span data-stu-id="4f598-171">Message</span></span>|  
|<span data-ttu-id="4f598-172">Değişken Uıalcertificateduplex</span><span class="sxs-lookup"><span data-stu-id="4f598-172">MutualCertificateDuplex</span></span>|<span data-ttu-id="4f598-173">X509</span><span class="sxs-lookup"><span data-stu-id="4f598-173">X509</span></span>|<span data-ttu-id="4f598-174">X509</span><span class="sxs-lookup"><span data-stu-id="4f598-174">X509</span></span>|<span data-ttu-id="4f598-175">İleti</span><span class="sxs-lookup"><span data-stu-id="4f598-175">Message</span></span>|  
|<span data-ttu-id="4f598-176">IssuedTokenForCertificate</span><span class="sxs-lookup"><span data-stu-id="4f598-176">IssuedTokenForCertificate</span></span>|<span data-ttu-id="4f598-177">Federe</span><span class="sxs-lookup"><span data-stu-id="4f598-177">Federated</span></span>|<span data-ttu-id="4f598-178">X509</span><span class="sxs-lookup"><span data-stu-id="4f598-178">X509</span></span>|<span data-ttu-id="4f598-179">İleti</span><span class="sxs-lookup"><span data-stu-id="4f598-179">Message</span></span>|  
|<span data-ttu-id="4f598-180">Kerberos</span><span class="sxs-lookup"><span data-stu-id="4f598-180">Kerberos</span></span>|<span data-ttu-id="4f598-181">Windows</span><span class="sxs-lookup"><span data-stu-id="4f598-181">Windows</span></span>|<span data-ttu-id="4f598-182">Windows</span><span class="sxs-lookup"><span data-stu-id="4f598-182">Windows</span></span>|<span data-ttu-id="4f598-183">İleti</span><span class="sxs-lookup"><span data-stu-id="4f598-183">Message</span></span>|  
|<span data-ttu-id="4f598-184">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="4f598-184">IssuedToken</span></span>|<span data-ttu-id="4f598-185">Federe</span><span class="sxs-lookup"><span data-stu-id="4f598-185">Federated</span></span>|<span data-ttu-id="4f598-186">Federe</span><span class="sxs-lookup"><span data-stu-id="4f598-186">Federated</span></span>|<span data-ttu-id="4f598-187">İleti</span><span class="sxs-lookup"><span data-stu-id="4f598-187">Message</span></span>|  
|<span data-ttu-id="4f598-188">SspiNegotiated</span><span class="sxs-lookup"><span data-stu-id="4f598-188">SspiNegotiated</span></span>|<span data-ttu-id="4f598-189">Üzerinde anlaşılan Windows SSPI</span><span class="sxs-lookup"><span data-stu-id="4f598-189">Windows Sspi Negotiated</span></span>|<span data-ttu-id="4f598-190">Üzerinde anlaşılan Windows SSPI</span><span class="sxs-lookup"><span data-stu-id="4f598-190">Windows Sspi Negotiated</span></span>|<span data-ttu-id="4f598-191">İleti</span><span class="sxs-lookup"><span data-stu-id="4f598-191">Message</span></span>|  
|<span data-ttu-id="4f598-192">Anonymousforsslanlaşmalı</span><span class="sxs-lookup"><span data-stu-id="4f598-192">AnonymousForSslNegotiated</span></span>|<span data-ttu-id="4f598-193">Yok</span><span class="sxs-lookup"><span data-stu-id="4f598-193">None</span></span>|<span data-ttu-id="4f598-194">X509, TLS-Nego</span><span class="sxs-lookup"><span data-stu-id="4f598-194">X509, TLS-Nego</span></span>|<span data-ttu-id="4f598-195">İleti</span><span class="sxs-lookup"><span data-stu-id="4f598-195">Message</span></span>|  
|<span data-ttu-id="4f598-196">Usernameforsslanlaşmalı</span><span class="sxs-lookup"><span data-stu-id="4f598-196">UserNameForSslNegotiated</span></span>|<span data-ttu-id="4f598-197">Kullanıcı adı/parola</span><span class="sxs-lookup"><span data-stu-id="4f598-197">User name/password</span></span>|<span data-ttu-id="4f598-198">X509, TLS-Nego</span><span class="sxs-lookup"><span data-stu-id="4f598-198">X509, TLS-Nego</span></span>|<span data-ttu-id="4f598-199">İleti</span><span class="sxs-lookup"><span data-stu-id="4f598-199">Message</span></span>|  
|<span data-ttu-id="4f598-200">Değişken anlaşmalı</span><span class="sxs-lookup"><span data-stu-id="4f598-200">MutualSslNegotiated</span></span>|<span data-ttu-id="4f598-201">X509</span><span class="sxs-lookup"><span data-stu-id="4f598-201">X509</span></span>|<span data-ttu-id="4f598-202">X509, TLS-Nego</span><span class="sxs-lookup"><span data-stu-id="4f598-202">X509, TLS-Nego</span></span>|<span data-ttu-id="4f598-203">İleti</span><span class="sxs-lookup"><span data-stu-id="4f598-203">Message</span></span>|  
|<span data-ttu-id="4f598-204">Issuedtokenforsslanlaşmalı</span><span class="sxs-lookup"><span data-stu-id="4f598-204">IssuedTokenForSslNegotiated</span></span>|<span data-ttu-id="4f598-205">Federe</span><span class="sxs-lookup"><span data-stu-id="4f598-205">Federated</span></span>|<span data-ttu-id="4f598-206">X509, TLS-Nego</span><span class="sxs-lookup"><span data-stu-id="4f598-206">X509, TLS-Nego</span></span>|<span data-ttu-id="4f598-207">İleti</span><span class="sxs-lookup"><span data-stu-id="4f598-207">Message</span></span>|  
  
 <span data-ttu-id="4f598-208">Bu tür kimlik doğrulama modlarını kullanan uç noktalar, WS-SecurityPolicy (WS-SP) kullanarak güvenlik gereksinimlerini ifade edebilir.</span><span class="sxs-lookup"><span data-stu-id="4f598-208">Endpoints using such authentication modes can express their security requirements using WS-SecurityPolicy (WS-SP).</span></span> <span data-ttu-id="4f598-209">Bu belgede, her kimlik doğrulama modu için güvenlik üst bilgisi ve altyapı iletilerinin yapısı açıklanmakta ve ilke ve ileti örnekleri verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4f598-209">This document describes the structure of security header and infrastructure messages for each authentication mode and provides examples of policies and messages.</span></span>  
  
 <span data-ttu-id="4f598-210">WCF, uygulamalar arasında çok ileti değişimlerinin korunması için güvenli oturumlar desteği sağlamak üzere WS-SecureConversation yararlanır.</span><span class="sxs-lookup"><span data-stu-id="4f598-210">WCF leverages WS-SecureConversation to provide secure sessions support to protect multi-message exchanges between applications.</span></span>  <span data-ttu-id="4f598-211">Uygulama ayrıntıları için aşağıda "güvenli oturumlar" başlığına bakın.</span><span class="sxs-lookup"><span data-stu-id="4f598-211">See "Secure Sessions" below for implementation details.</span></span>  
  
 <span data-ttu-id="4f598-212">WCF, kimlik doğrulama modlarına ek olarak, çoğu ileti güvenlik tabanlı kimlik doğrulama modu için uygulanan genel koruma mekanizmalarını denetlemek için ayarlar sağlar; örneğin, imza sırası, şifreleme işlemleri, algoritma paketleri, anahtar türetme ve imza onayı.</span><span class="sxs-lookup"><span data-stu-id="4f598-212">In addition to authentication modes, WCF provides settings to control common protection mechanisms that apply to most message security-based authentication modes, for example: order of signature versus encryption operations, algorithm suites, key derivation, and signature confirmation.</span></span>  
  
 <span data-ttu-id="4f598-213">Bu belgede aşağıdaki ön ekler ve ad alanları kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4f598-213">The following prefixes and namespaces are used in this document.</span></span>  
  
|<span data-ttu-id="4f598-214">Ön ek</span><span class="sxs-lookup"><span data-stu-id="4f598-214">Prefix</span></span>|<span data-ttu-id="4f598-215">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="4f598-215">Namespace</span></span>|  
|------------|---------------|  
|<span data-ttu-id="4f598-216">s</span><span class="sxs-lookup"><span data-stu-id="4f598-216">s</span></span>|<http://www.w3.org/2003/05/soap-envelope/>|
|<span data-ttu-id="4f598-217">sp</span><span class="sxs-lookup"><span data-stu-id="4f598-217">sp</span></span>|<http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/>|
|<span data-ttu-id="4f598-218">a</span><span class="sxs-lookup"><span data-stu-id="4f598-218">a</span></span>|<http://www.w3.org/2005/08/addressing>|  
|<span data-ttu-id="4f598-219">WSO</span><span class="sxs-lookup"><span data-stu-id="4f598-219">wsse</span></span>|<span data-ttu-id="4f598-220">TBD – OASSıS WSS 1,0 URI 'SI</span><span class="sxs-lookup"><span data-stu-id="4f598-220">TBD – OASIS WSS 1.0 URI</span></span>|  
|<span data-ttu-id="4f598-221">wsse11</span><span class="sxs-lookup"><span data-stu-id="4f598-221">wsse11</span></span>|<span data-ttu-id="4f598-222">TBD – OASSıS WSS 1,1 URI 'SI</span><span class="sxs-lookup"><span data-stu-id="4f598-222">TBD – OASIS WSS 1.1 URI</span></span>|  
|<span data-ttu-id="4f598-223">WSU dili</span><span class="sxs-lookup"><span data-stu-id="4f598-223">wsu</span></span>|<span data-ttu-id="4f598-224">TBD – OASSıS WSS 1,0 yardımcı programı URI 'SI</span><span class="sxs-lookup"><span data-stu-id="4f598-224">TBD – OASIS WSS 1.0 Utility URI</span></span>|  
|<span data-ttu-id="4f598-225">FID</span><span class="sxs-lookup"><span data-stu-id="4f598-225">ds</span></span>|<span data-ttu-id="4f598-226">TBD – W3C XMLDSIG URI 'SI</span><span class="sxs-lookup"><span data-stu-id="4f598-226">TBD – W3C XMLDSig URI</span></span>|  
|<span data-ttu-id="4f598-227">WST</span><span class="sxs-lookup"><span data-stu-id="4f598-227">wst</span></span>|<span data-ttu-id="4f598-228">TBD – WS-Trust 2005/02 URI 'SI</span><span class="sxs-lookup"><span data-stu-id="4f598-228">TBD – WS-Trust 2005/02 URI</span></span>|  
|<span data-ttu-id="4f598-229">wssc</span><span class="sxs-lookup"><span data-stu-id="4f598-229">wssc</span></span>|<span data-ttu-id="4f598-230">TBD – WS-SecureConversation 2005/02 URI 'SI</span><span class="sxs-lookup"><span data-stu-id="4f598-230">TBD – WS-SecureConversation 2005/02 URI</span></span>|  
|<span data-ttu-id="4f598-231">Wonu dili</span><span class="sxs-lookup"><span data-stu-id="4f598-231">wsaw</span></span>|<span data-ttu-id="4f598-232">TBD-WS-Addressing ilkesi ad alanı</span><span class="sxs-lookup"><span data-stu-id="4f598-232">TBD - WS-Addressing policy namespace</span></span>|  
|<span data-ttu-id="4f598-233">WSP</span><span class="sxs-lookup"><span data-stu-id="4f598-233">wsp</span></span>|<http://schemas.xmlsoap.org/ws/2004/09/policy>|  
|<span data-ttu-id="4f598-234">MSSP</span><span class="sxs-lookup"><span data-stu-id="4f598-234">mssp</span></span>|<http://schemas.xmlsoap.org/ws/2005/07/securitypolicy>|
  
## <a name="1-token-profiles"></a><span data-ttu-id="4f598-235">1. belirteç profilleri</span><span class="sxs-lookup"><span data-stu-id="4f598-235">1. Token Profiles</span></span>  

 <span data-ttu-id="4f598-236">Web Hizmetleri Güvenliği belirtimleri güvenlik belirteçleri olarak kimlik bilgisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4f598-236">Web Services Security specifications represent credential as security tokens.</span></span> <span data-ttu-id="4f598-237">WCF aşağıdaki belirteç türlerini destekler:</span><span class="sxs-lookup"><span data-stu-id="4f598-237">WCF supports the following token types:</span></span>  
  
### <a name="11-usernametoken"></a><span data-ttu-id="4f598-238">1,1 UsernameToken</span><span class="sxs-lookup"><span data-stu-id="4f598-238">1.1 UsernameToken</span></span>  

 <span data-ttu-id="4f598-239">WCF aşağıdaki kısıtlamalara sahip UsernameToken10 ve UsernameToken11 profillerini izler:</span><span class="sxs-lookup"><span data-stu-id="4f598-239">WCF follows UsernameToken10 and UsernameToken11 profiles with the following constraints:</span></span>  
  
 <span data-ttu-id="4f598-240">UsernameToken\Password öğesinde R1101 PasswordType özniteliği atlanmış veya değer #PasswordText (varsayılan) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4f598-240">R1101 PasswordType attribute on UsernameToken\Password element MUST be either omitted or have value #PasswordText (default).</span></span>  
  
 <span data-ttu-id="4f598-241">Bunlardan biri, genişletilebilirlik kullanarak #PasswordDigest uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="4f598-241">One can implement the #PasswordDigest using extensibility.</span></span> <span data-ttu-id="4f598-242">#PasswordDigest genellikle yeterince güvenli bir parola koruma mekanizması olması gözlemlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="4f598-242">It has been observed that #PasswordDigest was often mistaken to be a secure enough password protection mechanism.</span></span> <span data-ttu-id="4f598-243">Ancak #PasswordDigest, UsernameToken şifrelemesinin bir alternatifi olarak kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="4f598-243">But #PasswordDigest cannot serve as a substitute for encryption of the UsernameToken.</span></span> <span data-ttu-id="4f598-244">#PasswordDigest birincil amacı, yeniden yürütme saldırılarına karşı koruma sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="4f598-244">The primary goal of #PasswordDigest is protection against replay attacks.</span></span> <span data-ttu-id="4f598-245">WCF kimlik doğrulama modlarında, yeniden yürütme saldırı tehditleri ileti imzaları kullanılarak azaltıldığında.</span><span class="sxs-lookup"><span data-stu-id="4f598-245">In WCF authentication modes, replay attack threats are mitigated by using message signatures.</span></span>  
  
 <span data-ttu-id="4f598-246">B1102 WCF hiçbir şekilde hiçbir şekilde anahtar vermez ve UsernameToken alt öğelerini oluşturmuştur.</span><span class="sxs-lookup"><span data-stu-id="4f598-246">B1102 WCF never emits Nonce and Created sub-elements of the UsernameToken.</span></span>  
  
 <span data-ttu-id="4f598-247">Bu alt öğeler, yeniden yürütmeyi algılamaya yardımcı olmayı amaçlar.</span><span class="sxs-lookup"><span data-stu-id="4f598-247">These sub-elements are intended to help replay detection.</span></span> <span data-ttu-id="4f598-248">WCF bunun yerine ileti imzalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="4f598-248">WCF uses message signatures instead.</span></span>  
  
 <span data-ttu-id="4f598-249">OASSıS WSS SOAP Iletisi güvenliği UsernameToken profili 1,1 (UsernameToken11) parola özelliğinden anahtar türetme sunmuştur.</span><span class="sxs-lookup"><span data-stu-id="4f598-249">OASIS WSS SOAP Message Security UsernameToken Profile 1.1 (UsernameToken11) introduced key derivation from password feature.</span></span>  
  
 <span data-ttu-id="4f598-250">B1103 UsernameToken parolası, anahtar türetmede kullanılmamalıdır ve bu nedenle şifreleme işlemleri için kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="4f598-250">B1103 UsernameToken password MUST not be used for key derivation and therefore for cryptographic operations.</span></span>  
  
 <span data-ttu-id="4f598-251">Korale: parolalar genellikle şifreleme işlemleri için kullanılmak üzere çok zayıf kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="4f598-251">Rationale: passwords are generally considered too weak to be used for cryptographic operations.</span></span>  
  
### <a name="12-x509-token"></a><span data-ttu-id="4f598-252">1,2 x509 belirteci</span><span class="sxs-lookup"><span data-stu-id="4f598-252">1.2 X509 Token</span></span>  

 <span data-ttu-id="4f598-253">WCF, kimlik bilgisi türü olarak X509v3 sertifikalarını destekler ve aşağıdaki kısıtlamalara sahip X509TokenProfile 1.0 ve X509TokenProfile 1.1 ' i izler:</span><span class="sxs-lookup"><span data-stu-id="4f598-253">WCF supports X509v3 certificates as a credential type and follows X509TokenProfile1.0 and X509TokenProfile1.1 with the following constraints:</span></span>  
  
 <span data-ttu-id="4f598-254">R1201, BinarySecurityToken öğesindeki ValueType özniteliği bir X509v3 sertifikası içerdiğinde değer #X509v3 sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4f598-254">R1201 The ValueType attribute on the BinarySecurityToken element must have value #X509v3 when it contains an X509v3 certificate.</span></span>  
  
 <span data-ttu-id="4f598-255">WSS x509 belirteç profili 1,0 ve 1,1 de #X509PKIPathv1 ve #PKCS7 değer türleri olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4f598-255">WSS X509 Token Profile 1.0 and 1.1 define also #X509PKIPathv1 and #PKCS7 as value types.</span></span> <span data-ttu-id="4f598-256">WCF bu türleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="4f598-256">WCF does not support these types.</span></span>  
  
 <span data-ttu-id="4f598-257">R1202 bir subjectKeyIdentifier (kayak) uzantısı, bir x509 sertifikasında mevcutsa,, #X509SubjectKeyIdentifier ve içeriği için ValueType özniteliği ve Content 'in Kayak uzantısının şifreli değeri olan ' a yönelik dış başvurular için, WSI: KeyIdentifier kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4f598-257">R1202 If a SubjectKeyIdentifier (SKI) extension is present in an X509 certificate, wsse:KeyIdentifier should be used for external references to the token, with the ValueType attribute as #X509SubjectKeyIdentifier and its content the base64-encoded value of certificate's SKI extension.</span></span>  
  
 <span data-ttu-id="4f598-258">Kayak başvuruları yaygın olarak uygulanırlar ve yüksek oranda çalışabilen bir dış başvuru türü olarak kanıtlanmış olur.</span><span class="sxs-lookup"><span data-stu-id="4f598-258">SKI references are widely implemented and proven to be a highly interoperable external reference type.</span></span>  
  
 <span data-ttu-id="4f598-259">R1203 x509 güvenlik belirtecine bir dış başvuru DS: X509IssuerSerial KULLANMAMALıDıR.</span><span class="sxs-lookup"><span data-stu-id="4f598-259">R1203 An external Reference to X509 Security Token SHOULD NOT use ds:X509IssuerSerial.</span></span>  
  
 <span data-ttu-id="4f598-260">R1204 X509TokenProfile 1.1 kullanılıyorsa, x509 güvenlik belirtecine yönelik bir dış başvurunun WS-Security 1,1 tarafından tanıtılan parmak izini kullanması gerekır.</span><span class="sxs-lookup"><span data-stu-id="4f598-260">R1204 If X509TokenProfile1.1 is in use, an external reference to X509 Security Token SHOULD use the thumbprint introduced by WS-Security 1.1.</span></span>  
  
 <span data-ttu-id="4f598-261">WCF, X509IssuerSerial destekler.</span><span class="sxs-lookup"><span data-stu-id="4f598-261">WCF supports X509IssuerSerial.</span></span> <span data-ttu-id="4f598-262">Ancak X509IssuerSerial ile birlikte çalışabilirlik sorunları vardır: WCF, X509IssuerSerial 'in iki değerini karşılaştırmak için bir dize kullanır.</span><span class="sxs-lookup"><span data-stu-id="4f598-262">However There are interoperability issues with X509IssuerSerial: WCF uses a string to compare two values of X509IssuerSerial.</span></span> <span data-ttu-id="4f598-263">Bu nedenle, konu adının bileşenlerini yeniden sipariş eden bir, bir WCF hizmetine bir sertifikaya başvuru gönderirse, bu durum bulunamamıştır.</span><span class="sxs-lookup"><span data-stu-id="4f598-263">Therefore if one reorders components of the Subject Name and sends to an WCF service a reference to a certificate, it may not be found.</span></span>  
  
### <a name="13-kerberos-token"></a><span data-ttu-id="4f598-264">1,3 Kerberos belirteci</span><span class="sxs-lookup"><span data-stu-id="4f598-264">1.3 Kerberos Token</span></span>  

 <span data-ttu-id="4f598-265">WCF, Windows kimlik doğrulaması amacıyla aşağıdaki kısıtlamalara sahip KerberosTokenProfile 1.1 'yi destekler:</span><span class="sxs-lookup"><span data-stu-id="4f598-265">WCF supports KerberosTokenProfile1.1 for the purpose of Windows authentication with the following constraints:</span></span>  
  
 <span data-ttu-id="4f598-266">R1301 bir Kerberos belirtecinin, GSS_API ve Kerberos belirtiminde tanımlanan bir GSS sarmalanmış Kerberos v4 AP_REQ değerini taşıması ve değer #GSS_Kerberosv5_AP_REQ ValueType özniteliğine sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4f598-266">R1301 A Kerberos Token must carry the value of a GSS wrapped Kerberos v4 AP_REQ as defined in GSS_API and the Kerberos specification, and must have the ValueType attribute with the value #GSS_Kerberosv5_AP_REQ.</span></span>  
  
 <span data-ttu-id="4f598-267">WCF, tam bir AP-REQ değil, GSS sarmalanmış Kerberos AP-REQ kullanır.</span><span class="sxs-lookup"><span data-stu-id="4f598-267">WCF uses GSS wrapped Kerberos AP-REQ, not a bare AP-REQ.</span></span> <span data-ttu-id="4f598-268">Bu en iyi güvenlik uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="4f598-268">This is a security best practice.</span></span>  
  
### <a name="14-saml-v11-token"></a><span data-ttu-id="4f598-269">1,4 SAML v 1.1 belirteci</span><span class="sxs-lookup"><span data-stu-id="4f598-269">1.4 SAML v1.1 Token</span></span>  

 <span data-ttu-id="4f598-270">WCF, SAML v 1.1 belirteçleri için WSS SAML belirteci profilleri 1,0 ve 1,1 ' ü destekler.</span><span class="sxs-lookup"><span data-stu-id="4f598-270">WCF supports WSS SAML Token profiles 1.0 and 1.1 for SAML v1.1 tokens.</span></span> <span data-ttu-id="4f598-271">SAML belirteci biçimlerinin diğer sürümlerini uygulamak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="4f598-271">It is possible to implement other versions of SAML token formats.</span></span>  
  
### <a name="15-security-context-token"></a><span data-ttu-id="4f598-272">1,5 güvenlik bağlamı belirteci</span><span class="sxs-lookup"><span data-stu-id="4f598-272">1.5 Security Context Token</span></span>  

 <span data-ttu-id="4f598-273">WCF, WS-SecureConversation ' de tanıtılan güvenlik bağlamı belirtecini (SCT) destekler.</span><span class="sxs-lookup"><span data-stu-id="4f598-273">WCF supports the Security Context Token (SCT) introduced in WS-SecureConversation.</span></span> <span data-ttu-id="4f598-274">SCT, SecureConversation 'de kurulu bir güvenlik bağlamını ve aşağıda açıklanan ikili anlaşma protokolleri TLS ve SSPI 'yi temsil etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4f598-274">SCT is used to represent a security context established in SecureConversation as well as the binary negotiation protocols TLS and SSPI, described below.</span></span>  
  
## <a name="2-common-message-security-parameters"></a><span data-ttu-id="4f598-275">2. ortak Ileti güvenlik parametreleri</span><span class="sxs-lookup"><span data-stu-id="4f598-275">2. Common Message Security Parameters</span></span>  
  
### <a name="21-timestamp"></a><span data-ttu-id="4f598-276">2,1 zaman damgası</span><span class="sxs-lookup"><span data-stu-id="4f598-276">2.1 TimeStamp</span></span>  

 <span data-ttu-id="4f598-277">Zaman damgası varlığı, <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> sınıfının özelliği kullanılarak denetlenir <xref:System.ServiceModel.Channels.SecurityBindingElement> .</span><span class="sxs-lookup"><span data-stu-id="4f598-277">Timestamp presence is controlled using the <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> property of the <xref:System.ServiceModel.Channels.SecurityBindingElement> class.</span></span> <span data-ttu-id="4f598-278">WCF her zaman wsse: Created ve wsse: Expires alanları ile zaman damgası olarak serileştirir.</span><span class="sxs-lookup"><span data-stu-id="4f598-278">WCF always serializes wsse:TimeStamp with wsse:Created and wsse:Expires fields.</span></span> <span data-ttu-id="4f598-279">Wsse: imza kullanıldığında zaman damgası her zaman imzalanır.</span><span class="sxs-lookup"><span data-stu-id="4f598-279">The wsse:TimeStamp is always signed when signing is used.</span></span>  
  
### <a name="22-protection-order"></a><span data-ttu-id="4f598-280">2,2 koruma sırası</span><span class="sxs-lookup"><span data-stu-id="4f598-280">2.2 Protection Order</span></span>  

 <span data-ttu-id="4f598-281">WCF, "şifrelemeden önce Imzala" ve "oturum açmadan önce şifreleyin" (Güvenlik Ilkesi 1,1) ileti koruma sırasını destekler.</span><span class="sxs-lookup"><span data-stu-id="4f598-281">WCF supports the message protection order "Sign Before Encrypt" and "Encrypt Before Sign" (Security Policy 1.1).</span></span> <span data-ttu-id="4f598-282">Aşağıdakiler dahil olmak üzere "şifrelemeden önce imzala" önerilir: oturum açmadan önce şifrelemeden korunan iletiler, WS-Security 1,1 SignatureConfirmation mekanizması kullanılmamışsa ve şifrelenmiş içerik üzerinde bir imza denetimi daha zor hale getirir.</span><span class="sxs-lookup"><span data-stu-id="4f598-282">"Sign Before Encrypt" is recommended for reasons including: messages protected with Encrypt Before Sign are open to signature substitution attacks unless the WS-Security 1.1 SignatureConfirmation mechanism is used, and a signature over encrypted content makes auditing harder.</span></span>  
  
### <a name="23-signature-protection"></a><span data-ttu-id="4f598-283">2,3 imza koruması</span><span class="sxs-lookup"><span data-stu-id="4f598-283">2.3 Signature Protection</span></span>  

 <span data-ttu-id="4f598-284">İmza kullanılmadan önce şifrelendiğinde, şifrelenmiş içeriği veya imzalama anahtarını tahmin etmeye yönelik deneme yanılma saldırılarını engellemek için imzayı korumanız önerilir (özellikle de, zayıf anahtar malzemeyle özel bir belirteç kullanıldığında).</span><span class="sxs-lookup"><span data-stu-id="4f598-284">When Encrypt Before Sign is used, it is recommended to protect the signature to prevent brute force attacks for guessing the encrypted content or the signing key (especially when a custom token is used with weak key material).</span></span>  
  
### <a name="24-algorithm-suite"></a><span data-ttu-id="4f598-285">2,4 algoritma paketi</span><span class="sxs-lookup"><span data-stu-id="4f598-285">2.4 Algorithm Suite</span></span>  

 <span data-ttu-id="4f598-286">WCF, Güvenlik Ilkesi 1,1 ' de listelenen tüm algoritma paketlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="4f598-286">WCF supports all algorithm suites listed in Security Policy 1.1.</span></span>  
  
### <a name="25-key-derivation"></a><span data-ttu-id="4f598-287">2,5 anahtar türetme</span><span class="sxs-lookup"><span data-stu-id="4f598-287">2.5 Key Derivation</span></span>  

 <span data-ttu-id="4f598-288">WCF, WS-SecureConversation bölümünde açıklandığı gibi "simetrik anahtarlar için anahtar türetme" kullanır.</span><span class="sxs-lookup"><span data-stu-id="4f598-288">WCF uses "Key Derivation for symmetric keys" as described in WS-SecureConversation.</span></span>  
  
### <a name="26-signature-confirmation"></a><span data-ttu-id="4f598-289">2,6 imza onayı</span><span class="sxs-lookup"><span data-stu-id="4f598-289">2.6 Signature Confirmation</span></span>  

 <span data-ttu-id="4f598-290">İmza onaylama, imza kümesini korumak için ortadaki adam saldırılarına karşı koruma sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="4f598-290">Signature confirmation can be as protection from middle man attacks to protect the set of signatures.</span></span>  
  
### <a name="27-security-header-layout"></a><span data-ttu-id="4f598-291">2,7 güvenlik üst bilgisi düzeni</span><span class="sxs-lookup"><span data-stu-id="4f598-291">2.7 Security Header Layout</span></span>  

 <span data-ttu-id="4f598-292">Her kimlik doğrulama modu, güvenlik üst bilgisi için belirli bir düzeni tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4f598-292">Each authentication mode describes a certain layout for the security header.</span></span> <span data-ttu-id="4f598-293">Güvenlik üst bilgisi içindeki öğeler yarı sıralanır.</span><span class="sxs-lookup"><span data-stu-id="4f598-293">Elements within the security header are semi-ordered.</span></span> <span data-ttu-id="4f598-294">Güvenlik üst bilgisi alt öğelerinin sırasını tanımlamak için WS-Security Ilkesi aşağıdaki güvenlik üst bilgisi düzen modlarını tanımlar:</span><span class="sxs-lookup"><span data-stu-id="4f598-294">To define the order of security header child elements, WS-Security Policy defines the following security header layout modes:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4f598-295">Katı</span><span class="sxs-lookup"><span data-stu-id="4f598-295">Strict</span></span>|<span data-ttu-id="4f598-296">Öğeler, Güvenlik Ilkesi bölümünde açıklanan numaralandırılmış düzen kurallarından sonra, "kullanmadan önce bildir" genel ilkesine göre güvenlik üstbilgisine eklenir.</span><span class="sxs-lookup"><span data-stu-id="4f598-296">Items are added to the security header following the numbered layout rules described in Security Policy section 7.7.1 according to a general principle of "declare before use".</span></span>|  
|<span data-ttu-id="4f598-297">LAX</span><span class="sxs-lookup"><span data-stu-id="4f598-297">Lax</span></span>|<span data-ttu-id="4f598-298">Öğeler, WSS: SOAP Iletisi güvenliğine uyan herhangi bir sırada güvenlik başlığına eklenir.</span><span class="sxs-lookup"><span data-stu-id="4f598-298">Items are added to the security header in any order that conforms to WSS: SOAP Message Security.</span></span>|  
|<span data-ttu-id="4f598-299">Önce Laxtimestamp</span><span class="sxs-lookup"><span data-stu-id="4f598-299">LaxTimestampFirst</span></span>|<span data-ttu-id="4f598-300">Güvenlik üst bilgisindeki ilk öğenin bir WSO: Timestamp olması dışında LAX ile aynı</span><span class="sxs-lookup"><span data-stu-id="4f598-300">Same as Lax except that the first item in the security header must be a wsse:Timestamp</span></span>|  
|<span data-ttu-id="4f598-301">Laxtimestamp son</span><span class="sxs-lookup"><span data-stu-id="4f598-301">LaxTimestampLast</span></span>|<span data-ttu-id="4f598-302">Güvenlik üstbilgisindeki son öğenin bir WSO: Timestamp olması dışında LAX ile aynı</span><span class="sxs-lookup"><span data-stu-id="4f598-302">Same as lax except that the last item in the security header must be a wsse:Timestamp</span></span>|  
  
 <span data-ttu-id="4f598-303">WCF, güvenlik üst bilgisi düzeni için dört modunu destekler.</span><span class="sxs-lookup"><span data-stu-id="4f598-303">WCF supports all four modes for security header layout.</span></span> <span data-ttu-id="4f598-304">Güvenlik üst bilgisi yapısı ve aşağıdaki kimlik doğrulama modları için ileti örnekleri "katı" modunu izler.</span><span class="sxs-lookup"><span data-stu-id="4f598-304">Security header structure and message examples for authentication modes below follow the "Strict" mode.</span></span>  
  
## <a name="2-common-message-security-parameters"></a><span data-ttu-id="4f598-305">2. ortak Ileti güvenlik parametreleri</span><span class="sxs-lookup"><span data-stu-id="4f598-305">2. Common Message Security Parameters</span></span>  

 <span data-ttu-id="4f598-306">Bu bölümde, istemci ve hizmet tarafından değiştirilen iletilerde güvenlik üst bilgi yapısını gösteren örneklerle birlikte her bir kimlik doğrulama modu için örnek ilkeler sağlanır.</span><span class="sxs-lookup"><span data-stu-id="4f598-306">This section provides example policies for each authentication mode along with examples showing security header structure in messages exchanged by client and service.</span></span>  
  
### <a name="61-transport-protection"></a><span data-ttu-id="4f598-307">6,1 taşıma koruması</span><span class="sxs-lookup"><span data-stu-id="4f598-307">6.1 Transport Protection</span></span>  

 <span data-ttu-id="4f598-308">WCF, iletileri korumak için güvenli aktarım kullanan beş kimlik doğrulama modu sağlar; UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport ve SspiNegotiatedOverTransport.</span><span class="sxs-lookup"><span data-stu-id="4f598-308">WCF provides five authentication modes that use secure transport to protect messages; UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport and SspiNegotiatedOverTransport.</span></span>  
  
 <span data-ttu-id="4f598-309">Bu kimlik doğrulama modları, SecurityPolicy ' de açıklanan aktarım bağlaması kullanılarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="4f598-309">These authentication modes are constructed using the transport binding described in SecurityPolicy.</span></span> <span data-ttu-id="4f598-310">UserNameOverTransport kimlik doğrulama modu için UsernameToken imzalı bir destekleme belirtecidir.</span><span class="sxs-lookup"><span data-stu-id="4f598-310">For the UserNameOverTransport authentication mode the UsernameToken is a signed supporting token.</span></span> <span data-ttu-id="4f598-311">Diğer kimlik doğrulama modlarında, belirteç imzalı bir onaylama belirteci olarak görünür.</span><span class="sxs-lookup"><span data-stu-id="4f598-311">For the other authentication modes the token appears as a signed endorsing token.</span></span> <span data-ttu-id="4f598-312">Ek C. 1.2 ve C. 1.3 SecurityPolicy, güvenlik üst bilgisi yerleşimini ayrıntılı olarak anlatmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4f598-312">Appendix C.1.2 and C.1.3 of SecurityPolicy describe the security header layout in detail.</span></span> <span data-ttu-id="4f598-313">Aşağıdaki örnek güvenlik üstbilgileri, belirli bir kimlik doğrulama modu için katı düzeni gösterir.</span><span class="sxs-lookup"><span data-stu-id="4f598-313">The following example security headers show the Strict layout for a given authentication mode.</span></span>  
  
 <span data-ttu-id="4f598-314">Her durumda belirteçlerin "türetilmiş anahtarlar" özelliğinin değeri "false" şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="4f598-314">The value of the "Derived Keys" property for the tokens in all cases is "false".</span></span>  
  
 <span data-ttu-id="4f598-315">Aktarım bağlamasının çeşitli özelliklerinin değerleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="4f598-315">The values of the various properties of the transport binding are as follows:</span></span>  
  
 <span data-ttu-id="4f598-316">Zaman damgası: true</span><span class="sxs-lookup"><span data-stu-id="4f598-316">Timestamp: true</span></span>  
  
 <span data-ttu-id="4f598-317">Güvenlik üst bilgisi düzeni: katı</span><span class="sxs-lookup"><span data-stu-id="4f598-317">Security Header Layout: Strict</span></span>  
  
 <span data-ttu-id="4f598-318">Algoritma paketi: Basic256</span><span class="sxs-lookup"><span data-stu-id="4f598-318">Algorithm Suite: Basic256</span></span>  
  
#### <a name="611-usernameovertransport"></a><span data-ttu-id="4f598-319">6.1.1 UsernameOverTransport</span><span class="sxs-lookup"><span data-stu-id="4f598-319">6.1.1 UsernameOverTransport</span></span>  

 <span data-ttu-id="4f598-320">Bu kimlik doğrulama modu ile istemci, SOAP katmanında, her zaman başlatıcıdan alıcıya gönderilen imzalı bir destekleme belirteci olarak görünen bir Kullanıcı adı belirteci ile kimlik doğrular.</span><span class="sxs-lookup"><span data-stu-id="4f598-320">With this authentication mode, the client authenticates with a Username Token which appears at the SOAP layer as a signed supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="4f598-321">Hizmetin kimliği, aktarım katmanında bir X. 509.440 sertifikası kullanılarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="4f598-321">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="4f598-322">Kullanılan bağlama bir aktarım bağlamadır.</span><span class="sxs-lookup"><span data-stu-id="4f598-322">The binding used is a transport binding.</span></span>  
  
 <span data-ttu-id="4f598-323">İlke</span><span class="sxs-lookup"><span data-stu-id="4f598-323">Policy</span></span>  
  
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
  
 <span data-ttu-id="4f598-324">Güvenlik üst bilgisi düzeni</span><span class="sxs-lookup"><span data-stu-id="4f598-324">Security Header Layout</span></span>  
  
 <span data-ttu-id="4f598-325">İstek</span><span class="sxs-lookup"><span data-stu-id="4f598-325">Request</span></span>  
  
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
  
 <span data-ttu-id="4f598-326">Yanıt</span><span class="sxs-lookup"><span data-stu-id="4f598-326">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="612-certificateovertransport"></a><span data-ttu-id="4f598-327">6.1.2 CertificateOverTransport</span><span class="sxs-lookup"><span data-stu-id="4f598-327">6.1.2 CertificateOverTransport</span></span>  

 <span data-ttu-id="4f598-328">Bu kimlik doğrulama modunda, istemci, her zaman başlatıcıdan alıcıya gönderilen bir onaylama destekleme belirteci olarak SOAP katmanında görünen bir X. 509.440 sertifikası kullanarak kimlik doğrular.</span><span class="sxs-lookup"><span data-stu-id="4f598-328">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as an endorsing supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="4f598-329">Hizmetin kimliği, aktarım katmanında bir X. 509.440 sertifikası kullanılarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="4f598-329">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="4f598-330">Kullanılan bağlama bir aktarım bağlamadır.</span><span class="sxs-lookup"><span data-stu-id="4f598-330">The binding used is a transport binding.</span></span>  
  
 <span data-ttu-id="4f598-331">İlke</span><span class="sxs-lookup"><span data-stu-id="4f598-331">Policy</span></span>  
  
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
  
 <span data-ttu-id="4f598-332">Güvenlik üst bilgisi düzeni</span><span class="sxs-lookup"><span data-stu-id="4f598-332">Security Header Layout</span></span>  
  
 <span data-ttu-id="4f598-333">İstek</span><span class="sxs-lookup"><span data-stu-id="4f598-333">Request</span></span>  
  
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
  
 <span data-ttu-id="4f598-334">Yanıt</span><span class="sxs-lookup"><span data-stu-id="4f598-334">Response</span></span>  
  
```xml  
<o:Security>  
  <u:Timestamp u:Id="_0">  
  ...  
  </u:Timestamp>  
</o:Security>  
```  
  
#### <a name="613-issuedtokenovertransport"></a><span data-ttu-id="4f598-335">6.1.3 IssuedTokenOverTransport</span><span class="sxs-lookup"><span data-stu-id="4f598-335">6.1.3 IssuedTokenOverTransport</span></span>  

 <span data-ttu-id="4f598-336">Bu kimlik doğrulama modunda, istemci hizmette kimlik doğrulaması yapmaz, ancak bunun yerine güvenlik belirteci hizmeti (STS) tarafından verilen bir belirteç ve paylaşılan bir anahtar hakkında bilgi sahibi olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="4f598-336">With this authentication mode the client does not authenticate to the service, as such, but rather presents a token issued by a Security Token Service (STS) and proves knowledge of a shared key.</span></span> <span data-ttu-id="4f598-337">Verilen belirteç, her zaman başlatıcıdan alıcıya gönderilen bir onaylama destekleme belirteci olarak SOAP katmanında görünür.</span><span class="sxs-lookup"><span data-stu-id="4f598-337">The issued token appears at the SOAP layer as an endorsing supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="4f598-338">Hizmetin kimliği, aktarım katmanında bir X. 509.440 sertifikası kullanılarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="4f598-338">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="4f598-339">Bağlama bir aktarım bağlamadır.</span><span class="sxs-lookup"><span data-stu-id="4f598-339">The binding is a transport binding.</span></span>  
  
 <span data-ttu-id="4f598-340">İlke</span><span class="sxs-lookup"><span data-stu-id="4f598-340">Policy</span></span>  
  
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
  
 <span data-ttu-id="4f598-341">Güvenlik üst bilgisi düzeni</span><span class="sxs-lookup"><span data-stu-id="4f598-341">Security Header Layout</span></span>  
  
 <span data-ttu-id="4f598-342">İstek</span><span class="sxs-lookup"><span data-stu-id="4f598-342">Request</span></span>  
  
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
  
 <span data-ttu-id="4f598-343">Yanıt</span><span class="sxs-lookup"><span data-stu-id="4f598-343">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="614-kerberosovertransport"></a><span data-ttu-id="4f598-344">6.1.4 KerberosOverTransport</span><span class="sxs-lookup"><span data-stu-id="4f598-344">6.1.4 KerberosOverTransport</span></span>  

 <span data-ttu-id="4f598-345">Bu kimlik doğrulama modunda istemci Kerberos bileti kullanarak hizmeti doğrular.</span><span class="sxs-lookup"><span data-stu-id="4f598-345">With this authentication mode the client authenticates to the service using a Kerberos ticket.</span></span> <span data-ttu-id="4f598-346">Kerberos belirteci, SOAP katmanında bir onaylama destekleme belirteci olarak görünür.</span><span class="sxs-lookup"><span data-stu-id="4f598-346">The Kerberos token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="4f598-347">Hizmetin kimliği, aktarım katmanında bir X. 509.440 sertifikası kullanılarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="4f598-347">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="4f598-348">Bağlama bir aktarım bağlamadır.</span><span class="sxs-lookup"><span data-stu-id="4f598-348">The binding is a transport binding.</span></span>  
  
 <span data-ttu-id="4f598-349">İlke</span><span class="sxs-lookup"><span data-stu-id="4f598-349">Policy</span></span>  
  
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
  
 <span data-ttu-id="4f598-350">Güvenlik üst bilgisi düzeni</span><span class="sxs-lookup"><span data-stu-id="4f598-350">Security Header Layout</span></span>  
  
 <span data-ttu-id="4f598-351">İstek</span><span class="sxs-lookup"><span data-stu-id="4f598-351">Request</span></span>  
  
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
  
 <span data-ttu-id="4f598-352">Yanıt</span><span class="sxs-lookup"><span data-stu-id="4f598-352">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="615-sspinegotiatedovertransport"></a><span data-ttu-id="4f598-353">6.1.5 SspiNegotiatedOverTransport</span><span class="sxs-lookup"><span data-stu-id="4f598-353">6.1.5 SspiNegotiatedOverTransport</span></span>  

 <span data-ttu-id="4f598-354">Bu modda istemci ve sunucu kimlik doğrulamasını gerçekleştirmek için bir anlaşma protokolü kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4f598-354">With this mode a negotiation protocol is used to perform client and server authentication.</span></span> <span data-ttu-id="4f598-355">Mümkünse, Kerberos kullanılır, aksi takdirde NTLM kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4f598-355">Kerberos is used if possible, otherwise NTLM.</span></span> <span data-ttu-id="4f598-356">Elde edilen SCT, her zaman başlatıcıdan alıcıya gönderilen bir onaylama destekleme belirteci olarak SOAP katmanında görünür.</span><span class="sxs-lookup"><span data-stu-id="4f598-356">The resulting SCT appears at the SOAP layer as an endorsing supporting token that is always sent from initiator to recipient.</span></span> <span data-ttu-id="4f598-357">Ayrıca hizmet, aktarım katmanında bir X. 509.440 sertifikası tarafından da doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="4f598-357">The service is additionally authenticated at the transport layer by an X.509 certificate.</span></span> <span data-ttu-id="4f598-358">Kullanılan bağlama bir aktarım bağlamadır.</span><span class="sxs-lookup"><span data-stu-id="4f598-358">The binding used is a transport binding.</span></span> <span data-ttu-id="4f598-359">"SPNEGO" (anlaşma), WCF 'nin WS-Trust ile SSPI ikili anlaşma protokolünü nasıl kullandığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="4f598-359">"SPNEGO" (negotiation) describes how WCF uses SSPI binary negotiation protocol with WS-Trust.</span></span> <span data-ttu-id="4f598-360">Bu bölümdeki güvenlik üst bilgisi örnekleri, SPNEGO el sıkışma aracılığıyla SCT oluşturulduktan sonra verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="4f598-360">Security header examples in this section are after the SCT has been established through the SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="4f598-361">İlke</span><span class="sxs-lookup"><span data-stu-id="4f598-361">Policy</span></span>  
  
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
  
### <a name="security-header-examples"></a><span data-ttu-id="4f598-362">Güvenlik üst bilgisi örnekleri</span><span class="sxs-lookup"><span data-stu-id="4f598-362">Security Header Examples</span></span>  

 <span data-ttu-id="4f598-363">Güvenlik bağlamı belirteci WS-Trust Ikili anlaşma kullanılarak SPNEGO Handshake aracılığıyla kurulduktan sonra, uygulama iletilerinde aşağıdaki yapıyla güvenlik üst bilgileri bulunur.</span><span class="sxs-lookup"><span data-stu-id="4f598-363">Once the Security Context Token is established through SPNEGO handshake using WS-Trust Binary Negotiation, the application messages have security headers with the following structure.</span></span>  
  
 <span data-ttu-id="4f598-364">İstek</span><span class="sxs-lookup"><span data-stu-id="4f598-364">Request</span></span>  
  
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
  
 <span data-ttu-id="4f598-365">Yanıt</span><span class="sxs-lookup"><span data-stu-id="4f598-365">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
### <a name="62-using-x509-certificates-for-service-authentication"></a><span data-ttu-id="4f598-366">Hizmet kimlik doğrulaması için X. 509.440 sertifikalarını kullanma 6,2</span><span class="sxs-lookup"><span data-stu-id="4f598-366">6.2 Using X.509 Certificates for Service Authentication</span></span>  

 <span data-ttu-id="4f598-367">Bu bölümde şu kimlik doğrulama modları açıklanmaktadır: Mulualcertificate WSS 1.0, karşılıklı CertificateDuplex, Mulualcertificate WSS 1.1, AnonymousForCertificate, UserNameForCertificate ve IssuedTokenForCertificate.</span><span class="sxs-lookup"><span data-stu-id="4f598-367">This section describes the following authentication modes: MutualCertificate WSS1.0, Mutual CertificateDuplex, MutualCertificate WSS1.1, AnonymousForCertificate, UserNameForCertificate and IssuedTokenForCertificate.</span></span>  
  
#### <a name="621-mutualcertificate-wss10"></a><span data-ttu-id="4f598-368">6.2.1 Mulualcertificate WSS 1.0</span><span class="sxs-lookup"><span data-stu-id="4f598-368">6.2.1 MutualCertificate WSS1.0</span></span>  

 <span data-ttu-id="4f598-369">Bu kimlik doğrulama modunda istemci, başlatıcı belirteci olarak SOAP katmanında görünen bir X. 509.440 sertifikası kullanarak kimlik doğrular.</span><span class="sxs-lookup"><span data-stu-id="4f598-369">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as the initiator token.</span></span> <span data-ttu-id="4f598-370">Ayrıca, hizmet bir X. 509.440 sertifikası kullanılarak doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="4f598-370">The service is also authenticated using an X.509 certificate.</span></span>  
  
 <span data-ttu-id="4f598-371">Kullanılan bağlama, aşağıdaki özellik değerleriyle asimetrik bir bağlamadır:</span><span class="sxs-lookup"><span data-stu-id="4f598-371">The binding used is an asymmetric binding with the following property values:</span></span>  
  
 <span data-ttu-id="4f598-372">Başlatıcı belirteci: ekleme modu. ../IncludeToken/AlwaysToRecipient olarak ayarlanan istemcinin X. 509.440 sertifikası</span><span class="sxs-lookup"><span data-stu-id="4f598-372">Initiator Token: the client’s X.509 certificate, with inclusion mode set to …/IncludeToken/AlwaysToRecipient</span></span>  
  
 <span data-ttu-id="4f598-373">Alıcı belirteci: sunucu X. 509.440 sertifikası, dahil etme modu ayarlandı. ../Includetoken/No</span><span class="sxs-lookup"><span data-stu-id="4f598-373">Recipient Token: Server’s X.509 Certificate, with inclusion mode is set …/IncludeToken/Never</span></span>  
  
 <span data-ttu-id="4f598-374">Belirteç koruması: false</span><span class="sxs-lookup"><span data-stu-id="4f598-374">Token Protection: False</span></span>  
  
 <span data-ttu-id="4f598-375">Tüm başlık ve gövde Imzaları: doğru</span><span class="sxs-lookup"><span data-stu-id="4f598-375">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="4f598-376">Koruma sırası: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="4f598-376">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="4f598-377">Imzayı şifreleyin: doğru</span><span class="sxs-lookup"><span data-stu-id="4f598-377">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="4f598-378">İlke</span><span class="sxs-lookup"><span data-stu-id="4f598-378">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="4f598-379">Güvenlik üst bilgisi örnekleri: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="4f598-379">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="4f598-380">İstek</span><span class="sxs-lookup"><span data-stu-id="4f598-380">Request</span></span>  
  
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
  
 <span data-ttu-id="4f598-381">Yanıt</span><span class="sxs-lookup"><span data-stu-id="4f598-381">Response</span></span>  
  
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
  
 <span data-ttu-id="4f598-382">Güvenlik üst bilgisi örnekleri: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="4f598-382">Security Header Examples: EncryptBeforeSign</span></span>  
  
 <span data-ttu-id="4f598-383">İstek</span><span class="sxs-lookup"><span data-stu-id="4f598-383">Request</span></span>  
  
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
  
 <span data-ttu-id="4f598-384">Yanıt</span><span class="sxs-lookup"><span data-stu-id="4f598-384">Response</span></span>  
  
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
  
#### <a name="622-mutualcertificateduplex"></a><span data-ttu-id="4f598-385">6.2.2 Mulualcertificateduplex</span><span class="sxs-lookup"><span data-stu-id="4f598-385">6.2.2 MutualCertificateDuplex</span></span>  

 <span data-ttu-id="4f598-386">Bu kimlik doğrulama modunda istemci, başlatıcı belirteci olarak SOAP katmanında görünen bir X. 509.440 sertifikası kullanarak kimlik doğrular.</span><span class="sxs-lookup"><span data-stu-id="4f598-386">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as the initiator token.</span></span> <span data-ttu-id="4f598-387">Ayrıca, hizmet bir X. 509.440 sertifikası kullanılarak doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="4f598-387">The service is also authenticated using an X.509 certificate.</span></span>  
  
 <span data-ttu-id="4f598-388">Kullanılan bağlama, aşağıdaki özellik değerleriyle asimetrik bir bağlamadır:</span><span class="sxs-lookup"><span data-stu-id="4f598-388">The binding used is an asymmetric binding with the following property values:</span></span>  
  
 <span data-ttu-id="4f598-389">Başlatıcı belirteci: Istemcinin x509 sertifikası, ekleme modu. ../IncludeToken/AlwaysToRecipient olarak ayarlandı</span><span class="sxs-lookup"><span data-stu-id="4f598-389">Initiator Token: Client’s X509 Certificate, inclusion mode is set to …/IncludeToken/AlwaysToRecipient</span></span>  
  
 <span data-ttu-id="4f598-390">Alıcı belirteci: sunucunun x509 sertifikası, dahil etme modu. ../ıncludetoken/AlwaysToInitiator olarak ayarlandı</span><span class="sxs-lookup"><span data-stu-id="4f598-390">Recipient Token: Server’s X509 Certificate, inclusion mode is set to …/IncludeToken/AlwaysToInitiator</span></span>  
  
 <span data-ttu-id="4f598-391">Belirteç koruması: false</span><span class="sxs-lookup"><span data-stu-id="4f598-391">Token Protection: False</span></span>  
  
 <span data-ttu-id="4f598-392">Tüm başlık ve gövde Imzaları: doğru</span><span class="sxs-lookup"><span data-stu-id="4f598-392">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="4f598-393">Koruma sırası: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="4f598-393">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="4f598-394">Imzayı şifreleyin: doğru</span><span class="sxs-lookup"><span data-stu-id="4f598-394">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="4f598-395">İlke</span><span class="sxs-lookup"><span data-stu-id="4f598-395">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="4f598-396">Güvenlik üst bilgisi örnekleri: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="4f598-396">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="4f598-397">İstek ve yanıt</span><span class="sxs-lookup"><span data-stu-id="4f598-397">Request and Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="4f598-398">Güvenlik üst bilgisi örnekleri: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="4f598-398">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="4f598-399">İstek ve yanıt</span><span class="sxs-lookup"><span data-stu-id="4f598-399">Request and Response</span></span>  
  
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
  
#### <a name="623-using-symmetricbinding-with-x509-service-authentication"></a><span data-ttu-id="4f598-400">X. 509.440 hizmeti kimlik doğrulamasıyla SymmetricBinding kullanarak 6.2.3</span><span class="sxs-lookup"><span data-stu-id="4f598-400">6.2.3 Using SymmetricBinding with X.509 Service Authentication</span></span>  

 <span data-ttu-id="4f598-401">"WSS10", x509 belirteçleri olan senaryolar için sınırlı destek sağlamıştır.</span><span class="sxs-lookup"><span data-stu-id="4f598-401">"WSS10" provided limited support for scenarios with X509 tokens.</span></span> <span data-ttu-id="4f598-402">Örneğin, yalnızca Service x509 belirtecini kullanan iletiler için imza ve şifreleme koruması sağlanması mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="4f598-402">For example, there was no way to provide signature and encryption protection for messages using only service X509 token.</span></span> <span data-ttu-id="4f598-403">"WSS11", EncryptedKey öğesinin kullanımını simetrik bir belirteç olarak getirdi.</span><span class="sxs-lookup"><span data-stu-id="4f598-403">"WSS11" introduced the usage of EncryptedKey as a symmetric token.</span></span> <span data-ttu-id="4f598-404">Artık hem istek hem de yanıt iletileri koruması için hizmetin X. 509.440 sertifikası için şifrelenmiş bir geçici anahtar kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4f598-404">Now a temporary key encrypted for the service's X.509 certificate could be used for both request and response messages protection.</span></span> <span data-ttu-id="4f598-405">Aşağıdaki 6,4 bölümünde açıklanan kimlik doğrulama modları bu kalıbı kullanır.</span><span class="sxs-lookup"><span data-stu-id="4f598-405">The authentication modes described in the section 6.4 below use this pattern.</span></span>  
  
 <span data-ttu-id="4f598-406">WS-SecurityPolicy, koruma belirteci olarak Service x509 belirteci ile SymmetricBinding kullanarak bu kalıbı açıklar.</span><span class="sxs-lookup"><span data-stu-id="4f598-406">WS-SecurityPolicy describes this pattern using SymmetricBinding with Service X509 token as the protection token.</span></span>  
  
 <span data-ttu-id="4f598-407">Kimlik doğrulama modları AnonymousForCertificate, UsernameForCertificate, Mulualcertificate WSS11 ve IssuedTokenForCertificate All, aşağıdaki özellik değerleriyle benzer bir SP: SymmetricBinding örneği kullanır:</span><span class="sxs-lookup"><span data-stu-id="4f598-407">Authentication modes AnonymousForCertificate, UsernameForCertificate, MutualCertificate WSS11 and IssuedTokenForCertificate all use a similar instance of sp:SymmetricBinding with the following property values:</span></span>  
  
 <span data-ttu-id="4f598-408">Koruma belirteci: sunucunun x509 sertifikası, içerme modu olarak ayarlandı. ../Includetoken/hiçbir</span><span class="sxs-lookup"><span data-stu-id="4f598-408">Protection Token: Server’s X509 Certificate, inclusion mode is set to .../IncludeToken/Never</span></span>  
<span data-ttu-id="4f598-409">Belirteç koruması: false</span><span class="sxs-lookup"><span data-stu-id="4f598-409">Token Protection: False</span></span>  
  
 <span data-ttu-id="4f598-410">Tüm başlık ve gövde Imzaları: doğru</span><span class="sxs-lookup"><span data-stu-id="4f598-410">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="4f598-411">Koruma sırası: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="4f598-411">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="4f598-412">Imzayı şifreleyin: doğru</span><span class="sxs-lookup"><span data-stu-id="4f598-412">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="4f598-413">Yukarıdaki kimlik doğrulama modları yalnızca kullandıkları destekleyici belirteçlere göre farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="4f598-413">The above authentication modes only differ by the supporting tokens they use.</span></span> <span data-ttu-id="4f598-414">AnonymousForCertificate 'ın herhangi bir destekleme belirteci yoktur; çoklu Uıcertificate WSS 1,1 'nin istemcinin x509 sertifikası, destekleme belirteçleri onaylama olarak, UserNameForCertificate imzalı bir destekleme belirteci olarak bir Kullanıcı adı belirtecine sahiptir ve IssuedTokenForCertificate, verilen belirtece bir onaylama destekleme belirteci olarak sahiptir.</span><span class="sxs-lookup"><span data-stu-id="4f598-414">AnonymousForCertificate does not have any supporting tokens, MutualCertificate WSS 1.1 has the client’s X509 certificate as an endorsing supporting tokens, UserNameForCertificate has a UserName Token as a signed supporting token and IssuedTokenForCertificate has the issued token as an endorsing supporting token.</span></span>  
  
 <span data-ttu-id="4f598-415">İlke</span><span class="sxs-lookup"><span data-stu-id="4f598-415">Policy</span></span>  
  
 <span data-ttu-id="4f598-416">Simetrik bağlama</span><span class="sxs-lookup"><span data-stu-id="4f598-416">Symmetric Binding</span></span>  
  
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
  
#### <a name="624-anonymousforcertificate"></a><span data-ttu-id="4f598-417">6.2.4 AnonymousForCertificate</span><span class="sxs-lookup"><span data-stu-id="4f598-417">6.2.4 AnonymousForCertificate</span></span>  

 <span data-ttu-id="4f598-418">Bu kimlik doğrulama modunda, istemci anonimdir ve hizmetin kimliği bir X. 509.440 sertifikası kullanılarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="4f598-418">With this authentication mode the client is anonymous and the service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="4f598-419">Kullanılan bağlama, 6.4.2 içinde açıklandığı gibi simetrik bağlamanın bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="4f598-419">The binding used is an instance of symmetric binding as described in 6.4.2.</span></span>  
  
 <span data-ttu-id="4f598-420">İlke</span><span class="sxs-lookup"><span data-stu-id="4f598-420">Policy</span></span>  
  
 <span data-ttu-id="4f598-421">Bağlama ayrıntıları için yukarıdaki 6.2.3 içindeki "Ilke" başlığına bakın</span><span class="sxs-lookup"><span data-stu-id="4f598-421">See "Policy" in 6.2.3 above for binding details</span></span>  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="4f598-422">Güvenlik üst bilgisi örnekleri: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="4f598-422">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="4f598-423">İstek</span><span class="sxs-lookup"><span data-stu-id="4f598-423">Request</span></span>  
  
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
  
 <span data-ttu-id="4f598-424">Yanıt</span><span class="sxs-lookup"><span data-stu-id="4f598-424">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="4f598-425">Güvenlik üst bilgisi örnekleri: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="4f598-425">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="4f598-426">İstek</span><span class="sxs-lookup"><span data-stu-id="4f598-426">Request</span></span>  
  
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
  
 <span data-ttu-id="4f598-427">Yanıt</span><span class="sxs-lookup"><span data-stu-id="4f598-427">Response</span></span>  
  
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
  
#### <a name="625-usernameforcertificate"></a><span data-ttu-id="4f598-428">6.2.5 UserNameForCertificate</span><span class="sxs-lookup"><span data-stu-id="4f598-428">6.2.5 UserNameForCertificate</span></span>  

 <span data-ttu-id="4f598-429">Bu kimlik doğrulama modunda istemci, SOAP katmanında imzalı destekleyici belirteç olarak görünen bir Kullanıcı adı belirteci kullanarak hizmette kimlik doğrulaması yapar.</span><span class="sxs-lookup"><span data-stu-id="4f598-429">With this authentication mode the client authenticates to the service using a Username Token which appears at the SOAP layer as a signed supporting token.</span></span> <span data-ttu-id="4f598-430">Hizmet, bir X. 509.440 sertifikası kullanarak istemcinin kimliğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="4f598-430">The service authenticates to the client using an X.509 certificate.</span></span> <span data-ttu-id="4f598-431">Kullanılan bağlama, koruma belirtecinin istemci tarafından oluşturulan ve hizmetin ortak anahtarıyla şifrelenen bir anahtar olduğu simetrik bir bağlamadır.</span><span class="sxs-lookup"><span data-stu-id="4f598-431">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="4f598-432">İlke</span><span class="sxs-lookup"><span data-stu-id="4f598-432">Policy</span></span>  
  
 <span data-ttu-id="4f598-433">Bağlama ayrıntıları için yukarıdaki 6.2.3 içindeki "Ilke" başlığına bakın</span><span class="sxs-lookup"><span data-stu-id="4f598-433">See "Policy" in 6.2.3 above for binding details</span></span>  
  
 <span data-ttu-id="4f598-434">İmzalı destekleme belirteci</span><span class="sxs-lookup"><span data-stu-id="4f598-434">Signed Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="4f598-435">Güvenlik üst bilgisi örnekleri: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="4f598-435">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="4f598-436">İstek</span><span class="sxs-lookup"><span data-stu-id="4f598-436">Request</span></span>  
  
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
  
 <span data-ttu-id="4f598-437">Yanıt</span><span class="sxs-lookup"><span data-stu-id="4f598-437">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="4f598-438">Güvenlik üst bilgisi örnekleri: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="4f598-438">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="4f598-439">İstek</span><span class="sxs-lookup"><span data-stu-id="4f598-439">Request</span></span>  
  
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
  
 <span data-ttu-id="4f598-440">Yanıt</span><span class="sxs-lookup"><span data-stu-id="4f598-440">Response</span></span>  
  
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
  
#### <a name="626-mutualcertificate-wss-11"></a><span data-ttu-id="4f598-441">6.2.6 Mulualcertificate (WSS 1,1)</span><span class="sxs-lookup"><span data-stu-id="4f598-441">6.2.6 MutualCertificate (WSS 1.1)</span></span>  

 <span data-ttu-id="4f598-442">Bu kimlik doğrulama modunda istemci, SOAP katmanında bir destekleme desteği belirteci olarak görünen bir X. 509.440 sertifikası kullanarak kimlik doğrular.</span><span class="sxs-lookup"><span data-stu-id="4f598-442">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="4f598-443">Ayrıca, hizmet bir X. 509.440 sertifikası kullanılarak doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="4f598-443">The service is also authenticated using an X.509 certificate.</span></span> <span data-ttu-id="4f598-444">Kullanılan bağlama, koruma belirtecinin istemci tarafından oluşturulan ve hizmetin ortak anahtarıyla şifrelenen bir anahtar olduğu simetrik bir bağlamadır.</span><span class="sxs-lookup"><span data-stu-id="4f598-444">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="4f598-445">İlke</span><span class="sxs-lookup"><span data-stu-id="4f598-445">Policy</span></span>  
  
 <span data-ttu-id="4f598-446">Bağlama ayrıntıları için bkz. 6.2.3 içinde Ilke</span><span class="sxs-lookup"><span data-stu-id="4f598-446">See Policy in 6.2.3 for binding details</span></span>  
  
 <span data-ttu-id="4f598-447">Destekleyici belirteç onaylama</span><span class="sxs-lookup"><span data-stu-id="4f598-447">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="4f598-448">Güvenlik üst bilgisi örnekleri: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="4f598-448">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="4f598-449">İstek</span><span class="sxs-lookup"><span data-stu-id="4f598-449">Request</span></span>  
  
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
  
 <span data-ttu-id="4f598-450">Yanıt</span><span class="sxs-lookup"><span data-stu-id="4f598-450">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="4f598-451">Güvenlik üst bilgisi örnekleri: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="4f598-451">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="4f598-452">İstek</span><span class="sxs-lookup"><span data-stu-id="4f598-452">Request</span></span>  
  
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
  
 <span data-ttu-id="4f598-453">Yanıt</span><span class="sxs-lookup"><span data-stu-id="4f598-453">Response</span></span>  
  
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
  
#### <a name="627-issuedtokenforcertificate"></a><span data-ttu-id="4f598-454">6.2.7 IssuedTokenForCertificate</span><span class="sxs-lookup"><span data-stu-id="4f598-454">6.2.7 IssuedTokenForCertificate</span></span>  

 <span data-ttu-id="4f598-455">Bu kimlik doğrulama modunda istemci, bu şekilde hizmette kimlik doğrulaması yapmaz, ancak bunun yerine STS tarafından verilen bir belirteç ve paylaşılan anahtar hakkında bilgi sahibi olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="4f598-455">With this authentication mode the client does not authenticate to the service, as such, but instead presents a token issued by a STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="4f598-456">Verilen belirteç, SOAP katmanında bir onaylama destekleme belirteci olarak görünür.</span><span class="sxs-lookup"><span data-stu-id="4f598-456">The issued token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="4f598-457">Hizmet, bir X. 509.440 sertifikası kullanarak istemcinin kimliğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="4f598-457">The service authenticates to the client using an X.509 certificate.</span></span> <span data-ttu-id="4f598-458">Kullanılan bağlama, koruma belirtecinin istemci tarafından oluşturulan ve hizmetin ortak anahtarıyla şifrelenen bir anahtar olduğu simetrik bir bağlamadır.</span><span class="sxs-lookup"><span data-stu-id="4f598-458">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="4f598-459">İlke</span><span class="sxs-lookup"><span data-stu-id="4f598-459">Policy</span></span>  
  
 <span data-ttu-id="4f598-460">Bağlama ayrıntıları için yukarıdaki 6.2.3 içindeki Ilkeye bakın</span><span class="sxs-lookup"><span data-stu-id="4f598-460">See Policy in 6.2.3 above for binding details</span></span>  
  
 <span data-ttu-id="4f598-461">Destekleyici belirteç onaylama</span><span class="sxs-lookup"><span data-stu-id="4f598-461">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="4f598-462">Güvenlik üst bilgisi örnekleri: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="4f598-462">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="4f598-463">İstek</span><span class="sxs-lookup"><span data-stu-id="4f598-463">Request</span></span>  
  
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
  
 <span data-ttu-id="4f598-464">Yanıt</span><span class="sxs-lookup"><span data-stu-id="4f598-464">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="4f598-465">Güvenlik üst bilgisi örnekleri: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="4f598-465">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="4f598-466">İstek</span><span class="sxs-lookup"><span data-stu-id="4f598-466">Request</span></span>  
  
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
  
 <span data-ttu-id="4f598-467">Yanıt</span><span class="sxs-lookup"><span data-stu-id="4f598-467">Response</span></span>  
  
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
  
## <a name="63-kerberos"></a><span data-ttu-id="4f598-468">6,3 Kerberos</span><span class="sxs-lookup"><span data-stu-id="4f598-468">6.3 Kerberos</span></span>  

 <span data-ttu-id="4f598-469">Bu kimlik doğrulama modunda istemci Kerberos bileti kullanarak hizmeti doğrular.</span><span class="sxs-lookup"><span data-stu-id="4f598-469">With this authentication mode the client authenticates to the service using a Kerberos ticket.</span></span> <span data-ttu-id="4f598-470">Aynı bilet aynı zamanda sunucu kimlik doğrulaması da sağlar.</span><span class="sxs-lookup"><span data-stu-id="4f598-470">That same ticket also provides server authentication.</span></span> <span data-ttu-id="4f598-471">Kullanılan bağlama, aşağıdaki özelliklerle simetrik bir bağlamadır;</span><span class="sxs-lookup"><span data-stu-id="4f598-471">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="4f598-472">Koruma belirteci: Kerberos bileti, ekleme modu. ../IncludeToken/Once olarak ayarlandı</span><span class="sxs-lookup"><span data-stu-id="4f598-472">Protection Token: Kerberos Ticket, inclusion mode is set to .../IncludeToken/Once</span></span>  
<span data-ttu-id="4f598-473">Belirteç koruması: false</span><span class="sxs-lookup"><span data-stu-id="4f598-473">Token Protection: False</span></span>  
  
 <span data-ttu-id="4f598-474">Tüm başlık ve gövde Imzaları: doğru</span><span class="sxs-lookup"><span data-stu-id="4f598-474">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="4f598-475">Koruma sırası: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="4f598-475">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="4f598-476">Imzayı şifreleyin: doğru</span><span class="sxs-lookup"><span data-stu-id="4f598-476">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="4f598-477">İlke</span><span class="sxs-lookup"><span data-stu-id="4f598-477">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="4f598-478">Güvenlik üst bilgisi örnekleri: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="4f598-478">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="4f598-479">İstek</span><span class="sxs-lookup"><span data-stu-id="4f598-479">Request</span></span>  
  
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
  
 <span data-ttu-id="4f598-480">Yanıt</span><span class="sxs-lookup"><span data-stu-id="4f598-480">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="4f598-481">Güvenlik üst bilgisi örnekleri: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="4f598-481">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="4f598-482">İstek</span><span class="sxs-lookup"><span data-stu-id="4f598-482">Request</span></span>  
  
```xml  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
 <span data-ttu-id="4f598-483">Yanıt</span><span class="sxs-lookup"><span data-stu-id="4f598-483">Response</span></span>  
  
```xml  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
#### <a name="64-issuedtoken"></a><span data-ttu-id="4f598-484">6,4 IssuedToken</span><span class="sxs-lookup"><span data-stu-id="4f598-484">6.4 IssuedToken</span></span>  

 <span data-ttu-id="4f598-485">Bu kimlik doğrulama modunda, istemci hizmette kimlik doğrulaması yapmaz, bunun yerine istemci, STS tarafından verilen bir belirteç ve paylaşılan bir anahtar hakkında bilgi sahibi olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="4f598-485">With this authentication mode the client does not authenticate to the service, as such, rather the client presents a token issued by an STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="4f598-486">Bu hizmet, istemci tarafından kimlik doğrulaması değil, bu nedenle, STS, paylaşılan anahtarı yalnızca hizmetin şifresini çözebilmesini sağlayan, verilen belirtecin bir parçası olarak şifreler.</span><span class="sxs-lookup"><span data-stu-id="4f598-486">The service is not authenticated to the client, as such, instead the STS encrypts the shared key as part of the issued token such that only the service can decrypt the key.</span></span> <span data-ttu-id="4f598-487">Kullanılan bağlama, aşağıdaki özelliklerle simetrik bağlama olarak verilmiştir;</span><span class="sxs-lookup"><span data-stu-id="4f598-487">The binding used is as symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="4f598-488">Koruma belirteci: verilen belirteç, ekleme modu. ../IncludeToken/AlwaysToRecipient olarak ayarlandı</span><span class="sxs-lookup"><span data-stu-id="4f598-488">Protection Token: Issued Token, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
<span data-ttu-id="4f598-489">Belirteç koruması: false</span><span class="sxs-lookup"><span data-stu-id="4f598-489">Token Protection: False</span></span>  
  
 <span data-ttu-id="4f598-490">Tüm başlık ve gövde Imzaları: doğru</span><span class="sxs-lookup"><span data-stu-id="4f598-490">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="4f598-491">Koruma sırası: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="4f598-491">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="4f598-492">Imzayı şifreleyin: doğru</span><span class="sxs-lookup"><span data-stu-id="4f598-492">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="4f598-493">İlke</span><span class="sxs-lookup"><span data-stu-id="4f598-493">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="4f598-494">Güvenlik üst bilgisi örnekleri: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="4f598-494">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="4f598-495">İstek</span><span class="sxs-lookup"><span data-stu-id="4f598-495">Request</span></span>  
  
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
  
 <span data-ttu-id="4f598-496">Yanıt</span><span class="sxs-lookup"><span data-stu-id="4f598-496">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="4f598-497">Güvenlik üst bilgisi örnekleri: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="4f598-497">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="4f598-498">İstek</span><span class="sxs-lookup"><span data-stu-id="4f598-498">Request</span></span>  
  
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
  
 <span data-ttu-id="4f598-499">Yanıt</span><span class="sxs-lookup"><span data-stu-id="4f598-499">Response</span></span>  
  
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
  
### <a name="65-using-sslnegotiated-for-service-authentication"></a><span data-ttu-id="4f598-500">Hizmet kimlik doğrulaması için Sslanlaşmalı kullanma 6,5</span><span class="sxs-lookup"><span data-stu-id="4f598-500">6.5 Using SslNegotiated for Service Authentication</span></span>  

 <span data-ttu-id="4f598-501">Bu bölümde, WS-Trust (WS-T) RST/RSTR iletileri üzerinden TLS protokolünü yürüterek, anahtar değerine uygulanan WS-SecureConversation (WS-SC) başına bir güvenlik bağlamı belirteci olan koruma belirtecine sahip bir simetrik bağlama kullanan bir kimlik doğrulama modu grubu açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4f598-501">This section describes a group of authentication modes that use a symmetric binding with the protection token being a Security Context Token per WS-SecureConversation (WS-SC) whose key value is negotiated by executing the TLS protocol over WS-Trust (WS-T) RST/RSTR messages.</span></span> <span data-ttu-id="4f598-502">WS-Trust kullanarak TLS el sıkışma uygulamasının ayrıntıları TLSNEGO ' de açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4f598-502">Details of the TLS handshake implementation using WS-Trust are described in TLSNEGO.</span></span> <span data-ttu-id="4f598-503">Burada ileti örneklerinde, ilişkili bir güvenlik bağlamı olan SCT 'nin bir el sıkışma aracılığıyla zaten kurulduğu varsayılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4f598-503">Here in the message examples we will assume that SCT with an associated security context is already established through a handshake.</span></span>  
  
 <span data-ttu-id="4f598-504">Kullanılan bağlama, aşağıdaki özelliklerle simetrik bir bağlamadır;</span><span class="sxs-lookup"><span data-stu-id="4f598-504">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="4f598-505">Koruma belirteci: SslContextToken, ekleme modu olarak ayarlandı. ../Includetoken/hiçbir</span><span class="sxs-lookup"><span data-stu-id="4f598-505">Protection Token: SslContextToken, inclusion mode is set to .../IncludeToken/Never</span></span>  
<span data-ttu-id="4f598-506">Belirteç koruması: false</span><span class="sxs-lookup"><span data-stu-id="4f598-506">Token Protection: False</span></span>  
  
 <span data-ttu-id="4f598-507">Tüm başlık ve gövde Imzaları: doğru</span><span class="sxs-lookup"><span data-stu-id="4f598-507">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="4f598-508">Koruma sırası: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="4f598-508">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="4f598-509">Imzayı şifreleyin: doğru</span><span class="sxs-lookup"><span data-stu-id="4f598-509">Encrypt Signature: True</span></span>  
  
#### <a name="651-policy-for-sslnegotiated-service-authentication"></a><span data-ttu-id="4f598-510">Sslanlaşmalı hizmet kimlik doğrulaması için 6.5.1 ilkesi</span><span class="sxs-lookup"><span data-stu-id="4f598-510">6.5.1 Policy for SslNegotiated service authentication</span></span>  

 <span data-ttu-id="4f598-511">Bu bölümdeki tüm kimlik doğrulama modları için ilke benzerdir ve yalnızca belirli imzalı destekleyici veya onaylama belirteçlerine göre farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="4f598-511">Policy for all authentication modes in this section are similar and differ only by specific signed supporting or endorsing tokens used.</span></span>  
  
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
  
#### <a name="652-anonymousforsslnegotiated"></a><span data-ttu-id="4f598-512">6.5.2 Anonymousforsslanlaşmalı</span><span class="sxs-lookup"><span data-stu-id="4f598-512">6.5.2 AnonymousForSslNegotiated</span></span>  

 <span data-ttu-id="4f598-513">Bu kimlik doğrulama modunda, istemci anonimdir ve hizmetin kimliği bir X. 509.440 sertifikası kullanılarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="4f598-513">With this authentication mode the client is anonymous and the service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="4f598-514">Kullanılan bağlama, yukarıdaki 6.5.1 açıklanan simetrik bağlamanın bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="4f598-514">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="4f598-515">İlke</span><span class="sxs-lookup"><span data-stu-id="4f598-515">Policy</span></span>  
  
 <span data-ttu-id="4f598-516">Bağlama ayrıntıları için yukarıdaki 6.5.1 içindeki Ilkeye bakın.</span><span class="sxs-lookup"><span data-stu-id="4f598-516">See Policy in 6.5.1 above for binding details.</span></span>  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="4f598-517">Güvenlik üst bilgisi örnekleri: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="4f598-517">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="4f598-518">İstek</span><span class="sxs-lookup"><span data-stu-id="4f598-518">Request</span></span>  
  
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
  
 <span data-ttu-id="4f598-519">Yanıt</span><span class="sxs-lookup"><span data-stu-id="4f598-519">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="4f598-520">Güvenlik üst bilgisi örnekleri: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="4f598-520">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="4f598-521">İstek</span><span class="sxs-lookup"><span data-stu-id="4f598-521">Request</span></span>  
  
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
  
 <span data-ttu-id="4f598-522">Yanıt</span><span class="sxs-lookup"><span data-stu-id="4f598-522">Response</span></span>  
  
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
  
#### <a name="653-usernameforsslnegotiated"></a><span data-ttu-id="4f598-523">6.5.3 Usernameforsslanlaşmalı</span><span class="sxs-lookup"><span data-stu-id="4f598-523">6.5.3 UserNameForSslNegotiated</span></span>  

 <span data-ttu-id="4f598-524">Bu kimlik doğrulama modunda istemci, SOAP katmanında imzalı destekleyici belirteç olarak görünen bir Kullanıcı adı belirteci kullanarak kimlik doğrular.</span><span class="sxs-lookup"><span data-stu-id="4f598-524">With this authentication mode the client is authenticates using a Username Token which appears at the SOAP layer as a signed supporting token.</span></span> <span data-ttu-id="4f598-525">Hizmetin kimliği bir X. 509.440 sertifikası kullanılarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="4f598-525">The service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="4f598-526">Kullanılan bağlama, 6.5.1 içinde açıklandığı gibi simetrik bağlamanın bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="4f598-526">The binding used is an instance of symmetric binding as described in 6.5.1.</span></span>  
  
 <span data-ttu-id="4f598-527">İlke</span><span class="sxs-lookup"><span data-stu-id="4f598-527">Policy</span></span>  
  
 <span data-ttu-id="4f598-528">Bağlama ayrıntıları için yukarıdaki 6.5.1 bölümüne bakın</span><span class="sxs-lookup"><span data-stu-id="4f598-528">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="4f598-529">İmzalı destekleme belirteci</span><span class="sxs-lookup"><span data-stu-id="4f598-529">Signed Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="4f598-530">Güvenlik üst bilgisi örnekleri: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="4f598-530">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="4f598-531">İstek</span><span class="sxs-lookup"><span data-stu-id="4f598-531">Request</span></span>  
  
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
  
 <span data-ttu-id="4f598-532">Yanıt</span><span class="sxs-lookup"><span data-stu-id="4f598-532">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="4f598-533">Güvenlik üst bilgisi örnekleri: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="4f598-533">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="4f598-534">İstek</span><span class="sxs-lookup"><span data-stu-id="4f598-534">Request</span></span>  
  
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
  
 <span data-ttu-id="4f598-535">Yanıt</span><span class="sxs-lookup"><span data-stu-id="4f598-535">Response</span></span>  
  
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
  
#### <a name="654-issuedtokenforsslnegotiated"></a><span data-ttu-id="4f598-536">6.5.4 ıssuedtokenforsslanlaşmalı</span><span class="sxs-lookup"><span data-stu-id="4f598-536">6.5.4 IssuedTokenForSslNegotiated</span></span>  

 <span data-ttu-id="4f598-537">Bu kimlik doğrulama modunda istemci, bu şekilde hizmette kimlik doğrulaması yapmaz, ancak bunun yerine STS tarafından verilen bir belirteç ve paylaşılan anahtar hakkında bilgi sahibi olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="4f598-537">With this authentication mode the client does not authenticate to the service, as such, but instead presents a token issued by an STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="4f598-538">Verilen belirteç, SOAP katmanında bir onaylama destekleme belirteci olarak görünür.</span><span class="sxs-lookup"><span data-stu-id="4f598-538">The issued token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="4f598-539">Hizmetin kimliği bir X. 509.440 sertifikası kullanılarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="4f598-539">The service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="4f598-540">Kullanılan bağlama, yukarıdaki 6.5.1 açıklanan simetrik bağlamanın bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="4f598-540">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="4f598-541">İlke</span><span class="sxs-lookup"><span data-stu-id="4f598-541">Policy</span></span>  
  
 <span data-ttu-id="4f598-542">Bağlama ayrıntıları için yukarıdaki 6.5.1 bölümüne bakın</span><span class="sxs-lookup"><span data-stu-id="4f598-542">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="4f598-543">Destekleyici belirteç onaylama</span><span class="sxs-lookup"><span data-stu-id="4f598-543">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="4f598-544">Güvenlik üst bilgisi örnekleri: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="4f598-544">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="4f598-545">İstek</span><span class="sxs-lookup"><span data-stu-id="4f598-545">Request</span></span>  
  
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
  
 <span data-ttu-id="4f598-546">Yanıt</span><span class="sxs-lookup"><span data-stu-id="4f598-546">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="4f598-547">Güvenlik üst bilgisi örnekleri: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="4f598-547">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="4f598-548">İstek</span><span class="sxs-lookup"><span data-stu-id="4f598-548">Request</span></span>  
  
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
  
 <span data-ttu-id="4f598-549">Yanıt</span><span class="sxs-lookup"><span data-stu-id="4f598-549">Response</span></span>  
  
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
  
#### <a name="655-mutualsslnegotiated"></a><span data-ttu-id="4f598-550">6.5.5 Mulualsslanlaşmalı</span><span class="sxs-lookup"><span data-stu-id="4f598-550">6.5.5 MutualSslNegotiated</span></span>  

 <span data-ttu-id="4f598-551">Bu kimlik doğrulama moduyla, istemci ve hizmet X. 509.440 sertifikalarını kullanarak kimlik doğrular.</span><span class="sxs-lookup"><span data-stu-id="4f598-551">With this authentication mode the client and the service authenticate using X.509 certificates.</span></span> <span data-ttu-id="4f598-552">Kullanılan bağlama, yukarıdaki 6.5.1 açıklanan simetrik bağlamanın bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="4f598-552">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="4f598-553">İlke</span><span class="sxs-lookup"><span data-stu-id="4f598-553">Policy</span></span>  
  
 <span data-ttu-id="4f598-554">Bağlama ayrıntıları için yukarıdaki 6.5.1 bölümüne bakın</span><span class="sxs-lookup"><span data-stu-id="4f598-554">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="4f598-555">Destekleyici belirteç onaylama</span><span class="sxs-lookup"><span data-stu-id="4f598-555">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="4f598-556">Güvenlik üst bilgisi örnekleri: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="4f598-556">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="4f598-557">İstek</span><span class="sxs-lookup"><span data-stu-id="4f598-557">Request</span></span>  
  
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
  
 <span data-ttu-id="4f598-558">Yanıt</span><span class="sxs-lookup"><span data-stu-id="4f598-558">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="4f598-559">Güvenlik üst bilgisi örnekleri: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="4f598-559">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="4f598-560">İstek</span><span class="sxs-lookup"><span data-stu-id="4f598-560">Request</span></span>  
  
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
  
 <span data-ttu-id="4f598-561">Yanıt</span><span class="sxs-lookup"><span data-stu-id="4f598-561">Response</span></span>  
  
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
  
### <a name="66-sspinegotiated"></a><span data-ttu-id="4f598-562">6,6 SspiNegotiated</span><span class="sxs-lookup"><span data-stu-id="4f598-562">6.6 SspiNegotiated</span></span>  

 <span data-ttu-id="4f598-563">Bu kimlik doğrulama modunda, istemci ve sunucu kimlik doğrulamasını gerçekleştirmek için bir anlaşma protokolü kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4f598-563">With this authentication mode a negotiation protocol is used to perform client and server authentication.</span></span> <span data-ttu-id="4f598-564">Mümkünse, Kerberos kullanılır, aksi takdirde NTLM kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4f598-564">Kerberos is used if possible, otherwise NTLM.</span></span> <span data-ttu-id="4f598-565">Kullanılan bağlama, aşağıdaki özelliklerle simetrik bir bağlamadır;</span><span class="sxs-lookup"><span data-stu-id="4f598-565">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="4f598-566">Koruma belirteci: SpnegoContextToken, ekleme modu. ../ıncludetoken/AlwaysToRecipient olarak ayarlandı</span><span class="sxs-lookup"><span data-stu-id="4f598-566">Protection Token: SpnegoContextToken, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
<span data-ttu-id="4f598-567">Belirteç koruması: false</span><span class="sxs-lookup"><span data-stu-id="4f598-567">Token Protection: False</span></span>  
  
 <span data-ttu-id="4f598-568">Tüm başlık ve gövde Imzaları: doğru</span><span class="sxs-lookup"><span data-stu-id="4f598-568">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="4f598-569">Koruma sırası: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="4f598-569">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="4f598-570">Imzayı şifreleyin: doğru</span><span class="sxs-lookup"><span data-stu-id="4f598-570">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="4f598-571">İlke</span><span class="sxs-lookup"><span data-stu-id="4f598-571">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="4f598-572">Güvenlik üst bilgisi örnekleri: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="4f598-572">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="4f598-573">İstek</span><span class="sxs-lookup"><span data-stu-id="4f598-573">Request</span></span>  
  
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
  
 <span data-ttu-id="4f598-574">Yanıt</span><span class="sxs-lookup"><span data-stu-id="4f598-574">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="4f598-575">Güvenlik üst bilgisi örnekleri: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="4f598-575">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="4f598-576">İstek</span><span class="sxs-lookup"><span data-stu-id="4f598-576">Request</span></span>  
  
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
  
 <span data-ttu-id="4f598-577">Yanıt</span><span class="sxs-lookup"><span data-stu-id="4f598-577">Response</span></span>  
  
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
  
### <a name="67-secureconversation"></a><span data-ttu-id="4f598-578">6,7 SecureConversation</span><span class="sxs-lookup"><span data-stu-id="4f598-578">6.7 SecureConversation</span></span>  

 <span data-ttu-id="4f598-579">Kullanılan bağlama, koruma belirtecine WS-SecureConversation (WS-SC) başına SCT olan bir simetrik bağlamadır.</span><span class="sxs-lookup"><span data-stu-id="4f598-579">The binding used is a symmetric binding with the protection token being a SCT per WS-SecureConversation (WS-SC).</span></span> <span data-ttu-id="4f598-580">SCT, bir anlaşma Protokolü kullanan simetrik bir bağlama olan iç içe bir bağlamaya göre WS-Trust (WS-Trust) veya WS-SecureConversation (WS-SC) kullanılarak anlaşılır.</span><span class="sxs-lookup"><span data-stu-id="4f598-580">The SCT is negotiated using WS-Trust (WS-Trust) or WS-SecureConversation (WS-SC) according to a nested binding, which is itself a symmetric binding that uses a negotiation protocol.</span></span> <span data-ttu-id="4f598-581">Anlaşma Protokolü, mümkünse istemci ve sunucu kimlik doğrulaması gerçekleştirmek için Kerberos kullanır.</span><span class="sxs-lookup"><span data-stu-id="4f598-581">The negotiation protocol will use Kerberos to perform client and server authentication if possible.</span></span> <span data-ttu-id="4f598-582">Kerberos kullanılmıyorsa, NTLM 'ye geri döner.</span><span class="sxs-lookup"><span data-stu-id="4f598-582">If Kerberos cannot be used, it will fall back to NTLM.</span></span>  
  
 <span data-ttu-id="4f598-583">İlke</span><span class="sxs-lookup"><span data-stu-id="4f598-583">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="4f598-584">Güvenlik üst bilgisi örnekleri: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="4f598-584">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="4f598-585">İstek</span><span class="sxs-lookup"><span data-stu-id="4f598-585">Request</span></span>  
  
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
  
 <span data-ttu-id="4f598-586">Yanıt</span><span class="sxs-lookup"><span data-stu-id="4f598-586">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="4f598-587">Güvenlik üst bilgisi örnekleri: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="4f598-587">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="4f598-588">İstek</span><span class="sxs-lookup"><span data-stu-id="4f598-588">Request</span></span>  
  
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
  
 <span data-ttu-id="4f598-589">Yanıt</span><span class="sxs-lookup"><span data-stu-id="4f598-589">Response</span></span>  
  
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

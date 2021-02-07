---
description: 'Daha fazla bilgi edinin: güvenlik protokolleri'
title: Güvenlik Protokolleri
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF], protocols
ms.assetid: 57ffcbea-807c-4e43-a41c-44b3db8ed2af
ms.openlocfilehash: 267724f852e2402054c11fbada3ef465db4b1ca2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726812"
---
# <a name="security-protocols"></a><span data-ttu-id="31916-103">Güvenlik Protokolleri</span><span class="sxs-lookup"><span data-stu-id="31916-103">Security Protocols</span></span>

<span data-ttu-id="31916-104">Web Hizmetleri Güvenliği protokolleri, mevcut tüm kurumsal mesajlaşma güvenlik gereksinimlerini kapsayan Web Hizmetleri güvenlik mekanizmaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="31916-104">The Web Services Security Protocols provide Web services security mechanisms that cover all existing enterprise messaging security requirements.</span></span> <span data-ttu-id="31916-105">Bu bölümde, <xref:System.ServiceModel.Channels.SecurityBindingElement> aşağıdaki Web Hizmetleri güvenlik protokolleri için Windows Communication Foundation (WCF) ayrıntıları (' de uygulanır) açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="31916-105">This section describes the Windows Communication Foundation (WCF) details (implemented in the <xref:System.ServiceModel.Channels.SecurityBindingElement>) for the following Web services security protocols.</span></span>  
  
|<span data-ttu-id="31916-106">Belirtim/belge</span><span class="sxs-lookup"><span data-stu-id="31916-106">Specification/Document</span></span>|<span data-ttu-id="31916-107">Bağlantı</span><span class="sxs-lookup"><span data-stu-id="31916-107">Link</span></span>|  
|-|-|  
|<span data-ttu-id="31916-108">WSS: SOAP Iletisi güvenliği 1,0</span><span class="sxs-lookup"><span data-stu-id="31916-108">WSS: SOAP Message Security 1.0</span></span>|<http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf>|  
|<span data-ttu-id="31916-109">WSS: Kullanıcı adı belirteç profili 1,0</span><span class="sxs-lookup"><span data-stu-id="31916-109">WSS: Username Token Profile 1.0</span></span>|<http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf>|  
|<span data-ttu-id="31916-110">WSS: x509 belirteç profili 1,0</span><span class="sxs-lookup"><span data-stu-id="31916-110">WSS: X509 Token Profile 1.0</span></span>|<http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0.pdf>|  
|<span data-ttu-id="31916-111">WSS: SAML 1,1 belirteç profili 1,0</span><span class="sxs-lookup"><span data-stu-id="31916-111">WSS: SAML 1.1 Token Profile 1.0</span></span>|<http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.0.pdf>|  
|<span data-ttu-id="31916-112">WSS: SOAP Iletisi güvenliği 1,1</span><span class="sxs-lookup"><span data-stu-id="31916-112">WSS: SOAP Message Security 1.1</span></span>|<http://www.oasis-open.org/committees/download.php/16790/wss-v1.1-spec-os-SOAPMessageSecurity.pdf>|  
|<span data-ttu-id="31916-113">WSS Kullanıcı adı belirteç profili 1,1</span><span class="sxs-lookup"><span data-stu-id="31916-113">WSS Username Token Profile 1.1</span></span>|<http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf>|  
|<span data-ttu-id="31916-114">WSS: X. 509.440 belirteç profili 1,1</span><span class="sxs-lookup"><span data-stu-id="31916-114">WSS: X.509 Token Profile 1.1</span></span>|<http://www.oasis-open.org/committees/download.php/16785/wss-v1.1-spec-os-x509TokenProfile.pdf>|  
|<span data-ttu-id="31916-115">WSS: Kerberos belirteç profili 1,1</span><span class="sxs-lookup"><span data-stu-id="31916-115">WSS: Kerberos Token Profile 1.1</span></span>|<http://www.oasis-open.org/committees/download.php/16788/wss-v1.1-spec-os-KerberosTokenProfile.pdf>|  
|<span data-ttu-id="31916-116">WSS: SAML 1,1 belirteç profili 1,1</span><span class="sxs-lookup"><span data-stu-id="31916-116">WSS: SAML 1.1 Token Profile 1.1</span></span>|<http://www.oasis-open.org/committees/download.php/16768/wss-v1.1-spec-os-SAMLTokenProfile.pdf>|  
|<span data-ttu-id="31916-117">WS-Secure konuşması 1,3</span><span class="sxs-lookup"><span data-stu-id="31916-117">WS-Secure Conversation 1.3</span></span>|<http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512/ws-secureconversation-1.3-os.pdf>|  
|<span data-ttu-id="31916-118">WS-Trust 1,3</span><span class="sxs-lookup"><span data-stu-id="31916-118">WS-Trust 1.3</span></span>|<http://docs.oasis-open.org/ws-sx/ws-trust/200512/ws-trust-1.3-os.pdf>|  
|<span data-ttu-id="31916-119">Uygulama notunun:</span><span class="sxs-lookup"><span data-stu-id="31916-119">Application Note:</span></span><br /><br /> <span data-ttu-id="31916-120">TLS el sıkışması için WS-Trust kullanma</span><span class="sxs-lookup"><span data-stu-id="31916-120">Using WS-Trust for TLS Handshake</span></span>|<span data-ttu-id="31916-121">Yayımlanacak</span><span class="sxs-lookup"><span data-stu-id="31916-121">To be published</span></span>|  
|<span data-ttu-id="31916-122">Uygulama notunun:</span><span class="sxs-lookup"><span data-stu-id="31916-122">Application Note:</span></span><br /><br /> <span data-ttu-id="31916-123">SPNEGO için WS-Trust kullanma</span><span class="sxs-lookup"><span data-stu-id="31916-123">Using WS-Trust for SPNEGO</span></span>|<span data-ttu-id="31916-124">Yayımlanacak</span><span class="sxs-lookup"><span data-stu-id="31916-124">To be published</span></span>|  
|<span data-ttu-id="31916-125">Uygulama notunun:</span><span class="sxs-lookup"><span data-stu-id="31916-125">Application Note:</span></span><br /><br /> <span data-ttu-id="31916-126">Web Hizmetleri, uç nokta başvurularını ve kimliğini adresleyen</span><span class="sxs-lookup"><span data-stu-id="31916-126">Web Services Addressing Endpoint References And Identity</span></span>|<span data-ttu-id="31916-127">Yayımlanacak</span><span class="sxs-lookup"><span data-stu-id="31916-127">To be published</span></span>|  
|<span data-ttu-id="31916-128">WS-SecurityPolicy 1,2 (2007/04)</span><span class="sxs-lookup"><span data-stu-id="31916-128">WS-SecurityPolicy 1.2 (2007/04)</span></span>|<http://www.oasis-open.org/committees/download.php/23821/ws-securitypolicy-1.2-spec-cs.pdf>|  
  
 <span data-ttu-id="31916-129">WCF, sürüm 1, Web Hizmetleri güvenlik yapılandırması için temel olarak kullanılabilecek 17 kimlik doğrulama modu sağlar.</span><span class="sxs-lookup"><span data-stu-id="31916-129">WCF, version 1, provides 17 authentication modes that can be used as the basis for Web services security configuration.</span></span> <span data-ttu-id="31916-130">Her mod ortak bir dağıtım gereksinimleri kümesi için iyileştirilmiştir, örneğin:</span><span class="sxs-lookup"><span data-stu-id="31916-130">Each mode is optimized for a common set of deployment requirements, such as:</span></span>  
  
- <span data-ttu-id="31916-131">İstemci ve hizmetin kimliğini doğrulamak için kullanılan kimlik bilgileri.</span><span class="sxs-lookup"><span data-stu-id="31916-131">Credentials used to authenticate client and service.</span></span>  
  
- <span data-ttu-id="31916-132">İleti veya aktarım güvenliği koruma mekanizmaları.</span><span class="sxs-lookup"><span data-stu-id="31916-132">Message or transport security protection mechanisms.</span></span>  
  
- <span data-ttu-id="31916-133">İleti değişimi desenleri.</span><span class="sxs-lookup"><span data-stu-id="31916-133">Message exchange patterns.</span></span>  
  
|<span data-ttu-id="31916-134">Kimlik Doğrulaması Modu</span><span class="sxs-lookup"><span data-stu-id="31916-134">Authentication Mode</span></span>|<span data-ttu-id="31916-135">İstemci Kimlik Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="31916-135">Client Authentication</span></span>|<span data-ttu-id="31916-136">Sunucu kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="31916-136">Server Authentication</span></span>|<span data-ttu-id="31916-137">Mod</span><span class="sxs-lookup"><span data-stu-id="31916-137">Mode</span></span>|  
|-------------------------|---------------------------|---------------------------|----------|  
|<span data-ttu-id="31916-138">UserNameOverTransport</span><span class="sxs-lookup"><span data-stu-id="31916-138">UserNameOverTransport</span></span>|<span data-ttu-id="31916-139">Kullanıcı adı/parola</span><span class="sxs-lookup"><span data-stu-id="31916-139">User name/password</span></span>|<span data-ttu-id="31916-140">X509</span><span class="sxs-lookup"><span data-stu-id="31916-140">X509</span></span>|<span data-ttu-id="31916-141">Aktarım</span><span class="sxs-lookup"><span data-stu-id="31916-141">Transport</span></span>|  
|<span data-ttu-id="31916-142">CertificateOverTransport</span><span class="sxs-lookup"><span data-stu-id="31916-142">CertificateOverTransport</span></span>|<span data-ttu-id="31916-143">X509</span><span class="sxs-lookup"><span data-stu-id="31916-143">X509</span></span>|<span data-ttu-id="31916-144">X509</span><span class="sxs-lookup"><span data-stu-id="31916-144">X509</span></span>|<span data-ttu-id="31916-145">Aktarım</span><span class="sxs-lookup"><span data-stu-id="31916-145">Transport</span></span>|  
|<span data-ttu-id="31916-146">KerberosOverTransport</span><span class="sxs-lookup"><span data-stu-id="31916-146">KerberosOverTransport</span></span>|<span data-ttu-id="31916-147">Windows</span><span class="sxs-lookup"><span data-stu-id="31916-147">Windows</span></span>|<span data-ttu-id="31916-148">X509</span><span class="sxs-lookup"><span data-stu-id="31916-148">X509</span></span>|<span data-ttu-id="31916-149">Aktarım</span><span class="sxs-lookup"><span data-stu-id="31916-149">Transport</span></span>|  
|<span data-ttu-id="31916-150">IssuedTokenOverTransport</span><span class="sxs-lookup"><span data-stu-id="31916-150">IssuedTokenOverTransport</span></span>|<span data-ttu-id="31916-151">Federe</span><span class="sxs-lookup"><span data-stu-id="31916-151">Federated</span></span>|<span data-ttu-id="31916-152">X509</span><span class="sxs-lookup"><span data-stu-id="31916-152">X509</span></span>|<span data-ttu-id="31916-153">Aktarım</span><span class="sxs-lookup"><span data-stu-id="31916-153">Transport</span></span>|  
|<span data-ttu-id="31916-154">SspiNegotiatedOverTransport</span><span class="sxs-lookup"><span data-stu-id="31916-154">SspiNegotiatedOverTransport</span></span>|<span data-ttu-id="31916-155">Üzerinde anlaşılan Windows SSPI</span><span class="sxs-lookup"><span data-stu-id="31916-155">Windows Sspi Negotiated</span></span>|<span data-ttu-id="31916-156">Üzerinde anlaşılan Windows SSPI</span><span class="sxs-lookup"><span data-stu-id="31916-156">Windows Sspi Negotiated</span></span>|<span data-ttu-id="31916-157">Aktarım</span><span class="sxs-lookup"><span data-stu-id="31916-157">Transport</span></span>|  
|<span data-ttu-id="31916-158">AnonymousForCertificate</span><span class="sxs-lookup"><span data-stu-id="31916-158">AnonymousForCertificate</span></span>|<span data-ttu-id="31916-159">Yok</span><span class="sxs-lookup"><span data-stu-id="31916-159">None</span></span>|<span data-ttu-id="31916-160">X509</span><span class="sxs-lookup"><span data-stu-id="31916-160">X509</span></span>|<span data-ttu-id="31916-161">İleti</span><span class="sxs-lookup"><span data-stu-id="31916-161">Message</span></span>|  
|<span data-ttu-id="31916-162">UserNameForCertificate</span><span class="sxs-lookup"><span data-stu-id="31916-162">UserNameForCertificate</span></span>|<span data-ttu-id="31916-163">Kullanıcı adı/parola</span><span class="sxs-lookup"><span data-stu-id="31916-163">User name/password</span></span>|<span data-ttu-id="31916-164">X509</span><span class="sxs-lookup"><span data-stu-id="31916-164">X509</span></span>|<span data-ttu-id="31916-165">İleti</span><span class="sxs-lookup"><span data-stu-id="31916-165">Message</span></span>|  
|<span data-ttu-id="31916-166">Çoklu sertifika</span><span class="sxs-lookup"><span data-stu-id="31916-166">MutualCertificate</span></span>|<span data-ttu-id="31916-167">X509</span><span class="sxs-lookup"><span data-stu-id="31916-167">X509</span></span>|<span data-ttu-id="31916-168">X509</span><span class="sxs-lookup"><span data-stu-id="31916-168">X509</span></span>|<span data-ttu-id="31916-169">İleti</span><span class="sxs-lookup"><span data-stu-id="31916-169">Message</span></span>|  
|<span data-ttu-id="31916-170">Değişken Uıalcertificateduplex</span><span class="sxs-lookup"><span data-stu-id="31916-170">MutualCertificateDuplex</span></span>|<span data-ttu-id="31916-171">X509</span><span class="sxs-lookup"><span data-stu-id="31916-171">X509</span></span>|<span data-ttu-id="31916-172">X509</span><span class="sxs-lookup"><span data-stu-id="31916-172">X509</span></span>|<span data-ttu-id="31916-173">İleti</span><span class="sxs-lookup"><span data-stu-id="31916-173">Message</span></span>|  
|<span data-ttu-id="31916-174">IssuedTokenForCertificate</span><span class="sxs-lookup"><span data-stu-id="31916-174">IssuedTokenForCertificate</span></span>|<span data-ttu-id="31916-175">Federe</span><span class="sxs-lookup"><span data-stu-id="31916-175">Federated</span></span>|<span data-ttu-id="31916-176">X509</span><span class="sxs-lookup"><span data-stu-id="31916-176">X509</span></span>|<span data-ttu-id="31916-177">İleti</span><span class="sxs-lookup"><span data-stu-id="31916-177">Message</span></span>|  
|<span data-ttu-id="31916-178">Kerberos</span><span class="sxs-lookup"><span data-stu-id="31916-178">Kerberos</span></span>|<span data-ttu-id="31916-179">Windows</span><span class="sxs-lookup"><span data-stu-id="31916-179">Windows</span></span>|<span data-ttu-id="31916-180">Windows</span><span class="sxs-lookup"><span data-stu-id="31916-180">Windows</span></span>|<span data-ttu-id="31916-181">İleti</span><span class="sxs-lookup"><span data-stu-id="31916-181">Message</span></span>|  
|<span data-ttu-id="31916-182">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="31916-182">IssuedToken</span></span>|<span data-ttu-id="31916-183">Federe</span><span class="sxs-lookup"><span data-stu-id="31916-183">Federated</span></span>|<span data-ttu-id="31916-184">Federe</span><span class="sxs-lookup"><span data-stu-id="31916-184">Federated</span></span>|<span data-ttu-id="31916-185">İleti</span><span class="sxs-lookup"><span data-stu-id="31916-185">Message</span></span>|  
|<span data-ttu-id="31916-186">SspiNegotiated</span><span class="sxs-lookup"><span data-stu-id="31916-186">SspiNegotiated</span></span>|<span data-ttu-id="31916-187">Üzerinde anlaşılan Windows SSPI</span><span class="sxs-lookup"><span data-stu-id="31916-187">Windows Sspi Negotiated</span></span>|<span data-ttu-id="31916-188">Üzerinde anlaşılan Windows SSPI</span><span class="sxs-lookup"><span data-stu-id="31916-188">Windows Sspi Negotiated</span></span>|<span data-ttu-id="31916-189">İleti</span><span class="sxs-lookup"><span data-stu-id="31916-189">Message</span></span>|  
|<span data-ttu-id="31916-190">Anonymousforsslanlaşmalı</span><span class="sxs-lookup"><span data-stu-id="31916-190">AnonymousForSslNegotiated</span></span>|<span data-ttu-id="31916-191">Yok</span><span class="sxs-lookup"><span data-stu-id="31916-191">None</span></span>|<span data-ttu-id="31916-192">X509, TLS-Nego</span><span class="sxs-lookup"><span data-stu-id="31916-192">X509, TLS-Nego</span></span>|<span data-ttu-id="31916-193">İleti</span><span class="sxs-lookup"><span data-stu-id="31916-193">Message</span></span>|  
|<span data-ttu-id="31916-194">Usernameforsslanlaşmalı</span><span class="sxs-lookup"><span data-stu-id="31916-194">UserNameForSslNegotiated</span></span>|<span data-ttu-id="31916-195">Kullanıcı adı/parola</span><span class="sxs-lookup"><span data-stu-id="31916-195">User name/password</span></span>|<span data-ttu-id="31916-196">X509, TLS-Nego</span><span class="sxs-lookup"><span data-stu-id="31916-196">X509, TLS-Nego</span></span>|<span data-ttu-id="31916-197">İleti</span><span class="sxs-lookup"><span data-stu-id="31916-197">Message</span></span>|  
|<span data-ttu-id="31916-198">Değişken anlaşmalı</span><span class="sxs-lookup"><span data-stu-id="31916-198">MutualSslNegotiated</span></span>|<span data-ttu-id="31916-199">X509</span><span class="sxs-lookup"><span data-stu-id="31916-199">X509</span></span>|<span data-ttu-id="31916-200">X509, TLS-Nego</span><span class="sxs-lookup"><span data-stu-id="31916-200">X509, TLS-Nego</span></span>|<span data-ttu-id="31916-201">İleti</span><span class="sxs-lookup"><span data-stu-id="31916-201">Message</span></span>|  
|<span data-ttu-id="31916-202">Issuedtokenforsslanlaşmalı</span><span class="sxs-lookup"><span data-stu-id="31916-202">IssuedTokenForSslNegotiated</span></span>|<span data-ttu-id="31916-203">Federe</span><span class="sxs-lookup"><span data-stu-id="31916-203">Federated</span></span>|<span data-ttu-id="31916-204">X509, TLS-Nego</span><span class="sxs-lookup"><span data-stu-id="31916-204">X509, TLS-Nego</span></span>|<span data-ttu-id="31916-205">İleti</span><span class="sxs-lookup"><span data-stu-id="31916-205">Message</span></span>|  
  
 <span data-ttu-id="31916-206">Bu tür kimlik doğrulama modlarını kullanan uç noktalar, WS-SecurityPolicy (WS-SP) kullanarak güvenlik gereksinimlerini ifade edebilir.</span><span class="sxs-lookup"><span data-stu-id="31916-206">Endpoints using such authentication modes can express their security requirements using WS-SecurityPolicy (WS-SP).</span></span> <span data-ttu-id="31916-207">Bu belgede, her kimlik doğrulama modu için güvenlik üst bilgisi ve altyapı iletilerinin yapısı açıklanmakta ve ilke ve ileti örnekleri verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="31916-207">This document describes the structure of security header and infrastructure messages for each authentication mode and provides examples of policies and messages.</span></span>  
  
 <span data-ttu-id="31916-208">WCF, uygulamalar arasında çok ileti değişimlerinin korunması için güvenli oturumlar desteği sağlamak üzere WS-SecureConversation yararlanır.</span><span class="sxs-lookup"><span data-stu-id="31916-208">WCF leverages WS-SecureConversation to provide secure sessions support to protect multi-message exchanges between applications.</span></span>  <span data-ttu-id="31916-209">Uygulama ayrıntıları için aşağıda "güvenli oturumlar" başlığına bakın.</span><span class="sxs-lookup"><span data-stu-id="31916-209">See "Secure Sessions" below for implementation details.</span></span>  
  
 <span data-ttu-id="31916-210">WCF, kimlik doğrulama modlarına ek olarak, çoğu ileti güvenlik tabanlı kimlik doğrulama modu için uygulanan genel koruma mekanizmalarını denetlemek için ayarlar sağlar; örneğin, imza sırası, şifreleme işlemleri, algoritma paketleri, anahtar türetme ve imza onayı.</span><span class="sxs-lookup"><span data-stu-id="31916-210">In addition to authentication modes, WCF provides settings to control common protection mechanisms that apply to most message security-based authentication modes, for example: order of signature versus encryption operations, algorithm suites, key derivation, and signature confirmation.</span></span>  
  
 <span data-ttu-id="31916-211">Bu belgede aşağıdaki ön ekler ve ad alanları kullanılır.</span><span class="sxs-lookup"><span data-stu-id="31916-211">The following prefixes and namespaces are used in this document.</span></span>  
  
|<span data-ttu-id="31916-212">Ön ek</span><span class="sxs-lookup"><span data-stu-id="31916-212">Prefix</span></span>|<span data-ttu-id="31916-213">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="31916-213">Namespace</span></span>|  
|------------|---------------|  
|<span data-ttu-id="31916-214">s</span><span class="sxs-lookup"><span data-stu-id="31916-214">s</span></span>|`http://www.w3.org/2003/05/soap-envelope`|  
|<span data-ttu-id="31916-215">sp</span><span class="sxs-lookup"><span data-stu-id="31916-215">sp</span></span>|`http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702`|  
|<span data-ttu-id="31916-216">a</span><span class="sxs-lookup"><span data-stu-id="31916-216">a</span></span>|`http://www.w3.org/2005/08/addressing`|  
|<span data-ttu-id="31916-217">WSO</span><span class="sxs-lookup"><span data-stu-id="31916-217">wsse</span></span>|<span data-ttu-id="31916-218">TBD – OASSıS WSS 1,0 URI 'SI</span><span class="sxs-lookup"><span data-stu-id="31916-218">TBD – OASIS WSS 1.0 URI</span></span>|  
|<span data-ttu-id="31916-219">wsse11</span><span class="sxs-lookup"><span data-stu-id="31916-219">wsse11</span></span>|<span data-ttu-id="31916-220">TBD – OASSıS WSS 1,1 URI 'SI</span><span class="sxs-lookup"><span data-stu-id="31916-220">TBD – OASIS WSS 1.1 URI</span></span>|  
|<span data-ttu-id="31916-221">WSU dili</span><span class="sxs-lookup"><span data-stu-id="31916-221">wsu</span></span>|`http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd`|  
|<span data-ttu-id="31916-222">FID</span><span class="sxs-lookup"><span data-stu-id="31916-222">ds</span></span>|<span data-ttu-id="31916-223">TBD – W3C XMLDSIG URI 'SI</span><span class="sxs-lookup"><span data-stu-id="31916-223">TBD – W3C XMLDSig URI</span></span>|  
|<span data-ttu-id="31916-224">WST</span><span class="sxs-lookup"><span data-stu-id="31916-224">wst</span></span>|<span data-ttu-id="31916-225">TBD – WS-Trust 2005/02 URI 'SI</span><span class="sxs-lookup"><span data-stu-id="31916-225">TBD – WS-Trust 2005/02 URI</span></span>|  
|<span data-ttu-id="31916-226">wssc</span><span class="sxs-lookup"><span data-stu-id="31916-226">wssc</span></span>|<span data-ttu-id="31916-227">TBD – WS-SecureConversation 2005/02 URI 'SI</span><span class="sxs-lookup"><span data-stu-id="31916-227">TBD – WS-SecureConversation 2005/02 URI</span></span>|  
|<span data-ttu-id="31916-228">Wonu dili</span><span class="sxs-lookup"><span data-stu-id="31916-228">wsaw</span></span>|`http://www.w3.org/2006/05/addressing/wsdl`|  
|<span data-ttu-id="31916-229">WSP</span><span class="sxs-lookup"><span data-stu-id="31916-229">wsp</span></span>|`http://schemas.xmlsoap.org/ws/2004/09/policy`|  
|<span data-ttu-id="31916-230">MSSP</span><span class="sxs-lookup"><span data-stu-id="31916-230">mssp</span></span>|`http://schemas.microsoft.com/ws/2005/07/securitypolicy`|  
  
## <a name="1-token-profiles"></a><span data-ttu-id="31916-231">1. belirteç profilleri</span><span class="sxs-lookup"><span data-stu-id="31916-231">1. Token Profiles</span></span>  

 <span data-ttu-id="31916-232">Web Hizmetleri Güvenliği belirtimleri güvenlik belirteçleri olarak kimlik bilgisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="31916-232">Web Services Security specifications represent credential as security tokens.</span></span> <span data-ttu-id="31916-233">WCF aşağıdaki belirteç türlerini destekler:</span><span class="sxs-lookup"><span data-stu-id="31916-233">WCF supports the following token types:</span></span>  
  
### <a name="11-usernametoken"></a><span data-ttu-id="31916-234">1,1 UsernameToken</span><span class="sxs-lookup"><span data-stu-id="31916-234">1.1 UsernameToken</span></span>  

 <span data-ttu-id="31916-235">WCF aşağıdaki kısıtlamalara sahip UsernameToken10 ve UsernameToken11 profillerini izler:</span><span class="sxs-lookup"><span data-stu-id="31916-235">WCF follows UsernameToken10 and UsernameToken11 profiles with the following constraints:</span></span>  
  
 <span data-ttu-id="31916-236">UsernameToken\Password öğesinde R1101 PasswordType özniteliği atlanmış veya değer #PasswordText (varsayılan) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="31916-236">R1101 PasswordType attribute on UsernameToken\Password element MUST be either omitted or have value #PasswordText (default).</span></span>  
  
 <span data-ttu-id="31916-237">Bunlardan biri, genişletilebilirlik kullanarak #PasswordDigest uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="31916-237">One can implement the #PasswordDigest using extensibility.</span></span> <span data-ttu-id="31916-238">#PasswordDigest genellikle yeterince güvenli bir parola koruma mekanizması olması gözlemlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="31916-238">It has been observed that #PasswordDigest was often mistaken to be a secure enough password protection mechanism.</span></span> <span data-ttu-id="31916-239">Ancak #PasswordDigest, UsernameToken şifrelemesinin bir alternatifi olarak kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="31916-239">But #PasswordDigest cannot serve as a substitute for encryption of the UsernameToken.</span></span> <span data-ttu-id="31916-240">#PasswordDigest birincil amacı, yeniden yürütme saldırılarına karşı koruma sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="31916-240">The primary goal of #PasswordDigest is protection against replay attacks.</span></span> <span data-ttu-id="31916-241">WCF kimlik doğrulama modlarında, yeniden yürütme saldırı tehditleri ileti imzaları kullanılarak azaltıldığında.</span><span class="sxs-lookup"><span data-stu-id="31916-241">In WCF authentication modes, replay attack threats are mitigated by using message signatures.</span></span>  
  
 <span data-ttu-id="31916-242">B1102 WCF hiçbir şekilde hiçbir şekilde anahtar vermez ve UsernameToken alt öğelerini oluşturmuştur.</span><span class="sxs-lookup"><span data-stu-id="31916-242">B1102 WCF never emits Nonce and Created sub-elements of the UsernameToken.</span></span>  
  
 <span data-ttu-id="31916-243">Bu alt öğeler, yeniden yürütmeyi algılamaya yardımcı olmayı amaçlar.</span><span class="sxs-lookup"><span data-stu-id="31916-243">These sub-elements are intended to help replay detection.</span></span> <span data-ttu-id="31916-244">WCF bunun yerine ileti imzalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="31916-244">WCF uses message signatures instead.</span></span>  
  
 <span data-ttu-id="31916-245">OASSıS WSS SOAP Iletisi güvenliği UsernameToken profili 1,1 (UsernameToken11) parola özelliğinden anahtar türetme sunmuştur.</span><span class="sxs-lookup"><span data-stu-id="31916-245">OASIS WSS SOAP Message Security UsernameToken Profile 1.1 (UsernameToken11) introduced key derivation from password feature.</span></span>  
  
 <span data-ttu-id="31916-246">B1103 UsernameToken parolası, anahtar türetmede kullanılmamalıdır ve bu nedenle şifreleme işlemleri için kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="31916-246">B1103 UsernameToken password MUST not be used for key derivation and therefore for cryptographic operations.</span></span>  
  
 <span data-ttu-id="31916-247">Korale: parolalar genellikle şifreleme işlemleri için kullanılmak üzere çok zayıf kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="31916-247">Rationale: passwords are generally considered too weak to be used for cryptographic operations.</span></span>  
  
### <a name="12-x509-token"></a><span data-ttu-id="31916-248">1,2 x509 belirteci</span><span class="sxs-lookup"><span data-stu-id="31916-248">1.2 X509 Token</span></span>  

 <span data-ttu-id="31916-249">WCF, kimlik bilgisi türü olarak X509v3 sertifikalarını destekler ve aşağıdaki kısıtlamalara sahip X509TokenProfile 1.0 ve X509TokenProfile 1.1 ' i izler:</span><span class="sxs-lookup"><span data-stu-id="31916-249">WCF supports X509v3 certificates as a credential type and follows X509TokenProfile1.0 and X509TokenProfile1.1 with the following constraints:</span></span>  
  
 <span data-ttu-id="31916-250">R1201, BinarySecurityToken öğesindeki ValueType özniteliği bir X509v3 sertifikası içerdiğinde değer #X509v3 sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="31916-250">R1201 The ValueType attribute on the BinarySecurityToken element must have value #X509v3 when it contains an X509v3 certificate.</span></span>  
  
 <span data-ttu-id="31916-251">WSS x509 belirteç profili 1,0 ve 1,1 de #X509PKIPathv1 ve #PKCS7 değer türleri olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="31916-251">WSS X509 Token Profile 1.0 and 1.1 define also #X509PKIPathv1 and #PKCS7 as value types.</span></span> <span data-ttu-id="31916-252">WCF bu türleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="31916-252">WCF does not support these types.</span></span>  
  
 <span data-ttu-id="31916-253">R1202 bir subjectKeyIdentifier (kayak) uzantısı, bir x509 sertifikasında mevcutsa,, #X509SubjectKeyIdentifier ve içeriği için ValueType özniteliği ve Content 'in Kayak uzantısının şifreli değeri olan ' a yönelik dış başvurular için, WSI: KeyIdentifier kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="31916-253">R1202 If a SubjectKeyIdentifier (SKI) extension is present in an X509 certificate, wsse:KeyIdentifier should be used for external references to the token, with the ValueType attribute as #X509SubjectKeyIdentifier and its content the base64-encoded value of certificate's SKI extension.</span></span>  
  
 <span data-ttu-id="31916-254">Kayak başvuruları yaygın olarak uygulanırlar ve yüksek oranda çalışabilen bir dış başvuru türü olarak kanıtlanmış olur.</span><span class="sxs-lookup"><span data-stu-id="31916-254">SKI references are widely implemented and proven to be a highly interoperable external reference type.</span></span>  
  
 <span data-ttu-id="31916-255">R1203 x509 güvenlik belirtecine bir dış başvuru DS: X509IssuerSerial KULLANMAMALıDıR.</span><span class="sxs-lookup"><span data-stu-id="31916-255">R1203 An external Reference to X509 Security Token SHOULD NOT use ds:X509IssuerSerial.</span></span>  
  
 <span data-ttu-id="31916-256">R1204 X509TokenProfile 1.1 kullanılıyorsa, x509 güvenlik belirtecine yönelik bir dış başvurunun WS-Security 1,1 tarafından tanıtılan parmak izini kullanması gerekır.</span><span class="sxs-lookup"><span data-stu-id="31916-256">R1204 If X509TokenProfile1.1 is in use, an external reference to X509 Security Token SHOULD use the thumbprint introduced by WS-Security 1.1.</span></span>  
  
 <span data-ttu-id="31916-257">WCF, X509IssuerSerial destekler.</span><span class="sxs-lookup"><span data-stu-id="31916-257">WCF supports X509IssuerSerial.</span></span> <span data-ttu-id="31916-258">Ancak X509IssuerSerial ile birlikte çalışabilirlik sorunları vardır: WCF, X509IssuerSerial 'in iki değerini karşılaştırmak için bir dize kullanır.</span><span class="sxs-lookup"><span data-stu-id="31916-258">However there are interoperability issues with X509IssuerSerial: WCF uses a string to compare two values of X509IssuerSerial.</span></span> <span data-ttu-id="31916-259">Bu nedenle, konu adının bileşenlerini yeniden sipariş eden bir, bir WCF hizmetine bir sertifikaya başvuru gönderirse, bu durum bulunamamıştır.</span><span class="sxs-lookup"><span data-stu-id="31916-259">Therefore if one reorders components of the Subject Name and sends to an WCF service a reference to a certificate, it may not be found.</span></span>  
  
### <a name="13-kerberos-token"></a><span data-ttu-id="31916-260">1,3 Kerberos belirteci</span><span class="sxs-lookup"><span data-stu-id="31916-260">1.3 Kerberos Token</span></span>  

 <span data-ttu-id="31916-261">WCF, Windows kimlik doğrulaması amacıyla aşağıdaki kısıtlamalara sahip KerberosTokenProfile 1.1 'yi destekler:</span><span class="sxs-lookup"><span data-stu-id="31916-261">WCF supports KerberosTokenProfile1.1 for the purpose of Windows authentication with the following constraints:</span></span>  
  
 <span data-ttu-id="31916-262">R1301 bir Kerberos belirtecinin, GSS_API ve Kerberos belirtiminde tanımlanan bir GSS sarmalanmış Kerberos v4 AP_REQ değerini taşıması ve değer #GSS_Kerberosv5_AP_REQ ValueType özniteliğine sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="31916-262">R1301 A Kerberos Token must carry the value of a GSS wrapped Kerberos v4 AP_REQ as defined in GSS_API and the Kerberos specification, and must have the ValueType attribute with the value #GSS_Kerberosv5_AP_REQ.</span></span>  
  
 <span data-ttu-id="31916-263">WCF, tam bir AP-REQ değil, GSS sarmalanmış Kerberos AP-REQ kullanır.</span><span class="sxs-lookup"><span data-stu-id="31916-263">WCF uses GSS wrapped Kerberos AP-REQ, not a bare AP-REQ.</span></span> <span data-ttu-id="31916-264">Bu en iyi güvenlik uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="31916-264">This is a security best practice.</span></span>  
  
### <a name="14-saml-v11-token"></a><span data-ttu-id="31916-265">1,4 SAML v 1.1 belirteci</span><span class="sxs-lookup"><span data-stu-id="31916-265">1.4 SAML v1.1 Token</span></span>  

 <span data-ttu-id="31916-266">WCF, SAML v 1.1 belirteçleri için WSS SAML belirteci profilleri 1,0 ve 1,1 ' ü destekler.</span><span class="sxs-lookup"><span data-stu-id="31916-266">WCF supports WSS SAML Token profiles 1.0 and 1.1 for SAML v1.1 tokens.</span></span> <span data-ttu-id="31916-267">SAML belirteci biçimlerinin diğer sürümlerini uygulamak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="31916-267">It is possible to implement other versions of SAML token formats.</span></span>  
  
### <a name="15-security-context-token"></a><span data-ttu-id="31916-268">1,5 güvenlik bağlamı belirteci</span><span class="sxs-lookup"><span data-stu-id="31916-268">1.5 Security Context Token</span></span>  

 <span data-ttu-id="31916-269">WCF, WS-SecureConversation ' de tanıtılan güvenlik bağlamı belirtecini (SCT) destekler.</span><span class="sxs-lookup"><span data-stu-id="31916-269">WCF supports the Security Context Token (SCT) introduced in WS-SecureConversation.</span></span> <span data-ttu-id="31916-270">SCT, SecureConversation 'de kurulu bir güvenlik bağlamını ve aşağıda açıklanan ikili anlaşma protokolleri TLS ve SSPI 'yi temsil etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="31916-270">SCT is used to represent a security context established in SecureConversation as well as the binary negotiation protocols TLS and SSPI, described below.</span></span>  
  
## <a name="2-common-message-security-parameters"></a><span data-ttu-id="31916-271">2. ortak Ileti güvenlik parametreleri</span><span class="sxs-lookup"><span data-stu-id="31916-271">2. Common Message Security Parameters</span></span>  
  
### <a name="21-timestamp"></a><span data-ttu-id="31916-272">2,1 zaman damgası</span><span class="sxs-lookup"><span data-stu-id="31916-272">2.1 TimeStamp</span></span>  

 <span data-ttu-id="31916-273">Zaman damgası varlığı, <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> sınıfının özelliği kullanılarak denetlenir <xref:System.ServiceModel.Channels.SecurityBindingElement> .</span><span class="sxs-lookup"><span data-stu-id="31916-273">Timestamp presence is controlled using the <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> property of the <xref:System.ServiceModel.Channels.SecurityBindingElement> class.</span></span> <span data-ttu-id="31916-274">WCF her zaman wsse: Created ve wsse: Expires alanları ile zaman damgası olarak serileştirir.</span><span class="sxs-lookup"><span data-stu-id="31916-274">WCF always serializes wsse:TimeStamp with wsse:Created and wsse:Expires fields.</span></span> <span data-ttu-id="31916-275">Wsse: imza kullanıldığında zaman damgası her zaman imzalanır.</span><span class="sxs-lookup"><span data-stu-id="31916-275">The wsse:TimeStamp is always signed when signing is used.</span></span>  
  
### <a name="22-protection-order"></a><span data-ttu-id="31916-276">2,2 koruma sırası</span><span class="sxs-lookup"><span data-stu-id="31916-276">2.2 Protection Order</span></span>  

 <span data-ttu-id="31916-277">WCF, "şifrelemeden önce Imzala" ve "oturum açmadan önce şifreleyin" (Güvenlik Ilkesi 1,2) ileti koruma sırasını destekler.</span><span class="sxs-lookup"><span data-stu-id="31916-277">WCF supports the message protection order "Sign Before Encrypt" and "Encrypt Before Sign" (Security Policy 1.2).</span></span> <span data-ttu-id="31916-278">Aşağıdakiler dahil olmak üzere "şifrelemeden önce imzala" önerilir: oturum açmadan önce şifrelemeden korunan iletiler, WS-Security 1,1 SignatureConfirmation mekanizması kullanılmamışsa ve şifrelenmiş içerik üzerinde bir imza denetimi daha zor hale getirir.</span><span class="sxs-lookup"><span data-stu-id="31916-278">"Sign Before Encrypt" is recommended for reasons including: messages protected with Encrypt Before Sign are open to signature substitution attacks unless the WS-Security 1.1 SignatureConfirmation mechanism is used, and a signature over encrypted content makes auditing harder.</span></span>  
  
### <a name="23-signature-protection"></a><span data-ttu-id="31916-279">2,3 imza koruması</span><span class="sxs-lookup"><span data-stu-id="31916-279">2.3 Signature Protection</span></span>  

 <span data-ttu-id="31916-280">İmza kullanılmadan önce şifrelendiğinde, şifrelenmiş içeriği veya imzalama anahtarını tahmin etmeye yönelik deneme yanılma saldırılarını engellemek için imzayı korumanız önerilir (özellikle de, zayıf anahtar malzemeyle özel bir belirteç kullanıldığında).</span><span class="sxs-lookup"><span data-stu-id="31916-280">When Encrypt Before Sign is used, it is recommended to protect the signature to prevent brute force attacks for guessing the encrypted content or the signing key (especially when a custom token is used with weak key material).</span></span>  
  
### <a name="24-algorithm-suite"></a><span data-ttu-id="31916-281">2,4 algoritma paketi</span><span class="sxs-lookup"><span data-stu-id="31916-281">2.4 Algorithm Suite</span></span>  

 <span data-ttu-id="31916-282">WCF, Güvenlik Ilkesi 1,2 ' de listelenen tüm algoritma paketlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="31916-282">WCF supports all algorithm suites listed in Security Policy 1.2.</span></span>  
  
### <a name="25-key-derivation"></a><span data-ttu-id="31916-283">2,5 anahtar türetme</span><span class="sxs-lookup"><span data-stu-id="31916-283">2.5 Key Derivation</span></span>  

 <span data-ttu-id="31916-284">WCF, WS-SecureConversation bölümünde açıklandığı gibi "simetrik anahtarlar için anahtar türetme" kullanır.</span><span class="sxs-lookup"><span data-stu-id="31916-284">WCF uses "Key Derivation for symmetric keys" as described in WS-SecureConversation.</span></span>  
  
### <a name="26-signature-confirmation"></a><span data-ttu-id="31916-285">2,6 imza onayı</span><span class="sxs-lookup"><span data-stu-id="31916-285">2.6 Signature Confirmation</span></span>  

 <span data-ttu-id="31916-286">İmza onayını korumak için ortadaki adam saldırılarına karşı koruma olarak imza onayı kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="31916-286">Signature confirmation can be used as protection from middle man attacks to protect the set of signatures.</span></span>  
  
### <a name="27-security-header-layout"></a><span data-ttu-id="31916-287">2,7 güvenlik üst bilgisi düzeni</span><span class="sxs-lookup"><span data-stu-id="31916-287">2.7 Security Header Layout</span></span>  

 <span data-ttu-id="31916-288">Her kimlik doğrulama modu, güvenlik üst bilgisi için belirli bir düzeni tanımlar.</span><span class="sxs-lookup"><span data-stu-id="31916-288">Each authentication mode describes a certain layout for the security header.</span></span> <span data-ttu-id="31916-289">Güvenlik üst bilgisi içindeki öğeler yarı sıralanır.</span><span class="sxs-lookup"><span data-stu-id="31916-289">Elements within the security header are semi-ordered.</span></span> <span data-ttu-id="31916-290">Güvenlik üst bilgisi alt öğelerinin sırasını tanımlamak için WS-Security Ilkesi aşağıdaki güvenlik üst bilgisi düzen modlarını tanımlar:</span><span class="sxs-lookup"><span data-stu-id="31916-290">To define the order of security header child elements, WS-Security Policy defines the following security header layout modes:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="31916-291">Katı</span><span class="sxs-lookup"><span data-stu-id="31916-291">Strict</span></span>|<span data-ttu-id="31916-292">Öğeler, Güvenlik Ilkesi bölümünde açıklanan numaralandırılmış düzen kurallarından sonra, "kullanmadan önce bildir" genel ilkesine göre güvenlik üstbilgisine eklenir.</span><span class="sxs-lookup"><span data-stu-id="31916-292">Items are added to the security header following the numbered layout rules described in Security Policy section 7.7.1 according to a general principle of "declare before use".</span></span>|  
|<span data-ttu-id="31916-293">LAX</span><span class="sxs-lookup"><span data-stu-id="31916-293">Lax</span></span>|<span data-ttu-id="31916-294">Öğeler, WSS: SOAP Iletisi güvenliğine uyan herhangi bir sırada güvenlik başlığına eklenir.</span><span class="sxs-lookup"><span data-stu-id="31916-294">Items are added to the security header in any order that conforms to WSS: SOAP Message Security.</span></span>|  
|<span data-ttu-id="31916-295">Önce Laxtimestamp</span><span class="sxs-lookup"><span data-stu-id="31916-295">LaxTimestampFirst</span></span>|<span data-ttu-id="31916-296">Güvenlik üst bilgisindeki ilk öğenin bir WSO: Timestamp olması dışında LAX ile aynı</span><span class="sxs-lookup"><span data-stu-id="31916-296">Same as Lax except that the first item in the security header must be a wsse:Timestamp</span></span>|  
|<span data-ttu-id="31916-297">Laxtimestamp son</span><span class="sxs-lookup"><span data-stu-id="31916-297">LaxTimestampLast</span></span>|<span data-ttu-id="31916-298">Güvenlik üstbilgisindeki son öğenin bir WSO: Timestamp olması dışında LAX ile aynı</span><span class="sxs-lookup"><span data-stu-id="31916-298">Same as lax except that the last item in the security header must be a wsse:Timestamp</span></span>|  
  
 <span data-ttu-id="31916-299">WCF, güvenlik üst bilgisi düzeni için dört modunu destekler.</span><span class="sxs-lookup"><span data-stu-id="31916-299">WCF supports all four modes for security header layout.</span></span> <span data-ttu-id="31916-300">Güvenlik üst bilgisi yapısı ve aşağıdaki kimlik doğrulama modları için ileti örnekleri "katı" modunu izler.</span><span class="sxs-lookup"><span data-stu-id="31916-300">Security header structure and message examples for authentication modes below follow the "Strict" mode.</span></span>  
  
## <a name="3-common-message-security-parameters"></a><span data-ttu-id="31916-301">3. ortak Ileti güvenlik parametreleri</span><span class="sxs-lookup"><span data-stu-id="31916-301">3. Common Message Security Parameters</span></span>  

 <span data-ttu-id="31916-302">Bu bölümde, istemci ve hizmet tarafından değiştirilen iletilerde güvenlik üst bilgi yapısını gösteren örneklerle birlikte her bir kimlik doğrulama modu için örnek ilkeler sağlanır.</span><span class="sxs-lookup"><span data-stu-id="31916-302">This section provides example policies for each authentication mode along with examples showing security header structure in messages exchanged by client and service.</span></span>  
  
### <a name="31-transport-protection"></a><span data-ttu-id="31916-303">3,1 taşıma koruması</span><span class="sxs-lookup"><span data-stu-id="31916-303">3.1 Transport Protection</span></span>  

 <span data-ttu-id="31916-304">WCF, iletileri korumak için güvenli aktarım kullanan beş kimlik doğrulama modu sağlar; UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport ve SspiNegotiatedOverTransport.</span><span class="sxs-lookup"><span data-stu-id="31916-304">WCF provides five authentication modes that use secure transport to protect messages; UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport and SspiNegotiatedOverTransport.</span></span>  
  
 <span data-ttu-id="31916-305">Bu kimlik doğrulama modları, SecurityPolicy ' de açıklanan aktarım bağlaması kullanılarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="31916-305">These authentication modes are constructed using the transport binding described in SecurityPolicy.</span></span> <span data-ttu-id="31916-306">UserNameOverTransport kimlik doğrulama modu için UsernameToken imzalı bir destekleme belirtecidir.</span><span class="sxs-lookup"><span data-stu-id="31916-306">For the UserNameOverTransport authentication mode the UsernameToken is a signed supporting token.</span></span> <span data-ttu-id="31916-307">Diğer kimlik doğrulama modlarında, belirteç imzalı bir onaylama belirteci olarak görünür.</span><span class="sxs-lookup"><span data-stu-id="31916-307">For the other authentication modes the token appears as a signed endorsing token.</span></span> <span data-ttu-id="31916-308">Ek C. 1.2 ve C. 1.3 SecurityPolicy, güvenlik üst bilgisi yerleşimini ayrıntılı olarak anlatmaktadır.</span><span class="sxs-lookup"><span data-stu-id="31916-308">Appendix C.1.2 and C.1.3 of SecurityPolicy describe the security header layout in detail.</span></span> <span data-ttu-id="31916-309">Aşağıdaki örnek güvenlik üstbilgileri, belirli bir kimlik doğrulama modu için katı düzeni gösterir.</span><span class="sxs-lookup"><span data-stu-id="31916-309">The following example security headers show the Strict layout for a given authentication mode.</span></span>  
  
 <span data-ttu-id="31916-310">Her durumda belirteçlerin "türetilmiş anahtarlar" özelliğinin değeri "false" şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="31916-310">The value of the "Derived Keys" property for the tokens in all cases is "false".</span></span>  
  
 <span data-ttu-id="31916-311">Aktarım bağlamasının çeşitli özelliklerinin değerleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="31916-311">The values of the various properties of the transport binding are as follows:</span></span>  
  
 <span data-ttu-id="31916-312">Zaman damgası: true</span><span class="sxs-lookup"><span data-stu-id="31916-312">Timestamp: true</span></span>  
  
 <span data-ttu-id="31916-313">Güvenlik üst bilgisi düzeni: katı</span><span class="sxs-lookup"><span data-stu-id="31916-313">Security Header Layout: Strict</span></span>  
  
 <span data-ttu-id="31916-314">Algoritma paketi: Basic256</span><span class="sxs-lookup"><span data-stu-id="31916-314">Algorithm Suite: Basic256</span></span>  
  
#### <a name="311-usernameovertransport"></a><span data-ttu-id="31916-315">3.1.1 UsernameOverTransport</span><span class="sxs-lookup"><span data-stu-id="31916-315">3.1.1 UsernameOverTransport</span></span>  

 <span data-ttu-id="31916-316">Bu kimlik doğrulama modu ile istemci, SOAP katmanında, her zaman başlatıcıdan alıcıya gönderilen imzalı bir destekleme belirteci olarak görünen bir Kullanıcı adı belirteci ile kimlik doğrular.</span><span class="sxs-lookup"><span data-stu-id="31916-316">With this authentication mode, the client authenticates with a Username Token which appears at the SOAP layer as a signed supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="31916-317">Hizmetin kimliği, aktarım katmanında bir X. 509.440 sertifikası kullanılarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="31916-317">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="31916-318">Kullanılan bağlama bir aktarım bağlamadır.</span><span class="sxs-lookup"><span data-stu-id="31916-318">The binding used is a transport binding.</span></span>  
  
 <span data-ttu-id="31916-319">İlke</span><span class="sxs-lookup"><span data-stu-id="31916-319">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="UserNameOverTransport_policy"><wsp:ExactlyOne><wsp:All><sp:TransportBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:TransportToken><wsp:Policy><sp:HttpsToken/></wsp:Policy></sp:TransportToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/></wsp:Policy></sp:TransportBinding><sp:SignedEncryptedSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:UsernameToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:WssUsernameToken10/></wsp:Policy></sp:UsernameToken></wsp:Policy></sp:SignedEncryptedSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
 <span data-ttu-id="31916-320">Güvenlik üst bilgisi düzeni</span><span class="sxs-lookup"><span data-stu-id="31916-320">Security Header Layout</span></span>  
  
 <span data-ttu-id="31916-321">İstek</span><span class="sxs-lookup"><span data-stu-id="31916-321">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="_0"> ... </u:Timestamp><o:UsernameToken u:Id="uuid-b96fbb3a-e646-4403-9473-2e5ffc733ff8-1"> ... </o:UsernameToken></o:Security>  
```  
  
 <span data-ttu-id="31916-322">Yanıt</span><span class="sxs-lookup"><span data-stu-id="31916-322">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="_0"> ... </u:Timestamp></o:Security>  
```  
  
#### <a name="312-certificateovertransport"></a><span data-ttu-id="31916-323">3.1.2 CertificateOverTransport</span><span class="sxs-lookup"><span data-stu-id="31916-323">3.1.2 CertificateOverTransport</span></span>  

 <span data-ttu-id="31916-324">Bu kimlik doğrulama modunda, istemci, her zaman başlatıcıdan alıcıya gönderilen bir onaylama destekleme belirteci olarak SOAP katmanında görünen bir X. 509.440 sertifikası kullanarak kimlik doğrular.</span><span class="sxs-lookup"><span data-stu-id="31916-324">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as an endorsing supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="31916-325">Hizmetin kimliği, aktarım katmanında bir X. 509.440 sertifikası kullanılarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="31916-325">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="31916-326">Kullanılan bağlama bir aktarım bağlamadır.</span><span class="sxs-lookup"><span data-stu-id="31916-326">The binding used is a transport binding.</span></span> <span data-ttu-id="31916-327">CertificateOverTransport SOAP gövdesini değil yalnızca SOAP üstbilgilerini imzalar.</span><span class="sxs-lookup"><span data-stu-id="31916-327">CertificateOverTransport only signs the SOAP headers, not the SOAP body.</span></span> <span data-ttu-id="31916-328">Bu, TransportWithMessageCredentials güvenlik modu tarafından kullanılan kimlik doğrulama modudur.</span><span class="sxs-lookup"><span data-stu-id="31916-328">This is the authentication mode used by the TransportWithMessageCredentials security mode.</span></span> <span data-ttu-id="31916-329">İleti kimlik bilgileri kullanılarak kimlik doğrulaması yapıldığından yalnızca SOAP üstbilgileri imzalanır.</span><span class="sxs-lookup"><span data-stu-id="31916-329">Only the SOAP headers are signed because authentication is done by using message credentials.</span></span>  
  
 <span data-ttu-id="31916-330">İlke</span><span class="sxs-lookup"><span data-stu-id="31916-330">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="CertificateOverTransport_policy"><wsp:ExactlyOne><wsp:All><sp:TransportBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:TransportToken><wsp:Policy><sp:HttpsToken/></wsp:Policy></sp:TransportToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/></wsp:Policy></sp:TransportBinding><sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token><sp:SignedParts><sp:Header Name="To" Namespace="http://www.w3.org/2005/08/addressing"/></sp:SignedParts></wsp:Policy></sp:EndorsingSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
 <span data-ttu-id="31916-331">Güvenlik üst bilgisi düzeni</span><span class="sxs-lookup"><span data-stu-id="31916-331">Security Header Layout</span></span>  
  
 <span data-ttu-id="31916-332">İstek</span><span class="sxs-lookup"><span data-stu-id="31916-332">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="_0"> ... </u:Timestamp><o:BinarySecurityToken> ... </o:BinarySecurityToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature></o:Security>  
```  
  
 <span data-ttu-id="31916-333">Yanıt</span><span class="sxs-lookup"><span data-stu-id="31916-333">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="_0"> ... </u:Timestamp></o:Security>  
```  
  
#### <a name="313-issuedtokenovertransport"></a><span data-ttu-id="31916-334">3.1.3 IssuedTokenOverTransport</span><span class="sxs-lookup"><span data-stu-id="31916-334">3.1.3 IssuedTokenOverTransport</span></span>  

 <span data-ttu-id="31916-335">Bu kimlik doğrulama modunda, istemci hizmette kimlik doğrulaması yapmaz, ancak bunun yerine güvenlik belirteci hizmeti (STS) tarafından verilen bir belirteç ve paylaşılan bir anahtar hakkında bilgi sahibi olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="31916-335">With this authentication mode the client does not authenticate to the service, as such, but rather presents a token issued by a Security Token Service (STS) and proves knowledge of a shared key.</span></span> <span data-ttu-id="31916-336">Verilen belirteç, her zaman başlatıcıdan alıcıya gönderilen bir onaylama destekleme belirteci olarak SOAP katmanında görünür.</span><span class="sxs-lookup"><span data-stu-id="31916-336">The issued token appears at the SOAP layer as an endorsing supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="31916-337">Hizmetin kimliği, aktarım katmanında bir X. 509.440 sertifikası kullanılarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="31916-337">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="31916-338">Bağlama bir aktarım bağlamadır.</span><span class="sxs-lookup"><span data-stu-id="31916-338">The binding is a transport binding.</span></span>  
  
 <span data-ttu-id="31916-339">İlke</span><span class="sxs-lookup"><span data-stu-id="31916-339">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="IssuedTokenOverTransport_policy">
 <wsp:ExactlyOne>
  <wsp:All>
   <sp:TransportBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702">
    <wsp:Policy>
     <sp:TransportToken>
      <wsp:Policy>
       <sp:HttpsToken />
      </wsp:Policy>
     </sp:TransportToken>
     <sp:AlgorithmSuite>
      <wsp:Policy>
       <sp:Basic256 />
      </wsp:Policy>
     </sp:AlgorithmSuite>
     <sp:Layout>
      <wsp:Policy>
       <sp:Strict/>
      </wsp:Policy>
     </sp:Layout>
     <sp:IncludeTimestamp/>
    </wsp:Policy>
   </sp:TransportBinding>
   <sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702">
    <wsp:Policy>
     <sp:IssuedToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient">
      <Issuer xmlns="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702">
       <Address xmlns="http://www.w3.org/2005/08/addressing">http://www.w3.org/2005/08/addressing/anonymous</Address>
       <Metadata xmlns="http://www.w3.org/2005/08/addressing">
        <Metadata xmlns="http://schemas.xmlsoap.org/ws/2004/09/mex" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
         <wsx:MetadataSection xmlns="">
          <wsx:MetadataReference>
           <Address xmlns="http://www.w3.org/2005/08/addressing"> ... </Address>
           <Identity xmlns="http://schemas.xmlsoap.org/ws/2006/02/addressingidentity">
            <Dns> ...  </Dns>
           </Identity>
          </wsx:MetadataReference>
         </wsx:MetadataSection>
        </Metadata>
       </Metadata>
      </Issuer>
      <sp:RequestSecurityTokenTemplate>
       <trust:KeyType xmlns:trust="http://docs.oasis-open.org/ws-sx/ws-trust/200512">http://docs.oasis-open.org/ws-sx/ws-trust/200512/SymmetricKey</trust:KeyType>
      </sp:RequestSecurityTokenTemplate>
      <wsp:Policy>
       <sp:RequireInternalReference/>
      </wsp:Policy>
     </sp:IssuedToken>
     <sp:SignedParts>
      <sp:Header Name="To" Namespace="http://www.w3.org/2005/08/addressing"/>
     </sp:SignedParts>
    </wsp:Policy>
   </sp:EndorsingSupportingTokens>
   <sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702">
    <wsp:Policy>
     <sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/>
     <sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/>
    </wsp:Policy>
   </sp:Wss11>
   <sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702">
    <wsp:Policy>
     <sp:MustSupportIssuedTokens/>
     <sp:RequireClientEntropy/>
     <sp:RequireServerEntropy/>
    </wsp:Policy>
   </sp:Trust13>
   <wsaw:UsingAddressing/>
  </wsp:All>
 </wsp:ExactlyOne>
</wsp:Policy>
```  
  
 <span data-ttu-id="31916-340">Güvenlik üst bilgisi düzeni</span><span class="sxs-lookup"><span data-stu-id="31916-340">Security Header Layout</span></span>  
  
 <span data-ttu-id="31916-341">İstek</span><span class="sxs-lookup"><span data-stu-id="31916-341">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-67692bb6-85b7-4299-8587-3ce60086b0d2-5"> ... </u:Timestamp><c:SecurityContextToken u:Id="uuid-fab7e1b2-8dc4-412b-bda9-b95a4f836815-16" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:SecurityContextToken><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="31916-342">Yanıt</span><span class="sxs-lookup"><span data-stu-id="31916-342">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-fab7e1b2-8dc4-412b-bda9-b95a4f836815-21"> ... </u:Timestamp><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
#### <a name="314-kerberosovertransport"></a><span data-ttu-id="31916-343">3.1.4 KerberosOverTransport</span><span class="sxs-lookup"><span data-stu-id="31916-343">3.1.4 KerberosOverTransport</span></span>  

 <span data-ttu-id="31916-344">Bu kimlik doğrulama modunda istemci Kerberos bileti kullanarak hizmeti doğrular.</span><span class="sxs-lookup"><span data-stu-id="31916-344">With this authentication mode the client authenticates to the service using a Kerberos ticket.</span></span> <span data-ttu-id="31916-345">Kerberos belirteci, SOAP katmanında bir onaylama destekleme belirteci olarak görünür.</span><span class="sxs-lookup"><span data-stu-id="31916-345">The Kerberos token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="31916-346">Hizmetin kimliği, aktarım katmanında bir X. 509.440 sertifikası kullanılarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="31916-346">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="31916-347">Bağlama bir aktarım bağlamadır.</span><span class="sxs-lookup"><span data-stu-id="31916-347">The binding is a transport binding.</span></span>  
  
 <span data-ttu-id="31916-348">İlke</span><span class="sxs-lookup"><span data-stu-id="31916-348">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="KerberosOverTransport_policy"><wsp:ExactlyOne><wsp:All><sp:TransportBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:TransportToken><wsp:Policy><sp:HttpsToken/></wsp:Policy></sp:TransportToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic128/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/></wsp:Policy></sp:TransportBinding><sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:KerberosToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Once"><wsp:Policy><sp:WssGssKerberosV5ApReqToken11/></wsp:Policy></sp:KerberosToken><sp:SignedParts><sp:Header Name="To" Namespace="http://www.w3.org/2005/08/addressing"/></sp:SignedParts></wsp:Policy></sp:EndorsingSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
 <span data-ttu-id="31916-349">Güvenlik üst bilgisi düzeni</span><span class="sxs-lookup"><span data-stu-id="31916-349">Security Header Layout</span></span>  
  
 <span data-ttu-id="31916-350">İstek</span><span class="sxs-lookup"><span data-stu-id="31916-350">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="_0"> ... </u:Timestamp><o:BinarySecurityToken> ... </o:BinarySecurityToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature></o:Security>  
```  
  
 <span data-ttu-id="31916-351">Yanıt</span><span class="sxs-lookup"><span data-stu-id="31916-351">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="_0"> ... </u:Timestamp></o:Security>  
```  
  
#### <a name="315-sspinegotiatedovertransport"></a><span data-ttu-id="31916-352">3.1.5 SspiNegotiatedOverTransport</span><span class="sxs-lookup"><span data-stu-id="31916-352">3.1.5 SspiNegotiatedOverTransport</span></span>  

 <span data-ttu-id="31916-353">Bu modda istemci ve sunucu kimlik doğrulamasını gerçekleştirmek için bir anlaşma protokolü kullanılır.</span><span class="sxs-lookup"><span data-stu-id="31916-353">With this mode a negotiation protocol is used to perform client and server authentication.</span></span> <span data-ttu-id="31916-354">Mümkünse, Kerberos kullanılır, aksi takdirde NTLM kullanılır.</span><span class="sxs-lookup"><span data-stu-id="31916-354">Kerberos is used if possible, otherwise NTLM.</span></span> <span data-ttu-id="31916-355">Elde edilen SCT, her zaman başlatıcıdan alıcıya gönderilen bir onaylama destekleme belirteci olarak SOAP katmanında görünür.</span><span class="sxs-lookup"><span data-stu-id="31916-355">The resulting SCT appears at the SOAP layer as an endorsing supporting token that is always sent from initiator to recipient.</span></span> <span data-ttu-id="31916-356">Ayrıca hizmet, aktarım katmanında bir X. 509.440 sertifikası tarafından da doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="31916-356">The service is additionally authenticated at the transport layer by an X.509 certificate.</span></span> <span data-ttu-id="31916-357">Kullanılan bağlama bir aktarım bağlamadır.</span><span class="sxs-lookup"><span data-stu-id="31916-357">The binding used is a transport binding.</span></span> <span data-ttu-id="31916-358">"SPNEGO" (anlaşma), WCF 'nin WS-Trust ile SSPI ikili anlaşma protokolünü nasıl kullandığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="31916-358">"SPNEGO" (negotiation) describes how WCF uses SSPI binary negotiation protocol with WS-Trust.</span></span> <span data-ttu-id="31916-359">Bu bölümdeki güvenlik üst bilgisi örnekleri, SPNEGO el sıkışma aracılığıyla SCT oluşturulduktan sonra verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="31916-359">Security header examples in this section are after the SCT has been established through the SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="31916-360">İlke</span><span class="sxs-lookup"><span data-stu-id="31916-360">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="SspiNegotiatedOverTransport_policy"><wsp:ExactlyOne><wsp:All><sp:TransportBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:TransportToken><wsp:Policy><sp:HttpsToken/></wsp:Policy></sp:TransportToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/></wsp:Policy></sp:TransportBinding><sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:SpnegoContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:MustNotSendCancel/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></sp:SpnegoContextToken><sp:SignedParts><sp:Header Name="To" Namespace="http://www.w3.org/2005/08/addressing"/></sp:SignedParts></wsp:Policy></sp:EndorsingSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples"></a><span data-ttu-id="31916-361">Güvenlik üst bilgisi örnekleri</span><span class="sxs-lookup"><span data-stu-id="31916-361">Security Header Examples</span></span>  

 <span data-ttu-id="31916-362">Güvenlik bağlamı belirteci WS-Trust Ikili anlaşma kullanılarak SPNEGO Handshake aracılığıyla kurulduktan sonra, uygulama iletilerinde aşağıdaki yapıyla güvenlik üst bilgileri bulunur.</span><span class="sxs-lookup"><span data-stu-id="31916-362">Once the Security Context Token is established through SPNEGO handshake using WS-Trust Binary Negotiation, the application messages have security headers with the following structure.</span></span>  
  
 <span data-ttu-id="31916-363">İstek</span><span class="sxs-lookup"><span data-stu-id="31916-363">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="_0"> ... </u:Timestamp><sc:SecurityContextToken u:Id="uuid-9a29d087-5dae-4d40-bf86-5746d9d30eca-1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:SecurityContextToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature></o:Security>  
```  
  
 <span data-ttu-id="31916-364">Yanıt</span><span class="sxs-lookup"><span data-stu-id="31916-364">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="_0"> ... </u:Timestamp></o:Security>  
```  
  
### <a name="32-using-x509-certificates-for-service-authentication"></a><span data-ttu-id="31916-365">Hizmet kimlik doğrulaması için X. 509.440 sertifikalarını kullanma 3,2</span><span class="sxs-lookup"><span data-stu-id="31916-365">3.2 Using X.509 Certificates for Service Authentication</span></span>  

 <span data-ttu-id="31916-366">Bu bölümde şu kimlik doğrulama modları açıklanmaktadır: Mulualcertificate WSS 1.0, karşılıklı CertificateDuplex, Mulualcertificate WSS 1.1, AnonymousForCertificate, UserNameForCertificate ve IssuedTokenForCertificate.</span><span class="sxs-lookup"><span data-stu-id="31916-366">This section describes the following authentication modes: MutualCertificate WSS1.0, Mutual CertificateDuplex, MutualCertificate WSS1.1, AnonymousForCertificate, UserNameForCertificate and IssuedTokenForCertificate.</span></span>  
  
#### <a name="321-mutualcertificate-wss10"></a><span data-ttu-id="31916-367">3.2.1 Mulualcertificate WSS 1.0</span><span class="sxs-lookup"><span data-stu-id="31916-367">3.2.1 MutualCertificate WSS1.0</span></span>  

 <span data-ttu-id="31916-368">Bu kimlik doğrulama modunda istemci, başlatıcı belirteci olarak SOAP katmanında görünen bir X. 509.440 sertifikası kullanarak kimlik doğrular.</span><span class="sxs-lookup"><span data-stu-id="31916-368">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as the initiator token.</span></span> <span data-ttu-id="31916-369">Ayrıca, hizmet bir X. 509.440 sertifikası kullanılarak doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="31916-369">The service is also authenticated using an X.509 certificate.</span></span> <span data-ttu-id="31916-370">SOAP üstbilgileri ve SOAP gövdesi her ikisi de imzalanır.</span><span class="sxs-lookup"><span data-stu-id="31916-370">Both the SOAP headers and the SOAP body are signed.</span></span> <span data-ttu-id="31916-371">Simetrik anahtar oluşturulur ve alıcı için aktarım sertifikasıyla şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="31916-371">A symmetric key is created and is encrypted with the transport certificate for the recipient.</span></span>  
  
 <span data-ttu-id="31916-372">Kullanılan bağlama, aşağıdaki özellik değerleriyle asimetrik bir bağlamadır:</span><span class="sxs-lookup"><span data-stu-id="31916-372">The binding used is an asymmetric binding with the following property values:</span></span>  
  
 <span data-ttu-id="31916-373">Başlatıcı belirteci: ekleme modu. ../IncludeToken/AlwaysToRecipient olarak ayarlanan istemcinin X. 509.440 sertifikası</span><span class="sxs-lookup"><span data-stu-id="31916-373">Initiator Token: the client’s X.509 certificate, with inclusion mode set to .../IncludeToken/AlwaysToRecipient</span></span>  
  
 <span data-ttu-id="31916-374">Alıcı belirteci: sunucu X. 509.440 sertifikası, dahil etme modu ayarlandı. ../Includetoken/No</span><span class="sxs-lookup"><span data-stu-id="31916-374">Recipient Token: Server’s X.509 Certificate, with inclusion mode is set .../IncludeToken/Never</span></span>  
  
 <span data-ttu-id="31916-375">Belirteç koruması: false</span><span class="sxs-lookup"><span data-stu-id="31916-375">Token Protection: False</span></span>  
  
 <span data-ttu-id="31916-376">Tüm başlık ve gövde Imzaları: doğru</span><span class="sxs-lookup"><span data-stu-id="31916-376">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="31916-377">Koruma sırası: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="31916-377">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="31916-378">Imzayı şifreleyin: doğru</span><span class="sxs-lookup"><span data-stu-id="31916-378">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="31916-379">İlke</span><span class="sxs-lookup"><span data-stu-id="31916-379">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="MutualCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:AsymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:InitiatorToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:InitiatorToken><sp:RecipientToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:RecipientToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:AsymmetricBinding><sp:Wss10 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/></wsp:Policy></sp:Wss10><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="31916-380">Güvenlik üst bilgisi örnekleri: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="31916-380">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="31916-381">İstek</span><span class="sxs-lookup"><span data-stu-id="31916-381">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-39cb393e-9da8-4d5d-b273-540ef614569b-1"> ... </u:Timestamp><o:BinarySecurityToken> ... </o:BinarySecurityToken><e:EncryptedKey Id="_0" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><e:EncryptedData Id="_7" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="31916-382">Yanıt</span><span class="sxs-lookup"><span data-stu-id="31916-382">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"> <u:Timestamp u:Id="uuid-3d742930-70d3-4d7e-aa0a-8721128dc115-8"> ... </u:Timestamp><e:EncryptedKey Id="_0" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><e:EncryptedData Id="_5" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="31916-383">İlke</span><span class="sxs-lookup"><span data-stu-id="31916-383">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="MutualCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:AsymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:InitiatorToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:InitiatorToken><sp:RecipientToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:RecipientToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:AsymmetricBinding><sp:Wss10 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/></wsp:Policy></sp:Wss10><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="31916-384">Güvenlik üst bilgisi örnekleri: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="31916-384">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="31916-385">İstek</span><span class="sxs-lookup"><span data-stu-id="31916-385">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-73da3e21-abff-4294-a910-e75303d280cc-1"> ... </u:Timestamp><o:BinarySecurityToken> ... </o:BinarySecurityToken><e:EncryptedKey Id="_0" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
 <span data-ttu-id="31916-386">Yanıt</span><span class="sxs-lookup"><span data-stu-id="31916-386">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-02f276b6-804f-480d-99e9-2e90fc76ab27-3"> ... </u:Timestamp><e:EncryptedKey Id="_0" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
#### <a name="322-mutualcertificateduplex"></a><span data-ttu-id="31916-387">3.2.2 Mulualcertificateduplex</span><span class="sxs-lookup"><span data-stu-id="31916-387">3.2.2 MutualCertificateDuplex</span></span>  

 <span data-ttu-id="31916-388">Bu kimlik doğrulama modunda istemci, başlatıcı belirteci olarak SOAP katmanında görünen bir X. 509.440 sertifikası kullanarak kimlik doğrular.</span><span class="sxs-lookup"><span data-stu-id="31916-388">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as the initiator token.</span></span> <span data-ttu-id="31916-389">Ayrıca, hizmet bir X. 509.440 sertifikası kullanılarak doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="31916-389">The service is also authenticated using an X.509 certificate.</span></span>  
  
 <span data-ttu-id="31916-390">Kullanılan bağlama, aşağıdaki özellik değerleriyle asimetrik bir bağlamadır:</span><span class="sxs-lookup"><span data-stu-id="31916-390">The binding used is an asymmetric binding with the following property values:</span></span>  
  
 <span data-ttu-id="31916-391">Başlatıcı belirteci: Istemcinin x509 sertifikası, ekleme modu. ../IncludeToken/AlwaysToRecipient olarak ayarlandı</span><span class="sxs-lookup"><span data-stu-id="31916-391">Initiator Token: Client’s X509 Certificate, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
  
 <span data-ttu-id="31916-392">Alıcı belirteci: sunucunun x509 sertifikası, dahil etme modu. ../ıncludetoken/AlwaysToInitiator olarak ayarlandı</span><span class="sxs-lookup"><span data-stu-id="31916-392">Recipient Token: Server’s X509 Certificate, inclusion mode is set to .../IncludeToken/AlwaysToInitiator</span></span>  
  
 <span data-ttu-id="31916-393">Belirteç koruması: false</span><span class="sxs-lookup"><span data-stu-id="31916-393">Token Protection: False</span></span>  
  
 <span data-ttu-id="31916-394">Tüm başlık ve gövde Imzaları: doğru</span><span class="sxs-lookup"><span data-stu-id="31916-394">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="31916-395">Koruma sırası: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="31916-395">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="31916-396">Imzayı şifreleyin: doğru</span><span class="sxs-lookup"><span data-stu-id="31916-396">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="31916-397">İlke</span><span class="sxs-lookup"><span data-stu-id="31916-397">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="MutualCertificateDuplex_policy"><wsp:ExactlyOne><wsp:All><sp:AsymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:InitiatorToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:InitiatorToken><sp:RecipientToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToInitiator"><wsp:Policy><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:RecipientToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:AsymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><cdp:CompositeDuplex xmlns:cdp="http://schemas.microsoft.com/net/2006/06/duplex"/><ow:OneWay xmlns:ow="http://schemas.microsoft.com/ws/2005/05/routing/policy"/><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="31916-398">Güvenlik üst bilgisi örnekleri: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="31916-398">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="31916-399">İstek ve yanıt</span><span class="sxs-lookup"><span data-stu-id="31916-399">Request and Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-4dec3da4-b572-4654-ba4d-4a2f84a87510-1"> ... </u:Timestamp><o:BinarySecurityToken> ... </o:BinarySecurityToken><e:EncryptedKey Id="_0" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><e:EncryptedData Id="_7" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="31916-400">İlke</span><span class="sxs-lookup"><span data-stu-id="31916-400">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="MutualCertificateDuplex_policy"><wsp:ExactlyOne><wsp:All><sp:AsymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:InitiatorToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:InitiatorToken><sp:RecipientToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToInitiator"><wsp:Policy><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:RecipientToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:AsymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><cdp:CompositeDuplex xmlns:cdp="http://schemas.microsoft.com/net/2006/06/duplex"/><ow:OneWay xmlns:ow="http://schemas.microsoft.com/ws/2005/05/routing/policy"/><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="31916-401">Güvenlik üst bilgisi örnekleri: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="31916-401">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="31916-402">İstek ve yanıt</span><span class="sxs-lookup"><span data-stu-id="31916-402">Request and Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-b0e23feb-cd2d-4dc1-bad9-284bc45f3be3-1"> ... </u:Timestamp><o:BinarySecurityToken> ... </o:BinarySecurityToken><e:EncryptedKey Id="_0" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
#### <a name="323-using-symmetricbinding-with-x509-service-authentication"></a><span data-ttu-id="31916-403">X. 509.440 hizmeti kimlik doğrulamasıyla SymmetricBinding kullanarak 3.2.3</span><span class="sxs-lookup"><span data-stu-id="31916-403">3.2.3 Using SymmetricBinding with X.509 Service Authentication</span></span>  

 <span data-ttu-id="31916-404">"WSS10", x509 belirteçleri olan senaryolar için sınırlı destek sağlamıştır.</span><span class="sxs-lookup"><span data-stu-id="31916-404">"WSS10" provided limited support for scenarios with X509 tokens.</span></span> <span data-ttu-id="31916-405">Örneğin, yalnızca Service x509 belirtecini kullanan iletiler için imza ve şifreleme koruması sağlanması mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="31916-405">For example, there was no way to provide signature and encryption protection for messages using only service X509 token.</span></span> <span data-ttu-id="31916-406">"WSS11", EncryptedKey öğesinin kullanımını simetrik bir belirteç olarak getirdi.</span><span class="sxs-lookup"><span data-stu-id="31916-406">"WSS11" introduced the usage of EncryptedKey as a symmetric token.</span></span> <span data-ttu-id="31916-407">Artık hem istek hem de yanıt iletileri koruması için hizmetin X. 509.440 sertifikası için şifrelenmiş bir geçici anahtar kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="31916-407">Now a temporary key encrypted for the service's X.509 certificate could be used for both request and response messages protection.</span></span> <span data-ttu-id="31916-408">Aşağıdaki 3,4 bölümünde açıklanan kimlik doğrulama modları bu kalıbı kullanır.</span><span class="sxs-lookup"><span data-stu-id="31916-408">The authentication modes described in the section 3.4 below use this pattern.</span></span>  
  
 <span data-ttu-id="31916-409">WS-SecurityPolicy, koruma belirteci olarak Service x509 belirteci ile SymmetricBinding kullanarak bu kalıbı açıklar.</span><span class="sxs-lookup"><span data-stu-id="31916-409">WS-SecurityPolicy describes this pattern using SymmetricBinding with Service X509 token as the protection token.</span></span>  
  
 <span data-ttu-id="31916-410">Kimlik doğrulama modları AnonymousForCertificate, UsernameForCertificate, Mulualcertificate WSS11 ve IssuedTokenForCertificate All, aşağıdaki özellik değerleriyle benzer bir SP: SymmetricBinding örneği kullanır:</span><span class="sxs-lookup"><span data-stu-id="31916-410">Authentication modes AnonymousForCertificate, UsernameForCertificate, MutualCertificate WSS11 and IssuedTokenForCertificate all use a similar instance of sp:SymmetricBinding with the following property values:</span></span>  
  
 <span data-ttu-id="31916-411">Koruma belirteci: sunucunun x509 sertifikası, içerme modu olarak ayarlandı. ../Includetoken/hiçbir</span><span class="sxs-lookup"><span data-stu-id="31916-411">Protection Token: Server’s X509 Certificate, inclusion mode is set to .../IncludeToken/Never</span></span>  
<span data-ttu-id="31916-412">Belirteç koruması: false</span><span class="sxs-lookup"><span data-stu-id="31916-412">Token Protection: False</span></span>  
  
 <span data-ttu-id="31916-413">Tüm başlık ve gövde Imzaları: doğru</span><span class="sxs-lookup"><span data-stu-id="31916-413">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="31916-414">Koruma sırası: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="31916-414">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="31916-415">Imzayı şifreleyin: doğru</span><span class="sxs-lookup"><span data-stu-id="31916-415">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="31916-416">Yukarıdaki kimlik doğrulama modları yalnızca kullandıkları destekleyici belirteçlere göre farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="31916-416">The above authentication modes only differ by the supporting tokens they use.</span></span> <span data-ttu-id="31916-417">AnonymousForCertificate 'ın herhangi bir destekleme belirteci yoktur; çoklu Uıcertificate WSS 1,1 'nin istemcinin x509 sertifikası, destekleme belirteçleri onaylama olarak, UserNameForCertificate imzalı bir destekleme belirteci olarak bir Kullanıcı adı belirtecine sahiptir ve IssuedTokenForCertificate, verilen belirtece bir onaylama destekleme belirteci olarak sahiptir.</span><span class="sxs-lookup"><span data-stu-id="31916-417">AnonymousForCertificate does not have any supporting tokens, MutualCertificate WSS 1.1 has the client’s X509 certificate as an endorsing supporting tokens, UserNameForCertificate has a UserName Token as a signed supporting token and IssuedTokenForCertificate has the issued token as an endorsing supporting token.</span></span>  
  
#### <a name="324-anonymousforcertificate"></a><span data-ttu-id="31916-418">3.2.4 AnonymousForCertificate</span><span class="sxs-lookup"><span data-stu-id="31916-418">3.2.4 AnonymousForCertificate</span></span>  

 <span data-ttu-id="31916-419">Bu kimlik doğrulama modunda, istemci anonimdir ve hizmetin kimliği bir X. 509.440 sertifikası kullanılarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="31916-419">With this authentication mode the client is anonymous and the service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="31916-420">Kullanılan bağlama, 3.4.2 içinde açıklandığı gibi simetrik bağlamanın bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="31916-420">The binding used is an instance of symmetric binding as described in 3.4.2.</span></span>  
  
 <span data-ttu-id="31916-421">İlke</span><span class="sxs-lookup"><span data-stu-id="31916-421">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="AnonymousforCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/><sp:RequireSignatureConfirmation/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="31916-422">Güvenlik üst bilgisi örnekleri: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="31916-422">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="31916-423">İstek</span><span class="sxs-lookup"><span data-stu-id="31916-423">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-4de2d2a1-6266-4a02-93e6-242a1ac2aeb3-2"> ... </u:Timestamp><e:EncryptedKey Id="uuid-4de2d2a1-6266-4a02-93e6-242a1ac2aeb3-1" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="31916-424">Yanıt</span><span class="sxs-lookup"><span data-stu-id="31916-424">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-b06cb481-3176-4c56-af35-c38252bb6c78-4"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_2" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData><e:EncryptedData Id="_7" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="31916-425">İlke</span><span class="sxs-lookup"><span data-stu-id="31916-425">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="AnonymousforCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/><sp:RequireSignatureConfirmation/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="31916-426">Güvenlik üst bilgisi örnekleri: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="31916-426">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="31916-427">İstek</span><span class="sxs-lookup"><span data-stu-id="31916-427">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-562aac68-8cdd-45d5-bc03-df662e6ed048-2"> ... </u:Timestamp><e:EncryptedKey Id="uuid-562aac68-8cdd-45d5-bc03-df662e6ed048-1" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
 <span data-ttu-id="31916-428">Yanıt</span><span class="sxs-lookup"><span data-stu-id="31916-428">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-15b48260-23da-424d-8dc4-8f4e150fb8cf-3"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><k:SignatureConfirmation u:Id="_2" Value="ALF+QNGmWn2k3LpWEDIzSBgTkvo=" xmlns:k="http://docs.oasis-open.org/wss/oasis-wss-wssecurity-secext-1.1.xsd"></k:SignatureConfirmation><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
#### <a name="325-usernameforcertificate"></a><span data-ttu-id="31916-429">3.2.5 UserNameForCertificate</span><span class="sxs-lookup"><span data-stu-id="31916-429">3.2.5 UserNameForCertificate</span></span>  

 <span data-ttu-id="31916-430">Bu kimlik doğrulama modunda istemci, SOAP katmanında imzalı destekleyici belirteç olarak görünen bir Kullanıcı adı belirteci kullanarak hizmette kimlik doğrulaması yapar.</span><span class="sxs-lookup"><span data-stu-id="31916-430">With this authentication mode the client authenticates to the service using a Username Token which appears at the SOAP layer as a signed supporting token.</span></span> <span data-ttu-id="31916-431">Hizmet, bir X. 509.440 sertifikası kullanarak istemcinin kimliğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="31916-431">The service authenticates to the client using an X.509 certificate.</span></span> <span data-ttu-id="31916-432">Kullanılan bağlama, koruma belirtecinin istemci tarafından oluşturulan ve hizmetin ortak anahtarıyla şifrelenen bir anahtar olduğu simetrik bir bağlamadır.</span><span class="sxs-lookup"><span data-stu-id="31916-432">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="31916-433">İlke</span><span class="sxs-lookup"><span data-stu-id="31916-433">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="UserNameForCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:SignedEncryptedSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:UsernameToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:WssUsernameToken10/></wsp:Policy></sp:UsernameToken></wsp:Policy></sp:SignedEncryptedSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><http:BasicAuthentication xmlns:http="http://schemas.microsoft.com/ws/06/2004/policy/http"/><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="31916-434">Güvenlik üst bilgisi örnekleri: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="31916-434">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="31916-435">İstek</span><span class="sxs-lookup"><span data-stu-id="31916-435">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-27196139-acb9-410f-a2c6-51d20d24278b-2"> ... </u:Timestamp><e:EncryptedKey Id="uuid-27196139-acb9-410f-a2c6-51d20d24278b-1" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_9" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="31916-436">Yanıt</span><span class="sxs-lookup"><span data-stu-id="31916-436">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-681226f7-126a-4806-b732-fcca097cd7a8-5"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="31916-437">İlke</span><span class="sxs-lookup"><span data-stu-id="31916-437">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="UserNameForCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:SignedEncryptedSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:UsernameToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:WssUsernameToken10/></wsp:Policy></sp:UsernameToken></wsp:Policy></sp:SignedEncryptedSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><http:BasicAuthentication xmlns:http="http://schemas.microsoft.com/ws/06/2004/policy/http"/><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="31916-438">Güvenlik üst bilgisi örnekleri: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="31916-438">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="31916-439">İstek</span><span class="sxs-lookup"><span data-stu-id="31916-439">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-8276d8b7-74a0-4257-b8a5-e25350e7c2d4-2"> ... </u:Timestamp><e:EncryptedKey Id="uuid-8276d8b7-74a0-4257-b8a5-e25350e7c2d4-1" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
 <span data-ttu-id="31916-440">Yanıt</span><span class="sxs-lookup"><span data-stu-id="31916-440">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-8a7ad353-f071-49dc-90dd-5ad2e9abd40a-4"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
#### <a name="326-mutualcertificate-wss-11"></a><span data-ttu-id="31916-441">3.2.6 Mulualcertificate (WSS 1,1)</span><span class="sxs-lookup"><span data-stu-id="31916-441">3.2.6 MutualCertificate (WSS 1.1)</span></span>  

 <span data-ttu-id="31916-442">Bu kimlik doğrulama modunda istemci, SOAP katmanında bir destekleme desteği belirteci olarak görünen bir X. 509.440 sertifikası kullanarak kimlik doğrular.</span><span class="sxs-lookup"><span data-stu-id="31916-442">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="31916-443">Ayrıca, hizmet bir X. 509.440 sertifikası kullanılarak doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="31916-443">The service is also authenticated using an X.509 certificate.</span></span> <span data-ttu-id="31916-444">Kullanılan bağlama, koruma belirtecinin istemci tarafından oluşturulan ve hizmetin ortak anahtarıyla şifrelenen bir anahtar olduğu simetrik bir bağlamadır.</span><span class="sxs-lookup"><span data-stu-id="31916-444">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="31916-445">İlke</span><span class="sxs-lookup"><span data-stu-id="31916-445">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="MutualCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:EndorsingSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/><sp:RequireSignatureConfirmation/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="31916-446">Güvenlik üst bilgisi örnekleri: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="31916-446">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="31916-447">İstek</span><span class="sxs-lookup"><span data-stu-id="31916-447">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-75305d4e-f54f-4e36-9de9-45b6d2053c80-2"> ... </u:Timestamp><e:EncryptedKey Id="uuid-75305d4e-f54f-4e36-9de9-45b6d2053c80-1" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_2" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><o:BinarySecurityToken> ...</o:BinarySecurityToken><e:EncryptedData Id="_9" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData><e:EncryptedData Id="_10" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="31916-448">Yanıt</span><span class="sxs-lookup"><span data-stu-id="31916-448">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-8c73fa91-f95b-40ff-b088-48118e6fadcf-5"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_3" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_9" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData><e:EncryptedData Id="_10" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="31916-449">İlke</span><span class="sxs-lookup"><span data-stu-id="31916-449">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="MutualCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:EndorsingSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/><sp:RequireSignatureConfirmation/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="31916-450">Güvenlik üst bilgisi örnekleri: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="31916-450">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="31916-451">İstek</span><span class="sxs-lookup"><span data-stu-id="31916-451">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-0b940a9e-606f-43b9-b05d-a162043529bc-2"> ... </u:Timestamp><e:EncryptedKey Id="uuid-0b940a9e-606f-43b9-b05d-a162043529bc-1" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><o:BinarySecurityToken> ... </o:BinarySecurityToken><Signature Id="_2" xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
 <span data-ttu-id="31916-452">Yanıt</span><span class="sxs-lookup"><span data-stu-id="31916-452">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-67dacc31-4a50-4866-b673-ccc03e156337-3"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><k:SignatureConfirmation u:Id="_2" Value="mYyksUQKkK27Fd6hmgOiqFwvudk=" xmlns:k="http://docs.oasis-open.org/wss/oasis-wss-wssecurity-secext-1.1.xsd"></k:SignatureConfirmation><k:SignatureConfirmation u:Id="_3" Value="SreOZ4Rr2BcXjFQFvgN55ERypI/1/86hdWThE5lav0eYIxF1OCzQgZF+y7cQ82t+g3CRnLbE3c52DqMpY/HXlrdMct3m3rnpDH+fqdhNY4fE+M2v4zUMFR7uxDKWcEm9zZpmUvJCDfJRfKRaKjy5cTbccRKqSxw7HAqOYnqibA4=" xmlns:k="http://docs.oasis-open.org/wss/oasis-wss-wssecurity-secext-1.1.xsd"></k:SignatureConfirmation><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
#### <a name="327-issuedtokenforcertificate"></a><span data-ttu-id="31916-453">3.2.7 IssuedTokenForCertificate</span><span class="sxs-lookup"><span data-stu-id="31916-453">3.2.7 IssuedTokenForCertificate</span></span>  

 <span data-ttu-id="31916-454">Bu kimlik doğrulama modunda istemci, bu şekilde hizmette kimlik doğrulaması yapmaz, ancak bunun yerine STS tarafından verilen bir belirteç ve paylaşılan anahtar hakkında bilgi sahibi olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="31916-454">With this authentication mode the client does not authenticate to the service, as such, but instead presents a token issued by a STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="31916-455">Verilen belirteç, SOAP katmanında bir onaylama destekleme belirteci olarak görünür.</span><span class="sxs-lookup"><span data-stu-id="31916-455">The issued token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="31916-456">Hizmet, bir X. 509.440 sertifikası kullanarak istemcinin kimliğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="31916-456">The service authenticates to the client using an X.509 certificate.</span></span> <span data-ttu-id="31916-457">Kullanılan bağlama, koruma belirtecinin istemci tarafından oluşturulan ve hizmetin ortak anahtarıyla şifrelenen bir anahtar olduğu simetrik bir bağlamadır.</span><span class="sxs-lookup"><span data-stu-id="31916-457">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="31916-458">İlke</span><span class="sxs-lookup"><span data-stu-id="31916-458">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="IssuedTokenForCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:IssuedToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><Issuer xmlns="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><Address xmlns="http://www.w3.org/2005/08/addressing">http://www.w3.org/2005/08/addressing/anonymous</Address><Metadata xmlns="http://www.w3.org/2005/08/addressing"><Metadata xmlns="http://schemas.xmlsoap.org/ws/2004/09/mex" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"><wsx:MetadataSection xmlns=""><wsx:MetadataReference><Address xmlns="http://www.w3.org/2005/08/addressing"> ... </Address><Identity xmlns="http://schemas.xmlsoap.org/ws/2006/02/addressingidentity"><Dns> ...  </Dns></Identity></wsx:MetadataReference></wsx:MetadataSection></Metadata></Metadata></Issuer><sp:RequestSecurityTokenTemplate><trust:KeyType xmlns:trust="http://docs.oasis-open.org/ws-sx/ws-trust/200512">http://docs.oasis-open.org/ws-sx/ws-trust/200512/SymmetricKey</trust:KeyType></sp:RequestSecurityTokenTemplate><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireInternalReference/></wsp:Policy></sp:IssuedToken></wsp:Policy></sp:EndorsingSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/><sp:RequireSignatureConfirmation/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="31916-459">Güvenlik üst bilgisi örnekleri: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="31916-459">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="31916-460">İstek</span><span class="sxs-lookup"><span data-stu-id="31916-460">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-1d2c03e6-0b69-4483-903a-6ef9b9d286ed-5"> ... </u:Timestamp><c:SecurityContextToken u:Id="uuid-3f0f57fa-046d-40c0-919f-d0d7aa640b9f-1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:SecurityContextToken><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="31916-461">Yanıt</span><span class="sxs-lookup"><span data-stu-id="31916-461">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-3f0f57fa-046d-40c0-919f-d0d7aa640b9f-6"> ... </u:Timestamp><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="31916-462">Güvenlik üst bilgisi örnekleri: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="31916-462">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="31916-463">İlke</span><span class="sxs-lookup"><span data-stu-id="31916-463">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="IssuedTokenForCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:IssuedToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><Issuer xmlns="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><Address xmlns="http://www.w3.org/2005/08/addressing">http://www.w3.org/2005/08/addressing/anonymous</Address><Metadata xmlns="http://www.w3.org/2005/08/addressing"><Metadata xmlns="http://schemas.xmlsoap.org/ws/2004/09/mex" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"><wsx:MetadataSection xmlns=""><wsx:MetadataReference><Address xmlns="http://www.w3.org/2005/08/addressing"> ... </Address><Identity xmlns="http://schemas.xmlsoap.org/ws/2006/02/addressingidentity"><Dns> ...  </Dns></Identity></wsx:MetadataReference></wsx:MetadataSection></Metadata></Metadata></Issuer><sp:RequestSecurityTokenTemplate><trust:KeyType xmlns:trust="http://docs.oasis-open.org/ws-sx/ws-trust/200512">http://docs.oasis-open.org/ws-sx/ws-trust/200512/SymmetricKey</trust:KeyType></sp:RequestSecurityTokenTemplate><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireInternalReference/></wsp:Policy></sp:IssuedToken></wsp:Policy></sp:EndorsingSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/><sp:RequireSignatureConfirmation/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
 <span data-ttu-id="31916-464">İstek</span><span class="sxs-lookup"><span data-stu-id="31916-464">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-de1c51aa-2ecc-4e70-b6bd-9dca58331fa7-5"> ... </u:Timestamp><c:SecurityContextToken u:Id="uuid-96c5e80a-9b87-4c6f-af77-752ca65cf607-16" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:SecurityContextToken><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="31916-465">Yanıt</span><span class="sxs-lookup"><span data-stu-id="31916-465">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-96c5e80a-9b87-4c6f-af77-752ca65cf607-21"> ... </u:Timestamp><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
## <a name="33-kerberos"></a><span data-ttu-id="31916-466">3,3 Kerberos</span><span class="sxs-lookup"><span data-stu-id="31916-466">3.3 Kerberos</span></span>  

 <span data-ttu-id="31916-467">Bu kimlik doğrulama modunda istemci Kerberos bileti kullanarak hizmeti doğrular.</span><span class="sxs-lookup"><span data-stu-id="31916-467">With this authentication mode the client authenticates to the service using a Kerberos ticket.</span></span> <span data-ttu-id="31916-468">Aynı bilet aynı zamanda sunucu kimlik doğrulaması da sağlar.</span><span class="sxs-lookup"><span data-stu-id="31916-468">That same ticket also provides server authentication.</span></span> <span data-ttu-id="31916-469">Kullanılan bağlama, aşağıdaki özelliklerle simetrik bir bağlamadır;</span><span class="sxs-lookup"><span data-stu-id="31916-469">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="31916-470">Koruma belirteci: Kerberos bileti, ekleme modu. ../IncludeToken/Once olarak ayarlandı</span><span class="sxs-lookup"><span data-stu-id="31916-470">Protection Token: Kerberos Ticket, inclusion mode is set to .../IncludeToken/Once</span></span>  
<span data-ttu-id="31916-471">Belirteç koruması: false</span><span class="sxs-lookup"><span data-stu-id="31916-471">Token Protection: False</span></span>  
  
 <span data-ttu-id="31916-472">Tüm başlık ve gövde Imzaları: doğru</span><span class="sxs-lookup"><span data-stu-id="31916-472">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="31916-473">Koruma sırası: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="31916-473">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="31916-474">Imzayı şifreleyin: doğru</span><span class="sxs-lookup"><span data-stu-id="31916-474">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="31916-475">İlke</span><span class="sxs-lookup"><span data-stu-id="31916-475">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="Kerberos_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:KerberosToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Once"><wsp:Policy><sp:RequireDerivedKeys/><sp:WssGssKerberosV5ApReqToken11/></wsp:Policy></sp:KerberosToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic128/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="31916-476">Güvenlik üst bilgisi örnekleri: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="31916-476">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="31916-477">İstek</span><span class="sxs-lookup"><span data-stu-id="31916-477">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-e8f6dc3b-407d-4387-bd33-97aedfd8bf13-2"> ... </u:Timestamp><o:BinarySecurityToken> ... </o:BinarySecurityToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="31916-478">Yanıt</span><span class="sxs-lookup"><span data-stu-id="31916-478">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-7b03568e-66ae-49da-82ee-5d12d372876e-3"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="31916-479">İlke</span><span class="sxs-lookup"><span data-stu-id="31916-479">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="Kerberos_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:KerberosToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Once"><wsp:Policy><sp:RequireDerivedKeys/><sp:WssGssKerberosV5ApReqToken11/></wsp:Policy></sp:KerberosToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic128/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="31916-480">Güvenlik üst bilgisi örnekleri: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="31916-480">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="31916-481">İstek</span><span class="sxs-lookup"><span data-stu-id="31916-481">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-d29247f0-f220-4e81-9a8d-a15f5ac31072-2"> ... </u:Timestamp><o:BinarySecurityToken> ... </o:BinarySecurityToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
 <span data-ttu-id="31916-482">Yanıt</span><span class="sxs-lookup"><span data-stu-id="31916-482">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-9025b930-4f15-42fe-8e78-35d3a3480177-2"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
#### <a name="34-issuedtoken"></a><span data-ttu-id="31916-483">3,4 IssuedToken</span><span class="sxs-lookup"><span data-stu-id="31916-483">3.4 IssuedToken</span></span>  

 <span data-ttu-id="31916-484">Bu kimlik doğrulama modunda, istemci hizmette kimlik doğrulaması yapmaz, bunun yerine istemci, STS tarafından verilen bir belirteç ve paylaşılan bir anahtar hakkında bilgi sahibi olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="31916-484">With this authentication mode the client does not authenticate to the service, as such, rather the client presents a token issued by an STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="31916-485">Bu hizmet, istemci tarafından kimlik doğrulaması değil, bu nedenle, STS, paylaşılan anahtarı yalnızca hizmetin şifresini çözebilmesini sağlayan, verilen belirtecin bir parçası olarak şifreler.</span><span class="sxs-lookup"><span data-stu-id="31916-485">The service is not authenticated to the client, as such, instead the STS encrypts the shared key as part of the issued token such that only the service can decrypt the key.</span></span> <span data-ttu-id="31916-486">Kullanılan bağlama, aşağıdaki özelliklerle simetrik bağlama olarak verilmiştir;</span><span class="sxs-lookup"><span data-stu-id="31916-486">The binding used is as symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="31916-487">Koruma belirteci: verilen belirteç, ekleme modu. ../IncludeToken/AlwaysToRecipient olarak ayarlandı</span><span class="sxs-lookup"><span data-stu-id="31916-487">Protection Token: Issued Token, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
<span data-ttu-id="31916-488">Belirteç koruması: false</span><span class="sxs-lookup"><span data-stu-id="31916-488">Token Protection: False</span></span>  
  
 <span data-ttu-id="31916-489">Tüm başlık ve gövde Imzaları: doğru</span><span class="sxs-lookup"><span data-stu-id="31916-489">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="31916-490">Koruma sırası: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="31916-490">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="31916-491">Imzayı şifreleyin: doğru</span><span class="sxs-lookup"><span data-stu-id="31916-491">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="31916-492">İlke</span><span class="sxs-lookup"><span data-stu-id="31916-492">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="IssuedToken_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:IssuedToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><Issuer xmlns="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><Address xmlns="http://www.w3.org/2005/08/addressing">http://www.w3.org/2005/08/addressing/anonymous</Address><Metadata xmlns="http://www.w3.org/2005/08/addressing"><Metadata xmlns="http://schemas.xmlsoap.org/ws/2004/09/mex" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"><wsx:MetadataSection xmlns=""><wsx:MetadataReference><Address xmlns="http://www.w3.org/2005/08/addressing"> ... </Address><Identity xmlns="http://schemas.xmlsoap.org/ws/2006/02/addressingidentity"><Dns> ...  </Dns></Identity></wsx:MetadataReference></wsx:MetadataSection></Metadata></Metadata></Issuer><sp:RequestSecurityTokenTemplate><trust:KeyType xmlns:trust="http://docs.oasis-open.org/ws-sx/ws-trust/200512">http://docs.oasis-open.org/ws-sx/ws-trust/200512/SymmetricKey</trust:KeyType></sp:RequestSecurityTokenTemplate><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireInternalReference/></wsp:Policy></sp:IssuedToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="31916-493">Güvenlik üst bilgisi örnekleri: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="31916-493">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="31916-494">İstek</span><span class="sxs-lookup"><span data-stu-id="31916-494">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-61ce3989-bc38-4d67-8262-6232c9d49a26-5"> ... </u:Timestamp><c:SecurityContextToken u:Id="uuid-7e2d2617-1c28-465a-be30-de4a78cfc0e2-1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:SecurityContextToken><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="31916-495">Yanıt</span><span class="sxs-lookup"><span data-stu-id="31916-495">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-7e2d2617-1c28-465a-be30-de4a78cfc0e2-6"> ... </u:Timestamp><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>
```  
  
 <span data-ttu-id="31916-496">İlke</span><span class="sxs-lookup"><span data-stu-id="31916-496">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="IssuedToken_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:IssuedToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><Issuer xmlns="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><Address xmlns="http://www.w3.org/2005/08/addressing">http://www.w3.org/2005/08/addressing/anonymous</Address><Metadata xmlns="http://www.w3.org/2005/08/addressing"><Metadata xmlns="http://schemas.xmlsoap.org/ws/2004/09/mex" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"><wsx:MetadataSection xmlns=""><wsx:MetadataReference><Address xmlns="http://www.w3.org/2005/08/addressing"> ... </Address><Identity xmlns="http://schemas.xmlsoap.org/ws/2006/02/addressingidentity"><Dns> ...  </Dns></Identity></wsx:MetadataReference></wsx:MetadataSection></Metadata></Metadata></Issuer><sp:RequestSecurityTokenTemplate><trust:KeyType xmlns:trust="http://docs.oasis-open.org/ws-sx/ws-trust/200512">http://docs.oasis-open.org/ws-sx/ws-trust/200512/SymmetricKey</trust:KeyType></sp:RequestSecurityTokenTemplate><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireInternalReference/></wsp:Policy></sp:IssuedToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="31916-497">Güvenlik üst bilgisi örnekleri: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="31916-497">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="31916-498">İstek</span><span class="sxs-lookup"><span data-stu-id="31916-498">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-1dc8bdef-4202-4e08-8a5e-ab94da579dec-5"> ... </u:Timestamp><c:SecurityContextToken u:Id="uuid-7e004f51-63a3-4069-9b03-6a1a311a3181-1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:SecurityContextToken><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="31916-499">Yanıt</span><span class="sxs-lookup"><span data-stu-id="31916-499">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-7e004f51-63a3-4069-9b03-6a1a311a3181-6"> ... </u:Timestamp><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> </c:DerivedKeyToken> ... <c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
### <a name="35-using-sslnegotiated-for-service-authentication"></a><span data-ttu-id="31916-500">Hizmet kimlik doğrulaması için Sslanlaşmalı kullanma 3,5</span><span class="sxs-lookup"><span data-stu-id="31916-500">3.5 Using SslNegotiated for Service Authentication</span></span>  

 <span data-ttu-id="31916-501">Bu bölümde, WS-Trust (WS-T) RST/RSTR iletileri üzerinden TLS protokolünü yürüterek, anahtar değerine uygulanan WS-SecureConversation (WS-SC) başına bir güvenlik bağlamı belirteci olan koruma belirtecine sahip bir simetrik bağlama kullanan bir kimlik doğrulama modu grubu açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="31916-501">This section describes a group of authentication modes that use a symmetric binding with the protection token being a Security Context Token per WS-SecureConversation (WS-SC) whose key value is negotiated by executing the TLS protocol over WS-Trust (WS-T) RST/RSTR messages.</span></span> <span data-ttu-id="31916-502">WS-Trust kullanarak TLS el sıkışma uygulamasının ayrıntıları TLSNEGO ' de açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="31916-502">Details of the TLS handshake implementation using WS-Trust are described in TLSNEGO.</span></span> <span data-ttu-id="31916-503">Burada ileti örneklerinde, ilişkili bir güvenlik bağlamı olan SCT 'nin bir el sıkışma aracılığıyla zaten kurulduğu varsayılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="31916-503">Here in the message examples we will assume that SCT with an associated security context is already established through a handshake.</span></span>  
  
 <span data-ttu-id="31916-504">Kullanılan bağlama, aşağıdaki özelliklerle simetrik bir bağlamadır;</span><span class="sxs-lookup"><span data-stu-id="31916-504">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="31916-505">Koruma belirteci: SslContextToken, ekleme modu olarak ayarlandı. ../Includetoken/hiçbir</span><span class="sxs-lookup"><span data-stu-id="31916-505">Protection Token: SslContextToken, inclusion mode is set to .../IncludeToken/Never</span></span>  
<span data-ttu-id="31916-506">Belirteç koruması: false</span><span class="sxs-lookup"><span data-stu-id="31916-506">Token Protection: False</span></span>  
  
 <span data-ttu-id="31916-507">Tüm başlık ve gövde Imzaları: doğru</span><span class="sxs-lookup"><span data-stu-id="31916-507">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="31916-508">Koruma sırası: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="31916-508">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="31916-509">Imzayı şifreleyin: doğru</span><span class="sxs-lookup"><span data-stu-id="31916-509">Encrypt Signature: True</span></span>  
  
#### <a name="351-policy-for-sslnegotiated-service-authentication"></a><span data-ttu-id="31916-510">Sslanlaşmalı hizmet kimlik doğrulaması için 3.5.1 ilkesi</span><span class="sxs-lookup"><span data-stu-id="31916-510">3.5.1 Policy for SslNegotiated service authentication</span></span>  

 <span data-ttu-id="31916-511">Bu bölümdeki tüm kimlik doğrulama modları için ilke benzerdir ve yalnızca belirli imzalı destekleyici veya onaylama belirteçlerine göre farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="31916-511">Policy for all authentication modes in this section are similar and differ only by specific signed supporting or endorsing tokens used.</span></span>  
  
#### <a name="352-anonymousforsslnegotiated"></a><span data-ttu-id="31916-512">3.5.2 Anonymousforsslanlaşmalı</span><span class="sxs-lookup"><span data-stu-id="31916-512">3.5.2 AnonymousForSslNegotiated</span></span>  

 <span data-ttu-id="31916-513">Bu kimlik doğrulama modunda, istemci anonimdir ve hizmetin kimliği bir X. 509.440 sertifikası kullanılarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="31916-513">With this authentication mode the client is anonymous and the service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="31916-514">Kullanılan bağlama, yukarıdaki 3.5.1 bölümünde açıklandığı gibi simetrik bağlamanın bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="31916-514">The binding used is an instance of symmetric binding as described in 3.5.1 above.</span></span>  
  
 <span data-ttu-id="31916-515">İlke</span><span class="sxs-lookup"><span data-stu-id="31916-515">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="AnonymousForSslNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><mssp:SslContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient" xmlns:mssp="http://schemas.microsoft.com/ws/2005/07/securitypolicy"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></mssp:SslContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="31916-516">Güvenlik üst bilgisi örnekleri: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="31916-516">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="31916-517">İstek</span><span class="sxs-lookup"><span data-stu-id="31916-517">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-f4b86ce2-4ba6-4c55-bac1-2e920fc6d5db-4"> ... </u:Timestamp><sc:SecurityContextToken u:Id="uuid-d21ec2b8-99f5-443c-a4c6-a4d40619187e-1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:SecurityContextToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="31916-518">Yanıt</span><span class="sxs-lookup"><span data-stu-id="31916-518">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-d21ec2b8-99f5-443c-a4c6-a4d40619187e-4"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="31916-519">İlke</span><span class="sxs-lookup"><span data-stu-id="31916-519">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="AnonymousForSslNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><mssp:SslContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient" xmlns:mssp="http://schemas.microsoft.com/ws/2005/07/securitypolicy"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></mssp:SslContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="31916-520">Güvenlik üst bilgisi örnekleri: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="31916-520">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="31916-521">İstek</span><span class="sxs-lookup"><span data-stu-id="31916-521">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-c84b24b9-39e0-4cc3-99e2-cec088f1b9eb-4"> ... </u:Timestamp><sc:SecurityContextToken u:Id="uuid-df206ad9-1ee2-46d7-9fb4-6e4631c9762f-1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:SecurityContextToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
 <span data-ttu-id="31916-522">Yanıt</span><span class="sxs-lookup"><span data-stu-id="31916-522">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-df206ad9-1ee2-46d7-9fb4-6e4631c9762f-3"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
#### <a name="353-usernameforsslnegotiated"></a><span data-ttu-id="31916-523">3.5.3 Usernameforsslanlaşmalı</span><span class="sxs-lookup"><span data-stu-id="31916-523">3.5.3 UserNameForSslNegotiated</span></span>  

 <span data-ttu-id="31916-524">Bu kimlik doğrulama modunda istemci, SOAP katmanında imzalı destekleyici belirteç olarak görünen bir Kullanıcı adı belirteci kullanarak kimlik doğrular.</span><span class="sxs-lookup"><span data-stu-id="31916-524">With this authentication mode the client is authenticates using a Username Token which appears at the SOAP layer as a signed supporting token.</span></span> <span data-ttu-id="31916-525">Hizmetin kimliği bir X. 509.440 sertifikası kullanılarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="31916-525">The service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="31916-526">Kullanılan bağlama, 3.5.1 içinde açıklandığı gibi simetrik bağlamanın bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="31916-526">The binding used is an instance of symmetric binding as described in 3.5.1.</span></span>  
  
 <span data-ttu-id="31916-527">İlke</span><span class="sxs-lookup"><span data-stu-id="31916-527">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="UserNameForSslNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><mssp:SslContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient" xmlns:mssp="http://schemas.microsoft.com/ws/2005/07/securitypolicy"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></mssp:SslContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:SignedEncryptedSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:UsernameToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:WssUsernameToken10/></wsp:Policy></sp:UsernameToken></wsp:Policy></sp:SignedEncryptedSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="31916-528">Güvenlik üst bilgisi örnekleri: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="31916-528">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="31916-529">İstek</span><span class="sxs-lookup"><span data-stu-id="31916-529">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-3d1a12c3-e690-474a-a223-a346fc0329a9-4"> ... </u:Timestamp><sc:SecurityContextToken u:Id="uuid-137ea768-7d49-404b-87eb-f11d9c7154aa-1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:SecurityContextToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_9" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="31916-530">Yanıt</span><span class="sxs-lookup"><span data-stu-id="31916-530">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-137ea768-7d49-404b-87eb-f11d9c7154aa-5"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="31916-531">İlke</span><span class="sxs-lookup"><span data-stu-id="31916-531">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="UserNameForSslNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><mssp:SslContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient" xmlns:mssp="http://schemas.microsoft.com/ws/2005/07/securitypolicy"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></mssp:SslContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:SignedEncryptedSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:UsernameToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:WssUsernameToken10/></wsp:Policy></sp:UsernameToken></wsp:Policy></sp:SignedEncryptedSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="31916-532">Güvenlik üst bilgisi örnekleri: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="31916-532">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="31916-533">İstek</span><span class="sxs-lookup"><span data-stu-id="31916-533">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-56e931e8-20c2-457f-a83e-8fcd6b92c258-4"> ... </u:Timestamp><sc:SecurityContextToken u:Id="uuid-83d053cb-03a0-4461-9616-86475cf083c4-1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:SecurityContextToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
 <span data-ttu-id="31916-534">Yanıt</span><span class="sxs-lookup"><span data-stu-id="31916-534">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-83d053cb-03a0-4461-9616-86475cf083c4-4"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
#### <a name="354-issuedtokenforsslnegotiated"></a><span data-ttu-id="31916-535">3.5.4 ıssuedtokenforsslanlaşmalı</span><span class="sxs-lookup"><span data-stu-id="31916-535">3.5.4 IssuedTokenForSslNegotiated</span></span>  

 <span data-ttu-id="31916-536">Bu kimlik doğrulama modunda istemci, bu şekilde hizmette kimlik doğrulaması yapmaz, ancak bunun yerine STS tarafından verilen bir belirteç ve paylaşılan anahtar hakkında bilgi sahibi olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="31916-536">With this authentication mode the client does not authenticate to the service, as such, but instead presents a token issued by an STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="31916-537">Verilen belirteç, SOAP katmanında bir onaylama destekleme belirteci olarak görünür.</span><span class="sxs-lookup"><span data-stu-id="31916-537">The issued token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="31916-538">Hizmetin kimliği bir X. 509.440 sertifikası kullanılarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="31916-538">The service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="31916-539">Kullanılan bağlama, yukarıdaki 3.5.1 bölümünde açıklandığı gibi simetrik bağlamanın bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="31916-539">The binding used is an instance of symmetric binding as described in 3.5.1 above.</span></span>  
  
 <span data-ttu-id="31916-540">İlke</span><span class="sxs-lookup"><span data-stu-id="31916-540">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="IssuedTokenForSslNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><mssp:SslContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient" xmlns:mssp="http://schemas.microsoft.com/ws/2005/07/securitypolicy"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></mssp:SslContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:IssuedToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><Issuer xmlns="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><Address xmlns="http://www.w3.org/2005/08/addressing">http://www.w3.org/2005/08/addressing/anonymous</Address><Metadata xmlns="http://www.w3.org/2005/08/addressing"><Metadata xmlns="http://schemas.xmlsoap.org/ws/2004/09/mex" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"><wsx:MetadataSection xmlns=""><wsx:MetadataReference><Address xmlns="http://www.w3.org/2005/08/addressing"> ... </Address><Identity xmlns="http://schemas.xmlsoap.org/ws/2006/02/addressingidentity"><Dns> ... </Dns></Identity></wsx:MetadataReference></wsx:MetadataSection></Metadata></Metadata></Issuer><sp:RequestSecurityTokenTemplate><trust:KeyType xmlns:trust="http://docs.oasis-open.org/ws-sx/ws-trust/200512">http://docs.oasis-open.org/ws-sx/ws-trust/200512/SymmetricKey</trust:KeyType></sp:RequestSecurityTokenTemplate><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireInternalReference/></wsp:Policy></sp:IssuedToken></wsp:Policy></sp:EndorsingSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/><sp:RequireSignatureConfirmation/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="31916-541">Güvenlik üst bilgisi örnekleri: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="31916-541">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="31916-542">İstek</span><span class="sxs-lookup"><span data-stu-id="31916-542">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-b19fb2e7-8f0c-45c1-b62c-45d6ff6d57e7-5"> ... </u:Timestamp><c:SecurityContextToken u:Id="uuid-199509f9-7963-42b7-b340-7598ee261d5a-1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:SecurityContextToken><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="31916-543">Yanıt</span><span class="sxs-lookup"><span data-stu-id="31916-543">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-199509f9-7963-42b7-b340-7598ee261d5a-6"> ... </u:Timestamp><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="31916-544">İlke</span><span class="sxs-lookup"><span data-stu-id="31916-544">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="IssuedTokenForSslNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><mssp:SslContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient" xmlns:mssp="http://schemas.microsoft.com/ws/2005/07/securitypolicy"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></mssp:SslContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:IssuedToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><Issuer xmlns="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><Address xmlns="http://www.w3.org/2005/08/addressing">http://www.w3.org/2005/08/addressing/anonymous</Address><Metadata xmlns="http://www.w3.org/2005/08/addressing"><Metadata xmlns="http://schemas.xmlsoap.org/ws/2004/09/mex" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"><wsx:MetadataSection xmlns=""><wsx:MetadataReference><Address xmlns="http://www.w3.org/2005/08/addressing"> ... </Address><Identity xmlns="http://schemas.xmlsoap.org/ws/2006/02/addressingidentity"><Dns> ... </Dns></Identity></wsx:MetadataReference></wsx:MetadataSection></Metadata></Metadata></Issuer><sp:RequestSecurityTokenTemplate><trust:KeyType xmlns:trust="http://docs.oasis-open.org/ws-sx/ws-trust/200512">http://docs.oasis-open.org/ws-sx/ws-trust/200512/SymmetricKey</trust:KeyType></sp:RequestSecurityTokenTemplate><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireInternalReference/></wsp:Policy></sp:IssuedToken></wsp:Policy></sp:EndorsingSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/><sp:RequireSignatureConfirmation/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="31916-545">Güvenlik üst bilgisi örnekleri: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="31916-545">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="31916-546">İstek</span><span class="sxs-lookup"><span data-stu-id="31916-546">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-d75104d5-313e-440f-b112-db8aff57a5fe-5"> ... </u:Timestamp><c:SecurityContextToken u:Id="uuid-e668caab-b7e4-4056-ac42-4015ae2a67a6-1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:SecurityContextToken><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="31916-547">Yanıt</span><span class="sxs-lookup"><span data-stu-id="31916-547">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-e668caab-b7e4-4056-ac42-4015ae2a67a6-6"> ... </u:Timestamp><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
#### <a name="355-mutualsslnegotiated"></a><span data-ttu-id="31916-548">3.5.5 Mulualsslanlaşmalı</span><span class="sxs-lookup"><span data-stu-id="31916-548">3.5.5 MutualSslNegotiated</span></span>  

 <span data-ttu-id="31916-549">Bu kimlik doğrulama moduyla, istemci ve hizmet X. 509.440 sertifikalarını kullanarak kimlik doğrular.</span><span class="sxs-lookup"><span data-stu-id="31916-549">With this authentication mode the client and the service authenticate using X.509 certificates.</span></span> <span data-ttu-id="31916-550">Kullanılan bağlama, yukarıdaki 3.5.1 bölümünde açıklandığı gibi simetrik bağlamanın bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="31916-550">The binding used is an instance of symmetric binding as described in 3.5.1 above.</span></span>  
  
 <span data-ttu-id="31916-551">İlke</span><span class="sxs-lookup"><span data-stu-id="31916-551">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="MutualSslNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><mssp:SslContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient" xmlns:mssp="http://schemas.microsoft.com/ws/2005/07/securitypolicy"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><mssp:RequireClientCertificate/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></mssp:SslContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="31916-552">Güvenlik üst bilgisi örnekleri: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="31916-552">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="31916-553">İstek</span><span class="sxs-lookup"><span data-stu-id="31916-553">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-d1e6037e-8a64-494f-9447-07d3125b81b5-4"> ... </u:Timestamp><sc:SecurityContextToken u:Id="uuid-e4b73625-3011-4f6d-a6f9-4d682e860801-1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:SecurityContextToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="31916-554">Yanıt</span><span class="sxs-lookup"><span data-stu-id="31916-554">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-e4b73625-3011-4f6d-a6f9-4d682e860801-4"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="31916-555">İlke</span><span class="sxs-lookup"><span data-stu-id="31916-555">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="MutualSslNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><mssp:SslContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient" xmlns:mssp="http://schemas.microsoft.com/ws/2005/07/securitypolicy"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><mssp:RequireClientCertificate/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></mssp:SslContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="31916-556">Güvenlik üst bilgisi örnekleri: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="31916-556">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="31916-557">İstek</span><span class="sxs-lookup"><span data-stu-id="31916-557">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-c2a6ab10-889a-4ee1-871d-05410c90fc10-4"> ... </u:Timestamp><sc:SecurityContextToken u:Id="uuid-ede0bd89-1f7e-4453-96ed-13e58c7ba8fe-1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:SecurityContextToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
 <span data-ttu-id="31916-558">Yanıt</span><span class="sxs-lookup"><span data-stu-id="31916-558">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-ede0bd89-1f7e-4453-96ed-13e58c7ba8fe-3"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
### <a name="36-sspinegotiated"></a><span data-ttu-id="31916-559">3,6 SspiNegotiated</span><span class="sxs-lookup"><span data-stu-id="31916-559">3.6 SspiNegotiated</span></span>  

 <span data-ttu-id="31916-560">Bu kimlik doğrulama modunda, istemci ve sunucu kimlik doğrulamasını gerçekleştirmek için bir anlaşma protokolü kullanılır.</span><span class="sxs-lookup"><span data-stu-id="31916-560">With this authentication mode a negotiation protocol is used to perform client and server authentication.</span></span> <span data-ttu-id="31916-561">Mümkünse, Kerberos kullanılır, aksi takdirde NTLM kullanılır.</span><span class="sxs-lookup"><span data-stu-id="31916-561">Kerberos is used if possible, otherwise NTLM.</span></span> <span data-ttu-id="31916-562">Kullanılan bağlama, aşağıdaki özelliklerle simetrik bir bağlamadır;</span><span class="sxs-lookup"><span data-stu-id="31916-562">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="31916-563">Koruma belirteci: SpnegoContextToken, ekleme modu. ../ıncludetoken/AlwaysToRecipient olarak ayarlandı</span><span class="sxs-lookup"><span data-stu-id="31916-563">Protection Token: SpnegoContextToken, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
<span data-ttu-id="31916-564">Belirteç koruması: false</span><span class="sxs-lookup"><span data-stu-id="31916-564">Token Protection: False</span></span>  
  
 <span data-ttu-id="31916-565">Tüm başlık ve gövde Imzaları: doğru</span><span class="sxs-lookup"><span data-stu-id="31916-565">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="31916-566">Koruma sırası: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="31916-566">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="31916-567">Imzayı şifreleyin: doğru</span><span class="sxs-lookup"><span data-stu-id="31916-567">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="31916-568">İlke</span><span class="sxs-lookup"><span data-stu-id="31916-568">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="SspiNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:SpnegoContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></sp:SpnegoContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="31916-569">Güvenlik üst bilgisi örnekleri: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="31916-569">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="31916-570">İstek</span><span class="sxs-lookup"><span data-stu-id="31916-570">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-9a954fcb-4df2-4610-9800-f542f2b5130a-4"> ... </u:Timestamp><sc:SecurityContextToken u:Id="uuid-554d8cfc-e956-43db-9abb-afcafd024347-1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:SecurityContextToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="31916-571">Yanıt</span><span class="sxs-lookup"><span data-stu-id="31916-571">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-554d8cfc-e956-43db-9abb-afcafd024347-4"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>
```  
  
 <span data-ttu-id="31916-572">İlke</span><span class="sxs-lookup"><span data-stu-id="31916-572">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="SspiNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:SpnegoContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></sp:SpnegoContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="31916-573">Güvenlik üst bilgisi örnekleri: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="31916-573">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="31916-574">İstek</span><span class="sxs-lookup"><span data-stu-id="31916-574">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-f1673773-f9a7-4b43-b13b-405e7dd4a6e3-4"> ... </u:Timestamp><sc:SecurityContextToken u:Id="uuid-e0aabc81-6942-4fe6-81bc-9def184565ea-1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:SecurityContextToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
 <span data-ttu-id="31916-575">Yanıt</span><span class="sxs-lookup"><span data-stu-id="31916-575">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-e0aabc81-6942-4fe6-81bc-9def184565ea-3"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
### <a name="37-secureconversation"></a><span data-ttu-id="31916-576">3,7 SecureConversation</span><span class="sxs-lookup"><span data-stu-id="31916-576">3.7 SecureConversation</span></span>  

 <span data-ttu-id="31916-577">Kullanılan bağlama, koruma belirtecine WS-SecureConversation (WS-SC) başına SCT olan bir simetrik bağlamadır.</span><span class="sxs-lookup"><span data-stu-id="31916-577">The binding used is a symmetric binding with the protection token being a SCT per WS-SecureConversation (WS-SC).</span></span> <span data-ttu-id="31916-578">SCT, bir anlaşma Protokolü kullanan simetrik bir bağlama olan iç içe bir bağlamaya göre WS-Trust (WS-Trust) veya WS-SecureConversation (WS-SC) kullanılarak anlaşılır.</span><span class="sxs-lookup"><span data-stu-id="31916-578">The SCT is negotiated using WS-Trust (WS-Trust) or WS-SecureConversation (WS-SC) according to a nested binding, which is itself a symmetric binding that uses a negotiation protocol.</span></span> <span data-ttu-id="31916-579">Anlaşma Protokolü, mümkünse istemci ve sunucu kimlik doğrulaması gerçekleştirmek için Kerberos kullanır.</span><span class="sxs-lookup"><span data-stu-id="31916-579">The negotiation protocol will use Kerberos to perform client and server authentication if possible.</span></span> <span data-ttu-id="31916-580">Kerberos kullanılmıyorsa, NTLM 'ye geri döner.</span><span class="sxs-lookup"><span data-stu-id="31916-580">If Kerberos cannot be used, it will fall back to NTLM.</span></span>  
  
 <span data-ttu-id="31916-581">İlke</span><span class="sxs-lookup"><span data-stu-id="31916-581">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="SecureConversation_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:SecureConversationToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireDerivedKeys/><sp:BootstrapPolicy><wsp:Policy><sp:SignedParts xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><sp:Body/><sp:Header Name="To" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="From" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="FaultTo" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="ReplyTo" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="MessageID" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="RelatesTo" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="Action" Namespace="http://www.w3.org/2005/08/addressing"/></sp:SignedParts><sp:EncryptedParts xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><sp:Body/></sp:EncryptedParts><sp:SymmetricBinding xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:SpnegoContextToken sp:IncludeToken="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireDerivedKeys/></wsp:Policy></sp:SpnegoContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust10 xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust10></wsp:Policy></sp:BootstrapPolicy><sp:MustNotSendAmend/></wsp:Policy></sp:SecureConversationToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="31916-582">Güvenlik üst bilgisi örnekleri: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="31916-582">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  

 <span data-ttu-id="31916-583">İstek</span><span class="sxs-lookup"><span data-stu-id="31916-583">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-f01c6159-f159-454d-bd97-bbcc9b8e25d3-5"> ... </u:Timestamp><c:SecurityContextToken u:Id="uuid-582920d7-14a7-4adc-8091-e1f92d7d8055-1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:SecurityContextToken><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="31916-584">Yanıt</span><span class="sxs-lookup"><span data-stu-id="31916-584">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-582920d7-14a7-4adc-8091-e1f92d7d8055-6"> ... </u:Timestamp><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="31916-585">İlke</span><span class="sxs-lookup"><span data-stu-id="31916-585">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id="SecureConversation_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:SecureConversationToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireDerivedKeys/><sp:BootstrapPolicy><wsp:Policy><sp:SignedParts xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><sp:Body/><sp:Header Name="To" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="From" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="FaultTo" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="ReplyTo" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="MessageID" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="RelatesTo" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="Action" Namespace="http://www.w3.org/2005/08/addressing"/></sp:SignedParts><sp:EncryptedParts xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><sp:Body/></sp:EncryptedParts><sp:SymmetricBinding xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:SpnegoContextToken sp:IncludeToken="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireDerivedKeys/></wsp:Policy></sp:SpnegoContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust10 xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust10></wsp:Policy></sp:BootstrapPolicy><sp:MustNotSendAmend/></wsp:Policy></sp:SecureConversationToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="31916-586">Güvenlik üst bilgisi örnekleri: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="31916-586">Security Header Examples: EncryptBeforeSign</span></span>  

 <span data-ttu-id="31916-587">İstek</span><span class="sxs-lookup"><span data-stu-id="31916-587">Request</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-d57e6342-1c68-4095-a0c1-41979088a944-5"> ... </u:Timestamp><c:SecurityContextToken u:Id="uuid-9b22407d-b914-4c41-9105-1cf8cf7c3fe5-1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:SecurityContextToken><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 <span data-ttu-id="31916-588">Yanıt</span><span class="sxs-lookup"><span data-stu-id="31916-588">Response</span></span>  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-9b22407d-b914-4c41-9105-1cf8cf7c3fe5-6"> ... </u:Timestamp><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```

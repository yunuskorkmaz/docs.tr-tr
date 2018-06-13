---
title: Güvenlik Protokolleri sürüm 1.0
ms.date: 03/30/2017
ms.assetid: ee3402d2-1076-410b-a3cb-fae0372bd7af
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 1b1e911b20ac8974dbc8cfa79e03fbd14f9beb17
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509183"
---
# <a name="security-protocols-version-10"></a><span data-ttu-id="63bea-102">Güvenlik Protokolleri sürüm 1.0</span><span class="sxs-lookup"><span data-stu-id="63bea-102">Security Protocols version 1.0</span></span>
<span data-ttu-id="63bea-103">Web Hizmetleri Güvenlik protokolleri, tüm mevcut Kurumsal güvenlik gereksinimlerini Mesajlaşma kapak Web Hizmetleri güvenlik mekanizmaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="63bea-103">The Web Services Security Protocols provide Web services security mechanisms that cover all existing enterprise messaging security requirements.</span></span> <span data-ttu-id="63bea-104">Bu bölümde Windows Communication Foundation (WCF) sürümü 1.0 ayrıntıları açıklanmaktadır (uygulanan <xref:System.ServiceModel.Channels.SecurityBindingElement>) güvenlik protokolleri aşağıdaki Web Hizmetleri için.</span><span class="sxs-lookup"><span data-stu-id="63bea-104">This section describes the Windows Communication Foundation (WCF) version 1.0 details (implemented in the <xref:System.ServiceModel.Channels.SecurityBindingElement>) for the following Web services security protocols.</span></span>  
  
|<span data-ttu-id="63bea-105">Belirtim/belgesi</span><span class="sxs-lookup"><span data-stu-id="63bea-105">Specification/Document</span></span>|<span data-ttu-id="63bea-106">Bağlantı</span><span class="sxs-lookup"><span data-stu-id="63bea-106">Link</span></span>|  
|-|-|  
|<span data-ttu-id="63bea-107">WSS: SOAP iletisi güvenlik 1.0</span><span class="sxs-lookup"><span data-stu-id="63bea-107">WSS: SOAP Message Security 1.0</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf|  
|<span data-ttu-id="63bea-108">WSS: Kullanıcı belirteci profili 1.0</span><span class="sxs-lookup"><span data-stu-id="63bea-108">WSS: Username Token Profile 1.0</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf|  
|<span data-ttu-id="63bea-109">WSS: X509 profili 1.0 belirteci.</span><span class="sxs-lookup"><span data-stu-id="63bea-109">WSS: X509 Token Profile 1.0</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0.pdf|  
|<span data-ttu-id="63bea-110">WSS: SAML 1.1 belirteci profili 1.0</span><span class="sxs-lookup"><span data-stu-id="63bea-110">WSS: SAML 1.1 Token Profile 1.0</span></span>|http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.0.pdf|  
|<span data-ttu-id="63bea-111">WSS: SOAP iletisi güvenlik 1.1</span><span class="sxs-lookup"><span data-stu-id="63bea-111">WSS: SOAP Message Security 1.1</span></span>|http://www.oasis-open.org/committees/download.php/16790/wss-v1.1-spec-os-SOAPMessageSecurity.pdf|  
|<span data-ttu-id="63bea-112">WSS kullanıcıadı belirteci Profil 1.1</span><span class="sxs-lookup"><span data-stu-id="63bea-112">WSS Username Token Profile 1.1</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf|  
|<span data-ttu-id="63bea-113">WSS: X.509 belirteci Profil 1.1</span><span class="sxs-lookup"><span data-stu-id="63bea-113">WSS: X.509 Token Profile 1.1</span></span>|http://www.oasis-open.org/committees/download.php/16785/wss-v1.1-spec-os-x509TokenProfile.pdf|  
|<span data-ttu-id="63bea-114">WSS: Kerberos belirteci Profil 1.1</span><span class="sxs-lookup"><span data-stu-id="63bea-114">WSS: Kerberos Token Profile 1.1</span></span>|http://www.oasis-open.org/committees/download.php/16788/wss-v1.1-spec-os-KerberosTokenProfile.pdf|  
|<span data-ttu-id="63bea-115">WSS: SAML 1.1 belirteci Profil 1.1</span><span class="sxs-lookup"><span data-stu-id="63bea-115">WSS: SAML 1.1 Token Profile 1.1</span></span>|http://www.oasis-open.org/committees/download.php/16768/wss-v1.1-spec-os-SAMLTokenProfile.pdf|  
|<span data-ttu-id="63bea-116">WS-güvenli konuşma</span><span class="sxs-lookup"><span data-stu-id="63bea-116">WS-Secure Conversation</span></span>|http://msdn.microsoft.com/ws/2005/02/ws-secure-conversation/|  
|<span data-ttu-id="63bea-117">WS-Trust</span><span class="sxs-lookup"><span data-stu-id="63bea-117">WS-Trust</span></span>|http://msdn.microsoft.com/ws/2005/02/ws-trust/|  
|<span data-ttu-id="63bea-118">Uygulama Not:</span><span class="sxs-lookup"><span data-stu-id="63bea-118">Application Note:</span></span><br /><br /> <span data-ttu-id="63bea-119">WS-Trust TLS el sıkışma için kullanma</span><span class="sxs-lookup"><span data-stu-id="63bea-119">Using WS-Trust for TLS Handshake</span></span>|<span data-ttu-id="63bea-120">Yayımlanacak</span><span class="sxs-lookup"><span data-stu-id="63bea-120">To be published</span></span>|  
|<span data-ttu-id="63bea-121">Uygulama Not:</span><span class="sxs-lookup"><span data-stu-id="63bea-121">Application Note:</span></span><br /><br /> <span data-ttu-id="63bea-122">WS-Trust SPNEGO için kullanma</span><span class="sxs-lookup"><span data-stu-id="63bea-122">Using WS-Trust for SPNEGO</span></span>|<span data-ttu-id="63bea-123">Yayımlanacak</span><span class="sxs-lookup"><span data-stu-id="63bea-123">To be published</span></span>|  
|<span data-ttu-id="63bea-124">Uygulama Not:</span><span class="sxs-lookup"><span data-stu-id="63bea-124">Application Note:</span></span><br /><br /> <span data-ttu-id="63bea-125">Web Hizmetleri uç nokta başvuruları adresleme ve kimlik</span><span class="sxs-lookup"><span data-stu-id="63bea-125">Web Services Addressing Endpoint References And Identity</span></span>|<span data-ttu-id="63bea-126">Yayımlanacak</span><span class="sxs-lookup"><span data-stu-id="63bea-126">To be published</span></span>|  
|<span data-ttu-id="63bea-127">WS-SecurityPolicy 1.1</span><span class="sxs-lookup"><span data-stu-id="63bea-127">WS-SecurityPolicy 1.1</span></span><br /><br /> <span data-ttu-id="63bea-128">(2005/07)</span><span class="sxs-lookup"><span data-stu-id="63bea-128">(2005/07)</span></span>|http://msdn.microsoft.com/ws/2005/07/ws-security-policy/<br /><br /> <span data-ttu-id="63bea-129">OASIS WS-SX teknik komitesi gönderilen ayrıntıyla açıklayan hata bilgilerini tarafından dayanıklıdır gibi http://www.oasis-open.org/archives/ws-sx/200512/msg00017.html</span><span class="sxs-lookup"><span data-stu-id="63bea-129">as amended by errata submitted to OASIS WS-SX Technical Committee http://www.oasis-open.org/archives/ws-sx/200512/msg00017.html</span></span>|  
  
 <span data-ttu-id="63bea-130">WCF, sürüm 1, Web Hizmetleri güvenlik yapılandırması için temel olarak kullanılabilecek 17 kimlik doğrulama modları sağlar.</span><span class="sxs-lookup"><span data-stu-id="63bea-130">WCF, version 1, provides 17 authentication modes that can be used as the basis for Web services security configuration.</span></span> <span data-ttu-id="63bea-131">Her iki modda gibi dağıtım gereksinimleri, ortak bir dizi için optimize edilmiştir:</span><span class="sxs-lookup"><span data-stu-id="63bea-131">Each mode is optimized for a common set of deployment requirements, such as:</span></span>  
  
-   <span data-ttu-id="63bea-132">Hizmet ve istemci kimlik doğrulaması için kullanılan kimlik bilgileri.</span><span class="sxs-lookup"><span data-stu-id="63bea-132">Credentials used to authenticate client and service.</span></span>  
  
-   <span data-ttu-id="63bea-133">İleti veya taşıma güvenlik koruma mekanizması.</span><span class="sxs-lookup"><span data-stu-id="63bea-133">Message or transport security protection mechanisms.</span></span>  
  
-   <span data-ttu-id="63bea-134">İleti exchange desenleri.</span><span class="sxs-lookup"><span data-stu-id="63bea-134">Message exchange patterns.</span></span>  
  
|<span data-ttu-id="63bea-135">Kimlik doğrulama modu</span><span class="sxs-lookup"><span data-stu-id="63bea-135">Authentication Mode</span></span>|<span data-ttu-id="63bea-136">İstemci kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="63bea-136">Client Authentication</span></span>|<span data-ttu-id="63bea-137">Sunucu kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="63bea-137">Server Authentication</span></span>|<span data-ttu-id="63bea-138">Mod</span><span class="sxs-lookup"><span data-stu-id="63bea-138">Mode</span></span>|  
|-------------------------|---------------------------|---------------------------|----------|  
|<span data-ttu-id="63bea-139">UserNameOverTransport</span><span class="sxs-lookup"><span data-stu-id="63bea-139">UserNameOverTransport</span></span>|<span data-ttu-id="63bea-140">Kullanıcı adı/parola</span><span class="sxs-lookup"><span data-stu-id="63bea-140">User name/password</span></span>|<span data-ttu-id="63bea-141">X509</span><span class="sxs-lookup"><span data-stu-id="63bea-141">X509</span></span>|<span data-ttu-id="63bea-142">Taşıma</span><span class="sxs-lookup"><span data-stu-id="63bea-142">Transport</span></span>|  
|<span data-ttu-id="63bea-143">CertificateOverTransport</span><span class="sxs-lookup"><span data-stu-id="63bea-143">CertificateOverTransport</span></span>|<span data-ttu-id="63bea-144">X509</span><span class="sxs-lookup"><span data-stu-id="63bea-144">X509</span></span>|<span data-ttu-id="63bea-145">X509</span><span class="sxs-lookup"><span data-stu-id="63bea-145">X509</span></span>|<span data-ttu-id="63bea-146">Taşıma</span><span class="sxs-lookup"><span data-stu-id="63bea-146">Transport</span></span>|  
|<span data-ttu-id="63bea-147">KerberosOverTransport</span><span class="sxs-lookup"><span data-stu-id="63bea-147">KerberosOverTransport</span></span>|<span data-ttu-id="63bea-148">Windows</span><span class="sxs-lookup"><span data-stu-id="63bea-148">Windows</span></span>|<span data-ttu-id="63bea-149">X509</span><span class="sxs-lookup"><span data-stu-id="63bea-149">X509</span></span>|<span data-ttu-id="63bea-150">Taşıma</span><span class="sxs-lookup"><span data-stu-id="63bea-150">Transport</span></span>|  
|<span data-ttu-id="63bea-151">IssuedTokenOverTransport</span><span class="sxs-lookup"><span data-stu-id="63bea-151">IssuedTokenOverTransport</span></span>|<span data-ttu-id="63bea-152">Federasyon</span><span class="sxs-lookup"><span data-stu-id="63bea-152">Federated</span></span>|<span data-ttu-id="63bea-153">X509</span><span class="sxs-lookup"><span data-stu-id="63bea-153">X509</span></span>|<span data-ttu-id="63bea-154">Taşıma</span><span class="sxs-lookup"><span data-stu-id="63bea-154">Transport</span></span>|  
|<span data-ttu-id="63bea-155">SspiNegotiatedOverTransport</span><span class="sxs-lookup"><span data-stu-id="63bea-155">SspiNegotiatedOverTransport</span></span>|<span data-ttu-id="63bea-156">Windows SSPI anlaşması</span><span class="sxs-lookup"><span data-stu-id="63bea-156">Windows Sspi Negotiated</span></span>|<span data-ttu-id="63bea-157">Windows SSPI anlaşması</span><span class="sxs-lookup"><span data-stu-id="63bea-157">Windows Sspi Negotiated</span></span>|<span data-ttu-id="63bea-158">Taşıma</span><span class="sxs-lookup"><span data-stu-id="63bea-158">Transport</span></span>|  
|<span data-ttu-id="63bea-159">AnonymousForCertificate</span><span class="sxs-lookup"><span data-stu-id="63bea-159">AnonymousForCertificate</span></span>|<span data-ttu-id="63bea-160">Yok.</span><span class="sxs-lookup"><span data-stu-id="63bea-160">None</span></span>|<span data-ttu-id="63bea-161">X509</span><span class="sxs-lookup"><span data-stu-id="63bea-161">X509</span></span>|<span data-ttu-id="63bea-162">İleti</span><span class="sxs-lookup"><span data-stu-id="63bea-162">Message</span></span>|  
|<span data-ttu-id="63bea-163">UserNameForCertificate</span><span class="sxs-lookup"><span data-stu-id="63bea-163">UserNameForCertificate</span></span>|<span data-ttu-id="63bea-164">Kullanıcı adı/parola</span><span class="sxs-lookup"><span data-stu-id="63bea-164">User name/password</span></span>|<span data-ttu-id="63bea-165">X509</span><span class="sxs-lookup"><span data-stu-id="63bea-165">X509</span></span>|<span data-ttu-id="63bea-166">İleti</span><span class="sxs-lookup"><span data-stu-id="63bea-166">Message</span></span>|  
|<span data-ttu-id="63bea-167">MutualCertificate</span><span class="sxs-lookup"><span data-stu-id="63bea-167">MutualCertificate</span></span>|<span data-ttu-id="63bea-168">X509</span><span class="sxs-lookup"><span data-stu-id="63bea-168">X509</span></span>|<span data-ttu-id="63bea-169">X509</span><span class="sxs-lookup"><span data-stu-id="63bea-169">X509</span></span>|<span data-ttu-id="63bea-170">İleti</span><span class="sxs-lookup"><span data-stu-id="63bea-170">Message</span></span>|  
|<span data-ttu-id="63bea-171">MutualCertificateDuplex</span><span class="sxs-lookup"><span data-stu-id="63bea-171">MutualCertificateDuplex</span></span>|<span data-ttu-id="63bea-172">X509</span><span class="sxs-lookup"><span data-stu-id="63bea-172">X509</span></span>|<span data-ttu-id="63bea-173">X509</span><span class="sxs-lookup"><span data-stu-id="63bea-173">X509</span></span>|<span data-ttu-id="63bea-174">İleti</span><span class="sxs-lookup"><span data-stu-id="63bea-174">Message</span></span>|  
|<span data-ttu-id="63bea-175">IssuedTokenForCertificate</span><span class="sxs-lookup"><span data-stu-id="63bea-175">IssuedTokenForCertificate</span></span>|<span data-ttu-id="63bea-176">Federasyon</span><span class="sxs-lookup"><span data-stu-id="63bea-176">Federated</span></span>|<span data-ttu-id="63bea-177">X509</span><span class="sxs-lookup"><span data-stu-id="63bea-177">X509</span></span>|<span data-ttu-id="63bea-178">İleti</span><span class="sxs-lookup"><span data-stu-id="63bea-178">Message</span></span>|  
|<span data-ttu-id="63bea-179">Kerberos</span><span class="sxs-lookup"><span data-stu-id="63bea-179">Kerberos</span></span>|<span data-ttu-id="63bea-180">Windows</span><span class="sxs-lookup"><span data-stu-id="63bea-180">Windows</span></span>|<span data-ttu-id="63bea-181">Windows</span><span class="sxs-lookup"><span data-stu-id="63bea-181">Windows</span></span>|<span data-ttu-id="63bea-182">İleti</span><span class="sxs-lookup"><span data-stu-id="63bea-182">Message</span></span>|  
|<span data-ttu-id="63bea-183">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="63bea-183">IssuedToken</span></span>|<span data-ttu-id="63bea-184">Federasyon</span><span class="sxs-lookup"><span data-stu-id="63bea-184">Federated</span></span>|<span data-ttu-id="63bea-185">Federasyon</span><span class="sxs-lookup"><span data-stu-id="63bea-185">Federated</span></span>|<span data-ttu-id="63bea-186">İleti</span><span class="sxs-lookup"><span data-stu-id="63bea-186">Message</span></span>|  
|<span data-ttu-id="63bea-187">SspiNegotiated</span><span class="sxs-lookup"><span data-stu-id="63bea-187">SspiNegotiated</span></span>|<span data-ttu-id="63bea-188">Windows SSPI anlaşması</span><span class="sxs-lookup"><span data-stu-id="63bea-188">Windows Sspi Negotiated</span></span>|<span data-ttu-id="63bea-189">Windows SSPI anlaşması</span><span class="sxs-lookup"><span data-stu-id="63bea-189">Windows Sspi Negotiated</span></span>|<span data-ttu-id="63bea-190">İleti</span><span class="sxs-lookup"><span data-stu-id="63bea-190">Message</span></span>|  
|<span data-ttu-id="63bea-191">AnonymousForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="63bea-191">AnonymousForSslNegotiated</span></span>|<span data-ttu-id="63bea-192">Yok.</span><span class="sxs-lookup"><span data-stu-id="63bea-192">None</span></span>|<span data-ttu-id="63bea-193">X509, TLS Nego</span><span class="sxs-lookup"><span data-stu-id="63bea-193">X509, TLS-Nego</span></span>|<span data-ttu-id="63bea-194">İleti</span><span class="sxs-lookup"><span data-stu-id="63bea-194">Message</span></span>|  
|<span data-ttu-id="63bea-195">UserNameForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="63bea-195">UserNameForSslNegotiated</span></span>|<span data-ttu-id="63bea-196">Kullanıcı adı/parola</span><span class="sxs-lookup"><span data-stu-id="63bea-196">User name/password</span></span>|<span data-ttu-id="63bea-197">X509, TLS Nego</span><span class="sxs-lookup"><span data-stu-id="63bea-197">X509, TLS-Nego</span></span>|<span data-ttu-id="63bea-198">İleti</span><span class="sxs-lookup"><span data-stu-id="63bea-198">Message</span></span>|  
|<span data-ttu-id="63bea-199">MutualSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="63bea-199">MutualSslNegotiated</span></span>|<span data-ttu-id="63bea-200">X509</span><span class="sxs-lookup"><span data-stu-id="63bea-200">X509</span></span>|<span data-ttu-id="63bea-201">X509, TLS Nego</span><span class="sxs-lookup"><span data-stu-id="63bea-201">X509, TLS-Nego</span></span>|<span data-ttu-id="63bea-202">İleti</span><span class="sxs-lookup"><span data-stu-id="63bea-202">Message</span></span>|  
|<span data-ttu-id="63bea-203">IssuedTokenForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="63bea-203">IssuedTokenForSslNegotiated</span></span>|<span data-ttu-id="63bea-204">Federasyon</span><span class="sxs-lookup"><span data-stu-id="63bea-204">Federated</span></span>|<span data-ttu-id="63bea-205">X509, TLS Nego</span><span class="sxs-lookup"><span data-stu-id="63bea-205">X509, TLS-Nego</span></span>|<span data-ttu-id="63bea-206">İleti</span><span class="sxs-lookup"><span data-stu-id="63bea-206">Message</span></span>|  
  
 <span data-ttu-id="63bea-207">Bu tür kimlik doğrulama modları kullanarak uç noktaları WS-SecurityPolicy (WS-SP) kullanarak kendi güvenlik gereksinimlerini hızlı.</span><span class="sxs-lookup"><span data-stu-id="63bea-207">Endpoints using such authentication modes can express their security requirements using WS-SecurityPolicy (WS-SP).</span></span> <span data-ttu-id="63bea-208">Bu belgede güvenlik üstbilgi ve her kimlik doğrulama modu için altyapı iletileri yapısını açıklar ve ilkeleri ve iletileri örnekleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="63bea-208">This document describes the structure of security header and infrastructure messages for each authentication mode and provides examples of policies and messages.</span></span>  
  
 <span data-ttu-id="63bea-209">WCF uygulamalar arasında çok ileti iletişimlerini korumak için güvenli oturumlar desteği sağlamak için WS-SecureConversation yararlanır.</span><span class="sxs-lookup"><span data-stu-id="63bea-209">WCF leverages WS-SecureConversation to provide secure sessions support to protect multi-message exchanges between applications.</span></span>  <span data-ttu-id="63bea-210">"Güvenli oturumlar" aşağıdaki uygulama ayrıntıları için bkz.</span><span class="sxs-lookup"><span data-stu-id="63bea-210">See "Secure Sessions" below for implementation details.</span></span>  
  
 <span data-ttu-id="63bea-211">Kimlik doğrulama modları yanı sıra WCF çoğu ileti güvenlik tabanlı kimlik doğrulama modları, örneğin geçerli ortak koruma mekanizmalarını denetleyen ayarları sağlar: şifreleme işlemleri, algoritma paketleri, anahtar türetme karşı imza sırası ve imza onayı.</span><span class="sxs-lookup"><span data-stu-id="63bea-211">In addition to authentication modes, WCF provides settings to control common protection mechanisms that apply to most message security-based authentication modes, for example: order of signature versus encryption operations, algorithm suites, key derivation, and signature confirmation.</span></span>  
  
 <span data-ttu-id="63bea-212">Bu belgede, aşağıdaki ön ekleri ve ad alanları kullanılır.</span><span class="sxs-lookup"><span data-stu-id="63bea-212">The following prefixes and namespaces are used in this document.</span></span>  
  
|<span data-ttu-id="63bea-213">önek</span><span class="sxs-lookup"><span data-stu-id="63bea-213">Prefix</span></span>|<span data-ttu-id="63bea-214">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="63bea-214">Namespace</span></span>|  
|------------|---------------|  
|<span data-ttu-id="63bea-215">s</span><span class="sxs-lookup"><span data-stu-id="63bea-215">s</span></span>|http://www.w3.org/2003/05/soap-envelope|  
|<span data-ttu-id="63bea-216">SP</span><span class="sxs-lookup"><span data-stu-id="63bea-216">sp</span></span>|http://schemas.xmlsoap.org/ws/2005/07/securitypolicy|  
|<span data-ttu-id="63bea-217">a</span><span class="sxs-lookup"><span data-stu-id="63bea-217">a</span></span>|http://www.w3.org/2005/08/addressing|  
|<span data-ttu-id="63bea-218">wsse</span><span class="sxs-lookup"><span data-stu-id="63bea-218">wsse</span></span>|<span data-ttu-id="63bea-219">HENÜZ BELİRLENMEDİ – OASIS WSS 1.0 URI</span><span class="sxs-lookup"><span data-stu-id="63bea-219">TBD – OASIS WSS 1.0 URI</span></span>|  
|<span data-ttu-id="63bea-220">wsse11</span><span class="sxs-lookup"><span data-stu-id="63bea-220">wsse11</span></span>|<span data-ttu-id="63bea-221">HENÜZ BELİRLENMEDİ – OASIS WSS 1.1 URI</span><span class="sxs-lookup"><span data-stu-id="63bea-221">TBD – OASIS WSS 1.1 URI</span></span>|  
|<span data-ttu-id="63bea-222">wsu</span><span class="sxs-lookup"><span data-stu-id="63bea-222">wsu</span></span>|<span data-ttu-id="63bea-223">Henüz Belirlenmedi – OASIS WSS 1.0 yardımcı programı URI</span><span class="sxs-lookup"><span data-stu-id="63bea-223">TBD – OASIS WSS 1.0 Utility URI</span></span>|  
|<span data-ttu-id="63bea-224">DS</span><span class="sxs-lookup"><span data-stu-id="63bea-224">ds</span></span>|<span data-ttu-id="63bea-225">Henüz Belirlenmedi – W3C XMLDSig URI</span><span class="sxs-lookup"><span data-stu-id="63bea-225">TBD – W3C XMLDSig URI</span></span>|  
|<span data-ttu-id="63bea-226">WST</span><span class="sxs-lookup"><span data-stu-id="63bea-226">wst</span></span>|<span data-ttu-id="63bea-227">Henüz Belirlenmedi – WS-Trust 2005/02 URI</span><span class="sxs-lookup"><span data-stu-id="63bea-227">TBD – WS-Trust 2005/02 URI</span></span>|  
|<span data-ttu-id="63bea-228">wssc</span><span class="sxs-lookup"><span data-stu-id="63bea-228">wssc</span></span>|<span data-ttu-id="63bea-229">Henüz Belirlenmedi – WS-SecureConversation 2005/02 URI</span><span class="sxs-lookup"><span data-stu-id="63bea-229">TBD – WS-SecureConversation 2005/02 URI</span></span>|  
|<span data-ttu-id="63bea-230">wsaw</span><span class="sxs-lookup"><span data-stu-id="63bea-230">wsaw</span></span>|<span data-ttu-id="63bea-231">Henüz Belirlenmedi - WS adresleme İlkesi ad alanı</span><span class="sxs-lookup"><span data-stu-id="63bea-231">TBD - WS-Addressing policy namespace</span></span>|  
|<span data-ttu-id="63bea-232">WSP</span><span class="sxs-lookup"><span data-stu-id="63bea-232">wsp</span></span>|http://schemas.xmlsoap.org/ws/2004/09/policy|  
|<span data-ttu-id="63bea-233">mssp</span><span class="sxs-lookup"><span data-stu-id="63bea-233">mssp</span></span>|http://schemas.microsoft.com/ws/2005/07/securitypolicy|  
  
## <a name="1-token-profiles"></a><span data-ttu-id="63bea-234">1. Belirteç profilleri</span><span class="sxs-lookup"><span data-stu-id="63bea-234">1. Token Profiles</span></span>  
 <span data-ttu-id="63bea-235">Web Hizmetleri Güvenlik belirtimleri kimlik bilgisi güvenlik belirteçlerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="63bea-235">Web Services Security specifications represent credential as security tokens.</span></span> <span data-ttu-id="63bea-236">WCF aşağıdaki belirteç türlerini destekler:</span><span class="sxs-lookup"><span data-stu-id="63bea-236">WCF supports the following token types:</span></span>  
  
### <a name="11-usernametoken"></a><span data-ttu-id="63bea-237">1.1 UsernameToken</span><span class="sxs-lookup"><span data-stu-id="63bea-237">1.1 UsernameToken</span></span>  
 <span data-ttu-id="63bea-238">WCF aşağıdaki kısıtlamalar UsernameToken10 ve UsernameToken11 profilleriyle aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="63bea-238">WCF follows UsernameToken10 and UsernameToken11 profiles with the following constraints:</span></span>  
  
 <span data-ttu-id="63bea-239">UsernameToken\Password öğede R1101 PasswordType özniteliği atlanmış gerekir veya #PasswordText (varsayılan) değerine sahip.</span><span class="sxs-lookup"><span data-stu-id="63bea-239">R1101 PasswordType attribute on UsernameToken\Password element MUST be either omitted or have value #PasswordText (default).</span></span>  
  
 <span data-ttu-id="63bea-240">Bir genişletilebilirlik kullanarak #PasswordDigest uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="63bea-240">One can implement the #PasswordDigest using extensibility.</span></span> <span data-ttu-id="63bea-241">Yeterli güvenli parola koruma mekanizması olarak #PasswordDigest genellikle mistaken olduğunu gözlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="63bea-241">It has been observed that #PasswordDigest was often mistaken to be a secure enough password protection mechanism.</span></span> <span data-ttu-id="63bea-242">Ancak #PasswordDigest UsernameToken şifrelenmesi için bir alternatif olarak sunulamıyor.</span><span class="sxs-lookup"><span data-stu-id="63bea-242">But #PasswordDigest cannot serve as a substitute for encryption of the UsernameToken.</span></span> <span data-ttu-id="63bea-243">Birincil #PasswordDigest yeniden yürütme saldırılarına karşı koruma hedefidir.</span><span class="sxs-lookup"><span data-stu-id="63bea-243">The primary goal of #PasswordDigest is protection against replay attacks.</span></span> <span data-ttu-id="63bea-244">WCF kimlik doğrulama modu, ileti imzalarını kullanarak yeniden yürütme saldırı tehditleri azalır.</span><span class="sxs-lookup"><span data-stu-id="63bea-244">In WCF authentication modes, replay attack threats are mitigated by using message signatures.</span></span>  
  
 <span data-ttu-id="63bea-245">B1102 WCF hiçbir zaman UsernameToken Nonce ve oluşturulan alt öğeleri yayar.</span><span class="sxs-lookup"><span data-stu-id="63bea-245">B1102 WCF never emits Nonce and Created sub-elements of the UsernameToken.</span></span>  
  
 <span data-ttu-id="63bea-246">Bu alt öğeleri yeniden yürütme algılaması yardımcı olmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="63bea-246">These sub-elements are intended to help replay detection.</span></span> <span data-ttu-id="63bea-247">WCF yerine ileti imzalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="63bea-247">WCF uses message signatures instead.</span></span>  
  
 <span data-ttu-id="63bea-248">OASIS WSS SOAP iletisi güvenlik UsernameToken Profil 1.1 (UsernameToken11) anahtar türetme parola özelliğini kullanıma sunmuştur.</span><span class="sxs-lookup"><span data-stu-id="63bea-248">OASIS WSS SOAP Message Security UsernameToken Profile 1.1 (UsernameToken11) introduced key derivation from password feature.</span></span>  
  
 <span data-ttu-id="63bea-249">B1103 UsernameToken parola için anahtar türevi değil kullanılmalıdır ve bu nedenle şifreleme işlemleri için.</span><span class="sxs-lookup"><span data-stu-id="63bea-249">B1103 UsernameToken password MUST not be used for key derivation and therefore for cryptographic operations.</span></span>  
  
 <span data-ttu-id="63bea-250">Stratejinin: parolalar genellikle şifreleme işlemleri için kullanılacak zayıf olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="63bea-250">Rationale: passwords are generally considered too weak to be used for cryptographic operations.</span></span>  
  
### <a name="12-x509-token"></a><span data-ttu-id="63bea-251">x 509 belirteci 1.2</span><span class="sxs-lookup"><span data-stu-id="63bea-251">1.2 X509 Token</span></span>  
 <span data-ttu-id="63bea-252">WCF X509v3 sertifika bir kimlik bilgisi türü destekler ve X509TokenProfile1.0 ve X509TokenProfile1.1 aşağıdaki kısıtlamalarla izler:</span><span class="sxs-lookup"><span data-stu-id="63bea-252">WCF supports X509v3 certificates as a credential type and follows X509TokenProfile1.0 and X509TokenProfile1.1 with the following constraints:</span></span>  
  
 <span data-ttu-id="63bea-253">Bir X509v3 sertifika içerdiğinde BinarySecurityToken öğesindeki R1201 ValueType özniteliği değeri #X509v3 olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="63bea-253">R1201 The ValueType attribute on the BinarySecurityToken element must have value #X509v3 when it contains an X509v3 certificate.</span></span>  
  
 <span data-ttu-id="63bea-254">WSS belirteci profili 1.0 ve 1.1 #X509PKIPathv1 ve #PKCS7 olarak da tanımlayın X509 türleri değeri.</span><span class="sxs-lookup"><span data-stu-id="63bea-254">WSS X509 Token Profile 1.0 and 1.1 define also #X509PKIPathv1 and #PKCS7 as value types.</span></span> <span data-ttu-id="63bea-255">WCF bu türleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="63bea-255">WCF does not support these types.</span></span>  
  
 <span data-ttu-id="63bea-256">R1202 SubjectKeyIdentifier (SKI) uzantısı ise bir X509 mevcut sertifika wsse:KeyIdentifier olmalıdır dış başvurular belirteci için kullanılan, ValueType ile #X509SubjectKeyIdentifier ve içeriğini base64 ile kodlanmış değeri özniteliği Sertifikanın SKI uzantısı.</span><span class="sxs-lookup"><span data-stu-id="63bea-256">R1202 If a SubjectKeyIdentifier (SKI) extension is present in an X509 certificate, wsse:KeyIdentifier should be used for external references to the token, with the ValueType attribute as #X509SubjectKeyIdentifier and its content the base64-encoded value of certificate's SKI extension.</span></span>  
  
 <span data-ttu-id="63bea-257">SKI başvuruları yaygın olarak uygulanan ve yüksek oranda birlikte çalışabilir dış başvuru türünde olmasını kanıtlanmış.</span><span class="sxs-lookup"><span data-stu-id="63bea-257">SKI references are widely implemented and proven to be a highly interoperable external reference type.</span></span>  
  
 <span data-ttu-id="63bea-258">R1203 Dış başvuru X509 için güvenlik belirteci olmamalıdır ds:X509IssuerSerial'ı kullanın.</span><span class="sxs-lookup"><span data-stu-id="63bea-258">R1203 An external Reference to X509 Security Token SHOULD NOT use ds:X509IssuerSerial.</span></span>  
  
 <span data-ttu-id="63bea-259">R1204 varsa X509TokenProfile1.1, bir dış başvuru X509 güvenlik belirteci kullanmalıdır WS güvenliği 1.1 tarafından sunulan parmak izi için kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="63bea-259">R1204 If X509TokenProfile1.1 is in use, an external reference to X509 Security Token SHOULD use the thumbprint introduced by WS-Security 1.1.</span></span>  
  
 <span data-ttu-id="63bea-260">WCF X509IssuerSerial destekler.</span><span class="sxs-lookup"><span data-stu-id="63bea-260">WCF supports X509IssuerSerial.</span></span> <span data-ttu-id="63bea-261">Bununla birlikte çalışabilirlik sorunları vardır X509IssuerSerial: WCF X509IssuerSerial iki değerleri karşılaştırmak için bir dize kullanır.</span><span class="sxs-lookup"><span data-stu-id="63bea-261">However There are interoperability issues with X509IssuerSerial: WCF uses a string to compare two values of X509IssuerSerial.</span></span> <span data-ttu-id="63bea-262">Bir konu adı bileşenleri yeniden sıralar ve bir WCF hizmeti için bir sertifika için bir başvuru gönderir, bu nedenle onu bulunamayabilir.</span><span class="sxs-lookup"><span data-stu-id="63bea-262">Therefore if one reorders components of the Subject Name and sends to an WCF service a reference to a certificate, it may not be found.</span></span>  
  
### <a name="13-kerberos-token"></a><span data-ttu-id="63bea-263">1.3 Kerberos belirteci</span><span class="sxs-lookup"><span data-stu-id="63bea-263">1.3 Kerberos Token</span></span>  
 <span data-ttu-id="63bea-264">WCF KerberosTokenProfile1.1 amacıyla Windows kimlik doğrulaması aşağıdaki kısıtlamalar ile destekler:</span><span class="sxs-lookup"><span data-stu-id="63bea-264">WCF supports KerberosTokenProfile1.1 for the purpose of Windows authentication with the following constraints:</span></span>  
  
 <span data-ttu-id="63bea-265">R1301 A Kerberos belirteci gerekir taşıyan bir GSS değerini GSS_API ve Kerberos belirtimi tanımlandığı gibi Kerberos v4 AP_REQ Sarmalanan ve değer #GSS_Kerberosv5_AP_REQ ValueType özniteliğiyle olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="63bea-265">R1301 A Kerberos Token must carry the value of a GSS wrapped Kerberos v4 AP_REQ as defined in GSS_API and the Kerberos specification, and must have the ValueType attribute with the value #GSS_Kerberosv5_AP_REQ.</span></span>  
  
 <span data-ttu-id="63bea-266">WCF kullanır GSS Kerberos AP-REQ, olmayan bir tam AP-talep Sarmalanan</span><span class="sxs-lookup"><span data-stu-id="63bea-266">WCF uses GSS wrapped Kerberos AP-REQ, not a bare AP-REQ.</span></span> <span data-ttu-id="63bea-267">Bu bir güvenlik en iyi uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="63bea-267">This is a security best practice.</span></span>  
  
### <a name="14-saml-v11-token"></a><span data-ttu-id="63bea-268">1.4 SAML v1.1 belirteci</span><span class="sxs-lookup"><span data-stu-id="63bea-268">1.4 SAML v1.1 Token</span></span>  
 <span data-ttu-id="63bea-269">WCF WSS SAML belirteci profillerini 1.0 ve 1.1 için SAML v1.1 belirteçleri destekler.</span><span class="sxs-lookup"><span data-stu-id="63bea-269">WCF supports WSS SAML Token profiles 1.0 and 1.1 for SAML v1.1 tokens.</span></span> <span data-ttu-id="63bea-270">SAML belirteci biçimleri diğer sürümleri uygulamak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="63bea-270">It is possible to implement other versions of SAML token formats.</span></span>  
  
### <a name="15-security-context-token"></a><span data-ttu-id="63bea-271">1.5 güvenlik bağlamı belirteci</span><span class="sxs-lookup"><span data-stu-id="63bea-271">1.5 Security Context Token</span></span>  
 <span data-ttu-id="63bea-272">WCF güvenlik bağlamı belirteci (WS-SecureCoversation sunulan SCT) destekler.</span><span class="sxs-lookup"><span data-stu-id="63bea-272">WCF supports the Security Context Token (SCT) introduced in WS-SecureCoversation.</span></span> <span data-ttu-id="63bea-273">SCT SecureConversation içinde de kurulmuş bir güvenlik bağlamı belirtmek için kullanılan TLS ve SSPI ikili anlaşma protokolleri gibi aşağıda açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="63bea-273">SCT is used to represent a security context established in SecureConversation as well as the binary negotiation protocols TLS and SSPI, described below.</span></span>  
  
## <a name="2-common-message-security-parameters"></a><span data-ttu-id="63bea-274">2. Ortak ileti güvenlik parametreleri</span><span class="sxs-lookup"><span data-stu-id="63bea-274">2. Common Message Security Parameters</span></span>  
  
### <a name="21-timestamp"></a><span data-ttu-id="63bea-275">2.1 zaman damgası</span><span class="sxs-lookup"><span data-stu-id="63bea-275">2.1 TimeStamp</span></span>  
 <span data-ttu-id="63bea-276">Zaman damgası varlığı kullanılarak denetlenir <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> özelliği <xref:System.ServiceModel.Channels.SecurityBindingElement> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="63bea-276">Timestamp presence is controlled using the <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> property of the <xref:System.ServiceModel.Channels.SecurityBindingElement> class.</span></span> <span data-ttu-id="63bea-277">WCF her zaman wsse:TimeStamp wsse ile serileştiren: oluşturulan ve wsse: alanları süresi dolar.</span><span class="sxs-lookup"><span data-stu-id="63bea-277">WCF always serializes wsse:TimeStamp with wsse:Created and wsse:Expires fields.</span></span> <span data-ttu-id="63bea-278">İmzalama kullanıldığında wsse:TimeStamp her zaman imzalanır.</span><span class="sxs-lookup"><span data-stu-id="63bea-278">The wsse:TimeStamp is always signed when signing is used.</span></span>  
  
### <a name="22-protection-order"></a><span data-ttu-id="63bea-279">2.2 protection sırası</span><span class="sxs-lookup"><span data-stu-id="63bea-279">2.2 Protection Order</span></span>  
 <span data-ttu-id="63bea-280">WCF ileti koruma sırasını "Önce oturum şifrelemek" ve "Şifrelemek önce oturum" (Güvenlik İlkesi 1.1) destekler.</span><span class="sxs-lookup"><span data-stu-id="63bea-280">WCF supports the message protection order "Sign Before Encrypt" and "Encrypt Before Sign" (Security Policy 1.1).</span></span> <span data-ttu-id="63bea-281">"Şifrele önce oturum" nedenlere için önerilir: WS-güvenlik 1.1 SignatureConfirmation mekanizması kullanılır ve imza şifrelenmiş içerik üzerinde yapar sürece iletileri şifrelemek önce oturum ile korunan imza değiştirme saldırılara açık daha zor denetleme.</span><span class="sxs-lookup"><span data-stu-id="63bea-281">"Sign Before Encrypt" is recommended for reasons including: messages protected with Encrypt Before Sign are open to signature substitution attacks unless the WS-Security 1.1 SignatureConfirmation mechanism is used, and a signature over encrypted content makes auditing harder.</span></span>  
  
### <a name="23-signature-protection"></a><span data-ttu-id="63bea-282">2.3 imza koruma</span><span class="sxs-lookup"><span data-stu-id="63bea-282">2.3 Signature Protection</span></span>  
 <span data-ttu-id="63bea-283">Önce oturum şifrelemek kullanıldığında (özellikle özel belirteç zayıf anahtar malzemesi ile kullanıldığında) şifrelenmiş içeriği veya imzalama anahtarı tahmin için deneme yanılma saldırıları önlemek için imza korumak için önerilir.</span><span class="sxs-lookup"><span data-stu-id="63bea-283">When Encrypt Before Sign is used, it is recommended to protect the signature to prevent brute force attacks for guessing the encrypted content or the signing key (especially when a custom token is used with weak key material).</span></span>  
  
### <a name="24-algorithm-suite"></a><span data-ttu-id="63bea-284">2.4 algoritması paketi</span><span class="sxs-lookup"><span data-stu-id="63bea-284">2.4 Algorithm Suite</span></span>  
 <span data-ttu-id="63bea-285">WCF güvenlik ilkesi 1.1 içinde listelenen tüm algoritması paketlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="63bea-285">WCF supports all algorithm suites listed in Security Policy 1.1.</span></span>  
  
### <a name="25-key-derivation"></a><span data-ttu-id="63bea-286">2.5 anahtar türetme</span><span class="sxs-lookup"><span data-stu-id="63bea-286">2.5 Key Derivation</span></span>  
 <span data-ttu-id="63bea-287">WCF "Simetrik anahtarları için anahtar türetme" WS-SecureConversation açıklandığı gibi kullanır.</span><span class="sxs-lookup"><span data-stu-id="63bea-287">WCF uses "Key Derivation for symmetric keys" as described in WS-SecureConversation.</span></span>  
  
### <a name="26-signature-confirmation"></a><span data-ttu-id="63bea-288">2.6 imza onayı</span><span class="sxs-lookup"><span data-stu-id="63bea-288">2.6 Signature Confirmation</span></span>  
 <span data-ttu-id="63bea-289">İmza onayı imzaları kümesini korumak için ortadaki adam saldırılarına karşı koruma olarak olabilir.</span><span class="sxs-lookup"><span data-stu-id="63bea-289">Signature confirmation can be as protection from middle man attacks to protect the set of signatures.</span></span>  
  
### <a name="27-security-header-layout"></a><span data-ttu-id="63bea-290">2.7 güvenlik üstbilgi düzeni</span><span class="sxs-lookup"><span data-stu-id="63bea-290">2.7 Security Header Layout</span></span>  
 <span data-ttu-id="63bea-291">Her kimlik doğrulama modu güvenlik üstbilgisi için belirli bir düzen açıklar.</span><span class="sxs-lookup"><span data-stu-id="63bea-291">Each authentication mode describes a certain layout for the security header.</span></span> <span data-ttu-id="63bea-292">Güvenlik üstbilgisi içinde yarı sıralı öğelerdir.</span><span class="sxs-lookup"><span data-stu-id="63bea-292">Elements within the security header are semi-ordered.</span></span> <span data-ttu-id="63bea-293">Güvenlik üstbilgi alt öğelerin sırasını tanımlamak için aşağıdaki güvenlik üstbilgi düzeni modları WS-güvenlik ilkesini tanımlar:</span><span class="sxs-lookup"><span data-stu-id="63bea-293">To define the order of security header child elements, WS-Security Policy defines the following security header layout modes:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="63bea-294">Katı</span><span class="sxs-lookup"><span data-stu-id="63bea-294">Strict</span></span>|<span data-ttu-id="63bea-295">Öğeler "kullanılmadan önce bildirmek" prensibi güvenlik ilkesi Bölüm 7.7.1 genel göre numaralı düzeni kuralları açıklanan güvenlik üstbilgi aşağıdaki eklenir.</span><span class="sxs-lookup"><span data-stu-id="63bea-295">Items are added to the security header following the numbered layout rules described in Security Policy section 7.7.1 according to a general principle of "declare before use".</span></span>|  
|<span data-ttu-id="63bea-296">Belirsiz</span><span class="sxs-lookup"><span data-stu-id="63bea-296">Lax</span></span>|<span data-ttu-id="63bea-297">Öğeleri için WSS uyan herhangi bir sırada güvenlik üstbilgisi eklenir: SOAP ileti güvenliği.</span><span class="sxs-lookup"><span data-stu-id="63bea-297">Items are added to the security header in any order that conforms to WSS: SOAP Message Security.</span></span>|  
|<span data-ttu-id="63bea-298">LaxTimestampFirst</span><span class="sxs-lookup"><span data-stu-id="63bea-298">LaxTimestampFirst</span></span>|<span data-ttu-id="63bea-299">İlk öğe dışında güvenlik üstbilgisinde Lax bir wsse:Timestamp aynı olmalıdır</span><span class="sxs-lookup"><span data-stu-id="63bea-299">Same as Lax except that the first item in the security header must be a wsse:Timestamp</span></span>|  
|<span data-ttu-id="63bea-300">LaxTimestampLast</span><span class="sxs-lookup"><span data-stu-id="63bea-300">LaxTimestampLast</span></span>|<span data-ttu-id="63bea-301">Bir wsse:Timestamp son öğe dışında güvenlik üstbilgisinde belirsiz olarak aynı olmalıdır</span><span class="sxs-lookup"><span data-stu-id="63bea-301">Same as lax except that the last item in the security header must be a wsse:Timestamp</span></span>|  
  
 <span data-ttu-id="63bea-302">WCF güvenlik üstbilgi düzeni için tüm dört modlarını destekler.</span><span class="sxs-lookup"><span data-stu-id="63bea-302">WCF supports all four modes for security header layout.</span></span> <span data-ttu-id="63bea-303">Aşağıdaki kimlik doğrulama modları için güvenlik üstbilgi yapısı ve ileti örnekler "Strict" modu izleyin.</span><span class="sxs-lookup"><span data-stu-id="63bea-303">Security header structure and message examples for authentication modes below follow the "Strict" mode.</span></span>  
  
## <a name="2-common-message-security-parameters"></a><span data-ttu-id="63bea-304">2. Ortak ileti güvenlik parametreleri</span><span class="sxs-lookup"><span data-stu-id="63bea-304">2. Common Message Security Parameters</span></span>  
 <span data-ttu-id="63bea-305">Bu bölüm, istemci ve hizmet tarafından alınıp iletilerindeki güvenlik üst bilgisi yapısı gösteren örnekler yanı sıra her kimlik doğrulama modu için örnek ilkeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="63bea-305">This section provides example policies for each authentication mode along with examples showing security header structure in messages exchanged by client and service.</span></span>  
  
### <a name="61-transport-protection"></a><span data-ttu-id="63bea-306">6.1 taşıma koruma</span><span class="sxs-lookup"><span data-stu-id="63bea-306">6.1 Transport Protection</span></span>  
 <span data-ttu-id="63bea-307">WCF iletileri korumak için güvenli aktarım kullanmak beş kimlik doğrulama modları sağlar; UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport ve SspiNegotiatedOverTransport.</span><span class="sxs-lookup"><span data-stu-id="63bea-307">WCF provides five authentication modes that use secure transport to protect messages; UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport and SspiNegotiatedOverTransport.</span></span>  
  
 <span data-ttu-id="63bea-308">Bu kimlik doğrulama modları SecurityPolicy içinde açıklanan aktarım bağlama kullanılarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="63bea-308">These authentication modes are constructed using the transport binding described in SecurityPolicy.</span></span> <span data-ttu-id="63bea-309">UserNameOverTransport için kimlik doğrulama modu UsernameToken imzalı destekleme belirteci ' dir.</span><span class="sxs-lookup"><span data-stu-id="63bea-309">For the UserNameOverTransport authentication mode the UsernameToken is a signed supporting token.</span></span> <span data-ttu-id="63bea-310">Kimlik doğrulama modları belirteç imzalı onaylama belirteç olarak görünür.</span><span class="sxs-lookup"><span data-stu-id="63bea-310">For the other authentication modes the token appears as a signed endorsing token.</span></span> <span data-ttu-id="63bea-311">Ek C.1.2 ve C.1.3, SecurityPolicy ayrıntı güvenlik üstbilgisi yerleşiminde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="63bea-311">Appendix C.1.2 and C.1.3 of SecurityPolicy describe the security header layout in detail.</span></span> <span data-ttu-id="63bea-312">Aşağıdaki örnek güvenlik üstbilgileri bir belirli kimlik doğrulama modu katı düzenini gösterir.</span><span class="sxs-lookup"><span data-stu-id="63bea-312">The following example security headers show the Strict layout for a given authentication mode.</span></span>  
  
 <span data-ttu-id="63bea-313">Tüm durumlarda belirteçleri "Anahtarlar türetilen" özelliğinin değeri "false".</span><span class="sxs-lookup"><span data-stu-id="63bea-313">The value of the "Derived Keys" property for the tokens in all cases is "false".</span></span>  
  
 <span data-ttu-id="63bea-314">Aktarım bağlama çeşitli özelliklerinin değerleri aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="63bea-314">The values of the various properties of the transport binding are as follows:</span></span>  
  
 <span data-ttu-id="63bea-315">Zaman damgası: true</span><span class="sxs-lookup"><span data-stu-id="63bea-315">Timestamp: true</span></span>  
  
 <span data-ttu-id="63bea-316">Güvenlik üstbilgi Düzen: katı</span><span class="sxs-lookup"><span data-stu-id="63bea-316">Security Header Layout: Strict</span></span>  
  
 <span data-ttu-id="63bea-317">Algoritma paketini: Basic256</span><span class="sxs-lookup"><span data-stu-id="63bea-317">Algorithm Suite: Basic256</span></span>  
  
#### <a name="611-usernameovertransport"></a><span data-ttu-id="63bea-318">6.1.1 UsernameOverTransport</span><span class="sxs-lookup"><span data-stu-id="63bea-318">6.1.1 UsernameOverTransport</span></span>  
 <span data-ttu-id="63bea-319">Bu kimlik doğrulama modu ile SOAP katmanında başlatıcıdan alıcının her zaman gönderilen imzalı bir destekleme belirteci olarak görünen bir kullanıcı adı belirteci ile istemci kimliğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="63bea-319">With this authentication mode, the client authenticates with a Username Token which appears at the SOAP layer as a signed supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="63bea-320">Hizmet, aktarım katmanında bir X.509 sertifikası kullanılarak doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="63bea-320">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="63bea-321">Kullanılan bağlama aktarım bağlama ' dir.</span><span class="sxs-lookup"><span data-stu-id="63bea-321">The binding used is a transport binding.</span></span>  
  
 <span data-ttu-id="63bea-322">İlke</span><span class="sxs-lookup"><span data-stu-id="63bea-322">Policy</span></span>  
  
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
  
 <span data-ttu-id="63bea-323">Güvenlik üstbilgi düzeni</span><span class="sxs-lookup"><span data-stu-id="63bea-323">Security Header Layout</span></span>  
  
 <span data-ttu-id="63bea-324">İstek</span><span class="sxs-lookup"><span data-stu-id="63bea-324">Request</span></span>  
  
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
  
 <span data-ttu-id="63bea-325">Yanıt</span><span class="sxs-lookup"><span data-stu-id="63bea-325">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="612-certificateovertransport"></a><span data-ttu-id="63bea-326">6.1.2 CertificateOverTransport</span><span class="sxs-lookup"><span data-stu-id="63bea-326">6.1.2 CertificateOverTransport</span></span>  
 <span data-ttu-id="63bea-327">Bu kimlik doğrulama modu bir X.509 kullanarak istemcinin kimliğini doğrular SOAP katmanında başlatıcıdan alıcıya gönderilen her zaman bir onaylama destekleme belirteci olarak göründüğü sertifika.</span><span class="sxs-lookup"><span data-stu-id="63bea-327">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as an endorsing supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="63bea-328">Hizmet, aktarım katmanında bir X.509 sertifikası kullanılarak doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="63bea-328">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="63bea-329">Kullanılan bağlama aktarım bağlama ' dir.</span><span class="sxs-lookup"><span data-stu-id="63bea-329">The binding used is a transport binding.</span></span>  
  
 <span data-ttu-id="63bea-330">İlke</span><span class="sxs-lookup"><span data-stu-id="63bea-330">Policy</span></span>  
  
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
  
 <span data-ttu-id="63bea-331">Güvenlik üstbilgi düzeni</span><span class="sxs-lookup"><span data-stu-id="63bea-331">Security Header Layout</span></span>  
  
 <span data-ttu-id="63bea-332">İstek</span><span class="sxs-lookup"><span data-stu-id="63bea-332">Request</span></span>  
  
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
  
 <span data-ttu-id="63bea-333">Yanıt</span><span class="sxs-lookup"><span data-stu-id="63bea-333">Response</span></span>  
  
```xml  
<o:Security>  
  <u:Timestamp u:Id="_0">  
  ...  
  </u:Timestamp>  
</o:Security>  
```  
  
#### <a name="613-issuedtokenovertransport"></a><span data-ttu-id="63bea-334">6.1.3 IssuedTokenOverTransport</span><span class="sxs-lookup"><span data-stu-id="63bea-334">6.1.3 IssuedTokenOverTransport</span></span>  
 <span data-ttu-id="63bea-335">Bu kimlik doğrulama modu ile istemci hizmeti için bu nedenle, kimlik doğrulama kullanmaz, ancak yerine bir güvenlik belirteci hizmeti (STS) tarafından verilmiş bir belirteç sunar ve paylaşılan anahtar bilgi kanıtlar.</span><span class="sxs-lookup"><span data-stu-id="63bea-335">With this authentication mode the client does not authenticate to the service, as such, but rather presents a token issued by a Security Token Service (STS) and proves knowledge of a shared key.</span></span> <span data-ttu-id="63bea-336">Verilen belirteç SOAP katmanında başlatıcıdan alıcıya gönderilen her zaman bir onaylama destekleme belirteci olarak görünür.</span><span class="sxs-lookup"><span data-stu-id="63bea-336">The issued token appears at the SOAP layer as an endorsing supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="63bea-337">Hizmet, aktarım katmanında bir X.509 sertifikası kullanılarak doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="63bea-337">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="63bea-338">Bağlama aktarım bağlama ' dir.</span><span class="sxs-lookup"><span data-stu-id="63bea-338">The binding is a transport binding.</span></span>  
  
 <span data-ttu-id="63bea-339">İlke</span><span class="sxs-lookup"><span data-stu-id="63bea-339">Policy</span></span>  
  
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
  
 <span data-ttu-id="63bea-340">Güvenlik üstbilgi düzeni</span><span class="sxs-lookup"><span data-stu-id="63bea-340">Security Header Layout</span></span>  
  
 <span data-ttu-id="63bea-341">İstek</span><span class="sxs-lookup"><span data-stu-id="63bea-341">Request</span></span>  
  
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
  
 <span data-ttu-id="63bea-342">Yanıt</span><span class="sxs-lookup"><span data-stu-id="63bea-342">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="614-kerberosovertransport"></a><span data-ttu-id="63bea-343">6.1.4 KerberosOverTransport</span><span class="sxs-lookup"><span data-stu-id="63bea-343">6.1.4 KerberosOverTransport</span></span>  
 <span data-ttu-id="63bea-344">Bu kimlik doğrulama modu ile bir Kerberos anahtarı kullanarak hizmete istemci kimliğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="63bea-344">With this authentication mode the client authenticates to the service using a Kerberos ticket.</span></span> <span data-ttu-id="63bea-345">Kerberos belirteci SOAP katmanında bir onaylama destekleme belirteci görünür.</span><span class="sxs-lookup"><span data-stu-id="63bea-345">The Kerberos token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="63bea-346">Hizmet, aktarım katmanında bir X.509 sertifikası kullanılarak doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="63bea-346">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="63bea-347">Bağlama aktarım bağlama ' dir.</span><span class="sxs-lookup"><span data-stu-id="63bea-347">The binding is a transport binding.</span></span>  
  
 <span data-ttu-id="63bea-348">İlke</span><span class="sxs-lookup"><span data-stu-id="63bea-348">Policy</span></span>  
  
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
  
 <span data-ttu-id="63bea-349">Güvenlik üstbilgi düzeni</span><span class="sxs-lookup"><span data-stu-id="63bea-349">Security Header Layout</span></span>  
  
 <span data-ttu-id="63bea-350">İstek</span><span class="sxs-lookup"><span data-stu-id="63bea-350">Request</span></span>  
  
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
  
 <span data-ttu-id="63bea-351">Yanıt</span><span class="sxs-lookup"><span data-stu-id="63bea-351">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="615-sspinegotiatedovertransport"></a><span data-ttu-id="63bea-352">6.1.5 SspiNegotiatedOverTransport</span><span class="sxs-lookup"><span data-stu-id="63bea-352">6.1.5 SspiNegotiatedOverTransport</span></span>  
 <span data-ttu-id="63bea-353">Bu modda, istemci ve sunucu kimlik doğrulaması gerçekleştirmek için anlaşması protokolü kullanılır.</span><span class="sxs-lookup"><span data-stu-id="63bea-353">With this mode a negotiation protocol is used to perform client and server authentication.</span></span> <span data-ttu-id="63bea-354">Kerberos Mümkünse, kullanılan aksi NTLM.</span><span class="sxs-lookup"><span data-stu-id="63bea-354">Kerberos is used if possible, otherwise NTLM.</span></span> <span data-ttu-id="63bea-355">Sonuçta elde edilen SCT SOAP katmanında başlatıcıdan alıcıya gönderilen her zaman bir onaylama destekleme belirteci olarak görünür.</span><span class="sxs-lookup"><span data-stu-id="63bea-355">The resulting SCT appears at the SOAP layer as an endorsing supporting token that is always sent from initiator to recipient.</span></span> <span data-ttu-id="63bea-356">Hizmet, ayrıca aktarım katmanında bir X.509 sertifikası tarafından doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="63bea-356">The service is additionally authenticated at the transport layer by an X.509 certificate.</span></span> <span data-ttu-id="63bea-357">Kullanılan bağlama aktarım bağlama ' dir.</span><span class="sxs-lookup"><span data-stu-id="63bea-357">The binding used is a transport binding.</span></span> <span data-ttu-id="63bea-358">"SPNEGO" (anlaşma) WCF SSPI ikili anlaşma protokolü WS-Trust ile nasıl kullandığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="63bea-358">"SPNEGO" (negotiation) describes how WCF uses SSPI binary negotiation protocol with WS-Trust.</span></span> <span data-ttu-id="63bea-359">SCT SPNEGO el sıkışma kurulduktan sonra bu bölümde güvenlik üstbilgi örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="63bea-359">Security header examples in this section are after the SCT has been established through the SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="63bea-360">İlke</span><span class="sxs-lookup"><span data-stu-id="63bea-360">Policy</span></span>  
  
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
  
### <a name="security-header-examples"></a><span data-ttu-id="63bea-361">Güvenlik üstbilgi örnekler</span><span class="sxs-lookup"><span data-stu-id="63bea-361">Security Header Examples</span></span>  
 <span data-ttu-id="63bea-362">WS-Trust ikili anlaşma kullanarak SPNEGO el sıkışma ile güvenlik bağlamı belirteci kurulduktan sonra uygulama iletileri güvenlik üstbilgileri şu yapıda vardır.</span><span class="sxs-lookup"><span data-stu-id="63bea-362">Once the Security Context Token is established through SPNEGO handshake using WS-Trust Binary Negotiation, the application messages have security headers with the following structure.</span></span>  
  
 <span data-ttu-id="63bea-363">İstek</span><span class="sxs-lookup"><span data-stu-id="63bea-363">Request</span></span>  
  
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
  
 <span data-ttu-id="63bea-364">Yanıt</span><span class="sxs-lookup"><span data-stu-id="63bea-364">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
### <a name="62-using-x509-certificates-for-service-authentication"></a><span data-ttu-id="63bea-365">6.2 X.509 sertifikalarını hizmet kimlik doğrulaması kullanma</span><span class="sxs-lookup"><span data-stu-id="63bea-365">6.2 Using X.509 Certificates for Service Authentication</span></span>  
 <span data-ttu-id="63bea-366">Bu bölümde aşağıdaki kimlik doğrulama modları açıklanır: MutualCertificate WSS1.0, karşılıklı CertificateDuplex, MutualCertificate WSS1.1, AnonymousForCertificate, UserNameForCertificate ve IssuedTokenForCertificate.</span><span class="sxs-lookup"><span data-stu-id="63bea-366">This section describes the following authentication modes: MutualCertificate WSS1.0, Mutual CertificateDuplex, MutualCertificate WSS1.1, AnonymousForCertificate, UserNameForCertificate and IssuedTokenForCertificate.</span></span>  
  
#### <a name="621-mutualcertificate-wss10"></a><span data-ttu-id="63bea-367">6.2.1 MutualCertificate WSS1.0</span><span class="sxs-lookup"><span data-stu-id="63bea-367">6.2.1 MutualCertificate WSS1.0</span></span>  
 <span data-ttu-id="63bea-368">Bu kimlik doğrulama modu bir X.509 kullanarak istemcinin kimliğini doğrular, başlatıcı belirteç olarak SOAP katmanında göründüğü sertifika.</span><span class="sxs-lookup"><span data-stu-id="63bea-368">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as the initiator token.</span></span> <span data-ttu-id="63bea-369">Hizmet, ayrıca bir X.509 sertifikası kullanılarak kimlik doğrulaması yapılır.</span><span class="sxs-lookup"><span data-stu-id="63bea-369">The service is also authenticated using an X.509 certificate.</span></span>  
  
 <span data-ttu-id="63bea-370">Aşağıdaki özellik değerlerini asimetrik bir bağlamayla kullanılan bağlama şöyledir:</span><span class="sxs-lookup"><span data-stu-id="63bea-370">The binding used is an asymmetric binding with the following property values:</span></span>  
  
 <span data-ttu-id="63bea-371">Başlatıcı belirteç: ekleme modu için .../IncludeToken/AlwaysToRecipient ayarlandığında istemcinin X.509 sertifikası</span><span class="sxs-lookup"><span data-stu-id="63bea-371">Initiator Token: the client’s X.509 certificate, with inclusion mode set to …/IncludeToken/AlwaysToRecipient</span></span>  
  
 <span data-ttu-id="63bea-372">Alıcı belirteç: Sunucu X.509 sertifikası kullanıcının, ekleme moduyla .../IncludeToken/Never ayarlanır</span><span class="sxs-lookup"><span data-stu-id="63bea-372">Recipient Token: Server’s X.509 Certificate, with inclusion mode is set …/IncludeToken/Never</span></span>  
  
 <span data-ttu-id="63bea-373">Simge koruma: yanlış</span><span class="sxs-lookup"><span data-stu-id="63bea-373">Token Protection: False</span></span>  
  
 <span data-ttu-id="63bea-374">Tüm üstbilgi ve gövde imzalar: True</span><span class="sxs-lookup"><span data-stu-id="63bea-374">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="63bea-375">Koruma sırasını: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="63bea-375">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="63bea-376">İmza şifrelemek: True</span><span class="sxs-lookup"><span data-stu-id="63bea-376">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="63bea-377">İlke</span><span class="sxs-lookup"><span data-stu-id="63bea-377">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="63bea-378">Güvenlik üstbilgi örnekler: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="63bea-378">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="63bea-379">İstek</span><span class="sxs-lookup"><span data-stu-id="63bea-379">Request</span></span>  
  
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
  
 <span data-ttu-id="63bea-380">Yanıt</span><span class="sxs-lookup"><span data-stu-id="63bea-380">Response</span></span>  
  
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
  
 <span data-ttu-id="63bea-381">Güvenlik üstbilgi örnekler: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="63bea-381">Security Header Examples: EncryptBeforeSign</span></span>  
  
 <span data-ttu-id="63bea-382">İstek</span><span class="sxs-lookup"><span data-stu-id="63bea-382">Request</span></span>  
  
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
  
 <span data-ttu-id="63bea-383">Yanıt</span><span class="sxs-lookup"><span data-stu-id="63bea-383">Response</span></span>  
  
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
  
#### <a name="622-mutualcertificateduplex"></a><span data-ttu-id="63bea-384">6.2.2 MutualCertificateDuplex</span><span class="sxs-lookup"><span data-stu-id="63bea-384">6.2.2 MutualCertificateDuplex</span></span>  
 <span data-ttu-id="63bea-385">Bu kimlik doğrulama modu bir X.509 kullanarak istemcinin kimliğini doğrular, başlatıcı belirteç olarak SOAP katmanında göründüğü sertifika.</span><span class="sxs-lookup"><span data-stu-id="63bea-385">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as the initiator token.</span></span> <span data-ttu-id="63bea-386">Hizmet, ayrıca bir X.509 sertifikası kullanılarak kimlik doğrulaması yapılır.</span><span class="sxs-lookup"><span data-stu-id="63bea-386">The service is also authenticated using an X.509 certificate.</span></span>  
  
 <span data-ttu-id="63bea-387">Aşağıdaki özellik değerlerini asimetrik bir bağlamayla kullanılan bağlama şöyledir:</span><span class="sxs-lookup"><span data-stu-id="63bea-387">The binding used is an asymmetric binding with the following property values:</span></span>  
  
 <span data-ttu-id="63bea-388">Başlatıcı belirteç: İstemcinin X509 sertifikası ekleme modu için .../IncludeToken/AlwaysToRecipient ayarlanır</span><span class="sxs-lookup"><span data-stu-id="63bea-388">Initiator Token: Client’s X509 Certificate, inclusion mode is set to …/IncludeToken/AlwaysToRecipient</span></span>  
  
 <span data-ttu-id="63bea-389">Alıcı belirteç: Sunucunun X509 sertifikası ekleme modu için .../IncludeToken/AlwaysToInitiator ayarlanır</span><span class="sxs-lookup"><span data-stu-id="63bea-389">Recipient Token: Server’s X509 Certificate, inclusion mode is set to …/IncludeToken/AlwaysToInitiator</span></span>  
  
 <span data-ttu-id="63bea-390">Simge koruma: yanlış</span><span class="sxs-lookup"><span data-stu-id="63bea-390">Token Protection: False</span></span>  
  
 <span data-ttu-id="63bea-391">Tüm üstbilgi ve gövde imzalar: True</span><span class="sxs-lookup"><span data-stu-id="63bea-391">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="63bea-392">Koruma sırasını: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="63bea-392">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="63bea-393">İmza şifrelemek: True</span><span class="sxs-lookup"><span data-stu-id="63bea-393">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="63bea-394">İlke</span><span class="sxs-lookup"><span data-stu-id="63bea-394">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="63bea-395">Güvenlik üstbilgi örnekler: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="63bea-395">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="63bea-396">İstek ve yanıt</span><span class="sxs-lookup"><span data-stu-id="63bea-396">Request and Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="63bea-397">Güvenlik üstbilgi örnekler: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="63bea-397">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="63bea-398">İstek ve yanıt</span><span class="sxs-lookup"><span data-stu-id="63bea-398">Request and Response</span></span>  
  
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
  
#### <a name="623-using-symmetricbinding-with-x509-service-authentication"></a><span data-ttu-id="63bea-399">6.2.3 SymmetricBinding X.509 hizmet kimlik doğrulaması ile kullanma</span><span class="sxs-lookup"><span data-stu-id="63bea-399">6.2.3 Using SymmetricBinding with X.509 Service Authentication</span></span>  
 <span data-ttu-id="63bea-400">"WSS10" X509 ile senaryoları için sınırlı destek sağlanan belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="63bea-400">"WSS10" provided limited support for scenarios with X509 tokens.</span></span> <span data-ttu-id="63bea-401">Örneğin, yalnızca hizmet X509 belirteci kullanarak iletileri için imza ve şifreleme koruma sağlamak üzere hiçbir yolu yoktu.</span><span class="sxs-lookup"><span data-stu-id="63bea-401">For example, there was no way to provide signature and encryption protection for messages using only service X509 token.</span></span> <span data-ttu-id="63bea-402">"WSS11" EncryptedKey kullanımını simetrik belirteç olarak kullanıma sunuldu.</span><span class="sxs-lookup"><span data-stu-id="63bea-402">"WSS11" introduced the usage of EncryptedKey as a symmetric token.</span></span> <span data-ttu-id="63bea-403">Şimdi hizmetin X.509 sertifikası şifrelenmiş geçici bir anahtar istek ve yanıt iletileri koruma için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="63bea-403">Now a temporary key encrypted for the service's X.509 certificate could be used for both request and response messages protection.</span></span> <span data-ttu-id="63bea-404">6.4 bölümünde açıklanan kimlik doğrulama modları bu deseni kullanır.</span><span class="sxs-lookup"><span data-stu-id="63bea-404">The authentication modes described in the section 6.4 below use this pattern.</span></span>  
  
 <span data-ttu-id="63bea-405">WS-SecurityPolicy hizmetiyle SymmetricBinding kullanarak bu deseni açıklar X509 koruma belirteci olarak simge.</span><span class="sxs-lookup"><span data-stu-id="63bea-405">WS-SecurityPolicy describes this pattern using SymmetricBinding with Service X509 token as the protection token.</span></span>  
  
 <span data-ttu-id="63bea-406">Kimlik doğrulama modları AnonymousForCertificate, UsernameForCertificate, MutualCertificate WSS11 ve IssuedTokenForCertificate tüm sp:SymmetricBinding benzer bir örneğini aşağıdaki özellik değerleriyle kullanın:</span><span class="sxs-lookup"><span data-stu-id="63bea-406">Authentication modes AnonymousForCertificate, UsernameForCertificate, MutualCertificate WSS11 and IssuedTokenForCertificate all use a similar instance of sp:SymmetricBinding with the following property values:</span></span>  
  
 <span data-ttu-id="63bea-407">Koruma simgesi: Sunucunun X509 sertifikası ekleme modu için .../IncludeToken/Never ayarlanır</span><span class="sxs-lookup"><span data-stu-id="63bea-407">Protection Token: Server’s X509 Certificate, inclusion mode is set to .../IncludeToken/Never</span></span>  
<span data-ttu-id="63bea-408">Simge koruma: yanlış</span><span class="sxs-lookup"><span data-stu-id="63bea-408">Token Protection: False</span></span>  
  
 <span data-ttu-id="63bea-409">Tüm üstbilgi ve gövde imzalar: True</span><span class="sxs-lookup"><span data-stu-id="63bea-409">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="63bea-410">Koruma sırasını: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="63bea-410">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="63bea-411">İmza şifrelemek: True</span><span class="sxs-lookup"><span data-stu-id="63bea-411">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="63bea-412">Yukarıdaki kimlik doğrulama modları yalnızca kullandıkları destek belirteçleri göre farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="63bea-412">The above authentication modes only differ by the supporting tokens they use.</span></span> <span data-ttu-id="63bea-413">AnonymousForCertificate destekleyen herhangi bir belirtece sahip değil ve MutualCertificate WSS 1.1 sahip istemcinin X509 bir destek belirteçleri onaylama olarak sertifika, UserNameForCertificate sahip bir kullanıcı adı belirteci imzalı destekleme belirteci olarak ve IssuedTokenForCertificate bir onaylama destekleme belirteci verilen belirteç vardır.</span><span class="sxs-lookup"><span data-stu-id="63bea-413">AnonymousForCertificate does not have any supporting tokens, MutualCertificate WSS 1.1 has the client’s X509 certificate as an endorsing supporting tokens, UserNameForCertificate has a UserName Token as a signed supporting token and IssuedTokenForCertificate has the issued token as an endorsing supporting token.</span></span>  
  
 <span data-ttu-id="63bea-414">İlke</span><span class="sxs-lookup"><span data-stu-id="63bea-414">Policy</span></span>  
  
 <span data-ttu-id="63bea-415">Simetrik bağlama</span><span class="sxs-lookup"><span data-stu-id="63bea-415">Symmetric Binding</span></span>  
  
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
  
#### <a name="624-anonymousforcertificate"></a><span data-ttu-id="63bea-416">6.2.4 AnonymousForCertificate</span><span class="sxs-lookup"><span data-stu-id="63bea-416">6.2.4 AnonymousForCertificate</span></span>  
 <span data-ttu-id="63bea-417">Bu kimlik doğrulama modu ile istemci anonimdir ve hizmeti bir X.509 sertifikası kullanılarak doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="63bea-417">With this authentication mode the client is anonymous and the service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="63bea-418">Kullanılan bağlama 6.4.2 anlatıldığı gibi simetrik bağlama bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="63bea-418">The binding used is an instance of symmetric binding as described in 6.4.2.</span></span>  
  
 <span data-ttu-id="63bea-419">İlke</span><span class="sxs-lookup"><span data-stu-id="63bea-419">Policy</span></span>  
  
 <span data-ttu-id="63bea-420">Ayrıntılar bağlama için yukarıdaki 6.2.3 "ilke" konusuna bakın</span><span class="sxs-lookup"><span data-stu-id="63bea-420">See "Policy" in 6.2.3 above for binding details</span></span>  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="63bea-421">Güvenlik üstbilgi örnekler: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="63bea-421">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="63bea-422">İstek</span><span class="sxs-lookup"><span data-stu-id="63bea-422">Request</span></span>  
  
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
  
 <span data-ttu-id="63bea-423">Yanıt</span><span class="sxs-lookup"><span data-stu-id="63bea-423">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="63bea-424">Güvenlik üstbilgi örnekler: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="63bea-424">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="63bea-425">İstek</span><span class="sxs-lookup"><span data-stu-id="63bea-425">Request</span></span>  
  
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
  
 <span data-ttu-id="63bea-426">Yanıt</span><span class="sxs-lookup"><span data-stu-id="63bea-426">Response</span></span>  
  
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
  
#### <a name="625-usernameforcertificate"></a><span data-ttu-id="63bea-427">6.2.5 UserNameForCertificate</span><span class="sxs-lookup"><span data-stu-id="63bea-427">6.2.5 UserNameForCertificate</span></span>  
 <span data-ttu-id="63bea-428">Bu kimlik doğrulama modu ile istemci hizmeti görünen bir kullanıcı adı belirteci SOAP katmanında imzalı destekleme belirteci olarak kullanarak kimliğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="63bea-428">With this authentication mode the client authenticates to the service using a Username Token which appears at the SOAP layer as a signed supporting token.</span></span> <span data-ttu-id="63bea-429">Hizmet bir X.509 sertifikası kullanarak istemcinin kimliğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="63bea-429">The service authenticates to the client using an X.509 certificate.</span></span> <span data-ttu-id="63bea-430">Kullanılan bağlama simetrik bağlama hizmet ortak anahtarıyla şifrelenir istemci tarafından oluşturulan bir anahtarı olan koruma belirtecine sahip olur.</span><span class="sxs-lookup"><span data-stu-id="63bea-430">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="63bea-431">İlke</span><span class="sxs-lookup"><span data-stu-id="63bea-431">Policy</span></span>  
  
 <span data-ttu-id="63bea-432">Ayrıntılar bağlama için yukarıdaki 6.2.3 "ilke" konusuna bakın</span><span class="sxs-lookup"><span data-stu-id="63bea-432">See "Policy" in 6.2.3 above for binding details</span></span>  
  
 <span data-ttu-id="63bea-433">Destek belirteci imzalayan</span><span class="sxs-lookup"><span data-stu-id="63bea-433">Signed Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="63bea-434">Güvenlik üstbilgi örnekler: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="63bea-434">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="63bea-435">İstek</span><span class="sxs-lookup"><span data-stu-id="63bea-435">Request</span></span>  
  
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
  
 <span data-ttu-id="63bea-436">Yanıt</span><span class="sxs-lookup"><span data-stu-id="63bea-436">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="63bea-437">Güvenlik üstbilgi örnekler: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="63bea-437">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="63bea-438">İstek</span><span class="sxs-lookup"><span data-stu-id="63bea-438">Request</span></span>  
  
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
  
 <span data-ttu-id="63bea-439">Yanıt</span><span class="sxs-lookup"><span data-stu-id="63bea-439">Response</span></span>  
  
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
  
#### <a name="626-mutualcertificate-wss-11"></a><span data-ttu-id="63bea-440">6.2.6 MutualCertificate (WSS 1.1)</span><span class="sxs-lookup"><span data-stu-id="63bea-440">6.2.6 MutualCertificate (WSS 1.1)</span></span>  
 <span data-ttu-id="63bea-441">Bu kimlik doğrulama modu bir X.509 kullanarak istemcinin kimliğini doğrular, SOAP katmanında bir onaylama destekleme belirteci olarak göründüğü sertifika.</span><span class="sxs-lookup"><span data-stu-id="63bea-441">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="63bea-442">Hizmet, ayrıca bir X.509 sertifikası kullanılarak kimlik doğrulaması yapılır.</span><span class="sxs-lookup"><span data-stu-id="63bea-442">The service is also authenticated using an X.509 certificate.</span></span> <span data-ttu-id="63bea-443">Kullanılan bağlama simetrik bağlama hizmet ortak anahtarıyla şifrelenir istemci tarafından oluşturulan bir anahtarı olan koruma belirtecine sahip olur.</span><span class="sxs-lookup"><span data-stu-id="63bea-443">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="63bea-444">İlke</span><span class="sxs-lookup"><span data-stu-id="63bea-444">Policy</span></span>  
  
 <span data-ttu-id="63bea-445">İlke 6.2.3 bağlama ayrıntıları için bkz.</span><span class="sxs-lookup"><span data-stu-id="63bea-445">See Policy in 6.2.3 for binding details</span></span>  
  
 <span data-ttu-id="63bea-446">Belirteç destekleme onaylama</span><span class="sxs-lookup"><span data-stu-id="63bea-446">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="63bea-447">Güvenlik üstbilgi örnekler: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="63bea-447">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="63bea-448">İstek</span><span class="sxs-lookup"><span data-stu-id="63bea-448">Request</span></span>  
  
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
  
 <span data-ttu-id="63bea-449">Yanıt</span><span class="sxs-lookup"><span data-stu-id="63bea-449">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="63bea-450">Güvenlik üstbilgi örnekler: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="63bea-450">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="63bea-451">İstek</span><span class="sxs-lookup"><span data-stu-id="63bea-451">Request</span></span>  
  
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
  
 <span data-ttu-id="63bea-452">Yanıt</span><span class="sxs-lookup"><span data-stu-id="63bea-452">Response</span></span>  
  
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
  
#### <a name="627-issuedtokenforcertificate"></a><span data-ttu-id="63bea-453">6.2.7 IssuedTokenForCertificate</span><span class="sxs-lookup"><span data-stu-id="63bea-453">6.2.7 IssuedTokenForCertificate</span></span>  
 <span data-ttu-id="63bea-454">Bu kimlik doğrulaması ile istemci hizmeti için bu nedenle, ancak bunun yerine kimlik doğrulamasını yapmaz modu STS tarafından verilmiş bir belirteç gösterir ve paylaşılan anahtar bilgi kanıtlar.</span><span class="sxs-lookup"><span data-stu-id="63bea-454">With this authentication mode the client does not authenticate to the service, as such, but instead presents a token issued by a STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="63bea-455">Verilen belirteç SOAP katmanında bir onaylama destekleme belirteci görünür.</span><span class="sxs-lookup"><span data-stu-id="63bea-455">The issued token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="63bea-456">Hizmet bir X.509 sertifikası kullanarak istemcinin kimliğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="63bea-456">The service authenticates to the client using an X.509 certificate.</span></span> <span data-ttu-id="63bea-457">Kullanılan bağlama simetrik bağlama hizmet ortak anahtarıyla şifrelenir istemci tarafından oluşturulan bir anahtarı olan koruma belirtecine sahip olur.</span><span class="sxs-lookup"><span data-stu-id="63bea-457">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="63bea-458">İlke</span><span class="sxs-lookup"><span data-stu-id="63bea-458">Policy</span></span>  
  
 <span data-ttu-id="63bea-459">İlke 6.2.3 Bağlama Ayrıntılar için bkz.</span><span class="sxs-lookup"><span data-stu-id="63bea-459">See Policy in 6.2.3 above for binding details</span></span>  
  
 <span data-ttu-id="63bea-460">Belirteç destekleme onaylama</span><span class="sxs-lookup"><span data-stu-id="63bea-460">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="63bea-461">Güvenlik üstbilgi örnekler: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="63bea-461">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="63bea-462">İstek</span><span class="sxs-lookup"><span data-stu-id="63bea-462">Request</span></span>  
  
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
  
 <span data-ttu-id="63bea-463">Yanıt</span><span class="sxs-lookup"><span data-stu-id="63bea-463">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="63bea-464">Güvenlik üstbilgi örnekler: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="63bea-464">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="63bea-465">İstek</span><span class="sxs-lookup"><span data-stu-id="63bea-465">Request</span></span>  
  
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
  
 <span data-ttu-id="63bea-466">Yanıt</span><span class="sxs-lookup"><span data-stu-id="63bea-466">Response</span></span>  
  
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
  
## <a name="63-kerberos"></a><span data-ttu-id="63bea-467">6.3 Kerberos</span><span class="sxs-lookup"><span data-stu-id="63bea-467">6.3 Kerberos</span></span>  
 <span data-ttu-id="63bea-468">Bu kimlik doğrulama modu ile bir Kerberos anahtarı kullanarak hizmete istemci kimliğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="63bea-468">With this authentication mode the client authenticates to the service using a Kerberos ticket.</span></span> <span data-ttu-id="63bea-469">Bu aynı anahtar Ayrıca sunucu kimlik doğrulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="63bea-469">That same ticket also provides server authentication.</span></span> <span data-ttu-id="63bea-470">Kullanılan bağlama simetrik bağlama aşağıdaki özelliklere sahip olur;</span><span class="sxs-lookup"><span data-stu-id="63bea-470">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="63bea-471">Koruma simgesi: Kerberos bileti için .../IncludeToken/Once ekleme modu ayarlanır</span><span class="sxs-lookup"><span data-stu-id="63bea-471">Protection Token: Kerberos Ticket, inclusion mode is set to .../IncludeToken/Once</span></span>  
<span data-ttu-id="63bea-472">Simge koruma: yanlış</span><span class="sxs-lookup"><span data-stu-id="63bea-472">Token Protection: False</span></span>  
  
 <span data-ttu-id="63bea-473">Tüm üstbilgi ve gövde imzalar: True</span><span class="sxs-lookup"><span data-stu-id="63bea-473">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="63bea-474">Koruma sırasını: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="63bea-474">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="63bea-475">İmza şifrelemek: True</span><span class="sxs-lookup"><span data-stu-id="63bea-475">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="63bea-476">İlke</span><span class="sxs-lookup"><span data-stu-id="63bea-476">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="63bea-477">Güvenlik üstbilgi örnekler: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="63bea-477">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="63bea-478">İstek</span><span class="sxs-lookup"><span data-stu-id="63bea-478">Request</span></span>  
  
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
  
 <span data-ttu-id="63bea-479">Yanıt</span><span class="sxs-lookup"><span data-stu-id="63bea-479">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="63bea-480">Güvenlik üstbilgi örnekler: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="63bea-480">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="63bea-481">İstek</span><span class="sxs-lookup"><span data-stu-id="63bea-481">Request</span></span>  
  
```xml  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
 <span data-ttu-id="63bea-482">Yanıt</span><span class="sxs-lookup"><span data-stu-id="63bea-482">Response</span></span>  
  
```xml  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
#### <a name="64-issuedtoken"></a><span data-ttu-id="63bea-483">6.4 IssuedToken</span><span class="sxs-lookup"><span data-stu-id="63bea-483">6.4 IssuedToken</span></span>  
 <span data-ttu-id="63bea-484">İstemci hizmete kimlik doğrulama kullanmaz, bu kimlik doğrulama modu ile bu nedenle yerine istemci bir STS tarafından verilmiş bir belirteç gösterir ve paylaşılan anahtar bilgi kanıtlar.</span><span class="sxs-lookup"><span data-stu-id="63bea-484">With this authentication mode the client does not authenticate to the service, as such, rather the client presents a token issued by an STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="63bea-485">Hizmet istemcisi için bu nedenle kimlik doğrulaması yapılamıyor, bunun yerine STS şifreler paylaşılan anahtar verilen belirteç bir parçası olarak sağlayacak şekilde yalnızca hizmeti anahtarı şifresini çözebilir.</span><span class="sxs-lookup"><span data-stu-id="63bea-485">The service is not authenticated to the client, as such, instead the STS encrypts the shared key as part of the issued token such that only the service can decrypt the key.</span></span> <span data-ttu-id="63bea-486">Aşağıdaki özelliklerle simetrik bağlama kullanılan bağlama gibidir;</span><span class="sxs-lookup"><span data-stu-id="63bea-486">The binding used is as symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="63bea-487">Koruma: Belirteci belirteç, ekleme modu için .../IncludeToken/AlwaysToRecipient ayarlanır</span><span class="sxs-lookup"><span data-stu-id="63bea-487">Protection Token: Issued Token, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
<span data-ttu-id="63bea-488">Simge koruma: yanlış</span><span class="sxs-lookup"><span data-stu-id="63bea-488">Token Protection: False</span></span>  
  
 <span data-ttu-id="63bea-489">Tüm üstbilgi ve gövde imzalar: True</span><span class="sxs-lookup"><span data-stu-id="63bea-489">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="63bea-490">Koruma sırasını: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="63bea-490">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="63bea-491">İmza şifrelemek: True</span><span class="sxs-lookup"><span data-stu-id="63bea-491">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="63bea-492">İlke</span><span class="sxs-lookup"><span data-stu-id="63bea-492">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="63bea-493">Güvenlik üstbilgi örnekler: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="63bea-493">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="63bea-494">İstek</span><span class="sxs-lookup"><span data-stu-id="63bea-494">Request</span></span>  
  
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
  
 <span data-ttu-id="63bea-495">Yanıt</span><span class="sxs-lookup"><span data-stu-id="63bea-495">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="63bea-496">Güvenlik üstbilgi örnekler: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="63bea-496">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="63bea-497">İstek</span><span class="sxs-lookup"><span data-stu-id="63bea-497">Request</span></span>  
  
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
  
 <span data-ttu-id="63bea-498">Yanıt</span><span class="sxs-lookup"><span data-stu-id="63bea-498">Response</span></span>  
  
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
  
### <a name="65-using-sslnegotiated-for-service-authentication"></a><span data-ttu-id="63bea-499">6.5 SslNegotiated hizmet kimlik doğrulaması kullanma</span><span class="sxs-lookup"><span data-stu-id="63bea-499">6.5 Using SslNegotiated for Service Authentication</span></span>  
 <span data-ttu-id="63bea-500">Bu bölümde bir grup bir güvenlik bağlamı belirteci başına WS-anahtar değeri anlaşılan WS-Trust (WS-T) RST TLS protokolünü yürüterek SecureConversation (WS-SC) olan koruma belirteci ile bir simetrik bağlamayı kullanan kimlik doğrulama modları açıklanır / RSTR iletileri.</span><span class="sxs-lookup"><span data-stu-id="63bea-500">This section describes a group of authentication modes that use a symmetric binding with the protection token being a Security Context Token per WS-SecureConversation (WS-SC) whose key value is negotiated by executing the TLS protocol over WS-Trust (WS-T) RST/RSTR messages.</span></span> <span data-ttu-id="63bea-501">WS-Trust kullanarak TLS el sıkışma uygulama ayrıntılarını TLSNEGO içinde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="63bea-501">Details of the TLS handshake implementation using WS-Trust are described in TLSNEGO.</span></span> <span data-ttu-id="63bea-502">Burada ileti örneklerde SCT ilişkili güvenlik bağlamına sahip bir el sıkışması önceden oluşturulmuş varsayacağız.</span><span class="sxs-lookup"><span data-stu-id="63bea-502">Here in the message examples we will assume that SCT with an associated security context is already established through a handshake.</span></span>  
  
 <span data-ttu-id="63bea-503">Kullanılan bağlama simetrik bağlama aşağıdaki özelliklere sahip olur;</span><span class="sxs-lookup"><span data-stu-id="63bea-503">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="63bea-504">Koruma simgesi: SslContextToken, .../IncludeToken/Never için ekleme modu ayarlanır</span><span class="sxs-lookup"><span data-stu-id="63bea-504">Protection Token: SslContextToken, inclusion mode is set to .../IncludeToken/Never</span></span>  
<span data-ttu-id="63bea-505">Simge koruma: yanlış</span><span class="sxs-lookup"><span data-stu-id="63bea-505">Token Protection: False</span></span>  
  
 <span data-ttu-id="63bea-506">Tüm üstbilgi ve gövde imzalar: True</span><span class="sxs-lookup"><span data-stu-id="63bea-506">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="63bea-507">Koruma sırasını: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="63bea-507">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="63bea-508">İmza şifrelemek: True</span><span class="sxs-lookup"><span data-stu-id="63bea-508">Encrypt Signature: True</span></span>  
  
#### <a name="651-policy-for-sslnegotiated-service-authentication"></a><span data-ttu-id="63bea-509">6.5.1 SslNegotiated hizmeti kimlik doğrulama için İlkesi</span><span class="sxs-lookup"><span data-stu-id="63bea-509">6.5.1 Policy for SslNegotiated service authentication</span></span>  
 <span data-ttu-id="63bea-510">Bu bölümdeki tüm kimlik doğrulama modu için ilke benzerdir ve yalnızca özel imzalı destekleme veya kullanılan belirteçleri onaylama tarafından farklıdır.</span><span class="sxs-lookup"><span data-stu-id="63bea-510">Policy for all authentication modes in this section are similar and differ only by specific signed supporting or endorsing tokens used.</span></span>  
  
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
  
#### <a name="652-anonymousforsslnegotiated"></a><span data-ttu-id="63bea-511">6.5.2 AnonymousForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="63bea-511">6.5.2 AnonymousForSslNegotiated</span></span>  
 <span data-ttu-id="63bea-512">Bu kimlik doğrulama modu ile istemci anonimdir ve hizmeti bir X.509 sertifikası kullanılarak doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="63bea-512">With this authentication mode the client is anonymous and the service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="63bea-513">Kullanılan bağlama 6.5.1 yukarıda açıklandığı gibi simetrik bağlama bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="63bea-513">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="63bea-514">İlke</span><span class="sxs-lookup"><span data-stu-id="63bea-514">Policy</span></span>  
  
 <span data-ttu-id="63bea-515">6.5.1 Bağlama Ayrıntılar için bkz.</span><span class="sxs-lookup"><span data-stu-id="63bea-515">See Policy in 6.5.1 above for binding details.</span></span>  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="63bea-516">Güvenlik üstbilgi örnekler: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="63bea-516">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="63bea-517">İstek</span><span class="sxs-lookup"><span data-stu-id="63bea-517">Request</span></span>  
  
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
  
 <span data-ttu-id="63bea-518">Yanıt</span><span class="sxs-lookup"><span data-stu-id="63bea-518">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="63bea-519">Güvenlik üstbilgi örnekler: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="63bea-519">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="63bea-520">İstek</span><span class="sxs-lookup"><span data-stu-id="63bea-520">Request</span></span>  
  
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
  
 <span data-ttu-id="63bea-521">Yanıt</span><span class="sxs-lookup"><span data-stu-id="63bea-521">Response</span></span>  
  
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
  
#### <a name="653-usernameforsslnegotiated"></a><span data-ttu-id="63bea-522">6.5.3 UserNameForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="63bea-522">6.5.3 UserNameForSslNegotiated</span></span>  
 <span data-ttu-id="63bea-523">Bu kimlik doğrulaması ile görüntülenen bir kullanıcı adı belirteci SOAP katmanında imzalı destekleme belirteci olarak kullanan istemci modu kimliğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="63bea-523">With this authentication mode the client is authenticates using a Username Token which appears at the SOAP layer as a signed supporting token.</span></span> <span data-ttu-id="63bea-524">Hizmet, bir X.509 sertifikası kullanılarak doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="63bea-524">The service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="63bea-525">Kullanılan bağlama 6.5.1 anlatıldığı gibi simetrik bağlama bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="63bea-525">The binding used is an instance of symmetric binding as described in 6.5.1.</span></span>  
  
 <span data-ttu-id="63bea-526">İlke</span><span class="sxs-lookup"><span data-stu-id="63bea-526">Policy</span></span>  
  
 <span data-ttu-id="63bea-527">Ayrıntılar bağlama için yukarıdaki 6.5.1 bölümüne bakın</span><span class="sxs-lookup"><span data-stu-id="63bea-527">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="63bea-528">Destek belirteci imzalayan</span><span class="sxs-lookup"><span data-stu-id="63bea-528">Signed Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="63bea-529">Güvenlik üstbilgi örnekler: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="63bea-529">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="63bea-530">İstek</span><span class="sxs-lookup"><span data-stu-id="63bea-530">Request</span></span>  
  
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
  
 <span data-ttu-id="63bea-531">Yanıt</span><span class="sxs-lookup"><span data-stu-id="63bea-531">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="63bea-532">Güvenlik üstbilgi örnekler: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="63bea-532">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="63bea-533">İstek</span><span class="sxs-lookup"><span data-stu-id="63bea-533">Request</span></span>  
  
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
  
 <span data-ttu-id="63bea-534">Yanıt</span><span class="sxs-lookup"><span data-stu-id="63bea-534">Response</span></span>  
  
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
  
#### <a name="654-issuedtokenforsslnegotiated"></a><span data-ttu-id="63bea-535">6.5.4 IssuedTokenForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="63bea-535">6.5.4 IssuedTokenForSslNegotiated</span></span>  
 <span data-ttu-id="63bea-536">Bu kimlik doğrulaması ile istemci hizmeti için bu nedenle, ancak bunun yerine kimlik doğrulamasını yapmaz modu bir STS tarafından verilmiş bir belirteç gösterir ve paylaşılan anahtar bilgi kanıtlar.</span><span class="sxs-lookup"><span data-stu-id="63bea-536">With this authentication mode the client does not authenticate to the service, as such, but instead presents a token issued by an STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="63bea-537">Verilen belirteç SOAP katmanında bir onaylama destekleme belirteci görünür.</span><span class="sxs-lookup"><span data-stu-id="63bea-537">The issued token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="63bea-538">Hizmet, bir X.509 sertifikası kullanılarak doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="63bea-538">The service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="63bea-539">Kullanılan bağlama 6.5.1 yukarıda açıklandığı gibi simetrik bağlama bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="63bea-539">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="63bea-540">İlke</span><span class="sxs-lookup"><span data-stu-id="63bea-540">Policy</span></span>  
  
 <span data-ttu-id="63bea-541">Ayrıntılar bağlama için yukarıdaki 6.5.1 bölümüne bakın</span><span class="sxs-lookup"><span data-stu-id="63bea-541">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="63bea-542">Belirteç destekleme onaylama</span><span class="sxs-lookup"><span data-stu-id="63bea-542">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="63bea-543">Güvenlik üstbilgi örnekler: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="63bea-543">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="63bea-544">İstek</span><span class="sxs-lookup"><span data-stu-id="63bea-544">Request</span></span>  
  
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
  
 <span data-ttu-id="63bea-545">Yanıt</span><span class="sxs-lookup"><span data-stu-id="63bea-545">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="63bea-546">Güvenlik üstbilgi örnekler: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="63bea-546">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="63bea-547">İstek</span><span class="sxs-lookup"><span data-stu-id="63bea-547">Request</span></span>  
  
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
  
 <span data-ttu-id="63bea-548">Yanıt</span><span class="sxs-lookup"><span data-stu-id="63bea-548">Response</span></span>  
  
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
  
#### <a name="655-mutualsslnegotiated"></a><span data-ttu-id="63bea-549">6.5.5 MutualSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="63bea-549">6.5.5 MutualSslNegotiated</span></span>  
 <span data-ttu-id="63bea-550">Bu kimlik doğrulama modu ile istemci ve hizmet X.509 sertifikalarını kullanarak kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="63bea-550">With this authentication mode the client and the service authenticate using X.509 certificates.</span></span> <span data-ttu-id="63bea-551">Kullanılan bağlama 6.5.1 yukarıda açıklandığı gibi simetrik bağlama bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="63bea-551">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="63bea-552">İlke</span><span class="sxs-lookup"><span data-stu-id="63bea-552">Policy</span></span>  
  
 <span data-ttu-id="63bea-553">Ayrıntılar bağlama için yukarıdaki 6.5.1 bölümüne bakın</span><span class="sxs-lookup"><span data-stu-id="63bea-553">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="63bea-554">Belirteç destekleme onaylama</span><span class="sxs-lookup"><span data-stu-id="63bea-554">Endorsing Supporting Token</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="63bea-555">Güvenlik üstbilgi örnekler: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="63bea-555">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="63bea-556">İstek</span><span class="sxs-lookup"><span data-stu-id="63bea-556">Request</span></span>  
  
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
  
 <span data-ttu-id="63bea-557">Yanıt</span><span class="sxs-lookup"><span data-stu-id="63bea-557">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="63bea-558">Güvenlik üstbilgi örnekler: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="63bea-558">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="63bea-559">İstek</span><span class="sxs-lookup"><span data-stu-id="63bea-559">Request</span></span>  
  
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
  
 <span data-ttu-id="63bea-560">Yanıt</span><span class="sxs-lookup"><span data-stu-id="63bea-560">Response</span></span>  
  
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
  
### <a name="66-sspinegotiated"></a><span data-ttu-id="63bea-561">6.6 SspiNegotiated</span><span class="sxs-lookup"><span data-stu-id="63bea-561">6.6 SspiNegotiated</span></span>  
 <span data-ttu-id="63bea-562">Bu kimlik doğrulama modu ile istemci ve sunucu kimlik doğrulaması gerçekleştirmek için anlaşması protokolü kullanılır.</span><span class="sxs-lookup"><span data-stu-id="63bea-562">With this authentication mode a negotiation protocol is used to perform client and server authentication.</span></span> <span data-ttu-id="63bea-563">Kerberos Mümkünse, kullanılan aksi NTLM.</span><span class="sxs-lookup"><span data-stu-id="63bea-563">Kerberos is used if possible, otherwise NTLM.</span></span> <span data-ttu-id="63bea-564">Kullanılan bağlama simetrik bağlama aşağıdaki özelliklere sahip olur;</span><span class="sxs-lookup"><span data-stu-id="63bea-564">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="63bea-565">Koruma simgesi: SpnegoContextToken, .../IncludeToken/AlwaysToRecipient için ekleme modu ayarlanır</span><span class="sxs-lookup"><span data-stu-id="63bea-565">Protection Token: SpnegoContextToken, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
<span data-ttu-id="63bea-566">Simge koruma: yanlış</span><span class="sxs-lookup"><span data-stu-id="63bea-566">Token Protection: False</span></span>  
  
 <span data-ttu-id="63bea-567">Tüm üstbilgi ve gövde imzalar: True</span><span class="sxs-lookup"><span data-stu-id="63bea-567">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="63bea-568">Koruma sırasını: SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="63bea-568">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="63bea-569">İmza şifrelemek: True</span><span class="sxs-lookup"><span data-stu-id="63bea-569">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="63bea-570">İlke</span><span class="sxs-lookup"><span data-stu-id="63bea-570">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="63bea-571">Güvenlik üstbilgi örnekler: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="63bea-571">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="63bea-572">İstek</span><span class="sxs-lookup"><span data-stu-id="63bea-572">Request</span></span>  
  
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
  
 <span data-ttu-id="63bea-573">Yanıt</span><span class="sxs-lookup"><span data-stu-id="63bea-573">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="63bea-574">Güvenlik üstbilgi örnekler: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="63bea-574">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="63bea-575">İstek</span><span class="sxs-lookup"><span data-stu-id="63bea-575">Request</span></span>  
  
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
  
 <span data-ttu-id="63bea-576">Yanıt</span><span class="sxs-lookup"><span data-stu-id="63bea-576">Response</span></span>  
  
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
  
### <a name="67-secureconversation"></a><span data-ttu-id="63bea-577">6.7 SecureConversation</span><span class="sxs-lookup"><span data-stu-id="63bea-577">6.7 SecureConversation</span></span>  
 <span data-ttu-id="63bea-578">Kullanılan bağlama simetrik bağlama SCT WS-SecureConversation (WS-SC) başına olan koruma belirtecine sahip olur.</span><span class="sxs-lookup"><span data-stu-id="63bea-578">The binding used is a symmetric binding with the protection token being a SCT per WS-SecureConversation (WS-SC).</span></span> <span data-ttu-id="63bea-579">SCT göre kendisini anlaşma protokolünü kullanan bir simetrik bağlama olan iç içe bir bağlama, WS-Trust (WS-Trust) veya WS-SecureConversation (WS-SC) kullanılarak belirlenir.</span><span class="sxs-lookup"><span data-stu-id="63bea-579">The SCT is negotiated using WS-Trust (WS-Trust) or WS-SecureConversation (WS-SC) according to a nested binding, which is itself a symmetric binding that uses a negotiation protocol.</span></span> <span data-ttu-id="63bea-580">Anlaşma Protokolü, mümkün olduğunda istemci ve sunucu kimlik doğrulaması gerçekleştirmek için Kerberos kullanır.</span><span class="sxs-lookup"><span data-stu-id="63bea-580">The negotiation protocol will use Kerberos to perform client and server authentication if possible.</span></span> <span data-ttu-id="63bea-581">Kerberos kullanılamaz, NTLM olarak geri döner.</span><span class="sxs-lookup"><span data-stu-id="63bea-581">If Kerberos cannot be used, it will fall back to NTLM.</span></span>  
  
 <span data-ttu-id="63bea-582">İlke</span><span class="sxs-lookup"><span data-stu-id="63bea-582">Policy</span></span>  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="63bea-583">Güvenlik üstbilgi örnekler: SignBeforeEncrypt, EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="63bea-583">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="63bea-584">İstek</span><span class="sxs-lookup"><span data-stu-id="63bea-584">Request</span></span>  
  
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
  
 <span data-ttu-id="63bea-585">Yanıt</span><span class="sxs-lookup"><span data-stu-id="63bea-585">Response</span></span>  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="63bea-586">Güvenlik üstbilgi örnekler: EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="63bea-586">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="63bea-587">İstek</span><span class="sxs-lookup"><span data-stu-id="63bea-587">Request</span></span>  
  
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
  
 <span data-ttu-id="63bea-588">Yanıt</span><span class="sxs-lookup"><span data-stu-id="63bea-588">Response</span></span>  
  
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

---
title: "&lt;netTcpBinding&gt; &lt;taşıma&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 49462e0a-66e1-463f-b3e1-c83a441673c6
caps.latest.revision: "18"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: adec2ce082f063f5d3f2cff2c1c428a770aeb76d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="lttransportgt-of-ltnettcpbindinggt"></a><span data-ttu-id="b9642-102">&lt;netTcpBinding&gt; &lt;taşıma&gt;</span><span class="sxs-lookup"><span data-stu-id="b9642-102">&lt;transport&gt; of &lt;netTcpBinding&gt;</span></span>
<span data-ttu-id="b9642-103">İleti düzeyi güvenlik gereksinimleri ile yapılandırılmış bir uç nokta türünü tanımlar [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="b9642-103">Defines the type of message-level security requirements for an endpoint configured with the [\<netTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span></span>  
  
 <span data-ttu-id="b9642-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="b9642-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b9642-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="b9642-105">\<bindings></span></span>  
<span data-ttu-id="b9642-106">\<netTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="b9642-106">\<netTcpBinding></span></span>  
<span data-ttu-id="b9642-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="b9642-107">\<binding></span></span>  
<span data-ttu-id="b9642-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="b9642-108">\<security></span></span>  
<span data-ttu-id="b9642-109">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="b9642-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9642-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b9642-110">Syntax</span></span>  
  
```xml  
<netTcpBinding>  
    <binding>  
        <security  
         mode="None|Transport|Message|TransportWithMessageCredential">  
            <transport clientCredentialType="None|Windows|Certificate"  
             protectionLevel="None|Sign|EncryptAndSign"             sslProtocols="Tls|Tls11|Tls12">  
                <extendedProtectionPolicy  
                     policyEnforcement="Never|WhenSupported|Always"  
                     protectionScenario="TransportSelected|TrustedProxy">  
                    <customServiceNames></customServiceNames>  
                        </extendedProtectionPolicy>  
            </transport>  
        </security>  
    </binding>  
</netTcpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b9642-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b9642-111">Attributes and Elements</span></span>  
 <span data-ttu-id="b9642-112">Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır</span><span class="sxs-lookup"><span data-stu-id="b9642-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b9642-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b9642-113">Attributes</span></span>  
  
|<span data-ttu-id="b9642-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b9642-114">Attribute</span></span>|<span data-ttu-id="b9642-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b9642-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b9642-116">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="b9642-116">clientCredentialType</span></span>|<span data-ttu-id="b9642-117">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="b9642-117">Optional.</span></span> <span data-ttu-id="b9642-118">Taşıma güvenliği kullanarak istemci kimlik doğrulaması yapılırken kullanılacak kimlik bilgileri türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="b9642-118">Specifies the type of credential to be used when performing client authentication using Transport security.</span></span><br /><br /> <span data-ttu-id="b9642-119">-Varsayılan değer `Windows`.</span><span class="sxs-lookup"><span data-stu-id="b9642-119">-   The default value is `Windows`.</span></span><br /><span data-ttu-id="b9642-120">-Bu öznitelik türünde <xref:System.ServiceModel.TcpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="b9642-120">-   This attribute is of type <xref:System.ServiceModel.TcpClientCredentialType>.</span></span>|  
|<span data-ttu-id="b9642-121">ProtectionLevel</span><span class="sxs-lookup"><span data-stu-id="b9642-121">protectionLevel</span></span>|<span data-ttu-id="b9642-122">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="b9642-122">Optional.</span></span> <span data-ttu-id="b9642-123">TCP Aktarım düzeyinde güvenlik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b9642-123">Defines security at the level of the TCP transport.</span></span> <span data-ttu-id="b9642-124">İletileri imzalama bir üçüncü taraf onu aktarılırken iletiyle oynama riskini azaltır.</span><span class="sxs-lookup"><span data-stu-id="b9642-124">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="b9642-125">Şifreleme, aktarım sırasında veri düzeyi gizliliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="b9642-125">Encryption provides data-level privacy during transport.</span></span><br /><br /> <span data-ttu-id="b9642-126">Varsayılan değer `EncryptAndSign` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b9642-126">The default value is `EncryptAndSign`.</span></span>|  
|<span data-ttu-id="b9642-127">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="b9642-127">sslProtocols</span></span>|<span data-ttu-id="b9642-128">Hangi SslProtocols belirten bir SslProtocols enum bayrak değeri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="b9642-128">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="b9642-129">Varsayılan değer: Tls &#124; Tls11 &#124; Tls12.</span><span class="sxs-lookup"><span data-stu-id="b9642-129">The default is Tls&#124;Tls11&#124;Tls12.</span></span>|  
|<span data-ttu-id="b9642-130">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="b9642-130">policyEnforcement</span></span>|<span data-ttu-id="b9642-131">Bu numaralandırma ne zaman belirtir <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> zorunlu tutulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b9642-131">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="b9642-132">1.  Hiçbir zaman – ilke hiçbir zaman zorlanır (genişletilmiş koruma devre dışı).</span><span class="sxs-lookup"><span data-stu-id="b9642-132">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="b9642-133">2.  Yalnızca istemci genişletilmiş koruma destekliyorsa WhenSupported – ilke uygulanır.</span><span class="sxs-lookup"><span data-stu-id="b9642-133">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="b9642-134">3.  Her zaman – ilke her zaman zorlanır.</span><span class="sxs-lookup"><span data-stu-id="b9642-134">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="b9642-135">Genişletilmiş Koruma desteklemeyen istemcilerin kimliğini doğrulamak başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="b9642-135">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="b9642-136">clientCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="b9642-136">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="b9642-137">Değer</span><span class="sxs-lookup"><span data-stu-id="b9642-137">Value</span></span>|<span data-ttu-id="b9642-138">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b9642-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b9642-139">Yok.</span><span class="sxs-lookup"><span data-stu-id="b9642-139">None</span></span>|<span data-ttu-id="b9642-140">İstemci anonimdir.</span><span class="sxs-lookup"><span data-stu-id="b9642-140">The client is anonymous.</span></span> <span data-ttu-id="b9642-141">Bu hizmet için bir sertifika gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b9642-141">This requires a certificate for the service.</span></span>|  
|<span data-ttu-id="b9642-142">Windows</span><span class="sxs-lookup"><span data-stu-id="b9642-142">Windows</span></span>|<span data-ttu-id="b9642-143">Windows kimlik doğrulaması SP anlaşma (Kerberos anlaşması) kullanarak istemcinin belirtir.</span><span class="sxs-lookup"><span data-stu-id="b9642-143">Specifies Windows authentication of the client using SP Negotiation (Kerberos negotiation).</span></span>|  
|<span data-ttu-id="b9642-144">Sertifika</span><span class="sxs-lookup"><span data-stu-id="b9642-144">Certificate</span></span>|<span data-ttu-id="b9642-145">İstemci, bir sertifika kullanılarak doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="b9642-145">The client is authenticated using a certificate.</span></span> <span data-ttu-id="b9642-146">Bu, SSL anlaşması kullanır ve hizmet için bir sertifika gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b9642-146">This uses SSL Negotiation and requires a certificate for the service.</span></span>|  
  
## <a name="protectionlevel-attribute"></a><span data-ttu-id="b9642-147">protectionLevel özniteliği</span><span class="sxs-lookup"><span data-stu-id="b9642-147">protectionLevel Attribute</span></span>  
  
|<span data-ttu-id="b9642-148">Değer</span><span class="sxs-lookup"><span data-stu-id="b9642-148">Value</span></span>|<span data-ttu-id="b9642-149">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b9642-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b9642-150">Yok.</span><span class="sxs-lookup"><span data-stu-id="b9642-150">None</span></span>|<span data-ttu-id="b9642-151">Koruma yok.</span><span class="sxs-lookup"><span data-stu-id="b9642-151">No protection.</span></span>|  
|<span data-ttu-id="b9642-152">Oturum</span><span class="sxs-lookup"><span data-stu-id="b9642-152">Sign</span></span>|<span data-ttu-id="b9642-153">İmzalı iletiler.</span><span class="sxs-lookup"><span data-stu-id="b9642-153">Messages are signed.</span></span>|  
|<span data-ttu-id="b9642-154">Da EncryptAndSign</span><span class="sxs-lookup"><span data-stu-id="b9642-154">EncryptAndSign</span></span>|<span data-ttu-id="b9642-155">-İletileri şifrelenir ve imzalanmış.</span><span class="sxs-lookup"><span data-stu-id="b9642-155">-   Messages are encrypted and signed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b9642-156">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b9642-156">Child Elements</span></span>  
 <span data-ttu-id="b9642-157">Yok.</span><span class="sxs-lookup"><span data-stu-id="b9642-157">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b9642-158">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b9642-158">Parent Elements</span></span>  
  
|<span data-ttu-id="b9642-159">Öğe</span><span class="sxs-lookup"><span data-stu-id="b9642-159">Element</span></span>|<span data-ttu-id="b9642-160">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b9642-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b9642-161">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="b9642-161">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)|<span data-ttu-id="b9642-162">Güvenlik özellikleri belirtir [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="b9642-162">Specifies the security capabilities of the [\<netTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9642-163">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b9642-163">Remarks</span></span>  
 <span data-ttu-id="b9642-164">Taşıma güvenliği bütünlüğü ve gizliliği SOAP iletisi ve karşılıklı kimlik doğrulaması için kullanın.</span><span class="sxs-lookup"><span data-stu-id="b9642-164">Use Transport security for integrity and confidentiality of the SOAP message and for mutual authentication.</span></span> <span data-ttu-id="b9642-165">Bu güvenlik modunu bağlamada seçtiyseniz, kanal yığını güvenli bir taşıma kullanılarak yapılandırılır ve SOAP iletilerine, TCP üzerinden aktarım güvenliği gibi Windows (Negotiate) veya SSL kullanılarak güvenlik altına.</span><span class="sxs-lookup"><span data-stu-id="b9642-165">If this security mode is selected on a binding, the channel stack is configured using a secure transport and the SOAP messages are secured using transport security such as Windows (Negotiate) or SSL over TCP.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9642-166">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b9642-166">See Also</span></span>  
 <xref:System.ServiceModel.TcpTransportSecurity>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.NetTcpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>  
 [<span data-ttu-id="b9642-167">Hizmetler ve istemcileri güvenli hale getirme</span><span class="sxs-lookup"><span data-stu-id="b9642-167">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="b9642-168">Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="b9642-168">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="b9642-169">Sistem tarafından sağlanan bağlamaları yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b9642-169">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="b9642-170">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="b9642-170">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="b9642-171">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="b9642-171">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)

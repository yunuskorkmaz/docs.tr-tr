---
title: <transport> / <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 49462e0a-66e1-463f-b3e1-c83a441673c6
ms.openlocfilehash: 97139b6bea21e4d908c06f5210e54756865d3c46
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59217802"
---
# <a name="transport-of-nettcpbinding"></a><span data-ttu-id="9bec9-102">\<Aktarım >, \<netTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="9bec9-102">\<transport> of \<netTcpBinding></span></span>
<span data-ttu-id="9bec9-103">İleti düzeyi güvenliği gereksinimleri ile yapılandırılmış bir uç nokta türünü tanımlayan [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="9bec9-103">Defines the type of message-level security requirements for an endpoint configured with the [\<netTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span></span>  
  
 <span data-ttu-id="9bec9-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9bec9-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="9bec9-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="9bec9-105">\<bindings></span></span>  
<span data-ttu-id="9bec9-106">\<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="9bec9-106">\<netTcpBinding></span></span>  
<span data-ttu-id="9bec9-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="9bec9-107">\<binding></span></span>  
<span data-ttu-id="9bec9-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="9bec9-108">\<security></span></span>  
<span data-ttu-id="9bec9-109">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="9bec9-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bec9-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9bec9-110">Syntax</span></span>  
  
```xml  
<netTcpBinding>
  <binding>
    <security mode="None|Transport|Message|TransportWithMessageCredential">
      <transport clientCredentialType="None|Windows|Certificate"
                 protectionLevel="None|Sign|EncryptAndSign"
                 sslProtocols="Tls|Tls11|Tls12">
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</netTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9bec9-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9bec9-111">Attributes and Elements</span></span>  
 <span data-ttu-id="9bec9-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9bec9-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9bec9-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9bec9-113">Attributes</span></span>  
  
|<span data-ttu-id="9bec9-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9bec9-114">Attribute</span></span>|<span data-ttu-id="9bec9-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9bec9-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9bec9-116">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="9bec9-116">clientCredentialType</span></span>|<span data-ttu-id="9bec9-117">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="9bec9-117">Optional.</span></span> <span data-ttu-id="9bec9-118">Aktarım güvenliği kullanarak istemci kimlik doğrulaması yapılırken kullanılacak kimlik bilgisi türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="9bec9-118">Specifies the type of credential to be used when performing client authentication using Transport security.</span></span><br /><br /> <span data-ttu-id="9bec9-119">-Varsayılan değer `Windows`.</span><span class="sxs-lookup"><span data-stu-id="9bec9-119">-   The default value is `Windows`.</span></span><br /><span data-ttu-id="9bec9-120">-Bu öznitelik türünde <xref:System.ServiceModel.TcpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="9bec9-120">-   This attribute is of type <xref:System.ServiceModel.TcpClientCredentialType>.</span></span>|  
|<span data-ttu-id="9bec9-121">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="9bec9-121">protectionLevel</span></span>|<span data-ttu-id="9bec9-122">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="9bec9-122">Optional.</span></span> <span data-ttu-id="9bec9-123">TCP taşıma düzeyinde güvenliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9bec9-123">Defines security at the level of the TCP transport.</span></span> <span data-ttu-id="9bec9-124">İleti imzalama, bir üçüncü taraf aktarılırken iletinin oynama riskini azaltır.</span><span class="sxs-lookup"><span data-stu-id="9bec9-124">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="9bec9-125">Şifreleme, aktarım sırasında verileri düzeyinde gizlilik sağlar.</span><span class="sxs-lookup"><span data-stu-id="9bec9-125">Encryption provides data-level privacy during transport.</span></span><br /><br /> <span data-ttu-id="9bec9-126">Varsayılan değer `EncryptAndSign` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="9bec9-126">The default value is `EncryptAndSign`.</span></span>|  
|<span data-ttu-id="9bec9-127">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="9bec9-127">sslProtocols</span></span>|<span data-ttu-id="9bec9-128">Hangi SslProtocols belirten bir SslProtocols enum bayrak değeri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="9bec9-128">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="9bec9-129">Tls varsayılandır&#124;Tls11&#124;Tls12.</span><span class="sxs-lookup"><span data-stu-id="9bec9-129">The default is Tls&#124;Tls11&#124;Tls12.</span></span>|  
|<span data-ttu-id="9bec9-130">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="9bec9-130">policyEnforcement</span></span>|<span data-ttu-id="9bec9-131">Bu sabit listesi ne zaman belirtir <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> zorlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9bec9-131">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="9bec9-132">1.  Hiçbir zaman – hiçbir zaman ilkenin uygulanıp (genişletilmiş koruma devre dışı).</span><span class="sxs-lookup"><span data-stu-id="9bec9-132">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="9bec9-133">2.  Yalnızca istemci genişletilmiş koruma destekliyorsa WhenSupported – ilke zorunlu tutulur.</span><span class="sxs-lookup"><span data-stu-id="9bec9-133">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="9bec9-134">3.  Her zaman – ilke her zaman uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="9bec9-134">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="9bec9-135">Genişletilmiş Koruma desteklemeyen istemciler kimlik doğrulaması başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="9bec9-135">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="9bec9-136">clientCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="9bec9-136">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="9bec9-137">Değer</span><span class="sxs-lookup"><span data-stu-id="9bec9-137">Value</span></span>|<span data-ttu-id="9bec9-138">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9bec9-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9bec9-139">Yok.</span><span class="sxs-lookup"><span data-stu-id="9bec9-139">None</span></span>|<span data-ttu-id="9bec9-140">İstemci anonimdir.</span><span class="sxs-lookup"><span data-stu-id="9bec9-140">The client is anonymous.</span></span> <span data-ttu-id="9bec9-141">Bu hizmet için bir sertifika gerektirir.</span><span class="sxs-lookup"><span data-stu-id="9bec9-141">This requires a certificate for the service.</span></span>|  
|<span data-ttu-id="9bec9-142">Windows</span><span class="sxs-lookup"><span data-stu-id="9bec9-142">Windows</span></span>|<span data-ttu-id="9bec9-143">Windows kimlik doğrulaması SP anlaşma (Kerberos anlaşması) kullanarak istemciyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="9bec9-143">Specifies Windows authentication of the client using SP Negotiation (Kerberos negotiation).</span></span>|  
|<span data-ttu-id="9bec9-144">Sertifika</span><span class="sxs-lookup"><span data-stu-id="9bec9-144">Certificate</span></span>|<span data-ttu-id="9bec9-145">İstemci, bir sertifika kullanılarak doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="9bec9-145">The client is authenticated using a certificate.</span></span> <span data-ttu-id="9bec9-146">Bu, SSL anlaşması kullanır ve hizmet için bir sertifika gerektirir.</span><span class="sxs-lookup"><span data-stu-id="9bec9-146">This uses SSL Negotiation and requires a certificate for the service.</span></span>|  
  
## <a name="protectionlevel-attribute"></a><span data-ttu-id="9bec9-147">protectionLevel özniteliği</span><span class="sxs-lookup"><span data-stu-id="9bec9-147">protectionLevel Attribute</span></span>  
  
|<span data-ttu-id="9bec9-148">Değer</span><span class="sxs-lookup"><span data-stu-id="9bec9-148">Value</span></span>|<span data-ttu-id="9bec9-149">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9bec9-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9bec9-150">None</span><span class="sxs-lookup"><span data-stu-id="9bec9-150">None</span></span>|<span data-ttu-id="9bec9-151">Koruma yok.</span><span class="sxs-lookup"><span data-stu-id="9bec9-151">No protection.</span></span>|  
|<span data-ttu-id="9bec9-152">oturum</span><span class="sxs-lookup"><span data-stu-id="9bec9-152">Sign</span></span>|<span data-ttu-id="9bec9-153">İmzalı iletiler.</span><span class="sxs-lookup"><span data-stu-id="9bec9-153">Messages are signed.</span></span>|  
|<span data-ttu-id="9bec9-154">EncryptAndSign</span><span class="sxs-lookup"><span data-stu-id="9bec9-154">EncryptAndSign</span></span>|<span data-ttu-id="9bec9-155">-Sıradaki iletiler şifrelenir ve imzalanmış.</span><span class="sxs-lookup"><span data-stu-id="9bec9-155">-   Messages are encrypted and signed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9bec9-156">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9bec9-156">Child Elements</span></span>  
 <span data-ttu-id="9bec9-157">Yok.</span><span class="sxs-lookup"><span data-stu-id="9bec9-157">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9bec9-158">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9bec9-158">Parent Elements</span></span>  
  
|<span data-ttu-id="9bec9-159">Öğe</span><span class="sxs-lookup"><span data-stu-id="9bec9-159">Element</span></span>|<span data-ttu-id="9bec9-160">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9bec9-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9bec9-161">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="9bec9-161">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)|<span data-ttu-id="9bec9-162">Güvenlik yeteneklerini belirtir [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="9bec9-162">Specifies the security capabilities of the [\<netTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9bec9-163">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9bec9-163">Remarks</span></span>  
 <span data-ttu-id="9bec9-164">Aktarım güvenliği ve karşılıklı kimlik doğrulaması bütünlüğü ve gizliliği SOAP iletisi için kullanın.</span><span class="sxs-lookup"><span data-stu-id="9bec9-164">Use Transport security for integrity and confidentiality of the SOAP message and for mutual authentication.</span></span> <span data-ttu-id="9bec9-165">Üzerindeki bir bağlamaya bu güvenlik modunu seçtiyseniz, kanal yığının güvenli aktarım kullanarak yapılandırılır ve SOAP iletilerini TCP üzerinden gibi Windows (anlaş) ya da SSL Aktarım güvenliği kullanılarak güvenli hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="9bec9-165">If this security mode is selected on a binding, the channel stack is configured using a secure transport and the SOAP messages are secured using transport security such as Windows (Negotiate) or SSL over TCP.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bec9-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9bec9-166">See also</span></span>

- <xref:System.ServiceModel.TcpTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetTcpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [<span data-ttu-id="9bec9-167">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="9bec9-167">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="9bec9-168">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="9bec9-168">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="9bec9-169">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="9bec9-169">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="9bec9-170">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="9bec9-170">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="9bec9-171">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="9bec9-171">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)

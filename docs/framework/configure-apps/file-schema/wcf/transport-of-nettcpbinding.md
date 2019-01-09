---
title: '&lt;netTcpBinding&gt; &lt;taşıma&gt;'
ms.date: 03/30/2017
ms.assetid: 49462e0a-66e1-463f-b3e1-c83a441673c6
ms.openlocfilehash: 8416701ce4e787a49ee0a4bdd4829c6592cde94c
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147336"
---
# <a name="lttransportgt-of-ltnettcpbindinggt"></a><span data-ttu-id="fc97b-102">&lt;netTcpBinding&gt; &lt;taşıma&gt;</span><span class="sxs-lookup"><span data-stu-id="fc97b-102">&lt;transport&gt; of &lt;netTcpBinding&gt;</span></span>
<span data-ttu-id="fc97b-103">İleti düzeyi güvenliği gereksinimleri ile yapılandırılmış bir uç nokta türünü tanımlayan [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="fc97b-103">Defines the type of message-level security requirements for an endpoint configured with the [\<netTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span></span>  
  
 <span data-ttu-id="fc97b-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="fc97b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="fc97b-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="fc97b-105">\<bindings></span></span>  
<span data-ttu-id="fc97b-106">\<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="fc97b-106">\<netTcpBinding></span></span>  
<span data-ttu-id="fc97b-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="fc97b-107">\<binding></span></span>  
<span data-ttu-id="fc97b-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="fc97b-108">\<security></span></span>  
<span data-ttu-id="fc97b-109">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="fc97b-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc97b-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fc97b-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fc97b-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fc97b-111">Attributes and Elements</span></span>  
 <span data-ttu-id="fc97b-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fc97b-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fc97b-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fc97b-113">Attributes</span></span>  
  
|<span data-ttu-id="fc97b-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fc97b-114">Attribute</span></span>|<span data-ttu-id="fc97b-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fc97b-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fc97b-116">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="fc97b-116">clientCredentialType</span></span>|<span data-ttu-id="fc97b-117">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="fc97b-117">Optional.</span></span> <span data-ttu-id="fc97b-118">Aktarım güvenliği kullanarak istemci kimlik doğrulaması yapılırken kullanılacak kimlik bilgisi türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="fc97b-118">Specifies the type of credential to be used when performing client authentication using Transport security.</span></span><br /><br /> <span data-ttu-id="fc97b-119">-Varsayılan değer `Windows`.</span><span class="sxs-lookup"><span data-stu-id="fc97b-119">-   The default value is `Windows`.</span></span><br /><span data-ttu-id="fc97b-120">-Bu öznitelik türünde <xref:System.ServiceModel.TcpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="fc97b-120">-   This attribute is of type <xref:System.ServiceModel.TcpClientCredentialType>.</span></span>|  
|<span data-ttu-id="fc97b-121">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="fc97b-121">protectionLevel</span></span>|<span data-ttu-id="fc97b-122">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="fc97b-122">Optional.</span></span> <span data-ttu-id="fc97b-123">TCP taşıma düzeyinde güvenliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fc97b-123">Defines security at the level of the TCP transport.</span></span> <span data-ttu-id="fc97b-124">İleti imzalama, bir üçüncü taraf aktarılırken iletinin oynama riskini azaltır.</span><span class="sxs-lookup"><span data-stu-id="fc97b-124">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="fc97b-125">Şifreleme, aktarım sırasında verileri düzeyinde gizlilik sağlar.</span><span class="sxs-lookup"><span data-stu-id="fc97b-125">Encryption provides data-level privacy during transport.</span></span><br /><br /> <span data-ttu-id="fc97b-126">Varsayılan değer `EncryptAndSign` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="fc97b-126">The default value is `EncryptAndSign`.</span></span>|  
|<span data-ttu-id="fc97b-127">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="fc97b-127">sslProtocols</span></span>|<span data-ttu-id="fc97b-128">Hangi SslProtocols belirten bir SslProtocols enum bayrak değeri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="fc97b-128">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="fc97b-129">Tls varsayılandır&#124;Tls11&#124;Tls12.</span><span class="sxs-lookup"><span data-stu-id="fc97b-129">The default is Tls&#124;Tls11&#124;Tls12.</span></span>|  
|<span data-ttu-id="fc97b-130">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="fc97b-130">policyEnforcement</span></span>|<span data-ttu-id="fc97b-131">Bu sabit listesi ne zaman belirtir <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> zorlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fc97b-131">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="fc97b-132">1.  Hiçbir zaman – hiçbir zaman ilkenin uygulanıp (genişletilmiş koruma devre dışı).</span><span class="sxs-lookup"><span data-stu-id="fc97b-132">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="fc97b-133">2.  Yalnızca istemci genişletilmiş koruma destekliyorsa WhenSupported – ilke zorunlu tutulur.</span><span class="sxs-lookup"><span data-stu-id="fc97b-133">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="fc97b-134">3.  Her zaman – ilke her zaman uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="fc97b-134">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="fc97b-135">Genişletilmiş Koruma desteklemeyen istemciler kimlik doğrulaması başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="fc97b-135">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="fc97b-136">clientCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="fc97b-136">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="fc97b-137">Değer</span><span class="sxs-lookup"><span data-stu-id="fc97b-137">Value</span></span>|<span data-ttu-id="fc97b-138">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fc97b-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fc97b-139">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="fc97b-139">None</span></span>|<span data-ttu-id="fc97b-140">İstemci anonimdir.</span><span class="sxs-lookup"><span data-stu-id="fc97b-140">The client is anonymous.</span></span> <span data-ttu-id="fc97b-141">Bu hizmet için bir sertifika gerektirir.</span><span class="sxs-lookup"><span data-stu-id="fc97b-141">This requires a certificate for the service.</span></span>|  
|<span data-ttu-id="fc97b-142">Windows</span><span class="sxs-lookup"><span data-stu-id="fc97b-142">Windows</span></span>|<span data-ttu-id="fc97b-143">Windows kimlik doğrulaması SP anlaşma (Kerberos anlaşması) kullanarak istemciyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="fc97b-143">Specifies Windows authentication of the client using SP Negotiation (Kerberos negotiation).</span></span>|  
|<span data-ttu-id="fc97b-144">Sertifika</span><span class="sxs-lookup"><span data-stu-id="fc97b-144">Certificate</span></span>|<span data-ttu-id="fc97b-145">İstemci, bir sertifika kullanılarak doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="fc97b-145">The client is authenticated using a certificate.</span></span> <span data-ttu-id="fc97b-146">Bu, SSL anlaşması kullanır ve hizmet için bir sertifika gerektirir.</span><span class="sxs-lookup"><span data-stu-id="fc97b-146">This uses SSL Negotiation and requires a certificate for the service.</span></span>|  
  
## <a name="protectionlevel-attribute"></a><span data-ttu-id="fc97b-147">protectionLevel özniteliği</span><span class="sxs-lookup"><span data-stu-id="fc97b-147">protectionLevel Attribute</span></span>  
  
|<span data-ttu-id="fc97b-148">Değer</span><span class="sxs-lookup"><span data-stu-id="fc97b-148">Value</span></span>|<span data-ttu-id="fc97b-149">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fc97b-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fc97b-150">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="fc97b-150">None</span></span>|<span data-ttu-id="fc97b-151">Koruma yok.</span><span class="sxs-lookup"><span data-stu-id="fc97b-151">No protection.</span></span>|  
|<span data-ttu-id="fc97b-152">oturum</span><span class="sxs-lookup"><span data-stu-id="fc97b-152">Sign</span></span>|<span data-ttu-id="fc97b-153">İmzalı iletiler.</span><span class="sxs-lookup"><span data-stu-id="fc97b-153">Messages are signed.</span></span>|  
|<span data-ttu-id="fc97b-154">EncryptAndSign</span><span class="sxs-lookup"><span data-stu-id="fc97b-154">EncryptAndSign</span></span>|<span data-ttu-id="fc97b-155">-Sıradaki iletiler şifrelenir ve imzalanmış.</span><span class="sxs-lookup"><span data-stu-id="fc97b-155">-   Messages are encrypted and signed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fc97b-156">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fc97b-156">Child Elements</span></span>  
 <span data-ttu-id="fc97b-157">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="fc97b-157">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fc97b-158">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fc97b-158">Parent Elements</span></span>  
  
|<span data-ttu-id="fc97b-159">Öğe</span><span class="sxs-lookup"><span data-stu-id="fc97b-159">Element</span></span>|<span data-ttu-id="fc97b-160">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fc97b-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fc97b-161">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="fc97b-161">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)|<span data-ttu-id="fc97b-162">Güvenlik yeteneklerini belirtir [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="fc97b-162">Specifies the security capabilities of the [\<netTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc97b-163">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fc97b-163">Remarks</span></span>  
 <span data-ttu-id="fc97b-164">Aktarım güvenliği ve karşılıklı kimlik doğrulaması bütünlüğü ve gizliliği SOAP iletisi için kullanın.</span><span class="sxs-lookup"><span data-stu-id="fc97b-164">Use Transport security for integrity and confidentiality of the SOAP message and for mutual authentication.</span></span> <span data-ttu-id="fc97b-165">Üzerindeki bir bağlamaya bu güvenlik modunu seçtiyseniz, kanal yığının güvenli aktarım kullanarak yapılandırılır ve SOAP iletilerini TCP üzerinden gibi Windows (anlaş) ya da SSL Aktarım güvenliği kullanılarak güvenli hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="fc97b-165">If this security mode is selected on a binding, the channel stack is configured using a secure transport and the SOAP messages are secured using transport security such as Windows (Negotiate) or SSL over TCP.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc97b-166">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fc97b-166">See Also</span></span>  
 <xref:System.ServiceModel.TcpTransportSecurity>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.NetTcpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>  
 [<span data-ttu-id="fc97b-167">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="fc97b-167">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="fc97b-168">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="fc97b-168">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="fc97b-169">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="fc97b-169">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="fc97b-170">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="fc97b-170">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="fc97b-171">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="fc97b-171">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)

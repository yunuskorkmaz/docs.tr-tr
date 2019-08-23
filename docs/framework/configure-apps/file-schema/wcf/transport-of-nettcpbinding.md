---
title: <transport> / <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 49462e0a-66e1-463f-b3e1-c83a441673c6
ms.openlocfilehash: 265b68e058919d1d5c5f1dbcfb1419b57be9aeab
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915557"
---
# <a name="transport-of-nettcpbinding"></a><span data-ttu-id="b5272-102">\<\<NetTcpBinding > taşıma ></span><span class="sxs-lookup"><span data-stu-id="b5272-102">\<transport> of \<netTcpBinding></span></span>
<span data-ttu-id="b5272-103">[ \<NetTcpBinding >](nettcpbinding.md)yapılandırılmış bir uç nokta için ileti düzeyi güvenlik gereksinimlerinin türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b5272-103">Defines the type of message-level security requirements for an endpoint configured with the [\<netTcpBinding>](nettcpbinding.md).</span></span>  
  
 <span data-ttu-id="b5272-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b5272-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b5272-105">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="b5272-105">\<bindings></span></span>  
<span data-ttu-id="b5272-106">\<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="b5272-106">\<netTcpBinding></span></span>  
<span data-ttu-id="b5272-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="b5272-107">\<binding></span></span>  
<span data-ttu-id="b5272-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="b5272-108">\<security></span></span>  
<span data-ttu-id="b5272-109">\<Taşıma ></span><span class="sxs-lookup"><span data-stu-id="b5272-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5272-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b5272-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b5272-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b5272-111">Attributes and Elements</span></span>  
 <span data-ttu-id="b5272-112">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="b5272-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b5272-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b5272-113">Attributes</span></span>  
  
|<span data-ttu-id="b5272-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b5272-114">Attribute</span></span>|<span data-ttu-id="b5272-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b5272-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b5272-116">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="b5272-116">clientCredentialType</span></span>|<span data-ttu-id="b5272-117">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="b5272-117">Optional.</span></span> <span data-ttu-id="b5272-118">Aktarım güvenliği kullanılarak istemci kimlik doğrulaması gerçekleştirilirken kullanılacak kimlik bilgisinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="b5272-118">Specifies the type of credential to be used when performing client authentication using Transport security.</span></span><br /><br /> <span data-ttu-id="b5272-119">-Varsayılan değer `Windows`.</span><span class="sxs-lookup"><span data-stu-id="b5272-119">-   The default value is `Windows`.</span></span><br /><span data-ttu-id="b5272-120">-Bu öznitelik türündedir <xref:System.ServiceModel.TcpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="b5272-120">-   This attribute is of type <xref:System.ServiceModel.TcpClientCredentialType>.</span></span>|  
|<span data-ttu-id="b5272-121">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="b5272-121">protectionLevel</span></span>|<span data-ttu-id="b5272-122">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="b5272-122">Optional.</span></span> <span data-ttu-id="b5272-123">TCP aktarımı düzeyinde güvenliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b5272-123">Defines security at the level of the TCP transport.</span></span> <span data-ttu-id="b5272-124">İmzalama iletileri, üçüncü bir tarafın aktarılırken ileti üzerinde izinsiz değişiklik yaptığı riski azaltır.</span><span class="sxs-lookup"><span data-stu-id="b5272-124">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="b5272-125">Şifreleme, aktarım sırasında veri düzeyinde gizlilik sağlar.</span><span class="sxs-lookup"><span data-stu-id="b5272-125">Encryption provides data-level privacy during transport.</span></span><br /><br /> <span data-ttu-id="b5272-126">Varsayılan değer `EncryptAndSign` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b5272-126">The default value is `EncryptAndSign`.</span></span>|  
|<span data-ttu-id="b5272-127">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="b5272-127">sslProtocols</span></span>|<span data-ttu-id="b5272-128">Hangi SslProtocols desteklendiğini belirten bir SslProtocols numaralandırma bayrak değeri.</span><span class="sxs-lookup"><span data-stu-id="b5272-128">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="b5272-129">Varsayılan değer TLS&#124;Tls11&#124;Tls12 ' dir.</span><span class="sxs-lookup"><span data-stu-id="b5272-129">The default is Tls&#124;Tls11&#124;Tls12.</span></span>|  
|<span data-ttu-id="b5272-130">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="b5272-130">policyEnforcement</span></span>|<span data-ttu-id="b5272-131">Bu numaralandırma, <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> ne zaman uygulanacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b5272-131">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="b5272-132">1.  Hiçbir süre – ilke hiçbir şekilde zorlanmaz (genişletilmiş koruma devre dışı bırakılır).</span><span class="sxs-lookup"><span data-stu-id="b5272-132">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="b5272-133">2.  WhenSupported – ilke yalnızca istemci genişletilmiş korumayı destekliyorsa zorlanır.</span><span class="sxs-lookup"><span data-stu-id="b5272-133">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="b5272-134">3.  Her zaman – ilke her zaman zorlanır.</span><span class="sxs-lookup"><span data-stu-id="b5272-134">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="b5272-135">Genişletilmiş korumayı desteklemeyen istemciler kimlik doğrulaması yapamaz.</span><span class="sxs-lookup"><span data-stu-id="b5272-135">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="b5272-136">clientCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="b5272-136">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="b5272-137">Değer</span><span class="sxs-lookup"><span data-stu-id="b5272-137">Value</span></span>|<span data-ttu-id="b5272-138">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b5272-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b5272-139">Yok.</span><span class="sxs-lookup"><span data-stu-id="b5272-139">None</span></span>|<span data-ttu-id="b5272-140">İstemci anonimdir.</span><span class="sxs-lookup"><span data-stu-id="b5272-140">The client is anonymous.</span></span> <span data-ttu-id="b5272-141">Bu, hizmet için bir sertifika gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b5272-141">This requires a certificate for the service.</span></span>|  
|<span data-ttu-id="b5272-142">Windows</span><span class="sxs-lookup"><span data-stu-id="b5272-142">Windows</span></span>|<span data-ttu-id="b5272-143">İstemcinin Windows kimlik doğrulamasını SP anlaşması (Kerberos anlaşması) kullanarak belirtir.</span><span class="sxs-lookup"><span data-stu-id="b5272-143">Specifies Windows authentication of the client using SP Negotiation (Kerberos negotiation).</span></span>|  
|<span data-ttu-id="b5272-144">Sertifika</span><span class="sxs-lookup"><span data-stu-id="b5272-144">Certificate</span></span>|<span data-ttu-id="b5272-145">İstemcinin kimliği bir sertifika kullanılarak doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="b5272-145">The client is authenticated using a certificate.</span></span> <span data-ttu-id="b5272-146">Bu, SSL anlaşmasını kullanır ve hizmet için bir sertifika gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b5272-146">This uses SSL Negotiation and requires a certificate for the service.</span></span>|  
  
## <a name="protectionlevel-attribute"></a><span data-ttu-id="b5272-147">protectionLevel özniteliği</span><span class="sxs-lookup"><span data-stu-id="b5272-147">protectionLevel Attribute</span></span>  
  
|<span data-ttu-id="b5272-148">Değer</span><span class="sxs-lookup"><span data-stu-id="b5272-148">Value</span></span>|<span data-ttu-id="b5272-149">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b5272-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b5272-150">Yok.</span><span class="sxs-lookup"><span data-stu-id="b5272-150">None</span></span>|<span data-ttu-id="b5272-151">Koruma yok.</span><span class="sxs-lookup"><span data-stu-id="b5272-151">No protection.</span></span>|  
|<span data-ttu-id="b5272-152">İmzalayabilirsiniz</span><span class="sxs-lookup"><span data-stu-id="b5272-152">Sign</span></span>|<span data-ttu-id="b5272-153">İletiler imzalanır.</span><span class="sxs-lookup"><span data-stu-id="b5272-153">Messages are signed.</span></span>|  
|<span data-ttu-id="b5272-154">EncryptAndSign</span><span class="sxs-lookup"><span data-stu-id="b5272-154">EncryptAndSign</span></span>|<span data-ttu-id="b5272-155">-İletiler şifrelenir ve imzalanır.</span><span class="sxs-lookup"><span data-stu-id="b5272-155">-   Messages are encrypted and signed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b5272-156">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b5272-156">Child Elements</span></span>  
 <span data-ttu-id="b5272-157">Yok.</span><span class="sxs-lookup"><span data-stu-id="b5272-157">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b5272-158">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b5272-158">Parent Elements</span></span>  
  
|<span data-ttu-id="b5272-159">Öğe</span><span class="sxs-lookup"><span data-stu-id="b5272-159">Element</span></span>|<span data-ttu-id="b5272-160">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b5272-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b5272-161">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="b5272-161">\<security></span></span>](security-of-nettcpbinding.md)|<span data-ttu-id="b5272-162">[ \<NetTcpBinding >](nettcpbinding.md)'nin güvenlik yeteneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b5272-162">Specifies the security capabilities of the [\<netTcpBinding>](nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b5272-163">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b5272-163">Remarks</span></span>  
 <span data-ttu-id="b5272-164">SOAP iletisinin bütünlüğü ve gizliliği ve karşılıklı kimlik doğrulaması için aktarım güvenliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="b5272-164">Use Transport security for integrity and confidentiality of the SOAP message and for mutual authentication.</span></span> <span data-ttu-id="b5272-165">Bu güvenlik modu bir bağlamada seçilirse, kanal yığını güvenli bir aktarım kullanılarak yapılandırılır ve SOAP iletileri Windows (Negotiate) veya TCP üzerinden SSL gibi aktarım güvenliği kullanılarak güvenli hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="b5272-165">If this security mode is selected on a binding, the channel stack is configured using a secure transport and the SOAP messages are secured using transport security such as Windows (Negotiate) or SSL over TCP.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5272-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b5272-166">See also</span></span>

- <xref:System.ServiceModel.TcpTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetTcpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [<span data-ttu-id="b5272-167">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="b5272-167">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="b5272-168">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="b5272-168">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b5272-169">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b5272-169">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="b5272-170">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="b5272-170">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="b5272-171">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="b5272-171">\<binding></span></span>](../../../misc/binding.md)

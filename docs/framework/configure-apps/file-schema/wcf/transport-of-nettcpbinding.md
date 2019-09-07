---
title: <transport> / <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 49462e0a-66e1-463f-b3e1-c83a441673c6
ms.openlocfilehash: 41f11be9b4ae8f7a7535c9766965de8575cff784
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399312"
---
# <a name="transport-of-nettcpbinding"></a><span data-ttu-id="3dff8-102">\<\<NetTcpBinding > taşıma ></span><span class="sxs-lookup"><span data-stu-id="3dff8-102">\<transport> of \<netTcpBinding></span></span>
<span data-ttu-id="3dff8-103">[ \<NetTcpBinding >](nettcpbinding.md)yapılandırılmış bir uç nokta için ileti düzeyi güvenlik gereksinimlerinin türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3dff8-103">Defines the type of message-level security requirements for an endpoint configured with the [\<netTcpBinding>](nettcpbinding.md).</span></span>  
  
<span data-ttu-id="3dff8-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3dff8-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3dff8-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="3dff8-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="3dff8-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlama >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="3dff8-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="3dff8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netTcpBinding >** ](nettcpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="3dff8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netTcpBinding>**](nettcpbinding.md)</span></span>\
<span data-ttu-id="3dff8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="3dff8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="3dff8-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Güvenlik >** ](security-of-nettcpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="3dff8-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-nettcpbinding.md)</span></span>\
<span data-ttu-id="3dff8-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Taşıma >**</span><span class="sxs-lookup"><span data-stu-id="3dff8-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3dff8-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3dff8-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3dff8-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3dff8-112">Attributes and Elements</span></span>  
 <span data-ttu-id="3dff8-113">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="3dff8-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3dff8-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3dff8-114">Attributes</span></span>  
  
|<span data-ttu-id="3dff8-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3dff8-115">Attribute</span></span>|<span data-ttu-id="3dff8-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3dff8-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3dff8-117">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="3dff8-117">clientCredentialType</span></span>|<span data-ttu-id="3dff8-118">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="3dff8-118">Optional.</span></span> <span data-ttu-id="3dff8-119">Aktarım güvenliği kullanılarak istemci kimlik doğrulaması gerçekleştirilirken kullanılacak kimlik bilgisinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="3dff8-119">Specifies the type of credential to be used when performing client authentication using Transport security.</span></span><br /><br /> <span data-ttu-id="3dff8-120">-Varsayılan değer `Windows`.</span><span class="sxs-lookup"><span data-stu-id="3dff8-120">-   The default value is `Windows`.</span></span><br /><span data-ttu-id="3dff8-121">-Bu öznitelik türündedir <xref:System.ServiceModel.TcpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="3dff8-121">-   This attribute is of type <xref:System.ServiceModel.TcpClientCredentialType>.</span></span>|  
|<span data-ttu-id="3dff8-122">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="3dff8-122">protectionLevel</span></span>|<span data-ttu-id="3dff8-123">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="3dff8-123">Optional.</span></span> <span data-ttu-id="3dff8-124">TCP aktarımı düzeyinde güvenliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3dff8-124">Defines security at the level of the TCP transport.</span></span> <span data-ttu-id="3dff8-125">İmzalama iletileri, üçüncü bir tarafın aktarılırken ileti üzerinde izinsiz değişiklik yaptığı riski azaltır.</span><span class="sxs-lookup"><span data-stu-id="3dff8-125">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="3dff8-126">Şifreleme, aktarım sırasında veri düzeyinde gizlilik sağlar.</span><span class="sxs-lookup"><span data-stu-id="3dff8-126">Encryption provides data-level privacy during transport.</span></span><br /><br /> <span data-ttu-id="3dff8-127">Varsayılan değer `EncryptAndSign` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="3dff8-127">The default value is `EncryptAndSign`.</span></span>|  
|<span data-ttu-id="3dff8-128">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="3dff8-128">sslProtocols</span></span>|<span data-ttu-id="3dff8-129">Hangi SslProtocols desteklendiğini belirten bir SslProtocols numaralandırma bayrak değeri.</span><span class="sxs-lookup"><span data-stu-id="3dff8-129">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="3dff8-130">Varsayılan değer TLS&#124;Tls11&#124;Tls12 ' dir.</span><span class="sxs-lookup"><span data-stu-id="3dff8-130">The default is Tls&#124;Tls11&#124;Tls12.</span></span>|  
|<span data-ttu-id="3dff8-131">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="3dff8-131">policyEnforcement</span></span>|<span data-ttu-id="3dff8-132">Bu numaralandırma, <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> ne zaman uygulanacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3dff8-132">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="3dff8-133">1.  Hiçbir süre – ilke hiçbir şekilde zorlanmaz (genişletilmiş koruma devre dışı bırakılır).</span><span class="sxs-lookup"><span data-stu-id="3dff8-133">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="3dff8-134">2.  WhenSupported – ilke yalnızca istemci genişletilmiş korumayı destekliyorsa zorlanır.</span><span class="sxs-lookup"><span data-stu-id="3dff8-134">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="3dff8-135">3.  Her zaman – ilke her zaman zorlanır.</span><span class="sxs-lookup"><span data-stu-id="3dff8-135">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="3dff8-136">Genişletilmiş korumayı desteklemeyen istemciler kimlik doğrulaması yapamaz.</span><span class="sxs-lookup"><span data-stu-id="3dff8-136">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="3dff8-137">clientCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="3dff8-137">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="3dff8-138">Değer</span><span class="sxs-lookup"><span data-stu-id="3dff8-138">Value</span></span>|<span data-ttu-id="3dff8-139">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3dff8-139">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3dff8-140">Yok.</span><span class="sxs-lookup"><span data-stu-id="3dff8-140">None</span></span>|<span data-ttu-id="3dff8-141">İstemci anonimdir.</span><span class="sxs-lookup"><span data-stu-id="3dff8-141">The client is anonymous.</span></span> <span data-ttu-id="3dff8-142">Bu, hizmet için bir sertifika gerektirir.</span><span class="sxs-lookup"><span data-stu-id="3dff8-142">This requires a certificate for the service.</span></span>|  
|<span data-ttu-id="3dff8-143">Windows</span><span class="sxs-lookup"><span data-stu-id="3dff8-143">Windows</span></span>|<span data-ttu-id="3dff8-144">İstemcinin Windows kimlik doğrulamasını SP anlaşması (Kerberos anlaşması) kullanarak belirtir.</span><span class="sxs-lookup"><span data-stu-id="3dff8-144">Specifies Windows authentication of the client using SP Negotiation (Kerberos negotiation).</span></span>|  
|<span data-ttu-id="3dff8-145">Sertifika</span><span class="sxs-lookup"><span data-stu-id="3dff8-145">Certificate</span></span>|<span data-ttu-id="3dff8-146">İstemcinin kimliği bir sertifika kullanılarak doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="3dff8-146">The client is authenticated using a certificate.</span></span> <span data-ttu-id="3dff8-147">Bu, SSL anlaşmasını kullanır ve hizmet için bir sertifika gerektirir.</span><span class="sxs-lookup"><span data-stu-id="3dff8-147">This uses SSL Negotiation and requires a certificate for the service.</span></span>|  
  
## <a name="protectionlevel-attribute"></a><span data-ttu-id="3dff8-148">protectionLevel özniteliği</span><span class="sxs-lookup"><span data-stu-id="3dff8-148">protectionLevel Attribute</span></span>  
  
|<span data-ttu-id="3dff8-149">Değer</span><span class="sxs-lookup"><span data-stu-id="3dff8-149">Value</span></span>|<span data-ttu-id="3dff8-150">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3dff8-150">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3dff8-151">Yok.</span><span class="sxs-lookup"><span data-stu-id="3dff8-151">None</span></span>|<span data-ttu-id="3dff8-152">Koruma yok.</span><span class="sxs-lookup"><span data-stu-id="3dff8-152">No protection.</span></span>|  
|<span data-ttu-id="3dff8-153">İmzalayabilirsiniz</span><span class="sxs-lookup"><span data-stu-id="3dff8-153">Sign</span></span>|<span data-ttu-id="3dff8-154">İletiler imzalanır.</span><span class="sxs-lookup"><span data-stu-id="3dff8-154">Messages are signed.</span></span>|  
|<span data-ttu-id="3dff8-155">EncryptAndSign</span><span class="sxs-lookup"><span data-stu-id="3dff8-155">EncryptAndSign</span></span>|<span data-ttu-id="3dff8-156">-İletiler şifrelenir ve imzalanır.</span><span class="sxs-lookup"><span data-stu-id="3dff8-156">-   Messages are encrypted and signed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3dff8-157">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3dff8-157">Child Elements</span></span>  
 <span data-ttu-id="3dff8-158">Yok.</span><span class="sxs-lookup"><span data-stu-id="3dff8-158">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3dff8-159">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3dff8-159">Parent Elements</span></span>  
  
|<span data-ttu-id="3dff8-160">Öğe</span><span class="sxs-lookup"><span data-stu-id="3dff8-160">Element</span></span>|<span data-ttu-id="3dff8-161">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3dff8-161">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3dff8-162">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="3dff8-162">\<security></span></span>](security-of-nettcpbinding.md)|<span data-ttu-id="3dff8-163">[ \<NetTcpBinding >](nettcpbinding.md)'nin güvenlik yeteneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3dff8-163">Specifies the security capabilities of the [\<netTcpBinding>](nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3dff8-164">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3dff8-164">Remarks</span></span>  
 <span data-ttu-id="3dff8-165">SOAP iletisinin bütünlüğü ve gizliliği ve karşılıklı kimlik doğrulaması için aktarım güvenliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="3dff8-165">Use Transport security for integrity and confidentiality of the SOAP message and for mutual authentication.</span></span> <span data-ttu-id="3dff8-166">Bu güvenlik modu bir bağlamada seçilirse, kanal yığını güvenli bir aktarım kullanılarak yapılandırılır ve SOAP iletileri Windows (Negotiate) veya TCP üzerinden SSL gibi aktarım güvenliği kullanılarak güvenli hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="3dff8-166">If this security mode is selected on a binding, the channel stack is configured using a secure transport and the SOAP messages are secured using transport security such as Windows (Negotiate) or SSL over TCP.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dff8-167">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3dff8-167">See also</span></span>

- <xref:System.ServiceModel.TcpTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetTcpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [<span data-ttu-id="3dff8-168">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="3dff8-168">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="3dff8-169">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="3dff8-169">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="3dff8-170">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="3dff8-170">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="3dff8-171">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="3dff8-171">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="3dff8-172">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="3dff8-172">\<binding></span></span>](../../../misc/binding.md)

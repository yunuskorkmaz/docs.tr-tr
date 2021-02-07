---
description: 'Hakkında daha fazla bilgi <transport> edinin: <netTcpBinding>'
title: <transport> / <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 49462e0a-66e1-463f-b3e1-c83a441673c6
ms.openlocfilehash: 9005de300b41c9f53c62875ee185d0f8a3ee8d7f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664554"
---
# <a name="transport-of-nettcpbinding"></a><span data-ttu-id="394d7-103">\<transport> / \<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="394d7-103">\<transport> of \<netTcpBinding></span></span>

<span data-ttu-id="394d7-104">İle yapılandırılmış bir uç nokta için ileti düzeyi güvenlik gereksinimlerinin türünü tanımlar [\<netTcpBinding>](nettcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="394d7-104">Defines the type of message-level security requirements for an endpoint configured with the [\<netTcpBinding>](nettcpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netTcpBinding>**](nettcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-nettcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="394d7-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="394d7-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="394d7-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="394d7-106">Attributes and Elements</span></span>  

 <span data-ttu-id="394d7-107">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="394d7-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="394d7-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="394d7-108">Attributes</span></span>  
  
|<span data-ttu-id="394d7-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="394d7-109">Attribute</span></span>|<span data-ttu-id="394d7-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="394d7-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="394d7-111">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="394d7-111">clientCredentialType</span></span>|<span data-ttu-id="394d7-112">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="394d7-112">Optional.</span></span> <span data-ttu-id="394d7-113">Aktarım güvenliği kullanılarak istemci kimlik doğrulaması gerçekleştirilirken kullanılacak kimlik bilgisinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="394d7-113">Specifies the type of credential to be used when performing client authentication using Transport security.</span></span><br /><br /> <span data-ttu-id="394d7-114">-Varsayılan değer `Windows` .</span><span class="sxs-lookup"><span data-stu-id="394d7-114">-   The default value is `Windows`.</span></span><br /><span data-ttu-id="394d7-115">-Bu öznitelik türündedir <xref:System.ServiceModel.TcpClientCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="394d7-115">-   This attribute is of type <xref:System.ServiceModel.TcpClientCredentialType>.</span></span>|  
|<span data-ttu-id="394d7-116">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="394d7-116">protectionLevel</span></span>|<span data-ttu-id="394d7-117">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="394d7-117">Optional.</span></span> <span data-ttu-id="394d7-118">TCP aktarımı düzeyinde güvenliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="394d7-118">Defines security at the level of the TCP transport.</span></span> <span data-ttu-id="394d7-119">İmzalama iletileri, üçüncü bir tarafın aktarılırken ileti üzerinde izinsiz değişiklik yaptığı riski azaltır.</span><span class="sxs-lookup"><span data-stu-id="394d7-119">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="394d7-120">Şifreleme, aktarım sırasında veri düzeyinde gizlilik sağlar.</span><span class="sxs-lookup"><span data-stu-id="394d7-120">Encryption provides data-level privacy during transport.</span></span><br /><br /> <span data-ttu-id="394d7-121">`EncryptAndSign` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="394d7-121">The default value is `EncryptAndSign`.</span></span>|  
|<span data-ttu-id="394d7-122">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="394d7-122">sslProtocols</span></span>|<span data-ttu-id="394d7-123">Hangi SslProtocols desteklendiğini belirten bir SslProtocols numaralandırma bayrak değeri.</span><span class="sxs-lookup"><span data-stu-id="394d7-123">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="394d7-124">Varsayılan değer TLS&#124;Tls11&#124;Tls12 ' dir.</span><span class="sxs-lookup"><span data-stu-id="394d7-124">The default is Tls&#124;Tls11&#124;Tls12.</span></span>|  
|<span data-ttu-id="394d7-125">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="394d7-125">policyEnforcement</span></span>|<span data-ttu-id="394d7-126">Bu numaralandırma, ne zaman <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> uygulanacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="394d7-126">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="394d7-127">1. hiçbir süre – ilke hiçbir şekilde zorlanmaz (genişletilmiş koruma devre dışı bırakılır).</span><span class="sxs-lookup"><span data-stu-id="394d7-127">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="394d7-128">2. WhenSupported – ilke yalnızca istemci genişletilmiş korumayı destekliyorsa zorlanır.</span><span class="sxs-lookup"><span data-stu-id="394d7-128">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="394d7-129">3. her zaman – ilke her zaman zorlanır.</span><span class="sxs-lookup"><span data-stu-id="394d7-129">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="394d7-130">Genişletilmiş korumayı desteklemeyen istemciler kimlik doğrulaması yapamaz.</span><span class="sxs-lookup"><span data-stu-id="394d7-130">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="394d7-131">clientCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="394d7-131">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="394d7-132">Değer</span><span class="sxs-lookup"><span data-stu-id="394d7-132">Value</span></span>|<span data-ttu-id="394d7-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="394d7-133">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="394d7-134">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="394d7-134">None</span></span>|<span data-ttu-id="394d7-135">İstemci anonimdir.</span><span class="sxs-lookup"><span data-stu-id="394d7-135">The client is anonymous.</span></span> <span data-ttu-id="394d7-136">Bu, hizmet için bir sertifika gerektirir.</span><span class="sxs-lookup"><span data-stu-id="394d7-136">This requires a certificate for the service.</span></span>|  
|<span data-ttu-id="394d7-137">Windows</span><span class="sxs-lookup"><span data-stu-id="394d7-137">Windows</span></span>|<span data-ttu-id="394d7-138">İstemcinin Windows kimlik doğrulamasını SP anlaşması (Kerberos anlaşması) kullanarak belirtir.</span><span class="sxs-lookup"><span data-stu-id="394d7-138">Specifies Windows authentication of the client using SP Negotiation (Kerberos negotiation).</span></span>|  
|<span data-ttu-id="394d7-139">Sertifika</span><span class="sxs-lookup"><span data-stu-id="394d7-139">Certificate</span></span>|<span data-ttu-id="394d7-140">İstemcinin kimliği bir sertifika kullanılarak doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="394d7-140">The client is authenticated using a certificate.</span></span> <span data-ttu-id="394d7-141">Bu, SSL anlaşmasını kullanır ve hizmet için bir sertifika gerektirir.</span><span class="sxs-lookup"><span data-stu-id="394d7-141">This uses SSL Negotiation and requires a certificate for the service.</span></span>|  
  
## <a name="protectionlevel-attribute"></a><span data-ttu-id="394d7-142">protectionLevel özniteliği</span><span class="sxs-lookup"><span data-stu-id="394d7-142">protectionLevel Attribute</span></span>  
  
|<span data-ttu-id="394d7-143">Değer</span><span class="sxs-lookup"><span data-stu-id="394d7-143">Value</span></span>|<span data-ttu-id="394d7-144">Açıklama</span><span class="sxs-lookup"><span data-stu-id="394d7-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="394d7-145">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="394d7-145">None</span></span>|<span data-ttu-id="394d7-146">Koruma yok.</span><span class="sxs-lookup"><span data-stu-id="394d7-146">No protection.</span></span>|  
|<span data-ttu-id="394d7-147">İşaret</span><span class="sxs-lookup"><span data-stu-id="394d7-147">Sign</span></span>|<span data-ttu-id="394d7-148">İletiler imzalanır.</span><span class="sxs-lookup"><span data-stu-id="394d7-148">Messages are signed.</span></span>|  
|<span data-ttu-id="394d7-149">EncryptAndSign özelliğini</span><span class="sxs-lookup"><span data-stu-id="394d7-149">EncryptAndSign</span></span>|<span data-ttu-id="394d7-150">-İletiler şifrelenir ve imzalanır.</span><span class="sxs-lookup"><span data-stu-id="394d7-150">-   Messages are encrypted and signed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="394d7-151">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="394d7-151">Child Elements</span></span>  

 <span data-ttu-id="394d7-152">Yok</span><span class="sxs-lookup"><span data-stu-id="394d7-152">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="394d7-153">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="394d7-153">Parent Elements</span></span>  
  
|<span data-ttu-id="394d7-154">Öğe</span><span class="sxs-lookup"><span data-stu-id="394d7-154">Element</span></span>|<span data-ttu-id="394d7-155">Açıklama</span><span class="sxs-lookup"><span data-stu-id="394d7-155">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-nettcpbinding.md)|<span data-ttu-id="394d7-156">Öğesinin güvenlik yeteneklerini belirtir [\<netTcpBinding>](nettcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="394d7-156">Specifies the security capabilities of the [\<netTcpBinding>](nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="394d7-157">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="394d7-157">Remarks</span></span>  

 <span data-ttu-id="394d7-158">SOAP iletisinin bütünlüğü ve gizliliği ve karşılıklı kimlik doğrulaması için aktarım güvenliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="394d7-158">Use Transport security for integrity and confidentiality of the SOAP message and for mutual authentication.</span></span> <span data-ttu-id="394d7-159">Bu güvenlik modu bir bağlamada seçilirse, kanal yığını güvenli bir aktarım kullanılarak yapılandırılır ve SOAP iletileri Windows (Negotiate) veya TCP üzerinden SSL gibi aktarım güvenliği kullanılarak güvenli hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="394d7-159">If this security mode is selected on a binding, the channel stack is configured using a secure transport and the SOAP messages are secured using transport security such as Windows (Negotiate) or SSL over TCP.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="394d7-160">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="394d7-160">See also</span></span>

- <xref:System.ServiceModel.TcpTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetTcpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [<span data-ttu-id="394d7-161">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="394d7-161">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="394d7-162">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="394d7-162">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="394d7-163">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="394d7-163">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="394d7-164">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="394d7-164">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)

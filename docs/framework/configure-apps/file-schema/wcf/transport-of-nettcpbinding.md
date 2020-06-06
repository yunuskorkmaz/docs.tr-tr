---
title: <transport> / <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 49462e0a-66e1-463f-b3e1-c83a441673c6
ms.openlocfilehash: 4ef08ad73a03dea21d27217364a7bacb46a3848e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73735925"
---
# <a name="transport-of-nettcpbinding"></a><span data-ttu-id="764bc-102">\<transport> / \<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="764bc-102">\<transport> of \<netTcpBinding></span></span>
<span data-ttu-id="764bc-103">İle yapılandırılmış bir uç nokta için ileti düzeyi güvenlik gereksinimlerinin türünü tanımlar [\<netTcpBinding>](nettcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="764bc-103">Defines the type of message-level security requirements for an endpoint configured with the [\<netTcpBinding>](nettcpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netTcpBinding>**](nettcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-nettcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="764bc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="764bc-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="764bc-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="764bc-105">Attributes and Elements</span></span>  
 <span data-ttu-id="764bc-106">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="764bc-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="764bc-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="764bc-107">Attributes</span></span>  
  
|<span data-ttu-id="764bc-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="764bc-108">Attribute</span></span>|<span data-ttu-id="764bc-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="764bc-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="764bc-110">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="764bc-110">clientCredentialType</span></span>|<span data-ttu-id="764bc-111">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="764bc-111">Optional.</span></span> <span data-ttu-id="764bc-112">Aktarım güvenliği kullanılarak istemci kimlik doğrulaması gerçekleştirilirken kullanılacak kimlik bilgisinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="764bc-112">Specifies the type of credential to be used when performing client authentication using Transport security.</span></span><br /><br /> <span data-ttu-id="764bc-113">-Varsayılan değer `Windows` .</span><span class="sxs-lookup"><span data-stu-id="764bc-113">-   The default value is `Windows`.</span></span><br /><span data-ttu-id="764bc-114">-Bu öznitelik türündedir <xref:System.ServiceModel.TcpClientCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="764bc-114">-   This attribute is of type <xref:System.ServiceModel.TcpClientCredentialType>.</span></span>|  
|<span data-ttu-id="764bc-115">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="764bc-115">protectionLevel</span></span>|<span data-ttu-id="764bc-116">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="764bc-116">Optional.</span></span> <span data-ttu-id="764bc-117">TCP aktarımı düzeyinde güvenliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="764bc-117">Defines security at the level of the TCP transport.</span></span> <span data-ttu-id="764bc-118">İmzalama iletileri, üçüncü bir tarafın aktarılırken ileti üzerinde izinsiz değişiklik yaptığı riski azaltır.</span><span class="sxs-lookup"><span data-stu-id="764bc-118">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="764bc-119">Şifreleme, aktarım sırasında veri düzeyinde gizlilik sağlar.</span><span class="sxs-lookup"><span data-stu-id="764bc-119">Encryption provides data-level privacy during transport.</span></span><br /><br /> <span data-ttu-id="764bc-120">Varsayılan değer: `EncryptAndSign`.</span><span class="sxs-lookup"><span data-stu-id="764bc-120">The default value is `EncryptAndSign`.</span></span>|  
|<span data-ttu-id="764bc-121">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="764bc-121">sslProtocols</span></span>|<span data-ttu-id="764bc-122">Hangi SslProtocols desteklendiğini belirten bir SslProtocols numaralandırma bayrak değeri.</span><span class="sxs-lookup"><span data-stu-id="764bc-122">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="764bc-123">Varsayılan değer TLS&#124;Tls11&#124;Tls12 ' dir.</span><span class="sxs-lookup"><span data-stu-id="764bc-123">The default is Tls&#124;Tls11&#124;Tls12.</span></span>|  
|<span data-ttu-id="764bc-124">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="764bc-124">policyEnforcement</span></span>|<span data-ttu-id="764bc-125">Bu numaralandırma, ne zaman <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> uygulanacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="764bc-125">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="764bc-126">1. hiçbir süre – ilke hiçbir şekilde zorlanmaz (genişletilmiş koruma devre dışı bırakılır).</span><span class="sxs-lookup"><span data-stu-id="764bc-126">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="764bc-127">2. WhenSupported – ilke yalnızca istemci genişletilmiş korumayı destekliyorsa zorlanır.</span><span class="sxs-lookup"><span data-stu-id="764bc-127">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="764bc-128">3. her zaman – ilke her zaman zorlanır.</span><span class="sxs-lookup"><span data-stu-id="764bc-128">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="764bc-129">Genişletilmiş korumayı desteklemeyen istemciler kimlik doğrulaması yapamaz.</span><span class="sxs-lookup"><span data-stu-id="764bc-129">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="764bc-130">clientCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="764bc-130">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="764bc-131">Değer</span><span class="sxs-lookup"><span data-stu-id="764bc-131">Value</span></span>|<span data-ttu-id="764bc-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="764bc-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="764bc-133">Yok</span><span class="sxs-lookup"><span data-stu-id="764bc-133">None</span></span>|<span data-ttu-id="764bc-134">İstemci anonimdir.</span><span class="sxs-lookup"><span data-stu-id="764bc-134">The client is anonymous.</span></span> <span data-ttu-id="764bc-135">Bu, hizmet için bir sertifika gerektirir.</span><span class="sxs-lookup"><span data-stu-id="764bc-135">This requires a certificate for the service.</span></span>|  
|<span data-ttu-id="764bc-136">Windows</span><span class="sxs-lookup"><span data-stu-id="764bc-136">Windows</span></span>|<span data-ttu-id="764bc-137">İstemcinin Windows kimlik doğrulamasını SP anlaşması (Kerberos anlaşması) kullanarak belirtir.</span><span class="sxs-lookup"><span data-stu-id="764bc-137">Specifies Windows authentication of the client using SP Negotiation (Kerberos negotiation).</span></span>|  
|<span data-ttu-id="764bc-138">Sertifika</span><span class="sxs-lookup"><span data-stu-id="764bc-138">Certificate</span></span>|<span data-ttu-id="764bc-139">İstemcinin kimliği bir sertifika kullanılarak doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="764bc-139">The client is authenticated using a certificate.</span></span> <span data-ttu-id="764bc-140">Bu, SSL anlaşmasını kullanır ve hizmet için bir sertifika gerektirir.</span><span class="sxs-lookup"><span data-stu-id="764bc-140">This uses SSL Negotiation and requires a certificate for the service.</span></span>|  
  
## <a name="protectionlevel-attribute"></a><span data-ttu-id="764bc-141">protectionLevel özniteliği</span><span class="sxs-lookup"><span data-stu-id="764bc-141">protectionLevel Attribute</span></span>  
  
|<span data-ttu-id="764bc-142">Değer</span><span class="sxs-lookup"><span data-stu-id="764bc-142">Value</span></span>|<span data-ttu-id="764bc-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="764bc-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="764bc-144">Yok</span><span class="sxs-lookup"><span data-stu-id="764bc-144">None</span></span>|<span data-ttu-id="764bc-145">Koruma yok.</span><span class="sxs-lookup"><span data-stu-id="764bc-145">No protection.</span></span>|  
|<span data-ttu-id="764bc-146">İşaret</span><span class="sxs-lookup"><span data-stu-id="764bc-146">Sign</span></span>|<span data-ttu-id="764bc-147">İletiler imzalanır.</span><span class="sxs-lookup"><span data-stu-id="764bc-147">Messages are signed.</span></span>|  
|<span data-ttu-id="764bc-148">EncryptAndSign özelliğini</span><span class="sxs-lookup"><span data-stu-id="764bc-148">EncryptAndSign</span></span>|<span data-ttu-id="764bc-149">-İletiler şifrelenir ve imzalanır.</span><span class="sxs-lookup"><span data-stu-id="764bc-149">-   Messages are encrypted and signed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="764bc-150">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="764bc-150">Child Elements</span></span>  
 <span data-ttu-id="764bc-151">Yok</span><span class="sxs-lookup"><span data-stu-id="764bc-151">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="764bc-152">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="764bc-152">Parent Elements</span></span>  
  
|<span data-ttu-id="764bc-153">Öğe</span><span class="sxs-lookup"><span data-stu-id="764bc-153">Element</span></span>|<span data-ttu-id="764bc-154">Açıklama</span><span class="sxs-lookup"><span data-stu-id="764bc-154">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-nettcpbinding.md)|<span data-ttu-id="764bc-155">Öğesinin güvenlik yeteneklerini belirtir [\<netTcpBinding>](nettcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="764bc-155">Specifies the security capabilities of the [\<netTcpBinding>](nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="764bc-156">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="764bc-156">Remarks</span></span>  
 <span data-ttu-id="764bc-157">SOAP iletisinin bütünlüğü ve gizliliği ve karşılıklı kimlik doğrulaması için aktarım güvenliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="764bc-157">Use Transport security for integrity and confidentiality of the SOAP message and for mutual authentication.</span></span> <span data-ttu-id="764bc-158">Bu güvenlik modu bir bağlamada seçilirse, kanal yığını güvenli bir aktarım kullanılarak yapılandırılır ve SOAP iletileri Windows (Negotiate) veya TCP üzerinden SSL gibi aktarım güvenliği kullanılarak güvenli hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="764bc-158">If this security mode is selected on a binding, the channel stack is configured using a secure transport and the SOAP messages are secured using transport security such as Windows (Negotiate) or SSL over TCP.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="764bc-159">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="764bc-159">See also</span></span>

- <xref:System.ServiceModel.TcpTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetTcpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [<span data-ttu-id="764bc-160">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="764bc-160">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="764bc-161">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="764bc-161">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="764bc-162">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="764bc-162">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="764bc-163">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="764bc-163">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)

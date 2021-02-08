---
description: 'Hakkında daha fazla bilgi <transport> edinin: <netHttpBinding>'
title: <transport> / <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: 3b180006-1661-43bf-a699-96fd3da469af
ms.openlocfilehash: 1c2029fcbc57632b828fa180ba0ffbbf6b974775
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99773517"
---
# <a name="transport-of-nethttpbinding"></a><span data-ttu-id="f9de7-103">\<transport> / \<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="f9de7-103">\<transport> of \<netHttpBinding></span></span>

<span data-ttu-id="f9de7-104">HTTP taşıması için kimlik doğrulama parametrelerini denetleyen özellikleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f9de7-104">Defines properties that control authentication parameters for the HTTP transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="f9de7-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="f9de7-105">Syntax</span></span>  
  
```xml  
<netHttpBinding>
  <binding>
    <security mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">
      <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"
                 proxyCredentialType="None|Basic|Digest|Ntlm|Windows"
                 realm="string">
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</netHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f9de7-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f9de7-106">Attributes and Elements</span></span>  

 <span data-ttu-id="f9de7-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f9de7-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f9de7-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f9de7-108">Attributes</span></span>  
  
|<span data-ttu-id="f9de7-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f9de7-109">Attribute</span></span>|<span data-ttu-id="f9de7-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f9de7-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f9de7-111">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="f9de7-111">clientCredentialType</span></span>|<span data-ttu-id="f9de7-112">-HTTP kimlik doğrulaması kullanarak istemci kimlik doğrulaması gerçekleştirirken kullanılacak kimlik bilgisinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="f9de7-112">-   Specifies the type of credential to be used when performing client authentication using HTTP authentication.</span></span>  <span data-ttu-id="f9de7-113">Varsayılan değer: `None`.</span><span class="sxs-lookup"><span data-stu-id="f9de7-113">The default is `None`.</span></span> <span data-ttu-id="f9de7-114">Bu öznitelik türü <xref:System.ServiceModel.HttpClientCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="f9de7-114">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|<span data-ttu-id="f9de7-115">proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="f9de7-115">proxyCredentialType</span></span>|<span data-ttu-id="f9de7-116">-HTTP üzerinden proxy kullanan bir etki alanı içinden istemci kimlik doğrulaması gerçekleştirirken kullanılacak kimlik bilgisinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="f9de7-116">-   Specifies the type of credential to be used when performing client authentication from within a domain using a proxy over HTTP.</span></span> <span data-ttu-id="f9de7-117">Bu öznitelik yalnızca `mode` üst öğenin özniteliği veya olduğunda geçerlidir `security` `Transport` `TransportCredentialsOnly` .</span><span class="sxs-lookup"><span data-stu-id="f9de7-117">This attribute is applicable only when the `mode` attribute of the parent `security` element is `Transport` or `TransportCredentialsOnly`.</span></span> <span data-ttu-id="f9de7-118">Bu öznitelik türü <xref:System.ServiceModel.HttpProxyCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="f9de7-118">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|<span data-ttu-id="f9de7-119">bölgesindeki</span><span class="sxs-lookup"><span data-stu-id="f9de7-119">realm</span></span>|<span data-ttu-id="f9de7-120">Özet veya temel kimlik doğrulaması için HTTP kimlik doğrulama düzeni tarafından kullanılan bölgeyi belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="f9de7-120">A string that specifies the realm that is used by the HTTP authentication scheme for digest or basic authentication.</span></span> <span data-ttu-id="f9de7-121">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="f9de7-121">The default is an empty string.</span></span>|  
|<span data-ttu-id="f9de7-122">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="f9de7-122">policyEnforcement</span></span>|<span data-ttu-id="f9de7-123">Bu numaralandırma, ne zaman <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> uygulanacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f9de7-123">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="f9de7-124">1. hiçbir süre – ilke hiçbir şekilde zorlanmaz (genişletilmiş koruma devre dışı bırakılır).</span><span class="sxs-lookup"><span data-stu-id="f9de7-124">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="f9de7-125">2. WhenSupported – ilke yalnızca istemci genişletilmiş korumayı destekliyorsa zorlanır.</span><span class="sxs-lookup"><span data-stu-id="f9de7-125">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="f9de7-126">3. her zaman – ilke her zaman zorlanır.</span><span class="sxs-lookup"><span data-stu-id="f9de7-126">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="f9de7-127">Genişletilmiş korumayı desteklemeyen istemciler kimlik doğrulaması yapamaz.</span><span class="sxs-lookup"><span data-stu-id="f9de7-127">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
|<span data-ttu-id="f9de7-128">protectionScenario</span><span class="sxs-lookup"><span data-stu-id="f9de7-128">protectionScenario</span></span>|<span data-ttu-id="f9de7-129">Bu numaralandırma, ilke tarafından zorlanan koruma senaryosunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="f9de7-129">This enumeration specifies the protection scenario enforced by the policy.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="f9de7-130">clientCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="f9de7-130">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="f9de7-131">Değer</span><span class="sxs-lookup"><span data-stu-id="f9de7-131">Value</span></span>|<span data-ttu-id="f9de7-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f9de7-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f9de7-133">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="f9de7-133">None</span></span>|<span data-ttu-id="f9de7-134">Aktarım sırasında iletiler güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="f9de7-134">Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="f9de7-135">Temel</span><span class="sxs-lookup"><span data-stu-id="f9de7-135">Basic</span></span>|<span data-ttu-id="f9de7-136">Temel kimlik doğrulamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f9de7-136">Specifies basic authentication.</span></span>|  
|<span data-ttu-id="f9de7-137">Bilgisi</span><span class="sxs-lookup"><span data-stu-id="f9de7-137">Digest</span></span>|<span data-ttu-id="f9de7-138">Özet kimlik doğrulamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f9de7-138">Specifies digest authentication.</span></span>|  
|<span data-ttu-id="f9de7-139">NT</span><span class="sxs-lookup"><span data-stu-id="f9de7-139">Ntlm</span></span>|<span data-ttu-id="f9de7-140">Mümkünse NTLM kimlik doğrulamasını belirtir ve Windows kimlik doğrulaması başarısız olursa.</span><span class="sxs-lookup"><span data-stu-id="f9de7-140">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="f9de7-141">Windows</span><span class="sxs-lookup"><span data-stu-id="f9de7-141">Windows</span></span>|<span data-ttu-id="f9de7-142">Windows tümleşik kimlik doğrulamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f9de7-142">Specifies Windows integrated authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="f9de7-143">proxyCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="f9de7-143">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="f9de7-144">Değer</span><span class="sxs-lookup"><span data-stu-id="f9de7-144">Value</span></span>|<span data-ttu-id="f9de7-145">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f9de7-145">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f9de7-146">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="f9de7-146">None</span></span>|<span data-ttu-id="f9de7-147">-İletiler aktarım sırasında güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="f9de7-147">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="f9de7-148">Temel</span><span class="sxs-lookup"><span data-stu-id="f9de7-148">Basic</span></span>|<span data-ttu-id="f9de7-149">RFC 2617 – HTTP kimlik doğrulaması ile tanımlanan temel kimlik doğrulamasını belirtir: temel ve Özet kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="f9de7-149">Specifies basic authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="f9de7-150">Bilgisi</span><span class="sxs-lookup"><span data-stu-id="f9de7-150">Digest</span></span>|<span data-ttu-id="f9de7-151">RFC 2617 – HTTP kimlik doğrulaması ile tanımlanan Özet kimlik doğrulamasını belirtir: temel ve Özet kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="f9de7-151">Specifies digest authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="f9de7-152">NT</span><span class="sxs-lookup"><span data-stu-id="f9de7-152">Ntlm</span></span>|<span data-ttu-id="f9de7-153">Mümkünse NTLM kimlik doğrulamasını belirtir ve Windows kimlik doğrulaması başarısız olursa.</span><span class="sxs-lookup"><span data-stu-id="f9de7-153">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="f9de7-154">Windows</span><span class="sxs-lookup"><span data-stu-id="f9de7-154">Windows</span></span>|<span data-ttu-id="f9de7-155">Windows tümleşik kimlik doğrulamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f9de7-155">Specifies Windows integrated authentication.</span></span>|  
|<span data-ttu-id="f9de7-156">Sertifika</span><span class="sxs-lookup"><span data-stu-id="f9de7-156">Certificate</span></span>|<span data-ttu-id="f9de7-157">Bir sertifika kullanarak istemci kimlik doğrulaması gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="f9de7-157">Performs client authentication using a certificate.</span></span> <span data-ttu-id="f9de7-158">Bu seçenek yalnızca `Mode` üst `security` öğenin özniteliği Transport olarak ayarlandıysa ve yalnızca transportcredentialolarak ayarlandıysa işe yarar.</span><span class="sxs-lookup"><span data-stu-id="f9de7-158">This option works only if the `Mode` attribute of the parent `security` element is set to Transport, and will not work if it is set to TransportCredentialOnly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f9de7-159">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f9de7-159">Child Elements</span></span>  

 <span data-ttu-id="f9de7-160">Yok</span><span class="sxs-lookup"><span data-stu-id="f9de7-160">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f9de7-161">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f9de7-161">Parent Elements</span></span>  
  
|<span data-ttu-id="f9de7-162">Öğe</span><span class="sxs-lookup"><span data-stu-id="f9de7-162">Element</span></span>|<span data-ttu-id="f9de7-163">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f9de7-163">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-nethttpbinding.md)|<span data-ttu-id="f9de7-164">İçin güvenlik yeteneklerini tanımlar [\<netHttpBinding>](nethttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="f9de7-164">Defines the security capabilities for the [\<netHttpBinding>](nethttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f9de7-165">Örnek</span><span class="sxs-lookup"><span data-stu-id="f9de7-165">Example</span></span>  

 <span data-ttu-id="f9de7-166">Aşağıdaki örnek, temel bağlama ile SSL Aktarım güvenliği kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f9de7-166">The following example demonstrates the use of SSL transport security with the basic binding.</span></span> <span data-ttu-id="f9de7-167">Varsayılan olarak, temel bağlama HTTP iletişimini destekler.</span><span class="sxs-lookup"><span data-stu-id="f9de7-167">By default, the basic binding supports HTTP communication.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="netHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <netHttpBinding>
      <!-- Configure basicHttpBinding with Transport security -->
      <!-- mode and clientCredentialType set to None. -->
      <binding name="Binding1">
        <security mode="Transport">
          <transport clientCredentialType="None"
                     proxyCredentialType="None">
            <extendedProtectionPolicy policyEnforcement="WhenSupported"
                                      protectionScenario="TransportSelected">
              <customServiceNames>
              </customServiceNames>
            </extendedProtectionPolicy>
          </transport>
        </security>
      </binding>
    </netHttpBinding>
  </bindings>
</system.serviceModel>
```  
  
## <a name="see-also"></a><span data-ttu-id="f9de7-168">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9de7-168">See also</span></span>

- <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- <xref:System.ServiceModel.HttpTransportSecurity>
- [<span data-ttu-id="f9de7-169">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="f9de7-169">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="f9de7-170">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="f9de7-170">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f9de7-171">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f9de7-171">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="f9de7-172">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="f9de7-172">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)

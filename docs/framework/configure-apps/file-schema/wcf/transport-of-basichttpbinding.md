---
title: <transport> / <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 4c5ba293-3d7e-47a6-b84e-e9022857b7e5
ms.openlocfilehash: c563339e4f854cc4e60f92dd5b8c0b39112dc000
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736114"
---
# <a name="transport-of-basichttpbinding"></a><span data-ttu-id="a86bf-102">\<taşıma > \<basicHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="a86bf-102">\<transport> of \<basicHttpBinding></span></span>
<span data-ttu-id="a86bf-103">HTTP taşıması için kimlik doğrulama parametrelerini denetleyen özellikleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a86bf-103">Defines properties that control authentication parameters for the HTTP transport.</span></span>  
  
<span data-ttu-id="a86bf-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="a86bf-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a86bf-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="a86bf-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="a86bf-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlamaları >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="a86bf-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="a86bf-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<basicHttpBinding >** ](basichttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="a86bf-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<basicHttpBinding>**](basichttpbinding.md)</span></span>\
<span data-ttu-id="a86bf-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="a86bf-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="a86bf-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<güvenlik >** ](security-of-basichttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="a86bf-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-basichttpbinding.md)</span></span>\
<span data-ttu-id="a86bf-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<taşıma >**</span><span class="sxs-lookup"><span data-stu-id="a86bf-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a86bf-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a86bf-111">Syntax</span></span>  
  
```xml  
<basicHttpBinding>
  <binding>
    <security mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">
      <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"
                 proxyCredentialType="None|Basic|Digest|Ntlm|Windows"
                 realm="String">
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</basicHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a86bf-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a86bf-112">Attributes and Elements</span></span>  
 <span data-ttu-id="a86bf-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a86bf-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a86bf-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a86bf-114">Attributes</span></span>  
  
|<span data-ttu-id="a86bf-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a86bf-115">Attribute</span></span>|<span data-ttu-id="a86bf-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a86bf-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a86bf-117">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="a86bf-117">clientCredentialType</span></span>|<span data-ttu-id="a86bf-118">-HTTP kimlik doğrulaması kullanarak istemci kimlik doğrulaması gerçekleştirirken kullanılacak kimlik bilgisinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="a86bf-118">-   Specifies the type of credential to be used when performing client authentication using HTTP authentication.</span></span>  <span data-ttu-id="a86bf-119">Varsayılan, `None` değeridir.</span><span class="sxs-lookup"><span data-stu-id="a86bf-119">The default is `None`.</span></span> <span data-ttu-id="a86bf-120">Bu öznitelik <xref:System.ServiceModel.HttpClientCredentialType>türündedir.</span><span class="sxs-lookup"><span data-stu-id="a86bf-120">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|<span data-ttu-id="a86bf-121">proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="a86bf-121">proxyCredentialType</span></span>|<span data-ttu-id="a86bf-122">-HTTP üzerinden proxy kullanan bir etki alanı içinden istemci kimlik doğrulaması gerçekleştirirken kullanılacak kimlik bilgisinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="a86bf-122">-   Specifies the type of credential to be used when performing client authentication from within a domain using a proxy over HTTP.</span></span> <span data-ttu-id="a86bf-123">Bu öznitelik yalnızca üst `security` öğesinin `mode` özniteliği `Transport` veya `TransportCredentialsOnly`olduğunda geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="a86bf-123">This attribute is applicable only when the `mode` attribute of the parent `security` element is `Transport` or `TransportCredentialsOnly`.</span></span> <span data-ttu-id="a86bf-124">Bu öznitelik <xref:System.ServiceModel.HttpProxyCredentialType>türündedir.</span><span class="sxs-lookup"><span data-stu-id="a86bf-124">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|<span data-ttu-id="a86bf-125">bölgesindeki</span><span class="sxs-lookup"><span data-stu-id="a86bf-125">realm</span></span>|<span data-ttu-id="a86bf-126">Özet veya temel kimlik doğrulaması için HTTP kimlik doğrulama düzeni tarafından kullanılan bölgeyi belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="a86bf-126">A string that specifies the realm that is used by the HTTP authentication scheme for digest or basic authentication.</span></span> <span data-ttu-id="a86bf-127">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="a86bf-127">The default is an empty string.</span></span>|  
|<span data-ttu-id="a86bf-128">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="a86bf-128">policyEnforcement</span></span>|<span data-ttu-id="a86bf-129">Bu sabit listesi <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> ne zaman uygulanacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a86bf-129">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="a86bf-130">1. hiçbir süre – ilke hiçbir şekilde zorlanmaz (genişletilmiş koruma devre dışı bırakılır).</span><span class="sxs-lookup"><span data-stu-id="a86bf-130">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="a86bf-131">2. WhenSupported – ilke yalnızca istemci genişletilmiş korumayı destekliyorsa zorlanır.</span><span class="sxs-lookup"><span data-stu-id="a86bf-131">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="a86bf-132">3. her zaman – ilke her zaman zorlanır.</span><span class="sxs-lookup"><span data-stu-id="a86bf-132">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="a86bf-133">Genişletilmiş korumayı desteklemeyen istemciler kimlik doğrulaması yapamaz.</span><span class="sxs-lookup"><span data-stu-id="a86bf-133">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
|<span data-ttu-id="a86bf-134">protectionScenario</span><span class="sxs-lookup"><span data-stu-id="a86bf-134">protectionScenario</span></span>|<span data-ttu-id="a86bf-135">Bu numaralandırma, ilke tarafından zorlanan koruma senaryosunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="a86bf-135">This enumeration specifies the protection scenario enforced by the policy.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="a86bf-136">clientCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="a86bf-136">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="a86bf-137">Değer</span><span class="sxs-lookup"><span data-stu-id="a86bf-137">Value</span></span>|<span data-ttu-id="a86bf-138">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a86bf-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a86bf-139">Yok.</span><span class="sxs-lookup"><span data-stu-id="a86bf-139">None</span></span>|<span data-ttu-id="a86bf-140">Aktarım sırasında iletiler güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="a86bf-140">Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="a86bf-141">Temel</span><span class="sxs-lookup"><span data-stu-id="a86bf-141">Basic</span></span>|<span data-ttu-id="a86bf-142">Temel kimlik doğrulamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a86bf-142">Specifies basic authentication.</span></span>|  
|<span data-ttu-id="a86bf-143">bilgisi</span><span class="sxs-lookup"><span data-stu-id="a86bf-143">Digest</span></span>|<span data-ttu-id="a86bf-144">Özet kimlik doğrulamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a86bf-144">Specifies digest authentication.</span></span>|  
|<span data-ttu-id="a86bf-145">NT</span><span class="sxs-lookup"><span data-stu-id="a86bf-145">Ntlm</span></span>|<span data-ttu-id="a86bf-146">Mümkünse NTLM kimlik doğrulamasını belirtir ve Windows kimlik doğrulaması başarısız olursa.</span><span class="sxs-lookup"><span data-stu-id="a86bf-146">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="a86bf-147">Windows</span><span class="sxs-lookup"><span data-stu-id="a86bf-147">Windows</span></span>|<span data-ttu-id="a86bf-148">Windows tümleşik kimlik doğrulamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a86bf-148">Specifies Windows integrated authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="a86bf-149">proxyCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="a86bf-149">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="a86bf-150">Değer</span><span class="sxs-lookup"><span data-stu-id="a86bf-150">Value</span></span>|<span data-ttu-id="a86bf-151">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a86bf-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a86bf-152">Yok.</span><span class="sxs-lookup"><span data-stu-id="a86bf-152">None</span></span>|<span data-ttu-id="a86bf-153">-İletiler aktarım sırasında güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="a86bf-153">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="a86bf-154">Temel</span><span class="sxs-lookup"><span data-stu-id="a86bf-154">Basic</span></span>|<span data-ttu-id="a86bf-155">RFC 2617 – HTTP kimlik doğrulaması ile tanımlanan temel kimlik doğrulamasını belirtir: temel ve Özet kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="a86bf-155">Specifies basic authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="a86bf-156">bilgisi</span><span class="sxs-lookup"><span data-stu-id="a86bf-156">Digest</span></span>|<span data-ttu-id="a86bf-157">RFC 2617 – HTTP kimlik doğrulaması ile tanımlanan Özet kimlik doğrulamasını belirtir: temel ve Özet kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="a86bf-157">Specifies digest authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="a86bf-158">NT</span><span class="sxs-lookup"><span data-stu-id="a86bf-158">Ntlm</span></span>|<span data-ttu-id="a86bf-159">Mümkünse NTLM kimlik doğrulamasını belirtir ve Windows kimlik doğrulaması başarısız olursa.</span><span class="sxs-lookup"><span data-stu-id="a86bf-159">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="a86bf-160">Windows</span><span class="sxs-lookup"><span data-stu-id="a86bf-160">Windows</span></span>|<span data-ttu-id="a86bf-161">Windows tümleşik kimlik doğrulamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a86bf-161">Specifies Windows integrated authentication.</span></span>|  
|<span data-ttu-id="a86bf-162">Sertifika</span><span class="sxs-lookup"><span data-stu-id="a86bf-162">Certificate</span></span>|<span data-ttu-id="a86bf-163">Bir sertifika kullanarak istemci kimlik doğrulaması gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="a86bf-163">Performs client authentication using a certificate.</span></span> <span data-ttu-id="a86bf-164">Bu seçenek yalnızca üst `security` öğesinin `Mode` özniteliği Transport olarak ayarlandıysa ve yalnızca Transportcredentialolarak ayarlandıysa işe yarar.</span><span class="sxs-lookup"><span data-stu-id="a86bf-164">This option works only if the `Mode` attribute of the parent `security` element is set to Transport, and will not work if it is set to TransportCredentialOnly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a86bf-165">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a86bf-165">Child Elements</span></span>  
 <span data-ttu-id="a86bf-166">Yok.</span><span class="sxs-lookup"><span data-stu-id="a86bf-166">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a86bf-167">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a86bf-167">Parent Elements</span></span>  
  
|<span data-ttu-id="a86bf-168">Öğe</span><span class="sxs-lookup"><span data-stu-id="a86bf-168">Element</span></span>|<span data-ttu-id="a86bf-169">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a86bf-169">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a86bf-170">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="a86bf-170">\<security></span></span>](security-of-basichttpbinding.md)|<span data-ttu-id="a86bf-171">[\<basicHttpBinding >](basichttpbinding.md)için güvenlik yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a86bf-171">Defines the security capabilities for the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a86bf-172">Örnek</span><span class="sxs-lookup"><span data-stu-id="a86bf-172">Example</span></span>  
 <span data-ttu-id="a86bf-173">Aşağıdaki örnek, temel bağlama ile SSL Aktarım güvenliği kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a86bf-173">The following example demonstrates the use of SSL transport security with the basic binding.</span></span> <span data-ttu-id="a86bf-174">Varsayılan olarak, temel bağlama HTTP iletişimini destekler.</span><span class="sxs-lookup"><span data-stu-id="a86bf-174">By default, the basic binding supports HTTP communication.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="basicHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <basicHttpBinding>
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
    </basicHttpBinding>
  </bindings>
</system.serviceModel>
```  
  
## <a name="see-also"></a><span data-ttu-id="a86bf-175">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a86bf-175">See also</span></span>

- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.BasicHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- <xref:System.ServiceModel.HttpTransportSecurity>
- [<span data-ttu-id="a86bf-176">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="a86bf-176">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="a86bf-177">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="a86bf-177">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a86bf-178">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a86bf-178">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="a86bf-179">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="a86bf-179">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="a86bf-180">\< bağlama ></span><span class="sxs-lookup"><span data-stu-id="a86bf-180">\<binding></span></span>](bindings.md)

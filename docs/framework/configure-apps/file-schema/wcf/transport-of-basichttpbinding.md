---
title: <transport> / <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 4c5ba293-3d7e-47a6-b84e-e9022857b7e5
ms.openlocfilehash: 2cf69c48a51ce2c687ebcfe9f87f7c22f5f86084
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399379"
---
# <a name="transport-of-basichttpbinding"></a><span data-ttu-id="86068-102">\<\<BasicHttpBinding > taşıma ></span><span class="sxs-lookup"><span data-stu-id="86068-102">\<transport> of \<basicHttpBinding></span></span>
<span data-ttu-id="86068-103">HTTP taşıması için kimlik doğrulama parametrelerini denetleyen özellikleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="86068-103">Defines properties that control authentication parameters for the HTTP transport.</span></span>  
  
<span data-ttu-id="86068-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="86068-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="86068-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="86068-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="86068-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlama >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="86068-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="86068-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<basicHttpBinding >** ](basichttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="86068-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<basicHttpBinding>**](basichttpbinding.md)</span></span>\
<span data-ttu-id="86068-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="86068-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="86068-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Güvenlik >** ](security-of-basichttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="86068-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-basichttpbinding.md)</span></span>\
<span data-ttu-id="86068-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Taşıma >**</span><span class="sxs-lookup"><span data-stu-id="86068-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86068-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="86068-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="86068-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="86068-112">Attributes and Elements</span></span>  
 <span data-ttu-id="86068-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="86068-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="86068-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="86068-114">Attributes</span></span>  
  
|<span data-ttu-id="86068-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="86068-115">Attribute</span></span>|<span data-ttu-id="86068-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="86068-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="86068-117">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="86068-117">clientCredentialType</span></span>|<span data-ttu-id="86068-118">-HTTP kimlik doğrulaması kullanarak istemci kimlik doğrulaması gerçekleştirirken kullanılacak kimlik bilgisinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="86068-118">-   Specifies the type of credential to be used when performing client authentication using HTTP authentication.</span></span>  <span data-ttu-id="86068-119">Varsayılan, `None` değeridir.</span><span class="sxs-lookup"><span data-stu-id="86068-119">The default is `None`.</span></span> <span data-ttu-id="86068-120">Bu öznitelik türü <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="86068-120">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|<span data-ttu-id="86068-121">proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="86068-121">proxyCredentialType</span></span>|<span data-ttu-id="86068-122">-HTTP üzerinden proxy kullanan bir etki alanı içinden istemci kimlik doğrulaması gerçekleştirirken kullanılacak kimlik bilgisinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="86068-122">-   Specifies the type of credential to be used when performing client authentication from within a domain using a proxy over HTTP.</span></span> <span data-ttu-id="86068-123">Bu öznitelik yalnızca `mode` üst `security` öğenin `Transport` özniteliği veya `TransportCredentialsOnly`olduğunda geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="86068-123">This attribute is applicable only when the `mode` attribute of the parent `security` element is `Transport` or `TransportCredentialsOnly`.</span></span> <span data-ttu-id="86068-124">Bu öznitelik türü <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="86068-124">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|<span data-ttu-id="86068-125">bölgesindeki</span><span class="sxs-lookup"><span data-stu-id="86068-125">realm</span></span>|<span data-ttu-id="86068-126">Özet veya temel kimlik doğrulaması için HTTP kimlik doğrulama düzeni tarafından kullanılan bölgeyi belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="86068-126">A string that specifies the realm that is used by the HTTP authentication scheme for digest or basic authentication.</span></span> <span data-ttu-id="86068-127">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="86068-127">The default is an empty string.</span></span>|  
|<span data-ttu-id="86068-128">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="86068-128">policyEnforcement</span></span>|<span data-ttu-id="86068-129">Bu numaralandırma, <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> ne zaman uygulanacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="86068-129">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="86068-130">1.  Hiçbir süre – ilke hiçbir şekilde zorlanmaz (genişletilmiş koruma devre dışı bırakılır).</span><span class="sxs-lookup"><span data-stu-id="86068-130">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="86068-131">2.  WhenSupported – ilke yalnızca istemci genişletilmiş korumayı destekliyorsa zorlanır.</span><span class="sxs-lookup"><span data-stu-id="86068-131">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="86068-132">3.  Her zaman – ilke her zaman zorlanır.</span><span class="sxs-lookup"><span data-stu-id="86068-132">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="86068-133">Genişletilmiş korumayı desteklemeyen istemciler kimlik doğrulaması yapamaz.</span><span class="sxs-lookup"><span data-stu-id="86068-133">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
|<span data-ttu-id="86068-134">protectionScenario</span><span class="sxs-lookup"><span data-stu-id="86068-134">protectionScenario</span></span>|<span data-ttu-id="86068-135">Bu numaralandırma, ilke tarafından zorlanan koruma senaryosunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="86068-135">This enumeration specifies the protection scenario enforced by the policy.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="86068-136">clientCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="86068-136">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="86068-137">Değer</span><span class="sxs-lookup"><span data-stu-id="86068-137">Value</span></span>|<span data-ttu-id="86068-138">Açıklama</span><span class="sxs-lookup"><span data-stu-id="86068-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="86068-139">Yok.</span><span class="sxs-lookup"><span data-stu-id="86068-139">None</span></span>|<span data-ttu-id="86068-140">Aktarım sırasında iletiler güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="86068-140">Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="86068-141">Temel</span><span class="sxs-lookup"><span data-stu-id="86068-141">Basic</span></span>|<span data-ttu-id="86068-142">Temel kimlik doğrulamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="86068-142">Specifies basic authentication.</span></span>|  
|<span data-ttu-id="86068-143">Bilgisi</span><span class="sxs-lookup"><span data-stu-id="86068-143">Digest</span></span>|<span data-ttu-id="86068-144">Özet kimlik doğrulamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="86068-144">Specifies digest authentication.</span></span>|  
|<span data-ttu-id="86068-145">NT</span><span class="sxs-lookup"><span data-stu-id="86068-145">Ntlm</span></span>|<span data-ttu-id="86068-146">Mümkünse NTLM kimlik doğrulamasını belirtir ve Windows kimlik doğrulaması başarısız olursa.</span><span class="sxs-lookup"><span data-stu-id="86068-146">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="86068-147">Windows</span><span class="sxs-lookup"><span data-stu-id="86068-147">Windows</span></span>|<span data-ttu-id="86068-148">Windows tümleşik kimlik doğrulamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="86068-148">Specifies Windows integrated authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="86068-149">proxyCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="86068-149">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="86068-150">Değer</span><span class="sxs-lookup"><span data-stu-id="86068-150">Value</span></span>|<span data-ttu-id="86068-151">Açıklama</span><span class="sxs-lookup"><span data-stu-id="86068-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="86068-152">Yok.</span><span class="sxs-lookup"><span data-stu-id="86068-152">None</span></span>|<span data-ttu-id="86068-153">-İletiler aktarım sırasında güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="86068-153">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="86068-154">Temel</span><span class="sxs-lookup"><span data-stu-id="86068-154">Basic</span></span>|<span data-ttu-id="86068-155">RFC 2617 – HTTP kimlik doğrulaması tarafından tanımlanan temel kimlik doğrulamasını belirtir: Temel ve Özet kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="86068-155">Specifies basic authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="86068-156">Bilgisi</span><span class="sxs-lookup"><span data-stu-id="86068-156">Digest</span></span>|<span data-ttu-id="86068-157">RFC 2617 – HTTP kimlik doğrulaması tarafından tanımlanan Özet kimlik doğrulamasını belirtir: Temel ve Özet kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="86068-157">Specifies digest authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="86068-158">NT</span><span class="sxs-lookup"><span data-stu-id="86068-158">Ntlm</span></span>|<span data-ttu-id="86068-159">Mümkünse NTLM kimlik doğrulamasını belirtir ve Windows kimlik doğrulaması başarısız olursa.</span><span class="sxs-lookup"><span data-stu-id="86068-159">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="86068-160">Windows</span><span class="sxs-lookup"><span data-stu-id="86068-160">Windows</span></span>|<span data-ttu-id="86068-161">Windows tümleşik kimlik doğrulamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="86068-161">Specifies Windows integrated authentication.</span></span>|  
|<span data-ttu-id="86068-162">Sertifika</span><span class="sxs-lookup"><span data-stu-id="86068-162">Certificate</span></span>|<span data-ttu-id="86068-163">Bir sertifika kullanarak istemci kimlik doğrulaması gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="86068-163">Performs client authentication using a certificate.</span></span> <span data-ttu-id="86068-164">Bu seçenek yalnızca `Mode` üst `security` öğenin özniteliği Transport olarak ayarlandıysa ve yalnızca transportcredentialolarak ayarlandıysa işe yarar.</span><span class="sxs-lookup"><span data-stu-id="86068-164">This option works only if the `Mode` attribute of the parent `security` element is set to Transport, and will not work if it is set to TransportCredentialOnly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="86068-165">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="86068-165">Child Elements</span></span>  
 <span data-ttu-id="86068-166">Yok.</span><span class="sxs-lookup"><span data-stu-id="86068-166">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="86068-167">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="86068-167">Parent Elements</span></span>  
  
|<span data-ttu-id="86068-168">Öğe</span><span class="sxs-lookup"><span data-stu-id="86068-168">Element</span></span>|<span data-ttu-id="86068-169">Açıklama</span><span class="sxs-lookup"><span data-stu-id="86068-169">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="86068-170">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="86068-170">\<security></span></span>](security-of-basichttpbinding.md)|<span data-ttu-id="86068-171">[ \<BasicHttpBinding >](basichttpbinding.md)için güvenlik yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="86068-171">Defines the security capabilities for the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="86068-172">Örnek</span><span class="sxs-lookup"><span data-stu-id="86068-172">Example</span></span>  
 <span data-ttu-id="86068-173">Aşağıdaki örnek, temel bağlama ile SSL Aktarım güvenliği kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="86068-173">The following example demonstrates the use of SSL transport security with the basic binding.</span></span> <span data-ttu-id="86068-174">Varsayılan olarak, temel bağlama HTTP iletişimini destekler.</span><span class="sxs-lookup"><span data-stu-id="86068-174">By default, the basic binding supports HTTP communication.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="86068-175">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86068-175">See also</span></span>

- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.BasicHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- <xref:System.ServiceModel.HttpTransportSecurity>
- [<span data-ttu-id="86068-176">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="86068-176">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="86068-177">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="86068-177">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="86068-178">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="86068-178">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="86068-179">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="86068-179">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="86068-180">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="86068-180">\<binding></span></span>](../../../misc/binding.md)

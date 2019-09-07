---
title: <transport> / <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: 3b180006-1661-43bf-a699-96fd3da469af
ms.openlocfilehash: 521aaf3913a1d30d10a674b71d4d98affcabc296
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399349"
---
# <a name="transport-of-nethttpbinding"></a><span data-ttu-id="81111-102">\<\<NetHttpBinding > taşıma ></span><span class="sxs-lookup"><span data-stu-id="81111-102">\<transport> of \<netHttpBinding></span></span>
<span data-ttu-id="81111-103">HTTP taşıması için kimlik doğrulama parametrelerini denetleyen özellikleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="81111-103">Defines properties that control authentication parameters for the HTTP transport.</span></span>  
  
<span data-ttu-id="81111-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="81111-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="81111-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="81111-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="81111-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlama >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="81111-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="81111-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netHttpBinding >** ](nethttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="81111-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)</span></span>\
<span data-ttu-id="81111-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="81111-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="81111-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Güvenlik >** ](security-of-nethttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="81111-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-nethttpbinding.md)</span></span>\
<span data-ttu-id="81111-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Taşıma >**</span><span class="sxs-lookup"><span data-stu-id="81111-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81111-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="81111-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="81111-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="81111-112">Attributes and Elements</span></span>  
 <span data-ttu-id="81111-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="81111-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="81111-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="81111-114">Attributes</span></span>  
  
|<span data-ttu-id="81111-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="81111-115">Attribute</span></span>|<span data-ttu-id="81111-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="81111-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="81111-117">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="81111-117">clientCredentialType</span></span>|<span data-ttu-id="81111-118">-HTTP kimlik doğrulaması kullanarak istemci kimlik doğrulaması gerçekleştirirken kullanılacak kimlik bilgisinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="81111-118">-   Specifies the type of credential to be used when performing client authentication using HTTP authentication.</span></span>  <span data-ttu-id="81111-119">Varsayılan, `None` değeridir.</span><span class="sxs-lookup"><span data-stu-id="81111-119">The default is `None`.</span></span> <span data-ttu-id="81111-120">Bu öznitelik türü <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="81111-120">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|<span data-ttu-id="81111-121">proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="81111-121">proxyCredentialType</span></span>|<span data-ttu-id="81111-122">-HTTP üzerinden proxy kullanan bir etki alanı içinden istemci kimlik doğrulaması gerçekleştirirken kullanılacak kimlik bilgisinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="81111-122">-   Specifies the type of credential to be used when performing client authentication from within a domain using a proxy over HTTP.</span></span> <span data-ttu-id="81111-123">Bu öznitelik yalnızca `mode` üst `security` öğenin `Transport` özniteliği veya `TransportCredentialsOnly`olduğunda geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="81111-123">This attribute is applicable only when the `mode` attribute of the parent `security` element is `Transport` or `TransportCredentialsOnly`.</span></span> <span data-ttu-id="81111-124">Bu öznitelik türü <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="81111-124">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|<span data-ttu-id="81111-125">bölgesindeki</span><span class="sxs-lookup"><span data-stu-id="81111-125">realm</span></span>|<span data-ttu-id="81111-126">Özet veya temel kimlik doğrulaması için HTTP kimlik doğrulama düzeni tarafından kullanılan bölgeyi belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="81111-126">A string that specifies the realm that is used by the HTTP authentication scheme for digest or basic authentication.</span></span> <span data-ttu-id="81111-127">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="81111-127">The default is an empty string.</span></span>|  
|<span data-ttu-id="81111-128">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="81111-128">policyEnforcement</span></span>|<span data-ttu-id="81111-129">Bu numaralandırma, <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> ne zaman uygulanacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="81111-129">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="81111-130">1.  Hiçbir süre – ilke hiçbir şekilde zorlanmaz (genişletilmiş koruma devre dışı bırakılır).</span><span class="sxs-lookup"><span data-stu-id="81111-130">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="81111-131">2.  WhenSupported – ilke yalnızca istemci genişletilmiş korumayı destekliyorsa zorlanır.</span><span class="sxs-lookup"><span data-stu-id="81111-131">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="81111-132">3.  Her zaman – ilke her zaman zorlanır.</span><span class="sxs-lookup"><span data-stu-id="81111-132">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="81111-133">Genişletilmiş korumayı desteklemeyen istemciler kimlik doğrulaması yapamaz.</span><span class="sxs-lookup"><span data-stu-id="81111-133">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
|<span data-ttu-id="81111-134">protectionScenario</span><span class="sxs-lookup"><span data-stu-id="81111-134">protectionScenario</span></span>|<span data-ttu-id="81111-135">Bu numaralandırma, ilke tarafından zorlanan koruma senaryosunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="81111-135">This enumeration specifies the protection scenario enforced by the policy.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="81111-136">clientCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="81111-136">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="81111-137">Değer</span><span class="sxs-lookup"><span data-stu-id="81111-137">Value</span></span>|<span data-ttu-id="81111-138">Açıklama</span><span class="sxs-lookup"><span data-stu-id="81111-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="81111-139">Yok.</span><span class="sxs-lookup"><span data-stu-id="81111-139">None</span></span>|<span data-ttu-id="81111-140">Aktarım sırasında iletiler güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="81111-140">Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="81111-141">Temel</span><span class="sxs-lookup"><span data-stu-id="81111-141">Basic</span></span>|<span data-ttu-id="81111-142">Temel kimlik doğrulamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="81111-142">Specifies basic authentication.</span></span>|  
|<span data-ttu-id="81111-143">Bilgisi</span><span class="sxs-lookup"><span data-stu-id="81111-143">Digest</span></span>|<span data-ttu-id="81111-144">Özet kimlik doğrulamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="81111-144">Specifies digest authentication.</span></span>|  
|<span data-ttu-id="81111-145">NT</span><span class="sxs-lookup"><span data-stu-id="81111-145">Ntlm</span></span>|<span data-ttu-id="81111-146">Mümkünse NTLM kimlik doğrulamasını belirtir ve Windows kimlik doğrulaması başarısız olursa.</span><span class="sxs-lookup"><span data-stu-id="81111-146">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="81111-147">Windows</span><span class="sxs-lookup"><span data-stu-id="81111-147">Windows</span></span>|<span data-ttu-id="81111-148">Windows tümleşik kimlik doğrulamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="81111-148">Specifies Windows integrated authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="81111-149">proxyCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="81111-149">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="81111-150">Değer</span><span class="sxs-lookup"><span data-stu-id="81111-150">Value</span></span>|<span data-ttu-id="81111-151">Açıklama</span><span class="sxs-lookup"><span data-stu-id="81111-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="81111-152">Yok.</span><span class="sxs-lookup"><span data-stu-id="81111-152">None</span></span>|<span data-ttu-id="81111-153">-İletiler aktarım sırasında güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="81111-153">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="81111-154">Temel</span><span class="sxs-lookup"><span data-stu-id="81111-154">Basic</span></span>|<span data-ttu-id="81111-155">RFC 2617 – HTTP kimlik doğrulaması tarafından tanımlanan temel kimlik doğrulamasını belirtir: Temel ve Özet kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="81111-155">Specifies basic authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="81111-156">Bilgisi</span><span class="sxs-lookup"><span data-stu-id="81111-156">Digest</span></span>|<span data-ttu-id="81111-157">RFC 2617 – HTTP kimlik doğrulaması tarafından tanımlanan Özet kimlik doğrulamasını belirtir: Temel ve Özet kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="81111-157">Specifies digest authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="81111-158">NT</span><span class="sxs-lookup"><span data-stu-id="81111-158">Ntlm</span></span>|<span data-ttu-id="81111-159">Mümkünse NTLM kimlik doğrulamasını belirtir ve Windows kimlik doğrulaması başarısız olursa.</span><span class="sxs-lookup"><span data-stu-id="81111-159">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="81111-160">Windows</span><span class="sxs-lookup"><span data-stu-id="81111-160">Windows</span></span>|<span data-ttu-id="81111-161">Windows tümleşik kimlik doğrulamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="81111-161">Specifies Windows integrated authentication.</span></span>|  
|<span data-ttu-id="81111-162">Sertifika</span><span class="sxs-lookup"><span data-stu-id="81111-162">Certificate</span></span>|<span data-ttu-id="81111-163">Bir sertifika kullanarak istemci kimlik doğrulaması gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="81111-163">Performs client authentication using a certificate.</span></span> <span data-ttu-id="81111-164">Bu seçenek yalnızca `Mode` üst `security` öğenin özniteliği Transport olarak ayarlandıysa ve yalnızca transportcredentialolarak ayarlandıysa işe yarar.</span><span class="sxs-lookup"><span data-stu-id="81111-164">This option works only if the `Mode` attribute of the parent `security` element is set to Transport, and will not work if it is set to TransportCredentialOnly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="81111-165">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="81111-165">Child Elements</span></span>  
 <span data-ttu-id="81111-166">Yok.</span><span class="sxs-lookup"><span data-stu-id="81111-166">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="81111-167">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="81111-167">Parent Elements</span></span>  
  
|<span data-ttu-id="81111-168">Öğe</span><span class="sxs-lookup"><span data-stu-id="81111-168">Element</span></span>|<span data-ttu-id="81111-169">Açıklama</span><span class="sxs-lookup"><span data-stu-id="81111-169">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="81111-170">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="81111-170">\<security></span></span>](security-of-nethttpbinding.md)|<span data-ttu-id="81111-171">[ \<NetHttpBinding >](nethttpbinding.md)için güvenlik yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="81111-171">Defines the security capabilities for the [\<netHttpBinding>](nethttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="81111-172">Örnek</span><span class="sxs-lookup"><span data-stu-id="81111-172">Example</span></span>  
 <span data-ttu-id="81111-173">Aşağıdaki örnek, temel bağlama ile SSL Aktarım güvenliği kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="81111-173">The following example demonstrates the use of SSL transport security with the basic binding.</span></span> <span data-ttu-id="81111-174">Varsayılan olarak, temel bağlama HTTP iletişimini destekler.</span><span class="sxs-lookup"><span data-stu-id="81111-174">By default, the basic binding supports HTTP communication.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="81111-175">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="81111-175">See also</span></span>

- <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- <xref:System.ServiceModel.HttpTransportSecurity>
- [<span data-ttu-id="81111-176">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="81111-176">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="81111-177">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="81111-177">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="81111-178">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="81111-178">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="81111-179">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="81111-179">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="81111-180">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="81111-180">\<binding></span></span>](../../../misc/binding.md)

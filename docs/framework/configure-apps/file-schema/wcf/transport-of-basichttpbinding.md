---
title: <transport> / <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 4c5ba293-3d7e-47a6-b84e-e9022857b7e5
ms.openlocfilehash: af5852c3c7850f91686d50294c8846f85574e909
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918630"
---
# <a name="transport-of-basichttpbinding"></a><span data-ttu-id="97423-102">\<\<BasicHttpBinding > taşıma ></span><span class="sxs-lookup"><span data-stu-id="97423-102">\<transport> of \<basicHttpBinding></span></span>
<span data-ttu-id="97423-103">HTTP taşıması için kimlik doğrulama parametrelerini denetleyen özellikleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="97423-103">Defines properties that control authentication parameters for the HTTP transport.</span></span>  
  
 <span data-ttu-id="97423-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="97423-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="97423-105">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="97423-105">\<bindings></span></span>  
<span data-ttu-id="97423-106">\<basicHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="97423-106">\<basicHttpBinding></span></span>  
<span data-ttu-id="97423-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="97423-107">\<binding></span></span>  
<span data-ttu-id="97423-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="97423-108">\<security></span></span>  
<span data-ttu-id="97423-109">\<Taşıma ></span><span class="sxs-lookup"><span data-stu-id="97423-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97423-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="97423-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="97423-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="97423-111">Attributes and Elements</span></span>  
 <span data-ttu-id="97423-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="97423-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="97423-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="97423-113">Attributes</span></span>  
  
|<span data-ttu-id="97423-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="97423-114">Attribute</span></span>|<span data-ttu-id="97423-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="97423-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="97423-116">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="97423-116">clientCredentialType</span></span>|<span data-ttu-id="97423-117">-HTTP kimlik doğrulaması kullanarak istemci kimlik doğrulaması gerçekleştirirken kullanılacak kimlik bilgisinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="97423-117">-   Specifies the type of credential to be used when performing client authentication using HTTP authentication.</span></span>  <span data-ttu-id="97423-118">Varsayılan, `None` değeridir.</span><span class="sxs-lookup"><span data-stu-id="97423-118">The default is `None`.</span></span> <span data-ttu-id="97423-119">Bu öznitelik türü <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="97423-119">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|<span data-ttu-id="97423-120">proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="97423-120">proxyCredentialType</span></span>|<span data-ttu-id="97423-121">-HTTP üzerinden proxy kullanan bir etki alanı içinden istemci kimlik doğrulaması gerçekleştirirken kullanılacak kimlik bilgisinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="97423-121">-   Specifies the type of credential to be used when performing client authentication from within a domain using a proxy over HTTP.</span></span> <span data-ttu-id="97423-122">Bu öznitelik yalnızca `mode` üst `security` öğenin `Transport` özniteliği veya `TransportCredentialsOnly`olduğunda geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="97423-122">This attribute is applicable only when the `mode` attribute of the parent `security` element is `Transport` or `TransportCredentialsOnly`.</span></span> <span data-ttu-id="97423-123">Bu öznitelik türü <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="97423-123">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|<span data-ttu-id="97423-124">bölgesindeki</span><span class="sxs-lookup"><span data-stu-id="97423-124">realm</span></span>|<span data-ttu-id="97423-125">Özet veya temel kimlik doğrulaması için HTTP kimlik doğrulama düzeni tarafından kullanılan bölgeyi belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="97423-125">A string that specifies the realm that is used by the HTTP authentication scheme for digest or basic authentication.</span></span> <span data-ttu-id="97423-126">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="97423-126">The default is an empty string.</span></span>|  
|<span data-ttu-id="97423-127">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="97423-127">policyEnforcement</span></span>|<span data-ttu-id="97423-128">Bu numaralandırma, <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> ne zaman uygulanacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="97423-128">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="97423-129">1.  Hiçbir süre – ilke hiçbir şekilde zorlanmaz (genişletilmiş koruma devre dışı bırakılır).</span><span class="sxs-lookup"><span data-stu-id="97423-129">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="97423-130">2.  WhenSupported – ilke yalnızca istemci genişletilmiş korumayı destekliyorsa zorlanır.</span><span class="sxs-lookup"><span data-stu-id="97423-130">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="97423-131">3.  Her zaman – ilke her zaman zorlanır.</span><span class="sxs-lookup"><span data-stu-id="97423-131">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="97423-132">Genişletilmiş korumayı desteklemeyen istemciler kimlik doğrulaması yapamaz.</span><span class="sxs-lookup"><span data-stu-id="97423-132">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
|<span data-ttu-id="97423-133">protectionScenario</span><span class="sxs-lookup"><span data-stu-id="97423-133">protectionScenario</span></span>|<span data-ttu-id="97423-134">Bu numaralandırma, ilke tarafından zorlanan koruma senaryosunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="97423-134">This enumeration specifies the protection scenario enforced by the policy.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="97423-135">clientCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="97423-135">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="97423-136">Değer</span><span class="sxs-lookup"><span data-stu-id="97423-136">Value</span></span>|<span data-ttu-id="97423-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="97423-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="97423-138">Yok.</span><span class="sxs-lookup"><span data-stu-id="97423-138">None</span></span>|<span data-ttu-id="97423-139">Aktarım sırasında iletiler güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="97423-139">Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="97423-140">Temel</span><span class="sxs-lookup"><span data-stu-id="97423-140">Basic</span></span>|<span data-ttu-id="97423-141">Temel kimlik doğrulamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="97423-141">Specifies basic authentication.</span></span>|  
|<span data-ttu-id="97423-142">Bilgisi</span><span class="sxs-lookup"><span data-stu-id="97423-142">Digest</span></span>|<span data-ttu-id="97423-143">Özet kimlik doğrulamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="97423-143">Specifies digest authentication.</span></span>|  
|<span data-ttu-id="97423-144">NT</span><span class="sxs-lookup"><span data-stu-id="97423-144">Ntlm</span></span>|<span data-ttu-id="97423-145">Mümkünse NTLM kimlik doğrulamasını belirtir ve Windows kimlik doğrulaması başarısız olursa.</span><span class="sxs-lookup"><span data-stu-id="97423-145">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="97423-146">Windows</span><span class="sxs-lookup"><span data-stu-id="97423-146">Windows</span></span>|<span data-ttu-id="97423-147">Windows tümleşik kimlik doğrulamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="97423-147">Specifies Windows integrated authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="97423-148">proxyCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="97423-148">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="97423-149">Değer</span><span class="sxs-lookup"><span data-stu-id="97423-149">Value</span></span>|<span data-ttu-id="97423-150">Açıklama</span><span class="sxs-lookup"><span data-stu-id="97423-150">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="97423-151">Yok.</span><span class="sxs-lookup"><span data-stu-id="97423-151">None</span></span>|<span data-ttu-id="97423-152">-İletiler aktarım sırasında güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="97423-152">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="97423-153">Temel</span><span class="sxs-lookup"><span data-stu-id="97423-153">Basic</span></span>|<span data-ttu-id="97423-154">RFC 2617 – HTTP kimlik doğrulaması tarafından tanımlanan temel kimlik doğrulamasını belirtir: Temel ve Özet kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="97423-154">Specifies basic authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="97423-155">Bilgisi</span><span class="sxs-lookup"><span data-stu-id="97423-155">Digest</span></span>|<span data-ttu-id="97423-156">RFC 2617 – HTTP kimlik doğrulaması tarafından tanımlanan Özet kimlik doğrulamasını belirtir: Temel ve Özet kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="97423-156">Specifies digest authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="97423-157">NT</span><span class="sxs-lookup"><span data-stu-id="97423-157">Ntlm</span></span>|<span data-ttu-id="97423-158">Mümkünse NTLM kimlik doğrulamasını belirtir ve Windows kimlik doğrulaması başarısız olursa.</span><span class="sxs-lookup"><span data-stu-id="97423-158">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="97423-159">Windows</span><span class="sxs-lookup"><span data-stu-id="97423-159">Windows</span></span>|<span data-ttu-id="97423-160">Windows tümleşik kimlik doğrulamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="97423-160">Specifies Windows integrated authentication.</span></span>|  
|<span data-ttu-id="97423-161">Sertifika</span><span class="sxs-lookup"><span data-stu-id="97423-161">Certificate</span></span>|<span data-ttu-id="97423-162">Bir sertifika kullanarak istemci kimlik doğrulaması gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="97423-162">Performs client authentication using a certificate.</span></span> <span data-ttu-id="97423-163">Bu seçenek yalnızca `Mode` üst `security` öğenin özniteliği Transport olarak ayarlandıysa ve yalnızca transportcredentialolarak ayarlandıysa işe yarar.</span><span class="sxs-lookup"><span data-stu-id="97423-163">This option works only if the `Mode` attribute of the parent `security` element is set to Transport, and will not work if it is set to TransportCredentialOnly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="97423-164">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="97423-164">Child Elements</span></span>  
 <span data-ttu-id="97423-165">Yok.</span><span class="sxs-lookup"><span data-stu-id="97423-165">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="97423-166">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="97423-166">Parent Elements</span></span>  
  
|<span data-ttu-id="97423-167">Öğe</span><span class="sxs-lookup"><span data-stu-id="97423-167">Element</span></span>|<span data-ttu-id="97423-168">Açıklama</span><span class="sxs-lookup"><span data-stu-id="97423-168">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="97423-169">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="97423-169">\<security></span></span>](security-of-basichttpbinding.md)|<span data-ttu-id="97423-170">[ \<BasicHttpBinding >](basichttpbinding.md)için güvenlik yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="97423-170">Defines the security capabilities for the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="97423-171">Örnek</span><span class="sxs-lookup"><span data-stu-id="97423-171">Example</span></span>  
 <span data-ttu-id="97423-172">Aşağıdaki örnek, temel bağlama ile SSL Aktarım güvenliği kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="97423-172">The following example demonstrates the use of SSL transport security with the basic binding.</span></span> <span data-ttu-id="97423-173">Varsayılan olarak, temel bağlama HTTP iletişimini destekler.</span><span class="sxs-lookup"><span data-stu-id="97423-173">By default, the basic binding supports HTTP communication.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="97423-174">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="97423-174">See also</span></span>

- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.BasicHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- <xref:System.ServiceModel.HttpTransportSecurity>
- [<span data-ttu-id="97423-175">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="97423-175">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="97423-176">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="97423-176">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="97423-177">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="97423-177">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="97423-178">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="97423-178">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="97423-179">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="97423-179">\<binding></span></span>](../../../misc/binding.md)

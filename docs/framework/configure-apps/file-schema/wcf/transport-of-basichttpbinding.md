---
title: <transport> , <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 4c5ba293-3d7e-47a6-b84e-e9022857b7e5
ms.openlocfilehash: 5d1ef059f8fde7c41e333571d1c025a9c0c7e03f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59170644"
---
# <a name="transport-of-basichttpbinding"></a><span data-ttu-id="e3edb-102">\<Aktarım >, \<basicHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="e3edb-102">\<transport> of \<basicHttpBinding></span></span>
<span data-ttu-id="e3edb-103">HTTP taşıma için kimlik doğrulama parametrelerini denetleyen özellikleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e3edb-103">Defines properties that control authentication parameters for the HTTP transport.</span></span>  
  
 <span data-ttu-id="e3edb-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e3edb-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e3edb-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="e3edb-105">\<bindings></span></span>  
<span data-ttu-id="e3edb-106">\<basicHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="e3edb-106">\<basicHttpBinding></span></span>  
<span data-ttu-id="e3edb-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="e3edb-107">\<binding></span></span>  
<span data-ttu-id="e3edb-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="e3edb-108">\<security></span></span>  
<span data-ttu-id="e3edb-109">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="e3edb-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3edb-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e3edb-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e3edb-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e3edb-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e3edb-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e3edb-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e3edb-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e3edb-113">Attributes</span></span>  
  
|<span data-ttu-id="e3edb-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e3edb-114">Attribute</span></span>|<span data-ttu-id="e3edb-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e3edb-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e3edb-116">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="e3edb-116">clientCredentialType</span></span>|<span data-ttu-id="e3edb-117">-HTTP kimlik doğrulaması kullanarak istemci kimlik doğrulaması yapılırken kullanılacak kimlik bilgisi türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="e3edb-117">-   Specifies the type of credential to be used when performing client authentication using HTTP authentication.</span></span>  <span data-ttu-id="e3edb-118">Varsayılan, `None` değeridir.</span><span class="sxs-lookup"><span data-stu-id="e3edb-118">The default is `None`.</span></span> <span data-ttu-id="e3edb-119">Bu öznitelik türünde <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="e3edb-119">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|<span data-ttu-id="e3edb-120">proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="e3edb-120">proxyCredentialType</span></span>|<span data-ttu-id="e3edb-121">-Gelen istemci kimlik doğrulaması Ara sunucu kullanarak HTTP üzerinden bir etki alanı içinde gerçekleştirirken kullanılacak kimlik bilgisi türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="e3edb-121">-   Specifies the type of credential to be used when performing client authentication from within a domain using a proxy over HTTP.</span></span> <span data-ttu-id="e3edb-122">Bu özniteliği yalnızca uygun olduğunda, `mode` üst öğenin özniteliğini `security` öğesi `Transport` veya `TransportCredentialsOnly`.</span><span class="sxs-lookup"><span data-stu-id="e3edb-122">This attribute is applicable only when the `mode` attribute of the parent `security` element is `Transport` or `TransportCredentialsOnly`.</span></span> <span data-ttu-id="e3edb-123">Bu öznitelik türünde <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="e3edb-123">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|<span data-ttu-id="e3edb-124">Bölge</span><span class="sxs-lookup"><span data-stu-id="e3edb-124">realm</span></span>|<span data-ttu-id="e3edb-125">HTTP kimlik doğrulama şemasının Özet veya temel kimlik doğrulaması için kullanılan ölge belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="e3edb-125">A string that specifies the realm that is used by the HTTP authentication scheme for digest or basic authentication.</span></span> <span data-ttu-id="e3edb-126">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="e3edb-126">The default is an empty string.</span></span>|  
|<span data-ttu-id="e3edb-127">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="e3edb-127">policyEnforcement</span></span>|<span data-ttu-id="e3edb-128">Bu sabit listesi ne zaman belirtir <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> zorlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e3edb-128">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="e3edb-129">1.  Hiçbir zaman – hiçbir zaman ilkenin uygulanıp (genişletilmiş koruma devre dışı).</span><span class="sxs-lookup"><span data-stu-id="e3edb-129">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="e3edb-130">2.  Yalnızca istemci genişletilmiş koruma destekliyorsa WhenSupported – ilke zorunlu tutulur.</span><span class="sxs-lookup"><span data-stu-id="e3edb-130">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="e3edb-131">3.  Her zaman – ilke her zaman uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="e3edb-131">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="e3edb-132">Genişletilmiş Koruma desteklemeyen istemciler kimlik doğrulaması başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="e3edb-132">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
|<span data-ttu-id="e3edb-133">protectionScenario</span><span class="sxs-lookup"><span data-stu-id="e3edb-133">protectionScenario</span></span>|<span data-ttu-id="e3edb-134">Bu numaralandırma, ilke tarafından zorunlu koruma senaryosu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e3edb-134">This enumeration specifies the protection scenario enforced by the policy.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="e3edb-135">clientCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="e3edb-135">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="e3edb-136">Değer</span><span class="sxs-lookup"><span data-stu-id="e3edb-136">Value</span></span>|<span data-ttu-id="e3edb-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e3edb-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e3edb-138">None</span><span class="sxs-lookup"><span data-stu-id="e3edb-138">None</span></span>|<span data-ttu-id="e3edb-139">İleti aktarımı sırasında sağlanmaz.</span><span class="sxs-lookup"><span data-stu-id="e3edb-139">Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="e3edb-140">Temel</span><span class="sxs-lookup"><span data-stu-id="e3edb-140">Basic</span></span>|<span data-ttu-id="e3edb-141">Temel kimlik doğrulaması belirtir.</span><span class="sxs-lookup"><span data-stu-id="e3edb-141">Specifies basic authentication.</span></span>|  
|<span data-ttu-id="e3edb-142">Özet</span><span class="sxs-lookup"><span data-stu-id="e3edb-142">Digest</span></span>|<span data-ttu-id="e3edb-143">Özet kimlik doğrulaması belirtir.</span><span class="sxs-lookup"><span data-stu-id="e3edb-143">Specifies digest authentication.</span></span>|  
|<span data-ttu-id="e3edb-144">NTLM</span><span class="sxs-lookup"><span data-stu-id="e3edb-144">Ntlm</span></span>|<span data-ttu-id="e3edb-145">Mümkün olduğunda ve Windows kimlik doğrulaması başarısız olursa, NTLM kimlik doğrulaması belirtir.</span><span class="sxs-lookup"><span data-stu-id="e3edb-145">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="e3edb-146">Windows</span><span class="sxs-lookup"><span data-stu-id="e3edb-146">Windows</span></span>|<span data-ttu-id="e3edb-147">Windows tümleşik kimlik doğrulaması belirtir.</span><span class="sxs-lookup"><span data-stu-id="e3edb-147">Specifies Windows integrated authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="e3edb-148">proxyCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="e3edb-148">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="e3edb-149">Değer</span><span class="sxs-lookup"><span data-stu-id="e3edb-149">Value</span></span>|<span data-ttu-id="e3edb-150">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e3edb-150">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e3edb-151">None</span><span class="sxs-lookup"><span data-stu-id="e3edb-151">None</span></span>|<span data-ttu-id="e3edb-152">-Sıradaki iletiler, aktarım sırasında sağlanmaz.</span><span class="sxs-lookup"><span data-stu-id="e3edb-152">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="e3edb-153">Temel</span><span class="sxs-lookup"><span data-stu-id="e3edb-153">Basic</span></span>|<span data-ttu-id="e3edb-154">Temel kimlik doğrulaması, RFC 2617 – HTTP kimlik doğrulaması tarafından tanımlanan belirtir: Temel ve Özet kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="e3edb-154">Specifies basic authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="e3edb-155">Özet</span><span class="sxs-lookup"><span data-stu-id="e3edb-155">Digest</span></span>|<span data-ttu-id="e3edb-156">Özet kimlik doğrulaması, RFC 2617 – HTTP kimlik doğrulaması tarafından tanımlanan belirtir: Temel ve Özet kimlik doğrulama.</span><span class="sxs-lookup"><span data-stu-id="e3edb-156">Specifies digest authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="e3edb-157">NTLM</span><span class="sxs-lookup"><span data-stu-id="e3edb-157">Ntlm</span></span>|<span data-ttu-id="e3edb-158">Mümkün olduğunda ve Windows kimlik doğrulaması başarısız olursa, NTLM kimlik doğrulaması belirtir.</span><span class="sxs-lookup"><span data-stu-id="e3edb-158">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="e3edb-159">Windows</span><span class="sxs-lookup"><span data-stu-id="e3edb-159">Windows</span></span>|<span data-ttu-id="e3edb-160">Windows tümleşik kimlik doğrulaması belirtir.</span><span class="sxs-lookup"><span data-stu-id="e3edb-160">Specifies Windows integrated authentication.</span></span>|  
|<span data-ttu-id="e3edb-161">Sertifika</span><span class="sxs-lookup"><span data-stu-id="e3edb-161">Certificate</span></span>|<span data-ttu-id="e3edb-162">Bir sertifika kullanarak bir istemci kimlik doğrulaması gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="e3edb-162">Performs client authentication using a certificate.</span></span> <span data-ttu-id="e3edb-163">Bu seçenek yalnızca çalışır `Mode` üst öğenin özniteliğini `security` öğe taşıma imkanı kullanılarak ayarlanır ve TransportCredentialOnly için ayarlanmışsa çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="e3edb-163">This option works only if the `Mode` attribute of the parent `security` element is set to Transport, and will not work if it is set to TransportCredentialOnly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e3edb-164">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e3edb-164">Child Elements</span></span>  
 <span data-ttu-id="e3edb-165">None</span><span class="sxs-lookup"><span data-stu-id="e3edb-165">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e3edb-166">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e3edb-166">Parent Elements</span></span>  
  
|<span data-ttu-id="e3edb-167">Öğe</span><span class="sxs-lookup"><span data-stu-id="e3edb-167">Element</span></span>|<span data-ttu-id="e3edb-168">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e3edb-168">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e3edb-169">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="e3edb-169">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|<span data-ttu-id="e3edb-170">İçin güvenlik özelliklerini tanımlar [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="e3edb-170">Defines the security capabilities for the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e3edb-171">Örnek</span><span class="sxs-lookup"><span data-stu-id="e3edb-171">Example</span></span>  
 <span data-ttu-id="e3edb-172">Aşağıdaki örnek, basit bağlama ile SSL Aktarım güvenliği kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e3edb-172">The following example demonstrates the use of SSL transport security with the basic binding.</span></span> <span data-ttu-id="e3edb-173">Varsayılan olarak, HTTP iletişimi için temel bağlamayı destekler.</span><span class="sxs-lookup"><span data-stu-id="e3edb-173">By default, the basic binding supports HTTP communication.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e3edb-174">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e3edb-174">See also</span></span>

- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.BasicHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- <xref:System.ServiceModel.HttpTransportSecurity>
- [<span data-ttu-id="e3edb-175">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="e3edb-175">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="e3edb-176">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="e3edb-176">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="e3edb-177">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e3edb-177">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="e3edb-178">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="e3edb-178">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="e3edb-179">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="e3edb-179">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)

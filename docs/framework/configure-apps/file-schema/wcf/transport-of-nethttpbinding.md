---
title: '&lt;netHttpBinding&gt; &lt;taşıma&gt;'
ms.date: 03/30/2017
ms.assetid: 3b180006-1661-43bf-a699-96fd3da469af
ms.openlocfilehash: 6603e590632f0bc21a2d98482d1f42f03bb9d9e7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="lttransportgt-of-ltnethttpbindinggt"></a><span data-ttu-id="d6378-102">&lt;netHttpBinding&gt; &lt;taşıma&gt;</span><span class="sxs-lookup"><span data-stu-id="d6378-102">&lt;transport&gt; of &lt;netHttpBinding&gt;</span></span>
<span data-ttu-id="d6378-103">HTTP taşıma için kimlik doğrulama parametrelerini denetleyen özellikler tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d6378-103">Defines properties that control authentication parameters for the HTTP transport.</span></span>  
  
<span data-ttu-id="d6378-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d6378-104">\<system.serviceModel></span></span>  
<span data-ttu-id="d6378-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="d6378-105">\<bindings></span></span>  
<span data-ttu-id="d6378-106">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="d6378-106">\<netHttpBinding></span></span>  
<span data-ttu-id="d6378-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="d6378-107">\<binding></span></span>  
<span data-ttu-id="d6378-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="d6378-108">\<security></span></span>  
<span data-ttu-id="d6378-109">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="d6378-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6378-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d6378-110">Syntax</span></span>  
  
```xml
<netHttpBinding>  
  <binding>  
    <security mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">  
      <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"  
                 proxyCredentialType="None|Basic|Digest|Ntlm|Windows" realm="string">  
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"  
                                  protectionScenario="TransportSelected|TrustedProxy">  
          <customServiceNames></customServiceNames>  
        </extendedProtectionPolicy>  
      </transport>  
    </security>  
  </binding>  
</netHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d6378-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d6378-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d6378-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d6378-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d6378-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d6378-113">Attributes</span></span>  
  
|<span data-ttu-id="d6378-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d6378-114">Attribute</span></span>|<span data-ttu-id="d6378-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d6378-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d6378-116">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="d6378-116">clientCredentialType</span></span>|<span data-ttu-id="d6378-117">-HTTP kimlik doğrulaması kullanarak istemci kimlik doğrulaması yapılırken kullanılacak kimlik bilgileri türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="d6378-117">-   Specifies the type of credential to be used when performing client authentication using HTTP authentication.</span></span>  <span data-ttu-id="d6378-118">Varsayılan, `None` değeridir.</span><span class="sxs-lookup"><span data-stu-id="d6378-118">The default is `None`.</span></span> <span data-ttu-id="d6378-119">Bu öznitelik türünde <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="d6378-119">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|<span data-ttu-id="d6378-120">proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="d6378-120">proxyCredentialType</span></span>|<span data-ttu-id="d6378-121">-İstemci kimlik doğrulamasını bir proxy sunucu HTTP üzerinden kullanarak bir etki alanı içinde gerçekleştirirken kullanılacak kimlik bilgileri türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="d6378-121">-   Specifies the type of credential to be used when performing client authentication from within a domain using a proxy over HTTP.</span></span> <span data-ttu-id="d6378-122">Bu öznitelik yalnızca uygun olduğunda olan `mode` üst öznitelik `security` öğesi `Transport` veya `TransportCredentialsOnly`.</span><span class="sxs-lookup"><span data-stu-id="d6378-122">This attribute is applicable only when the `mode` attribute of the parent `security` element is `Transport` or `TransportCredentialsOnly`.</span></span> <span data-ttu-id="d6378-123">Bu öznitelik türünde <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="d6378-123">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|<span data-ttu-id="d6378-124">Bölge</span><span class="sxs-lookup"><span data-stu-id="d6378-124">realm</span></span>|<span data-ttu-id="d6378-125">HTTP kimlik doğrulama şeması tarafından Özet veya temel kimlik doğrulaması için kullanılan bölge belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="d6378-125">A string that specifies the realm that is used by the HTTP authentication scheme for digest or basic authentication.</span></span> <span data-ttu-id="d6378-126">Varsayılan boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="d6378-126">The default is an empty string.</span></span>|  
|<span data-ttu-id="d6378-127">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="d6378-127">policyEnforcement</span></span>|<span data-ttu-id="d6378-128">Bu numaralandırma ne zaman belirtir <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> zorunlu tutulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d6378-128">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="d6378-129">1.  Hiçbir zaman – ilke hiçbir zaman zorlanır (genişletilmiş koruma devre dışı).</span><span class="sxs-lookup"><span data-stu-id="d6378-129">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="d6378-130">2.  Yalnızca istemci genişletilmiş koruma destekliyorsa WhenSupported – ilke uygulanır.</span><span class="sxs-lookup"><span data-stu-id="d6378-130">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="d6378-131">3.  Her zaman – ilke her zaman zorlanır.</span><span class="sxs-lookup"><span data-stu-id="d6378-131">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="d6378-132">Genişletilmiş Koruma desteklemeyen istemcilerin kimliğini doğrulamak başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="d6378-132">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
|<span data-ttu-id="d6378-133">protectionScenario</span><span class="sxs-lookup"><span data-stu-id="d6378-133">protectionScenario</span></span>|<span data-ttu-id="d6378-134">Bu numaralandırma ilke tarafından zorlanan koruma senaryosu belirtir.</span><span class="sxs-lookup"><span data-stu-id="d6378-134">This enumeration specifies the protection scenario enforced by the policy.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="d6378-135">clientCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="d6378-135">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="d6378-136">Değer</span><span class="sxs-lookup"><span data-stu-id="d6378-136">Value</span></span>|<span data-ttu-id="d6378-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d6378-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d6378-138">Yok.</span><span class="sxs-lookup"><span data-stu-id="d6378-138">None</span></span>|<span data-ttu-id="d6378-139">İleti aktarımı sırasında sağlanmaz.</span><span class="sxs-lookup"><span data-stu-id="d6378-139">Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="d6378-140">Temel</span><span class="sxs-lookup"><span data-stu-id="d6378-140">Basic</span></span>|<span data-ttu-id="d6378-141">Temel kimlik doğrulaması belirtir.</span><span class="sxs-lookup"><span data-stu-id="d6378-141">Specifies basic authentication.</span></span>|  
|<span data-ttu-id="d6378-142">Özet</span><span class="sxs-lookup"><span data-stu-id="d6378-142">Digest</span></span>|<span data-ttu-id="d6378-143">Özet kimlik doğrulaması belirtir.</span><span class="sxs-lookup"><span data-stu-id="d6378-143">Specifies digest authentication.</span></span>|  
|<span data-ttu-id="d6378-144">NTLM</span><span class="sxs-lookup"><span data-stu-id="d6378-144">Ntlm</span></span>|<span data-ttu-id="d6378-145">NTLM kimlik doğrulaması, mümkün olduğunda ve Windows kimlik doğrulaması başarısız olursa belirtir.</span><span class="sxs-lookup"><span data-stu-id="d6378-145">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="d6378-146">Windows</span><span class="sxs-lookup"><span data-stu-id="d6378-146">Windows</span></span>|<span data-ttu-id="d6378-147">Windows tümleşik kimlik doğrulaması belirtir.</span><span class="sxs-lookup"><span data-stu-id="d6378-147">Specifies Windows integrated authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="d6378-148">proxyCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="d6378-148">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="d6378-149">Değer</span><span class="sxs-lookup"><span data-stu-id="d6378-149">Value</span></span>|<span data-ttu-id="d6378-150">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d6378-150">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d6378-151">Yok.</span><span class="sxs-lookup"><span data-stu-id="d6378-151">None</span></span>|<span data-ttu-id="d6378-152">-Aktarım sırasında iletileri güvenli değil.</span><span class="sxs-lookup"><span data-stu-id="d6378-152">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="d6378-153">Temel</span><span class="sxs-lookup"><span data-stu-id="d6378-153">Basic</span></span>|<span data-ttu-id="d6378-154">Temel kimlik doğrulaması RFC 2617 – HTTP kimlik doğrulaması tarafından tanımlandığı şekilde belirtir: temel ve Özet kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="d6378-154">Specifies basic authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="d6378-155">Özet</span><span class="sxs-lookup"><span data-stu-id="d6378-155">Digest</span></span>|<span data-ttu-id="d6378-156">Özet kimlik doğrulaması RFC 2617 – HTTP kimlik doğrulaması tarafından tanımlandığı şekilde belirtir: temel ve Özet kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="d6378-156">Specifies digest authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="d6378-157">NTLM</span><span class="sxs-lookup"><span data-stu-id="d6378-157">Ntlm</span></span>|<span data-ttu-id="d6378-158">NTLM kimlik doğrulaması, mümkün olduğunda ve Windows kimlik doğrulaması başarısız olursa belirtir.</span><span class="sxs-lookup"><span data-stu-id="d6378-158">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="d6378-159">Windows</span><span class="sxs-lookup"><span data-stu-id="d6378-159">Windows</span></span>|<span data-ttu-id="d6378-160">Windows tümleşik kimlik doğrulaması belirtir.</span><span class="sxs-lookup"><span data-stu-id="d6378-160">Specifies Windows integrated authentication.</span></span>|  
|<span data-ttu-id="d6378-161">Sertifika</span><span class="sxs-lookup"><span data-stu-id="d6378-161">Certificate</span></span>|<span data-ttu-id="d6378-162">Bir sertifika kullanarak istemci kimlik doğrulaması gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="d6378-162">Performs client authentication using a certificate.</span></span> <span data-ttu-id="d6378-163">Bu seçenek yalnızca çalışır `Mode` üst öznitelik `security` öğesi taşıma için ayarlanır ve TransportCredentialOnly için ayarlarsanız çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="d6378-163">This option works only if the `Mode` attribute of the parent `security` element is set to Transport, and will not work if it is set to TransportCredentialOnly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d6378-164">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d6378-164">Child Elements</span></span>  
 <span data-ttu-id="d6378-165">Yok.</span><span class="sxs-lookup"><span data-stu-id="d6378-165">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d6378-166">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d6378-166">Parent Elements</span></span>  
  
|<span data-ttu-id="d6378-167">Öğe</span><span class="sxs-lookup"><span data-stu-id="d6378-167">Element</span></span>|<span data-ttu-id="d6378-168">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d6378-168">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d6378-169">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="d6378-169">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nethttpbinding.md)|<span data-ttu-id="d6378-170">Güvenlik özellikleri için tanımlar [ \<netHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nethttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="d6378-170">Defines the security capabilities for the [\<netHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/nethttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d6378-171">Örnek</span><span class="sxs-lookup"><span data-stu-id="d6378-171">Example</span></span>  
 <span data-ttu-id="d6378-172">Aşağıdaki örnek, temel bağlama ile SSL taşıma güvenliği kullanımını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="d6378-172">The following example demonstrates the use of SSL transport security with the basic binding.</span></span> <span data-ttu-id="d6378-173">Varsayılan olarak, temel bağlama HTTP iletişimi destekler.</span><span class="sxs-lookup"><span data-stu-id="d6378-173">By default, the basic binding supports HTTP communication.</span></span>  
  
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
      <!-- Configure basicHttpBinding with Transport security -- >  
      <!-- mode and clientCredentialType set to None.-->  
      <binding name="Binding1">  
        <security mode="Transport">  
          <transport clientCredentialType="None"  
                     proxyCredentialType="None">  
            <extendedProtectionPolicy policyEnforcement="WhenSupported"  
                                      protectionScenario="TransportSelected">  
              <customServiceNames></customServiceNames>  
            </extendedProtectionPolicy>
          </transport> 
        </security>  
      </binding>  
    </netHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d6378-174">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d6378-174">See Also</span></span>  
 <span data-ttu-id="d6378-175"><xref:System.ServiceModel.BasicHttpSecurityMode.Transport><xref:System.ServiceModel.Configuration.HttpTransportSecurityElement></span><span class="sxs-lookup"><span data-stu-id="d6378-175"><xref:System.ServiceModel.BasicHttpSecurityMode.Transport> <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement></span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 [<span data-ttu-id="d6378-176">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="d6378-176">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="d6378-177">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="d6378-177">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="d6378-178">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d6378-178">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="d6378-179">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="d6378-179">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="d6378-180">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="d6378-180">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)

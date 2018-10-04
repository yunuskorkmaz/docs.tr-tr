---
title: '&lt;basicHttpBinding&gt; &lt;taşıma&gt;'
ms.date: 03/30/2017
ms.assetid: 4c5ba293-3d7e-47a6-b84e-e9022857b7e5
ms.openlocfilehash: f4e37281539106fef93dc4ab566d94d781c39d29
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48777727"
---
# <a name="lttransportgt-of-ltbasichttpbindinggt"></a><span data-ttu-id="264f1-102">&lt;basicHttpBinding&gt; &lt;taşıma&gt;</span><span class="sxs-lookup"><span data-stu-id="264f1-102">&lt;transport&gt; of &lt;basicHttpBinding&gt;</span></span>
<span data-ttu-id="264f1-103">HTTP taşıma için kimlik doğrulama parametrelerini denetleyen özellikleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="264f1-103">Defines properties that control authentication parameters for the HTTP transport.</span></span>  
  
 <span data-ttu-id="264f1-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="264f1-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="264f1-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="264f1-105">\<bindings></span></span>  
<span data-ttu-id="264f1-106">\<basicHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="264f1-106">\<basicHttpBinding></span></span>  
<span data-ttu-id="264f1-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="264f1-107">\<binding></span></span>  
<span data-ttu-id="264f1-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="264f1-108">\<security></span></span>  
<span data-ttu-id="264f1-109">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="264f1-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="264f1-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="264f1-110">Syntax</span></span>  
  
```xml  
<basicHttpBinding>  
    <binding>  
        <security  
        mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">  
            <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"  
             proxyCredentialType="None|Basic|Digest|Ntlm|Windows" realm="string" >  
                <extendedProtectionPolicy  
                     policyEnforcement="Never|WhenSupported|Always"  
                     protectionScenario="TransportSelected|TrustedProxy">  
                    <customServiceNames></customServiceNames>  
                        </extendedProtectionPolicy>  
            </transport>  
        </security>  
    </binding>  
</basicHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="264f1-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="264f1-111">Attributes and Elements</span></span>  
 <span data-ttu-id="264f1-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="264f1-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="264f1-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="264f1-113">Attributes</span></span>  
  
|<span data-ttu-id="264f1-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="264f1-114">Attribute</span></span>|<span data-ttu-id="264f1-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="264f1-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="264f1-116">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="264f1-116">clientCredentialType</span></span>|<span data-ttu-id="264f1-117">-HTTP kimlik doğrulaması kullanarak istemci kimlik doğrulaması yapılırken kullanılacak kimlik bilgisi türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="264f1-117">-   Specifies the type of credential to be used when performing client authentication using HTTP authentication.</span></span>  <span data-ttu-id="264f1-118">Varsayılan, `None` değeridir.</span><span class="sxs-lookup"><span data-stu-id="264f1-118">The default is `None`.</span></span> <span data-ttu-id="264f1-119">Bu öznitelik türünde <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="264f1-119">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|<span data-ttu-id="264f1-120">proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="264f1-120">proxyCredentialType</span></span>|<span data-ttu-id="264f1-121">-Gelen istemci kimlik doğrulaması Ara sunucu kullanarak HTTP üzerinden bir etki alanı içinde gerçekleştirirken kullanılacak kimlik bilgisi türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="264f1-121">-   Specifies the type of credential to be used when performing client authentication from within a domain using a proxy over HTTP.</span></span> <span data-ttu-id="264f1-122">Bu özniteliği yalnızca uygun olduğunda, `mode` üst öğenin özniteliğini `security` öğesi `Transport` veya `TransportCredentialsOnly`.</span><span class="sxs-lookup"><span data-stu-id="264f1-122">This attribute is applicable only when the `mode` attribute of the parent `security` element is `Transport` or `TransportCredentialsOnly`.</span></span> <span data-ttu-id="264f1-123">Bu öznitelik türünde <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="264f1-123">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|<span data-ttu-id="264f1-124">Bölge</span><span class="sxs-lookup"><span data-stu-id="264f1-124">realm</span></span>|<span data-ttu-id="264f1-125">HTTP kimlik doğrulama şemasının Özet veya temel kimlik doğrulaması için kullanılan ölge belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="264f1-125">A string that specifies the realm that is used by the HTTP authentication scheme for digest or basic authentication.</span></span> <span data-ttu-id="264f1-126">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="264f1-126">The default is an empty string.</span></span>|  
|<span data-ttu-id="264f1-127">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="264f1-127">policyEnforcement</span></span>|<span data-ttu-id="264f1-128">Bu sabit listesi ne zaman belirtir <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> zorlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="264f1-128">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="264f1-129">1.  Hiçbir zaman – hiçbir zaman ilkenin uygulanıp (genişletilmiş koruma devre dışı).</span><span class="sxs-lookup"><span data-stu-id="264f1-129">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="264f1-130">2.  Yalnızca istemci genişletilmiş koruma destekliyorsa WhenSupported – ilke zorunlu tutulur.</span><span class="sxs-lookup"><span data-stu-id="264f1-130">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="264f1-131">3.  Her zaman – ilke her zaman uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="264f1-131">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="264f1-132">Genişletilmiş Koruma desteklemeyen istemciler kimlik doğrulaması başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="264f1-132">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
|<span data-ttu-id="264f1-133">protectionScenario</span><span class="sxs-lookup"><span data-stu-id="264f1-133">protectionScenario</span></span>|<span data-ttu-id="264f1-134">Bu numaralandırma, ilke tarafından zorunlu koruma senaryosu belirtir.</span><span class="sxs-lookup"><span data-stu-id="264f1-134">This enumeration specifies the protection scenario enforced by the policy.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="264f1-135">clientCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="264f1-135">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="264f1-136">Değer</span><span class="sxs-lookup"><span data-stu-id="264f1-136">Value</span></span>|<span data-ttu-id="264f1-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="264f1-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="264f1-138">Yok.</span><span class="sxs-lookup"><span data-stu-id="264f1-138">None</span></span>|<span data-ttu-id="264f1-139">İleti aktarımı sırasında sağlanmaz.</span><span class="sxs-lookup"><span data-stu-id="264f1-139">Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="264f1-140">Temel</span><span class="sxs-lookup"><span data-stu-id="264f1-140">Basic</span></span>|<span data-ttu-id="264f1-141">Temel kimlik doğrulaması belirtir.</span><span class="sxs-lookup"><span data-stu-id="264f1-141">Specifies basic authentication.</span></span>|  
|<span data-ttu-id="264f1-142">Özet</span><span class="sxs-lookup"><span data-stu-id="264f1-142">Digest</span></span>|<span data-ttu-id="264f1-143">Özet kimlik doğrulaması belirtir.</span><span class="sxs-lookup"><span data-stu-id="264f1-143">Specifies digest authentication.</span></span>|  
|<span data-ttu-id="264f1-144">NTLM</span><span class="sxs-lookup"><span data-stu-id="264f1-144">Ntlm</span></span>|<span data-ttu-id="264f1-145">Mümkün olduğunda ve Windows kimlik doğrulaması başarısız olursa, NTLM kimlik doğrulaması belirtir.</span><span class="sxs-lookup"><span data-stu-id="264f1-145">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="264f1-146">Windows</span><span class="sxs-lookup"><span data-stu-id="264f1-146">Windows</span></span>|<span data-ttu-id="264f1-147">Windows tümleşik kimlik doğrulaması belirtir.</span><span class="sxs-lookup"><span data-stu-id="264f1-147">Specifies Windows integrated authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="264f1-148">proxyCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="264f1-148">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="264f1-149">Değer</span><span class="sxs-lookup"><span data-stu-id="264f1-149">Value</span></span>|<span data-ttu-id="264f1-150">Açıklama</span><span class="sxs-lookup"><span data-stu-id="264f1-150">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="264f1-151">Yok.</span><span class="sxs-lookup"><span data-stu-id="264f1-151">None</span></span>|<span data-ttu-id="264f1-152">-Sıradaki iletiler, aktarım sırasında sağlanmaz.</span><span class="sxs-lookup"><span data-stu-id="264f1-152">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="264f1-153">Temel</span><span class="sxs-lookup"><span data-stu-id="264f1-153">Basic</span></span>|<span data-ttu-id="264f1-154">RFC 2617 – HTTP kimlik doğrulaması tarafından tanımlandığı gibi temel kimlik doğrulaması belirtir: temel ve Özet kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="264f1-154">Specifies basic authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="264f1-155">Özet</span><span class="sxs-lookup"><span data-stu-id="264f1-155">Digest</span></span>|<span data-ttu-id="264f1-156">Özet kimlik doğrulaması RFC 2617 – HTTP kimlik doğrulaması tarafından tanımlanan belirtir: temel ve Özet kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="264f1-156">Specifies digest authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="264f1-157">NTLM</span><span class="sxs-lookup"><span data-stu-id="264f1-157">Ntlm</span></span>|<span data-ttu-id="264f1-158">Mümkün olduğunda ve Windows kimlik doğrulaması başarısız olursa, NTLM kimlik doğrulaması belirtir.</span><span class="sxs-lookup"><span data-stu-id="264f1-158">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="264f1-159">Windows</span><span class="sxs-lookup"><span data-stu-id="264f1-159">Windows</span></span>|<span data-ttu-id="264f1-160">Windows tümleşik kimlik doğrulaması belirtir.</span><span class="sxs-lookup"><span data-stu-id="264f1-160">Specifies Windows integrated authentication.</span></span>|  
|<span data-ttu-id="264f1-161">Sertifika</span><span class="sxs-lookup"><span data-stu-id="264f1-161">Certificate</span></span>|<span data-ttu-id="264f1-162">Bir sertifika kullanarak bir istemci kimlik doğrulaması gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="264f1-162">Performs client authentication using a certificate.</span></span> <span data-ttu-id="264f1-163">Bu seçenek yalnızca çalışır `Mode` üst öğenin özniteliğini `security` öğe taşıma imkanı kullanılarak ayarlanır ve TransportCredentialOnly için ayarlanmışsa çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="264f1-163">This option works only if the `Mode` attribute of the parent `security` element is set to Transport, and will not work if it is set to TransportCredentialOnly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="264f1-164">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="264f1-164">Child Elements</span></span>  
 <span data-ttu-id="264f1-165">Yok.</span><span class="sxs-lookup"><span data-stu-id="264f1-165">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="264f1-166">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="264f1-166">Parent Elements</span></span>  
  
|<span data-ttu-id="264f1-167">Öğe</span><span class="sxs-lookup"><span data-stu-id="264f1-167">Element</span></span>|<span data-ttu-id="264f1-168">Açıklama</span><span class="sxs-lookup"><span data-stu-id="264f1-168">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="264f1-169">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="264f1-169">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|<span data-ttu-id="264f1-170">İçin güvenlik özelliklerini tanımlar [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="264f1-170">Defines the security capabilities for the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="264f1-171">Örnek</span><span class="sxs-lookup"><span data-stu-id="264f1-171">Example</span></span>  
 <span data-ttu-id="264f1-172">Aşağıdaki örnek, basit bağlama ile SSL Aktarım güvenliği kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="264f1-172">The following example demonstrates the use of SSL transport security with the basic binding.</span></span> <span data-ttu-id="264f1-173">Varsayılan olarak, HTTP iletişimi için temel bağlamayı destekler.</span><span class="sxs-lookup"><span data-stu-id="264f1-173">By default, the basic binding supports HTTP communication.</span></span>  
  
```xml  
<system.serviceModel>  
   <services>  
      <service   
          type="Microsoft.ServiceModel.Samples.CalculatorService"  
          behaviorConfiguration="CalculatorServiceBehavior">  
         <endpoint address=""  
               binding="basicHttpBinding"  
               bindingConfiguration="Binding1"   
               contract="Microsoft.ServiceModel.Samples.ICalculator" />  
      </service>  
   </services>  
    <bindings>  
        <basicHttpBinding>  
        <!-- Configure basicHttpBinding with Transport security -- >  
        <!-- mode and clientCredentialType set to None.-->  
           <binding name="Binding1">  
               <security mode="Transport">  
                   <transport clientCredentialType="None"  
                              proxyCredentialType="None">  
                       <extendedProtectionPolicy  
                          policyEnforcement="WhenSupported"  
                          protectionScenario="TransportSelected">  
                    <customServiceNames></customServiceNames>  
                       </extendedProtectionPolicy>  
               </security>  
           </binding>  
        </basicHttpBinding>  
    </bindings>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a><span data-ttu-id="264f1-174">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="264f1-174">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.BasicHttpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 [<span data-ttu-id="264f1-175">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="264f1-175">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="264f1-176">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="264f1-176">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="264f1-177">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="264f1-177">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="264f1-178">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="264f1-178">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="264f1-179">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="264f1-179">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)

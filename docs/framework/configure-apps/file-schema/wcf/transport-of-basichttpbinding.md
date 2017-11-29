---
title: "&lt;basicHttpBinding&gt; &lt;taşıma&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4c5ba293-3d7e-47a6-b84e-e9022857b7e5
caps.latest.revision: "18"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a69be01146e71e71ba7e901de288d84c533b1e1c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="lttransportgt-of-ltbasichttpbindinggt"></a><span data-ttu-id="3e3c7-102">&lt;basicHttpBinding&gt; &lt;taşıma&gt;</span><span class="sxs-lookup"><span data-stu-id="3e3c7-102">&lt;transport&gt; of &lt;basicHttpBinding&gt;</span></span>
<span data-ttu-id="3e3c7-103">HTTP taşıma için kimlik doğrulama parametrelerini denetleyen özellikler tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3e3c7-103">Defines properties that control authentication parameters for the HTTP transport.</span></span>  
  
 <span data-ttu-id="3e3c7-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="3e3c7-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="3e3c7-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="3e3c7-105">\<bindings></span></span>  
<span data-ttu-id="3e3c7-106">\<basicHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="3e3c7-106">\<basicHttpBinding></span></span>  
<span data-ttu-id="3e3c7-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="3e3c7-107">\<binding></span></span>  
<span data-ttu-id="3e3c7-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="3e3c7-108">\<security></span></span>  
<span data-ttu-id="3e3c7-109">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="3e3c7-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e3c7-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3e3c7-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3e3c7-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3e3c7-111">Attributes and Elements</span></span>  
 <span data-ttu-id="3e3c7-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3e3c7-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3e3c7-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3e3c7-113">Attributes</span></span>  
  
|<span data-ttu-id="3e3c7-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3e3c7-114">Attribute</span></span>|<span data-ttu-id="3e3c7-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3e3c7-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3e3c7-116">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="3e3c7-116">clientCredentialType</span></span>|<span data-ttu-id="3e3c7-117">-HTTP kimlik doğrulaması kullanarak istemci kimlik doğrulaması yapılırken kullanılacak kimlik bilgileri türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e3c7-117">-   Specifies the type of credential to be used when performing client authentication using HTTP authentication.</span></span>  <span data-ttu-id="3e3c7-118">Varsayılan, `None` değeridir.</span><span class="sxs-lookup"><span data-stu-id="3e3c7-118">The default is `None`.</span></span> <span data-ttu-id="3e3c7-119">Bu öznitelik türünde <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="3e3c7-119">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|<span data-ttu-id="3e3c7-120">proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="3e3c7-120">proxyCredentialType</span></span>|<span data-ttu-id="3e3c7-121">-İstemci kimlik doğrulamasını bir proxy sunucu HTTP üzerinden kullanarak bir etki alanı içinde gerçekleştirirken kullanılacak kimlik bilgileri türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e3c7-121">-   Specifies the type of credential to be used when performing client authentication from within a domain using a proxy over HTTP.</span></span> <span data-ttu-id="3e3c7-122">Bu öznitelik yalnızca uygun olduğunda olan `mode` üst öznitelik `security` öğesi `Transport` veya `TransportCredentialsOnly`.</span><span class="sxs-lookup"><span data-stu-id="3e3c7-122">This attribute is applicable only when the `mode` attribute of the parent `security` element is `Transport` or `TransportCredentialsOnly`.</span></span> <span data-ttu-id="3e3c7-123">Bu öznitelik türünde <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="3e3c7-123">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|<span data-ttu-id="3e3c7-124">Bölge</span><span class="sxs-lookup"><span data-stu-id="3e3c7-124">realm</span></span>|<span data-ttu-id="3e3c7-125">HTTP kimlik doğrulama şeması tarafından Özet veya temel kimlik doğrulaması için kullanılan bölge belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="3e3c7-125">A string that specifies the realm that is used by the HTTP authentication scheme for digest or basic authentication.</span></span> <span data-ttu-id="3e3c7-126">Varsayılan boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="3e3c7-126">The default is an empty string.</span></span>|  
|<span data-ttu-id="3e3c7-127">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="3e3c7-127">policyEnforcement</span></span>|<span data-ttu-id="3e3c7-128">Bu numaralandırma ne zaman belirtir <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> zorunlu tutulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3e3c7-128">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="3e3c7-129">1.  Hiçbir zaman – ilke hiçbir zaman zorlanır (genişletilmiş koruma devre dışı).</span><span class="sxs-lookup"><span data-stu-id="3e3c7-129">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="3e3c7-130">2.  Yalnızca istemci genişletilmiş koruma destekliyorsa WhenSupported – ilke uygulanır.</span><span class="sxs-lookup"><span data-stu-id="3e3c7-130">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="3e3c7-131">3.  Her zaman – ilke her zaman zorlanır.</span><span class="sxs-lookup"><span data-stu-id="3e3c7-131">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="3e3c7-132">Genişletilmiş Koruma desteklemeyen istemcilerin kimliğini doğrulamak başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="3e3c7-132">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
|<span data-ttu-id="3e3c7-133">protectionScenario</span><span class="sxs-lookup"><span data-stu-id="3e3c7-133">protectionScenario</span></span>|<span data-ttu-id="3e3c7-134">Bu numaralandırma ilke tarafından zorlanan koruma senaryosu belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e3c7-134">This enumeration specifies the protection scenario enforced by the policy.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="3e3c7-135">clientCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="3e3c7-135">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="3e3c7-136">Değer</span><span class="sxs-lookup"><span data-stu-id="3e3c7-136">Value</span></span>|<span data-ttu-id="3e3c7-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3e3c7-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3e3c7-138">Yok.</span><span class="sxs-lookup"><span data-stu-id="3e3c7-138">None</span></span>|<span data-ttu-id="3e3c7-139">İleti aktarımı sırasında sağlanmaz.</span><span class="sxs-lookup"><span data-stu-id="3e3c7-139">Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="3e3c7-140">Temel</span><span class="sxs-lookup"><span data-stu-id="3e3c7-140">Basic</span></span>|<span data-ttu-id="3e3c7-141">Temel kimlik doğrulaması belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e3c7-141">Specifies basic authentication.</span></span>|  
|<span data-ttu-id="3e3c7-142">Özet</span><span class="sxs-lookup"><span data-stu-id="3e3c7-142">Digest</span></span>|<span data-ttu-id="3e3c7-143">Özet kimlik doğrulaması belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e3c7-143">Specifies digest authentication.</span></span>|  
|<span data-ttu-id="3e3c7-144">NTLM</span><span class="sxs-lookup"><span data-stu-id="3e3c7-144">Ntlm</span></span>|<span data-ttu-id="3e3c7-145">NTLM kimlik doğrulaması, mümkün olduğunda ve Windows kimlik doğrulaması başarısız olursa belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e3c7-145">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="3e3c7-146">Windows</span><span class="sxs-lookup"><span data-stu-id="3e3c7-146">Windows</span></span>|<span data-ttu-id="3e3c7-147">Windows tümleşik kimlik doğrulaması belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e3c7-147">Specifies Windows integrated authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="3e3c7-148">proxyCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="3e3c7-148">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="3e3c7-149">Değer</span><span class="sxs-lookup"><span data-stu-id="3e3c7-149">Value</span></span>|<span data-ttu-id="3e3c7-150">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3e3c7-150">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3e3c7-151">Yok.</span><span class="sxs-lookup"><span data-stu-id="3e3c7-151">None</span></span>|<span data-ttu-id="3e3c7-152">-Aktarım sırasında iletileri güvenli değil.</span><span class="sxs-lookup"><span data-stu-id="3e3c7-152">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="3e3c7-153">Temel</span><span class="sxs-lookup"><span data-stu-id="3e3c7-153">Basic</span></span>|<span data-ttu-id="3e3c7-154">Temel kimlik doğrulaması RFC 2617 – HTTP kimlik doğrulaması tarafından tanımlandığı şekilde belirtir: temel ve Özet kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="3e3c7-154">Specifies basic authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="3e3c7-155">Özet</span><span class="sxs-lookup"><span data-stu-id="3e3c7-155">Digest</span></span>|<span data-ttu-id="3e3c7-156">Özet kimlik doğrulaması RFC 2617 – HTTP kimlik doğrulaması tarafından tanımlandığı şekilde belirtir: temel ve Özet kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="3e3c7-156">Specifies digest authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="3e3c7-157">NTLM</span><span class="sxs-lookup"><span data-stu-id="3e3c7-157">Ntlm</span></span>|<span data-ttu-id="3e3c7-158">NTLM kimlik doğrulaması, mümkün olduğunda ve Windows kimlik doğrulaması başarısız olursa belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e3c7-158">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="3e3c7-159">Windows</span><span class="sxs-lookup"><span data-stu-id="3e3c7-159">Windows</span></span>|<span data-ttu-id="3e3c7-160">Windows tümleşik kimlik doğrulaması belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e3c7-160">Specifies Windows integrated authentication.</span></span>|  
|<span data-ttu-id="3e3c7-161">Sertifika</span><span class="sxs-lookup"><span data-stu-id="3e3c7-161">Certificate</span></span>|<span data-ttu-id="3e3c7-162">Bir sertifika kullanarak istemci kimlik doğrulaması gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="3e3c7-162">Performs client authentication using a certificate.</span></span> <span data-ttu-id="3e3c7-163">Bu seçenek yalnızca çalışır `Mode` üst öznitelik `security` öğesi taşıma için ayarlanır ve TransportCredentialOnly için ayarlarsanız çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="3e3c7-163">This option works only if the `Mode` attribute of the parent `security` element is set to Transport, and will not work if it is set to TransportCredentialOnly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3e3c7-164">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3e3c7-164">Child Elements</span></span>  
 <span data-ttu-id="3e3c7-165">Yok.</span><span class="sxs-lookup"><span data-stu-id="3e3c7-165">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3e3c7-166">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3e3c7-166">Parent Elements</span></span>  
  
|<span data-ttu-id="3e3c7-167">Öğe</span><span class="sxs-lookup"><span data-stu-id="3e3c7-167">Element</span></span>|<span data-ttu-id="3e3c7-168">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3e3c7-168">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3e3c7-169">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="3e3c7-169">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|<span data-ttu-id="3e3c7-170">Güvenlik özellikleri için tanımlar [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="3e3c7-170">Defines the security capabilities for the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3e3c7-171">Örnek</span><span class="sxs-lookup"><span data-stu-id="3e3c7-171">Example</span></span>  
 <span data-ttu-id="3e3c7-172">Aşağıdaki örnek, temel bağlama ile SSL taşıma güvenliği kullanımını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="3e3c7-172">The following example demonstrates the use of SSL transport security with the basic binding.</span></span> <span data-ttu-id="3e3c7-173">Varsayılan olarak, temel bağlama HTTP iletişimi destekler.</span><span class="sxs-lookup"><span data-stu-id="3e3c7-173">By default, the basic binding supports HTTP communication.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3e3c7-174">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3e3c7-174">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.BasicHttpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 [<span data-ttu-id="3e3c7-175">Hizmetler ve istemcileri güvenli hale getirme</span><span class="sxs-lookup"><span data-stu-id="3e3c7-175">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="3e3c7-176">Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="3e3c7-176">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="3e3c7-177">Sistem tarafından sağlanan bağlamaları yapılandırma</span><span class="sxs-lookup"><span data-stu-id="3e3c7-177">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="3e3c7-178">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="3e3c7-178">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="3e3c7-179">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="3e3c7-179">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)

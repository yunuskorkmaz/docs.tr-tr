---
description: 'Hakkında daha fazla bilgi <transport> edinin: <basicHttpBinding>'
title: <transport> / <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 4c5ba293-3d7e-47a6-b84e-e9022857b7e5
ms.openlocfilehash: 6148bbd5fa234adb51266714fff818e72f0abf40
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99773543"
---
# <a name="transport-of-basichttpbinding"></a><span data-ttu-id="2f034-103">\<transport> / \<basicHttpBinding></span><span class="sxs-lookup"><span data-stu-id="2f034-103">\<transport> of \<basicHttpBinding></span></span>

<span data-ttu-id="2f034-104">HTTP taşıması için kimlik doğrulama parametrelerini denetleyen özellikleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2f034-104">Defines properties that control authentication parameters for the HTTP transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<basicHttpBinding>**](basichttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-basichttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="2f034-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="2f034-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2f034-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2f034-106">Attributes and Elements</span></span>  

 <span data-ttu-id="2f034-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2f034-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2f034-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2f034-108">Attributes</span></span>  
  
|<span data-ttu-id="2f034-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2f034-109">Attribute</span></span>|<span data-ttu-id="2f034-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2f034-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2f034-111">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="2f034-111">clientCredentialType</span></span>|<span data-ttu-id="2f034-112">-HTTP kimlik doğrulaması kullanarak istemci kimlik doğrulaması gerçekleştirirken kullanılacak kimlik bilgisinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="2f034-112">-   Specifies the type of credential to be used when performing client authentication using HTTP authentication.</span></span>  <span data-ttu-id="2f034-113">Varsayılan değer: `None`.</span><span class="sxs-lookup"><span data-stu-id="2f034-113">The default is `None`.</span></span> <span data-ttu-id="2f034-114">Bu öznitelik türü <xref:System.ServiceModel.HttpClientCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="2f034-114">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|<span data-ttu-id="2f034-115">proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="2f034-115">proxyCredentialType</span></span>|<span data-ttu-id="2f034-116">-HTTP üzerinden proxy kullanan bir etki alanı içinden istemci kimlik doğrulaması gerçekleştirirken kullanılacak kimlik bilgisinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="2f034-116">-   Specifies the type of credential to be used when performing client authentication from within a domain using a proxy over HTTP.</span></span> <span data-ttu-id="2f034-117">Bu öznitelik yalnızca `mode` üst öğenin özniteliği veya olduğunda geçerlidir `security` `Transport` `TransportCredentialsOnly` .</span><span class="sxs-lookup"><span data-stu-id="2f034-117">This attribute is applicable only when the `mode` attribute of the parent `security` element is `Transport` or `TransportCredentialsOnly`.</span></span> <span data-ttu-id="2f034-118">Bu öznitelik türü <xref:System.ServiceModel.HttpProxyCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="2f034-118">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|<span data-ttu-id="2f034-119">bölgesindeki</span><span class="sxs-lookup"><span data-stu-id="2f034-119">realm</span></span>|<span data-ttu-id="2f034-120">Özet veya temel kimlik doğrulaması için HTTP kimlik doğrulama düzeni tarafından kullanılan bölgeyi belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="2f034-120">A string that specifies the realm that is used by the HTTP authentication scheme for digest or basic authentication.</span></span> <span data-ttu-id="2f034-121">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="2f034-121">The default is an empty string.</span></span>|  
|<span data-ttu-id="2f034-122">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="2f034-122">policyEnforcement</span></span>|<span data-ttu-id="2f034-123">Bu numaralandırma, ne zaman <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> uygulanacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2f034-123">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="2f034-124">1. hiçbir süre – ilke hiçbir şekilde zorlanmaz (genişletilmiş koruma devre dışı bırakılır).</span><span class="sxs-lookup"><span data-stu-id="2f034-124">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="2f034-125">2. WhenSupported – ilke yalnızca istemci genişletilmiş korumayı destekliyorsa zorlanır.</span><span class="sxs-lookup"><span data-stu-id="2f034-125">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="2f034-126">3. her zaman – ilke her zaman zorlanır.</span><span class="sxs-lookup"><span data-stu-id="2f034-126">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="2f034-127">Genişletilmiş korumayı desteklemeyen istemciler kimlik doğrulaması yapamaz.</span><span class="sxs-lookup"><span data-stu-id="2f034-127">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
|<span data-ttu-id="2f034-128">protectionScenario</span><span class="sxs-lookup"><span data-stu-id="2f034-128">protectionScenario</span></span>|<span data-ttu-id="2f034-129">Bu numaralandırma, ilke tarafından zorlanan koruma senaryosunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="2f034-129">This enumeration specifies the protection scenario enforced by the policy.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="2f034-130">clientCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="2f034-130">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="2f034-131">Değer</span><span class="sxs-lookup"><span data-stu-id="2f034-131">Value</span></span>|<span data-ttu-id="2f034-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2f034-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2f034-133">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="2f034-133">None</span></span>|<span data-ttu-id="2f034-134">Aktarım sırasında iletiler güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="2f034-134">Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="2f034-135">Temel</span><span class="sxs-lookup"><span data-stu-id="2f034-135">Basic</span></span>|<span data-ttu-id="2f034-136">Temel kimlik doğrulamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2f034-136">Specifies basic authentication.</span></span>|  
|<span data-ttu-id="2f034-137">Bilgisi</span><span class="sxs-lookup"><span data-stu-id="2f034-137">Digest</span></span>|<span data-ttu-id="2f034-138">Özet kimlik doğrulamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2f034-138">Specifies digest authentication.</span></span>|  
|<span data-ttu-id="2f034-139">NT</span><span class="sxs-lookup"><span data-stu-id="2f034-139">Ntlm</span></span>|<span data-ttu-id="2f034-140">Mümkünse NTLM kimlik doğrulamasını belirtir ve Windows kimlik doğrulaması başarısız olursa.</span><span class="sxs-lookup"><span data-stu-id="2f034-140">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="2f034-141">Windows</span><span class="sxs-lookup"><span data-stu-id="2f034-141">Windows</span></span>|<span data-ttu-id="2f034-142">Windows tümleşik kimlik doğrulamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2f034-142">Specifies Windows integrated authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="2f034-143">proxyCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="2f034-143">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="2f034-144">Değer</span><span class="sxs-lookup"><span data-stu-id="2f034-144">Value</span></span>|<span data-ttu-id="2f034-145">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2f034-145">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2f034-146">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="2f034-146">None</span></span>|<span data-ttu-id="2f034-147">-İletiler aktarım sırasında güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="2f034-147">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="2f034-148">Temel</span><span class="sxs-lookup"><span data-stu-id="2f034-148">Basic</span></span>|<span data-ttu-id="2f034-149">RFC 2617 – HTTP kimlik doğrulaması ile tanımlanan temel kimlik doğrulamasını belirtir: temel ve Özet kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="2f034-149">Specifies basic authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="2f034-150">Bilgisi</span><span class="sxs-lookup"><span data-stu-id="2f034-150">Digest</span></span>|<span data-ttu-id="2f034-151">RFC 2617 – HTTP kimlik doğrulaması ile tanımlanan Özet kimlik doğrulamasını belirtir: temel ve Özet kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="2f034-151">Specifies digest authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="2f034-152">NT</span><span class="sxs-lookup"><span data-stu-id="2f034-152">Ntlm</span></span>|<span data-ttu-id="2f034-153">Mümkünse NTLM kimlik doğrulamasını belirtir ve Windows kimlik doğrulaması başarısız olursa.</span><span class="sxs-lookup"><span data-stu-id="2f034-153">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="2f034-154">Windows</span><span class="sxs-lookup"><span data-stu-id="2f034-154">Windows</span></span>|<span data-ttu-id="2f034-155">Windows tümleşik kimlik doğrulamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2f034-155">Specifies Windows integrated authentication.</span></span>|  
|<span data-ttu-id="2f034-156">Sertifika</span><span class="sxs-lookup"><span data-stu-id="2f034-156">Certificate</span></span>|<span data-ttu-id="2f034-157">Bir sertifika kullanarak istemci kimlik doğrulaması gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="2f034-157">Performs client authentication using a certificate.</span></span> <span data-ttu-id="2f034-158">Bu seçenek yalnızca `Mode` üst `security` öğenin özniteliği Transport olarak ayarlandıysa ve yalnızca transportcredentialolarak ayarlandıysa işe yarar.</span><span class="sxs-lookup"><span data-stu-id="2f034-158">This option works only if the `Mode` attribute of the parent `security` element is set to Transport, and will not work if it is set to TransportCredentialOnly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2f034-159">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2f034-159">Child Elements</span></span>  

 <span data-ttu-id="2f034-160">Yok</span><span class="sxs-lookup"><span data-stu-id="2f034-160">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2f034-161">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2f034-161">Parent Elements</span></span>  
  
|<span data-ttu-id="2f034-162">Öğe</span><span class="sxs-lookup"><span data-stu-id="2f034-162">Element</span></span>|<span data-ttu-id="2f034-163">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2f034-163">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-basichttpbinding.md)|<span data-ttu-id="2f034-164">İçin güvenlik yeteneklerini tanımlar [\<basicHttpBinding>](basichttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="2f034-164">Defines the security capabilities for the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2f034-165">Örnek</span><span class="sxs-lookup"><span data-stu-id="2f034-165">Example</span></span>  

 <span data-ttu-id="2f034-166">Aşağıdaki örnek, temel bağlama ile SSL Aktarım güvenliği kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2f034-166">The following example demonstrates the use of SSL transport security with the basic binding.</span></span> <span data-ttu-id="2f034-167">Varsayılan olarak, temel bağlama HTTP iletişimini destekler.</span><span class="sxs-lookup"><span data-stu-id="2f034-167">By default, the basic binding supports HTTP communication.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2f034-168">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2f034-168">See also</span></span>

- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.BasicHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- <xref:System.ServiceModel.HttpTransportSecurity>
- [<span data-ttu-id="2f034-169">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="2f034-169">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="2f034-170">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="2f034-170">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="2f034-171">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="2f034-171">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="2f034-172">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="2f034-172">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)

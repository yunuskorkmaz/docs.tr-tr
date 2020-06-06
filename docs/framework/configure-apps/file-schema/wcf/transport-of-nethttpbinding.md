---
title: <transport> / <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: 3b180006-1661-43bf-a699-96fd3da469af
ms.openlocfilehash: b975015a9c9a0af53117900c45d917ce1c1a53e9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73732818"
---
# <a name="transport-of-nethttpbinding"></a><span data-ttu-id="174fb-102">\<transport> / \<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="174fb-102">\<transport> of \<netHttpBinding></span></span>
<span data-ttu-id="174fb-103">HTTP taşıması için kimlik doğrulama parametrelerini denetleyen özellikleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="174fb-103">Defines properties that control authentication parameters for the HTTP transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="174fb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="174fb-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="174fb-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="174fb-105">Attributes and Elements</span></span>  
 <span data-ttu-id="174fb-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="174fb-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="174fb-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="174fb-107">Attributes</span></span>  
  
|<span data-ttu-id="174fb-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="174fb-108">Attribute</span></span>|<span data-ttu-id="174fb-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="174fb-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="174fb-110">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="174fb-110">clientCredentialType</span></span>|<span data-ttu-id="174fb-111">-HTTP kimlik doğrulaması kullanarak istemci kimlik doğrulaması gerçekleştirirken kullanılacak kimlik bilgisinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="174fb-111">-   Specifies the type of credential to be used when performing client authentication using HTTP authentication.</span></span>  <span data-ttu-id="174fb-112">Varsayılan değer: `None`.</span><span class="sxs-lookup"><span data-stu-id="174fb-112">The default is `None`.</span></span> <span data-ttu-id="174fb-113">Bu öznitelik türü <xref:System.ServiceModel.HttpClientCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="174fb-113">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|<span data-ttu-id="174fb-114">proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="174fb-114">proxyCredentialType</span></span>|<span data-ttu-id="174fb-115">-HTTP üzerinden proxy kullanan bir etki alanı içinden istemci kimlik doğrulaması gerçekleştirirken kullanılacak kimlik bilgisinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="174fb-115">-   Specifies the type of credential to be used when performing client authentication from within a domain using a proxy over HTTP.</span></span> <span data-ttu-id="174fb-116">Bu öznitelik yalnızca `mode` üst öğenin özniteliği veya olduğunda geçerlidir `security` `Transport` `TransportCredentialsOnly` .</span><span class="sxs-lookup"><span data-stu-id="174fb-116">This attribute is applicable only when the `mode` attribute of the parent `security` element is `Transport` or `TransportCredentialsOnly`.</span></span> <span data-ttu-id="174fb-117">Bu öznitelik türü <xref:System.ServiceModel.HttpProxyCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="174fb-117">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|<span data-ttu-id="174fb-118">bölgesindeki</span><span class="sxs-lookup"><span data-stu-id="174fb-118">realm</span></span>|<span data-ttu-id="174fb-119">Özet veya temel kimlik doğrulaması için HTTP kimlik doğrulama düzeni tarafından kullanılan bölgeyi belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="174fb-119">A string that specifies the realm that is used by the HTTP authentication scheme for digest or basic authentication.</span></span> <span data-ttu-id="174fb-120">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="174fb-120">The default is an empty string.</span></span>|  
|<span data-ttu-id="174fb-121">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="174fb-121">policyEnforcement</span></span>|<span data-ttu-id="174fb-122">Bu numaralandırma, ne zaman <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> uygulanacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="174fb-122">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="174fb-123">1. hiçbir süre – ilke hiçbir şekilde zorlanmaz (genişletilmiş koruma devre dışı bırakılır).</span><span class="sxs-lookup"><span data-stu-id="174fb-123">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="174fb-124">2. WhenSupported – ilke yalnızca istemci genişletilmiş korumayı destekliyorsa zorlanır.</span><span class="sxs-lookup"><span data-stu-id="174fb-124">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="174fb-125">3. her zaman – ilke her zaman zorlanır.</span><span class="sxs-lookup"><span data-stu-id="174fb-125">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="174fb-126">Genişletilmiş korumayı desteklemeyen istemciler kimlik doğrulaması yapamaz.</span><span class="sxs-lookup"><span data-stu-id="174fb-126">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
|<span data-ttu-id="174fb-127">protectionScenario</span><span class="sxs-lookup"><span data-stu-id="174fb-127">protectionScenario</span></span>|<span data-ttu-id="174fb-128">Bu numaralandırma, ilke tarafından zorlanan koruma senaryosunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="174fb-128">This enumeration specifies the protection scenario enforced by the policy.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="174fb-129">clientCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="174fb-129">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="174fb-130">Değer</span><span class="sxs-lookup"><span data-stu-id="174fb-130">Value</span></span>|<span data-ttu-id="174fb-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="174fb-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="174fb-132">Yok</span><span class="sxs-lookup"><span data-stu-id="174fb-132">None</span></span>|<span data-ttu-id="174fb-133">Aktarım sırasında iletiler güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="174fb-133">Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="174fb-134">Temel</span><span class="sxs-lookup"><span data-stu-id="174fb-134">Basic</span></span>|<span data-ttu-id="174fb-135">Temel kimlik doğrulamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="174fb-135">Specifies basic authentication.</span></span>|  
|<span data-ttu-id="174fb-136">Bilgisi</span><span class="sxs-lookup"><span data-stu-id="174fb-136">Digest</span></span>|<span data-ttu-id="174fb-137">Özet kimlik doğrulamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="174fb-137">Specifies digest authentication.</span></span>|  
|<span data-ttu-id="174fb-138">NT</span><span class="sxs-lookup"><span data-stu-id="174fb-138">Ntlm</span></span>|<span data-ttu-id="174fb-139">Mümkünse NTLM kimlik doğrulamasını belirtir ve Windows kimlik doğrulaması başarısız olursa.</span><span class="sxs-lookup"><span data-stu-id="174fb-139">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="174fb-140">Windows</span><span class="sxs-lookup"><span data-stu-id="174fb-140">Windows</span></span>|<span data-ttu-id="174fb-141">Windows tümleşik kimlik doğrulamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="174fb-141">Specifies Windows integrated authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="174fb-142">proxyCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="174fb-142">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="174fb-143">Değer</span><span class="sxs-lookup"><span data-stu-id="174fb-143">Value</span></span>|<span data-ttu-id="174fb-144">Açıklama</span><span class="sxs-lookup"><span data-stu-id="174fb-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="174fb-145">Yok</span><span class="sxs-lookup"><span data-stu-id="174fb-145">None</span></span>|<span data-ttu-id="174fb-146">-İletiler aktarım sırasında güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="174fb-146">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="174fb-147">Temel</span><span class="sxs-lookup"><span data-stu-id="174fb-147">Basic</span></span>|<span data-ttu-id="174fb-148">RFC 2617 – HTTP kimlik doğrulaması ile tanımlanan temel kimlik doğrulamasını belirtir: temel ve Özet kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="174fb-148">Specifies basic authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="174fb-149">Bilgisi</span><span class="sxs-lookup"><span data-stu-id="174fb-149">Digest</span></span>|<span data-ttu-id="174fb-150">RFC 2617 – HTTP kimlik doğrulaması ile tanımlanan Özet kimlik doğrulamasını belirtir: temel ve Özet kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="174fb-150">Specifies digest authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="174fb-151">NT</span><span class="sxs-lookup"><span data-stu-id="174fb-151">Ntlm</span></span>|<span data-ttu-id="174fb-152">Mümkünse NTLM kimlik doğrulamasını belirtir ve Windows kimlik doğrulaması başarısız olursa.</span><span class="sxs-lookup"><span data-stu-id="174fb-152">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="174fb-153">Windows</span><span class="sxs-lookup"><span data-stu-id="174fb-153">Windows</span></span>|<span data-ttu-id="174fb-154">Windows tümleşik kimlik doğrulamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="174fb-154">Specifies Windows integrated authentication.</span></span>|  
|<span data-ttu-id="174fb-155">Sertifika</span><span class="sxs-lookup"><span data-stu-id="174fb-155">Certificate</span></span>|<span data-ttu-id="174fb-156">Bir sertifika kullanarak istemci kimlik doğrulaması gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="174fb-156">Performs client authentication using a certificate.</span></span> <span data-ttu-id="174fb-157">Bu seçenek yalnızca `Mode` üst `security` öğenin özniteliği Transport olarak ayarlandıysa ve yalnızca transportcredentialolarak ayarlandıysa işe yarar.</span><span class="sxs-lookup"><span data-stu-id="174fb-157">This option works only if the `Mode` attribute of the parent `security` element is set to Transport, and will not work if it is set to TransportCredentialOnly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="174fb-158">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="174fb-158">Child Elements</span></span>  
 <span data-ttu-id="174fb-159">Yok</span><span class="sxs-lookup"><span data-stu-id="174fb-159">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="174fb-160">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="174fb-160">Parent Elements</span></span>  
  
|<span data-ttu-id="174fb-161">Öğe</span><span class="sxs-lookup"><span data-stu-id="174fb-161">Element</span></span>|<span data-ttu-id="174fb-162">Açıklama</span><span class="sxs-lookup"><span data-stu-id="174fb-162">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-nethttpbinding.md)|<span data-ttu-id="174fb-163">İçin güvenlik yeteneklerini tanımlar [\<netHttpBinding>](nethttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="174fb-163">Defines the security capabilities for the [\<netHttpBinding>](nethttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="174fb-164">Örnek</span><span class="sxs-lookup"><span data-stu-id="174fb-164">Example</span></span>  
 <span data-ttu-id="174fb-165">Aşağıdaki örnek, temel bağlama ile SSL Aktarım güvenliği kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="174fb-165">The following example demonstrates the use of SSL transport security with the basic binding.</span></span> <span data-ttu-id="174fb-166">Varsayılan olarak, temel bağlama HTTP iletişimini destekler.</span><span class="sxs-lookup"><span data-stu-id="174fb-166">By default, the basic binding supports HTTP communication.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="174fb-167">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="174fb-167">See also</span></span>

- <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- <xref:System.ServiceModel.HttpTransportSecurity>
- [<span data-ttu-id="174fb-168">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="174fb-168">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="174fb-169">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="174fb-169">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="174fb-170">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="174fb-170">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="174fb-171">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="174fb-171">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)

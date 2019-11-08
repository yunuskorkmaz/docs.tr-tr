---
title: <transport> / <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: f150fb19-7de1-44af-81f4-86cad881cd05
ms.openlocfilehash: e8016eb9058f132722587368f1f8c7c03220af4a
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73732793"
---
# <a name="transport-of-webhttpbinding"></a><span data-ttu-id="25dbd-102">\<webHttpBinding \<taşıma > ></span><span class="sxs-lookup"><span data-stu-id="25dbd-102">\<transport> of \<webHttpBinding></span></span>
<span data-ttu-id="25dbd-103">HTTP isteklerini alacak şekilde yapılandırılmış bir hizmet uç noktası için aktarım düzeyi güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="25dbd-103">Defines the transport-level security settings for a service endpoint configured to receive HTTP requests.</span></span>  
  
<span data-ttu-id="25dbd-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="25dbd-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="25dbd-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="25dbd-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="25dbd-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlamaları >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="25dbd-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="25dbd-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<webHttpBinding >** ](webhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="25dbd-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<webHttpBinding>**](webhttpbinding.md)</span></span>\
<span data-ttu-id="25dbd-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="25dbd-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="25dbd-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<güvenlik >** ](security-of-webhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="25dbd-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-webhttpbinding.md)</span></span>\
<span data-ttu-id="25dbd-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<taşıma >**</span><span class="sxs-lookup"><span data-stu-id="25dbd-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25dbd-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="25dbd-111">Syntax</span></span>  
  
```xml  
<webHttpBinding>
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
</webHttpBinding>
```  
  
## <a name="type"></a><span data-ttu-id="25dbd-112">Tür</span><span class="sxs-lookup"><span data-stu-id="25dbd-112">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="25dbd-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="25dbd-113">Attributes and Elements</span></span>  
 <span data-ttu-id="25dbd-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="25dbd-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="25dbd-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="25dbd-115">Attributes</span></span>  
  
|<span data-ttu-id="25dbd-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="25dbd-116">Attribute</span></span>|<span data-ttu-id="25dbd-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="25dbd-117">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="25dbd-118">Hizmetin istemcinin kimliğini doğrulamak için kullanılan kimlik bilgisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="25dbd-118">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="25dbd-119">Bu öznitelik <xref:System.ServiceModel.HttpClientCredentialType>türündedir.</span><span class="sxs-lookup"><span data-stu-id="25dbd-119">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="25dbd-120">Bir etki alanı ara sunucusu için istemcinin kimliğini doğrulamak için kullanılan kimlik bilgisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="25dbd-120">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="25dbd-121">Bu öznitelik <xref:System.ServiceModel.HttpProxyCredentialType>türündedir.</span><span class="sxs-lookup"><span data-stu-id="25dbd-121">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="25dbd-122">Özet veya temel kimlik doğrulaması için kimlik doğrulama bölgesini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="25dbd-122">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="25dbd-123">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="25dbd-123">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="25dbd-124">Kimlik doğrulama bölgesi, kimlik doğrulamasını gerçekleştiren konağın en azından adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="25dbd-124">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="25dbd-125">Ayrıca, erişimi olan bir kullanıcı koleksiyonu da belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="25dbd-125">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="25dbd-126">Kullanıcı, birkaç olası Kullanıcı adı ve parolanın kullanılabileceğini belirlemek için kimlik doğrulama bölgesini sorgulayabilir.</span><span class="sxs-lookup"><span data-stu-id="25dbd-126">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|  
|`policyEnforcement`|<span data-ttu-id="25dbd-127">Bu sabit listesi <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> ne zaman uygulanacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="25dbd-127">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="25dbd-128">1. hiçbir süre – ilke hiçbir şekilde zorlanmaz (genişletilmiş koruma devre dışı bırakılır).</span><span class="sxs-lookup"><span data-stu-id="25dbd-128">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="25dbd-129">2. WhenSupported – ilke yalnızca istemci genişletilmiş korumayı destekliyorsa zorlanır.</span><span class="sxs-lookup"><span data-stu-id="25dbd-129">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="25dbd-130">3. her zaman – ilke her zaman zorlanır.</span><span class="sxs-lookup"><span data-stu-id="25dbd-130">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="25dbd-131">Genişletilmiş korumayı desteklemeyen istemciler kimlik doğrulaması yapamaz.</span><span class="sxs-lookup"><span data-stu-id="25dbd-131">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="25dbd-132">clientCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="25dbd-132">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="25dbd-133">Değer</span><span class="sxs-lookup"><span data-stu-id="25dbd-133">Value</span></span>|<span data-ttu-id="25dbd-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="25dbd-134">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="25dbd-135">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="25dbd-135">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="25dbd-136">Temel kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="25dbd-136">Uses basic authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="25dbd-137">İstemcinin kimliğini doğrulamak için X. 509.440 sertifikalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="25dbd-137">Uses X.509 certificates to authenticate the client.</span></span>|  
|`Digest`|<span data-ttu-id="25dbd-138">Özet kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="25dbd-138">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="25dbd-139">Windows etki alanı ile geri dönüş olarak NTLM kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="25dbd-139">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="25dbd-140">Tümleşik Windows kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="25dbd-140">Uses integrated Windows authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="25dbd-141">proxyCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="25dbd-141">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="25dbd-142">Değer</span><span class="sxs-lookup"><span data-stu-id="25dbd-142">Value</span></span>|<span data-ttu-id="25dbd-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="25dbd-143">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="25dbd-144">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="25dbd-144">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="25dbd-145">Temel kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="25dbd-145">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="25dbd-146">Özet kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="25dbd-146">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="25dbd-147">Windows etki alanı ile geri dönüş olarak NTLM kullanır.</span><span class="sxs-lookup"><span data-stu-id="25dbd-147">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="25dbd-148">Tümleşik Windows kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="25dbd-148">Uses integrated Windows authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="25dbd-149">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="25dbd-149">Child Elements</span></span>  
 <span data-ttu-id="25dbd-150">Yok.</span><span class="sxs-lookup"><span data-stu-id="25dbd-150">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="25dbd-151">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="25dbd-151">Parent Elements</span></span>  
  
|<span data-ttu-id="25dbd-152">Öğe</span><span class="sxs-lookup"><span data-stu-id="25dbd-152">Element</span></span>|<span data-ttu-id="25dbd-153">Açıklama</span><span class="sxs-lookup"><span data-stu-id="25dbd-153">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="25dbd-154">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="25dbd-154">\<security></span></span>](security-of-webhttpbinding.md)|<span data-ttu-id="25dbd-155">[\<wsHttpBinding >](wshttpbinding.md) öğesinin güvenlik yeteneklerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="25dbd-155">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="25dbd-156">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="25dbd-156">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.WebHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WebHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [<span data-ttu-id="25dbd-157">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="25dbd-157">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="25dbd-158">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="25dbd-158">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="25dbd-159">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="25dbd-159">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="25dbd-160">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="25dbd-160">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="25dbd-161">\< bağlama ></span><span class="sxs-lookup"><span data-stu-id="25dbd-161">\<binding></span></span>](bindings.md)
- [<span data-ttu-id="25dbd-162">WCF Web HTTP Programlama Modeli</span><span class="sxs-lookup"><span data-stu-id="25dbd-162">WCF Web HTTP Programming Model</span></span>](../../../wcf/feature-details/wcf-web-http-programming-model.md)

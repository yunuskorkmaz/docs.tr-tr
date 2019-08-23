---
title: <transport> / <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: f150fb19-7de1-44af-81f4-86cad881cd05
ms.openlocfilehash: f78add5397644dc40bfd22f10bd84aa5c5eb29e6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923207"
---
# <a name="transport-of-webhttpbinding"></a><span data-ttu-id="1ec74-102">\<\<WebHttpBinding > taşıma ></span><span class="sxs-lookup"><span data-stu-id="1ec74-102">\<transport> of \<webHttpBinding></span></span>
<span data-ttu-id="1ec74-103">HTTP isteklerini alacak şekilde yapılandırılmış bir hizmet uç noktası için aktarım düzeyi güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1ec74-103">Defines the transport-level security settings for a service endpoint configured to receive HTTP requests.</span></span>  
  
 <span data-ttu-id="1ec74-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1ec74-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="1ec74-105">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="1ec74-105">\<bindings></span></span>  
<span data-ttu-id="1ec74-106">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="1ec74-106">\<webHttpBinding></span></span>  
<span data-ttu-id="1ec74-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="1ec74-107">\<binding></span></span>  
<span data-ttu-id="1ec74-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="1ec74-108">\<security></span></span>  
<span data-ttu-id="1ec74-109">\<Taşıma ></span><span class="sxs-lookup"><span data-stu-id="1ec74-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ec74-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1ec74-110">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="1ec74-111">Tür</span><span class="sxs-lookup"><span data-stu-id="1ec74-111">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1ec74-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1ec74-112">Attributes and Elements</span></span>  
 <span data-ttu-id="1ec74-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1ec74-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1ec74-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1ec74-114">Attributes</span></span>  
  
|<span data-ttu-id="1ec74-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1ec74-115">Attribute</span></span>|<span data-ttu-id="1ec74-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1ec74-116">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="1ec74-117">Hizmetin istemcinin kimliğini doğrulamak için kullanılan kimlik bilgisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1ec74-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="1ec74-118">Bu öznitelik türü <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="1ec74-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="1ec74-119">Bir etki alanı ara sunucusu için istemcinin kimliğini doğrulamak için kullanılan kimlik bilgisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1ec74-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="1ec74-120">Bu öznitelik türü <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="1ec74-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="1ec74-121">Özet veya temel kimlik doğrulaması için kimlik doğrulama bölgesini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="1ec74-121">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="1ec74-122">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="1ec74-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="1ec74-123">Kimlik doğrulama bölgesi, kimlik doğrulamasını gerçekleştiren konağın en azından adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1ec74-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="1ec74-124">Ayrıca, erişimi olan bir kullanıcı koleksiyonu da belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="1ec74-124">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="1ec74-125">Kullanıcı, birkaç olası Kullanıcı adı ve parolanın kullanılabileceğini belirlemek için kimlik doğrulama bölgesini sorgulayabilir.</span><span class="sxs-lookup"><span data-stu-id="1ec74-125">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|  
|`policyEnforcement`|<span data-ttu-id="1ec74-126">Bu numaralandırma, <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> ne zaman uygulanacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1ec74-126">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="1ec74-127">1.  Hiçbir süre – ilke hiçbir şekilde zorlanmaz (genişletilmiş koruma devre dışı bırakılır).</span><span class="sxs-lookup"><span data-stu-id="1ec74-127">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="1ec74-128">2.  WhenSupported – ilke yalnızca istemci genişletilmiş korumayı destekliyorsa zorlanır.</span><span class="sxs-lookup"><span data-stu-id="1ec74-128">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="1ec74-129">3.  Her zaman – ilke her zaman zorlanır.</span><span class="sxs-lookup"><span data-stu-id="1ec74-129">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="1ec74-130">Genişletilmiş korumayı desteklemeyen istemciler kimlik doğrulaması yapamaz.</span><span class="sxs-lookup"><span data-stu-id="1ec74-130">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="1ec74-131">clientCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="1ec74-131">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="1ec74-132">Değer</span><span class="sxs-lookup"><span data-stu-id="1ec74-132">Value</span></span>|<span data-ttu-id="1ec74-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1ec74-133">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="1ec74-134">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="1ec74-134">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="1ec74-135">Temel kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="1ec74-135">Uses basic authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="1ec74-136">İstemcinin kimliğini doğrulamak için X. 509.440 sertifikalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="1ec74-136">Uses X.509 certificates to authenticate the client.</span></span>|  
|`Digest`|<span data-ttu-id="1ec74-137">Özet kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="1ec74-137">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="1ec74-138">Windows etki alanı ile geri dönüş olarak NTLM kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="1ec74-138">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="1ec74-139">Tümleşik Windows kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="1ec74-139">Uses integrated Windows authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="1ec74-140">proxyCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="1ec74-140">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="1ec74-141">Değer</span><span class="sxs-lookup"><span data-stu-id="1ec74-141">Value</span></span>|<span data-ttu-id="1ec74-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1ec74-142">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="1ec74-143">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="1ec74-143">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="1ec74-144">Temel kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="1ec74-144">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="1ec74-145">Özet kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="1ec74-145">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="1ec74-146">Windows etki alanı ile geri dönüş olarak NTLM kullanır.</span><span class="sxs-lookup"><span data-stu-id="1ec74-146">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="1ec74-147">Tümleşik Windows kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="1ec74-147">Uses integrated Windows authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1ec74-148">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1ec74-148">Child Elements</span></span>  
 <span data-ttu-id="1ec74-149">Yok.</span><span class="sxs-lookup"><span data-stu-id="1ec74-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1ec74-150">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1ec74-150">Parent Elements</span></span>  
  
|<span data-ttu-id="1ec74-151">Öğe</span><span class="sxs-lookup"><span data-stu-id="1ec74-151">Element</span></span>|<span data-ttu-id="1ec74-152">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1ec74-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1ec74-153">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="1ec74-153">\<security></span></span>](security-of-webhttpbinding.md)|<span data-ttu-id="1ec74-154">WSHttpBinding > öğesinin güvenlik yeteneklerini [ \<](wshttpbinding.md) temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1ec74-154">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1ec74-155">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1ec74-155">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.WebHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WebHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [<span data-ttu-id="1ec74-156">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="1ec74-156">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="1ec74-157">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="1ec74-157">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="1ec74-158">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="1ec74-158">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="1ec74-159">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="1ec74-159">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="1ec74-160">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="1ec74-160">\<binding></span></span>](../../../misc/binding.md)
- [<span data-ttu-id="1ec74-161">WCF Web HTTP Programlama Modeli</span><span class="sxs-lookup"><span data-stu-id="1ec74-161">WCF Web HTTP Programming Model</span></span>](../../../wcf/feature-details/wcf-web-http-programming-model.md)

---
title: "&lt;wsHttpBinding&gt; &lt;taşıma&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21e38acf-450a-4bda-82b6-de305e1f7cd8
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e1ea5fc60f4dc64fd895469b580b81379da26191
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="lttransportgt-of-ltwshttpbindinggt"></a><span data-ttu-id="7be69-102">&lt;wsHttpBinding&gt; &lt;taşıma&gt;</span><span class="sxs-lookup"><span data-stu-id="7be69-102">&lt;transport&gt; of &lt;wsHttpBinding&gt;</span></span>
<span data-ttu-id="7be69-103">HTTP taşıma için kimlik doğrulama ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7be69-103">Defines authentication settings for the HTTP transport.</span></span>  
  
 <span data-ttu-id="7be69-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="7be69-104">\<system.serviceModel></span></span>  
<span data-ttu-id="7be69-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="7be69-105">\<bindings></span></span>  
<span data-ttu-id="7be69-106">\<wsHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="7be69-106">\<wsHttpBinding></span></span>  
<span data-ttu-id="7be69-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="7be69-107">\<binding></span></span>  
<span data-ttu-id="7be69-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="7be69-108">\<security></span></span>  
<span data-ttu-id="7be69-109">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="7be69-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7be69-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7be69-110">Syntax</span></span>  
  
```xml  
<wsHttpBinding>  
    <binding>  
        <security mode="None|Transport|TransportWithMessageCredential|TransportCredentialOnly">  
            <transport  
            clientCredentialType="Basic|Certificate|Digest|None|Ntlm|Windows"  
            proxyCredentialType="Basic|Digest|None|Ntlm|Windows"  
            realm="string" />  
                <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always" protectionScenario="TransportSelected|TrustedProxy">  
                    <customServiceNames></customServiceNames>  
                </extendedProtecutionPolicy>  
            </transport>  
        </security>  
    </binding>  
</wsHttpBinding>  
```  
  
## <a name="type"></a><span data-ttu-id="7be69-111">Tür</span><span class="sxs-lookup"><span data-stu-id="7be69-111">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7be69-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7be69-112">Attributes and Elements</span></span>  
 <span data-ttu-id="7be69-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7be69-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7be69-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7be69-114">Attributes</span></span>  
  
|<span data-ttu-id="7be69-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7be69-115">Attribute</span></span>|<span data-ttu-id="7be69-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7be69-116">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="7be69-117">Hizmeti için istemci kimlik doğrulaması için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7be69-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="7be69-118">Bu öznitelik türünde <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="7be69-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="7be69-119">Bir etki alanı Ara sunucu için istemci kimlik doğrulaması için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7be69-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="7be69-120">Bu öznitelik türünde <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="7be69-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="7be69-121">Özet veya temel kimlik doğrulaması için kimlik doğrulaması bölgesi belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="7be69-121">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="7be69-122">Varsayılan boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="7be69-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="7be69-123">Bir kimlik doğrulaması bölgesi, en az kimlik doğrulaması yapan ana bilgisayar adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7be69-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="7be69-124">Ayrıca, erişimi olan bir kullanıcı koleksiyonu de belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7be69-124">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="7be69-125">Bir kullanıcı hangisinin birkaç olası kullanıcı adları ve parolalar kullanılabilir olmadığından emin olmak için kimlik doğrulaması bölgesi sorgulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7be69-125">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|  
|`policyEnforcement`|<span data-ttu-id="7be69-126">Bu numaralandırma ne zaman belirtir <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> zorunlu tutulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7be69-126">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="7be69-127">1.  Hiçbir zaman – ilke hiçbir zaman zorlanır (genişletilmiş koruma devre dışı).</span><span class="sxs-lookup"><span data-stu-id="7be69-127">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="7be69-128">2.  Yalnızca istemci genişletilmiş koruma destekliyorsa WhenSupported – ilke uygulanır.</span><span class="sxs-lookup"><span data-stu-id="7be69-128">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="7be69-129">3.  Her zaman – ilke her zaman zorlanır.</span><span class="sxs-lookup"><span data-stu-id="7be69-129">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="7be69-130">Genişletilmiş Koruma desteklemeyen istemcilerin kimliğini doğrulamak başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="7be69-130">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="7be69-131">clientCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="7be69-131">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="7be69-132">Değer</span><span class="sxs-lookup"><span data-stu-id="7be69-132">Value</span></span>|<span data-ttu-id="7be69-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7be69-133">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="7be69-134">Güvenliği devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="7be69-134">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="7be69-135">Temel kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="7be69-135">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="7be69-136">Özet kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="7be69-136">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="7be69-137">Bir Windows etki alanı ile bir geri dönüş olarak NTLM kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="7be69-137">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="7be69-138">Tümleşik Windows kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="7be69-138">Uses integrated Windows authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="7be69-139">İstemci kimlik doğrulaması için X.509 sertifikaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="7be69-139">Uses X.509 certificates to authenticate the client.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="7be69-140">proxyCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="7be69-140">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="7be69-141">Değer</span><span class="sxs-lookup"><span data-stu-id="7be69-141">Value</span></span>|<span data-ttu-id="7be69-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7be69-142">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="7be69-143">Güvenliği devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="7be69-143">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="7be69-144">Temel kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="7be69-144">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="7be69-145">Özet kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="7be69-145">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="7be69-146">Bir Windows etki alanı ile bir geri dönüş olarak NTLM kullanır.</span><span class="sxs-lookup"><span data-stu-id="7be69-146">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="7be69-147">Tümleşik Windows kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="7be69-147">Uses integrated Windows authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="7be69-148">İstemci kimlik doğrulaması için X.509 sertifikaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="7be69-148">Uses X.509 certificates to authenticate the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7be69-149">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7be69-149">Child Elements</span></span>  
 <span data-ttu-id="7be69-150">Yok.</span><span class="sxs-lookup"><span data-stu-id="7be69-150">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7be69-151">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7be69-151">Parent Elements</span></span>  
  
|<span data-ttu-id="7be69-152">Öğe</span><span class="sxs-lookup"><span data-stu-id="7be69-152">Element</span></span>|<span data-ttu-id="7be69-153">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7be69-153">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7be69-154">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="7be69-154">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)|<span data-ttu-id="7be69-155">Güvenlik özellikleri temsil eden [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="7be69-155">Represents the security capabilities of the [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7be69-156">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7be69-156">See Also</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>  
 [<span data-ttu-id="7be69-157">Hizmetler ve istemcileri güvenli hale getirme</span><span class="sxs-lookup"><span data-stu-id="7be69-157">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="7be69-158">Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="7be69-158">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="7be69-159">Sistem tarafından sağlanan bağlamaları yapılandırma</span><span class="sxs-lookup"><span data-stu-id="7be69-159">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="7be69-160">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="7be69-160">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="7be69-161">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="7be69-161">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)

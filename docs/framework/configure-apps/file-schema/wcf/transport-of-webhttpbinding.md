---
title: "&lt;webHttpBinding&gt; &lt;taşıma&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f150fb19-7de1-44af-81f4-86cad881cd05
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2d5c0d17f756c4cca84a48cf6849c4d0945cc2b3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="lttransportgt-of-ltwebhttpbindinggt"></a><span data-ttu-id="c7bba-102">&lt;webHttpBinding&gt; &lt;taşıma&gt;</span><span class="sxs-lookup"><span data-stu-id="c7bba-102">&lt;transport&gt; of &lt;webHttpBinding&gt;</span></span>
<span data-ttu-id="c7bba-103">HTTP isteklerini almak için yapılandırılan hizmet uç noktası için aktarım düzeyinde güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c7bba-103">Defines the transport-level security settings for a service endpoint configured to receive HTTP requests.</span></span>  
  
 <span data-ttu-id="c7bba-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="c7bba-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="c7bba-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="c7bba-105">\<bindings></span></span>  
<span data-ttu-id="c7bba-106">\<webHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="c7bba-106">\<webHttpBinding></span></span>  
<span data-ttu-id="c7bba-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="c7bba-107">\<binding></span></span>  
<span data-ttu-id="c7bba-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="c7bba-108">\<security></span></span>  
<span data-ttu-id="c7bba-109">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="c7bba-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7bba-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c7bba-110">Syntax</span></span>  
  
```xml  
<webHttpBinding>  
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
</WebHttpBinding>  
```  
  
## <a name="type"></a><span data-ttu-id="c7bba-111">Tür</span><span class="sxs-lookup"><span data-stu-id="c7bba-111">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c7bba-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c7bba-112">Attributes and Elements</span></span>  
 <span data-ttu-id="c7bba-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c7bba-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c7bba-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c7bba-114">Attributes</span></span>  
  
|<span data-ttu-id="c7bba-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c7bba-115">Attribute</span></span>|<span data-ttu-id="c7bba-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c7bba-116">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="c7bba-117">Hizmeti için istemci kimlik doğrulaması için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c7bba-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="c7bba-118">Bu öznitelik türünde <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="c7bba-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="c7bba-119">Bir etki alanı Ara sunucu için istemci kimlik doğrulaması için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c7bba-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="c7bba-120">Bu öznitelik türünde <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="c7bba-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="c7bba-121">Özet veya temel kimlik doğrulaması için kimlik doğrulaması bölgesi belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="c7bba-121">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="c7bba-122">Varsayılan boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="c7bba-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="c7bba-123">Bir kimlik doğrulaması bölgesi, en az kimlik doğrulaması yapan ana bilgisayar adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c7bba-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="c7bba-124">Ayrıca, erişimi olan bir kullanıcı koleksiyonu de belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7bba-124">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="c7bba-125">Bir kullanıcı hangisinin birkaç olası kullanıcı adları ve parolalar kullanılabilir olmadığından emin olmak için kimlik doğrulaması bölgesi sorgulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7bba-125">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|  
|`policyEnforcement`|<span data-ttu-id="c7bba-126">Bu numaralandırma ne zaman belirtir <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> zorunlu tutulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c7bba-126">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="c7bba-127">1.  Hiçbir zaman – ilke hiçbir zaman zorlanır (genişletilmiş koruma devre dışı).</span><span class="sxs-lookup"><span data-stu-id="c7bba-127">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="c7bba-128">2.  Yalnızca istemci genişletilmiş koruma destekliyorsa WhenSupported – ilke uygulanır.</span><span class="sxs-lookup"><span data-stu-id="c7bba-128">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="c7bba-129">3.  Her zaman – ilke her zaman zorlanır.</span><span class="sxs-lookup"><span data-stu-id="c7bba-129">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="c7bba-130">Genişletilmiş Koruma desteklemeyen istemcilerin kimliğini doğrulamak başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="c7bba-130">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="c7bba-131">clientCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="c7bba-131">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="c7bba-132">Değer</span><span class="sxs-lookup"><span data-stu-id="c7bba-132">Value</span></span>|<span data-ttu-id="c7bba-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c7bba-133">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="c7bba-134">Güvenliği devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="c7bba-134">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="c7bba-135">Temel kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="c7bba-135">Uses basic authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="c7bba-136">İstemci kimlik doğrulaması için X.509 sertifikaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="c7bba-136">Uses X.509 certificates to authenticate the client.</span></span>|  
|`Digest`|<span data-ttu-id="c7bba-137">Özet kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="c7bba-137">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="c7bba-138">Bir Windows etki alanı ile bir geri dönüş olarak NTLM kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="c7bba-138">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="c7bba-139">Tümleşik Windows kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="c7bba-139">Uses integrated Windows authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="c7bba-140">proxyCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="c7bba-140">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="c7bba-141">Değer</span><span class="sxs-lookup"><span data-stu-id="c7bba-141">Value</span></span>|<span data-ttu-id="c7bba-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c7bba-142">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="c7bba-143">Güvenliği devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="c7bba-143">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="c7bba-144">Temel kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="c7bba-144">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="c7bba-145">Özet kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="c7bba-145">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="c7bba-146">Bir Windows etki alanı ile bir geri dönüş olarak NTLM kullanır.</span><span class="sxs-lookup"><span data-stu-id="c7bba-146">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="c7bba-147">Tümleşik Windows kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="c7bba-147">Uses integrated Windows authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c7bba-148">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c7bba-148">Child Elements</span></span>  
 <span data-ttu-id="c7bba-149">Yok.</span><span class="sxs-lookup"><span data-stu-id="c7bba-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c7bba-150">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c7bba-150">Parent Elements</span></span>  
  
|<span data-ttu-id="c7bba-151">Öğe</span><span class="sxs-lookup"><span data-stu-id="c7bba-151">Element</span></span>|<span data-ttu-id="c7bba-152">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c7bba-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c7bba-153">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="c7bba-153">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-webhttpbinding.md)|<span data-ttu-id="c7bba-154">Güvenlik özellikleri temsil eden [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="c7bba-154">Represents the security capabilities of the [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c7bba-155">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c7bba-155">See Also</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 <xref:System.ServiceModel.Configuration.WebHttpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.WebHttpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>  
 [<span data-ttu-id="c7bba-156">Hizmetler ve istemcileri güvenli hale getirme</span><span class="sxs-lookup"><span data-stu-id="c7bba-156">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="c7bba-157">Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="c7bba-157">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="c7bba-158">Sistem tarafından sağlanan bağlamaları yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c7bba-158">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="c7bba-159">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="c7bba-159">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="c7bba-160">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="c7bba-160">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="c7bba-161">WCF Web HTTP programlama modeli</span><span class="sxs-lookup"><span data-stu-id="c7bba-161">WCF Web HTTP Programming Model</span></span>](../../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)

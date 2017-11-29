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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 44397edf2d2c5e2f99a255789452b08d91484b81
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="lttransportgt-of-ltwebhttpbindinggt"></a><span data-ttu-id="de985-102">&lt;webHttpBinding&gt; &lt;taşıma&gt;</span><span class="sxs-lookup"><span data-stu-id="de985-102">&lt;transport&gt; of &lt;webHttpBinding&gt;</span></span>
<span data-ttu-id="de985-103">HTTP isteklerini almak için yapılandırılan hizmet uç noktası için aktarım düzeyinde güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="de985-103">Defines the transport-level security settings for a service endpoint configured to receive HTTP requests.</span></span>  
  
 <span data-ttu-id="de985-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="de985-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="de985-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="de985-105">\<bindings></span></span>  
<span data-ttu-id="de985-106">\<webHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="de985-106">\<webHttpBinding></span></span>  
<span data-ttu-id="de985-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="de985-107">\<binding></span></span>  
<span data-ttu-id="de985-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="de985-108">\<security></span></span>  
<span data-ttu-id="de985-109">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="de985-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de985-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="de985-110">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="de985-111">Tür</span><span class="sxs-lookup"><span data-stu-id="de985-111">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="de985-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="de985-112">Attributes and Elements</span></span>  
 <span data-ttu-id="de985-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="de985-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="de985-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="de985-114">Attributes</span></span>  
  
|<span data-ttu-id="de985-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="de985-115">Attribute</span></span>|<span data-ttu-id="de985-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="de985-116">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="de985-117">Hizmeti için istemci kimlik doğrulaması için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="de985-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="de985-118">Bu öznitelik türünde <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="de985-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="de985-119">Bir etki alanı Ara sunucu için istemci kimlik doğrulaması için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="de985-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="de985-120">Bu öznitelik türünde <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="de985-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="de985-121">Özet veya temel kimlik doğrulaması için kimlik doğrulaması bölgesi belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="de985-121">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="de985-122">Varsayılan boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="de985-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="de985-123">Bir kimlik doğrulaması bölgesi, en az kimlik doğrulaması yapan ana bilgisayar adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="de985-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="de985-124">Ayrıca, erişimi olan bir kullanıcı koleksiyonu de belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="de985-124">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="de985-125">Bir kullanıcı hangisinin birkaç olası kullanıcı adları ve parolalar kullanılabilir olmadığından emin olmak için kimlik doğrulaması bölgesi sorgulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="de985-125">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|  
|`policyEnforcement`|<span data-ttu-id="de985-126">Bu numaralandırma ne zaman belirtir <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> zorunlu tutulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="de985-126">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="de985-127">1.  Hiçbir zaman – ilke hiçbir zaman zorlanır (genişletilmiş koruma devre dışı).</span><span class="sxs-lookup"><span data-stu-id="de985-127">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="de985-128">2.  Yalnızca istemci genişletilmiş koruma destekliyorsa WhenSupported – ilke uygulanır.</span><span class="sxs-lookup"><span data-stu-id="de985-128">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="de985-129">3.  Her zaman – ilke her zaman zorlanır.</span><span class="sxs-lookup"><span data-stu-id="de985-129">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="de985-130">Genişletilmiş Koruma desteklemeyen istemcilerin kimliğini doğrulamak başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="de985-130">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="de985-131">clientCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="de985-131">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="de985-132">Değer</span><span class="sxs-lookup"><span data-stu-id="de985-132">Value</span></span>|<span data-ttu-id="de985-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="de985-133">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="de985-134">Güvenliği devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="de985-134">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="de985-135">Temel kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="de985-135">Uses basic authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="de985-136">İstemci kimlik doğrulaması için X.509 sertifikaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="de985-136">Uses X.509 certificates to authenticate the client.</span></span>|  
|`Digest`|<span data-ttu-id="de985-137">Özet kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="de985-137">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="de985-138">Bir Windows etki alanı ile bir geri dönüş olarak NTLM kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="de985-138">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="de985-139">Tümleşik Windows kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="de985-139">Uses integrated Windows authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="de985-140">proxyCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="de985-140">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="de985-141">Değer</span><span class="sxs-lookup"><span data-stu-id="de985-141">Value</span></span>|<span data-ttu-id="de985-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="de985-142">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="de985-143">Güvenliği devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="de985-143">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="de985-144">Temel kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="de985-144">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="de985-145">Özet kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="de985-145">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="de985-146">Bir Windows etki alanı ile bir geri dönüş olarak NTLM kullanır.</span><span class="sxs-lookup"><span data-stu-id="de985-146">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="de985-147">Tümleşik Windows kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="de985-147">Uses integrated Windows authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="de985-148">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="de985-148">Child Elements</span></span>  
 <span data-ttu-id="de985-149">Yok.</span><span class="sxs-lookup"><span data-stu-id="de985-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="de985-150">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="de985-150">Parent Elements</span></span>  
  
|<span data-ttu-id="de985-151">Öğe</span><span class="sxs-lookup"><span data-stu-id="de985-151">Element</span></span>|<span data-ttu-id="de985-152">Açıklama</span><span class="sxs-lookup"><span data-stu-id="de985-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="de985-153">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="de985-153">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-webhttpbinding.md)|<span data-ttu-id="de985-154">Güvenlik özellikleri temsil eden [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="de985-154">Represents the security capabilities of the [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="de985-155">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="de985-155">See Also</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 <xref:System.ServiceModel.Configuration.WebHttpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.WebHttpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>  
 [<span data-ttu-id="de985-156">Hizmetler ve istemcileri güvenli hale getirme</span><span class="sxs-lookup"><span data-stu-id="de985-156">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="de985-157">Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="de985-157">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="de985-158">Sistem tarafından sağlanan bağlamaları yapılandırma</span><span class="sxs-lookup"><span data-stu-id="de985-158">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="de985-159">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="de985-159">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="de985-160">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="de985-160">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="de985-161">WCF Web HTTP programlama modeli</span><span class="sxs-lookup"><span data-stu-id="de985-161">WCF Web HTTP Programming Model</span></span>](../../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)

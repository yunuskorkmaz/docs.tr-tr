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
ms.workload: dotnet
ms.openlocfilehash: ebc9bb8b128f4b4097d4f470920dbd28d17e6f00
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="lttransportgt-of-ltwebhttpbindinggt"></a><span data-ttu-id="d7e1c-102">&lt;webHttpBinding&gt; &lt;taşıma&gt;</span><span class="sxs-lookup"><span data-stu-id="d7e1c-102">&lt;transport&gt; of &lt;webHttpBinding&gt;</span></span>
<span data-ttu-id="d7e1c-103">HTTP isteklerini almak için yapılandırılan hizmet uç noktası için aktarım düzeyinde güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d7e1c-103">Defines the transport-level security settings for a service endpoint configured to receive HTTP requests.</span></span>  
  
 <span data-ttu-id="d7e1c-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="d7e1c-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d7e1c-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="d7e1c-105">\<bindings></span></span>  
<span data-ttu-id="d7e1c-106">\<webHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="d7e1c-106">\<webHttpBinding></span></span>  
<span data-ttu-id="d7e1c-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="d7e1c-107">\<binding></span></span>  
<span data-ttu-id="d7e1c-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="d7e1c-108">\<security></span></span>  
<span data-ttu-id="d7e1c-109">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="d7e1c-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7e1c-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d7e1c-110">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="d7e1c-111">Tür</span><span class="sxs-lookup"><span data-stu-id="d7e1c-111">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d7e1c-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d7e1c-112">Attributes and Elements</span></span>  
 <span data-ttu-id="d7e1c-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d7e1c-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d7e1c-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d7e1c-114">Attributes</span></span>  
  
|<span data-ttu-id="d7e1c-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d7e1c-115">Attribute</span></span>|<span data-ttu-id="d7e1c-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d7e1c-116">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="d7e1c-117">Hizmeti için istemci kimlik doğrulaması için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d7e1c-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="d7e1c-118">Bu öznitelik türünde <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="d7e1c-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="d7e1c-119">Bir etki alanı Ara sunucu için istemci kimlik doğrulaması için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d7e1c-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="d7e1c-120">Bu öznitelik türünde <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="d7e1c-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="d7e1c-121">Özet veya temel kimlik doğrulaması için kimlik doğrulaması bölgesi belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="d7e1c-121">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="d7e1c-122">Varsayılan boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="d7e1c-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="d7e1c-123">Bir kimlik doğrulaması bölgesi, en az kimlik doğrulaması yapan ana bilgisayar adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d7e1c-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="d7e1c-124">Ayrıca, erişimi olan bir kullanıcı koleksiyonu de belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d7e1c-124">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="d7e1c-125">Bir kullanıcı hangisinin birkaç olası kullanıcı adları ve parolalar kullanılabilir olmadığından emin olmak için kimlik doğrulaması bölgesi sorgulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d7e1c-125">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|  
|`policyEnforcement`|<span data-ttu-id="d7e1c-126">Bu numaralandırma ne zaman belirtir <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> zorunlu tutulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d7e1c-126">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="d7e1c-127">1.  Hiçbir zaman – ilke hiçbir zaman zorlanır (genişletilmiş koruma devre dışı).</span><span class="sxs-lookup"><span data-stu-id="d7e1c-127">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="d7e1c-128">2.  Yalnızca istemci genişletilmiş koruma destekliyorsa WhenSupported – ilke uygulanır.</span><span class="sxs-lookup"><span data-stu-id="d7e1c-128">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="d7e1c-129">3.  Her zaman – ilke her zaman zorlanır.</span><span class="sxs-lookup"><span data-stu-id="d7e1c-129">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="d7e1c-130">Genişletilmiş Koruma desteklemeyen istemcilerin kimliğini doğrulamak başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="d7e1c-130">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="d7e1c-131">clientCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="d7e1c-131">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="d7e1c-132">Değer</span><span class="sxs-lookup"><span data-stu-id="d7e1c-132">Value</span></span>|<span data-ttu-id="d7e1c-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d7e1c-133">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="d7e1c-134">Güvenliği devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="d7e1c-134">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="d7e1c-135">Temel kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="d7e1c-135">Uses basic authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="d7e1c-136">İstemci kimlik doğrulaması için X.509 sertifikaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="d7e1c-136">Uses X.509 certificates to authenticate the client.</span></span>|  
|`Digest`|<span data-ttu-id="d7e1c-137">Özet kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="d7e1c-137">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="d7e1c-138">Bir Windows etki alanı ile bir geri dönüş olarak NTLM kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="d7e1c-138">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="d7e1c-139">Tümleşik Windows kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="d7e1c-139">Uses integrated Windows authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="d7e1c-140">proxyCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="d7e1c-140">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="d7e1c-141">Değer</span><span class="sxs-lookup"><span data-stu-id="d7e1c-141">Value</span></span>|<span data-ttu-id="d7e1c-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d7e1c-142">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="d7e1c-143">Güvenliği devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="d7e1c-143">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="d7e1c-144">Temel kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="d7e1c-144">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="d7e1c-145">Özet kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="d7e1c-145">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="d7e1c-146">Bir Windows etki alanı ile bir geri dönüş olarak NTLM kullanır.</span><span class="sxs-lookup"><span data-stu-id="d7e1c-146">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="d7e1c-147">Tümleşik Windows kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="d7e1c-147">Uses integrated Windows authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d7e1c-148">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d7e1c-148">Child Elements</span></span>  
 <span data-ttu-id="d7e1c-149">Yok.</span><span class="sxs-lookup"><span data-stu-id="d7e1c-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d7e1c-150">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d7e1c-150">Parent Elements</span></span>  
  
|<span data-ttu-id="d7e1c-151">Öğe</span><span class="sxs-lookup"><span data-stu-id="d7e1c-151">Element</span></span>|<span data-ttu-id="d7e1c-152">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d7e1c-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d7e1c-153">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="d7e1c-153">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-webhttpbinding.md)|<span data-ttu-id="d7e1c-154">Güvenlik özellikleri temsil eden [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="d7e1c-154">Represents the security capabilities of the [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d7e1c-155">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d7e1c-155">See Also</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 <xref:System.ServiceModel.Configuration.WebHttpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.WebHttpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>  
 [<span data-ttu-id="d7e1c-156">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="d7e1c-156">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="d7e1c-157">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="d7e1c-157">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="d7e1c-158">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d7e1c-158">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="d7e1c-159">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="d7e1c-159">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="d7e1c-160">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="d7e1c-160">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="d7e1c-161">WCF Web HTTP Programlama Modeli</span><span class="sxs-lookup"><span data-stu-id="d7e1c-161">WCF Web HTTP Programming Model</span></span>](../../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)

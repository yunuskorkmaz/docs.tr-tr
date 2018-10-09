---
title: '&lt;webHttpBinding&gt; &lt;taşıma&gt;'
ms.date: 03/30/2017
ms.assetid: f150fb19-7de1-44af-81f4-86cad881cd05
ms.openlocfilehash: 3401eada9ae2580cc665d9b4a5a6475f86b68072
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48873819"
---
# <a name="lttransportgt-of-ltwebhttpbindinggt"></a><span data-ttu-id="58027-102">&lt;webHttpBinding&gt; &lt;taşıma&gt;</span><span class="sxs-lookup"><span data-stu-id="58027-102">&lt;transport&gt; of &lt;webHttpBinding&gt;</span></span>
<span data-ttu-id="58027-103">HTTP isteklerini almak için yapılandırılmış hizmet uç noktası için aktarma düzeyinde güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="58027-103">Defines the transport-level security settings for a service endpoint configured to receive HTTP requests.</span></span>  
  
 <span data-ttu-id="58027-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="58027-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="58027-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="58027-105">\<bindings></span></span>  
<span data-ttu-id="58027-106">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="58027-106">\<webHttpBinding></span></span>  
<span data-ttu-id="58027-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="58027-107">\<binding></span></span>  
<span data-ttu-id="58027-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="58027-108">\<security></span></span>  
<span data-ttu-id="58027-109">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="58027-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58027-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="58027-110">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="58027-111">Tür</span><span class="sxs-lookup"><span data-stu-id="58027-111">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="58027-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="58027-112">Attributes and Elements</span></span>  
 <span data-ttu-id="58027-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="58027-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="58027-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="58027-114">Attributes</span></span>  
  
|<span data-ttu-id="58027-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="58027-115">Attribute</span></span>|<span data-ttu-id="58027-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="58027-116">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="58027-117">Bir hizmete istemcinin kimliğini doğrulamak için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="58027-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="58027-118">Bu öznitelik türünde <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="58027-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="58027-119">Bir etki alanı Ara sunucusu istemcinin kimliğini doğrulamak için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="58027-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="58027-120">Bu öznitelik türünde <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="58027-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="58027-121">Özet veya temel kimlik doğrulaması için kimlik doğrulaması bölgesi belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="58027-121">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="58027-122">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="58027-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="58027-123">Bir kimlik doğrulaması bölgesi, kimlik doğrulaması yapan bir ana bilgisayar adı en az belirtir.</span><span class="sxs-lookup"><span data-stu-id="58027-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="58027-124">Ayrıca, erişimi olan bir kullanıcı koleksiyonu da belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="58027-124">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="58027-125">Bir kullanıcı kimlik doğrulaması bölgesi, hangisinin birkaç olası kullanıcı adları ve parolalar kullanılabilir olmadığından emin olmak için sorgulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="58027-125">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|  
|`policyEnforcement`|<span data-ttu-id="58027-126">Bu sabit listesi ne zaman belirtir <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> zorlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="58027-126">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="58027-127">1.  Hiçbir zaman – hiçbir zaman ilkenin uygulanıp (genişletilmiş koruma devre dışı).</span><span class="sxs-lookup"><span data-stu-id="58027-127">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="58027-128">2.  Yalnızca istemci genişletilmiş koruma destekliyorsa WhenSupported – ilke zorunlu tutulur.</span><span class="sxs-lookup"><span data-stu-id="58027-128">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="58027-129">3.  Her zaman – ilke her zaman uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="58027-129">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="58027-130">Genişletilmiş Koruma desteklemeyen istemciler kimlik doğrulaması başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="58027-130">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="58027-131">clientCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="58027-131">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="58027-132">Değer</span><span class="sxs-lookup"><span data-stu-id="58027-132">Value</span></span>|<span data-ttu-id="58027-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="58027-133">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="58027-134">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="58027-134">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="58027-135">Temel kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="58027-135">Uses basic authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="58027-136">İstemcinin kimliğini doğrulamak için X.509 sertifikaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="58027-136">Uses X.509 certificates to authenticate the client.</span></span>|  
|`Digest`|<span data-ttu-id="58027-137">Özet kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="58027-137">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="58027-138">Bir Windows etki alanı ile bir geri dönüş olarak NTLM kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="58027-138">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="58027-139">Tümleşik Windows kimlik doğrulaması olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="58027-139">Uses integrated Windows authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="58027-140">proxyCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="58027-140">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="58027-141">Değer</span><span class="sxs-lookup"><span data-stu-id="58027-141">Value</span></span>|<span data-ttu-id="58027-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="58027-142">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="58027-143">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="58027-143">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="58027-144">Temel kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="58027-144">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="58027-145">Özet kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="58027-145">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="58027-146">Bir Windows etki alanı ile bir geri dönüş olarak NTLM kullanır.</span><span class="sxs-lookup"><span data-stu-id="58027-146">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="58027-147">Tümleşik Windows kimlik doğrulaması olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="58027-147">Uses integrated Windows authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="58027-148">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="58027-148">Child Elements</span></span>  
 <span data-ttu-id="58027-149">Yok.</span><span class="sxs-lookup"><span data-stu-id="58027-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="58027-150">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="58027-150">Parent Elements</span></span>  
  
|<span data-ttu-id="58027-151">Öğe</span><span class="sxs-lookup"><span data-stu-id="58027-151">Element</span></span>|<span data-ttu-id="58027-152">Açıklama</span><span class="sxs-lookup"><span data-stu-id="58027-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="58027-153">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="58027-153">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-webhttpbinding.md)|<span data-ttu-id="58027-154">Güvenlik özelliklerini gösteren [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="58027-154">Represents the security capabilities of the [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="58027-155">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="58027-155">See Also</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 <xref:System.ServiceModel.Configuration.WebHttpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.WebHttpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>  
 [<span data-ttu-id="58027-156">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="58027-156">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="58027-157">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="58027-157">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="58027-158">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="58027-158">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="58027-159">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="58027-159">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="58027-160">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="58027-160">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="58027-161">WCF Web HTTP Programlama Modeli</span><span class="sxs-lookup"><span data-stu-id="58027-161">WCF Web HTTP Programming Model</span></span>](../../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)

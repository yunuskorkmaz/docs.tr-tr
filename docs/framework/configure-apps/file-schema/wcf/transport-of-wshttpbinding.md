---
title: '&lt;wsHttpBinding&gt; &lt;taşıma&gt;'
ms.date: 03/30/2017
ms.assetid: 21e38acf-450a-4bda-82b6-de305e1f7cd8
ms.openlocfilehash: 5a62eefa6865a6908caecef87b0e457040df0b21
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48850159"
---
# <a name="lttransportgt-of-ltwshttpbindinggt"></a><span data-ttu-id="a011e-102">&lt;wsHttpBinding&gt; &lt;taşıma&gt;</span><span class="sxs-lookup"><span data-stu-id="a011e-102">&lt;transport&gt; of &lt;wsHttpBinding&gt;</span></span>
<span data-ttu-id="a011e-103">HTTP taşıma için kimlik doğrulama ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a011e-103">Defines authentication settings for the HTTP transport.</span></span>  
  
 <span data-ttu-id="a011e-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a011e-104">\<system.serviceModel></span></span>  
<span data-ttu-id="a011e-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="a011e-105">\<bindings></span></span>  
<span data-ttu-id="a011e-106">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="a011e-106">\<wsHttpBinding></span></span>  
<span data-ttu-id="a011e-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="a011e-107">\<binding></span></span>  
<span data-ttu-id="a011e-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="a011e-108">\<security></span></span>  
<span data-ttu-id="a011e-109">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="a011e-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a011e-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a011e-110">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="a011e-111">Tür</span><span class="sxs-lookup"><span data-stu-id="a011e-111">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a011e-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a011e-112">Attributes and Elements</span></span>  
 <span data-ttu-id="a011e-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a011e-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a011e-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a011e-114">Attributes</span></span>  
  
|<span data-ttu-id="a011e-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a011e-115">Attribute</span></span>|<span data-ttu-id="a011e-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a011e-116">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="a011e-117">Bir hizmete istemcinin kimliğini doğrulamak için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a011e-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="a011e-118">Bu öznitelik türünde <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="a011e-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="a011e-119">Bir etki alanı Ara sunucusu istemcinin kimliğini doğrulamak için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a011e-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="a011e-120">Bu öznitelik türünde <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="a011e-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="a011e-121">Özet veya temel kimlik doğrulaması için kimlik doğrulaması bölgesi belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="a011e-121">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="a011e-122">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="a011e-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="a011e-123">Bir kimlik doğrulaması bölgesi, kimlik doğrulaması yapan bir ana bilgisayar adı en az belirtir.</span><span class="sxs-lookup"><span data-stu-id="a011e-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="a011e-124">Ayrıca, erişimi olan bir kullanıcı koleksiyonu da belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a011e-124">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="a011e-125">Bir kullanıcı kimlik doğrulaması bölgesi, hangisinin birkaç olası kullanıcı adları ve parolalar kullanılabilir olmadığından emin olmak için sorgulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a011e-125">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|  
|`policyEnforcement`|<span data-ttu-id="a011e-126">Bu sabit listesi ne zaman belirtir <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> zorlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a011e-126">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="a011e-127">1.  Hiçbir zaman – hiçbir zaman ilkenin uygulanıp (genişletilmiş koruma devre dışı).</span><span class="sxs-lookup"><span data-stu-id="a011e-127">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="a011e-128">2.  Yalnızca istemci genişletilmiş koruma destekliyorsa WhenSupported – ilke zorunlu tutulur.</span><span class="sxs-lookup"><span data-stu-id="a011e-128">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="a011e-129">3.  Her zaman – ilke her zaman uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="a011e-129">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="a011e-130">Genişletilmiş Koruma desteklemeyen istemciler kimlik doğrulaması başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="a011e-130">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="a011e-131">clientCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="a011e-131">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="a011e-132">Değer</span><span class="sxs-lookup"><span data-stu-id="a011e-132">Value</span></span>|<span data-ttu-id="a011e-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a011e-133">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="a011e-134">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="a011e-134">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="a011e-135">Temel kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="a011e-135">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="a011e-136">Özet kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="a011e-136">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="a011e-137">Bir Windows etki alanı ile bir geri dönüş olarak NTLM kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="a011e-137">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="a011e-138">Tümleşik Windows kimlik doğrulaması olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="a011e-138">Uses integrated Windows authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="a011e-139">İstemcinin kimliğini doğrulamak için X.509 sertifikaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="a011e-139">Uses X.509 certificates to authenticate the client.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="a011e-140">proxyCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="a011e-140">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="a011e-141">Değer</span><span class="sxs-lookup"><span data-stu-id="a011e-141">Value</span></span>|<span data-ttu-id="a011e-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a011e-142">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="a011e-143">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="a011e-143">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="a011e-144">Temel kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="a011e-144">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="a011e-145">Özet kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="a011e-145">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="a011e-146">Bir Windows etki alanı ile bir geri dönüş olarak NTLM kullanır.</span><span class="sxs-lookup"><span data-stu-id="a011e-146">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="a011e-147">Tümleşik Windows kimlik doğrulaması olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="a011e-147">Uses integrated Windows authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="a011e-148">İstemcinin kimliğini doğrulamak için X.509 sertifikaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="a011e-148">Uses X.509 certificates to authenticate the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a011e-149">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a011e-149">Child Elements</span></span>  
 <span data-ttu-id="a011e-150">Yok.</span><span class="sxs-lookup"><span data-stu-id="a011e-150">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a011e-151">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a011e-151">Parent Elements</span></span>  
  
|<span data-ttu-id="a011e-152">Öğe</span><span class="sxs-lookup"><span data-stu-id="a011e-152">Element</span></span>|<span data-ttu-id="a011e-153">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a011e-153">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a011e-154">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="a011e-154">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)|<span data-ttu-id="a011e-155">Güvenlik özelliklerini gösteren [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="a011e-155">Represents the security capabilities of the [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a011e-156">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a011e-156">See Also</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>  
 [<span data-ttu-id="a011e-157">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="a011e-157">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="a011e-158">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="a011e-158">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="a011e-159">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a011e-159">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="a011e-160">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="a011e-160">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="a011e-161">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="a011e-161">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)

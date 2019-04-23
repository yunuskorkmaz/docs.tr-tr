---
title: <transport> / <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: f150fb19-7de1-44af-81f4-86cad881cd05
ms.openlocfilehash: 8dcd51cd248dbba3ccf60295cb1712167684328e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59116288"
---
# <a name="transport-of-webhttpbinding"></a><span data-ttu-id="726f7-102">\<Aktarım >, \<webHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="726f7-102">\<transport> of \<webHttpBinding></span></span>
<span data-ttu-id="726f7-103">HTTP isteklerini almak için yapılandırılmış hizmet uç noktası için aktarma düzeyinde güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="726f7-103">Defines the transport-level security settings for a service endpoint configured to receive HTTP requests.</span></span>  
  
 <span data-ttu-id="726f7-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="726f7-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="726f7-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="726f7-105">\<bindings></span></span>  
<span data-ttu-id="726f7-106">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="726f7-106">\<webHttpBinding></span></span>  
<span data-ttu-id="726f7-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="726f7-107">\<binding></span></span>  
<span data-ttu-id="726f7-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="726f7-108">\<security></span></span>  
<span data-ttu-id="726f7-109">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="726f7-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="726f7-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="726f7-110">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="726f7-111">Tür</span><span class="sxs-lookup"><span data-stu-id="726f7-111">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="726f7-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="726f7-112">Attributes and Elements</span></span>  
 <span data-ttu-id="726f7-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="726f7-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="726f7-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="726f7-114">Attributes</span></span>  
  
|<span data-ttu-id="726f7-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="726f7-115">Attribute</span></span>|<span data-ttu-id="726f7-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="726f7-116">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="726f7-117">Bir hizmete istemcinin kimliğini doğrulamak için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="726f7-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="726f7-118">Bu öznitelik türünde <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="726f7-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="726f7-119">Bir etki alanı Ara sunucusu istemcinin kimliğini doğrulamak için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="726f7-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="726f7-120">Bu öznitelik türünde <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="726f7-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="726f7-121">Özet veya temel kimlik doğrulaması için kimlik doğrulaması bölgesi belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="726f7-121">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="726f7-122">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="726f7-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="726f7-123">Bir kimlik doğrulaması bölgesi, kimlik doğrulaması yapan bir ana bilgisayar adı en az belirtir.</span><span class="sxs-lookup"><span data-stu-id="726f7-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="726f7-124">Ayrıca, erişimi olan bir kullanıcı koleksiyonu da belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="726f7-124">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="726f7-125">Bir kullanıcı kimlik doğrulaması bölgesi, hangisinin birkaç olası kullanıcı adları ve parolalar kullanılabilir olmadığından emin olmak için sorgulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="726f7-125">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|  
|`policyEnforcement`|<span data-ttu-id="726f7-126">Bu sabit listesi ne zaman belirtir <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> zorlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="726f7-126">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="726f7-127">1.  Hiçbir zaman – hiçbir zaman ilkenin uygulanıp (genişletilmiş koruma devre dışı).</span><span class="sxs-lookup"><span data-stu-id="726f7-127">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="726f7-128">2.  Yalnızca istemci genişletilmiş koruma destekliyorsa WhenSupported – ilke zorunlu tutulur.</span><span class="sxs-lookup"><span data-stu-id="726f7-128">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="726f7-129">3.  Her zaman – ilke her zaman uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="726f7-129">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="726f7-130">Genişletilmiş Koruma desteklemeyen istemciler kimlik doğrulaması başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="726f7-130">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="726f7-131">clientCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="726f7-131">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="726f7-132">Değer</span><span class="sxs-lookup"><span data-stu-id="726f7-132">Value</span></span>|<span data-ttu-id="726f7-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="726f7-133">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="726f7-134">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="726f7-134">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="726f7-135">Temel kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="726f7-135">Uses basic authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="726f7-136">İstemcinin kimliğini doğrulamak için X.509 sertifikaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="726f7-136">Uses X.509 certificates to authenticate the client.</span></span>|  
|`Digest`|<span data-ttu-id="726f7-137">Özet kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="726f7-137">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="726f7-138">Bir Windows etki alanı ile bir geri dönüş olarak NTLM kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="726f7-138">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="726f7-139">Tümleşik Windows kimlik doğrulaması olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="726f7-139">Uses integrated Windows authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="726f7-140">proxyCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="726f7-140">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="726f7-141">Değer</span><span class="sxs-lookup"><span data-stu-id="726f7-141">Value</span></span>|<span data-ttu-id="726f7-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="726f7-142">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="726f7-143">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="726f7-143">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="726f7-144">Temel kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="726f7-144">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="726f7-145">Özet kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="726f7-145">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="726f7-146">Bir Windows etki alanı ile bir geri dönüş olarak NTLM kullanır.</span><span class="sxs-lookup"><span data-stu-id="726f7-146">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="726f7-147">Tümleşik Windows kimlik doğrulaması olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="726f7-147">Uses integrated Windows authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="726f7-148">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="726f7-148">Child Elements</span></span>  
 <span data-ttu-id="726f7-149">Yok.</span><span class="sxs-lookup"><span data-stu-id="726f7-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="726f7-150">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="726f7-150">Parent Elements</span></span>  
  
|<span data-ttu-id="726f7-151">Öğe</span><span class="sxs-lookup"><span data-stu-id="726f7-151">Element</span></span>|<span data-ttu-id="726f7-152">Açıklama</span><span class="sxs-lookup"><span data-stu-id="726f7-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="726f7-153">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="726f7-153">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-webhttpbinding.md)|<span data-ttu-id="726f7-154">Güvenlik özelliklerini gösteren [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="726f7-154">Represents the security capabilities of the [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="726f7-155">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="726f7-155">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.WebHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WebHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [<span data-ttu-id="726f7-156">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="726f7-156">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="726f7-157">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="726f7-157">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="726f7-158">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="726f7-158">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="726f7-159">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="726f7-159">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="726f7-160">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="726f7-160">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
- [<span data-ttu-id="726f7-161">WCF Web HTTP Programlama Modeli</span><span class="sxs-lookup"><span data-stu-id="726f7-161">WCF Web HTTP Programming Model</span></span>](../../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)

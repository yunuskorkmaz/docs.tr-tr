---
title: <transport> , <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 692befa3-8b0b-4ec5-b601-755874e98eb0
ms.openlocfilehash: a1540b53d4af76141c1daee60a6bddbbecd9d6da
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59153874"
---
# <a name="transport-of-ws2007httpbinding"></a><span data-ttu-id="79a15-102">\<Aktarım >, \<ws2007HttpBinding ></span><span class="sxs-lookup"><span data-stu-id="79a15-102">\<transport> of \<ws2007HttpBinding></span></span>
<span data-ttu-id="79a15-103">HTTP taşıma için kimlik doğrulama ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="79a15-103">Defines authentication settings for the HTTP transport.</span></span>  
  
 <span data-ttu-id="79a15-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="79a15-104">\<system.serviceModel></span></span>  
<span data-ttu-id="79a15-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="79a15-105">\<bindings></span></span>  
<span data-ttu-id="79a15-106">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="79a15-106">\<ws2007HttpBinding></span></span>  
<span data-ttu-id="79a15-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="79a15-107">\<binding></span></span>  
<span data-ttu-id="79a15-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="79a15-108">\<security></span></span>  
<span data-ttu-id="79a15-109">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="79a15-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79a15-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="79a15-110">Syntax</span></span>  
  
```xml  
<transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
           proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
           realm="string" />
```  
  
## <a name="type"></a><span data-ttu-id="79a15-111">Tür</span><span class="sxs-lookup"><span data-stu-id="79a15-111">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="79a15-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="79a15-112">Attributes and Elements</span></span>  
 <span data-ttu-id="79a15-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="79a15-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="79a15-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="79a15-114">Attributes</span></span>  
  
|<span data-ttu-id="79a15-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="79a15-115">Attribute</span></span>|<span data-ttu-id="79a15-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="79a15-116">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="79a15-117">Bir hizmete istemcinin kimliğini doğrulamak için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="79a15-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="79a15-118">Bu öznitelik türünde <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="79a15-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="79a15-119">Bir etki alanı Ara sunucusu istemcinin kimliğini doğrulamak için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="79a15-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="79a15-120">Bu öznitelik türünde <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="79a15-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="79a15-121">Özet veya temel kimlik doğrulaması için kimlik doğrulaması bölgesi.</span><span class="sxs-lookup"><span data-stu-id="79a15-121">The authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="79a15-122">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="79a15-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="79a15-123">Bir kimlik doğrulaması bölgesi, kimlik doğrulaması yapan bir ana bilgisayar adı en az belirtir.</span><span class="sxs-lookup"><span data-stu-id="79a15-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="79a15-124">Ayrıca, erişime sahip kullanıcılar bir koleksiyonu da belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="79a15-124">It can also specify a collection of users who have access.</span></span> <span data-ttu-id="79a15-125">Bir kullanıcı kimlik doğrulaması bölgesi, birkaç olası kullanıcı adları ve parolalar hangisinin kullanılacağını belirlemek için sorgulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="79a15-125">A user can query the authentication realm to determine which one of the several possible usernames and passwords can be used.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="79a15-126">clientCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="79a15-126">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="79a15-127">Değer</span><span class="sxs-lookup"><span data-stu-id="79a15-127">Value</span></span>|<span data-ttu-id="79a15-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="79a15-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="79a15-129">Yok.</span><span class="sxs-lookup"><span data-stu-id="79a15-129">None</span></span>|<span data-ttu-id="79a15-130">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="79a15-130">Security is disabled.</span></span>|  
|<span data-ttu-id="79a15-131">Temel</span><span class="sxs-lookup"><span data-stu-id="79a15-131">Basic</span></span>|<span data-ttu-id="79a15-132">Temel kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="79a15-132">Uses basic authentication.</span></span>|  
|<span data-ttu-id="79a15-133">Özet</span><span class="sxs-lookup"><span data-stu-id="79a15-133">Digest</span></span>|<span data-ttu-id="79a15-134">Özet kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="79a15-134">Uses digest authentication.</span></span>|  
|<span data-ttu-id="79a15-135">NTLM</span><span class="sxs-lookup"><span data-stu-id="79a15-135">Ntlm</span></span>|<span data-ttu-id="79a15-136">Bir Windows etki alanı ile bir geri dönüş olarak NTLM kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="79a15-136">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="79a15-137">Windows</span><span class="sxs-lookup"><span data-stu-id="79a15-137">Windows</span></span>|<span data-ttu-id="79a15-138">Tümleşik Windows kimlik doğrulaması olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="79a15-138">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="79a15-139">Sertifika</span><span class="sxs-lookup"><span data-stu-id="79a15-139">Certificate</span></span>|<span data-ttu-id="79a15-140">İstemcinin kimliğini doğrulamak için X.509 sertifikaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="79a15-140">Uses X.509 certificates to authenticate the client.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="79a15-141">proxyCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="79a15-141">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="79a15-142">Değer</span><span class="sxs-lookup"><span data-stu-id="79a15-142">Value</span></span>|<span data-ttu-id="79a15-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="79a15-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="79a15-144">Yok.</span><span class="sxs-lookup"><span data-stu-id="79a15-144">None</span></span>|<span data-ttu-id="79a15-145">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="79a15-145">Security is disabled.</span></span>|  
|<span data-ttu-id="79a15-146">Temel</span><span class="sxs-lookup"><span data-stu-id="79a15-146">Basic</span></span>|<span data-ttu-id="79a15-147">Temel kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="79a15-147">Uses basic authentication.</span></span>|  
|<span data-ttu-id="79a15-148">Özet</span><span class="sxs-lookup"><span data-stu-id="79a15-148">Digest</span></span>|<span data-ttu-id="79a15-149">Özet kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="79a15-149">Uses digest authentication.</span></span>|  
|<span data-ttu-id="79a15-150">NTLM</span><span class="sxs-lookup"><span data-stu-id="79a15-150">Ntlm</span></span>|<span data-ttu-id="79a15-151">Bir Windows etki alanı ile bir geri dönüş olarak NTLM kullanır.</span><span class="sxs-lookup"><span data-stu-id="79a15-151">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="79a15-152">Windows</span><span class="sxs-lookup"><span data-stu-id="79a15-152">Windows</span></span>|<span data-ttu-id="79a15-153">Tümleşik Windows kimlik doğrulaması olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="79a15-153">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="79a15-154">Sertifika</span><span class="sxs-lookup"><span data-stu-id="79a15-154">Certificate</span></span>|<span data-ttu-id="79a15-155">İstemcinin kimliğini doğrulamak için X.509 sertifikaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="79a15-155">Uses X.509 certificates to authenticate the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="79a15-156">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="79a15-156">Child Elements</span></span>  
 <span data-ttu-id="79a15-157">None</span><span class="sxs-lookup"><span data-stu-id="79a15-157">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="79a15-158">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="79a15-158">Parent Elements</span></span>  
  
|<span data-ttu-id="79a15-159">Öğe</span><span class="sxs-lookup"><span data-stu-id="79a15-159">Element</span></span>|<span data-ttu-id="79a15-160">Açıklama</span><span class="sxs-lookup"><span data-stu-id="79a15-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="79a15-161">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="79a15-161">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-ws2007httpbinding.md)|<span data-ttu-id="79a15-162">Güvenlik özelliklerini gösteren [ \<ws2007HttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="79a15-162">Represents the security capabilities of the [\<ws2007HttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="79a15-163">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="79a15-163">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpTransportSecurityElement>
- [<span data-ttu-id="79a15-164">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="79a15-164">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="79a15-165">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="79a15-165">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="79a15-166">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="79a15-166">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="79a15-167">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="79a15-167">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="79a15-168">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="79a15-168">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)

---
title: <transport> , <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 692befa3-8b0b-4ec5-b601-755874e98eb0
ms.openlocfilehash: b8f84d0ed6c6248e72e3353675c9da96a0678ae6
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55273312"
---
# <a name="transport-of-ws2007httpbinding"></a><span data-ttu-id="9976d-102">\<Aktarım >, \<ws2007HttpBinding ></span><span class="sxs-lookup"><span data-stu-id="9976d-102">\<transport> of \<ws2007HttpBinding></span></span>
<span data-ttu-id="9976d-103">HTTP taşıma için kimlik doğrulama ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9976d-103">Defines authentication settings for the HTTP transport.</span></span>  
  
 <span data-ttu-id="9976d-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="9976d-104">\<system.serviceModel></span></span>  
<span data-ttu-id="9976d-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="9976d-105">\<bindings></span></span>  
<span data-ttu-id="9976d-106">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="9976d-106">\<ws2007HttpBinding></span></span>  
<span data-ttu-id="9976d-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="9976d-107">\<binding></span></span>  
<span data-ttu-id="9976d-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="9976d-108">\<security></span></span>  
<span data-ttu-id="9976d-109">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="9976d-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9976d-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9976d-110">Syntax</span></span>  
  
```xml  
<transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
           proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
           realm="string" />
```  
  
## <a name="type"></a><span data-ttu-id="9976d-111">Tür</span><span class="sxs-lookup"><span data-stu-id="9976d-111">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9976d-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9976d-112">Attributes and Elements</span></span>  
 <span data-ttu-id="9976d-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9976d-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9976d-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9976d-114">Attributes</span></span>  
  
|<span data-ttu-id="9976d-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9976d-115">Attribute</span></span>|<span data-ttu-id="9976d-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9976d-116">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="9976d-117">Bir hizmete istemcinin kimliğini doğrulamak için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9976d-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="9976d-118">Bu öznitelik türünde <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="9976d-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="9976d-119">Bir etki alanı Ara sunucusu istemcinin kimliğini doğrulamak için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9976d-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="9976d-120">Bu öznitelik türünde <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="9976d-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="9976d-121">Özet veya temel kimlik doğrulaması için kimlik doğrulaması bölgesi.</span><span class="sxs-lookup"><span data-stu-id="9976d-121">The authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="9976d-122">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="9976d-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="9976d-123">Bir kimlik doğrulaması bölgesi, kimlik doğrulaması yapan bir ana bilgisayar adı en az belirtir.</span><span class="sxs-lookup"><span data-stu-id="9976d-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="9976d-124">Ayrıca, erişime sahip kullanıcılar bir koleksiyonu da belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9976d-124">It can also specify a collection of users who have access.</span></span> <span data-ttu-id="9976d-125">Bir kullanıcı kimlik doğrulaması bölgesi, birkaç olası kullanıcı adları ve parolalar hangisinin kullanılacağını belirlemek için sorgulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9976d-125">A user can query the authentication realm to determine which one of the several possible usernames and passwords can be used.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="9976d-126">clientCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="9976d-126">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="9976d-127">Değer</span><span class="sxs-lookup"><span data-stu-id="9976d-127">Value</span></span>|<span data-ttu-id="9976d-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9976d-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9976d-129">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="9976d-129">None</span></span>|<span data-ttu-id="9976d-130">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="9976d-130">Security is disabled.</span></span>|  
|<span data-ttu-id="9976d-131">Temel</span><span class="sxs-lookup"><span data-stu-id="9976d-131">Basic</span></span>|<span data-ttu-id="9976d-132">Temel kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="9976d-132">Uses basic authentication.</span></span>|  
|<span data-ttu-id="9976d-133">Özet</span><span class="sxs-lookup"><span data-stu-id="9976d-133">Digest</span></span>|<span data-ttu-id="9976d-134">Özet kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="9976d-134">Uses digest authentication.</span></span>|  
|<span data-ttu-id="9976d-135">NTLM</span><span class="sxs-lookup"><span data-stu-id="9976d-135">Ntlm</span></span>|<span data-ttu-id="9976d-136">Bir Windows etki alanı ile bir geri dönüş olarak NTLM kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="9976d-136">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="9976d-137">Windows</span><span class="sxs-lookup"><span data-stu-id="9976d-137">Windows</span></span>|<span data-ttu-id="9976d-138">Tümleşik Windows kimlik doğrulaması olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="9976d-138">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="9976d-139">Sertifika</span><span class="sxs-lookup"><span data-stu-id="9976d-139">Certificate</span></span>|<span data-ttu-id="9976d-140">İstemcinin kimliğini doğrulamak için X.509 sertifikaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="9976d-140">Uses X.509 certificates to authenticate the client.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="9976d-141">proxyCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="9976d-141">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="9976d-142">Değer</span><span class="sxs-lookup"><span data-stu-id="9976d-142">Value</span></span>|<span data-ttu-id="9976d-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9976d-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9976d-144">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="9976d-144">None</span></span>|<span data-ttu-id="9976d-145">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="9976d-145">Security is disabled.</span></span>|  
|<span data-ttu-id="9976d-146">Temel</span><span class="sxs-lookup"><span data-stu-id="9976d-146">Basic</span></span>|<span data-ttu-id="9976d-147">Temel kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="9976d-147">Uses basic authentication.</span></span>|  
|<span data-ttu-id="9976d-148">Özet</span><span class="sxs-lookup"><span data-stu-id="9976d-148">Digest</span></span>|<span data-ttu-id="9976d-149">Özet kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="9976d-149">Uses digest authentication.</span></span>|  
|<span data-ttu-id="9976d-150">NTLM</span><span class="sxs-lookup"><span data-stu-id="9976d-150">Ntlm</span></span>|<span data-ttu-id="9976d-151">Bir Windows etki alanı ile bir geri dönüş olarak NTLM kullanır.</span><span class="sxs-lookup"><span data-stu-id="9976d-151">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="9976d-152">Windows</span><span class="sxs-lookup"><span data-stu-id="9976d-152">Windows</span></span>|<span data-ttu-id="9976d-153">Tümleşik Windows kimlik doğrulaması olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="9976d-153">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="9976d-154">Sertifika</span><span class="sxs-lookup"><span data-stu-id="9976d-154">Certificate</span></span>|<span data-ttu-id="9976d-155">İstemcinin kimliğini doğrulamak için X.509 sertifikaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="9976d-155">Uses X.509 certificates to authenticate the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9976d-156">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9976d-156">Child Elements</span></span>  
 <span data-ttu-id="9976d-157">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="9976d-157">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9976d-158">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9976d-158">Parent Elements</span></span>  
  
|<span data-ttu-id="9976d-159">Öğe</span><span class="sxs-lookup"><span data-stu-id="9976d-159">Element</span></span>|<span data-ttu-id="9976d-160">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9976d-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9976d-161">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="9976d-161">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-ws2007httpbinding.md)|<span data-ttu-id="9976d-162">Güvenlik özelliklerini gösteren [ \<ws2007HttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="9976d-162">Represents the security capabilities of the [\<ws2007HttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9976d-163">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9976d-163">See also</span></span>
- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpTransportSecurityElement>
- [<span data-ttu-id="9976d-164">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="9976d-164">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="9976d-165">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="9976d-165">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="9976d-166">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="9976d-166">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="9976d-167">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="9976d-167">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="9976d-168">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="9976d-168">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)

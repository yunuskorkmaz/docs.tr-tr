---
title: '&lt;ws2007HttpBinding&gt; &lt;taşıma&gt;'
ms.date: 03/30/2017
ms.assetid: 692befa3-8b0b-4ec5-b601-755874e98eb0
ms.openlocfilehash: 3be9d4e64e63b32156cb64257f5bed8230cee3aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33350955"
---
# <a name="lttransportgt-of-ltws2007httpbindinggt"></a><span data-ttu-id="5d826-102">&lt;ws2007HttpBinding&gt; &lt;taşıma&gt;</span><span class="sxs-lookup"><span data-stu-id="5d826-102">&lt;transport&gt; of &lt;ws2007HttpBinding&gt;</span></span>
<span data-ttu-id="5d826-103">HTTP taşıma için kimlik doğrulama ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5d826-103">Defines authentication settings for the HTTP transport.</span></span>  
  
 <span data-ttu-id="5d826-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="5d826-104">\<system.serviceModel></span></span>  
<span data-ttu-id="5d826-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="5d826-105">\<bindings></span></span>  
<span data-ttu-id="5d826-106">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="5d826-106">\<ws2007HttpBinding></span></span>  
<span data-ttu-id="5d826-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="5d826-107">\<binding></span></span>  
<span data-ttu-id="5d826-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="5d826-108">\<security></span></span>  
<span data-ttu-id="5d826-109">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="5d826-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d826-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5d826-110">Syntax</span></span>  
  
```  
transport clientCredentialType =   
       "Basic/Certificate/Digest/None/Ntlm/Windows"  
       proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
       realm="string"   
```  
  
## <a name="type"></a><span data-ttu-id="5d826-111">Tür</span><span class="sxs-lookup"><span data-stu-id="5d826-111">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5d826-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5d826-112">Attributes and Elements</span></span>  
 <span data-ttu-id="5d826-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5d826-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5d826-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5d826-114">Attributes</span></span>  
  
|<span data-ttu-id="5d826-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5d826-115">Attribute</span></span>|<span data-ttu-id="5d826-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5d826-116">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="5d826-117">Hizmeti için istemci kimlik doğrulaması için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5d826-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="5d826-118">Bu öznitelik türünde <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="5d826-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="5d826-119">Bir etki alanı Ara sunucu için istemci kimlik doğrulaması için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5d826-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="5d826-120">Bu öznitelik türünde <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="5d826-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="5d826-121">Özet veya temel kimlik doğrulaması için kimlik doğrulaması bölgesi.</span><span class="sxs-lookup"><span data-stu-id="5d826-121">The authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="5d826-122">Varsayılan boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="5d826-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="5d826-123">Bir kimlik doğrulaması bölgesi, en az kimlik doğrulaması yapan ana bilgisayar adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5d826-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="5d826-124">Ayrıca, erişimi olan kullanıcıların koleksiyonu de belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d826-124">It can also specify a collection of users who have access.</span></span> <span data-ttu-id="5d826-125">Bir kullanıcı, birkaç olası kullanıcı adları ve parolalar hangisinin kullanılacağını belirlemek için kimlik doğrulaması bölgesi sorgulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d826-125">A user can query the authentication realm to determine which one of the several possible usernames and passwords can be used.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="5d826-126">clientCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="5d826-126">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="5d826-127">Değer</span><span class="sxs-lookup"><span data-stu-id="5d826-127">Value</span></span>|<span data-ttu-id="5d826-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5d826-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5d826-129">Yok.</span><span class="sxs-lookup"><span data-stu-id="5d826-129">None</span></span>|<span data-ttu-id="5d826-130">Güvenliği devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="5d826-130">Security is disabled.</span></span>|  
|<span data-ttu-id="5d826-131">Temel</span><span class="sxs-lookup"><span data-stu-id="5d826-131">Basic</span></span>|<span data-ttu-id="5d826-132">Temel kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="5d826-132">Uses basic authentication.</span></span>|  
|<span data-ttu-id="5d826-133">Özet</span><span class="sxs-lookup"><span data-stu-id="5d826-133">Digest</span></span>|<span data-ttu-id="5d826-134">Özet kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="5d826-134">Uses digest authentication.</span></span>|  
|<span data-ttu-id="5d826-135">NTLM</span><span class="sxs-lookup"><span data-stu-id="5d826-135">Ntlm</span></span>|<span data-ttu-id="5d826-136">Bir Windows etki alanı ile bir geri dönüş olarak NTLM kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="5d826-136">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="5d826-137">Windows</span><span class="sxs-lookup"><span data-stu-id="5d826-137">Windows</span></span>|<span data-ttu-id="5d826-138">Tümleşik Windows kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="5d826-138">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="5d826-139">Sertifika</span><span class="sxs-lookup"><span data-stu-id="5d826-139">Certificate</span></span>|<span data-ttu-id="5d826-140">İstemci kimlik doğrulaması için X.509 sertifikaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="5d826-140">Uses X.509 certificates to authenticate the client.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="5d826-141">proxyCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="5d826-141">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="5d826-142">Değer</span><span class="sxs-lookup"><span data-stu-id="5d826-142">Value</span></span>|<span data-ttu-id="5d826-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5d826-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5d826-144">Yok.</span><span class="sxs-lookup"><span data-stu-id="5d826-144">None</span></span>|<span data-ttu-id="5d826-145">Güvenliği devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="5d826-145">Security is disabled.</span></span>|  
|<span data-ttu-id="5d826-146">Temel</span><span class="sxs-lookup"><span data-stu-id="5d826-146">Basic</span></span>|<span data-ttu-id="5d826-147">Temel kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="5d826-147">Uses basic authentication.</span></span>|  
|<span data-ttu-id="5d826-148">Özet</span><span class="sxs-lookup"><span data-stu-id="5d826-148">Digest</span></span>|<span data-ttu-id="5d826-149">Özet kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="5d826-149">Uses digest authentication.</span></span>|  
|<span data-ttu-id="5d826-150">NTLM</span><span class="sxs-lookup"><span data-stu-id="5d826-150">Ntlm</span></span>|<span data-ttu-id="5d826-151">Bir Windows etki alanı ile bir geri dönüş olarak NTLM kullanır.</span><span class="sxs-lookup"><span data-stu-id="5d826-151">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="5d826-152">Windows</span><span class="sxs-lookup"><span data-stu-id="5d826-152">Windows</span></span>|<span data-ttu-id="5d826-153">Tümleşik Windows kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="5d826-153">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="5d826-154">Sertifika</span><span class="sxs-lookup"><span data-stu-id="5d826-154">Certificate</span></span>|<span data-ttu-id="5d826-155">İstemci kimlik doğrulaması için X.509 sertifikaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="5d826-155">Uses X.509 certificates to authenticate the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5d826-156">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5d826-156">Child Elements</span></span>  
 <span data-ttu-id="5d826-157">Yok.</span><span class="sxs-lookup"><span data-stu-id="5d826-157">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5d826-158">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5d826-158">Parent Elements</span></span>  
  
|<span data-ttu-id="5d826-159">Öğe</span><span class="sxs-lookup"><span data-stu-id="5d826-159">Element</span></span>|<span data-ttu-id="5d826-160">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5d826-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5d826-161">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="5d826-161">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-ws2007httpbinding.md)|<span data-ttu-id="5d826-162">Güvenlik özellikleri temsil eden [ \<ws2007HttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="5d826-162">Represents the security capabilities of the [\<ws2007HttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5d826-163">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5d826-163">See Also</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpTransportSecurityElement>  
 [<span data-ttu-id="5d826-164">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="5d826-164">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="5d826-165">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="5d826-165">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="5d826-166">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="5d826-166">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="5d826-167">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="5d826-167">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="5d826-168">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="5d826-168">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)

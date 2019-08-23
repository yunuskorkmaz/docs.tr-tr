---
title: <transport> / <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 692befa3-8b0b-4ec5-b601-755874e98eb0
ms.openlocfilehash: ce8b2acb7d87b094958e20ca0b6cca9fc8266a8d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911981"
---
# <a name="transport-of-ws2007httpbinding"></a><span data-ttu-id="e9aba-102">\<\<WS2007HttpBinding > taşıma ></span><span class="sxs-lookup"><span data-stu-id="e9aba-102">\<transport> of \<ws2007HttpBinding></span></span>
<span data-ttu-id="e9aba-103">HTTP taşıması için kimlik doğrulama ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e9aba-103">Defines authentication settings for the HTTP transport.</span></span>  
  
 <span data-ttu-id="e9aba-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e9aba-104">\<system.serviceModel></span></span>  
<span data-ttu-id="e9aba-105">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="e9aba-105">\<bindings></span></span>  
<span data-ttu-id="e9aba-106">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="e9aba-106">\<ws2007HttpBinding></span></span>  
<span data-ttu-id="e9aba-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="e9aba-107">\<binding></span></span>  
<span data-ttu-id="e9aba-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="e9aba-108">\<security></span></span>  
<span data-ttu-id="e9aba-109">\<Taşıma ></span><span class="sxs-lookup"><span data-stu-id="e9aba-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9aba-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e9aba-110">Syntax</span></span>  
  
```xml  
<transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
           proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
           realm="string" />
```  
  
## <a name="type"></a><span data-ttu-id="e9aba-111">Tür</span><span class="sxs-lookup"><span data-stu-id="e9aba-111">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e9aba-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e9aba-112">Attributes and Elements</span></span>  
 <span data-ttu-id="e9aba-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e9aba-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e9aba-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e9aba-114">Attributes</span></span>  
  
|<span data-ttu-id="e9aba-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e9aba-115">Attribute</span></span>|<span data-ttu-id="e9aba-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e9aba-116">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="e9aba-117">Hizmetin istemcinin kimliğini doğrulamak için kullanılan kimlik bilgisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e9aba-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="e9aba-118">Bu öznitelik türü <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="e9aba-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="e9aba-119">Bir etki alanı ara sunucusu için istemcinin kimliğini doğrulamak için kullanılan kimlik bilgisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e9aba-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="e9aba-120">Bu öznitelik türü <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="e9aba-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="e9aba-121">Özet veya temel kimlik doğrulaması için kimlik doğrulama bölgesi.</span><span class="sxs-lookup"><span data-stu-id="e9aba-121">The authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="e9aba-122">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="e9aba-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="e9aba-123">Kimlik doğrulama bölgesi, kimlik doğrulamasını gerçekleştiren konağın en azından adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e9aba-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="e9aba-124">Ayrıca, erişimi olan bir kullanıcı koleksiyonu da belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="e9aba-124">It can also specify a collection of users who have access.</span></span> <span data-ttu-id="e9aba-125">Kullanıcı, birkaç olası Kullanıcı adı ve parolanın kullanılabileceğini belirleyebilmek için kimlik doğrulama bölgesini sorgulayabilir.</span><span class="sxs-lookup"><span data-stu-id="e9aba-125">A user can query the authentication realm to determine which one of the several possible usernames and passwords can be used.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="e9aba-126">clientCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="e9aba-126">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="e9aba-127">Değer</span><span class="sxs-lookup"><span data-stu-id="e9aba-127">Value</span></span>|<span data-ttu-id="e9aba-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e9aba-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e9aba-129">Yok.</span><span class="sxs-lookup"><span data-stu-id="e9aba-129">None</span></span>|<span data-ttu-id="e9aba-130">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="e9aba-130">Security is disabled.</span></span>|  
|<span data-ttu-id="e9aba-131">Temel</span><span class="sxs-lookup"><span data-stu-id="e9aba-131">Basic</span></span>|<span data-ttu-id="e9aba-132">Temel kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="e9aba-132">Uses basic authentication.</span></span>|  
|<span data-ttu-id="e9aba-133">Bilgisi</span><span class="sxs-lookup"><span data-stu-id="e9aba-133">Digest</span></span>|<span data-ttu-id="e9aba-134">Özet kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="e9aba-134">Uses digest authentication.</span></span>|  
|<span data-ttu-id="e9aba-135">NT</span><span class="sxs-lookup"><span data-stu-id="e9aba-135">Ntlm</span></span>|<span data-ttu-id="e9aba-136">Windows etki alanı ile geri dönüş olarak NTLM kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="e9aba-136">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="e9aba-137">Windows</span><span class="sxs-lookup"><span data-stu-id="e9aba-137">Windows</span></span>|<span data-ttu-id="e9aba-138">Tümleşik Windows kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="e9aba-138">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="e9aba-139">Sertifika</span><span class="sxs-lookup"><span data-stu-id="e9aba-139">Certificate</span></span>|<span data-ttu-id="e9aba-140">İstemcinin kimliğini doğrulamak için X. 509.440 sertifikalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="e9aba-140">Uses X.509 certificates to authenticate the client.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="e9aba-141">proxyCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="e9aba-141">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="e9aba-142">Değer</span><span class="sxs-lookup"><span data-stu-id="e9aba-142">Value</span></span>|<span data-ttu-id="e9aba-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e9aba-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e9aba-144">Yok.</span><span class="sxs-lookup"><span data-stu-id="e9aba-144">None</span></span>|<span data-ttu-id="e9aba-145">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="e9aba-145">Security is disabled.</span></span>|  
|<span data-ttu-id="e9aba-146">Temel</span><span class="sxs-lookup"><span data-stu-id="e9aba-146">Basic</span></span>|<span data-ttu-id="e9aba-147">Temel kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="e9aba-147">Uses basic authentication.</span></span>|  
|<span data-ttu-id="e9aba-148">Bilgisi</span><span class="sxs-lookup"><span data-stu-id="e9aba-148">Digest</span></span>|<span data-ttu-id="e9aba-149">Özet kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="e9aba-149">Uses digest authentication.</span></span>|  
|<span data-ttu-id="e9aba-150">NT</span><span class="sxs-lookup"><span data-stu-id="e9aba-150">Ntlm</span></span>|<span data-ttu-id="e9aba-151">Windows etki alanı ile geri dönüş olarak NTLM kullanır.</span><span class="sxs-lookup"><span data-stu-id="e9aba-151">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="e9aba-152">Windows</span><span class="sxs-lookup"><span data-stu-id="e9aba-152">Windows</span></span>|<span data-ttu-id="e9aba-153">Tümleşik Windows kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="e9aba-153">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="e9aba-154">Sertifika</span><span class="sxs-lookup"><span data-stu-id="e9aba-154">Certificate</span></span>|<span data-ttu-id="e9aba-155">İstemcinin kimliğini doğrulamak için X. 509.440 sertifikalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="e9aba-155">Uses X.509 certificates to authenticate the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e9aba-156">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e9aba-156">Child Elements</span></span>  
 <span data-ttu-id="e9aba-157">Yok.</span><span class="sxs-lookup"><span data-stu-id="e9aba-157">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e9aba-158">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e9aba-158">Parent Elements</span></span>  
  
|<span data-ttu-id="e9aba-159">Öğe</span><span class="sxs-lookup"><span data-stu-id="e9aba-159">Element</span></span>|<span data-ttu-id="e9aba-160">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e9aba-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e9aba-161">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="e9aba-161">\<security></span></span>](security-of-ws2007httpbinding.md)|<span data-ttu-id="e9aba-162">WS2007HttpBinding > öğesinin güvenlik yeteneklerini [ \<](ws2007httpbinding.md) temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e9aba-162">Represents the security capabilities of the [\<ws2007HttpBinding>](ws2007httpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e9aba-163">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e9aba-163">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpTransportSecurityElement>
- [<span data-ttu-id="e9aba-164">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="e9aba-164">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="e9aba-165">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="e9aba-165">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="e9aba-166">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e9aba-166">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="e9aba-167">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="e9aba-167">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="e9aba-168">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="e9aba-168">\<binding></span></span>](../../../misc/binding.md)

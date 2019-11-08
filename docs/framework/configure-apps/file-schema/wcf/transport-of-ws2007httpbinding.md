---
title: <transport> / <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 692befa3-8b0b-4ec5-b601-755874e98eb0
ms.openlocfilehash: 0cd20c607b0c4ddd3ecfd806d38ba63b4a5c5a25
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73732768"
---
# <a name="transport-of-ws2007httpbinding"></a><span data-ttu-id="272b4-102">\<ws2007HttpBinding \<taşıma > ></span><span class="sxs-lookup"><span data-stu-id="272b4-102">\<transport> of \<ws2007HttpBinding></span></span>
<span data-ttu-id="272b4-103">HTTP taşıması için kimlik doğrulama ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="272b4-103">Defines authentication settings for the HTTP transport.</span></span>  
  
<span data-ttu-id="272b4-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="272b4-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="272b4-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="272b4-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="272b4-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlamaları >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="272b4-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="272b4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<ws2007HttpBinding >** ](ws2007httpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="272b4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007HttpBinding>**](ws2007httpbinding.md)</span></span>\
<span data-ttu-id="272b4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="272b4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="272b4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<güvenlik >** ](security-of-ws2007httpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="272b4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-ws2007httpbinding.md)</span></span>\
<span data-ttu-id="272b4-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<taşıma >**</span><span class="sxs-lookup"><span data-stu-id="272b4-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="272b4-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="272b4-111">Syntax</span></span>  
  
```xml  
<transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
           proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
           realm="string" />
```  
  
## <a name="type"></a><span data-ttu-id="272b4-112">Tür</span><span class="sxs-lookup"><span data-stu-id="272b4-112">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="272b4-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="272b4-113">Attributes and Elements</span></span>  
 <span data-ttu-id="272b4-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="272b4-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="272b4-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="272b4-115">Attributes</span></span>  
  
|<span data-ttu-id="272b4-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="272b4-116">Attribute</span></span>|<span data-ttu-id="272b4-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="272b4-117">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="272b4-118">Hizmetin istemcinin kimliğini doğrulamak için kullanılan kimlik bilgisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="272b4-118">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="272b4-119">Bu öznitelik <xref:System.ServiceModel.HttpClientCredentialType>türündedir.</span><span class="sxs-lookup"><span data-stu-id="272b4-119">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="272b4-120">Bir etki alanı ara sunucusu için istemcinin kimliğini doğrulamak için kullanılan kimlik bilgisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="272b4-120">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="272b4-121">Bu öznitelik <xref:System.ServiceModel.HttpProxyCredentialType>türündedir.</span><span class="sxs-lookup"><span data-stu-id="272b4-121">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="272b4-122">Özet veya temel kimlik doğrulaması için kimlik doğrulama bölgesi.</span><span class="sxs-lookup"><span data-stu-id="272b4-122">The authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="272b4-123">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="272b4-123">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="272b4-124">Kimlik doğrulama bölgesi, kimlik doğrulamasını gerçekleştiren konağın en azından adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="272b4-124">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="272b4-125">Ayrıca, erişimi olan bir kullanıcı koleksiyonu da belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="272b4-125">It can also specify a collection of users who have access.</span></span> <span data-ttu-id="272b4-126">Kullanıcı, birkaç olası Kullanıcı adı ve parolanın kullanılabileceğini belirleyebilmek için kimlik doğrulama bölgesini sorgulayabilir.</span><span class="sxs-lookup"><span data-stu-id="272b4-126">A user can query the authentication realm to determine which one of the several possible usernames and passwords can be used.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="272b4-127">clientCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="272b4-127">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="272b4-128">Değer</span><span class="sxs-lookup"><span data-stu-id="272b4-128">Value</span></span>|<span data-ttu-id="272b4-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="272b4-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="272b4-130">Yok.</span><span class="sxs-lookup"><span data-stu-id="272b4-130">None</span></span>|<span data-ttu-id="272b4-131">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="272b4-131">Security is disabled.</span></span>|  
|<span data-ttu-id="272b4-132">Temel</span><span class="sxs-lookup"><span data-stu-id="272b4-132">Basic</span></span>|<span data-ttu-id="272b4-133">Temel kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="272b4-133">Uses basic authentication.</span></span>|  
|<span data-ttu-id="272b4-134">bilgisi</span><span class="sxs-lookup"><span data-stu-id="272b4-134">Digest</span></span>|<span data-ttu-id="272b4-135">Özet kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="272b4-135">Uses digest authentication.</span></span>|  
|<span data-ttu-id="272b4-136">NT</span><span class="sxs-lookup"><span data-stu-id="272b4-136">Ntlm</span></span>|<span data-ttu-id="272b4-137">Windows etki alanı ile geri dönüş olarak NTLM kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="272b4-137">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="272b4-138">Windows</span><span class="sxs-lookup"><span data-stu-id="272b4-138">Windows</span></span>|<span data-ttu-id="272b4-139">Tümleşik Windows kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="272b4-139">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="272b4-140">Sertifika</span><span class="sxs-lookup"><span data-stu-id="272b4-140">Certificate</span></span>|<span data-ttu-id="272b4-141">İstemcinin kimliğini doğrulamak için X. 509.440 sertifikalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="272b4-141">Uses X.509 certificates to authenticate the client.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="272b4-142">proxyCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="272b4-142">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="272b4-143">Değer</span><span class="sxs-lookup"><span data-stu-id="272b4-143">Value</span></span>|<span data-ttu-id="272b4-144">Açıklama</span><span class="sxs-lookup"><span data-stu-id="272b4-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="272b4-145">Yok.</span><span class="sxs-lookup"><span data-stu-id="272b4-145">None</span></span>|<span data-ttu-id="272b4-146">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="272b4-146">Security is disabled.</span></span>|  
|<span data-ttu-id="272b4-147">Temel</span><span class="sxs-lookup"><span data-stu-id="272b4-147">Basic</span></span>|<span data-ttu-id="272b4-148">Temel kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="272b4-148">Uses basic authentication.</span></span>|  
|<span data-ttu-id="272b4-149">bilgisi</span><span class="sxs-lookup"><span data-stu-id="272b4-149">Digest</span></span>|<span data-ttu-id="272b4-150">Özet kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="272b4-150">Uses digest authentication.</span></span>|  
|<span data-ttu-id="272b4-151">NT</span><span class="sxs-lookup"><span data-stu-id="272b4-151">Ntlm</span></span>|<span data-ttu-id="272b4-152">Windows etki alanı ile geri dönüş olarak NTLM kullanır.</span><span class="sxs-lookup"><span data-stu-id="272b4-152">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="272b4-153">Windows</span><span class="sxs-lookup"><span data-stu-id="272b4-153">Windows</span></span>|<span data-ttu-id="272b4-154">Tümleşik Windows kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="272b4-154">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="272b4-155">Sertifika</span><span class="sxs-lookup"><span data-stu-id="272b4-155">Certificate</span></span>|<span data-ttu-id="272b4-156">İstemcinin kimliğini doğrulamak için X. 509.440 sertifikalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="272b4-156">Uses X.509 certificates to authenticate the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="272b4-157">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="272b4-157">Child Elements</span></span>  
 <span data-ttu-id="272b4-158">Yok.</span><span class="sxs-lookup"><span data-stu-id="272b4-158">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="272b4-159">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="272b4-159">Parent Elements</span></span>  
  
|<span data-ttu-id="272b4-160">Öğe</span><span class="sxs-lookup"><span data-stu-id="272b4-160">Element</span></span>|<span data-ttu-id="272b4-161">Açıklama</span><span class="sxs-lookup"><span data-stu-id="272b4-161">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="272b4-162">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="272b4-162">\<security></span></span>](security-of-ws2007httpbinding.md)|<span data-ttu-id="272b4-163">[\<ws2007HttpBinding >](ws2007httpbinding.md) öğesinin güvenlik yeteneklerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="272b4-163">Represents the security capabilities of the [\<ws2007HttpBinding>](ws2007httpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="272b4-164">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="272b4-164">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpTransportSecurityElement>
- [<span data-ttu-id="272b4-165">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="272b4-165">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="272b4-166">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="272b4-166">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="272b4-167">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="272b4-167">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="272b4-168">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="272b4-168">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="272b4-169">\< bağlama ></span><span class="sxs-lookup"><span data-stu-id="272b4-169">\<binding></span></span>](bindings.md)

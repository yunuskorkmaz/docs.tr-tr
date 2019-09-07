---
title: <transport> / <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 692befa3-8b0b-4ec5-b601-755874e98eb0
ms.openlocfilehash: 4ea60ccaba58bc0b3fa8f2263295bf1413d25e89
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399264"
---
# <a name="transport-of-ws2007httpbinding"></a><span data-ttu-id="4560b-102">\<\<WS2007HttpBinding > taşıma ></span><span class="sxs-lookup"><span data-stu-id="4560b-102">\<transport> of \<ws2007HttpBinding></span></span>
<span data-ttu-id="4560b-103">HTTP taşıması için kimlik doğrulama ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4560b-103">Defines authentication settings for the HTTP transport.</span></span>  
  
<span data-ttu-id="4560b-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="4560b-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="4560b-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="4560b-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="4560b-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlama >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="4560b-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="4560b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<ws2007HttpBinding >** ](ws2007httpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="4560b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007HttpBinding>**](ws2007httpbinding.md)</span></span>\
<span data-ttu-id="4560b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="4560b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="4560b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Güvenlik >** ](security-of-ws2007httpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="4560b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-ws2007httpbinding.md)</span></span>\
<span data-ttu-id="4560b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Taşıma >**</span><span class="sxs-lookup"><span data-stu-id="4560b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4560b-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4560b-111">Syntax</span></span>  
  
```xml  
<transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
           proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
           realm="string" />
```  
  
## <a name="type"></a><span data-ttu-id="4560b-112">Tür</span><span class="sxs-lookup"><span data-stu-id="4560b-112">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4560b-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4560b-113">Attributes and Elements</span></span>  
 <span data-ttu-id="4560b-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4560b-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4560b-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4560b-115">Attributes</span></span>  
  
|<span data-ttu-id="4560b-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4560b-116">Attribute</span></span>|<span data-ttu-id="4560b-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4560b-117">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="4560b-118">Hizmetin istemcinin kimliğini doğrulamak için kullanılan kimlik bilgisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4560b-118">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="4560b-119">Bu öznitelik türü <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="4560b-119">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="4560b-120">Bir etki alanı ara sunucusu için istemcinin kimliğini doğrulamak için kullanılan kimlik bilgisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4560b-120">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="4560b-121">Bu öznitelik türü <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="4560b-121">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="4560b-122">Özet veya temel kimlik doğrulaması için kimlik doğrulama bölgesi.</span><span class="sxs-lookup"><span data-stu-id="4560b-122">The authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="4560b-123">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="4560b-123">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="4560b-124">Kimlik doğrulama bölgesi, kimlik doğrulamasını gerçekleştiren konağın en azından adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4560b-124">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="4560b-125">Ayrıca, erişimi olan bir kullanıcı koleksiyonu da belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="4560b-125">It can also specify a collection of users who have access.</span></span> <span data-ttu-id="4560b-126">Kullanıcı, birkaç olası Kullanıcı adı ve parolanın kullanılabileceğini belirleyebilmek için kimlik doğrulama bölgesini sorgulayabilir.</span><span class="sxs-lookup"><span data-stu-id="4560b-126">A user can query the authentication realm to determine which one of the several possible usernames and passwords can be used.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="4560b-127">clientCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="4560b-127">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="4560b-128">Değer</span><span class="sxs-lookup"><span data-stu-id="4560b-128">Value</span></span>|<span data-ttu-id="4560b-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4560b-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4560b-130">Yok.</span><span class="sxs-lookup"><span data-stu-id="4560b-130">None</span></span>|<span data-ttu-id="4560b-131">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="4560b-131">Security is disabled.</span></span>|  
|<span data-ttu-id="4560b-132">Temel</span><span class="sxs-lookup"><span data-stu-id="4560b-132">Basic</span></span>|<span data-ttu-id="4560b-133">Temel kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="4560b-133">Uses basic authentication.</span></span>|  
|<span data-ttu-id="4560b-134">Bilgisi</span><span class="sxs-lookup"><span data-stu-id="4560b-134">Digest</span></span>|<span data-ttu-id="4560b-135">Özet kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="4560b-135">Uses digest authentication.</span></span>|  
|<span data-ttu-id="4560b-136">NT</span><span class="sxs-lookup"><span data-stu-id="4560b-136">Ntlm</span></span>|<span data-ttu-id="4560b-137">Windows etki alanı ile geri dönüş olarak NTLM kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="4560b-137">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="4560b-138">Windows</span><span class="sxs-lookup"><span data-stu-id="4560b-138">Windows</span></span>|<span data-ttu-id="4560b-139">Tümleşik Windows kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="4560b-139">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="4560b-140">Sertifika</span><span class="sxs-lookup"><span data-stu-id="4560b-140">Certificate</span></span>|<span data-ttu-id="4560b-141">İstemcinin kimliğini doğrulamak için X. 509.440 sertifikalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="4560b-141">Uses X.509 certificates to authenticate the client.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="4560b-142">proxyCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="4560b-142">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="4560b-143">Değer</span><span class="sxs-lookup"><span data-stu-id="4560b-143">Value</span></span>|<span data-ttu-id="4560b-144">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4560b-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4560b-145">Yok.</span><span class="sxs-lookup"><span data-stu-id="4560b-145">None</span></span>|<span data-ttu-id="4560b-146">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="4560b-146">Security is disabled.</span></span>|  
|<span data-ttu-id="4560b-147">Temel</span><span class="sxs-lookup"><span data-stu-id="4560b-147">Basic</span></span>|<span data-ttu-id="4560b-148">Temel kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="4560b-148">Uses basic authentication.</span></span>|  
|<span data-ttu-id="4560b-149">Bilgisi</span><span class="sxs-lookup"><span data-stu-id="4560b-149">Digest</span></span>|<span data-ttu-id="4560b-150">Özet kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="4560b-150">Uses digest authentication.</span></span>|  
|<span data-ttu-id="4560b-151">NT</span><span class="sxs-lookup"><span data-stu-id="4560b-151">Ntlm</span></span>|<span data-ttu-id="4560b-152">Windows etki alanı ile geri dönüş olarak NTLM kullanır.</span><span class="sxs-lookup"><span data-stu-id="4560b-152">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="4560b-153">Windows</span><span class="sxs-lookup"><span data-stu-id="4560b-153">Windows</span></span>|<span data-ttu-id="4560b-154">Tümleşik Windows kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="4560b-154">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="4560b-155">Sertifika</span><span class="sxs-lookup"><span data-stu-id="4560b-155">Certificate</span></span>|<span data-ttu-id="4560b-156">İstemcinin kimliğini doğrulamak için X. 509.440 sertifikalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="4560b-156">Uses X.509 certificates to authenticate the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4560b-157">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4560b-157">Child Elements</span></span>  
 <span data-ttu-id="4560b-158">Yok.</span><span class="sxs-lookup"><span data-stu-id="4560b-158">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4560b-159">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4560b-159">Parent Elements</span></span>  
  
|<span data-ttu-id="4560b-160">Öğe</span><span class="sxs-lookup"><span data-stu-id="4560b-160">Element</span></span>|<span data-ttu-id="4560b-161">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4560b-161">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4560b-162">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="4560b-162">\<security></span></span>](security-of-ws2007httpbinding.md)|<span data-ttu-id="4560b-163">WS2007HttpBinding > öğesinin güvenlik yeteneklerini [ \<](ws2007httpbinding.md) temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4560b-163">Represents the security capabilities of the [\<ws2007HttpBinding>](ws2007httpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4560b-164">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4560b-164">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpTransportSecurityElement>
- [<span data-ttu-id="4560b-165">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="4560b-165">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="4560b-166">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="4560b-166">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="4560b-167">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="4560b-167">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="4560b-168">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="4560b-168">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="4560b-169">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="4560b-169">\<binding></span></span>](../../../misc/binding.md)

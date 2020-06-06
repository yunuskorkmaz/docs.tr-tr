---
title: <transport> / <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 692befa3-8b0b-4ec5-b601-755874e98eb0
ms.openlocfilehash: 0cd20c607b0c4ddd3ecfd806d38ba63b4a5c5a25
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73732768"
---
# <a name="transport-of-ws2007httpbinding"></a><span data-ttu-id="0c999-102">\<transport> / \<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="0c999-102">\<transport> of \<ws2007HttpBinding></span></span>
<span data-ttu-id="0c999-103">HTTP taşıması için kimlik doğrulama ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0c999-103">Defines authentication settings for the HTTP transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007HttpBinding>**](ws2007httpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-ws2007httpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="0c999-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0c999-104">Syntax</span></span>  
  
```xml  
<transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
           proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
           realm="string" />
```  
  
## <a name="type"></a><span data-ttu-id="0c999-105">Tür</span><span class="sxs-lookup"><span data-stu-id="0c999-105">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0c999-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0c999-106">Attributes and Elements</span></span>  
 <span data-ttu-id="0c999-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0c999-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0c999-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0c999-108">Attributes</span></span>  
  
|<span data-ttu-id="0c999-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0c999-109">Attribute</span></span>|<span data-ttu-id="0c999-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0c999-110">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="0c999-111">Hizmetin istemcinin kimliğini doğrulamak için kullanılan kimlik bilgisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0c999-111">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="0c999-112">Bu öznitelik türü <xref:System.ServiceModel.HttpClientCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="0c999-112">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="0c999-113">Bir etki alanı ara sunucusu için istemcinin kimliğini doğrulamak için kullanılan kimlik bilgisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0c999-113">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="0c999-114">Bu öznitelik türü <xref:System.ServiceModel.HttpProxyCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="0c999-114">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="0c999-115">Özet veya temel kimlik doğrulaması için kimlik doğrulama bölgesi.</span><span class="sxs-lookup"><span data-stu-id="0c999-115">The authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="0c999-116">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="0c999-116">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="0c999-117">Kimlik doğrulama bölgesi, kimlik doğrulamasını gerçekleştiren konağın en azından adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0c999-117">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="0c999-118">Ayrıca, erişimi olan bir kullanıcı koleksiyonu da belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="0c999-118">It can also specify a collection of users who have access.</span></span> <span data-ttu-id="0c999-119">Kullanıcı, birkaç olası Kullanıcı adı ve parolanın kullanılabileceğini belirleyebilmek için kimlik doğrulama bölgesini sorgulayabilir.</span><span class="sxs-lookup"><span data-stu-id="0c999-119">A user can query the authentication realm to determine which one of the several possible usernames and passwords can be used.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="0c999-120">clientCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="0c999-120">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="0c999-121">Değer</span><span class="sxs-lookup"><span data-stu-id="0c999-121">Value</span></span>|<span data-ttu-id="0c999-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0c999-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0c999-123">Yok</span><span class="sxs-lookup"><span data-stu-id="0c999-123">None</span></span>|<span data-ttu-id="0c999-124">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="0c999-124">Security is disabled.</span></span>|  
|<span data-ttu-id="0c999-125">Temel</span><span class="sxs-lookup"><span data-stu-id="0c999-125">Basic</span></span>|<span data-ttu-id="0c999-126">Temel kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="0c999-126">Uses basic authentication.</span></span>|  
|<span data-ttu-id="0c999-127">Bilgisi</span><span class="sxs-lookup"><span data-stu-id="0c999-127">Digest</span></span>|<span data-ttu-id="0c999-128">Özet kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="0c999-128">Uses digest authentication.</span></span>|  
|<span data-ttu-id="0c999-129">NT</span><span class="sxs-lookup"><span data-stu-id="0c999-129">Ntlm</span></span>|<span data-ttu-id="0c999-130">Windows etki alanı ile geri dönüş olarak NTLM kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="0c999-130">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="0c999-131">Windows</span><span class="sxs-lookup"><span data-stu-id="0c999-131">Windows</span></span>|<span data-ttu-id="0c999-132">Tümleşik Windows kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="0c999-132">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="0c999-133">Sertifika</span><span class="sxs-lookup"><span data-stu-id="0c999-133">Certificate</span></span>|<span data-ttu-id="0c999-134">İstemcinin kimliğini doğrulamak için X. 509.440 sertifikalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="0c999-134">Uses X.509 certificates to authenticate the client.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="0c999-135">proxyCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="0c999-135">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="0c999-136">Değer</span><span class="sxs-lookup"><span data-stu-id="0c999-136">Value</span></span>|<span data-ttu-id="0c999-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0c999-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0c999-138">Yok</span><span class="sxs-lookup"><span data-stu-id="0c999-138">None</span></span>|<span data-ttu-id="0c999-139">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="0c999-139">Security is disabled.</span></span>|  
|<span data-ttu-id="0c999-140">Temel</span><span class="sxs-lookup"><span data-stu-id="0c999-140">Basic</span></span>|<span data-ttu-id="0c999-141">Temel kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="0c999-141">Uses basic authentication.</span></span>|  
|<span data-ttu-id="0c999-142">Bilgisi</span><span class="sxs-lookup"><span data-stu-id="0c999-142">Digest</span></span>|<span data-ttu-id="0c999-143">Özet kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="0c999-143">Uses digest authentication.</span></span>|  
|<span data-ttu-id="0c999-144">NT</span><span class="sxs-lookup"><span data-stu-id="0c999-144">Ntlm</span></span>|<span data-ttu-id="0c999-145">Windows etki alanı ile geri dönüş olarak NTLM kullanır.</span><span class="sxs-lookup"><span data-stu-id="0c999-145">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="0c999-146">Windows</span><span class="sxs-lookup"><span data-stu-id="0c999-146">Windows</span></span>|<span data-ttu-id="0c999-147">Tümleşik Windows kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="0c999-147">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="0c999-148">Sertifika</span><span class="sxs-lookup"><span data-stu-id="0c999-148">Certificate</span></span>|<span data-ttu-id="0c999-149">İstemcinin kimliğini doğrulamak için X. 509.440 sertifikalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="0c999-149">Uses X.509 certificates to authenticate the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0c999-150">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0c999-150">Child Elements</span></span>  
 <span data-ttu-id="0c999-151">Yok</span><span class="sxs-lookup"><span data-stu-id="0c999-151">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0c999-152">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0c999-152">Parent Elements</span></span>  
  
|<span data-ttu-id="0c999-153">Öğe</span><span class="sxs-lookup"><span data-stu-id="0c999-153">Element</span></span>|<span data-ttu-id="0c999-154">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0c999-154">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-ws2007httpbinding.md)|<span data-ttu-id="0c999-155">Öğesinin güvenlik yeteneklerini temsil eder [\<ws2007HttpBinding>](ws2007httpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="0c999-155">Represents the security capabilities of the [\<ws2007HttpBinding>](ws2007httpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0c999-156">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0c999-156">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpTransportSecurityElement>
- [<span data-ttu-id="0c999-157">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="0c999-157">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="0c999-158">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="0c999-158">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="0c999-159">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="0c999-159">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="0c999-160">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="0c999-160">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)

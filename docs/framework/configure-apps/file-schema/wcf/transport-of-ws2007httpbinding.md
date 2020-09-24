---
title: <transport> / <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 692befa3-8b0b-4ec5-b601-755874e98eb0
ms.openlocfilehash: 60e8758d653848176ca3f287e253bd7990e78470
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91162055"
---
# <a name="transport-of-ws2007httpbinding"></a><span data-ttu-id="81731-102">\<transport> / \<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="81731-102">\<transport> of \<ws2007HttpBinding></span></span>

<span data-ttu-id="81731-103">HTTP taşıması için kimlik doğrulama ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="81731-103">Defines authentication settings for the HTTP transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007HttpBinding>**](ws2007httpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-ws2007httpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="81731-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="81731-104">Syntax</span></span>  
  
```xml  
<transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
           proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
           realm="string" />
```  
  
## <a name="type"></a><span data-ttu-id="81731-105">Tür</span><span class="sxs-lookup"><span data-stu-id="81731-105">Type</span></span>  

 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="81731-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="81731-106">Attributes and Elements</span></span>  

 <span data-ttu-id="81731-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="81731-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="81731-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="81731-108">Attributes</span></span>  
  
|<span data-ttu-id="81731-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="81731-109">Attribute</span></span>|<span data-ttu-id="81731-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="81731-110">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="81731-111">Hizmetin istemcinin kimliğini doğrulamak için kullanılan kimlik bilgisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="81731-111">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="81731-112">Bu öznitelik türü <xref:System.ServiceModel.HttpClientCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="81731-112">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="81731-113">Bir etki alanı ara sunucusu için istemcinin kimliğini doğrulamak için kullanılan kimlik bilgisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="81731-113">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="81731-114">Bu öznitelik türü <xref:System.ServiceModel.HttpProxyCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="81731-114">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="81731-115">Özet veya temel kimlik doğrulaması için kimlik doğrulama bölgesi.</span><span class="sxs-lookup"><span data-stu-id="81731-115">The authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="81731-116">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="81731-116">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="81731-117">Kimlik doğrulama bölgesi, kimlik doğrulamasını gerçekleştiren konağın en azından adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="81731-117">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="81731-118">Ayrıca, erişimi olan bir kullanıcı koleksiyonu da belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="81731-118">It can also specify a collection of users who have access.</span></span> <span data-ttu-id="81731-119">Kullanıcı, birkaç olası Kullanıcı adı ve parolanın kullanılabileceğini belirleyebilmek için kimlik doğrulama bölgesini sorgulayabilir.</span><span class="sxs-lookup"><span data-stu-id="81731-119">A user can query the authentication realm to determine which one of the several possible usernames and passwords can be used.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="81731-120">clientCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="81731-120">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="81731-121">Değer</span><span class="sxs-lookup"><span data-stu-id="81731-121">Value</span></span>|<span data-ttu-id="81731-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="81731-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="81731-123">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="81731-123">None</span></span>|<span data-ttu-id="81731-124">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="81731-124">Security is disabled.</span></span>|  
|<span data-ttu-id="81731-125">Temel</span><span class="sxs-lookup"><span data-stu-id="81731-125">Basic</span></span>|<span data-ttu-id="81731-126">Temel kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="81731-126">Uses basic authentication.</span></span>|  
|<span data-ttu-id="81731-127">Bilgisi</span><span class="sxs-lookup"><span data-stu-id="81731-127">Digest</span></span>|<span data-ttu-id="81731-128">Özet kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="81731-128">Uses digest authentication.</span></span>|  
|<span data-ttu-id="81731-129">NT</span><span class="sxs-lookup"><span data-stu-id="81731-129">Ntlm</span></span>|<span data-ttu-id="81731-130">Windows etki alanı ile geri dönüş olarak NTLM kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="81731-130">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="81731-131">Windows</span><span class="sxs-lookup"><span data-stu-id="81731-131">Windows</span></span>|<span data-ttu-id="81731-132">Tümleşik Windows kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="81731-132">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="81731-133">Sertifika</span><span class="sxs-lookup"><span data-stu-id="81731-133">Certificate</span></span>|<span data-ttu-id="81731-134">İstemcinin kimliğini doğrulamak için X. 509.440 sertifikalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="81731-134">Uses X.509 certificates to authenticate the client.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="81731-135">proxyCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="81731-135">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="81731-136">Değer</span><span class="sxs-lookup"><span data-stu-id="81731-136">Value</span></span>|<span data-ttu-id="81731-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="81731-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="81731-138">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="81731-138">None</span></span>|<span data-ttu-id="81731-139">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="81731-139">Security is disabled.</span></span>|  
|<span data-ttu-id="81731-140">Temel</span><span class="sxs-lookup"><span data-stu-id="81731-140">Basic</span></span>|<span data-ttu-id="81731-141">Temel kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="81731-141">Uses basic authentication.</span></span>|  
|<span data-ttu-id="81731-142">Bilgisi</span><span class="sxs-lookup"><span data-stu-id="81731-142">Digest</span></span>|<span data-ttu-id="81731-143">Özet kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="81731-143">Uses digest authentication.</span></span>|  
|<span data-ttu-id="81731-144">NT</span><span class="sxs-lookup"><span data-stu-id="81731-144">Ntlm</span></span>|<span data-ttu-id="81731-145">Windows etki alanı ile geri dönüş olarak NTLM kullanır.</span><span class="sxs-lookup"><span data-stu-id="81731-145">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="81731-146">Windows</span><span class="sxs-lookup"><span data-stu-id="81731-146">Windows</span></span>|<span data-ttu-id="81731-147">Tümleşik Windows kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="81731-147">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="81731-148">Sertifika</span><span class="sxs-lookup"><span data-stu-id="81731-148">Certificate</span></span>|<span data-ttu-id="81731-149">İstemcinin kimliğini doğrulamak için X. 509.440 sertifikalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="81731-149">Uses X.509 certificates to authenticate the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="81731-150">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="81731-150">Child Elements</span></span>  

 <span data-ttu-id="81731-151">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="81731-151">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="81731-152">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="81731-152">Parent Elements</span></span>  
  
|<span data-ttu-id="81731-153">Öğe</span><span class="sxs-lookup"><span data-stu-id="81731-153">Element</span></span>|<span data-ttu-id="81731-154">Açıklama</span><span class="sxs-lookup"><span data-stu-id="81731-154">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-ws2007httpbinding.md)|<span data-ttu-id="81731-155">Öğesinin güvenlik yeteneklerini temsil eder [\<ws2007HttpBinding>](ws2007httpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="81731-155">Represents the security capabilities of the [\<ws2007HttpBinding>](ws2007httpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="81731-156">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="81731-156">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpTransportSecurityElement>
- [<span data-ttu-id="81731-157">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="81731-157">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="81731-158">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="81731-158">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="81731-159">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="81731-159">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="81731-160">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="81731-160">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)

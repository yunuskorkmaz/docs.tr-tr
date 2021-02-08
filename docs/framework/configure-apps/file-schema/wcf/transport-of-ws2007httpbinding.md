---
description: 'Hakkında daha fazla bilgi <transport> edinin: <ws2007HttpBinding>'
title: <transport> / <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 692befa3-8b0b-4ec5-b601-755874e98eb0
ms.openlocfilehash: 8c6890bc291458ba0849ab7a206487431b279576
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99773439"
---
# <a name="transport-of-ws2007httpbinding"></a><span data-ttu-id="9bfd1-103">\<transport> / \<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="9bfd1-103">\<transport> of \<ws2007HttpBinding></span></span>

<span data-ttu-id="9bfd1-104">HTTP taşıması için kimlik doğrulama ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9bfd1-104">Defines authentication settings for the HTTP transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007HttpBinding>**](ws2007httpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-ws2007httpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="9bfd1-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="9bfd1-105">Syntax</span></span>  
  
```xml  
<transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
           proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
           realm="string" />
```  
  
## <a name="type"></a><span data-ttu-id="9bfd1-106">Tür</span><span class="sxs-lookup"><span data-stu-id="9bfd1-106">Type</span></span>  

 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9bfd1-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9bfd1-107">Attributes and Elements</span></span>  

 <span data-ttu-id="9bfd1-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9bfd1-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9bfd1-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9bfd1-109">Attributes</span></span>  
  
|<span data-ttu-id="9bfd1-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9bfd1-110">Attribute</span></span>|<span data-ttu-id="9bfd1-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9bfd1-111">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="9bfd1-112">Hizmetin istemcinin kimliğini doğrulamak için kullanılan kimlik bilgisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9bfd1-112">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="9bfd1-113">Bu öznitelik türü <xref:System.ServiceModel.HttpClientCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="9bfd1-113">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="9bfd1-114">Bir etki alanı ara sunucusu için istemcinin kimliğini doğrulamak için kullanılan kimlik bilgisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9bfd1-114">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="9bfd1-115">Bu öznitelik türü <xref:System.ServiceModel.HttpProxyCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="9bfd1-115">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="9bfd1-116">Özet veya temel kimlik doğrulaması için kimlik doğrulama bölgesi.</span><span class="sxs-lookup"><span data-stu-id="9bfd1-116">The authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="9bfd1-117">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="9bfd1-117">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="9bfd1-118">Kimlik doğrulama bölgesi, kimlik doğrulamasını gerçekleştiren konağın en azından adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9bfd1-118">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="9bfd1-119">Ayrıca, erişimi olan bir kullanıcı koleksiyonu da belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="9bfd1-119">It can also specify a collection of users who have access.</span></span> <span data-ttu-id="9bfd1-120">Kullanıcı, birkaç olası Kullanıcı adı ve parolanın kullanılabileceğini belirleyebilmek için kimlik doğrulama bölgesini sorgulayabilir.</span><span class="sxs-lookup"><span data-stu-id="9bfd1-120">A user can query the authentication realm to determine which one of the several possible usernames and passwords can be used.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="9bfd1-121">clientCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="9bfd1-121">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="9bfd1-122">Değer</span><span class="sxs-lookup"><span data-stu-id="9bfd1-122">Value</span></span>|<span data-ttu-id="9bfd1-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9bfd1-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9bfd1-124">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="9bfd1-124">None</span></span>|<span data-ttu-id="9bfd1-125">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="9bfd1-125">Security is disabled.</span></span>|  
|<span data-ttu-id="9bfd1-126">Temel</span><span class="sxs-lookup"><span data-stu-id="9bfd1-126">Basic</span></span>|<span data-ttu-id="9bfd1-127">Temel kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="9bfd1-127">Uses basic authentication.</span></span>|  
|<span data-ttu-id="9bfd1-128">Bilgisi</span><span class="sxs-lookup"><span data-stu-id="9bfd1-128">Digest</span></span>|<span data-ttu-id="9bfd1-129">Özet kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="9bfd1-129">Uses digest authentication.</span></span>|  
|<span data-ttu-id="9bfd1-130">NT</span><span class="sxs-lookup"><span data-stu-id="9bfd1-130">Ntlm</span></span>|<span data-ttu-id="9bfd1-131">Windows etki alanı ile geri dönüş olarak NTLM kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="9bfd1-131">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="9bfd1-132">Windows</span><span class="sxs-lookup"><span data-stu-id="9bfd1-132">Windows</span></span>|<span data-ttu-id="9bfd1-133">Tümleşik Windows kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="9bfd1-133">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="9bfd1-134">Sertifika</span><span class="sxs-lookup"><span data-stu-id="9bfd1-134">Certificate</span></span>|<span data-ttu-id="9bfd1-135">İstemcinin kimliğini doğrulamak için X. 509.440 sertifikalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="9bfd1-135">Uses X.509 certificates to authenticate the client.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="9bfd1-136">proxyCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="9bfd1-136">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="9bfd1-137">Değer</span><span class="sxs-lookup"><span data-stu-id="9bfd1-137">Value</span></span>|<span data-ttu-id="9bfd1-138">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9bfd1-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9bfd1-139">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="9bfd1-139">None</span></span>|<span data-ttu-id="9bfd1-140">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="9bfd1-140">Security is disabled.</span></span>|  
|<span data-ttu-id="9bfd1-141">Temel</span><span class="sxs-lookup"><span data-stu-id="9bfd1-141">Basic</span></span>|<span data-ttu-id="9bfd1-142">Temel kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="9bfd1-142">Uses basic authentication.</span></span>|  
|<span data-ttu-id="9bfd1-143">Bilgisi</span><span class="sxs-lookup"><span data-stu-id="9bfd1-143">Digest</span></span>|<span data-ttu-id="9bfd1-144">Özet kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="9bfd1-144">Uses digest authentication.</span></span>|  
|<span data-ttu-id="9bfd1-145">NT</span><span class="sxs-lookup"><span data-stu-id="9bfd1-145">Ntlm</span></span>|<span data-ttu-id="9bfd1-146">Windows etki alanı ile geri dönüş olarak NTLM kullanır.</span><span class="sxs-lookup"><span data-stu-id="9bfd1-146">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="9bfd1-147">Windows</span><span class="sxs-lookup"><span data-stu-id="9bfd1-147">Windows</span></span>|<span data-ttu-id="9bfd1-148">Tümleşik Windows kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="9bfd1-148">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="9bfd1-149">Sertifika</span><span class="sxs-lookup"><span data-stu-id="9bfd1-149">Certificate</span></span>|<span data-ttu-id="9bfd1-150">İstemcinin kimliğini doğrulamak için X. 509.440 sertifikalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="9bfd1-150">Uses X.509 certificates to authenticate the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9bfd1-151">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9bfd1-151">Child Elements</span></span>  

 <span data-ttu-id="9bfd1-152">Yok</span><span class="sxs-lookup"><span data-stu-id="9bfd1-152">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9bfd1-153">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9bfd1-153">Parent Elements</span></span>  
  
|<span data-ttu-id="9bfd1-154">Öğe</span><span class="sxs-lookup"><span data-stu-id="9bfd1-154">Element</span></span>|<span data-ttu-id="9bfd1-155">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9bfd1-155">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-ws2007httpbinding.md)|<span data-ttu-id="9bfd1-156">Öğesinin güvenlik yeteneklerini temsil eder [\<ws2007HttpBinding>](ws2007httpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="9bfd1-156">Represents the security capabilities of the [\<ws2007HttpBinding>](ws2007httpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9bfd1-157">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9bfd1-157">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpTransportSecurityElement>
- [<span data-ttu-id="9bfd1-158">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="9bfd1-158">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="9bfd1-159">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="9bfd1-159">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="9bfd1-160">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="9bfd1-160">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="9bfd1-161">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="9bfd1-161">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)

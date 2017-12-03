---
title: "&lt;ws2007HttpBinding&gt; &lt;taşıma&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 692befa3-8b0b-4ec5-b601-755874e98eb0
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 573b7fb5cf130d0a638326b87ae49f90db881df4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="lttransportgt-of-ltws2007httpbindinggt"></a><span data-ttu-id="32566-102">&lt;ws2007HttpBinding&gt; &lt;taşıma&gt;</span><span class="sxs-lookup"><span data-stu-id="32566-102">&lt;transport&gt; of &lt;ws2007HttpBinding&gt;</span></span>
<span data-ttu-id="32566-103">HTTP taşıma için kimlik doğrulama ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="32566-103">Defines authentication settings for the HTTP transport.</span></span>  
  
 <span data-ttu-id="32566-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="32566-104">\<system.serviceModel></span></span>  
<span data-ttu-id="32566-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="32566-105">\<bindings></span></span>  
<span data-ttu-id="32566-106">\<ws2007HttpBinding ></span><span class="sxs-lookup"><span data-stu-id="32566-106">\<ws2007HttpBinding></span></span>  
<span data-ttu-id="32566-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="32566-107">\<binding></span></span>  
<span data-ttu-id="32566-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="32566-108">\<security></span></span>  
<span data-ttu-id="32566-109">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="32566-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32566-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="32566-110">Syntax</span></span>  
  
```  
transport clientCredentialType =   
       "Basic/Certificate/Digest/None/Ntlm/Windows"  
       proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
       realm="string"   
```  
  
## <a name="type"></a><span data-ttu-id="32566-111">Tür</span><span class="sxs-lookup"><span data-stu-id="32566-111">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="32566-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="32566-112">Attributes and Elements</span></span>  
 <span data-ttu-id="32566-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="32566-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="32566-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="32566-114">Attributes</span></span>  
  
|<span data-ttu-id="32566-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="32566-115">Attribute</span></span>|<span data-ttu-id="32566-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="32566-116">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="32566-117">Hizmeti için istemci kimlik doğrulaması için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="32566-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="32566-118">Bu öznitelik türünde <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="32566-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="32566-119">Bir etki alanı Ara sunucu için istemci kimlik doğrulaması için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="32566-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="32566-120">Bu öznitelik türünde <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="32566-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="32566-121">Özet veya temel kimlik doğrulaması için kimlik doğrulaması bölgesi.</span><span class="sxs-lookup"><span data-stu-id="32566-121">The authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="32566-122">Varsayılan boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="32566-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="32566-123">Bir kimlik doğrulaması bölgesi, en az kimlik doğrulaması yapan ana bilgisayar adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="32566-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="32566-124">Ayrıca, erişimi olan kullanıcıların koleksiyonu de belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="32566-124">It can also specify a collection of users who have access.</span></span> <span data-ttu-id="32566-125">Bir kullanıcı, birkaç olası kullanıcı adları ve parolalar hangisinin kullanılacağını belirlemek için kimlik doğrulaması bölgesi sorgulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="32566-125">A user can query the authentication realm to determine which one of the several possible usernames and passwords can be used.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="32566-126">clientCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="32566-126">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="32566-127">Değer</span><span class="sxs-lookup"><span data-stu-id="32566-127">Value</span></span>|<span data-ttu-id="32566-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="32566-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="32566-129">Yok.</span><span class="sxs-lookup"><span data-stu-id="32566-129">None</span></span>|<span data-ttu-id="32566-130">Güvenliği devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="32566-130">Security is disabled.</span></span>|  
|<span data-ttu-id="32566-131">Temel</span><span class="sxs-lookup"><span data-stu-id="32566-131">Basic</span></span>|<span data-ttu-id="32566-132">Temel kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="32566-132">Uses basic authentication.</span></span>|  
|<span data-ttu-id="32566-133">Özet</span><span class="sxs-lookup"><span data-stu-id="32566-133">Digest</span></span>|<span data-ttu-id="32566-134">Özet kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="32566-134">Uses digest authentication.</span></span>|  
|<span data-ttu-id="32566-135">NTLM</span><span class="sxs-lookup"><span data-stu-id="32566-135">Ntlm</span></span>|<span data-ttu-id="32566-136">Bir Windows etki alanı ile bir geri dönüş olarak NTLM kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="32566-136">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="32566-137">Windows</span><span class="sxs-lookup"><span data-stu-id="32566-137">Windows</span></span>|<span data-ttu-id="32566-138">Tümleşik Windows kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="32566-138">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="32566-139">Sertifika</span><span class="sxs-lookup"><span data-stu-id="32566-139">Certificate</span></span>|<span data-ttu-id="32566-140">İstemci kimlik doğrulaması için X.509 sertifikaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="32566-140">Uses X.509 certificates to authenticate the client.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="32566-141">proxyCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="32566-141">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="32566-142">Değer</span><span class="sxs-lookup"><span data-stu-id="32566-142">Value</span></span>|<span data-ttu-id="32566-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="32566-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="32566-144">Yok.</span><span class="sxs-lookup"><span data-stu-id="32566-144">None</span></span>|<span data-ttu-id="32566-145">Güvenliği devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="32566-145">Security is disabled.</span></span>|  
|<span data-ttu-id="32566-146">Temel</span><span class="sxs-lookup"><span data-stu-id="32566-146">Basic</span></span>|<span data-ttu-id="32566-147">Temel kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="32566-147">Uses basic authentication.</span></span>|  
|<span data-ttu-id="32566-148">Özet</span><span class="sxs-lookup"><span data-stu-id="32566-148">Digest</span></span>|<span data-ttu-id="32566-149">Özet kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="32566-149">Uses digest authentication.</span></span>|  
|<span data-ttu-id="32566-150">NTLM</span><span class="sxs-lookup"><span data-stu-id="32566-150">Ntlm</span></span>|<span data-ttu-id="32566-151">Bir Windows etki alanı ile bir geri dönüş olarak NTLM kullanır.</span><span class="sxs-lookup"><span data-stu-id="32566-151">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="32566-152">Windows</span><span class="sxs-lookup"><span data-stu-id="32566-152">Windows</span></span>|<span data-ttu-id="32566-153">Tümleşik Windows kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="32566-153">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="32566-154">Sertifika</span><span class="sxs-lookup"><span data-stu-id="32566-154">Certificate</span></span>|<span data-ttu-id="32566-155">İstemci kimlik doğrulaması için X.509 sertifikaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="32566-155">Uses X.509 certificates to authenticate the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="32566-156">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="32566-156">Child Elements</span></span>  
 <span data-ttu-id="32566-157">Yok.</span><span class="sxs-lookup"><span data-stu-id="32566-157">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="32566-158">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="32566-158">Parent Elements</span></span>  
  
|<span data-ttu-id="32566-159">Öğe</span><span class="sxs-lookup"><span data-stu-id="32566-159">Element</span></span>|<span data-ttu-id="32566-160">Açıklama</span><span class="sxs-lookup"><span data-stu-id="32566-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="32566-161">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="32566-161">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-ws2007httpbinding.md)|<span data-ttu-id="32566-162">Güvenlik özellikleri temsil eden [ \<ws2007HttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="32566-162">Represents the security capabilities of the [\<ws2007HttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="32566-163">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="32566-163">See Also</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpTransportSecurityElement>  
 [<span data-ttu-id="32566-164">Hizmetler ve istemcileri güvenli hale getirme</span><span class="sxs-lookup"><span data-stu-id="32566-164">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="32566-165">Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="32566-165">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="32566-166">Sistem tarafından sağlanan bağlamaları yapılandırma</span><span class="sxs-lookup"><span data-stu-id="32566-166">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="32566-167">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="32566-167">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="32566-168">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="32566-168">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)

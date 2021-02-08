---
description: 'Hakkında daha fazla bilgi <transport> edinin: <webHttpBinding>'
title: <transport> / <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: f150fb19-7de1-44af-81f4-86cad881cd05
ms.openlocfilehash: a845786f4e60a44dcb157201235d28d49ab8d40b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99773452"
---
# <a name="transport-of-webhttpbinding"></a><span data-ttu-id="3f4c1-103">\<transport> / \<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="3f4c1-103">\<transport> of \<webHttpBinding></span></span>

<span data-ttu-id="3f4c1-104">HTTP isteklerini alacak şekilde yapılandırılmış bir hizmet uç noktası için aktarım düzeyi güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3f4c1-104">Defines the transport-level security settings for a service endpoint configured to receive HTTP requests.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<webHttpBinding>**](webhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-webhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="3f4c1-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="3f4c1-105">Syntax</span></span>  
  
```xml  
<webHttpBinding>
  <binding>
    <security mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">
      <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"
                 proxyCredentialType="None|Basic|Digest|Ntlm|Windows"
                 realm="string">
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</webHttpBinding>
```  
  
## <a name="type"></a><span data-ttu-id="3f4c1-106">Tür</span><span class="sxs-lookup"><span data-stu-id="3f4c1-106">Type</span></span>  

 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3f4c1-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3f4c1-107">Attributes and Elements</span></span>  

 <span data-ttu-id="3f4c1-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3f4c1-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3f4c1-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3f4c1-109">Attributes</span></span>  
  
|<span data-ttu-id="3f4c1-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3f4c1-110">Attribute</span></span>|<span data-ttu-id="3f4c1-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3f4c1-111">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="3f4c1-112">Hizmetin istemcinin kimliğini doğrulamak için kullanılan kimlik bilgisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3f4c1-112">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="3f4c1-113">Bu öznitelik türü <xref:System.ServiceModel.HttpClientCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="3f4c1-113">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="3f4c1-114">Bir etki alanı ara sunucusu için istemcinin kimliğini doğrulamak için kullanılan kimlik bilgisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3f4c1-114">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="3f4c1-115">Bu öznitelik türü <xref:System.ServiceModel.HttpProxyCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="3f4c1-115">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="3f4c1-116">Özet veya temel kimlik doğrulaması için kimlik doğrulama bölgesini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="3f4c1-116">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="3f4c1-117">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="3f4c1-117">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="3f4c1-118">Kimlik doğrulama bölgesi, kimlik doğrulamasını gerçekleştiren konağın en azından adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3f4c1-118">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="3f4c1-119">Ayrıca, erişimi olan bir kullanıcı koleksiyonu da belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="3f4c1-119">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="3f4c1-120">Kullanıcı, birkaç olası Kullanıcı adı ve parolanın kullanılabileceğini belirlemek için kimlik doğrulama bölgesini sorgulayabilir.</span><span class="sxs-lookup"><span data-stu-id="3f4c1-120">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|  
|`policyEnforcement`|<span data-ttu-id="3f4c1-121">Bu numaralandırma, ne zaman <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> uygulanacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3f4c1-121">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="3f4c1-122">1. hiçbir süre – ilke hiçbir şekilde zorlanmaz (genişletilmiş koruma devre dışı bırakılır).</span><span class="sxs-lookup"><span data-stu-id="3f4c1-122">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="3f4c1-123">2. WhenSupported – ilke yalnızca istemci genişletilmiş korumayı destekliyorsa zorlanır.</span><span class="sxs-lookup"><span data-stu-id="3f4c1-123">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="3f4c1-124">3. her zaman – ilke her zaman zorlanır.</span><span class="sxs-lookup"><span data-stu-id="3f4c1-124">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="3f4c1-125">Genişletilmiş korumayı desteklemeyen istemciler kimlik doğrulaması yapamaz.</span><span class="sxs-lookup"><span data-stu-id="3f4c1-125">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="3f4c1-126">clientCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="3f4c1-126">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="3f4c1-127">Değer</span><span class="sxs-lookup"><span data-stu-id="3f4c1-127">Value</span></span>|<span data-ttu-id="3f4c1-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3f4c1-128">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="3f4c1-129">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="3f4c1-129">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="3f4c1-130">Temel kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="3f4c1-130">Uses basic authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="3f4c1-131">İstemcinin kimliğini doğrulamak için X. 509.440 sertifikalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="3f4c1-131">Uses X.509 certificates to authenticate the client.</span></span>|  
|`Digest`|<span data-ttu-id="3f4c1-132">Özet kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="3f4c1-132">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="3f4c1-133">Windows etki alanı ile geri dönüş olarak NTLM kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="3f4c1-133">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="3f4c1-134">Tümleşik Windows kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="3f4c1-134">Uses integrated Windows authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="3f4c1-135">proxyCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="3f4c1-135">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="3f4c1-136">Değer</span><span class="sxs-lookup"><span data-stu-id="3f4c1-136">Value</span></span>|<span data-ttu-id="3f4c1-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3f4c1-137">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="3f4c1-138">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="3f4c1-138">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="3f4c1-139">Temel kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="3f4c1-139">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="3f4c1-140">Özet kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="3f4c1-140">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="3f4c1-141">Windows etki alanı ile geri dönüş olarak NTLM kullanır.</span><span class="sxs-lookup"><span data-stu-id="3f4c1-141">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="3f4c1-142">Tümleşik Windows kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="3f4c1-142">Uses integrated Windows authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3f4c1-143">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3f4c1-143">Child Elements</span></span>  

 <span data-ttu-id="3f4c1-144">Yok.</span><span class="sxs-lookup"><span data-stu-id="3f4c1-144">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3f4c1-145">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3f4c1-145">Parent Elements</span></span>  
  
|<span data-ttu-id="3f4c1-146">Öğe</span><span class="sxs-lookup"><span data-stu-id="3f4c1-146">Element</span></span>|<span data-ttu-id="3f4c1-147">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3f4c1-147">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-webhttpbinding.md)|<span data-ttu-id="3f4c1-148">Öğesinin güvenlik yeteneklerini temsil eder [\<wsHttpBinding>](wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="3f4c1-148">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3f4c1-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f4c1-149">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.WebHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WebHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [<span data-ttu-id="3f4c1-150">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="3f4c1-150">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="3f4c1-151">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="3f4c1-151">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="3f4c1-152">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="3f4c1-152">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="3f4c1-153">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="3f4c1-153">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- [<span data-ttu-id="3f4c1-154">WCF Web HTTP Programlama Modeli</span><span class="sxs-lookup"><span data-stu-id="3f4c1-154">WCF Web HTTP Programming Model</span></span>](../../../wcf/feature-details/wcf-web-http-programming-model.md)

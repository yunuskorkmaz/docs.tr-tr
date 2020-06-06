---
title: <transport> / <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: f150fb19-7de1-44af-81f4-86cad881cd05
ms.openlocfilehash: e8016eb9058f132722587368f1f8c7c03220af4a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73732793"
---
# <a name="transport-of-webhttpbinding"></a><span data-ttu-id="b5637-102">\<transport> / \<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="b5637-102">\<transport> of \<webHttpBinding></span></span>
<span data-ttu-id="b5637-103">HTTP isteklerini alacak şekilde yapılandırılmış bir hizmet uç noktası için aktarım düzeyi güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b5637-103">Defines the transport-level security settings for a service endpoint configured to receive HTTP requests.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<webHttpBinding>**](webhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-webhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="b5637-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b5637-104">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="b5637-105">Tür</span><span class="sxs-lookup"><span data-stu-id="b5637-105">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b5637-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b5637-106">Attributes and Elements</span></span>  
 <span data-ttu-id="b5637-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b5637-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b5637-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b5637-108">Attributes</span></span>  
  
|<span data-ttu-id="b5637-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b5637-109">Attribute</span></span>|<span data-ttu-id="b5637-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b5637-110">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="b5637-111">Hizmetin istemcinin kimliğini doğrulamak için kullanılan kimlik bilgisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b5637-111">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="b5637-112">Bu öznitelik türü <xref:System.ServiceModel.HttpClientCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="b5637-112">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="b5637-113">Bir etki alanı ara sunucusu için istemcinin kimliğini doğrulamak için kullanılan kimlik bilgisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b5637-113">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="b5637-114">Bu öznitelik türü <xref:System.ServiceModel.HttpProxyCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="b5637-114">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="b5637-115">Özet veya temel kimlik doğrulaması için kimlik doğrulama bölgesini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="b5637-115">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="b5637-116">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="b5637-116">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="b5637-117">Kimlik doğrulama bölgesi, kimlik doğrulamasını gerçekleştiren konağın en azından adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b5637-117">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="b5637-118">Ayrıca, erişimi olan bir kullanıcı koleksiyonu da belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="b5637-118">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="b5637-119">Kullanıcı, birkaç olası Kullanıcı adı ve parolanın kullanılabileceğini belirlemek için kimlik doğrulama bölgesini sorgulayabilir.</span><span class="sxs-lookup"><span data-stu-id="b5637-119">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|  
|`policyEnforcement`|<span data-ttu-id="b5637-120">Bu numaralandırma, ne zaman <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> uygulanacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b5637-120">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="b5637-121">1. hiçbir süre – ilke hiçbir şekilde zorlanmaz (genişletilmiş koruma devre dışı bırakılır).</span><span class="sxs-lookup"><span data-stu-id="b5637-121">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="b5637-122">2. WhenSupported – ilke yalnızca istemci genişletilmiş korumayı destekliyorsa zorlanır.</span><span class="sxs-lookup"><span data-stu-id="b5637-122">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="b5637-123">3. her zaman – ilke her zaman zorlanır.</span><span class="sxs-lookup"><span data-stu-id="b5637-123">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="b5637-124">Genişletilmiş korumayı desteklemeyen istemciler kimlik doğrulaması yapamaz.</span><span class="sxs-lookup"><span data-stu-id="b5637-124">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="b5637-125">clientCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="b5637-125">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="b5637-126">Değer</span><span class="sxs-lookup"><span data-stu-id="b5637-126">Value</span></span>|<span data-ttu-id="b5637-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b5637-127">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="b5637-128">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="b5637-128">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="b5637-129">Temel kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="b5637-129">Uses basic authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="b5637-130">İstemcinin kimliğini doğrulamak için X. 509.440 sertifikalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="b5637-130">Uses X.509 certificates to authenticate the client.</span></span>|  
|`Digest`|<span data-ttu-id="b5637-131">Özet kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="b5637-131">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="b5637-132">Windows etki alanı ile geri dönüş olarak NTLM kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="b5637-132">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="b5637-133">Tümleşik Windows kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="b5637-133">Uses integrated Windows authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="b5637-134">proxyCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="b5637-134">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="b5637-135">Değer</span><span class="sxs-lookup"><span data-stu-id="b5637-135">Value</span></span>|<span data-ttu-id="b5637-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b5637-136">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="b5637-137">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="b5637-137">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="b5637-138">Temel kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="b5637-138">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="b5637-139">Özet kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="b5637-139">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="b5637-140">Windows etki alanı ile geri dönüş olarak NTLM kullanır.</span><span class="sxs-lookup"><span data-stu-id="b5637-140">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="b5637-141">Tümleşik Windows kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="b5637-141">Uses integrated Windows authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b5637-142">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b5637-142">Child Elements</span></span>  
 <span data-ttu-id="b5637-143">Yok.</span><span class="sxs-lookup"><span data-stu-id="b5637-143">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b5637-144">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b5637-144">Parent Elements</span></span>  
  
|<span data-ttu-id="b5637-145">Öğe</span><span class="sxs-lookup"><span data-stu-id="b5637-145">Element</span></span>|<span data-ttu-id="b5637-146">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b5637-146">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-webhttpbinding.md)|<span data-ttu-id="b5637-147">Öğesinin güvenlik yeteneklerini temsil eder [\<wsHttpBinding>](wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="b5637-147">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b5637-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b5637-148">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.WebHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WebHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [<span data-ttu-id="b5637-149">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="b5637-149">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="b5637-150">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="b5637-150">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b5637-151">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b5637-151">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="b5637-152">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="b5637-152">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- [<span data-ttu-id="b5637-153">WCF Web HTTP Programlama Modeli</span><span class="sxs-lookup"><span data-stu-id="b5637-153">WCF Web HTTP Programming Model</span></span>](../../../wcf/feature-details/wcf-web-http-programming-model.md)

---
description: 'Hakkında daha fazla bilgi <transport> edinin: <wsHttpBinding>'
title: <transport> / <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 21e38acf-450a-4bda-82b6-de305e1f7cd8
ms.openlocfilehash: 7801148d76aaa9c074eeb7a83c1dd2fa152d871c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749323"
---
# <a name="transport-of-wshttpbinding"></a><span data-ttu-id="5ca3b-103">\<transport> / \<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="5ca3b-103">\<transport> of \<wsHttpBinding></span></span>

<span data-ttu-id="5ca3b-104">HTTP taşıması için kimlik doğrulama ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5ca3b-104">Defines authentication settings for the HTTP transport.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsHttpBinding>**](wshttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wshttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  

## <a name="syntax"></a><span data-ttu-id="5ca3b-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="5ca3b-105">Syntax</span></span>

```xml
<wsHttpBinding>
  <binding>
    <security mode="None|Transport|TransportWithMessageCredential|TransportCredentialOnly">
      <transport clientCredentialType="Basic|Certificate|Digest|None|Ntlm|Windows"
                 proxyCredentialType="Basic|Digest|None|Ntlm|Windows"
                 realm="string" />
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</wsHttpBinding>
```

## <a name="type"></a><span data-ttu-id="5ca3b-106">Tür</span><span class="sxs-lookup"><span data-stu-id="5ca3b-106">Type</span></span>

<xref:System.ServiceModel.HttpTransportSecurity>

## <a name="attributes-and-elements"></a><span data-ttu-id="5ca3b-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5ca3b-107">Attributes and Elements</span></span>

<span data-ttu-id="5ca3b-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5ca3b-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="5ca3b-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5ca3b-109">Attributes</span></span>

|<span data-ttu-id="5ca3b-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5ca3b-110">Attribute</span></span>|<span data-ttu-id="5ca3b-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5ca3b-111">Description</span></span>|
|---------------|-----------------|
|`clientCredentialType`|<span data-ttu-id="5ca3b-112">Hizmetin istemcinin kimliğini doğrulamak için kullanılan kimlik bilgisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5ca3b-112">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="5ca3b-113">Bu öznitelik türü <xref:System.ServiceModel.HttpClientCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="5ca3b-113">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|
|`proxyCredentialType`|<span data-ttu-id="5ca3b-114">Bir etki alanı ara sunucusu için istemcinin kimliğini doğrulamak için kullanılan kimlik bilgisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5ca3b-114">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="5ca3b-115">Bu öznitelik türü <xref:System.ServiceModel.HttpProxyCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="5ca3b-115">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|
|`realm`|<span data-ttu-id="5ca3b-116">Özet veya temel kimlik doğrulaması için kimlik doğrulama bölgesini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="5ca3b-116">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="5ca3b-117">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="5ca3b-117">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="5ca3b-118">Kimlik doğrulama bölgesi, kimlik doğrulamasını gerçekleştiren konağın en azından adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5ca3b-118">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="5ca3b-119">Ayrıca, erişimi olan bir kullanıcı koleksiyonu da belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="5ca3b-119">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="5ca3b-120">Kullanıcı, birkaç olası Kullanıcı adı ve parolanın kullanılabileceğini belirlemek için kimlik doğrulama bölgesini sorgulayabilir.</span><span class="sxs-lookup"><span data-stu-id="5ca3b-120">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|
|`policyEnforcement`|<span data-ttu-id="5ca3b-121">Bu numaralandırma, ne zaman <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> uygulanacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5ca3b-121">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="5ca3b-122">1. hiçbir süre – ilke hiçbir şekilde zorlanmaz (genişletilmiş koruma devre dışı bırakılır).</span><span class="sxs-lookup"><span data-stu-id="5ca3b-122">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="5ca3b-123">2. WhenSupported – ilke yalnızca istemci genişletilmiş korumayı destekliyorsa zorlanır.</span><span class="sxs-lookup"><span data-stu-id="5ca3b-123">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="5ca3b-124">3. her zaman – ilke her zaman zorlanır.</span><span class="sxs-lookup"><span data-stu-id="5ca3b-124">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="5ca3b-125">Genişletilmiş korumayı desteklemeyen istemciler kimlik doğrulaması yapamaz.</span><span class="sxs-lookup"><span data-stu-id="5ca3b-125">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|

## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="5ca3b-126">clientCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="5ca3b-126">clientCredentialType Attribute</span></span>

|<span data-ttu-id="5ca3b-127">Değer</span><span class="sxs-lookup"><span data-stu-id="5ca3b-127">Value</span></span>|<span data-ttu-id="5ca3b-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5ca3b-128">Description</span></span>|
|-----------|-----------------|
|`None`|<span data-ttu-id="5ca3b-129">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="5ca3b-129">Security is disabled.</span></span>|
|`Basic`|<span data-ttu-id="5ca3b-130">Temel kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="5ca3b-130">Uses basic authentication.</span></span>|
|`Digest`|<span data-ttu-id="5ca3b-131">Özet kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="5ca3b-131">Uses digest authentication.</span></span>|
|`Ntlm`|<span data-ttu-id="5ca3b-132">Windows etki alanı ile geri dönüş olarak NTLM kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="5ca3b-132">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|
|`Windows`|<span data-ttu-id="5ca3b-133">Tümleşik Windows kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="5ca3b-133">Uses integrated Windows authentication.</span></span>|
|`Certificate`|<span data-ttu-id="5ca3b-134">İstemcinin kimliğini doğrulamak için X. 509.440 sertifikalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="5ca3b-134">Uses X.509 certificates to authenticate the client.</span></span>|

## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="5ca3b-135">proxyCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="5ca3b-135">proxyCredentialType Attribute</span></span>

|<span data-ttu-id="5ca3b-136">Değer</span><span class="sxs-lookup"><span data-stu-id="5ca3b-136">Value</span></span>|<span data-ttu-id="5ca3b-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5ca3b-137">Description</span></span>|
|-----------|-----------------|
|`None`|<span data-ttu-id="5ca3b-138">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="5ca3b-138">Security is disabled.</span></span>|
|`Basic`|<span data-ttu-id="5ca3b-139">Temel kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="5ca3b-139">Uses basic authentication.</span></span>|
|`Digest`|<span data-ttu-id="5ca3b-140">Özet kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="5ca3b-140">Uses digest authentication.</span></span>|
|`Ntlm`|<span data-ttu-id="5ca3b-141">Windows etki alanı ile geri dönüş olarak NTLM kullanır.</span><span class="sxs-lookup"><span data-stu-id="5ca3b-141">Uses NTLM as a fallback with a Windows domain.</span></span>|
|`Windows`|<span data-ttu-id="5ca3b-142">Tümleşik Windows kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="5ca3b-142">Uses integrated Windows authentication.</span></span>|
|`Certificate`|<span data-ttu-id="5ca3b-143">İstemcinin kimliğini doğrulamak için X. 509.440 sertifikalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="5ca3b-143">Uses X.509 certificates to authenticate the client.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="5ca3b-144">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5ca3b-144">Child Elements</span></span>

<span data-ttu-id="5ca3b-145">Yok.</span><span class="sxs-lookup"><span data-stu-id="5ca3b-145">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5ca3b-146">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5ca3b-146">Parent Elements</span></span>

|<span data-ttu-id="5ca3b-147">Öğe</span><span class="sxs-lookup"><span data-stu-id="5ca3b-147">Element</span></span>|<span data-ttu-id="5ca3b-148">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5ca3b-148">Description</span></span>|
|-------------|-----------------|
|[\<security>](security-of-wshttpbinding.md)|<span data-ttu-id="5ca3b-149">Öğesinin güvenlik yeteneklerini temsil eder [\<wsHttpBinding>](wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="5ca3b-149">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md).</span></span>|

## <a name="see-also"></a><span data-ttu-id="5ca3b-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ca3b-150">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [<span data-ttu-id="5ca3b-151">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="5ca3b-151">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="5ca3b-152">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="5ca3b-152">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="5ca3b-153">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="5ca3b-153">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="5ca3b-154">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="5ca3b-154">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)

---
title: <transport> / <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 21e38acf-450a-4bda-82b6-de305e1f7cd8
ms.openlocfilehash: 1afeed62fcbf3b083d69a7cedb7eb80b81f5c17b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73732744"
---
# <a name="transport-of-wshttpbinding"></a><span data-ttu-id="e61f8-102">\<transport> / \<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="e61f8-102">\<transport> of \<wsHttpBinding></span></span>

<span data-ttu-id="e61f8-103">HTTP taşıması için kimlik doğrulama ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e61f8-103">Defines authentication settings for the HTTP transport.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsHttpBinding>**](wshttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wshttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  

## <a name="syntax"></a><span data-ttu-id="e61f8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e61f8-104">Syntax</span></span>

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

## <a name="type"></a><span data-ttu-id="e61f8-105">Tür</span><span class="sxs-lookup"><span data-stu-id="e61f8-105">Type</span></span>

<xref:System.ServiceModel.HttpTransportSecurity>

## <a name="attributes-and-elements"></a><span data-ttu-id="e61f8-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e61f8-106">Attributes and Elements</span></span>

<span data-ttu-id="e61f8-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e61f8-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="e61f8-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e61f8-108">Attributes</span></span>

|<span data-ttu-id="e61f8-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e61f8-109">Attribute</span></span>|<span data-ttu-id="e61f8-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e61f8-110">Description</span></span>|
|---------------|-----------------|
|`clientCredentialType`|<span data-ttu-id="e61f8-111">Hizmetin istemcinin kimliğini doğrulamak için kullanılan kimlik bilgisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e61f8-111">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="e61f8-112">Bu öznitelik türü <xref:System.ServiceModel.HttpClientCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="e61f8-112">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|
|`proxyCredentialType`|<span data-ttu-id="e61f8-113">Bir etki alanı ara sunucusu için istemcinin kimliğini doğrulamak için kullanılan kimlik bilgisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e61f8-113">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="e61f8-114">Bu öznitelik türü <xref:System.ServiceModel.HttpProxyCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="e61f8-114">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|
|`realm`|<span data-ttu-id="e61f8-115">Özet veya temel kimlik doğrulaması için kimlik doğrulama bölgesini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="e61f8-115">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="e61f8-116">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="e61f8-116">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="e61f8-117">Kimlik doğrulama bölgesi, kimlik doğrulamasını gerçekleştiren konağın en azından adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e61f8-117">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="e61f8-118">Ayrıca, erişimi olan bir kullanıcı koleksiyonu da belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="e61f8-118">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="e61f8-119">Kullanıcı, birkaç olası Kullanıcı adı ve parolanın kullanılabileceğini belirlemek için kimlik doğrulama bölgesini sorgulayabilir.</span><span class="sxs-lookup"><span data-stu-id="e61f8-119">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|
|`policyEnforcement`|<span data-ttu-id="e61f8-120">Bu numaralandırma, ne zaman <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> uygulanacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e61f8-120">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="e61f8-121">1. hiçbir süre – ilke hiçbir şekilde zorlanmaz (genişletilmiş koruma devre dışı bırakılır).</span><span class="sxs-lookup"><span data-stu-id="e61f8-121">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="e61f8-122">2. WhenSupported – ilke yalnızca istemci genişletilmiş korumayı destekliyorsa zorlanır.</span><span class="sxs-lookup"><span data-stu-id="e61f8-122">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="e61f8-123">3. her zaman – ilke her zaman zorlanır.</span><span class="sxs-lookup"><span data-stu-id="e61f8-123">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="e61f8-124">Genişletilmiş korumayı desteklemeyen istemciler kimlik doğrulaması yapamaz.</span><span class="sxs-lookup"><span data-stu-id="e61f8-124">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|

## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="e61f8-125">clientCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="e61f8-125">clientCredentialType Attribute</span></span>

|<span data-ttu-id="e61f8-126">Değer</span><span class="sxs-lookup"><span data-stu-id="e61f8-126">Value</span></span>|<span data-ttu-id="e61f8-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e61f8-127">Description</span></span>|
|-----------|-----------------|
|`None`|<span data-ttu-id="e61f8-128">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="e61f8-128">Security is disabled.</span></span>|
|`Basic`|<span data-ttu-id="e61f8-129">Temel kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="e61f8-129">Uses basic authentication.</span></span>|
|`Digest`|<span data-ttu-id="e61f8-130">Özet kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="e61f8-130">Uses digest authentication.</span></span>|
|`Ntlm`|<span data-ttu-id="e61f8-131">Windows etki alanı ile geri dönüş olarak NTLM kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="e61f8-131">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|
|`Windows`|<span data-ttu-id="e61f8-132">Tümleşik Windows kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="e61f8-132">Uses integrated Windows authentication.</span></span>|
|`Certificate`|<span data-ttu-id="e61f8-133">İstemcinin kimliğini doğrulamak için X. 509.440 sertifikalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="e61f8-133">Uses X.509 certificates to authenticate the client.</span></span>|

## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="e61f8-134">proxyCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="e61f8-134">proxyCredentialType Attribute</span></span>

|<span data-ttu-id="e61f8-135">Değer</span><span class="sxs-lookup"><span data-stu-id="e61f8-135">Value</span></span>|<span data-ttu-id="e61f8-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e61f8-136">Description</span></span>|
|-----------|-----------------|
|`None`|<span data-ttu-id="e61f8-137">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="e61f8-137">Security is disabled.</span></span>|
|`Basic`|<span data-ttu-id="e61f8-138">Temel kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="e61f8-138">Uses basic authentication.</span></span>|
|`Digest`|<span data-ttu-id="e61f8-139">Özet kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="e61f8-139">Uses digest authentication.</span></span>|
|`Ntlm`|<span data-ttu-id="e61f8-140">Windows etki alanı ile geri dönüş olarak NTLM kullanır.</span><span class="sxs-lookup"><span data-stu-id="e61f8-140">Uses NTLM as a fallback with a Windows domain.</span></span>|
|`Windows`|<span data-ttu-id="e61f8-141">Tümleşik Windows kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="e61f8-141">Uses integrated Windows authentication.</span></span>|
|`Certificate`|<span data-ttu-id="e61f8-142">İstemcinin kimliğini doğrulamak için X. 509.440 sertifikalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="e61f8-142">Uses X.509 certificates to authenticate the client.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="e61f8-143">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e61f8-143">Child Elements</span></span>

<span data-ttu-id="e61f8-144">Yok.</span><span class="sxs-lookup"><span data-stu-id="e61f8-144">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e61f8-145">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e61f8-145">Parent Elements</span></span>

|<span data-ttu-id="e61f8-146">Öğe</span><span class="sxs-lookup"><span data-stu-id="e61f8-146">Element</span></span>|<span data-ttu-id="e61f8-147">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e61f8-147">Description</span></span>|
|-------------|-----------------|
|[\<security>](security-of-wshttpbinding.md)|<span data-ttu-id="e61f8-148">Öğesinin güvenlik yeteneklerini temsil eder [\<wsHttpBinding>](wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="e61f8-148">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md).</span></span>|

## <a name="see-also"></a><span data-ttu-id="e61f8-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e61f8-149">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [<span data-ttu-id="e61f8-150">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="e61f8-150">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="e61f8-151">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="e61f8-151">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="e61f8-152">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e61f8-152">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="e61f8-153">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="e61f8-153">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)

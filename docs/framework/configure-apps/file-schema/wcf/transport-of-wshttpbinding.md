---
title: <transport> / <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 21e38acf-450a-4bda-82b6-de305e1f7cd8
ms.openlocfilehash: 1afeed62fcbf3b083d69a7cedb7eb80b81f5c17b
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73732744"
---
# <a name="transport-of-wshttpbinding"></a><span data-ttu-id="5bb0d-102">\<taşıma > \<wsHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="5bb0d-102">\<transport> of \<wsHttpBinding></span></span>

<span data-ttu-id="5bb0d-103">HTTP taşıması için kimlik doğrulama ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5bb0d-103">Defines authentication settings for the HTTP transport.</span></span>

<span data-ttu-id="5bb0d-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="5bb0d-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5bb0d-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="5bb0d-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="5bb0d-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlamaları >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="5bb0d-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="5bb0d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsHttpBinding >** ](wshttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="5bb0d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsHttpBinding>**](wshttpbinding.md)</span></span>\
<span data-ttu-id="5bb0d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="5bb0d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="5bb0d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<güvenlik >** ](security-of-wshttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="5bb0d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wshttpbinding.md)</span></span>\
<span data-ttu-id="5bb0d-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<taşıma >**</span><span class="sxs-lookup"><span data-stu-id="5bb0d-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="5bb0d-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5bb0d-111">Syntax</span></span>

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

## <a name="type"></a><span data-ttu-id="5bb0d-112">Tür</span><span class="sxs-lookup"><span data-stu-id="5bb0d-112">Type</span></span>

<xref:System.ServiceModel.HttpTransportSecurity>

## <a name="attributes-and-elements"></a><span data-ttu-id="5bb0d-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5bb0d-113">Attributes and Elements</span></span>

<span data-ttu-id="5bb0d-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5bb0d-114">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="5bb0d-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5bb0d-115">Attributes</span></span>

|<span data-ttu-id="5bb0d-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5bb0d-116">Attribute</span></span>|<span data-ttu-id="5bb0d-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5bb0d-117">Description</span></span>|
|---------------|-----------------|
|`clientCredentialType`|<span data-ttu-id="5bb0d-118">Hizmetin istemcinin kimliğini doğrulamak için kullanılan kimlik bilgisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5bb0d-118">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="5bb0d-119">Bu öznitelik <xref:System.ServiceModel.HttpClientCredentialType>türündedir.</span><span class="sxs-lookup"><span data-stu-id="5bb0d-119">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|
|`proxyCredentialType`|<span data-ttu-id="5bb0d-120">Bir etki alanı ara sunucusu için istemcinin kimliğini doğrulamak için kullanılan kimlik bilgisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5bb0d-120">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="5bb0d-121">Bu öznitelik <xref:System.ServiceModel.HttpProxyCredentialType>türündedir.</span><span class="sxs-lookup"><span data-stu-id="5bb0d-121">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|
|`realm`|<span data-ttu-id="5bb0d-122">Özet veya temel kimlik doğrulaması için kimlik doğrulama bölgesini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="5bb0d-122">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="5bb0d-123">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="5bb0d-123">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="5bb0d-124">Kimlik doğrulama bölgesi, kimlik doğrulamasını gerçekleştiren konağın en azından adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5bb0d-124">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="5bb0d-125">Ayrıca, erişimi olan bir kullanıcı koleksiyonu da belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="5bb0d-125">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="5bb0d-126">Kullanıcı, birkaç olası Kullanıcı adı ve parolanın kullanılabileceğini belirlemek için kimlik doğrulama bölgesini sorgulayabilir.</span><span class="sxs-lookup"><span data-stu-id="5bb0d-126">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|
|`policyEnforcement`|<span data-ttu-id="5bb0d-127">Bu sabit listesi <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> ne zaman uygulanacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5bb0d-127">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="5bb0d-128">1. hiçbir süre – ilke hiçbir şekilde zorlanmaz (genişletilmiş koruma devre dışı bırakılır).</span><span class="sxs-lookup"><span data-stu-id="5bb0d-128">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="5bb0d-129">2. WhenSupported – ilke yalnızca istemci genişletilmiş korumayı destekliyorsa zorlanır.</span><span class="sxs-lookup"><span data-stu-id="5bb0d-129">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="5bb0d-130">3. her zaman – ilke her zaman zorlanır.</span><span class="sxs-lookup"><span data-stu-id="5bb0d-130">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="5bb0d-131">Genişletilmiş korumayı desteklemeyen istemciler kimlik doğrulaması yapamaz.</span><span class="sxs-lookup"><span data-stu-id="5bb0d-131">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|

## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="5bb0d-132">clientCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="5bb0d-132">clientCredentialType Attribute</span></span>

|<span data-ttu-id="5bb0d-133">Değer</span><span class="sxs-lookup"><span data-stu-id="5bb0d-133">Value</span></span>|<span data-ttu-id="5bb0d-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5bb0d-134">Description</span></span>|
|-----------|-----------------|
|`None`|<span data-ttu-id="5bb0d-135">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="5bb0d-135">Security is disabled.</span></span>|
|`Basic`|<span data-ttu-id="5bb0d-136">Temel kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="5bb0d-136">Uses basic authentication.</span></span>|
|`Digest`|<span data-ttu-id="5bb0d-137">Özet kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="5bb0d-137">Uses digest authentication.</span></span>|
|`Ntlm`|<span data-ttu-id="5bb0d-138">Windows etki alanı ile geri dönüş olarak NTLM kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="5bb0d-138">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|
|`Windows`|<span data-ttu-id="5bb0d-139">Tümleşik Windows kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="5bb0d-139">Uses integrated Windows authentication.</span></span>|
|`Certificate`|<span data-ttu-id="5bb0d-140">İstemcinin kimliğini doğrulamak için X. 509.440 sertifikalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="5bb0d-140">Uses X.509 certificates to authenticate the client.</span></span>|

## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="5bb0d-141">proxyCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="5bb0d-141">proxyCredentialType Attribute</span></span>

|<span data-ttu-id="5bb0d-142">Değer</span><span class="sxs-lookup"><span data-stu-id="5bb0d-142">Value</span></span>|<span data-ttu-id="5bb0d-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5bb0d-143">Description</span></span>|
|-----------|-----------------|
|`None`|<span data-ttu-id="5bb0d-144">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="5bb0d-144">Security is disabled.</span></span>|
|`Basic`|<span data-ttu-id="5bb0d-145">Temel kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="5bb0d-145">Uses basic authentication.</span></span>|
|`Digest`|<span data-ttu-id="5bb0d-146">Özet kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="5bb0d-146">Uses digest authentication.</span></span>|
|`Ntlm`|<span data-ttu-id="5bb0d-147">Windows etki alanı ile geri dönüş olarak NTLM kullanır.</span><span class="sxs-lookup"><span data-stu-id="5bb0d-147">Uses NTLM as a fallback with a Windows domain.</span></span>|
|`Windows`|<span data-ttu-id="5bb0d-148">Tümleşik Windows kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="5bb0d-148">Uses integrated Windows authentication.</span></span>|
|`Certificate`|<span data-ttu-id="5bb0d-149">İstemcinin kimliğini doğrulamak için X. 509.440 sertifikalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="5bb0d-149">Uses X.509 certificates to authenticate the client.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="5bb0d-150">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5bb0d-150">Child Elements</span></span>

<span data-ttu-id="5bb0d-151">Yok.</span><span class="sxs-lookup"><span data-stu-id="5bb0d-151">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5bb0d-152">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5bb0d-152">Parent Elements</span></span>

|<span data-ttu-id="5bb0d-153">Öğe</span><span class="sxs-lookup"><span data-stu-id="5bb0d-153">Element</span></span>|<span data-ttu-id="5bb0d-154">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5bb0d-154">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5bb0d-155">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="5bb0d-155">\<security></span></span>](security-of-wshttpbinding.md)|<span data-ttu-id="5bb0d-156">[\<wsHttpBinding >](wshttpbinding.md)'nin güvenlik yeteneklerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5bb0d-156">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md).</span></span>|

## <a name="see-also"></a><span data-ttu-id="5bb0d-157">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5bb0d-157">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [<span data-ttu-id="5bb0d-158">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="5bb0d-158">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="5bb0d-159">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="5bb0d-159">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="5bb0d-160">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="5bb0d-160">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="5bb0d-161">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="5bb0d-161">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="5bb0d-162">\< bağlama ></span><span class="sxs-lookup"><span data-stu-id="5bb0d-162">\<binding></span></span>](bindings.md)

---
title: <transport> / <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 21e38acf-450a-4bda-82b6-de305e1f7cd8
ms.openlocfilehash: 384267e3d018d714f95356461eb303bc9ec0cb3e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934633"
---
# <a name="transport-of-wshttpbinding"></a><span data-ttu-id="49fd0-102">\<\<WSHttpBinding > taşıma ></span><span class="sxs-lookup"><span data-stu-id="49fd0-102">\<transport> of \<wsHttpBinding></span></span>

<span data-ttu-id="49fd0-103">HTTP taşıması için kimlik doğrulama ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="49fd0-103">Defines authentication settings for the HTTP transport.</span></span>

<span data-ttu-id="49fd0-104">\<System. serviceModel > </span><span class="sxs-lookup"><span data-stu-id="49fd0-104">\<system.serviceModel></span></span>\
<span data-ttu-id="49fd0-105">\<bağlamalar > </span><span class="sxs-lookup"><span data-stu-id="49fd0-105">\<bindings></span></span>\
<span data-ttu-id="49fd0-106">\<wsHttpBinding > </span><span class="sxs-lookup"><span data-stu-id="49fd0-106">\<wsHttpBinding></span></span>\
<span data-ttu-id="49fd0-107">\<bağlama > </span><span class="sxs-lookup"><span data-stu-id="49fd0-107">\<binding></span></span>\
<span data-ttu-id="49fd0-108">\<Güvenlik > </span><span class="sxs-lookup"><span data-stu-id="49fd0-108">\<security></span></span>\
<span data-ttu-id="49fd0-109">\<Taşıma ></span><span class="sxs-lookup"><span data-stu-id="49fd0-109">\<transport></span></span>

## <a name="syntax"></a><span data-ttu-id="49fd0-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="49fd0-110">Syntax</span></span>

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

## <a name="type"></a><span data-ttu-id="49fd0-111">Tür</span><span class="sxs-lookup"><span data-stu-id="49fd0-111">Type</span></span>

<xref:System.ServiceModel.HttpTransportSecurity>

## <a name="attributes-and-elements"></a><span data-ttu-id="49fd0-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="49fd0-112">Attributes and Elements</span></span>

<span data-ttu-id="49fd0-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="49fd0-113">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="49fd0-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="49fd0-114">Attributes</span></span>

|<span data-ttu-id="49fd0-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="49fd0-115">Attribute</span></span>|<span data-ttu-id="49fd0-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="49fd0-116">Description</span></span>|
|---------------|-----------------|
|`clientCredentialType`|<span data-ttu-id="49fd0-117">Hizmetin istemcinin kimliğini doğrulamak için kullanılan kimlik bilgisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="49fd0-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="49fd0-118">Bu öznitelik türü <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="49fd0-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|
|`proxyCredentialType`|<span data-ttu-id="49fd0-119">Bir etki alanı ara sunucusu için istemcinin kimliğini doğrulamak için kullanılan kimlik bilgisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="49fd0-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="49fd0-120">Bu öznitelik türü <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="49fd0-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|
|`realm`|<span data-ttu-id="49fd0-121">Özet veya temel kimlik doğrulaması için kimlik doğrulama bölgesini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="49fd0-121">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="49fd0-122">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="49fd0-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="49fd0-123">Kimlik doğrulama bölgesi, kimlik doğrulamasını gerçekleştiren konağın en azından adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="49fd0-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="49fd0-124">Ayrıca, erişimi olan bir kullanıcı koleksiyonu da belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="49fd0-124">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="49fd0-125">Kullanıcı, birkaç olası Kullanıcı adı ve parolanın kullanılabileceğini belirlemek için kimlik doğrulama bölgesini sorgulayabilir.</span><span class="sxs-lookup"><span data-stu-id="49fd0-125">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|
|`policyEnforcement`|<span data-ttu-id="49fd0-126">Bu numaralandırma, <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> ne zaman uygulanacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="49fd0-126">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="49fd0-127">1.  Hiçbir süre – ilke hiçbir şekilde zorlanmaz (genişletilmiş koruma devre dışı bırakılır).</span><span class="sxs-lookup"><span data-stu-id="49fd0-127">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="49fd0-128">2.  WhenSupported – ilke yalnızca istemci genişletilmiş korumayı destekliyorsa zorlanır.</span><span class="sxs-lookup"><span data-stu-id="49fd0-128">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="49fd0-129">3.  Her zaman – ilke her zaman zorlanır.</span><span class="sxs-lookup"><span data-stu-id="49fd0-129">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="49fd0-130">Genişletilmiş korumayı desteklemeyen istemciler kimlik doğrulaması yapamaz.</span><span class="sxs-lookup"><span data-stu-id="49fd0-130">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|

## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="49fd0-131">clientCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="49fd0-131">clientCredentialType Attribute</span></span>

|<span data-ttu-id="49fd0-132">Değer</span><span class="sxs-lookup"><span data-stu-id="49fd0-132">Value</span></span>|<span data-ttu-id="49fd0-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="49fd0-133">Description</span></span>|
|-----------|-----------------|
|`None`|<span data-ttu-id="49fd0-134">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="49fd0-134">Security is disabled.</span></span>|
|`Basic`|<span data-ttu-id="49fd0-135">Temel kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="49fd0-135">Uses basic authentication.</span></span>|
|`Digest`|<span data-ttu-id="49fd0-136">Özet kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="49fd0-136">Uses digest authentication.</span></span>|
|`Ntlm`|<span data-ttu-id="49fd0-137">Windows etki alanı ile geri dönüş olarak NTLM kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="49fd0-137">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|
|`Windows`|<span data-ttu-id="49fd0-138">Tümleşik Windows kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="49fd0-138">Uses integrated Windows authentication.</span></span>|
|`Certificate`|<span data-ttu-id="49fd0-139">İstemcinin kimliğini doğrulamak için X. 509.440 sertifikalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="49fd0-139">Uses X.509 certificates to authenticate the client.</span></span>|

## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="49fd0-140">proxyCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="49fd0-140">proxyCredentialType Attribute</span></span>

|<span data-ttu-id="49fd0-141">Değer</span><span class="sxs-lookup"><span data-stu-id="49fd0-141">Value</span></span>|<span data-ttu-id="49fd0-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="49fd0-142">Description</span></span>|
|-----------|-----------------|
|`None`|<span data-ttu-id="49fd0-143">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="49fd0-143">Security is disabled.</span></span>|
|`Basic`|<span data-ttu-id="49fd0-144">Temel kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="49fd0-144">Uses basic authentication.</span></span>|
|`Digest`|<span data-ttu-id="49fd0-145">Özet kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="49fd0-145">Uses digest authentication.</span></span>|
|`Ntlm`|<span data-ttu-id="49fd0-146">Windows etki alanı ile geri dönüş olarak NTLM kullanır.</span><span class="sxs-lookup"><span data-stu-id="49fd0-146">Uses NTLM as a fallback with a Windows domain.</span></span>|
|`Windows`|<span data-ttu-id="49fd0-147">Tümleşik Windows kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="49fd0-147">Uses integrated Windows authentication.</span></span>|
|`Certificate`|<span data-ttu-id="49fd0-148">İstemcinin kimliğini doğrulamak için X. 509.440 sertifikalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="49fd0-148">Uses X.509 certificates to authenticate the client.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="49fd0-149">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="49fd0-149">Child Elements</span></span>

<span data-ttu-id="49fd0-150">Yok.</span><span class="sxs-lookup"><span data-stu-id="49fd0-150">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="49fd0-151">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="49fd0-151">Parent Elements</span></span>

|<span data-ttu-id="49fd0-152">Öğe</span><span class="sxs-lookup"><span data-stu-id="49fd0-152">Element</span></span>|<span data-ttu-id="49fd0-153">Açıklama</span><span class="sxs-lookup"><span data-stu-id="49fd0-153">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="49fd0-154">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="49fd0-154">\<security></span></span>](security-of-wshttpbinding.md)|<span data-ttu-id="49fd0-155">[ \<WSHttpBinding >](wshttpbinding.md)'nin güvenlik yeteneklerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="49fd0-155">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md).</span></span>|

## <a name="see-also"></a><span data-ttu-id="49fd0-156">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="49fd0-156">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [<span data-ttu-id="49fd0-157">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="49fd0-157">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="49fd0-158">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="49fd0-158">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="49fd0-159">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="49fd0-159">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="49fd0-160">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="49fd0-160">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="49fd0-161">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="49fd0-161">\<binding></span></span>](../../../misc/binding.md)

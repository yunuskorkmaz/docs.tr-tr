---
title: <transport> / <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 21e38acf-450a-4bda-82b6-de305e1f7cd8
ms.openlocfilehash: 95cfa076f62f767af431ff5a0bcc2ca31b824e30
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399237"
---
# <a name="transport-of-wshttpbinding"></a><span data-ttu-id="0ebdf-102">\<\<WSHttpBinding > taşıma ></span><span class="sxs-lookup"><span data-stu-id="0ebdf-102">\<transport> of \<wsHttpBinding></span></span>

<span data-ttu-id="0ebdf-103">HTTP taşıması için kimlik doğrulama ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0ebdf-103">Defines authentication settings for the HTTP transport.</span></span>

<span data-ttu-id="0ebdf-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0ebdf-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0ebdf-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="0ebdf-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="0ebdf-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlama >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="0ebdf-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="0ebdf-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsHttpBinding >** ](wshttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="0ebdf-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsHttpBinding>**](wshttpbinding.md)</span></span>\
<span data-ttu-id="0ebdf-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="0ebdf-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="0ebdf-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Güvenlik >** ](security-of-wshttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="0ebdf-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wshttpbinding.md)</span></span>\
<span data-ttu-id="0ebdf-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Taşıma >**</span><span class="sxs-lookup"><span data-stu-id="0ebdf-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="0ebdf-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0ebdf-111">Syntax</span></span>

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

## <a name="type"></a><span data-ttu-id="0ebdf-112">Tür</span><span class="sxs-lookup"><span data-stu-id="0ebdf-112">Type</span></span>

<xref:System.ServiceModel.HttpTransportSecurity>

## <a name="attributes-and-elements"></a><span data-ttu-id="0ebdf-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0ebdf-113">Attributes and Elements</span></span>

<span data-ttu-id="0ebdf-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0ebdf-114">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="0ebdf-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0ebdf-115">Attributes</span></span>

|<span data-ttu-id="0ebdf-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0ebdf-116">Attribute</span></span>|<span data-ttu-id="0ebdf-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0ebdf-117">Description</span></span>|
|---------------|-----------------|
|`clientCredentialType`|<span data-ttu-id="0ebdf-118">Hizmetin istemcinin kimliğini doğrulamak için kullanılan kimlik bilgisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0ebdf-118">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="0ebdf-119">Bu öznitelik türü <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="0ebdf-119">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|
|`proxyCredentialType`|<span data-ttu-id="0ebdf-120">Bir etki alanı ara sunucusu için istemcinin kimliğini doğrulamak için kullanılan kimlik bilgisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0ebdf-120">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="0ebdf-121">Bu öznitelik türü <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="0ebdf-121">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|
|`realm`|<span data-ttu-id="0ebdf-122">Özet veya temel kimlik doğrulaması için kimlik doğrulama bölgesini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="0ebdf-122">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="0ebdf-123">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="0ebdf-123">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="0ebdf-124">Kimlik doğrulama bölgesi, kimlik doğrulamasını gerçekleştiren konağın en azından adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0ebdf-124">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="0ebdf-125">Ayrıca, erişimi olan bir kullanıcı koleksiyonu da belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="0ebdf-125">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="0ebdf-126">Kullanıcı, birkaç olası Kullanıcı adı ve parolanın kullanılabileceğini belirlemek için kimlik doğrulama bölgesini sorgulayabilir.</span><span class="sxs-lookup"><span data-stu-id="0ebdf-126">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|
|`policyEnforcement`|<span data-ttu-id="0ebdf-127">Bu numaralandırma, <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> ne zaman uygulanacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0ebdf-127">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="0ebdf-128">1.  Hiçbir süre – ilke hiçbir şekilde zorlanmaz (genişletilmiş koruma devre dışı bırakılır).</span><span class="sxs-lookup"><span data-stu-id="0ebdf-128">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="0ebdf-129">2.  WhenSupported – ilke yalnızca istemci genişletilmiş korumayı destekliyorsa zorlanır.</span><span class="sxs-lookup"><span data-stu-id="0ebdf-129">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="0ebdf-130">3.  Her zaman – ilke her zaman zorlanır.</span><span class="sxs-lookup"><span data-stu-id="0ebdf-130">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="0ebdf-131">Genişletilmiş korumayı desteklemeyen istemciler kimlik doğrulaması yapamaz.</span><span class="sxs-lookup"><span data-stu-id="0ebdf-131">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|

## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="0ebdf-132">clientCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="0ebdf-132">clientCredentialType Attribute</span></span>

|<span data-ttu-id="0ebdf-133">Değer</span><span class="sxs-lookup"><span data-stu-id="0ebdf-133">Value</span></span>|<span data-ttu-id="0ebdf-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0ebdf-134">Description</span></span>|
|-----------|-----------------|
|`None`|<span data-ttu-id="0ebdf-135">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="0ebdf-135">Security is disabled.</span></span>|
|`Basic`|<span data-ttu-id="0ebdf-136">Temel kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="0ebdf-136">Uses basic authentication.</span></span>|
|`Digest`|<span data-ttu-id="0ebdf-137">Özet kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="0ebdf-137">Uses digest authentication.</span></span>|
|`Ntlm`|<span data-ttu-id="0ebdf-138">Windows etki alanı ile geri dönüş olarak NTLM kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="0ebdf-138">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|
|`Windows`|<span data-ttu-id="0ebdf-139">Tümleşik Windows kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="0ebdf-139">Uses integrated Windows authentication.</span></span>|
|`Certificate`|<span data-ttu-id="0ebdf-140">İstemcinin kimliğini doğrulamak için X. 509.440 sertifikalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="0ebdf-140">Uses X.509 certificates to authenticate the client.</span></span>|

## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="0ebdf-141">proxyCredentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="0ebdf-141">proxyCredentialType Attribute</span></span>

|<span data-ttu-id="0ebdf-142">Değer</span><span class="sxs-lookup"><span data-stu-id="0ebdf-142">Value</span></span>|<span data-ttu-id="0ebdf-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0ebdf-143">Description</span></span>|
|-----------|-----------------|
|`None`|<span data-ttu-id="0ebdf-144">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="0ebdf-144">Security is disabled.</span></span>|
|`Basic`|<span data-ttu-id="0ebdf-145">Temel kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="0ebdf-145">Uses basic authentication.</span></span>|
|`Digest`|<span data-ttu-id="0ebdf-146">Özet kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="0ebdf-146">Uses digest authentication.</span></span>|
|`Ntlm`|<span data-ttu-id="0ebdf-147">Windows etki alanı ile geri dönüş olarak NTLM kullanır.</span><span class="sxs-lookup"><span data-stu-id="0ebdf-147">Uses NTLM as a fallback with a Windows domain.</span></span>|
|`Windows`|<span data-ttu-id="0ebdf-148">Tümleşik Windows kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="0ebdf-148">Uses integrated Windows authentication.</span></span>|
|`Certificate`|<span data-ttu-id="0ebdf-149">İstemcinin kimliğini doğrulamak için X. 509.440 sertifikalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="0ebdf-149">Uses X.509 certificates to authenticate the client.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="0ebdf-150">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0ebdf-150">Child Elements</span></span>

<span data-ttu-id="0ebdf-151">Yok.</span><span class="sxs-lookup"><span data-stu-id="0ebdf-151">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0ebdf-152">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0ebdf-152">Parent Elements</span></span>

|<span data-ttu-id="0ebdf-153">Öğe</span><span class="sxs-lookup"><span data-stu-id="0ebdf-153">Element</span></span>|<span data-ttu-id="0ebdf-154">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0ebdf-154">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0ebdf-155">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="0ebdf-155">\<security></span></span>](security-of-wshttpbinding.md)|<span data-ttu-id="0ebdf-156">[ \<WSHttpBinding >](wshttpbinding.md)'nin güvenlik yeteneklerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0ebdf-156">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md).</span></span>|

## <a name="see-also"></a><span data-ttu-id="0ebdf-157">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ebdf-157">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [<span data-ttu-id="0ebdf-158">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="0ebdf-158">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="0ebdf-159">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="0ebdf-159">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="0ebdf-160">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="0ebdf-160">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="0ebdf-161">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="0ebdf-161">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="0ebdf-162">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="0ebdf-162">\<binding></span></span>](../../../misc/binding.md)

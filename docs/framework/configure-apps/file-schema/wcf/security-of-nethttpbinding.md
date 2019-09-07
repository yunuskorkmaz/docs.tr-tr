---
title: <security> / <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: dc41f6f7-cabc-4a64-9fa0-ceabf861b348
ms.openlocfilehash: 890cee3271c410a921b3a88f78d0705ba8718252
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399850"
---
# <a name="security-of-nethttpbinding"></a><span data-ttu-id="81340-102">\<\<NetHttpBinding > Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="81340-102">\<security> of \<netHttpBinding></span></span>

<span data-ttu-id="81340-103">[ \<NetHttpBinding >](nethttpbinding.md)'nin güvenlik yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="81340-103">Defines the security capabilities of the [\<netHttpBinding>](nethttpbinding.md).</span></span>

<span data-ttu-id="81340-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="81340-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="81340-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="81340-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="81340-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlama >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="81340-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="81340-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netHttpBinding >** ](nethttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="81340-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)</span></span>\
<span data-ttu-id="81340-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="81340-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="81340-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Güvenlik >**</span><span class="sxs-lookup"><span data-stu-id="81340-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="81340-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="81340-110">Syntax</span></span>

```xml
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="string" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="81340-111">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="81340-111">Attributes and elements</span></span>

<span data-ttu-id="81340-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="81340-112">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="81340-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="81340-113">Attributes</span></span>

|<span data-ttu-id="81340-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="81340-114">Attribute</span></span>|<span data-ttu-id="81340-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="81340-115">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="81340-116">mod</span><span class="sxs-lookup"><span data-stu-id="81340-116">mode</span></span>|<span data-ttu-id="81340-117">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="81340-117">Optional.</span></span> <span data-ttu-id="81340-118">Kullanılan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="81340-118">Specifies the type of security that is used.</span></span> <span data-ttu-id="81340-119">Varsayılan, `None` değeridir.</span><span class="sxs-lookup"><span data-stu-id="81340-119">The default is `None`.</span></span> <span data-ttu-id="81340-120">Bu öznitelik türü <xref:System.ServiceModel.BasicHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="81340-120">This attribute is of type <xref:System.ServiceModel.BasicHttpSecurityMode>.</span></span>|

## <a name="mode-attribute"></a><span data-ttu-id="81340-121">mode özniteliği</span><span class="sxs-lookup"><span data-stu-id="81340-121">mode attribute</span></span>

|<span data-ttu-id="81340-122">Değer</span><span class="sxs-lookup"><span data-stu-id="81340-122">Value</span></span>|<span data-ttu-id="81340-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="81340-123">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="81340-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="81340-124">None</span></span>|<span data-ttu-id="81340-125">-İletiler aktarım sırasında güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="81340-125">-   Messages are not secured during transfer.</span></span>|
|<span data-ttu-id="81340-126">Aktarım</span><span class="sxs-lookup"><span data-stu-id="81340-126">Transport</span></span>|<span data-ttu-id="81340-127">Güvenlik, HTTPS taşıması kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="81340-127">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="81340-128">SOAP iletilerinin HTTPS kullanılarak güvenliği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="81340-128">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="81340-129">Hizmetin, hizmetin X. 509.440 sertifikası kullanılarak istemcinin kimliği doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="81340-129">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="81340-130">İstemcinin kimliği, sağlanan ClientCredentialType kullanılarak doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="81340-130">The client is authenticated using the ClientCredentialType supplied.</span></span>|
|<span data-ttu-id="81340-131">`Message`</span><span class="sxs-lookup"><span data-stu-id="81340-131">Message</span></span>|<span data-ttu-id="81340-132">Güvenlik, SOAP iletisi güvenliği kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="81340-132">Security is provided using SOAP message security.</span></span> <span data-ttu-id="81340-133">Varsayılan olarak, gövde şifrelenir ve imzalanır.</span><span class="sxs-lookup"><span data-stu-id="81340-133">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="81340-134">Bu bağlama için, sistem, sunucu sertifikasının bant dışı istemciye sağlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="81340-134">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="81340-135">`ClientCredentialType` Bu`Certificate`bağlama için geçerli tek geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="81340-135">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|
|<span data-ttu-id="81340-136">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="81340-136">TransportWithMessageCredential</span></span>|<span data-ttu-id="81340-137">Bütünlük, gizlilik ve sunucu kimlik doğrulaması, aktarım güvenliği tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="81340-137">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="81340-138">İstemci kimlik doğrulaması, SOAP iletisi güvenliği aracılığıyla sağlanır.</span><span class="sxs-lookup"><span data-stu-id="81340-138">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="81340-139">Bu mod, Kullanıcı Kullanıcı adı/parola kullanarak kimlik doğrulaması yapıldığında ve ileti aktarımını güvenli hale getirmek için mevcut bir HTTP dağıtımı olduğunda geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="81340-139">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|
|<span data-ttu-id="81340-140">Yalnızca transportcredential</span><span class="sxs-lookup"><span data-stu-id="81340-140">TransportCredentialOnly</span></span>|<span data-ttu-id="81340-141">Bu mod ileti bütünlüğü ve gizliliği sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="81340-141">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="81340-142">HTTP tabanlı istemci kimlik doğrulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="81340-142">It provides http-based client authentication.</span></span> <span data-ttu-id="81340-143">Bu mod dikkatli kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="81340-143">This mode should be used with caution.</span></span> <span data-ttu-id="81340-144">Aktarım güvenliğinin diğer yollarla (IPSec gibi) sağlandığı ve yalnızca WCF altyapısı tarafından istemci kimlik doğrulamasının sağlandığı ortamlarda kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="81340-144">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="81340-145">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="81340-145">Child elements</span></span>

|<span data-ttu-id="81340-146">Öğe</span><span class="sxs-lookup"><span data-stu-id="81340-146">Element</span></span>|<span data-ttu-id="81340-147">Açıklama</span><span class="sxs-lookup"><span data-stu-id="81340-147">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="81340-148">\<Taşıma ></span><span class="sxs-lookup"><span data-stu-id="81340-148">\<transport></span></span>](transport-of-nethttpbinding.md)|<span data-ttu-id="81340-149">Temel bir HTTP hizmeti için taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="81340-149">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="81340-150">Bu öğe öğesine <xref:System.ServiceModel.HttpTransportSecurity>karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="81340-150">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|
|[<span data-ttu-id="81340-151">\<ileti ></span><span class="sxs-lookup"><span data-stu-id="81340-151">\<message></span></span>](message-of-nethttpbinding.md)|<span data-ttu-id="81340-152">Temel bir HTTP hizmeti için ileti güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="81340-152">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="81340-153">Bu öğe öğesine <xref:System.ServiceModel.BasicHttpMessageSecurity>karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="81340-153">This element corresponds to <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="81340-154">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="81340-154">Parent elements</span></span>

|<span data-ttu-id="81340-155">Öğe</span><span class="sxs-lookup"><span data-stu-id="81340-155">Element</span></span>|<span data-ttu-id="81340-156">Açıklama</span><span class="sxs-lookup"><span data-stu-id="81340-156">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="81340-157">bağlama</span><span class="sxs-lookup"><span data-stu-id="81340-157">binding</span></span>|<span data-ttu-id="81340-158">BasicHttpBinding > Binding öğesi. [ \<](basichttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="81340-158">The binding element of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|

## <a name="remarks"></a><span data-ttu-id="81340-159">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="81340-159">Remarks</span></span>

 <span data-ttu-id="81340-160">Varsayılan olarak, SOAP iletisi güvenli değildir ve istemcinin kimliği doğrulanmaz.</span><span class="sxs-lookup"><span data-stu-id="81340-160">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="81340-161">Bu öğe, `netHttpBinding` öğesi için ek güvenlik ayarları yapılandırmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="81340-161">This element enables you to configure additional security settings for the `netHttpBinding` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="81340-162">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="81340-162">See also</span></span>

- <xref:System.ServiceModel.NetHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetHttpBindingElement.Security%2A>  
- [<span data-ttu-id="81340-163">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="81340-163">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="81340-164">Kimlik Bilgisi Türü Seçme</span><span class="sxs-lookup"><span data-stu-id="81340-164">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="81340-165">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="81340-165">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="81340-166">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="81340-166">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="81340-167">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="81340-167">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="81340-168">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="81340-168">\<binding></span></span>](../../../misc/binding.md)

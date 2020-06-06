---
title: <security> / <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: dc41f6f7-cabc-4a64-9fa0-ceabf861b348
ms.openlocfilehash: 97c52fa4f062ed0c65d5b1a8ca47a1439ab04cf5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736485"
---
# <a name="security-of-nethttpbinding"></a><span data-ttu-id="d144e-102">\<security> / \<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="d144e-102">\<security> of \<netHttpBinding></span></span>

<span data-ttu-id="d144e-103">Uygulamasının güvenlik yeteneklerini tanımlar [\<netHttpBinding>](nethttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="d144e-103">Defines the security capabilities of the [\<netHttpBinding>](nethttpbinding.md).</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  

## <a name="syntax"></a><span data-ttu-id="d144e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d144e-104">Syntax</span></span>

```xml
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="string" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d144e-105">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="d144e-105">Attributes and elements</span></span>

<span data-ttu-id="d144e-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d144e-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="d144e-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d144e-107">Attributes</span></span>

|<span data-ttu-id="d144e-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d144e-108">Attribute</span></span>|<span data-ttu-id="d144e-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d144e-109">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="d144e-110">mod</span><span class="sxs-lookup"><span data-stu-id="d144e-110">mode</span></span>|<span data-ttu-id="d144e-111">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="d144e-111">Optional.</span></span> <span data-ttu-id="d144e-112">Kullanılan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="d144e-112">Specifies the type of security that is used.</span></span> <span data-ttu-id="d144e-113">Varsayılan değer: `None`.</span><span class="sxs-lookup"><span data-stu-id="d144e-113">The default is `None`.</span></span> <span data-ttu-id="d144e-114">Bu öznitelik türü <xref:System.ServiceModel.BasicHttpSecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="d144e-114">This attribute is of type <xref:System.ServiceModel.BasicHttpSecurityMode>.</span></span>|

## <a name="mode-attribute"></a><span data-ttu-id="d144e-115">mode özniteliği</span><span class="sxs-lookup"><span data-stu-id="d144e-115">mode attribute</span></span>

|<span data-ttu-id="d144e-116">Değer</span><span class="sxs-lookup"><span data-stu-id="d144e-116">Value</span></span>|<span data-ttu-id="d144e-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d144e-117">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="d144e-118">Yok</span><span class="sxs-lookup"><span data-stu-id="d144e-118">None</span></span>|<span data-ttu-id="d144e-119">-İletiler aktarım sırasında güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="d144e-119">-   Messages are not secured during transfer.</span></span>|
|<span data-ttu-id="d144e-120">Aktarım</span><span class="sxs-lookup"><span data-stu-id="d144e-120">Transport</span></span>|<span data-ttu-id="d144e-121">Güvenlik, HTTPS taşıması kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="d144e-121">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="d144e-122">SOAP iletilerinin HTTPS kullanılarak güvenliği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="d144e-122">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="d144e-123">Hizmetin, hizmetin X. 509.440 sertifikası kullanılarak istemcinin kimliği doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="d144e-123">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="d144e-124">İstemcinin kimliği, sağlanan ClientCredentialType kullanılarak doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="d144e-124">The client is authenticated using the ClientCredentialType supplied.</span></span>|
|<span data-ttu-id="d144e-125">İleti</span><span class="sxs-lookup"><span data-stu-id="d144e-125">Message</span></span>|<span data-ttu-id="d144e-126">Güvenlik, SOAP iletisi güvenliği kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="d144e-126">Security is provided using SOAP message security.</span></span> <span data-ttu-id="d144e-127">Varsayılan olarak, gövde şifrelenir ve imzalanır.</span><span class="sxs-lookup"><span data-stu-id="d144e-127">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="d144e-128">Bu bağlama için, sistem, sunucu sertifikasının bant dışı istemciye sağlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d144e-128">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="d144e-129">`ClientCredentialType`Bu bağlama için geçerli tek geçerlidir `Certificate` .</span><span class="sxs-lookup"><span data-stu-id="d144e-129">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|
|<span data-ttu-id="d144e-130">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="d144e-130">TransportWithMessageCredential</span></span>|<span data-ttu-id="d144e-131">Bütünlük, gizlilik ve sunucu kimlik doğrulaması, aktarım güvenliği tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="d144e-131">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="d144e-132">İstemci kimlik doğrulaması, SOAP iletisi güvenliği aracılığıyla sağlanır.</span><span class="sxs-lookup"><span data-stu-id="d144e-132">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="d144e-133">Bu mod, Kullanıcı Kullanıcı adı/parola kullanarak kimlik doğrulaması yapıldığında ve ileti aktarımını güvenli hale getirmek için mevcut bir HTTP dağıtımı olduğunda geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="d144e-133">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|
|<span data-ttu-id="d144e-134">Yalnızca transportcredential</span><span class="sxs-lookup"><span data-stu-id="d144e-134">TransportCredentialOnly</span></span>|<span data-ttu-id="d144e-135">Bu mod ileti bütünlüğü ve gizliliği sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="d144e-135">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="d144e-136">HTTP tabanlı istemci kimlik doğrulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="d144e-136">It provides http-based client authentication.</span></span> <span data-ttu-id="d144e-137">Bu mod dikkatli kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d144e-137">This mode should be used with caution.</span></span> <span data-ttu-id="d144e-138">Aktarım güvenliğinin diğer yollarla (IPSec gibi) sağlandığı ve yalnızca WCF altyapısı tarafından istemci kimlik doğrulamasının sağlandığı ortamlarda kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d144e-138">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="d144e-139">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="d144e-139">Child elements</span></span>

|<span data-ttu-id="d144e-140">Öğe</span><span class="sxs-lookup"><span data-stu-id="d144e-140">Element</span></span>|<span data-ttu-id="d144e-141">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d144e-141">Description</span></span>|
|-------------|-----------------|
|[\<transport>](transport-of-nethttpbinding.md)|<span data-ttu-id="d144e-142">Temel bir HTTP hizmeti için taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d144e-142">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="d144e-143">Bu öğe öğesine karşılık gelir <xref:System.ServiceModel.HttpTransportSecurity> .</span><span class="sxs-lookup"><span data-stu-id="d144e-143">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|
|[\<message>](message-of-nethttpbinding.md)|<span data-ttu-id="d144e-144">Temel bir HTTP hizmeti için ileti güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d144e-144">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="d144e-145">Bu öğe öğesine karşılık gelir <xref:System.ServiceModel.BasicHttpMessageSecurity> .</span><span class="sxs-lookup"><span data-stu-id="d144e-145">This element corresponds to <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d144e-146">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="d144e-146">Parent elements</span></span>

|<span data-ttu-id="d144e-147">Öğe</span><span class="sxs-lookup"><span data-stu-id="d144e-147">Element</span></span>|<span data-ttu-id="d144e-148">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d144e-148">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="d144e-149">bağlama</span><span class="sxs-lookup"><span data-stu-id="d144e-149">binding</span></span>|<span data-ttu-id="d144e-150">Öğesinin bağlama öğesi [\<basicHttpBinding>](basichttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="d144e-150">The binding element of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|

## <a name="remarks"></a><span data-ttu-id="d144e-151">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d144e-151">Remarks</span></span>

 <span data-ttu-id="d144e-152">Varsayılan olarak, SOAP iletisi güvenli değildir ve istemcinin kimliği doğrulanmaz.</span><span class="sxs-lookup"><span data-stu-id="d144e-152">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="d144e-153">Bu öğe, öğesi için ek güvenlik ayarları yapılandırmanıza olanak sağlar `netHttpBinding` .</span><span class="sxs-lookup"><span data-stu-id="d144e-153">This element enables you to configure additional security settings for the `netHttpBinding` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="d144e-154">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d144e-154">See also</span></span>

- <xref:System.ServiceModel.NetHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetHttpBindingElement.Security%2A>  
- [<span data-ttu-id="d144e-155">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="d144e-155">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="d144e-156">Kimlik Bilgisi Türü Seçme</span><span class="sxs-lookup"><span data-stu-id="d144e-156">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="d144e-157">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="d144e-157">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="d144e-158">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d144e-158">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="d144e-159">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="d144e-159">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)

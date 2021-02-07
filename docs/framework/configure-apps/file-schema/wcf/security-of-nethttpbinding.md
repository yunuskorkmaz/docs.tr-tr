---
description: 'Hakkında daha fazla bilgi <security> edinin: <netHttpBinding>'
title: <security> / <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: dc41f6f7-cabc-4a64-9fa0-ceabf861b348
ms.openlocfilehash: 70d6363c0ac7fa00d83880ddc8c873548b385a29
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683131"
---
# <a name="security-of-nethttpbinding"></a><span data-ttu-id="6be5b-103">\<security> / \<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="6be5b-103">\<security> of \<netHttpBinding></span></span>

<span data-ttu-id="6be5b-104">Uygulamasının güvenlik yeteneklerini tanımlar [\<netHttpBinding>](nethttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="6be5b-104">Defines the security capabilities of the [\<netHttpBinding>](nethttpbinding.md).</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  

## <a name="syntax"></a><span data-ttu-id="6be5b-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="6be5b-105">Syntax</span></span>

```xml
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="string" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6be5b-106">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="6be5b-106">Attributes and elements</span></span>

<span data-ttu-id="6be5b-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6be5b-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="6be5b-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6be5b-108">Attributes</span></span>

|<span data-ttu-id="6be5b-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6be5b-109">Attribute</span></span>|<span data-ttu-id="6be5b-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6be5b-110">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="6be5b-111">mod</span><span class="sxs-lookup"><span data-stu-id="6be5b-111">mode</span></span>|<span data-ttu-id="6be5b-112">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="6be5b-112">Optional.</span></span> <span data-ttu-id="6be5b-113">Kullanılan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="6be5b-113">Specifies the type of security that is used.</span></span> <span data-ttu-id="6be5b-114">Varsayılan değer: `None`.</span><span class="sxs-lookup"><span data-stu-id="6be5b-114">The default is `None`.</span></span> <span data-ttu-id="6be5b-115">Bu öznitelik türü <xref:System.ServiceModel.BasicHttpSecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="6be5b-115">This attribute is of type <xref:System.ServiceModel.BasicHttpSecurityMode>.</span></span>|

## <a name="mode-attribute"></a><span data-ttu-id="6be5b-116">mode özniteliği</span><span class="sxs-lookup"><span data-stu-id="6be5b-116">mode attribute</span></span>

|<span data-ttu-id="6be5b-117">Değer</span><span class="sxs-lookup"><span data-stu-id="6be5b-117">Value</span></span>|<span data-ttu-id="6be5b-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6be5b-118">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="6be5b-119">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="6be5b-119">None</span></span>|<span data-ttu-id="6be5b-120">-İletiler aktarım sırasında güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="6be5b-120">-   Messages are not secured during transfer.</span></span>|
|<span data-ttu-id="6be5b-121">Aktarım</span><span class="sxs-lookup"><span data-stu-id="6be5b-121">Transport</span></span>|<span data-ttu-id="6be5b-122">Güvenlik, HTTPS taşıması kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="6be5b-122">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="6be5b-123">SOAP iletilerinin HTTPS kullanılarak güvenliği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="6be5b-123">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="6be5b-124">Hizmetin, hizmetin X. 509.440 sertifikası kullanılarak istemcinin kimliği doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="6be5b-124">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="6be5b-125">İstemcinin kimliği, sağlanan ClientCredentialType kullanılarak doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="6be5b-125">The client is authenticated using the ClientCredentialType supplied.</span></span>|
|<span data-ttu-id="6be5b-126">İleti</span><span class="sxs-lookup"><span data-stu-id="6be5b-126">Message</span></span>|<span data-ttu-id="6be5b-127">Güvenlik, SOAP iletisi güvenliği kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="6be5b-127">Security is provided using SOAP message security.</span></span> <span data-ttu-id="6be5b-128">Varsayılan olarak, gövde şifrelenir ve imzalanır.</span><span class="sxs-lookup"><span data-stu-id="6be5b-128">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="6be5b-129">Bu bağlama için, sistem, sunucu sertifikasının bant dışı istemciye sağlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6be5b-129">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="6be5b-130">`ClientCredentialType`Bu bağlama için geçerli tek geçerlidir `Certificate` .</span><span class="sxs-lookup"><span data-stu-id="6be5b-130">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|
|<span data-ttu-id="6be5b-131">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="6be5b-131">TransportWithMessageCredential</span></span>|<span data-ttu-id="6be5b-132">Bütünlük, gizlilik ve sunucu kimlik doğrulaması, aktarım güvenliği tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="6be5b-132">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="6be5b-133">İstemci kimlik doğrulaması, SOAP iletisi güvenliği aracılığıyla sağlanır.</span><span class="sxs-lookup"><span data-stu-id="6be5b-133">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="6be5b-134">Bu mod, Kullanıcı Kullanıcı adı/parola kullanarak kimlik doğrulaması yapıldığında ve ileti aktarımını güvenli hale getirmek için mevcut bir HTTP dağıtımı olduğunda geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="6be5b-134">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|
|<span data-ttu-id="6be5b-135">Yalnızca transportcredential</span><span class="sxs-lookup"><span data-stu-id="6be5b-135">TransportCredentialOnly</span></span>|<span data-ttu-id="6be5b-136">Bu mod ileti bütünlüğü ve gizliliği sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="6be5b-136">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="6be5b-137">HTTP tabanlı istemci kimlik doğrulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="6be5b-137">It provides http-based client authentication.</span></span> <span data-ttu-id="6be5b-138">Bu mod dikkatli kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6be5b-138">This mode should be used with caution.</span></span> <span data-ttu-id="6be5b-139">Aktarım güvenliğinin diğer yollarla (IPSec gibi) sağlandığı ve yalnızca WCF altyapısı tarafından istemci kimlik doğrulamasının sağlandığı ortamlarda kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6be5b-139">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="6be5b-140">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="6be5b-140">Child elements</span></span>

|<span data-ttu-id="6be5b-141">Öğe</span><span class="sxs-lookup"><span data-stu-id="6be5b-141">Element</span></span>|<span data-ttu-id="6be5b-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6be5b-142">Description</span></span>|
|-------------|-----------------|
|[\<transport>](transport-of-nethttpbinding.md)|<span data-ttu-id="6be5b-143">Temel bir HTTP hizmeti için taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6be5b-143">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="6be5b-144">Bu öğe öğesine karşılık gelir <xref:System.ServiceModel.HttpTransportSecurity> .</span><span class="sxs-lookup"><span data-stu-id="6be5b-144">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|
|[\<message>](message-of-nethttpbinding.md)|<span data-ttu-id="6be5b-145">Temel bir HTTP hizmeti için ileti güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6be5b-145">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="6be5b-146">Bu öğe öğesine karşılık gelir <xref:System.ServiceModel.BasicHttpMessageSecurity> .</span><span class="sxs-lookup"><span data-stu-id="6be5b-146">This element corresponds to <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6be5b-147">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="6be5b-147">Parent elements</span></span>

|<span data-ttu-id="6be5b-148">Öğe</span><span class="sxs-lookup"><span data-stu-id="6be5b-148">Element</span></span>|<span data-ttu-id="6be5b-149">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6be5b-149">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="6be5b-150">bağlama</span><span class="sxs-lookup"><span data-stu-id="6be5b-150">binding</span></span>|<span data-ttu-id="6be5b-151">Öğesinin bağlama öğesi [\<basicHttpBinding>](basichttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="6be5b-151">The binding element of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|

## <a name="remarks"></a><span data-ttu-id="6be5b-152">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6be5b-152">Remarks</span></span>

 <span data-ttu-id="6be5b-153">Varsayılan olarak, SOAP iletisi güvenli değildir ve istemcinin kimliği doğrulanmaz.</span><span class="sxs-lookup"><span data-stu-id="6be5b-153">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="6be5b-154">Bu öğe, öğesi için ek güvenlik ayarları yapılandırmanıza olanak sağlar `netHttpBinding` .</span><span class="sxs-lookup"><span data-stu-id="6be5b-154">This element enables you to configure additional security settings for the `netHttpBinding` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="6be5b-155">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6be5b-155">See also</span></span>

- <xref:System.ServiceModel.NetHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetHttpBindingElement.Security%2A>  
- [<span data-ttu-id="6be5b-156">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="6be5b-156">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="6be5b-157">Kimlik Bilgisi Türü Seçme</span><span class="sxs-lookup"><span data-stu-id="6be5b-157">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="6be5b-158">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="6be5b-158">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="6be5b-159">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6be5b-159">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="6be5b-160">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="6be5b-160">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)

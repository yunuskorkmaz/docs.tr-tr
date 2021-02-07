---
description: 'Hakkında daha fazla bilgi <security> edinin: <basicHttpBinding>'
title: <security> / <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 6432708d-5465-4bd9-bfc2-466742db99cb
ms.openlocfilehash: 92d938d062d56cbb066a1170a9d3b8f3f5ba0186
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683263"
---
# <a name="security-of-basichttpbinding"></a><span data-ttu-id="c0bf1-103">\<security> / \<basicHttpBinding></span><span class="sxs-lookup"><span data-stu-id="c0bf1-103">\<security> of \<basicHttpBinding></span></span>

<span data-ttu-id="c0bf1-104">Uygulamasının güvenlik yeteneklerini tanımlar [\<basicHttpBinding>](basichttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="c0bf1-104">Defines the security capabilities of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<basicHttpBinding>**](basichttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="c0bf1-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="c0bf1-105">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="string" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c0bf1-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c0bf1-106">Attributes and Elements</span></span>  

 <span data-ttu-id="c0bf1-107">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="c0bf1-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c0bf1-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c0bf1-108">Attributes</span></span>  
  
|<span data-ttu-id="c0bf1-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c0bf1-109">Attribute</span></span>|<span data-ttu-id="c0bf1-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c0bf1-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c0bf1-111">mod</span><span class="sxs-lookup"><span data-stu-id="c0bf1-111">mode</span></span>|<span data-ttu-id="c0bf1-112">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c0bf1-112">Optional.</span></span> <span data-ttu-id="c0bf1-113">Kullanılan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="c0bf1-113">Specifies the type of security that is used.</span></span> <span data-ttu-id="c0bf1-114">Varsayılan değer: `None`.</span><span class="sxs-lookup"><span data-stu-id="c0bf1-114">The default is `None`.</span></span> <span data-ttu-id="c0bf1-115">Bu öznitelik türü <xref:System.ServiceModel.BasicHttpSecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="c0bf1-115">This attribute is of type <xref:System.ServiceModel.BasicHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="c0bf1-116">mode özniteliği</span><span class="sxs-lookup"><span data-stu-id="c0bf1-116">mode Attribute</span></span>  
  
|<span data-ttu-id="c0bf1-117">Değer</span><span class="sxs-lookup"><span data-stu-id="c0bf1-117">Value</span></span>|<span data-ttu-id="c0bf1-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c0bf1-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c0bf1-119">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="c0bf1-119">None</span></span>|<span data-ttu-id="c0bf1-120">-İletiler aktarım sırasında güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="c0bf1-120">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="c0bf1-121">Aktarım</span><span class="sxs-lookup"><span data-stu-id="c0bf1-121">Transport</span></span>|<span data-ttu-id="c0bf1-122">Güvenlik, HTTPS taşıması kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="c0bf1-122">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="c0bf1-123">SOAP iletilerinin HTTPS kullanılarak güvenliği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="c0bf1-123">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="c0bf1-124">Hizmetin, hizmetin X. 509.440 sertifikası kullanılarak istemcinin kimliği doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="c0bf1-124">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="c0bf1-125">İstemcinin kimliği, sağlanan ClientCredentialType kullanılarak doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="c0bf1-125">The client is authenticated using the ClientCredentialType supplied.</span></span> <span data-ttu-id="c0bf1-126">Bkz [\<transport>](transport-of-basichttpbinding.md) ..</span><span class="sxs-lookup"><span data-stu-id="c0bf1-126">See the [\<transport>](transport-of-basichttpbinding.md).</span></span>|  
|<span data-ttu-id="c0bf1-127">İleti</span><span class="sxs-lookup"><span data-stu-id="c0bf1-127">Message</span></span>|<span data-ttu-id="c0bf1-128">Güvenlik, SOAP iletisi güvenliği kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="c0bf1-128">Security is provided using SOAP message security.</span></span> <span data-ttu-id="c0bf1-129">Varsayılan olarak, gövde şifrelenir ve imzalanır.</span><span class="sxs-lookup"><span data-stu-id="c0bf1-129">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="c0bf1-130">Bu bağlama için, sistem, sunucu sertifikasının bant dışı istemciye sağlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c0bf1-130">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="c0bf1-131">`ClientCredentialType`Bu bağlama için geçerli tek geçerlidir `Certificate` .</span><span class="sxs-lookup"><span data-stu-id="c0bf1-131">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|  
|<span data-ttu-id="c0bf1-132">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="c0bf1-132">TransportWithMessageCredential</span></span>|<span data-ttu-id="c0bf1-133">Bütünlük, gizlilik ve sunucu kimlik doğrulaması, aktarım güvenliği tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="c0bf1-133">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="c0bf1-134">İstemci kimlik doğrulaması, SOAP iletisi güvenliği aracılığıyla sağlanır.</span><span class="sxs-lookup"><span data-stu-id="c0bf1-134">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="c0bf1-135">Bu mod, Kullanıcı Kullanıcı adı/parola kullanarak kimlik doğrulaması yapıldığında ve ileti aktarımını güvenli hale getirmek için mevcut bir HTTP dağıtımı olduğunda geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="c0bf1-135">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|  
|<span data-ttu-id="c0bf1-136">Yalnızca transportcredential</span><span class="sxs-lookup"><span data-stu-id="c0bf1-136">TransportCredentialOnly</span></span>|<span data-ttu-id="c0bf1-137">Bu mod ileti bütünlüğü ve gizliliği sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="c0bf1-137">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="c0bf1-138">HTTP tabanlı istemci kimlik doğrulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="c0bf1-138">It provides http-based client authentication.</span></span> <span data-ttu-id="c0bf1-139">Bu mod dikkatli kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c0bf1-139">This mode should be used with caution.</span></span> <span data-ttu-id="c0bf1-140">Aktarım güvenliğinin diğer yollarla (IPSec gibi) sağlandığı ve yalnızca WCF altyapısı tarafından istemci kimlik doğrulamasının sağlandığı ortamlarda kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c0bf1-140">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c0bf1-141">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c0bf1-141">Child Elements</span></span>  
  
|<span data-ttu-id="c0bf1-142">Öğe</span><span class="sxs-lookup"><span data-stu-id="c0bf1-142">Element</span></span>|<span data-ttu-id="c0bf1-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c0bf1-143">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-basichttpbinding.md)|<span data-ttu-id="c0bf1-144">Temel bir HTTP hizmeti için taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c0bf1-144">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="c0bf1-145">Bu öğe öğesine karşılık gelir <xref:System.ServiceModel.HttpTransportSecurity> .</span><span class="sxs-lookup"><span data-stu-id="c0bf1-145">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|  
|[\<message>](message-of-basichttpbinding.md)|<span data-ttu-id="c0bf1-146">Temel bir HTTP hizmeti için ileti güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c0bf1-146">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="c0bf1-147">Bu öğe öğesine karşılık gelir <xref:System.ServiceModel.BasicHttpMessageSecurity> .</span><span class="sxs-lookup"><span data-stu-id="c0bf1-147">This element corresponds to <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c0bf1-148">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c0bf1-148">Parent Elements</span></span>  
  
|<span data-ttu-id="c0bf1-149">Öğe</span><span class="sxs-lookup"><span data-stu-id="c0bf1-149">Element</span></span>|<span data-ttu-id="c0bf1-150">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c0bf1-150">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c0bf1-151">bağlama</span><span class="sxs-lookup"><span data-stu-id="c0bf1-151">binding</span></span>|<span data-ttu-id="c0bf1-152">Öğesinin bağlama öğesi [\<basicHttpBinding>](basichttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="c0bf1-152">The binding element of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c0bf1-153">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c0bf1-153">Remarks</span></span>  

 <span data-ttu-id="c0bf1-154">Varsayılan olarak, SOAP iletisi güvenli değildir ve istemcinin kimliği doğrulanmaz.</span><span class="sxs-lookup"><span data-stu-id="c0bf1-154">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="c0bf1-155">Bu öğe, öğesi için ek güvenlik ayarları yapılandırmanıza olanak sağlar `basicHttpBinding` .</span><span class="sxs-lookup"><span data-stu-id="c0bf1-155">This element enables you to configure additional security settings for the `basicHttpBinding` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0bf1-156">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c0bf1-156">See also</span></span>

- <xref:System.ServiceModel.BasicHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="c0bf1-157">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="c0bf1-157">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="c0bf1-158">Kimlik Bilgisi Türü Seçme</span><span class="sxs-lookup"><span data-stu-id="c0bf1-158">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="c0bf1-159">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="c0bf1-159">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="c0bf1-160">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c0bf1-160">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="c0bf1-161">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="c0bf1-161">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)

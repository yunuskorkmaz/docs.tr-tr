---
title: <security> / <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 6432708d-5465-4bd9-bfc2-466742db99cb
ms.openlocfilehash: 00a933892376c2dc9771752beaf76d4994554968
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399890"
---
# <a name="security-of-basichttpbinding"></a><span data-ttu-id="2d158-102">\<\<BasicHttpBinding > Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="2d158-102">\<security> of \<basicHttpBinding></span></span>
<span data-ttu-id="2d158-103">[ \<BasicHttpBinding >](basichttpbinding.md)'nin güvenlik yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2d158-103">Defines the security capabilities of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>  
  
<span data-ttu-id="2d158-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2d158-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2d158-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="2d158-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="2d158-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlama >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="2d158-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="2d158-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<basicHttpBinding >** ](basichttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="2d158-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<basicHttpBinding>**](basichttpbinding.md)</span></span>\
<span data-ttu-id="2d158-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="2d158-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="2d158-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Güvenlik >**</span><span class="sxs-lookup"><span data-stu-id="2d158-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d158-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2d158-110">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="string" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2d158-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2d158-111">Attributes and Elements</span></span>  
 <span data-ttu-id="2d158-112">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="2d158-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2d158-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2d158-113">Attributes</span></span>  
  
|<span data-ttu-id="2d158-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2d158-114">Attribute</span></span>|<span data-ttu-id="2d158-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2d158-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2d158-116">mod</span><span class="sxs-lookup"><span data-stu-id="2d158-116">mode</span></span>|<span data-ttu-id="2d158-117">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="2d158-117">Optional.</span></span> <span data-ttu-id="2d158-118">Kullanılan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="2d158-118">Specifies the type of security that is used.</span></span> <span data-ttu-id="2d158-119">Varsayılan, `None` değeridir.</span><span class="sxs-lookup"><span data-stu-id="2d158-119">The default is `None`.</span></span> <span data-ttu-id="2d158-120">Bu öznitelik türü <xref:System.ServiceModel.BasicHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="2d158-120">This attribute is of type <xref:System.ServiceModel.BasicHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="2d158-121">mode özniteliği</span><span class="sxs-lookup"><span data-stu-id="2d158-121">mode Attribute</span></span>  
  
|<span data-ttu-id="2d158-122">Değer</span><span class="sxs-lookup"><span data-stu-id="2d158-122">Value</span></span>|<span data-ttu-id="2d158-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2d158-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2d158-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="2d158-124">None</span></span>|<span data-ttu-id="2d158-125">-İletiler aktarım sırasında güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="2d158-125">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="2d158-126">Aktarım</span><span class="sxs-lookup"><span data-stu-id="2d158-126">Transport</span></span>|<span data-ttu-id="2d158-127">Güvenlik, HTTPS taşıması kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="2d158-127">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="2d158-128">SOAP iletilerinin HTTPS kullanılarak güvenliği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="2d158-128">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="2d158-129">Hizmetin, hizmetin X. 509.440 sertifikası kullanılarak istemcinin kimliği doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="2d158-129">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="2d158-130">İstemcinin kimliği, sağlanan ClientCredentialType kullanılarak doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="2d158-130">The client is authenticated using the ClientCredentialType supplied.</span></span> <span data-ttu-id="2d158-131">Aktarım > bakın. [ \<](transport-of-basichttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="2d158-131">See the [\<transport>](transport-of-basichttpbinding.md).</span></span>|  
|<span data-ttu-id="2d158-132">`Message`</span><span class="sxs-lookup"><span data-stu-id="2d158-132">Message</span></span>|<span data-ttu-id="2d158-133">Güvenlik, SOAP iletisi güvenliği kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="2d158-133">Security is provided using SOAP message security.</span></span> <span data-ttu-id="2d158-134">Varsayılan olarak, gövde şifrelenir ve imzalanır.</span><span class="sxs-lookup"><span data-stu-id="2d158-134">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="2d158-135">Bu bağlama için, sistem, sunucu sertifikasının bant dışı istemciye sağlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2d158-135">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="2d158-136">`ClientCredentialType` Bu`Certificate`bağlama için geçerli tek geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="2d158-136">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|  
|<span data-ttu-id="2d158-137">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="2d158-137">TransportWithMessageCredential</span></span>|<span data-ttu-id="2d158-138">Bütünlük, gizlilik ve sunucu kimlik doğrulaması, aktarım güvenliği tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="2d158-138">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="2d158-139">İstemci kimlik doğrulaması, SOAP iletisi güvenliği aracılığıyla sağlanır.</span><span class="sxs-lookup"><span data-stu-id="2d158-139">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="2d158-140">Bu mod, Kullanıcı Kullanıcı adı/parola kullanarak kimlik doğrulaması yapıldığında ve ileti aktarımını güvenli hale getirmek için mevcut bir HTTP dağıtımı olduğunda geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="2d158-140">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|  
|<span data-ttu-id="2d158-141">Yalnızca transportcredential</span><span class="sxs-lookup"><span data-stu-id="2d158-141">TransportCredentialOnly</span></span>|<span data-ttu-id="2d158-142">Bu mod ileti bütünlüğü ve gizliliği sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="2d158-142">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="2d158-143">HTTP tabanlı istemci kimlik doğrulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="2d158-143">It provides http-based client authentication.</span></span> <span data-ttu-id="2d158-144">Bu mod dikkatli kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2d158-144">This mode should be used with caution.</span></span> <span data-ttu-id="2d158-145">Aktarım güvenliğinin diğer yollarla (IPSec gibi) sağlandığı ve yalnızca WCF altyapısı tarafından istemci kimlik doğrulamasının sağlandığı ortamlarda kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2d158-145">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2d158-146">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2d158-146">Child Elements</span></span>  
  
|<span data-ttu-id="2d158-147">Öğe</span><span class="sxs-lookup"><span data-stu-id="2d158-147">Element</span></span>|<span data-ttu-id="2d158-148">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2d158-148">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2d158-149">\<Taşıma ></span><span class="sxs-lookup"><span data-stu-id="2d158-149">\<transport></span></span>](transport-of-basichttpbinding.md)|<span data-ttu-id="2d158-150">Temel bir HTTP hizmeti için taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2d158-150">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="2d158-151">Bu öğe öğesine <xref:System.ServiceModel.HttpTransportSecurity>karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="2d158-151">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|  
|[<span data-ttu-id="2d158-152">\<ileti ></span><span class="sxs-lookup"><span data-stu-id="2d158-152">\<message></span></span>](message-of-basichttpbinding.md)|<span data-ttu-id="2d158-153">Temel bir HTTP hizmeti için ileti güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2d158-153">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="2d158-154">Bu öğe öğesine <xref:System.ServiceModel.BasicHttpMessageSecurity>karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="2d158-154">This element corresponds to <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2d158-155">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2d158-155">Parent Elements</span></span>  
  
|<span data-ttu-id="2d158-156">Öğe</span><span class="sxs-lookup"><span data-stu-id="2d158-156">Element</span></span>|<span data-ttu-id="2d158-157">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2d158-157">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2d158-158">bağlama</span><span class="sxs-lookup"><span data-stu-id="2d158-158">binding</span></span>|<span data-ttu-id="2d158-159">BasicHttpBinding > Binding öğesi. [ \<](basichttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="2d158-159">The binding element of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d158-160">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2d158-160">Remarks</span></span>  
 <span data-ttu-id="2d158-161">Varsayılan olarak, SOAP iletisi güvenli değildir ve istemcinin kimliği doğrulanmaz.</span><span class="sxs-lookup"><span data-stu-id="2d158-161">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="2d158-162">Bu öğe, `basicHttpBinding` öğesi için ek güvenlik ayarları yapılandırmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="2d158-162">This element enables you to configure additional security settings for the `basicHttpBinding` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d158-163">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2d158-163">See also</span></span>

- <xref:System.ServiceModel.BasicHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="2d158-164">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="2d158-164">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="2d158-165">Kimlik Bilgisi Türü Seçme</span><span class="sxs-lookup"><span data-stu-id="2d158-165">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="2d158-166">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="2d158-166">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="2d158-167">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="2d158-167">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="2d158-168">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="2d158-168">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="2d158-169">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="2d158-169">\<binding></span></span>](../../../misc/binding.md)

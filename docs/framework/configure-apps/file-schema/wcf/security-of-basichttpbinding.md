---
title: <security> / <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 6432708d-5465-4bd9-bfc2-466742db99cb
ms.openlocfilehash: f84f6c0f9988dd2d07377bf694286922db9d8364
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936798"
---
# <a name="security-of-basichttpbinding"></a><span data-ttu-id="24b90-102">\<\<BasicHttpBinding > Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="24b90-102">\<security> of \<basicHttpBinding></span></span>
<span data-ttu-id="24b90-103">[ \<BasicHttpBinding >](basichttpbinding.md)'nin güvenlik yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="24b90-103">Defines the security capabilities of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>  
  
 <span data-ttu-id="24b90-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="24b90-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="24b90-105">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="24b90-105">\<bindings></span></span>  
<span data-ttu-id="24b90-106">\<basicHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="24b90-106">\<basicHttpBinding></span></span>  
<span data-ttu-id="24b90-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="24b90-107">\<binding></span></span>  
<span data-ttu-id="24b90-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="24b90-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24b90-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="24b90-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="string" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="24b90-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="24b90-110">Attributes and Elements</span></span>  
 <span data-ttu-id="24b90-111">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="24b90-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="24b90-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="24b90-112">Attributes</span></span>  
  
|<span data-ttu-id="24b90-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="24b90-113">Attribute</span></span>|<span data-ttu-id="24b90-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="24b90-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="24b90-115">mod</span><span class="sxs-lookup"><span data-stu-id="24b90-115">mode</span></span>|<span data-ttu-id="24b90-116">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="24b90-116">Optional.</span></span> <span data-ttu-id="24b90-117">Kullanılan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="24b90-117">Specifies the type of security that is used.</span></span> <span data-ttu-id="24b90-118">Varsayılan, `None` değeridir.</span><span class="sxs-lookup"><span data-stu-id="24b90-118">The default is `None`.</span></span> <span data-ttu-id="24b90-119">Bu öznitelik türü <xref:System.ServiceModel.BasicHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="24b90-119">This attribute is of type <xref:System.ServiceModel.BasicHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="24b90-120">mode özniteliği</span><span class="sxs-lookup"><span data-stu-id="24b90-120">mode Attribute</span></span>  
  
|<span data-ttu-id="24b90-121">Değer</span><span class="sxs-lookup"><span data-stu-id="24b90-121">Value</span></span>|<span data-ttu-id="24b90-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="24b90-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="24b90-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="24b90-123">None</span></span>|<span data-ttu-id="24b90-124">-İletiler aktarım sırasında güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="24b90-124">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="24b90-125">Aktarım</span><span class="sxs-lookup"><span data-stu-id="24b90-125">Transport</span></span>|<span data-ttu-id="24b90-126">Güvenlik, HTTPS taşıması kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="24b90-126">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="24b90-127">SOAP iletilerinin HTTPS kullanılarak güvenliği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="24b90-127">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="24b90-128">Hizmetin, hizmetin X. 509.440 sertifikası kullanılarak istemcinin kimliği doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="24b90-128">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="24b90-129">İstemcinin kimliği, sağlanan ClientCredentialType kullanılarak doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="24b90-129">The client is authenticated using the ClientCredentialType supplied.</span></span> <span data-ttu-id="24b90-130">Aktarım > bakın. [ \<](transport-of-basichttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="24b90-130">See the [\<transport>](transport-of-basichttpbinding.md).</span></span>|  
|<span data-ttu-id="24b90-131">`Message`</span><span class="sxs-lookup"><span data-stu-id="24b90-131">Message</span></span>|<span data-ttu-id="24b90-132">Güvenlik, SOAP iletisi güvenliği kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="24b90-132">Security is provided using SOAP message security.</span></span> <span data-ttu-id="24b90-133">Varsayılan olarak, gövde şifrelenir ve imzalanır.</span><span class="sxs-lookup"><span data-stu-id="24b90-133">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="24b90-134">Bu bağlama için, sistem, sunucu sertifikasının bant dışı istemciye sağlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="24b90-134">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="24b90-135">`ClientCredentialType` Bu`Certificate`bağlama için geçerli tek geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="24b90-135">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|  
|<span data-ttu-id="24b90-136">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="24b90-136">TransportWithMessageCredential</span></span>|<span data-ttu-id="24b90-137">Bütünlük, gizlilik ve sunucu kimlik doğrulaması, aktarım güvenliği tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="24b90-137">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="24b90-138">İstemci kimlik doğrulaması, SOAP iletisi güvenliği aracılığıyla sağlanır.</span><span class="sxs-lookup"><span data-stu-id="24b90-138">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="24b90-139">Bu mod, Kullanıcı Kullanıcı adı/parola kullanarak kimlik doğrulaması yapıldığında ve ileti aktarımını güvenli hale getirmek için mevcut bir HTTP dağıtımı olduğunda geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="24b90-139">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|  
|<span data-ttu-id="24b90-140">Yalnızca transportcredential</span><span class="sxs-lookup"><span data-stu-id="24b90-140">TransportCredentialOnly</span></span>|<span data-ttu-id="24b90-141">Bu mod ileti bütünlüğü ve gizliliği sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="24b90-141">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="24b90-142">HTTP tabanlı istemci kimlik doğrulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="24b90-142">It provides http-based client authentication.</span></span> <span data-ttu-id="24b90-143">Bu mod dikkatli kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="24b90-143">This mode should be used with caution.</span></span> <span data-ttu-id="24b90-144">Aktarım güvenliğinin diğer yollarla (IPSec gibi) sağlandığı ve yalnızca WCF altyapısı tarafından istemci kimlik doğrulamasının sağlandığı ortamlarda kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="24b90-144">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="24b90-145">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="24b90-145">Child Elements</span></span>  
  
|<span data-ttu-id="24b90-146">Öğe</span><span class="sxs-lookup"><span data-stu-id="24b90-146">Element</span></span>|<span data-ttu-id="24b90-147">Açıklama</span><span class="sxs-lookup"><span data-stu-id="24b90-147">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="24b90-148">\<Taşıma ></span><span class="sxs-lookup"><span data-stu-id="24b90-148">\<transport></span></span>](transport-of-basichttpbinding.md)|<span data-ttu-id="24b90-149">Temel bir HTTP hizmeti için taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="24b90-149">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="24b90-150">Bu öğe öğesine <xref:System.ServiceModel.HttpTransportSecurity>karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="24b90-150">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|  
|[<span data-ttu-id="24b90-151">\<ileti ></span><span class="sxs-lookup"><span data-stu-id="24b90-151">\<message></span></span>](message-of-basichttpbinding.md)|<span data-ttu-id="24b90-152">Temel bir HTTP hizmeti için ileti güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="24b90-152">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="24b90-153">Bu öğe öğesine <xref:System.ServiceModel.BasicHttpMessageSecurity>karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="24b90-153">This element corresponds to <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="24b90-154">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="24b90-154">Parent Elements</span></span>  
  
|<span data-ttu-id="24b90-155">Öğe</span><span class="sxs-lookup"><span data-stu-id="24b90-155">Element</span></span>|<span data-ttu-id="24b90-156">Açıklama</span><span class="sxs-lookup"><span data-stu-id="24b90-156">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="24b90-157">bağlama</span><span class="sxs-lookup"><span data-stu-id="24b90-157">binding</span></span>|<span data-ttu-id="24b90-158">BasicHttpBinding > Binding öğesi. [ \<](basichttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="24b90-158">The binding element of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="24b90-159">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="24b90-159">Remarks</span></span>  
 <span data-ttu-id="24b90-160">Varsayılan olarak, SOAP iletisi güvenli değildir ve istemcinin kimliği doğrulanmaz.</span><span class="sxs-lookup"><span data-stu-id="24b90-160">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="24b90-161">Bu öğe, `basicHttpBinding` öğesi için ek güvenlik ayarları yapılandırmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="24b90-161">This element enables you to configure additional security settings for the `basicHttpBinding` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24b90-162">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="24b90-162">See also</span></span>

- <xref:System.ServiceModel.BasicHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="24b90-163">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="24b90-163">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="24b90-164">Kimlik Bilgisi Türü Seçme</span><span class="sxs-lookup"><span data-stu-id="24b90-164">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="24b90-165">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="24b90-165">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="24b90-166">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="24b90-166">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="24b90-167">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="24b90-167">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="24b90-168">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="24b90-168">\<binding></span></span>](../../../misc/binding.md)

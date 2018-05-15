---
title: '&lt;basicHttpBinding&gt; &lt;güvenliği&gt;'
ms.date: 03/30/2017
ms.assetid: 6432708d-5465-4bd9-bfc2-466742db99cb
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: ddf120d5462c7fcb0774e29fa18e80b71727acd8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltsecuritygt-of-ltbasichttpbindinggt"></a><span data-ttu-id="5f379-102">&lt;basicHttpBinding&gt; &lt;güvenliği&gt;</span><span class="sxs-lookup"><span data-stu-id="5f379-102">&lt;security&gt; of &lt;basicHttpBinding&gt;</span></span>
<span data-ttu-id="5f379-103">Güvenlik özelliklerini tanımlayan [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="5f379-103">Defines the security capabilities of the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>  
  
 <span data-ttu-id="5f379-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5f379-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5f379-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="5f379-105">\<bindings></span></span>  
<span data-ttu-id="5f379-106">\<basicHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="5f379-106">\<basicHttpBinding></span></span>  
<span data-ttu-id="5f379-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="5f379-107">\<binding></span></span>  
<span data-ttu-id="5f379-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="5f379-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f379-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5f379-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">  
   <transport  
      clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
      proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
      realm="string" />  
   <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
            clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />  
</security>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5f379-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5f379-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5f379-111">Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır</span><span class="sxs-lookup"><span data-stu-id="5f379-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5f379-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5f379-112">Attributes</span></span>  
  
|<span data-ttu-id="5f379-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5f379-113">Attribute</span></span>|<span data-ttu-id="5f379-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5f379-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5f379-115">mod</span><span class="sxs-lookup"><span data-stu-id="5f379-115">mode</span></span>|<span data-ttu-id="5f379-116">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="5f379-116">Optional.</span></span> <span data-ttu-id="5f379-117">Kullanılan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="5f379-117">Specifies the type of security that is used.</span></span> <span data-ttu-id="5f379-118">Varsayılan, `None` değeridir.</span><span class="sxs-lookup"><span data-stu-id="5f379-118">The default is `None`.</span></span> <span data-ttu-id="5f379-119">Bu öznitelik türünde <xref:System.ServiceModel.BasicHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="5f379-119">This attribute is of type <xref:System.ServiceModel.BasicHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="5f379-120">mod özniteliği</span><span class="sxs-lookup"><span data-stu-id="5f379-120">mode Attribute</span></span>  
  
|<span data-ttu-id="5f379-121">Değer</span><span class="sxs-lookup"><span data-stu-id="5f379-121">Value</span></span>|<span data-ttu-id="5f379-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5f379-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5f379-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="5f379-123">None</span></span>|<span data-ttu-id="5f379-124">-Aktarım sırasında iletileri güvenli değil.</span><span class="sxs-lookup"><span data-stu-id="5f379-124">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="5f379-125">Taşıma</span><span class="sxs-lookup"><span data-stu-id="5f379-125">Transport</span></span>|<span data-ttu-id="5f379-126">Güvenlik, HTTPS aktarımı kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="5f379-126">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="5f379-127">SOAP iletilerine HTTPS kullanan güvenli hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="5f379-127">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="5f379-128">Hizmet, hizmetin X.509 sertifikası kullanarak istemci kimlik doğrulaması yapılır.</span><span class="sxs-lookup"><span data-stu-id="5f379-128">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="5f379-129">İstemci tarafından sağlanan ClientCredentialType kullanılarak doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="5f379-129">The client is authenticated using the ClientCredentialType supplied.</span></span> <span data-ttu-id="5f379-130">Bkz: [ \<aktarım >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="5f379-130">See the [\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md).</span></span>|  
|<span data-ttu-id="5f379-131">İleti</span><span class="sxs-lookup"><span data-stu-id="5f379-131">Message</span></span>|<span data-ttu-id="5f379-132">Güvenlik SOAP ileti güvenliği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="5f379-132">Security is provided using SOAP message security.</span></span> <span data-ttu-id="5f379-133">Varsayılan olarak, gövde imzalı ve şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="5f379-133">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="5f379-134">Bu bağlama için sunucu sertifikası, bant dışı istemciye sağlanması sistemi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="5f379-134">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="5f379-135">Yalnızca geçerli `ClientCredentialType` Bu bağlama için `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="5f379-135">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|  
|<span data-ttu-id="5f379-136">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="5f379-136">TransportWithMessageCredential</span></span>|<span data-ttu-id="5f379-137">Bütünlük, gizlilik ve sunucu kimlik doğrulama ile taşıma güvenliği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="5f379-137">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="5f379-138">İstemci kimlik doğrulaması SOAP iletisi güvenlik yoluyla sağlanır.</span><span class="sxs-lookup"><span data-stu-id="5f379-138">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="5f379-139">Bu mod, kullanıcının kullanıcı adı/parola kullanarak kimlik doğrulaması ve ileti aktarma güvenliğini sağlamak için var olan bir HTTP dağıtım olduğunda geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="5f379-139">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|  
|<span data-ttu-id="5f379-140">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="5f379-140">TransportCredentialOnly</span></span>|<span data-ttu-id="5f379-141">Bu mod, ileti bütünlüğü ve gizliliği sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="5f379-141">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="5f379-142">Http tabanlı istemci kimlik doğrulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="5f379-142">It provides http-based client authentication.</span></span> <span data-ttu-id="5f379-143">Bu mod dikkatli kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5f379-143">This mode should be used with caution.</span></span> <span data-ttu-id="5f379-144">Burada taşıma güvenliği (IPSec gibi) diğer yollarla sağlanmaktadır ve yalnızca istemci kimlik doğrulaması tarafından sağlanan ortamlarda kullanılmalıdır [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] altyapı.</span><span class="sxs-lookup"><span data-stu-id="5f379-144">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5f379-145">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5f379-145">Child Elements</span></span>  
  
|<span data-ttu-id="5f379-146">Öğe</span><span class="sxs-lookup"><span data-stu-id="5f379-146">Element</span></span>|<span data-ttu-id="5f379-147">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5f379-147">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5f379-148">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="5f379-148">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md)|<span data-ttu-id="5f379-149">Temel HTTP hizmeti Aktarım güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5f379-149">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="5f379-150">Bu öğe karşılık gelen <xref:System.ServiceModel.HttpTransportSecurity>.</span><span class="sxs-lookup"><span data-stu-id="5f379-150">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|  
|[<span data-ttu-id="5f379-151">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="5f379-151">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-basichttpbinding.md)|<span data-ttu-id="5f379-152">Temel HTTP hizmeti ileti güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5f379-152">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="5f379-153">Bu öğe karşılık gelen <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span><span class="sxs-lookup"><span data-stu-id="5f379-153">This element corresponds to <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5f379-154">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5f379-154">Parent Elements</span></span>  
  
|<span data-ttu-id="5f379-155">Öğe</span><span class="sxs-lookup"><span data-stu-id="5f379-155">Element</span></span>|<span data-ttu-id="5f379-156">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5f379-156">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5f379-157">bağlama</span><span class="sxs-lookup"><span data-stu-id="5f379-157">binding</span></span>|<span data-ttu-id="5f379-158">Bağlama öğesi [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="5f379-158">The binding element of the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f379-159">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5f379-159">Remarks</span></span>  
 <span data-ttu-id="5f379-160">Varsayılan olarak, SOAP ileti güvenli olmadığından ve istemci kimliği doğrulanmamış.</span><span class="sxs-lookup"><span data-stu-id="5f379-160">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="5f379-161">Bu öğe için ek güvenlik ayarlarını yapılandırmanızı sağlar `basicHttpBinding` öğesi.</span><span class="sxs-lookup"><span data-stu-id="5f379-161">This element enables you to configure additional security settings for the `basicHttpBinding` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f379-162">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5f379-162">See Also</span></span>  
 <xref:System.ServiceModel.BasicHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>  
 <xref:System.ServiceModel.BasicHttpSecurity>  
 [<span data-ttu-id="5f379-163">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="5f379-163">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="5f379-164">Kimlik Bilgisi Türü Seçme</span><span class="sxs-lookup"><span data-stu-id="5f379-164">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="5f379-165">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="5f379-165">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="5f379-166">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="5f379-166">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="5f379-167">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="5f379-167">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="5f379-168">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="5f379-168">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)

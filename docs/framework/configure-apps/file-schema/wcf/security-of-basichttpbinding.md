---
title: '&lt;basicHttpBinding&gt; &lt;güvenliği&gt;'
ms.date: 03/30/2017
ms.assetid: 6432708d-5465-4bd9-bfc2-466742db99cb
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: e39d32a9cc689905bed42f56e4f998bbd8c6e038
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33355034"
---
# <a name="ltsecuritygt-of-ltbasichttpbindinggt"></a><span data-ttu-id="78e02-102">&lt;basicHttpBinding&gt; &lt;güvenliği&gt;</span><span class="sxs-lookup"><span data-stu-id="78e02-102">&lt;security&gt; of &lt;basicHttpBinding&gt;</span></span>
<span data-ttu-id="78e02-103">Güvenlik özelliklerini tanımlayan [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="78e02-103">Defines the security capabilities of the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>  
  
 <span data-ttu-id="78e02-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="78e02-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="78e02-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="78e02-105">\<bindings></span></span>  
<span data-ttu-id="78e02-106">\<basicHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="78e02-106">\<basicHttpBinding></span></span>  
<span data-ttu-id="78e02-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="78e02-107">\<binding></span></span>  
<span data-ttu-id="78e02-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="78e02-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78e02-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="78e02-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="78e02-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="78e02-110">Attributes and Elements</span></span>  
 <span data-ttu-id="78e02-111">Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır</span><span class="sxs-lookup"><span data-stu-id="78e02-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="78e02-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="78e02-112">Attributes</span></span>  
  
|<span data-ttu-id="78e02-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="78e02-113">Attribute</span></span>|<span data-ttu-id="78e02-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="78e02-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="78e02-115">mod</span><span class="sxs-lookup"><span data-stu-id="78e02-115">mode</span></span>|<span data-ttu-id="78e02-116">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="78e02-116">Optional.</span></span> <span data-ttu-id="78e02-117">Kullanılan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="78e02-117">Specifies the type of security that is used.</span></span> <span data-ttu-id="78e02-118">Varsayılan, `None` değeridir.</span><span class="sxs-lookup"><span data-stu-id="78e02-118">The default is `None`.</span></span> <span data-ttu-id="78e02-119">Bu öznitelik türünde <xref:System.ServiceModel.BasicHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="78e02-119">This attribute is of type <xref:System.ServiceModel.BasicHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="78e02-120">mod özniteliği</span><span class="sxs-lookup"><span data-stu-id="78e02-120">mode Attribute</span></span>  
  
|<span data-ttu-id="78e02-121">Değer</span><span class="sxs-lookup"><span data-stu-id="78e02-121">Value</span></span>|<span data-ttu-id="78e02-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="78e02-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="78e02-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="78e02-123">None</span></span>|<span data-ttu-id="78e02-124">-Aktarım sırasında iletileri güvenli değil.</span><span class="sxs-lookup"><span data-stu-id="78e02-124">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="78e02-125">Taşıma</span><span class="sxs-lookup"><span data-stu-id="78e02-125">Transport</span></span>|<span data-ttu-id="78e02-126">Güvenlik, HTTPS aktarımı kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="78e02-126">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="78e02-127">SOAP iletilerine HTTPS kullanan güvenli hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="78e02-127">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="78e02-128">Hizmet, hizmetin X.509 sertifikası kullanarak istemci kimlik doğrulaması yapılır.</span><span class="sxs-lookup"><span data-stu-id="78e02-128">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="78e02-129">İstemci tarafından sağlanan ClientCredentialType kullanılarak doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="78e02-129">The client is authenticated using the ClientCredentialType supplied.</span></span> <span data-ttu-id="78e02-130">Bkz: [ \<aktarım >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="78e02-130">See the [\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md).</span></span>|  
|<span data-ttu-id="78e02-131">İleti</span><span class="sxs-lookup"><span data-stu-id="78e02-131">Message</span></span>|<span data-ttu-id="78e02-132">Güvenlik SOAP ileti güvenliği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="78e02-132">Security is provided using SOAP message security.</span></span> <span data-ttu-id="78e02-133">Varsayılan olarak, gövde imzalı ve şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="78e02-133">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="78e02-134">Bu bağlama için sunucu sertifikası, bant dışı istemciye sağlanması sistemi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="78e02-134">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="78e02-135">Yalnızca geçerli `ClientCredentialType` Bu bağlama için `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="78e02-135">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|  
|<span data-ttu-id="78e02-136">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="78e02-136">TransportWithMessageCredential</span></span>|<span data-ttu-id="78e02-137">Bütünlük, gizlilik ve sunucu kimlik doğrulama ile taşıma güvenliği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="78e02-137">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="78e02-138">İstemci kimlik doğrulaması SOAP iletisi güvenlik yoluyla sağlanır.</span><span class="sxs-lookup"><span data-stu-id="78e02-138">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="78e02-139">Bu mod, kullanıcının kullanıcı adı/parola kullanarak kimlik doğrulaması ve ileti aktarma güvenliğini sağlamak için var olan bir HTTP dağıtım olduğunda geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="78e02-139">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|  
|<span data-ttu-id="78e02-140">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="78e02-140">TransportCredentialOnly</span></span>|<span data-ttu-id="78e02-141">Bu mod, ileti bütünlüğü ve gizliliği sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="78e02-141">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="78e02-142">Http tabanlı istemci kimlik doğrulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="78e02-142">It provides http-based client authentication.</span></span> <span data-ttu-id="78e02-143">Bu mod dikkatli kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="78e02-143">This mode should be used with caution.</span></span> <span data-ttu-id="78e02-144">Burada taşıma güvenliği (IPSec gibi) diğer yollarla sağlanmaktadır ve yalnızca istemci kimlik doğrulaması WCF altyapısı tarafından sağlanan ortamlarda kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="78e02-144">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="78e02-145">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="78e02-145">Child Elements</span></span>  
  
|<span data-ttu-id="78e02-146">Öğe</span><span class="sxs-lookup"><span data-stu-id="78e02-146">Element</span></span>|<span data-ttu-id="78e02-147">Açıklama</span><span class="sxs-lookup"><span data-stu-id="78e02-147">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="78e02-148">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="78e02-148">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md)|<span data-ttu-id="78e02-149">Temel HTTP hizmeti Aktarım güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="78e02-149">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="78e02-150">Bu öğe karşılık gelen <xref:System.ServiceModel.HttpTransportSecurity>.</span><span class="sxs-lookup"><span data-stu-id="78e02-150">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|  
|[<span data-ttu-id="78e02-151">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="78e02-151">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-basichttpbinding.md)|<span data-ttu-id="78e02-152">Temel HTTP hizmeti ileti güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="78e02-152">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="78e02-153">Bu öğe karşılık gelen <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span><span class="sxs-lookup"><span data-stu-id="78e02-153">This element corresponds to <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="78e02-154">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="78e02-154">Parent Elements</span></span>  
  
|<span data-ttu-id="78e02-155">Öğe</span><span class="sxs-lookup"><span data-stu-id="78e02-155">Element</span></span>|<span data-ttu-id="78e02-156">Açıklama</span><span class="sxs-lookup"><span data-stu-id="78e02-156">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="78e02-157">bağlama</span><span class="sxs-lookup"><span data-stu-id="78e02-157">binding</span></span>|<span data-ttu-id="78e02-158">Bağlama öğesi [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="78e02-158">The binding element of the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="78e02-159">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="78e02-159">Remarks</span></span>  
 <span data-ttu-id="78e02-160">Varsayılan olarak, SOAP ileti güvenli olmadığından ve istemci kimliği doğrulanmamış.</span><span class="sxs-lookup"><span data-stu-id="78e02-160">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="78e02-161">Bu öğe için ek güvenlik ayarlarını yapılandırmanızı sağlar `basicHttpBinding` öğesi.</span><span class="sxs-lookup"><span data-stu-id="78e02-161">This element enables you to configure additional security settings for the `basicHttpBinding` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78e02-162">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="78e02-162">See Also</span></span>  
 <xref:System.ServiceModel.BasicHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>  
 <xref:System.ServiceModel.BasicHttpSecurity>  
 [<span data-ttu-id="78e02-163">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="78e02-163">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="78e02-164">Kimlik Bilgisi Türü Seçme</span><span class="sxs-lookup"><span data-stu-id="78e02-164">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="78e02-165">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="78e02-165">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="78e02-166">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="78e02-166">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="78e02-167">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="78e02-167">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="78e02-168">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="78e02-168">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)

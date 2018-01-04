---
title: "&lt;netHttpBinding &gt;güvenliği&lt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dc41f6f7-cabc-4a64-9fa0-ceabf861b348
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1caae9411ca0ba8896613a38b446a3f0d190bb18
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsecuritygt-of-ltnethttpbinding"></a><span data-ttu-id="94eea-102">&lt;netHttpBinding &gt;güvenliği&lt;</span><span class="sxs-lookup"><span data-stu-id="94eea-102">&lt;security&gt; of &lt;netHttpBinding</span></span>
<span data-ttu-id="94eea-103">Güvenlik özelliklerini tanımlayan [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="94eea-103">Defines the security capabilities of the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>  
  
 <span data-ttu-id="94eea-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="94eea-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="94eea-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="94eea-105">\<bindings></span></span>  
<span data-ttu-id="94eea-106">\<netHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="94eea-106">\<netHttpBinding></span></span>  
<span data-ttu-id="94eea-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="94eea-107">\<binding></span></span>  
<span data-ttu-id="94eea-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="94eea-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94eea-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="94eea-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="94eea-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="94eea-110">Attributes and Elements</span></span>  
 <span data-ttu-id="94eea-111">Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır</span><span class="sxs-lookup"><span data-stu-id="94eea-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="94eea-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="94eea-112">Attributes</span></span>  
  
|<span data-ttu-id="94eea-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="94eea-113">Attribute</span></span>|<span data-ttu-id="94eea-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="94eea-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="94eea-115">mod</span><span class="sxs-lookup"><span data-stu-id="94eea-115">mode</span></span>|<span data-ttu-id="94eea-116">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="94eea-116">Optional.</span></span> <span data-ttu-id="94eea-117">Kullanılan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="94eea-117">Specifies the type of security that is used.</span></span> <span data-ttu-id="94eea-118">Varsayılan, `None` değeridir.</span><span class="sxs-lookup"><span data-stu-id="94eea-118">The default is `None`.</span></span> <span data-ttu-id="94eea-119">Bu öznitelik türünde <!--zz <xref:System.ServiceModel.NetHttpSecurityMode> --> `System.ServiceModel.NetHttpSecurityMode`.</span><span class="sxs-lookup"><span data-stu-id="94eea-119">This attribute is of type <!--zz <xref:System.ServiceModel.NetHttpSecurityMode> -->`System.ServiceModel.NetHttpSecurityMode`.</span></span>|
  
## <a name="mode-attribute"></a><span data-ttu-id="94eea-120">mod özniteliği</span><span class="sxs-lookup"><span data-stu-id="94eea-120">mode Attribute</span></span>  
  
|<span data-ttu-id="94eea-121">Değer</span><span class="sxs-lookup"><span data-stu-id="94eea-121">Value</span></span>|<span data-ttu-id="94eea-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="94eea-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="94eea-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="94eea-123">None</span></span>|<span data-ttu-id="94eea-124">-Aktarım sırasında iletileri güvenli değil.</span><span class="sxs-lookup"><span data-stu-id="94eea-124">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="94eea-125">Taşıma</span><span class="sxs-lookup"><span data-stu-id="94eea-125">Transport</span></span>|<span data-ttu-id="94eea-126">Güvenlik, HTTPS aktarımı kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="94eea-126">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="94eea-127">SOAP iletilerine HTTPS kullanan güvenli hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="94eea-127">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="94eea-128">Hizmet, hizmetin X.509 sertifikası kullanarak istemci kimlik doğrulaması yapılır.</span><span class="sxs-lookup"><span data-stu-id="94eea-128">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="94eea-129">İstemci tarafından sağlanan ClientCredentialType kullanılarak doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="94eea-129">The client is authenticated using the ClientCredentialType supplied.</span></span>|  
|<span data-ttu-id="94eea-130">İleti</span><span class="sxs-lookup"><span data-stu-id="94eea-130">Message</span></span>|<span data-ttu-id="94eea-131">Güvenlik SOAP ileti güvenliği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="94eea-131">Security is provided using SOAP message security.</span></span> <span data-ttu-id="94eea-132">Varsayılan olarak, gövde imzalı ve şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="94eea-132">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="94eea-133">Bu bağlama için sunucu sertifikası, bant dışı istemciye sağlanması sistemi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="94eea-133">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="94eea-134">Yalnızca geçerli `ClientCredentialType` Bu bağlama için `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="94eea-134">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|  
|<span data-ttu-id="94eea-135">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="94eea-135">TransportWithMessageCredential</span></span>|<span data-ttu-id="94eea-136">Bütünlük, gizlilik ve sunucu kimlik doğrulama ile taşıma güvenliği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="94eea-136">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="94eea-137">İstemci kimlik doğrulaması SOAP iletisi güvenlik yoluyla sağlanır.</span><span class="sxs-lookup"><span data-stu-id="94eea-137">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="94eea-138">Bu mod, kullanıcının kullanıcı adı/parola kullanarak kimlik doğrulaması ve ileti aktarma güvenliğini sağlamak için var olan bir HTTP dağıtım olduğunda geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="94eea-138">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|  
|<span data-ttu-id="94eea-139">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="94eea-139">TransportCredentialOnly</span></span>|<span data-ttu-id="94eea-140">Bu mod, ileti bütünlüğü ve gizliliği sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="94eea-140">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="94eea-141">Http tabanlı istemci kimlik doğrulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="94eea-141">It provides http-based client authentication.</span></span> <span data-ttu-id="94eea-142">Bu mod dikkatli kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="94eea-142">This mode should be used with caution.</span></span> <span data-ttu-id="94eea-143">Burada taşıma güvenliği (IPSec gibi) diğer yollarla sağlanmaktadır ve yalnızca istemci kimlik doğrulaması tarafından sağlanan ortamlarda kullanılmalıdır [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] altyapı.</span><span class="sxs-lookup"><span data-stu-id="94eea-143">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="94eea-144">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="94eea-144">Child Elements</span></span>  
  
|<span data-ttu-id="94eea-145">Öğe</span><span class="sxs-lookup"><span data-stu-id="94eea-145">Element</span></span>|<span data-ttu-id="94eea-146">Açıklama</span><span class="sxs-lookup"><span data-stu-id="94eea-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="94eea-147">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="94eea-147">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-nethttpbinding.md)|<span data-ttu-id="94eea-148">Temel HTTP hizmeti Aktarım güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="94eea-148">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="94eea-149">Bu öğe karşılık gelen <xref:System.ServiceModel.HttpTransportSecurity>.</span><span class="sxs-lookup"><span data-stu-id="94eea-149">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|  
|[<span data-ttu-id="94eea-150">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="94eea-150">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-nethttpbinding.md)|<span data-ttu-id="94eea-151">Temel HTTP hizmeti ileti güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="94eea-151">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="94eea-152">Bu öğe karşılık gelen <!--zz <xref:System.ServiceModel.NetHttpMessageSecurity> --> `System.ServiceModel.NetHttpMessageSecurity`.</span><span class="sxs-lookup"><span data-stu-id="94eea-152">This element corresponds to <!--zz <xref:System.ServiceModel.NetHttpMessageSecurity> --> `System.ServiceModel.NetHttpMessageSecurity`.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="94eea-153">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="94eea-153">Parent Elements</span></span>  
  
|<span data-ttu-id="94eea-154">Öğe</span><span class="sxs-lookup"><span data-stu-id="94eea-154">Element</span></span>|<span data-ttu-id="94eea-155">Açıklama</span><span class="sxs-lookup"><span data-stu-id="94eea-155">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="94eea-156">bağlama</span><span class="sxs-lookup"><span data-stu-id="94eea-156">binding</span></span>|<span data-ttu-id="94eea-157">Bağlama öğesi [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="94eea-157">The binding element of the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="94eea-158">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="94eea-158">Remarks</span></span>  
 <span data-ttu-id="94eea-159">Varsayılan olarak, SOAP ileti güvenli olmadığından ve istemci kimliği doğrulanmamış.</span><span class="sxs-lookup"><span data-stu-id="94eea-159">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="94eea-160">Bu öğe için ek güvenlik ayarlarını yapılandırmanızı sağlar `netHttpBinding` öğesi.</span><span class="sxs-lookup"><span data-stu-id="94eea-160">This element enables you to configure additional security settings for the `netHttpBinding` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94eea-161">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="94eea-161">See Also</span></span>  
 <xref:System.ServiceModel.NetHttpBinding.Security%2A>  
 <span data-ttu-id="94eea-162"><xref:System.ServiceModel.Configuration.NetHttpBindingElement.Security%2A></span><span class="sxs-lookup"><span data-stu-id="94eea-162"><xref:System.ServiceModel.Configuration.NetHttpBindingElement.Security%2A></span></span>    
 [<span data-ttu-id="94eea-163">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="94eea-163">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="94eea-164">Kimlik Bilgisi Türü Seçme</span><span class="sxs-lookup"><span data-stu-id="94eea-164">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="94eea-165">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="94eea-165">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="94eea-166">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="94eea-166">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="94eea-167">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="94eea-167">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="94eea-168">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="94eea-168">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)

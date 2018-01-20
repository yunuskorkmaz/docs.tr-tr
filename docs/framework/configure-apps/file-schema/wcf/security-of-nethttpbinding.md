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
ms.openlocfilehash: cbe36a801565af0d3664e5c827f8ce903be3b5c7
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="ltsecuritygt-of-ltnethttpbinding"></a><span data-ttu-id="0883a-102">&lt;netHttpBinding &gt;güvenliği&lt;</span><span class="sxs-lookup"><span data-stu-id="0883a-102">&lt;security&gt; of &lt;netHttpBinding</span></span>
<span data-ttu-id="0883a-103">Güvenlik özelliklerini tanımlayan [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="0883a-103">Defines the security capabilities of the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>  
  
 <span data-ttu-id="0883a-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="0883a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="0883a-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="0883a-105">\<bindings></span></span>  
<span data-ttu-id="0883a-106">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="0883a-106">\<netHttpBinding></span></span>  
<span data-ttu-id="0883a-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="0883a-107">\<binding></span></span>  
<span data-ttu-id="0883a-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="0883a-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0883a-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0883a-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0883a-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0883a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0883a-111">Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır</span><span class="sxs-lookup"><span data-stu-id="0883a-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0883a-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0883a-112">Attributes</span></span>  
  
|<span data-ttu-id="0883a-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0883a-113">Attribute</span></span>|<span data-ttu-id="0883a-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0883a-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0883a-115">mod</span><span class="sxs-lookup"><span data-stu-id="0883a-115">mode</span></span>|<span data-ttu-id="0883a-116">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="0883a-116">Optional.</span></span> <span data-ttu-id="0883a-117">Kullanılan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="0883a-117">Specifies the type of security that is used.</span></span> <span data-ttu-id="0883a-118">Varsayılan, `None` değeridir.</span><span class="sxs-lookup"><span data-stu-id="0883a-118">The default is `None`.</span></span> <span data-ttu-id="0883a-119">Bu öznitelik türünde <!--zz <xref:System.ServiceModel.NetHttpSecurityMode> --> `System.ServiceModel.NetHttpSecurityMode`.</span><span class="sxs-lookup"><span data-stu-id="0883a-119">This attribute is of type <!--zz <xref:System.ServiceModel.NetHttpSecurityMode> -->`System.ServiceModel.NetHttpSecurityMode`.</span></span>|
  
## <a name="mode-attribute"></a><span data-ttu-id="0883a-120">mod özniteliği</span><span class="sxs-lookup"><span data-stu-id="0883a-120">mode Attribute</span></span>  
  
|<span data-ttu-id="0883a-121">Değer</span><span class="sxs-lookup"><span data-stu-id="0883a-121">Value</span></span>|<span data-ttu-id="0883a-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0883a-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0883a-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="0883a-123">None</span></span>|<span data-ttu-id="0883a-124">-Aktarım sırasında iletileri güvenli değil.</span><span class="sxs-lookup"><span data-stu-id="0883a-124">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="0883a-125">Taşıma</span><span class="sxs-lookup"><span data-stu-id="0883a-125">Transport</span></span>|<span data-ttu-id="0883a-126">Güvenlik, HTTPS aktarımı kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="0883a-126">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="0883a-127">SOAP iletilerine HTTPS kullanan güvenli hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="0883a-127">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="0883a-128">Hizmet, hizmetin X.509 sertifikası kullanarak istemci kimlik doğrulaması yapılır.</span><span class="sxs-lookup"><span data-stu-id="0883a-128">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="0883a-129">İstemci tarafından sağlanan ClientCredentialType kullanılarak doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="0883a-129">The client is authenticated using the ClientCredentialType supplied.</span></span>|  
|<span data-ttu-id="0883a-130">İleti</span><span class="sxs-lookup"><span data-stu-id="0883a-130">Message</span></span>|<span data-ttu-id="0883a-131">Güvenlik SOAP ileti güvenliği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="0883a-131">Security is provided using SOAP message security.</span></span> <span data-ttu-id="0883a-132">Varsayılan olarak, gövde imzalı ve şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="0883a-132">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="0883a-133">Bu bağlama için sunucu sertifikası, bant dışı istemciye sağlanması sistemi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="0883a-133">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="0883a-134">Yalnızca geçerli `ClientCredentialType` Bu bağlama için `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="0883a-134">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|  
|<span data-ttu-id="0883a-135">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="0883a-135">TransportWithMessageCredential</span></span>|<span data-ttu-id="0883a-136">Bütünlük, gizlilik ve sunucu kimlik doğrulama ile taşıma güvenliği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="0883a-136">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="0883a-137">İstemci kimlik doğrulaması SOAP iletisi güvenlik yoluyla sağlanır.</span><span class="sxs-lookup"><span data-stu-id="0883a-137">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="0883a-138">Bu mod, kullanıcının kullanıcı adı/parola kullanarak kimlik doğrulaması ve ileti aktarma güvenliğini sağlamak için var olan bir HTTP dağıtım olduğunda geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="0883a-138">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|  
|<span data-ttu-id="0883a-139">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="0883a-139">TransportCredentialOnly</span></span>|<span data-ttu-id="0883a-140">Bu mod, ileti bütünlüğü ve gizliliği sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="0883a-140">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="0883a-141">Http tabanlı istemci kimlik doğrulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="0883a-141">It provides http-based client authentication.</span></span> <span data-ttu-id="0883a-142">Bu mod dikkatli kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0883a-142">This mode should be used with caution.</span></span> <span data-ttu-id="0883a-143">Burada taşıma güvenliği (IPSec gibi) diğer yollarla sağlanmaktadır ve yalnızca istemci kimlik doğrulaması tarafından sağlanan ortamlarda kullanılmalıdır [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] altyapı.</span><span class="sxs-lookup"><span data-stu-id="0883a-143">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0883a-144">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0883a-144">Child Elements</span></span>  
  
|<span data-ttu-id="0883a-145">Öğe</span><span class="sxs-lookup"><span data-stu-id="0883a-145">Element</span></span>|<span data-ttu-id="0883a-146">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0883a-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0883a-147">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="0883a-147">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-nethttpbinding.md)|<span data-ttu-id="0883a-148">Temel HTTP hizmeti Aktarım güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0883a-148">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="0883a-149">Bu öğe karşılık gelen <xref:System.ServiceModel.HttpTransportSecurity>.</span><span class="sxs-lookup"><span data-stu-id="0883a-149">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|  
|[<span data-ttu-id="0883a-150">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="0883a-150">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-nethttpbinding.md)|<span data-ttu-id="0883a-151">Temel HTTP hizmeti ileti güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0883a-151">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="0883a-152">Bu öğe karşılık gelen <!--zz <xref:System.ServiceModel.NetHttpMessageSecurity> --> `System.ServiceModel.NetHttpMessageSecurity`.</span><span class="sxs-lookup"><span data-stu-id="0883a-152">This element corresponds to <!--zz <xref:System.ServiceModel.NetHttpMessageSecurity> --> `System.ServiceModel.NetHttpMessageSecurity`.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0883a-153">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0883a-153">Parent Elements</span></span>  
  
|<span data-ttu-id="0883a-154">Öğe</span><span class="sxs-lookup"><span data-stu-id="0883a-154">Element</span></span>|<span data-ttu-id="0883a-155">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0883a-155">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0883a-156">bağlama</span><span class="sxs-lookup"><span data-stu-id="0883a-156">binding</span></span>|<span data-ttu-id="0883a-157">Bağlama öğesi [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="0883a-157">The binding element of the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0883a-158">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0883a-158">Remarks</span></span>  
 <span data-ttu-id="0883a-159">Varsayılan olarak, SOAP ileti güvenli olmadığından ve istemci kimliği doğrulanmamış.</span><span class="sxs-lookup"><span data-stu-id="0883a-159">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="0883a-160">Bu öğe için ek güvenlik ayarlarını yapılandırmanızı sağlar `netHttpBinding` öğesi.</span><span class="sxs-lookup"><span data-stu-id="0883a-160">This element enables you to configure additional security settings for the `netHttpBinding` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0883a-161">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0883a-161">See Also</span></span>  
 <xref:System.ServiceModel.NetHttpBinding.Security%2A>  
 <span data-ttu-id="0883a-162"><xref:System.ServiceModel.Configuration.NetHttpBindingElement.Security%2A></span><span class="sxs-lookup"><span data-stu-id="0883a-162"><xref:System.ServiceModel.Configuration.NetHttpBindingElement.Security%2A></span></span>    
 [<span data-ttu-id="0883a-163">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="0883a-163">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="0883a-164">Kimlik Bilgisi Türü Seçme</span><span class="sxs-lookup"><span data-stu-id="0883a-164">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="0883a-165">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="0883a-165">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="0883a-166">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="0883a-166">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="0883a-167">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="0883a-167">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="0883a-168">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="0883a-168">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)

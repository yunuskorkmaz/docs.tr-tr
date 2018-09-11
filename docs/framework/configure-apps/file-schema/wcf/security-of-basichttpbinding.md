---
title: '&lt;basicHttpBinding&gt; &lt;güvenliği&gt;'
ms.date: 03/30/2017
ms.assetid: 6432708d-5465-4bd9-bfc2-466742db99cb
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 2adb5736cca59d42ab3c62d61513bbfd80a4be04
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44277659"
---
# <a name="ltsecuritygt-of-ltbasichttpbindinggt"></a><span data-ttu-id="d0ed6-102">&lt;basicHttpBinding&gt; &lt;güvenliği&gt;</span><span class="sxs-lookup"><span data-stu-id="d0ed6-102">&lt;security&gt; of &lt;basicHttpBinding&gt;</span></span>
<span data-ttu-id="d0ed6-103">Güvenlik yeteneklerini tanımlar [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="d0ed6-103">Defines the security capabilities of the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>  
  
 <span data-ttu-id="d0ed6-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d0ed6-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d0ed6-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="d0ed6-105">\<bindings></span></span>  
<span data-ttu-id="d0ed6-106">\<basicHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="d0ed6-106">\<basicHttpBinding></span></span>  
<span data-ttu-id="d0ed6-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="d0ed6-107">\<binding></span></span>  
<span data-ttu-id="d0ed6-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="d0ed6-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0ed6-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d0ed6-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d0ed6-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d0ed6-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d0ed6-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d0ed6-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d0ed6-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d0ed6-112">Attributes</span></span>  
  
|<span data-ttu-id="d0ed6-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d0ed6-113">Attribute</span></span>|<span data-ttu-id="d0ed6-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d0ed6-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d0ed6-115">mod</span><span class="sxs-lookup"><span data-stu-id="d0ed6-115">mode</span></span>|<span data-ttu-id="d0ed6-116">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="d0ed6-116">Optional.</span></span> <span data-ttu-id="d0ed6-117">Kullanılan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="d0ed6-117">Specifies the type of security that is used.</span></span> <span data-ttu-id="d0ed6-118">Varsayılan, `None` değeridir.</span><span class="sxs-lookup"><span data-stu-id="d0ed6-118">The default is `None`.</span></span> <span data-ttu-id="d0ed6-119">Bu öznitelik türünde <xref:System.ServiceModel.BasicHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="d0ed6-119">This attribute is of type <xref:System.ServiceModel.BasicHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="d0ed6-120">mod özniteliği</span><span class="sxs-lookup"><span data-stu-id="d0ed6-120">mode Attribute</span></span>  
  
|<span data-ttu-id="d0ed6-121">Değer</span><span class="sxs-lookup"><span data-stu-id="d0ed6-121">Value</span></span>|<span data-ttu-id="d0ed6-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d0ed6-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d0ed6-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="d0ed6-123">None</span></span>|<span data-ttu-id="d0ed6-124">-Sıradaki iletiler, aktarım sırasında sağlanmaz.</span><span class="sxs-lookup"><span data-stu-id="d0ed6-124">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="d0ed6-125">Taşıma</span><span class="sxs-lookup"><span data-stu-id="d0ed6-125">Transport</span></span>|<span data-ttu-id="d0ed6-126">HTTPS aktarımı kullanarak güvenliği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="d0ed6-126">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="d0ed6-127">SOAP iletilerini HTTPS kullanılarak güvenli hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="d0ed6-127">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="d0ed6-128">Hizmet, hizmetin X.509 sertifikası kullanarak istemci kimlik doğrulaması yapılır.</span><span class="sxs-lookup"><span data-stu-id="d0ed6-128">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="d0ed6-129">İstemci tarafından sağlanan ClientCredentialType kullanarak kimlik doğrulaması yapılır.</span><span class="sxs-lookup"><span data-stu-id="d0ed6-129">The client is authenticated using the ClientCredentialType supplied.</span></span> <span data-ttu-id="d0ed6-130">Bkz: [ \<aktarım >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="d0ed6-130">See the [\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md).</span></span>|  
|<span data-ttu-id="d0ed6-131">İleti</span><span class="sxs-lookup"><span data-stu-id="d0ed6-131">Message</span></span>|<span data-ttu-id="d0ed6-132">SOAP ileti güveliği kullanarak güvenliği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="d0ed6-132">Security is provided using SOAP message security.</span></span> <span data-ttu-id="d0ed6-133">Varsayılan olarak, gövde imzalı ve şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="d0ed6-133">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="d0ed6-134">Bu bağlama için sistem sunucu sertifikası istemciyi bant dışından sağlanmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d0ed6-134">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="d0ed6-135">Yalnızca geçerli `ClientCredentialType` Bu bağlama için `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="d0ed6-135">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|  
|<span data-ttu-id="d0ed6-136">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="d0ed6-136">TransportWithMessageCredential</span></span>|<span data-ttu-id="d0ed6-137">Bütünlüğü, gizliliği ve sunucu kimlik doğrulaması ile Aktarım güvenliği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="d0ed6-137">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="d0ed6-138">İstemci kimlik doğrulaması yoluyla SOAP ileti güvenliği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="d0ed6-138">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="d0ed6-139">Bu mod, kullanıcının kullanıcı adı/parola kullanarak kimlik doğrulaması ve ileti aktarım güvenliğini sağlamak için var olan bir HTTP dağıtım olduğunda geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="d0ed6-139">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|  
|<span data-ttu-id="d0ed6-140">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="d0ed6-140">TransportCredentialOnly</span></span>|<span data-ttu-id="d0ed6-141">Bu mod, ileti bütünlüğü ve gizliliği sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="d0ed6-141">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="d0ed6-142">Bu, http tabanlı istemci kimlik doğrulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="d0ed6-142">It provides http-based client authentication.</span></span> <span data-ttu-id="d0ed6-143">Bu mod, dikkatli kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d0ed6-143">This mode should be used with caution.</span></span> <span data-ttu-id="d0ed6-144">Burada aktarım güvenliği (IPSec gibi) diğer yollarla sağlanmaktadır ve yalnızca istemci kimlik doğrulaması WCF altyapısı tarafından sağlanan ortamlarda kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d0ed6-144">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d0ed6-145">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d0ed6-145">Child Elements</span></span>  
  
|<span data-ttu-id="d0ed6-146">Öğe</span><span class="sxs-lookup"><span data-stu-id="d0ed6-146">Element</span></span>|<span data-ttu-id="d0ed6-147">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d0ed6-147">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d0ed6-148">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="d0ed6-148">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md)|<span data-ttu-id="d0ed6-149">Temel HTTP hizmeti için taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d0ed6-149">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="d0ed6-150">Bu öğe için karşılık gelen <xref:System.ServiceModel.HttpTransportSecurity>.</span><span class="sxs-lookup"><span data-stu-id="d0ed6-150">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|  
|[<span data-ttu-id="d0ed6-151">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="d0ed6-151">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-basichttpbinding.md)|<span data-ttu-id="d0ed6-152">Temel HTTP hizmeti için ileti güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d0ed6-152">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="d0ed6-153">Bu öğe için karşılık gelen <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span><span class="sxs-lookup"><span data-stu-id="d0ed6-153">This element corresponds to <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d0ed6-154">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d0ed6-154">Parent Elements</span></span>  
  
|<span data-ttu-id="d0ed6-155">Öğe</span><span class="sxs-lookup"><span data-stu-id="d0ed6-155">Element</span></span>|<span data-ttu-id="d0ed6-156">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d0ed6-156">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d0ed6-157">bağlama</span><span class="sxs-lookup"><span data-stu-id="d0ed6-157">binding</span></span>|<span data-ttu-id="d0ed6-158">Bağlama öğesi [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="d0ed6-158">The binding element of the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d0ed6-159">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d0ed6-159">Remarks</span></span>  
 <span data-ttu-id="d0ed6-160">Varsayılan olarak, SOAP ileti güvenli olmadığından ve istemci kimliği doğrulanmamış.</span><span class="sxs-lookup"><span data-stu-id="d0ed6-160">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="d0ed6-161">Bu öğe için ek güvenlik ayarları yapılandırmanızı sağlar `basicHttpBinding` öğesi.</span><span class="sxs-lookup"><span data-stu-id="d0ed6-161">This element enables you to configure additional security settings for the `basicHttpBinding` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0ed6-162">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d0ed6-162">See Also</span></span>  
 <xref:System.ServiceModel.BasicHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>  
 <xref:System.ServiceModel.BasicHttpSecurity>  
 [<span data-ttu-id="d0ed6-163">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="d0ed6-163">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="d0ed6-164">Kimlik Bilgisi Türü Seçme</span><span class="sxs-lookup"><span data-stu-id="d0ed6-164">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="d0ed6-165">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="d0ed6-165">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="d0ed6-166">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d0ed6-166">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="d0ed6-167">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="d0ed6-167">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="d0ed6-168">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="d0ed6-168">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)

---
title: <security> / <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 6432708d-5465-4bd9-bfc2-466742db99cb
ms.openlocfilehash: 6144e5448526d7f2a7c89693f70f71a7f26c4a22
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183669"
---
# <a name="security-of-basichttpbinding"></a><span data-ttu-id="4982f-102">\<security> / \<basicHttpBinding></span><span class="sxs-lookup"><span data-stu-id="4982f-102">\<security> of \<basicHttpBinding></span></span>

<span data-ttu-id="4982f-103">Uygulamasının güvenlik yeteneklerini tanımlar [\<basicHttpBinding>](basichttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="4982f-103">Defines the security capabilities of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<basicHttpBinding>**](basichttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="4982f-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="4982f-104">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="string" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4982f-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4982f-105">Attributes and Elements</span></span>  

 <span data-ttu-id="4982f-106">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="4982f-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4982f-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4982f-107">Attributes</span></span>  
  
|<span data-ttu-id="4982f-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4982f-108">Attribute</span></span>|<span data-ttu-id="4982f-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4982f-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4982f-110">mod</span><span class="sxs-lookup"><span data-stu-id="4982f-110">mode</span></span>|<span data-ttu-id="4982f-111">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="4982f-111">Optional.</span></span> <span data-ttu-id="4982f-112">Kullanılan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="4982f-112">Specifies the type of security that is used.</span></span> <span data-ttu-id="4982f-113">Varsayılan değer: `None`.</span><span class="sxs-lookup"><span data-stu-id="4982f-113">The default is `None`.</span></span> <span data-ttu-id="4982f-114">Bu öznitelik türü <xref:System.ServiceModel.BasicHttpSecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="4982f-114">This attribute is of type <xref:System.ServiceModel.BasicHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="4982f-115">mode özniteliği</span><span class="sxs-lookup"><span data-stu-id="4982f-115">mode Attribute</span></span>  
  
|<span data-ttu-id="4982f-116">Değer</span><span class="sxs-lookup"><span data-stu-id="4982f-116">Value</span></span>|<span data-ttu-id="4982f-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4982f-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4982f-118">Yok</span><span class="sxs-lookup"><span data-stu-id="4982f-118">None</span></span>|<span data-ttu-id="4982f-119">-İletiler aktarım sırasında güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="4982f-119">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="4982f-120">Aktarım</span><span class="sxs-lookup"><span data-stu-id="4982f-120">Transport</span></span>|<span data-ttu-id="4982f-121">Güvenlik, HTTPS taşıması kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="4982f-121">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="4982f-122">SOAP iletilerinin HTTPS kullanılarak güvenliği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="4982f-122">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="4982f-123">Hizmetin, hizmetin X. 509.440 sertifikası kullanılarak istemcinin kimliği doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="4982f-123">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="4982f-124">İstemcinin kimliği, sağlanan ClientCredentialType kullanılarak doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="4982f-124">The client is authenticated using the ClientCredentialType supplied.</span></span> <span data-ttu-id="4982f-125">Bkz [\<transport>](transport-of-basichttpbinding.md) ..</span><span class="sxs-lookup"><span data-stu-id="4982f-125">See the [\<transport>](transport-of-basichttpbinding.md).</span></span>|  
|<span data-ttu-id="4982f-126">İleti</span><span class="sxs-lookup"><span data-stu-id="4982f-126">Message</span></span>|<span data-ttu-id="4982f-127">Güvenlik, SOAP iletisi güvenliği kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="4982f-127">Security is provided using SOAP message security.</span></span> <span data-ttu-id="4982f-128">Varsayılan olarak, gövde şifrelenir ve imzalanır.</span><span class="sxs-lookup"><span data-stu-id="4982f-128">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="4982f-129">Bu bağlama için, sistem, sunucu sertifikasının bant dışı istemciye sağlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4982f-129">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="4982f-130">`ClientCredentialType`Bu bağlama için geçerli tek geçerlidir `Certificate` .</span><span class="sxs-lookup"><span data-stu-id="4982f-130">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|  
|<span data-ttu-id="4982f-131">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="4982f-131">TransportWithMessageCredential</span></span>|<span data-ttu-id="4982f-132">Bütünlük, gizlilik ve sunucu kimlik doğrulaması, aktarım güvenliği tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="4982f-132">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="4982f-133">İstemci kimlik doğrulaması, SOAP iletisi güvenliği aracılığıyla sağlanır.</span><span class="sxs-lookup"><span data-stu-id="4982f-133">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="4982f-134">Bu mod, Kullanıcı Kullanıcı adı/parola kullanarak kimlik doğrulaması yapıldığında ve ileti aktarımını güvenli hale getirmek için mevcut bir HTTP dağıtımı olduğunda geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="4982f-134">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|  
|<span data-ttu-id="4982f-135">Yalnızca transportcredential</span><span class="sxs-lookup"><span data-stu-id="4982f-135">TransportCredentialOnly</span></span>|<span data-ttu-id="4982f-136">Bu mod ileti bütünlüğü ve gizliliği sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="4982f-136">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="4982f-137">HTTP tabanlı istemci kimlik doğrulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="4982f-137">It provides http-based client authentication.</span></span> <span data-ttu-id="4982f-138">Bu mod dikkatli kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4982f-138">This mode should be used with caution.</span></span> <span data-ttu-id="4982f-139">Aktarım güvenliğinin diğer yollarla (IPSec gibi) sağlandığı ve yalnızca WCF altyapısı tarafından istemci kimlik doğrulamasının sağlandığı ortamlarda kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4982f-139">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4982f-140">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4982f-140">Child Elements</span></span>  
  
|<span data-ttu-id="4982f-141">Öğe</span><span class="sxs-lookup"><span data-stu-id="4982f-141">Element</span></span>|<span data-ttu-id="4982f-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4982f-142">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-basichttpbinding.md)|<span data-ttu-id="4982f-143">Temel bir HTTP hizmeti için taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4982f-143">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="4982f-144">Bu öğe öğesine karşılık gelir <xref:System.ServiceModel.HttpTransportSecurity> .</span><span class="sxs-lookup"><span data-stu-id="4982f-144">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|  
|[\<message>](message-of-basichttpbinding.md)|<span data-ttu-id="4982f-145">Temel bir HTTP hizmeti için ileti güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4982f-145">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="4982f-146">Bu öğe öğesine karşılık gelir <xref:System.ServiceModel.BasicHttpMessageSecurity> .</span><span class="sxs-lookup"><span data-stu-id="4982f-146">This element corresponds to <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4982f-147">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4982f-147">Parent Elements</span></span>  
  
|<span data-ttu-id="4982f-148">Öğe</span><span class="sxs-lookup"><span data-stu-id="4982f-148">Element</span></span>|<span data-ttu-id="4982f-149">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4982f-149">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4982f-150">bağlama</span><span class="sxs-lookup"><span data-stu-id="4982f-150">binding</span></span>|<span data-ttu-id="4982f-151">Öğesinin bağlama öğesi [\<basicHttpBinding>](basichttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="4982f-151">The binding element of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4982f-152">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4982f-152">Remarks</span></span>  

 <span data-ttu-id="4982f-153">Varsayılan olarak, SOAP iletisi güvenli değildir ve istemcinin kimliği doğrulanmaz.</span><span class="sxs-lookup"><span data-stu-id="4982f-153">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="4982f-154">Bu öğe, öğesi için ek güvenlik ayarları yapılandırmanıza olanak sağlar `basicHttpBinding` .</span><span class="sxs-lookup"><span data-stu-id="4982f-154">This element enables you to configure additional security settings for the `basicHttpBinding` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4982f-155">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4982f-155">See also</span></span>

- <xref:System.ServiceModel.BasicHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="4982f-156">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="4982f-156">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="4982f-157">Kimlik Bilgisi Türü Seçme</span><span class="sxs-lookup"><span data-stu-id="4982f-157">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="4982f-158">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="4982f-158">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="4982f-159">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="4982f-159">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="4982f-160">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="4982f-160">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)

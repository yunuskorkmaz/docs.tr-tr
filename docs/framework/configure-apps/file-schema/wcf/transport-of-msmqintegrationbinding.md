---
title: "&lt;msmqIntegrationBinding&gt; &lt;taşıma&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 054579e3-7fdd-47df-99ca-952706ba5c8e
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 03cd07681c111f51a4ea02ac46354fa9a19f42d3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="lttransportgt-of-ltmsmqintegrationbindinggt"></a><span data-ttu-id="444c0-102">&lt;msmqIntegrationBinding&gt; &lt;taşıma&gt;</span><span class="sxs-lookup"><span data-stu-id="444c0-102">&lt;transport&gt; of &lt;msmqIntegrationBinding&gt;</span></span>
<span data-ttu-id="444c0-103">Message Queuing tümleştirme taşıma için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="444c0-103">Defines the security settings for the Message Queuing integration transport.</span></span>  
  
 <span data-ttu-id="444c0-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="444c0-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="444c0-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="444c0-105">\<bindings></span></span>  
<span data-ttu-id="444c0-106">msmqIntegrationBinding</span><span class="sxs-lookup"><span data-stu-id="444c0-106">msmqIntegrationBinding</span></span>  
<span data-ttu-id="444c0-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="444c0-107">\<binding></span></span>  
<span data-ttu-id="444c0-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="444c0-108">\<security></span></span>  
<span data-ttu-id="444c0-109">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="444c0-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="444c0-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="444c0-110">Syntax</span></span>  
  
```xml  
<security>  
    <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"  
        msmqEncryptionAlgorithm="RC4Stream/AES"  
        msmqProtectionLevel="None/Sign/EncryptAndSign"  
        msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />  
</security>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="444c0-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="444c0-111">Attributes and Elements</span></span>  
 <span data-ttu-id="444c0-112">Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır</span><span class="sxs-lookup"><span data-stu-id="444c0-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="444c0-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="444c0-113">Attributes</span></span>  
  
|<span data-ttu-id="444c0-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="444c0-114">Attribute</span></span>|<span data-ttu-id="444c0-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="444c0-115">Description</span></span>|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|<span data-ttu-id="444c0-116">İletinin MSMQ taşıma tarafından nasıl doğrulanmış gerekir belirtir.</span><span class="sxs-lookup"><span data-stu-id="444c0-116">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="444c0-117">Bu ayarlanırsa `None`, değeri `msmqProtectionLevel` özniteliği de ayarlanmalıdır `None`.</span><span class="sxs-lookup"><span data-stu-id="444c0-117">If this is set to `None`, the value of the `msmqProtectionLevel` attribute must also be set to `None`.</span></span><br /><br /> <span data-ttu-id="444c0-118">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="444c0-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="444c0-119">-Hiçbiri: Kimlik doğrulaması yok.</span><span class="sxs-lookup"><span data-stu-id="444c0-119">-   None: No authentication.</span></span><br /><span data-ttu-id="444c0-120">-WindowsDomain: SID iletiyle ilişkili X.509 sertifikası almak için Active Directory kimlik doğrulama mekanizması kullanır.</span><span class="sxs-lookup"><span data-stu-id="444c0-120">-   WindowsDomain: The authentication mechanism uses Active Directory to get the X.509 certificate for the SID associated with the message.</span></span> <span data-ttu-id="444c0-121">Bu, daha sonra kullanıcı emin olmak için ACL sırasının sıraya yazmak için yeterli izne sahip denetlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="444c0-121">This is then used to check the ACL of the queue to ensure the user has permission to write to the queue.</span></span><br /><span data-ttu-id="444c0-122">-Sertifika: Kanal sertifikayı sertifika deposundan alır.</span><span class="sxs-lookup"><span data-stu-id="444c0-122">-   Certificate: The channel gets the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="444c0-123">WindowsDomain varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="444c0-123">The default value is WindowsDomain.</span></span> <span data-ttu-id="444c0-124">Bu öznitelik türünde <xref:System.ServiceModel.MsmqAuthenticationMode>.</span><span class="sxs-lookup"><span data-stu-id="444c0-124">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode>.</span></span>|  
|`msmqEncryptionAlgorithm`|<span data-ttu-id="444c0-125">İleti şifreleme hattaki iletileri ileti sırası yöneticileri arasında aktarırken kullanılacak algoritmayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="444c0-125">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="444c0-126">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="444c0-126">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="444c0-127">-RC4Stream</span><span class="sxs-lookup"><span data-stu-id="444c0-127">-   RC4Stream</span></span><br /><span data-ttu-id="444c0-128">-AES</span><span class="sxs-lookup"><span data-stu-id="444c0-128">-   AES</span></span><br /><br /> <span data-ttu-id="444c0-129">RC4Stream varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="444c0-129">The default value is RC4Stream.</span></span> <span data-ttu-id="444c0-130">Bu öznitelik türünde <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="444c0-130">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|`msmqProtectionLevel`|<span data-ttu-id="444c0-131">İletinin MSMQ taşıma düzeyinde güvenliği nasıl belirtir.</span><span class="sxs-lookup"><span data-stu-id="444c0-131">Specifies how the message is secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="444c0-132">İleti bütünlüğü ve takası da EncryptAndSign sağlar ancak şifreleme ileti bütünlüğü sağlar; diğer bir deyişle, iletinin gerçekten gönderenden gelir ve gönderenin kim kendisinin gerçekleştirilmesine söyler.</span><span class="sxs-lookup"><span data-stu-id="444c0-132">Encryption ensures message integrity while EncryptAndSign ensures both message integrity and non-repudiation; that is, the message indeed comes from the sender and the sender is who he says he is.</span></span><br /><br /> <span data-ttu-id="444c0-133">-Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="444c0-133">-   Valid values include the following:</span></span><br /><span data-ttu-id="444c0-134">-Hiçbiri: Koruma yok.</span><span class="sxs-lookup"><span data-stu-id="444c0-134">-   None: No protection.</span></span><br /><span data-ttu-id="444c0-135">-Oturum: İletileri imzalanmıştır.</span><span class="sxs-lookup"><span data-stu-id="444c0-135">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="444c0-136">-Da EncryptAndSign: İletileri şifrelenmiş ve imzalanmış.</span><span class="sxs-lookup"><span data-stu-id="444c0-136">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="444c0-137">Varsayılan değer işaretidir.</span><span class="sxs-lookup"><span data-stu-id="444c0-137">The default value is Sign.</span></span> <span data-ttu-id="444c0-138">Bu öznitelik ProtectionLevel türüdür.</span><span class="sxs-lookup"><span data-stu-id="444c0-138">This attribute is of type ProtectionLevel.</span></span>|  
|`msmqSecureHashAlgorithm`|<span data-ttu-id="444c0-139">-Özet imzaları bir parçası olarak bilgisayar kullanılacak algoritmayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="444c0-139">-   Specifies the algorithm to be used in computing the digest as part of signatures.</span></span> <span data-ttu-id="444c0-140">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="444c0-140">Valid values include the following:</span></span><br /><span data-ttu-id="444c0-141">-MD5</span><span class="sxs-lookup"><span data-stu-id="444c0-141">-   MD5</span></span><br /><span data-ttu-id="444c0-142">-SHA1</span><span class="sxs-lookup"><span data-stu-id="444c0-142">-   SHA1</span></span><br /><span data-ttu-id="444c0-143">-SHA256</span><span class="sxs-lookup"><span data-stu-id="444c0-143">-   SHA256</span></span><br /><span data-ttu-id="444c0-144">-SHA512</span><span class="sxs-lookup"><span data-stu-id="444c0-144">-   SHA512</span></span><br /><br /> <span data-ttu-id="444c0-145">SHA1 varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="444c0-145">The default value is SHA1.</span></span> <span data-ttu-id="444c0-146">Bu öznitelik türünde <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="444c0-146">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="444c0-147">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="444c0-147">Child Elements</span></span>  
 <span data-ttu-id="444c0-148">Yok.</span><span class="sxs-lookup"><span data-stu-id="444c0-148">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="444c0-149">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="444c0-149">Parent Elements</span></span>  
  
|<span data-ttu-id="444c0-150">Öğe</span><span class="sxs-lookup"><span data-stu-id="444c0-150">Element</span></span>|<span data-ttu-id="444c0-151">Açıklama</span><span class="sxs-lookup"><span data-stu-id="444c0-151">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="444c0-152">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="444c0-152">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|<span data-ttu-id="444c0-153">MSMQ bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="444c0-153">Defines the security settings for a MSMQ binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="444c0-154">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="444c0-154">Remarks</span></span>  
 <span data-ttu-id="444c0-155">Bu öğe Message Queuing tümleştirme taşıma için güvenlik ayarlarını saklar.</span><span class="sxs-lookup"><span data-stu-id="444c0-155">This element encapsulates the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="444c0-156">Ayarları Message Queuing tümleştirme ve sıraya alınan taşımaları için aynıdır.</span><span class="sxs-lookup"><span data-stu-id="444c0-156">The settings are the same for both the Message Queuing integration and queued transports.</span></span> <span data-ttu-id="444c0-157">Kimlik doğrulama modu, şifreleme algoritması, güvenli karma algoritması ve koruma düzeyini ayarlamanıza imkan sağlar.</span><span class="sxs-lookup"><span data-stu-id="444c0-157">It enables you to set the Authentication Mode, Encryption Algorithm, Secure Hash Algorithm, and Protection Level.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="444c0-158">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="444c0-158">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>  
 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.MsmqTransportSecurity>  
 [<span data-ttu-id="444c0-159">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="444c0-159">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="444c0-160">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="444c0-160">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="444c0-161">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="444c0-161">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="444c0-162">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="444c0-162">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="444c0-163">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="444c0-163">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="444c0-164">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="444c0-164">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)

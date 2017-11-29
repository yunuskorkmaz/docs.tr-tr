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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d9def7fbd0082cc7fa9d9f18388604383cb71f9b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="lttransportgt-of-ltmsmqintegrationbindinggt"></a><span data-ttu-id="89ec7-102">&lt;msmqIntegrationBinding&gt; &lt;taşıma&gt;</span><span class="sxs-lookup"><span data-stu-id="89ec7-102">&lt;transport&gt; of &lt;msmqIntegrationBinding&gt;</span></span>
<span data-ttu-id="89ec7-103">Message Queuing tümleştirme taşıma için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="89ec7-103">Defines the security settings for the Message Queuing integration transport.</span></span>  
  
 <span data-ttu-id="89ec7-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="89ec7-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="89ec7-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="89ec7-105">\<bindings></span></span>  
<span data-ttu-id="89ec7-106">msmqIntegrationBinding</span><span class="sxs-lookup"><span data-stu-id="89ec7-106">msmqIntegrationBinding</span></span>  
<span data-ttu-id="89ec7-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="89ec7-107">\<binding></span></span>  
<span data-ttu-id="89ec7-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="89ec7-108">\<security></span></span>  
<span data-ttu-id="89ec7-109">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="89ec7-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89ec7-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="89ec7-110">Syntax</span></span>  
  
```xml  
<security>  
    <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"  
        msmqEncryptionAlgorithm="RC4Stream/AES"  
        msmqProtectionLevel="None/Sign/EncryptAndSign"  
        msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />  
</security>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="89ec7-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="89ec7-111">Attributes and Elements</span></span>  
 <span data-ttu-id="89ec7-112">Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır</span><span class="sxs-lookup"><span data-stu-id="89ec7-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="89ec7-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="89ec7-113">Attributes</span></span>  
  
|<span data-ttu-id="89ec7-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="89ec7-114">Attribute</span></span>|<span data-ttu-id="89ec7-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="89ec7-115">Description</span></span>|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|<span data-ttu-id="89ec7-116">İletinin MSMQ taşıma tarafından nasıl doğrulanmış gerekir belirtir.</span><span class="sxs-lookup"><span data-stu-id="89ec7-116">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="89ec7-117">Bu ayarlanırsa `None`, değeri `msmqProtectionLevel` özniteliği de ayarlanmalıdır `None`.</span><span class="sxs-lookup"><span data-stu-id="89ec7-117">If this is set to `None`, the value of the `msmqProtectionLevel` attribute must also be set to `None`.</span></span><br /><br /> <span data-ttu-id="89ec7-118">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="89ec7-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="89ec7-119">-Hiçbiri: Kimlik doğrulaması yok.</span><span class="sxs-lookup"><span data-stu-id="89ec7-119">-   None: No authentication.</span></span><br /><span data-ttu-id="89ec7-120">-WindowsDomain: SID iletiyle ilişkili X.509 sertifikası almak için Active Directory kimlik doğrulama mekanizması kullanır.</span><span class="sxs-lookup"><span data-stu-id="89ec7-120">-   WindowsDomain: The authentication mechanism uses Active Directory to get the X.509 certificate for the SID associated with the message.</span></span> <span data-ttu-id="89ec7-121">Bu, daha sonra kullanıcı emin olmak için ACL sırasının sıraya yazmak için yeterli izne sahip denetlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="89ec7-121">This is then used to check the ACL of the queue to ensure the user has permission to write to the queue.</span></span><br /><span data-ttu-id="89ec7-122">-Sertifika: Kanal sertifikayı sertifika deposundan alır.</span><span class="sxs-lookup"><span data-stu-id="89ec7-122">-   Certificate: The channel gets the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="89ec7-123">WindowsDomain varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="89ec7-123">The default value is WindowsDomain.</span></span> <span data-ttu-id="89ec7-124">Bu öznitelik türünde <xref:System.ServiceModel.MsmqAuthenticationMode>.</span><span class="sxs-lookup"><span data-stu-id="89ec7-124">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode>.</span></span>|  
|`msmqEncryptionAlgorithm`|<span data-ttu-id="89ec7-125">İleti şifreleme hattaki iletileri ileti sırası yöneticileri arasında aktarırken kullanılacak algoritmayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="89ec7-125">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="89ec7-126">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="89ec7-126">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="89ec7-127">-RC4Stream</span><span class="sxs-lookup"><span data-stu-id="89ec7-127">-   RC4Stream</span></span><br /><span data-ttu-id="89ec7-128">-AES</span><span class="sxs-lookup"><span data-stu-id="89ec7-128">-   AES</span></span><br /><br /> <span data-ttu-id="89ec7-129">RC4Stream varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="89ec7-129">The default value is RC4Stream.</span></span> <span data-ttu-id="89ec7-130">Bu öznitelik türünde <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="89ec7-130">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|`msmqProtectionLevel`|<span data-ttu-id="89ec7-131">İletinin MSMQ taşıma düzeyinde güvenliği nasıl belirtir.</span><span class="sxs-lookup"><span data-stu-id="89ec7-131">Specifies how the message is secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="89ec7-132">İleti bütünlüğü ve takası da EncryptAndSign sağlar ancak şifreleme ileti bütünlüğü sağlar; diğer bir deyişle, iletinin gerçekten gönderenden gelir ve gönderenin kim kendisinin gerçekleştirilmesine söyler.</span><span class="sxs-lookup"><span data-stu-id="89ec7-132">Encryption ensures message integrity while EncryptAndSign ensures both message integrity and non-repudiation; that is, the message indeed comes from the sender and the sender is who he says he is.</span></span><br /><br /> <span data-ttu-id="89ec7-133">-Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="89ec7-133">-   Valid values include the following:</span></span><br /><span data-ttu-id="89ec7-134">-Hiçbiri: Koruma yok.</span><span class="sxs-lookup"><span data-stu-id="89ec7-134">-   None: No protection.</span></span><br /><span data-ttu-id="89ec7-135">-Oturum: İletileri imzalanmıştır.</span><span class="sxs-lookup"><span data-stu-id="89ec7-135">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="89ec7-136">-Da EncryptAndSign: İletileri şifrelenmiş ve imzalanmış.</span><span class="sxs-lookup"><span data-stu-id="89ec7-136">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="89ec7-137">Varsayılan değer işaretidir.</span><span class="sxs-lookup"><span data-stu-id="89ec7-137">The default value is Sign.</span></span> <span data-ttu-id="89ec7-138">Bu öznitelik ProtectionLevel türüdür.</span><span class="sxs-lookup"><span data-stu-id="89ec7-138">This attribute is of type ProtectionLevel.</span></span>|  
|`msmqSecureHashAlgorithm`|<span data-ttu-id="89ec7-139">-Özet imzaları bir parçası olarak bilgisayar kullanılacak algoritmayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="89ec7-139">-   Specifies the algorithm to be used in computing the digest as part of signatures.</span></span> <span data-ttu-id="89ec7-140">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="89ec7-140">Valid values include the following:</span></span><br /><span data-ttu-id="89ec7-141">-MD5</span><span class="sxs-lookup"><span data-stu-id="89ec7-141">-   MD5</span></span><br /><span data-ttu-id="89ec7-142">-SHA1</span><span class="sxs-lookup"><span data-stu-id="89ec7-142">-   SHA1</span></span><br /><span data-ttu-id="89ec7-143">-SHA256</span><span class="sxs-lookup"><span data-stu-id="89ec7-143">-   SHA256</span></span><br /><span data-ttu-id="89ec7-144">-SHA512</span><span class="sxs-lookup"><span data-stu-id="89ec7-144">-   SHA512</span></span><br /><br /> <span data-ttu-id="89ec7-145">SHA1 varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="89ec7-145">The default value is SHA1.</span></span> <span data-ttu-id="89ec7-146">Bu öznitelik türünde <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="89ec7-146">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="89ec7-147">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="89ec7-147">Child Elements</span></span>  
 <span data-ttu-id="89ec7-148">Yok.</span><span class="sxs-lookup"><span data-stu-id="89ec7-148">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="89ec7-149">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="89ec7-149">Parent Elements</span></span>  
  
|<span data-ttu-id="89ec7-150">Öğe</span><span class="sxs-lookup"><span data-stu-id="89ec7-150">Element</span></span>|<span data-ttu-id="89ec7-151">Açıklama</span><span class="sxs-lookup"><span data-stu-id="89ec7-151">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="89ec7-152">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="89ec7-152">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|<span data-ttu-id="89ec7-153">MSMQ bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="89ec7-153">Defines the security settings for a MSMQ binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89ec7-154">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="89ec7-154">Remarks</span></span>  
 <span data-ttu-id="89ec7-155">Bu öğe Message Queuing tümleştirme taşıma için güvenlik ayarlarını saklar.</span><span class="sxs-lookup"><span data-stu-id="89ec7-155">This element encapsulates the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="89ec7-156">Ayarları Message Queuing tümleştirme ve sıraya alınan taşımaları için aynıdır.</span><span class="sxs-lookup"><span data-stu-id="89ec7-156">The settings are the same for both the Message Queuing integration and queued transports.</span></span> <span data-ttu-id="89ec7-157">Kimlik doğrulama modu, şifreleme algoritması, güvenli karma algoritması ve koruma düzeyini ayarlamanıza imkan sağlar.</span><span class="sxs-lookup"><span data-stu-id="89ec7-157">It enables you to set the Authentication Mode, Encryption Algorithm, Secure Hash Algorithm, and Protection Level.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89ec7-158">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="89ec7-158">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>  
 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.MsmqTransportSecurity>  
 [<span data-ttu-id="89ec7-159">Hizmetler ve istemcileri güvenli hale getirme</span><span class="sxs-lookup"><span data-stu-id="89ec7-159">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="89ec7-160">Hizmetler ve istemcileri güvenli hale getirme</span><span class="sxs-lookup"><span data-stu-id="89ec7-160">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="89ec7-161">Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="89ec7-161">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="89ec7-162">Sistem tarafından sağlanan bağlamaları yapılandırma</span><span class="sxs-lookup"><span data-stu-id="89ec7-162">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="89ec7-163">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="89ec7-163">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="89ec7-164">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="89ec7-164">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)

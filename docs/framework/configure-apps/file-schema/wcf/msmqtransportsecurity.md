---
title: '&lt;msmqTransportSecurity&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 092e911b-ab1b-4069-a26e-6134c3299e06
caps.latest.revision: "10"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: eee2cb916d79bf3b79e882cd757b10344121f6b2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltmsmqtransportsecuritygt"></a><span data-ttu-id="e8c31-102">&lt;msmqTransportSecurity&gt;</span><span class="sxs-lookup"><span data-stu-id="e8c31-102">&lt;msmqTransportSecurity&gt;</span></span>
<span data-ttu-id="e8c31-103">Özel bağlama için MSMQ taşıma güvenlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e8c31-103">Specifies MSMQ transport security settings for a custom binding.</span></span>  
  
 <span data-ttu-id="e8c31-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="e8c31-104">\<system.serviceModel></span></span>  
<span data-ttu-id="e8c31-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="e8c31-105">\<bindings></span></span>  
<span data-ttu-id="e8c31-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="e8c31-106">\<customBinding></span></span>  
<span data-ttu-id="e8c31-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="e8c31-107">\<binding></span></span>  
<span data-ttu-id="e8c31-108">\<msmqIntegration ></span><span class="sxs-lookup"><span data-stu-id="e8c31-108">\<msmqIntegration></span></span>  
<span data-ttu-id="e8c31-109">\<msmqTransportSecurity ></span><span class="sxs-lookup"><span data-stu-id="e8c31-109">\<msmqTransportSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8c31-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e8c31-110">Syntax</span></span>  
  
```xml  
<msmqTransportSecurity>  
   msmqAuthenticationMode="None/Windows/Certificate"  
   msmqEncryptionAlgorithm="RC4Stream/AES"  
   msmqProtectionLevel="None/Sign/EncryptAndSign"  
   msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />  
</msmqTransportSecurity>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e8c31-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e8c31-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e8c31-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e8c31-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e8c31-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e8c31-113">Attributes</span></span>  
  
|<span data-ttu-id="e8c31-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e8c31-114">Attribute</span></span>|<span data-ttu-id="e8c31-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e8c31-115">Description</span></span>|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|<span data-ttu-id="e8c31-116">İletinin MSMQ taşıma tarafından nasıl doğrulanmış gerekir belirtir.</span><span class="sxs-lookup"><span data-stu-id="e8c31-116">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="e8c31-117">Bu ayarlanırsa `None`, değeri `msmqProtectionLevel` özniteliği de ayarlanmalıdır `None`.</span><span class="sxs-lookup"><span data-stu-id="e8c31-117">If this is set to `None`, the value of the `msmqProtectionLevel` attribute must also be set to `None`.</span></span><br /><br /> <span data-ttu-id="e8c31-118">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e8c31-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="e8c31-119">-Hiçbiri: Kimlik doğrulaması yok.</span><span class="sxs-lookup"><span data-stu-id="e8c31-119">-   None: No authentication.</span></span><br /><span data-ttu-id="e8c31-120">-Windows: SID iletiyle ilişkili X.509 sertifikası almak için Active Directory kimlik doğrulama mekanizması kullanır.</span><span class="sxs-lookup"><span data-stu-id="e8c31-120">-   Windows: The authentication mechanism uses Active Directory to get the X.509 certificate for the SID associated with the message.</span></span> <span data-ttu-id="e8c31-121">Bu, daha sonra kullanıcı emin olmak için ACL sırasının sıraya yazmak için yeterli izne sahip denetlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e8c31-121">This is then used to check the ACL of the queue to ensure the user has permission to write to the queue.</span></span><br /><span data-ttu-id="e8c31-122">-Sertifika: Kanal sertifikayı sertifika deposundan alır.</span><span class="sxs-lookup"><span data-stu-id="e8c31-122">-   Certificate: The channel gets the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="e8c31-123">Windows varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="e8c31-123">The default value is Windows.</span></span> <span data-ttu-id="e8c31-124">Bu öznitelik türünde <xref:System.ServiceModel.MsmqAuthenticationMode>.</span><span class="sxs-lookup"><span data-stu-id="e8c31-124">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode>.</span></span>|  
|`msmqEncryptionAlgorithm`|<span data-ttu-id="e8c31-125">İleti şifreleme hattaki iletileri ileti sırası yöneticileri arasında aktarırken kullanılacak algoritmayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="e8c31-125">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="e8c31-126">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e8c31-126">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="e8c31-127">-RC4Stream</span><span class="sxs-lookup"><span data-stu-id="e8c31-127">-   RC4Stream</span></span><br /><span data-ttu-id="e8c31-128">-AES</span><span class="sxs-lookup"><span data-stu-id="e8c31-128">-   AES</span></span><br /><br /> <span data-ttu-id="e8c31-129">RC4Stream varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="e8c31-129">The default value is RC4Stream.</span></span> <span data-ttu-id="e8c31-130">Bu öznitelik türünde <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="e8c31-130">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|`msmqProtectionLevel`|<span data-ttu-id="e8c31-131">İletinin MSMQ taşıma düzeyinde güvenliği nasıl belirtir.</span><span class="sxs-lookup"><span data-stu-id="e8c31-131">Specifies how the message is secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="e8c31-132">İleti bütünlüğü ve takası da EncryptAndSign sağlar ancak şifreleme ileti bütünlüğü sağlar; diğer bir deyişle, iletinin gerçekten gönderenden gelir ve gönderenin kim kendisinin gerçekleştirilmesine söyler.</span><span class="sxs-lookup"><span data-stu-id="e8c31-132">Encryption ensures message integrity while EncryptAndSign ensures both message integrity and non-repudiation; that is, the message indeed comes from the sender and the sender is who he says he is.</span></span> <span data-ttu-id="e8c31-133">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e8c31-133">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="e8c31-134">-Hiçbiri: Koruma yok.</span><span class="sxs-lookup"><span data-stu-id="e8c31-134">-   None: No protection.</span></span><br /><span data-ttu-id="e8c31-135">-Oturum: İletileri imzalanmıştır.</span><span class="sxs-lookup"><span data-stu-id="e8c31-135">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="e8c31-136">-Da EncryptAndSign: İletileri şifrelenmiş ve imzalanmış.</span><span class="sxs-lookup"><span data-stu-id="e8c31-136">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="e8c31-137">Varsayılan değer işaretidir.</span><span class="sxs-lookup"><span data-stu-id="e8c31-137">The default value is Sign.</span></span> <span data-ttu-id="e8c31-138">Bu öznitelik türünde <xref:System.Net.Security.ProtectionLevel>.</span><span class="sxs-lookup"><span data-stu-id="e8c31-138">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
|`msmqSecureHashAlgorithm`|<span data-ttu-id="e8c31-139">Özet imzaları bir parçası olarak bilgisayar kullanılacak algoritmayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="e8c31-139">Specifies the algorithm to be used in computing the digest as part of signatures.</span></span> <span data-ttu-id="e8c31-140">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e8c31-140">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="e8c31-141">-MD5</span><span class="sxs-lookup"><span data-stu-id="e8c31-141">-   MD5</span></span><br /><span data-ttu-id="e8c31-142">-SHA1</span><span class="sxs-lookup"><span data-stu-id="e8c31-142">-   SHA1</span></span><br /><span data-ttu-id="e8c31-143">-SHA256</span><span class="sxs-lookup"><span data-stu-id="e8c31-143">-   SHA256</span></span><br /><span data-ttu-id="e8c31-144">-SHA512</span><span class="sxs-lookup"><span data-stu-id="e8c31-144">-   SHA512</span></span><br /><br /> <span data-ttu-id="e8c31-145">SHA1 varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="e8c31-145">The default value is SHA1.</span></span> <span data-ttu-id="e8c31-146">Bu öznitelik türünde <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="e8c31-146">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e8c31-147">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e8c31-147">Child Elements</span></span>  
 <span data-ttu-id="e8c31-148">Yok.</span><span class="sxs-lookup"><span data-stu-id="e8c31-148">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e8c31-149">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e8c31-149">Parent Elements</span></span>  
  
|<span data-ttu-id="e8c31-150">Öğe</span><span class="sxs-lookup"><span data-stu-id="e8c31-150">Element</span></span>|<span data-ttu-id="e8c31-151">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e8c31-151">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e8c31-152">\<msmqIntegration ></span><span class="sxs-lookup"><span data-stu-id="e8c31-152">\<msmqIntegration></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegration.md)|<span data-ttu-id="e8c31-153">Message Queuing (MSMQ) gönderen veya alıcı ile etkileşim için gerekli ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="e8c31-153">Specifies settings required for interaction with a Message Queuing (MSMQ) sender or receiver.</span></span>|  
|[<span data-ttu-id="e8c31-154">\<msmqTransport ></span><span class="sxs-lookup"><span data-stu-id="e8c31-154">\<msmqTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqtransport.md)|<span data-ttu-id="e8c31-155">Yerel MSMQ protokolünü kullanan bir Windows Communication Foundation (WCF) hizmetini queuing iletişimi özelliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e8c31-155">Specifies the queuing communication properties for a Windows Communication Foundation (WCF) service that uses the native MSMQ protocol.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e8c31-156">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e8c31-156">Remarks</span></span>  
 <span data-ttu-id="e8c31-157">Taşıma güvenliği hakkında daha fazla bilgi için bkz: [taşıma güvenliği](../../../../../docs/framework/wcf/feature-details/transport-security.md).</span><span class="sxs-lookup"><span data-stu-id="e8c31-157">For more information on transport security, see [Transport Security](../../../../../docs/framework/wcf/feature-details/transport-security.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8c31-158">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e8c31-158">See Also</span></span>  
 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>  
 <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="e8c31-159">Wcf'de kuyruklar</span><span class="sxs-lookup"><span data-stu-id="e8c31-159">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [<span data-ttu-id="e8c31-160">Taşımalar</span><span class="sxs-lookup"><span data-stu-id="e8c31-160">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="e8c31-161">Taşıma seçme</span><span class="sxs-lookup"><span data-stu-id="e8c31-161">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [<span data-ttu-id="e8c31-162">Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="e8c31-162">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="e8c31-163">Bağlamaları genişletme</span><span class="sxs-lookup"><span data-stu-id="e8c31-163">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="e8c31-164">Özel bağlamalar</span><span class="sxs-lookup"><span data-stu-id="e8c31-164">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="e8c31-165">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="e8c31-165">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="e8c31-166">Taşıma güvenliği</span><span class="sxs-lookup"><span data-stu-id="e8c31-166">Transport Security</span></span>](../../../../../docs/framework/wcf/feature-details/transport-security.md)

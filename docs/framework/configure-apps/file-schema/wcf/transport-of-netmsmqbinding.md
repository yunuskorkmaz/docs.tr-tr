---
title: "&lt;netMsmqBinding&gt; &lt;taşıma&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 72e1b338-39f0-4af1-a5d9-7a2fb79f6a0b
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 611d6730695c2e353782d11cb74d391107c02c35
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="lttransportgt-of-ltnetmsmqbindinggt"></a><span data-ttu-id="bca59-102">&lt;netMsmqBinding&gt; &lt;taşıma&gt;</span><span class="sxs-lookup"><span data-stu-id="bca59-102">&lt;transport&gt; of &lt;netMsmqBinding&gt;</span></span>
<span data-ttu-id="bca59-103">Taşıma güvenlik ayarları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bca59-103">Defines the transport security settings.</span></span>  
  
 <span data-ttu-id="bca59-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="bca59-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="bca59-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="bca59-105">\<bindings></span></span>  
<span data-ttu-id="bca59-106">\<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="bca59-106">\<netMsmqBinding></span></span>  
<span data-ttu-id="bca59-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="bca59-107">\<binding></span></span>  
<span data-ttu-id="bca59-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="bca59-108">\<security></span></span>  
<span data-ttu-id="bca59-109">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="bca59-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bca59-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bca59-110">Syntax</span></span>  
  
```xml  
<netMsmqBinding>  
    <binding>  
    <security>  
         <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"  
            msmqEncryptionAlgorithm="RC4Stream/AES"  
            msmqProtectionLevel="None/Sign/EncryptAndSign"  
            msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />  
    </security>  
   </binding>  
</netMsmqBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bca59-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bca59-111">Attributes and Elements</span></span>  
 <span data-ttu-id="bca59-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bca59-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bca59-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bca59-113">Attributes</span></span>  
  
|<span data-ttu-id="bca59-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="bca59-114">Attribute</span></span>|<span data-ttu-id="bca59-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bca59-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bca59-116">msmqAuthenticationMode</span><span class="sxs-lookup"><span data-stu-id="bca59-116">msmqAuthenticationMode</span></span>|<span data-ttu-id="bca59-117">İletinin MSMQ taşıma tarafından nasıl doğrulanmış gerekir belirtir.</span><span class="sxs-lookup"><span data-stu-id="bca59-117">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="bca59-118">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="bca59-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="bca59-119">-Hiçbiri: Kimlik doğrulaması yok.</span><span class="sxs-lookup"><span data-stu-id="bca59-119">-   None: No authentication.</span></span><br /><span data-ttu-id="bca59-120">-WindowsDomain: İleti ile ilişkili güvenlik tanımlayıcısı X.509 sertifikası almak için Active Directory kimlik doğrulama mekanizması kullanır.</span><span class="sxs-lookup"><span data-stu-id="bca59-120">-   WindowsDomain: The authentication mechanism uses Active Directory to retrieve the X.509 certificate for the security identifier associated with the message.</span></span> <span data-ttu-id="bca59-121">Bu, daha sonra kullanıcı emin olmak için ACL sıranın sıra için yazma iznine sahip denetlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bca59-121">This is then used to check the ACL of the queue to ensure the user has write permission for the queue.</span></span><br /><span data-ttu-id="bca59-122">-Sertifika: Kanal sertifikayı sertifika deposundan alır.</span><span class="sxs-lookup"><span data-stu-id="bca59-122">-   Certificate: The channel retrieves the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="bca59-123">Varsayılan, `WindowsDomain` değeridir.</span><span class="sxs-lookup"><span data-stu-id="bca59-123">The default is `WindowsDomain`.</span></span><br /><br /> <span data-ttu-id="bca59-124">Bu öznitelik ayarlanırsa `None`, `msmqProtectionLevel` özniteliği de ayarlanmalıdır `None`.</span><span class="sxs-lookup"><span data-stu-id="bca59-124">If this attribute is set to `None`, the `msmqProtectionLevel` attribute must also be set to `None`.</span></span> <span data-ttu-id="bca59-125">Bu öznitelik türünde<xref:System.ServiceModel.MsmqAuthenticationMode></span><span class="sxs-lookup"><span data-stu-id="bca59-125">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode></span></span>|  
|<span data-ttu-id="bca59-126">msmqEncryptionAlgorithm</span><span class="sxs-lookup"><span data-stu-id="bca59-126">msmqEncryptionAlgorithm</span></span>|<span data-ttu-id="bca59-127">İleti şifreleme hattaki iletileri ileti sırası yöneticileri arasında aktarırken kullanılacak algoritmayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="bca59-127">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="bca59-128">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="bca59-128">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="bca59-129">-RC4Stream</span><span class="sxs-lookup"><span data-stu-id="bca59-129">-   RC4Stream</span></span><br /><span data-ttu-id="bca59-130">-   AES</span><span class="sxs-lookup"><span data-stu-id="bca59-130">-   AES</span></span><br /><span data-ttu-id="bca59-131">-Varsayılan değer `RC4Stream`.</span><span class="sxs-lookup"><span data-stu-id="bca59-131">-   The default value is `RC4Stream`.</span></span> <span data-ttu-id="bca59-132">Bu öznitelik türünde <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="bca59-132">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|<span data-ttu-id="bca59-133">msmqProtectionLevel</span><span class="sxs-lookup"><span data-stu-id="bca59-133">msmqProtectionLevel</span></span>|<span data-ttu-id="bca59-134">MSMQ taşıma düzeyinde şekilde iletileri güvenli hale getirilen belirtir.</span><span class="sxs-lookup"><span data-stu-id="bca59-134">Specifies the way messages are secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="bca59-135">İleti bütünlüğü ve takası ileti bütünlüğü, oturum while ve şifreleme sağlar şifreleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="bca59-135">Encryption ensures message integrity, while sign and encrypt ensures both message integrity and non-repudiation.</span></span> <span data-ttu-id="bca59-136">Diğer bir deyişle, gerçekten gönderenden gelen ileti ve gönderenin kim kendisinin gerçekleştirilmesine söyler.</span><span class="sxs-lookup"><span data-stu-id="bca59-136">That is, the message indeed came from the sender and the sender is who he says he is.</span></span> <span data-ttu-id="bca59-137">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="bca59-137">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="bca59-138">-Hiçbiri: Koruma yok.</span><span class="sxs-lookup"><span data-stu-id="bca59-138">-   None: No protection.</span></span><br /><span data-ttu-id="bca59-139">-Oturum: İletileri imzalanmıştır.</span><span class="sxs-lookup"><span data-stu-id="bca59-139">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="bca59-140">-Da EncryptAndSign: İletileri şifrelenmiş ve imzalanmış.</span><span class="sxs-lookup"><span data-stu-id="bca59-140">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><span data-ttu-id="bca59-141">-Varsayılan `Sign`.</span><span class="sxs-lookup"><span data-stu-id="bca59-141">-   The default is `Sign`.</span></span>|  
|<span data-ttu-id="bca59-142">msmqSecureHashAlgorithm</span><span class="sxs-lookup"><span data-stu-id="bca59-142">msmqSecureHashAlgorithm</span></span>|<span data-ttu-id="bca59-143">İleti özeti bilgi işlem için kullanılacak karma algoritmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="bca59-143">Specifies the hash algorithm to be used for computing the message digest.</span></span> <span data-ttu-id="bca59-144">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="bca59-144">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="bca59-145">-   MD5</span><span class="sxs-lookup"><span data-stu-id="bca59-145">-   MD5</span></span><br /><span data-ttu-id="bca59-146">-   SHA1</span><span class="sxs-lookup"><span data-stu-id="bca59-146">-   SHA1</span></span><br /><span data-ttu-id="bca59-147">-   SHA256</span><span class="sxs-lookup"><span data-stu-id="bca59-147">-   SHA256</span></span><br /><span data-ttu-id="bca59-148">-   SHA512</span><span class="sxs-lookup"><span data-stu-id="bca59-148">-   SHA512</span></span><br /><br /> <span data-ttu-id="bca59-149">Varsayılan, `SHA1` değeridir.</span><span class="sxs-lookup"><span data-stu-id="bca59-149">The default is `SHA1`.</span></span> <span data-ttu-id="bca59-150">Bu öznitelik türünde <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="bca59-150">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bca59-151">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bca59-151">Child Elements</span></span>  
 <span data-ttu-id="bca59-152">Yok.</span><span class="sxs-lookup"><span data-stu-id="bca59-152">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bca59-153">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bca59-153">Parent Elements</span></span>  
  
|<span data-ttu-id="bca59-154">Öğe</span><span class="sxs-lookup"><span data-stu-id="bca59-154">Element</span></span>|<span data-ttu-id="bca59-155">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bca59-155">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bca59-156">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="bca59-156">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|<span data-ttu-id="bca59-157">Sıraya alınan taşımaları taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bca59-157">Defines the transport security settings for queued transports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bca59-158">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bca59-158">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>  
 <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A>  
 <xref:System.ServiceModel.MsmqTransportSecurity>  
 [<span data-ttu-id="bca59-159">WCF'de Kuyruklar</span><span class="sxs-lookup"><span data-stu-id="bca59-159">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [<span data-ttu-id="bca59-160">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="bca59-160">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="bca59-161">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="bca59-161">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="bca59-162">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="bca59-162">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="bca59-163">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="bca59-163">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="bca59-164">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="bca59-164">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)

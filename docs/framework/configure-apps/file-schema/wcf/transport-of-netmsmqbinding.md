---
title: <transport> / <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 72e1b338-39f0-4af1-a5d9-7a2fb79f6a0b
ms.openlocfilehash: ec726c4b39fedbf63a7ecc9e685a86367609fa43
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59085018"
---
# <a name="transport-of-netmsmqbinding"></a><span data-ttu-id="d5e58-102">\<Aktarım >, \<netMsmqBinding ></span><span class="sxs-lookup"><span data-stu-id="d5e58-102">\<transport> of \<netMsmqBinding></span></span>
<span data-ttu-id="d5e58-103">Taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d5e58-103">Defines the transport security settings.</span></span>  
  
 <span data-ttu-id="d5e58-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d5e58-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d5e58-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="d5e58-105">\<bindings></span></span>  
<span data-ttu-id="d5e58-106">\<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="d5e58-106">\<netMsmqBinding></span></span>  
<span data-ttu-id="d5e58-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="d5e58-107">\<binding></span></span>  
<span data-ttu-id="d5e58-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="d5e58-108">\<security></span></span>  
<span data-ttu-id="d5e58-109">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="d5e58-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5e58-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d5e58-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d5e58-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d5e58-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d5e58-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d5e58-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d5e58-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d5e58-113">Attributes</span></span>  
  
|<span data-ttu-id="d5e58-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d5e58-114">Attribute</span></span>|<span data-ttu-id="d5e58-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d5e58-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d5e58-116">msmqAuthenticationMode</span><span class="sxs-lookup"><span data-stu-id="d5e58-116">msmqAuthenticationMode</span></span>|<span data-ttu-id="d5e58-117">İletinin MSMQ taşıma tarafından nasıl doğrulacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d5e58-117">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="d5e58-118">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="d5e58-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="d5e58-119">-Yok: Kimlik doğrulaması yok.</span><span class="sxs-lookup"><span data-stu-id="d5e58-119">-   None: No authentication.</span></span><br /><span data-ttu-id="d5e58-120">-   WindowsDomain: İletiyle ilişkili güvenlik kimliği için X.509 sertifikası almak için Active Directory kimlik doğrulama mekanizması kullanır.</span><span class="sxs-lookup"><span data-stu-id="d5e58-120">-   WindowsDomain: The authentication mechanism uses Active Directory to retrieve the X.509 certificate for the security identifier associated with the message.</span></span> <span data-ttu-id="d5e58-121">Bu, ardından kullanıcı emin olmak için ACL kuyruğun sıra için yazma iznine sahip olmadığını denetlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d5e58-121">This is then used to check the ACL of the queue to ensure the user has write permission for the queue.</span></span><br /><span data-ttu-id="d5e58-122">-Sertifikası: Kanal sertifikayı sertifika deposundan alır.</span><span class="sxs-lookup"><span data-stu-id="d5e58-122">-   Certificate: The channel retrieves the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="d5e58-123">Varsayılan, `WindowsDomain` değeridir.</span><span class="sxs-lookup"><span data-stu-id="d5e58-123">The default is `WindowsDomain`.</span></span><br /><br /> <span data-ttu-id="d5e58-124">Bu öznitelik ayarlanırsa `None`, `msmqProtectionLevel` özniteliği de ayarlanması gerekir `None`.</span><span class="sxs-lookup"><span data-stu-id="d5e58-124">If this attribute is set to `None`, the `msmqProtectionLevel` attribute must also be set to `None`.</span></span> <span data-ttu-id="d5e58-125">Bu öznitelik türünde <xref:System.ServiceModel.MsmqAuthenticationMode></span><span class="sxs-lookup"><span data-stu-id="d5e58-125">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode></span></span>|  
|<span data-ttu-id="d5e58-126">msmqEncryptionAlgorithm</span><span class="sxs-lookup"><span data-stu-id="d5e58-126">msmqEncryptionAlgorithm</span></span>|<span data-ttu-id="d5e58-127">Etkin ileti şifreleme için iletileri ileti sıra yöneticileri arasında transfer ederken kullanılan algoritmayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="d5e58-127">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="d5e58-128">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="d5e58-128">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="d5e58-129">-RC4Stream</span><span class="sxs-lookup"><span data-stu-id="d5e58-129">-   RC4Stream</span></span><br /><span data-ttu-id="d5e58-130">-AES</span><span class="sxs-lookup"><span data-stu-id="d5e58-130">-   AES</span></span><br /><span data-ttu-id="d5e58-131">-Varsayılan değer `RC4Stream`.</span><span class="sxs-lookup"><span data-stu-id="d5e58-131">-   The default value is `RC4Stream`.</span></span> <span data-ttu-id="d5e58-132">Bu öznitelik türünde <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="d5e58-132">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|<span data-ttu-id="d5e58-133">msmqProtectionLevel</span><span class="sxs-lookup"><span data-stu-id="d5e58-133">msmqProtectionLevel</span></span>|<span data-ttu-id="d5e58-134">MSMQ taşıma düzeyinde güvenli şekilde iletileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="d5e58-134">Specifies the way messages are secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="d5e58-135">İleti bütünlüğü hem takası ileti bütünlüğü çalışırken işaretini ve şifreleme sağlar şifreleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="d5e58-135">Encryption ensures message integrity, while sign and encrypt ensures both message integrity and non-repudiation.</span></span> <span data-ttu-id="d5e58-136">Diğer bir deyişle, ileti gönderen gerçekten geldi ve gönderen kim kendisinin kendisinin olduğunu söylüyor.</span><span class="sxs-lookup"><span data-stu-id="d5e58-136">That is, the message indeed came from the sender and the sender is who he says he is.</span></span> <span data-ttu-id="d5e58-137">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="d5e58-137">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="d5e58-138">-Yok: Koruma yok.</span><span class="sxs-lookup"><span data-stu-id="d5e58-138">-   None: No protection.</span></span><br /><span data-ttu-id="d5e58-139">-Oturum: İmzalı iletiler.</span><span class="sxs-lookup"><span data-stu-id="d5e58-139">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="d5e58-140">-   EncryptAndSign: İletileri şifrelenir ve imzalanmış.</span><span class="sxs-lookup"><span data-stu-id="d5e58-140">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><span data-ttu-id="d5e58-141">-Varsayılan `Sign`.</span><span class="sxs-lookup"><span data-stu-id="d5e58-141">-   The default is `Sign`.</span></span>|  
|<span data-ttu-id="d5e58-142">msmqSecureHashAlgorithm</span><span class="sxs-lookup"><span data-stu-id="d5e58-142">msmqSecureHashAlgorithm</span></span>|<span data-ttu-id="d5e58-143">İleti özeti bilgi işlem için kullanılan karma algoritmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d5e58-143">Specifies the hash algorithm to be used for computing the message digest.</span></span> <span data-ttu-id="d5e58-144">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="d5e58-144">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="d5e58-145">-MD5</span><span class="sxs-lookup"><span data-stu-id="d5e58-145">-   MD5</span></span><br /><span data-ttu-id="d5e58-146">-   SHA1</span><span class="sxs-lookup"><span data-stu-id="d5e58-146">-   SHA1</span></span><br /><span data-ttu-id="d5e58-147">-   SHA256</span><span class="sxs-lookup"><span data-stu-id="d5e58-147">-   SHA256</span></span><br /><span data-ttu-id="d5e58-148">-   SHA512</span><span class="sxs-lookup"><span data-stu-id="d5e58-148">-   SHA512</span></span><br /><br /> <span data-ttu-id="d5e58-149">Varsayılan, `SHA1` değeridir.</span><span class="sxs-lookup"><span data-stu-id="d5e58-149">The default is `SHA1`.</span></span> <span data-ttu-id="d5e58-150">Bu öznitelik türünde <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="d5e58-150">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span><br><span data-ttu-id="d5e58-151">Çakışma sorunları nedeniyle MD5 ve SHA1, SHA256 veya iyi Microsoft önerir.</span><span class="sxs-lookup"><span data-stu-id="d5e58-151">Due to collision problems with MD5 and SHA1, Microsoft recommends SHA256 or better.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d5e58-152">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d5e58-152">Child Elements</span></span>  
 <span data-ttu-id="d5e58-153">Yok.</span><span class="sxs-lookup"><span data-stu-id="d5e58-153">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d5e58-154">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d5e58-154">Parent Elements</span></span>  
  
|<span data-ttu-id="d5e58-155">Öğe</span><span class="sxs-lookup"><span data-stu-id="d5e58-155">Element</span></span>|<span data-ttu-id="d5e58-156">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d5e58-156">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d5e58-157">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="d5e58-157">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|<span data-ttu-id="d5e58-158">Sıraya alınan taşımalar için taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d5e58-158">Defines the transport security settings for queued transports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d5e58-159">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d5e58-159">See also</span></span>

- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [<span data-ttu-id="d5e58-160">WCF'de Kuyruklar</span><span class="sxs-lookup"><span data-stu-id="d5e58-160">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="d5e58-161">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="d5e58-161">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="d5e58-162">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="d5e58-162">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="d5e58-163">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d5e58-163">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="d5e58-164">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="d5e58-164">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="d5e58-165">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="d5e58-165">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)

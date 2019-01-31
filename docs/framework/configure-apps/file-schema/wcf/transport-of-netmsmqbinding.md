---
title: <transport> , <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 72e1b338-39f0-4af1-a5d9-7a2fb79f6a0b
ms.openlocfilehash: c82a786fe8e4a2b2e3243db007f4f705d9fbd79a
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55277153"
---
# <a name="transport-of-netmsmqbinding"></a><span data-ttu-id="3fe9c-102">\<Aktarım >, \<netMsmqBinding ></span><span class="sxs-lookup"><span data-stu-id="3fe9c-102">\<transport> of \<netMsmqBinding></span></span>
<span data-ttu-id="3fe9c-103">Taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3fe9c-103">Defines the transport security settings.</span></span>  
  
 <span data-ttu-id="3fe9c-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3fe9c-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="3fe9c-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="3fe9c-105">\<bindings></span></span>  
<span data-ttu-id="3fe9c-106">\<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="3fe9c-106">\<netMsmqBinding></span></span>  
<span data-ttu-id="3fe9c-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="3fe9c-107">\<binding></span></span>  
<span data-ttu-id="3fe9c-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="3fe9c-108">\<security></span></span>  
<span data-ttu-id="3fe9c-109">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="3fe9c-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fe9c-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3fe9c-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3fe9c-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3fe9c-111">Attributes and Elements</span></span>  
 <span data-ttu-id="3fe9c-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3fe9c-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3fe9c-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3fe9c-113">Attributes</span></span>  
  
|<span data-ttu-id="3fe9c-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3fe9c-114">Attribute</span></span>|<span data-ttu-id="3fe9c-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3fe9c-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3fe9c-116">msmqAuthenticationMode</span><span class="sxs-lookup"><span data-stu-id="3fe9c-116">msmqAuthenticationMode</span></span>|<span data-ttu-id="3fe9c-117">İletinin MSMQ taşıma tarafından nasıl doğrulacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3fe9c-117">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="3fe9c-118">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="3fe9c-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="3fe9c-119">-Yok: Kimlik doğrulaması yok.</span><span class="sxs-lookup"><span data-stu-id="3fe9c-119">-   None: No authentication.</span></span><br /><span data-ttu-id="3fe9c-120">-   WindowsDomain: İletiyle ilişkili güvenlik kimliği için X.509 sertifikası almak için Active Directory kimlik doğrulama mekanizması kullanır.</span><span class="sxs-lookup"><span data-stu-id="3fe9c-120">-   WindowsDomain: The authentication mechanism uses Active Directory to retrieve the X.509 certificate for the security identifier associated with the message.</span></span> <span data-ttu-id="3fe9c-121">Bu, ardından kullanıcı emin olmak için ACL kuyruğun sıra için yazma iznine sahip olmadığını denetlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3fe9c-121">This is then used to check the ACL of the queue to ensure the user has write permission for the queue.</span></span><br /><span data-ttu-id="3fe9c-122">-Sertifikası: Kanal sertifikayı sertifika deposundan alır.</span><span class="sxs-lookup"><span data-stu-id="3fe9c-122">-   Certificate: The channel retrieves the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="3fe9c-123">Varsayılan, `WindowsDomain` değeridir.</span><span class="sxs-lookup"><span data-stu-id="3fe9c-123">The default is `WindowsDomain`.</span></span><br /><br /> <span data-ttu-id="3fe9c-124">Bu öznitelik ayarlanırsa `None`, `msmqProtectionLevel` özniteliği de ayarlanması gerekir `None`.</span><span class="sxs-lookup"><span data-stu-id="3fe9c-124">If this attribute is set to `None`, the `msmqProtectionLevel` attribute must also be set to `None`.</span></span> <span data-ttu-id="3fe9c-125">Bu öznitelik türünde <xref:System.ServiceModel.MsmqAuthenticationMode></span><span class="sxs-lookup"><span data-stu-id="3fe9c-125">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode></span></span>|  
|<span data-ttu-id="3fe9c-126">msmqEncryptionAlgorithm</span><span class="sxs-lookup"><span data-stu-id="3fe9c-126">msmqEncryptionAlgorithm</span></span>|<span data-ttu-id="3fe9c-127">Etkin ileti şifreleme için iletileri ileti sıra yöneticileri arasında transfer ederken kullanılan algoritmayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="3fe9c-127">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="3fe9c-128">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="3fe9c-128">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="3fe9c-129">-RC4Stream</span><span class="sxs-lookup"><span data-stu-id="3fe9c-129">-   RC4Stream</span></span><br /><span data-ttu-id="3fe9c-130">-AES</span><span class="sxs-lookup"><span data-stu-id="3fe9c-130">-   AES</span></span><br /><span data-ttu-id="3fe9c-131">-Varsayılan değer `RC4Stream`.</span><span class="sxs-lookup"><span data-stu-id="3fe9c-131">-   The default value is `RC4Stream`.</span></span> <span data-ttu-id="3fe9c-132">Bu öznitelik türünde <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="3fe9c-132">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|<span data-ttu-id="3fe9c-133">msmqProtectionLevel</span><span class="sxs-lookup"><span data-stu-id="3fe9c-133">msmqProtectionLevel</span></span>|<span data-ttu-id="3fe9c-134">MSMQ taşıma düzeyinde güvenli şekilde iletileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="3fe9c-134">Specifies the way messages are secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="3fe9c-135">İleti bütünlüğü hem takası ileti bütünlüğü çalışırken işaretini ve şifreleme sağlar şifreleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="3fe9c-135">Encryption ensures message integrity, while sign and encrypt ensures both message integrity and non-repudiation.</span></span> <span data-ttu-id="3fe9c-136">Diğer bir deyişle, ileti gönderen gerçekten geldi ve gönderen kim kendisinin kendisinin olduğunu söylüyor.</span><span class="sxs-lookup"><span data-stu-id="3fe9c-136">That is, the message indeed came from the sender and the sender is who he says he is.</span></span> <span data-ttu-id="3fe9c-137">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="3fe9c-137">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="3fe9c-138">-Yok: Koruma yok.</span><span class="sxs-lookup"><span data-stu-id="3fe9c-138">-   None: No protection.</span></span><br /><span data-ttu-id="3fe9c-139">-Oturum: İmzalı iletiler.</span><span class="sxs-lookup"><span data-stu-id="3fe9c-139">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="3fe9c-140">-   EncryptAndSign: İletileri şifrelenir ve imzalanmış.</span><span class="sxs-lookup"><span data-stu-id="3fe9c-140">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><span data-ttu-id="3fe9c-141">-Varsayılan `Sign`.</span><span class="sxs-lookup"><span data-stu-id="3fe9c-141">-   The default is `Sign`.</span></span>|  
|<span data-ttu-id="3fe9c-142">msmqSecureHashAlgorithm</span><span class="sxs-lookup"><span data-stu-id="3fe9c-142">msmqSecureHashAlgorithm</span></span>|<span data-ttu-id="3fe9c-143">İleti özeti bilgi işlem için kullanılan karma algoritmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3fe9c-143">Specifies the hash algorithm to be used for computing the message digest.</span></span> <span data-ttu-id="3fe9c-144">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="3fe9c-144">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="3fe9c-145">-MD5</span><span class="sxs-lookup"><span data-stu-id="3fe9c-145">-   MD5</span></span><br /><span data-ttu-id="3fe9c-146">-   SHA1</span><span class="sxs-lookup"><span data-stu-id="3fe9c-146">-   SHA1</span></span><br /><span data-ttu-id="3fe9c-147">-   SHA256</span><span class="sxs-lookup"><span data-stu-id="3fe9c-147">-   SHA256</span></span><br /><span data-ttu-id="3fe9c-148">-   SHA512</span><span class="sxs-lookup"><span data-stu-id="3fe9c-148">-   SHA512</span></span><br /><br /> <span data-ttu-id="3fe9c-149">Varsayılan, `SHA1` değeridir.</span><span class="sxs-lookup"><span data-stu-id="3fe9c-149">The default is `SHA1`.</span></span> <span data-ttu-id="3fe9c-150">Bu öznitelik türünde <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="3fe9c-150">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3fe9c-151">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3fe9c-151">Child Elements</span></span>  
 <span data-ttu-id="3fe9c-152">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="3fe9c-152">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3fe9c-153">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3fe9c-153">Parent Elements</span></span>  
  
|<span data-ttu-id="3fe9c-154">Öğe</span><span class="sxs-lookup"><span data-stu-id="3fe9c-154">Element</span></span>|<span data-ttu-id="3fe9c-155">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3fe9c-155">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3fe9c-156">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="3fe9c-156">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|<span data-ttu-id="3fe9c-157">Sıraya alınan taşımalar için taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3fe9c-157">Defines the transport security settings for queued transports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3fe9c-158">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3fe9c-158">See also</span></span>
- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [<span data-ttu-id="3fe9c-159">WCF'de Kuyruklar</span><span class="sxs-lookup"><span data-stu-id="3fe9c-159">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="3fe9c-160">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="3fe9c-160">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="3fe9c-161">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="3fe9c-161">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="3fe9c-162">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="3fe9c-162">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="3fe9c-163">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="3fe9c-163">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="3fe9c-164">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="3fe9c-164">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)

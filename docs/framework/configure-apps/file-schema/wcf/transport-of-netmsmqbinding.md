---
title: <transport> / <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 72e1b338-39f0-4af1-a5d9-7a2fb79f6a0b
ms.openlocfilehash: ede4103f9c8f2f73ac34036fe7a58242e32350e0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934686"
---
# <a name="transport-of-netmsmqbinding"></a><span data-ttu-id="f5474-102">\<\<NetMsmqBinding > taşıma ></span><span class="sxs-lookup"><span data-stu-id="f5474-102">\<transport> of \<netMsmqBinding></span></span>
<span data-ttu-id="f5474-103">Taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f5474-103">Defines the transport security settings.</span></span>  
  
 <span data-ttu-id="f5474-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f5474-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f5474-105">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="f5474-105">\<bindings></span></span>  
<span data-ttu-id="f5474-106">\<netMsmqBinding ></span><span class="sxs-lookup"><span data-stu-id="f5474-106">\<netMsmqBinding></span></span>  
<span data-ttu-id="f5474-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="f5474-107">\<binding></span></span>  
<span data-ttu-id="f5474-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="f5474-108">\<security></span></span>  
<span data-ttu-id="f5474-109">\<Taşıma ></span><span class="sxs-lookup"><span data-stu-id="f5474-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5474-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f5474-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f5474-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f5474-111">Attributes and Elements</span></span>  
 <span data-ttu-id="f5474-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f5474-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f5474-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f5474-113">Attributes</span></span>  
  
|<span data-ttu-id="f5474-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f5474-114">Attribute</span></span>|<span data-ttu-id="f5474-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f5474-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f5474-116">msmqAuthenticationMode</span><span class="sxs-lookup"><span data-stu-id="f5474-116">msmqAuthenticationMode</span></span>|<span data-ttu-id="f5474-117">İletinin MSMQ taşıması tarafından nasıl doğrulanabilmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f5474-117">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="f5474-118">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f5474-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="f5474-119">Seçim Kimlik doğrulaması yok.</span><span class="sxs-lookup"><span data-stu-id="f5474-119">-   None: No authentication.</span></span><br /><span data-ttu-id="f5474-120">-WindowsDomain: Kimlik doğrulama mekanizması, iletiyle ilişkili güvenlik tanımlayıcısı için X. 509.440 sertifikasını almak üzere Active Directory kullanır.</span><span class="sxs-lookup"><span data-stu-id="f5474-120">-   WindowsDomain: The authentication mechanism uses Active Directory to retrieve the X.509 certificate for the security identifier associated with the message.</span></span> <span data-ttu-id="f5474-121">Bu daha sonra kullanıcının sıra için yazma iznine sahip olduğundan emin olmak üzere kuyruğun ACL 'sini denetlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f5474-121">This is then used to check the ACL of the queue to ensure the user has write permission for the queue.</span></span><br /><span data-ttu-id="f5474-122">Sertifika Kanal, sertifika deposundan sertifikayı alır.</span><span class="sxs-lookup"><span data-stu-id="f5474-122">-   Certificate: The channel retrieves the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="f5474-123">Varsayılan, `WindowsDomain` değeridir.</span><span class="sxs-lookup"><span data-stu-id="f5474-123">The default is `WindowsDomain`.</span></span><br /><br /> <span data-ttu-id="f5474-124">Bu öznitelik olarak `None`ayarlandıysa `msmqProtectionLevel` , özniteliği de olarak `None`ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f5474-124">If this attribute is set to `None`, the `msmqProtectionLevel` attribute must also be set to `None`.</span></span> <span data-ttu-id="f5474-125">Bu öznitelik türü<xref:System.ServiceModel.MsmqAuthenticationMode></span><span class="sxs-lookup"><span data-stu-id="f5474-125">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode></span></span>|  
|<span data-ttu-id="f5474-126">Msmqencryptionalgoritması</span><span class="sxs-lookup"><span data-stu-id="f5474-126">msmqEncryptionAlgorithm</span></span>|<span data-ttu-id="f5474-127">Message Queue yöneticileri arasında ileti aktarılırken ileti şifreleme için kullanılacak algoritmayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="f5474-127">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="f5474-128">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f5474-128">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="f5474-129">- RC4Stream</span><span class="sxs-lookup"><span data-stu-id="f5474-129">-   RC4Stream</span></span><br /><span data-ttu-id="f5474-130">-AES</span><span class="sxs-lookup"><span data-stu-id="f5474-130">-   AES</span></span><br /><span data-ttu-id="f5474-131">-Varsayılan değer `RC4Stream`.</span><span class="sxs-lookup"><span data-stu-id="f5474-131">-   The default value is `RC4Stream`.</span></span> <span data-ttu-id="f5474-132">Bu öznitelik türü <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="f5474-132">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|<span data-ttu-id="f5474-133">msmqProtectionLevel</span><span class="sxs-lookup"><span data-stu-id="f5474-133">msmqProtectionLevel</span></span>|<span data-ttu-id="f5474-134">MSMQ taşıması düzeyinde iletilerin güvenli hale getirilme yöntemini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f5474-134">Specifies the way messages are secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="f5474-135">Şifreleme ileti bütünlüğünü sağlar, oturum açma ve şifreleme hem ileti bütünlüğünü hem de Red olmamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="f5474-135">Encryption ensures message integrity, while sign and encrypt ensures both message integrity and non-repudiation.</span></span> <span data-ttu-id="f5474-136">Diğer bir deyişle, ileti gerçekten gönderenden geldi ve gönderen kim olduğunu söylüyor.</span><span class="sxs-lookup"><span data-stu-id="f5474-136">That is, the message indeed came from the sender and the sender is who he says he is.</span></span> <span data-ttu-id="f5474-137">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f5474-137">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="f5474-138">Seçim Koruma yok.</span><span class="sxs-lookup"><span data-stu-id="f5474-138">-   None: No protection.</span></span><br /><span data-ttu-id="f5474-139">İmzalayabilirsiniz İletiler imzalanır.</span><span class="sxs-lookup"><span data-stu-id="f5474-139">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="f5474-140">EncryptAndSign özelliğini İletiler şifrelenir ve imzalanır.</span><span class="sxs-lookup"><span data-stu-id="f5474-140">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><span data-ttu-id="f5474-141">-Varsayılan `Sign`değer.</span><span class="sxs-lookup"><span data-stu-id="f5474-141">-   The default is `Sign`.</span></span>|  
|<span data-ttu-id="f5474-142">msmqSecureHashAlgorithm</span><span class="sxs-lookup"><span data-stu-id="f5474-142">msmqSecureHashAlgorithm</span></span>|<span data-ttu-id="f5474-143">İleti özetinin bilgi işlem için kullanılacak karma algoritmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f5474-143">Specifies the hash algorithm to be used for computing the message digest.</span></span> <span data-ttu-id="f5474-144">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f5474-144">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="f5474-145">-MD5</span><span class="sxs-lookup"><span data-stu-id="f5474-145">-   MD5</span></span><br /><span data-ttu-id="f5474-146">-   SHA1</span><span class="sxs-lookup"><span data-stu-id="f5474-146">-   SHA1</span></span><br /><span data-ttu-id="f5474-147">-   SHA256</span><span class="sxs-lookup"><span data-stu-id="f5474-147">-   SHA256</span></span><br /><span data-ttu-id="f5474-148">-   SHA512</span><span class="sxs-lookup"><span data-stu-id="f5474-148">-   SHA512</span></span><br /><br /> <span data-ttu-id="f5474-149">Varsayılan, `SHA1` değeridir.</span><span class="sxs-lookup"><span data-stu-id="f5474-149">The default is `SHA1`.</span></span> <span data-ttu-id="f5474-150">Bu öznitelik türü <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="f5474-150">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span><br><span data-ttu-id="f5474-151">MD5 ve SHA1 ile ilgili çarpışma sorunları nedeniyle, Microsoft SHA256 veya daha iyi bir performans öneriyor.</span><span class="sxs-lookup"><span data-stu-id="f5474-151">Due to collision problems with MD5 and SHA1, Microsoft recommends SHA256 or better.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f5474-152">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f5474-152">Child Elements</span></span>  
 <span data-ttu-id="f5474-153">Yok.</span><span class="sxs-lookup"><span data-stu-id="f5474-153">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f5474-154">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f5474-154">Parent Elements</span></span>  
  
|<span data-ttu-id="f5474-155">Öğe</span><span class="sxs-lookup"><span data-stu-id="f5474-155">Element</span></span>|<span data-ttu-id="f5474-156">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f5474-156">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f5474-157">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="f5474-157">\<security></span></span>](security-of-netmsmqbinding.md)|<span data-ttu-id="f5474-158">Sıraya alınan taşıtlar için taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f5474-158">Defines the transport security settings for queued transports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f5474-159">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f5474-159">See also</span></span>

- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [<span data-ttu-id="f5474-160">WCF'de Kuyruklar</span><span class="sxs-lookup"><span data-stu-id="f5474-160">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="f5474-161">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="f5474-161">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="f5474-162">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="f5474-162">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f5474-163">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f5474-163">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="f5474-164">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="f5474-164">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="f5474-165">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="f5474-165">\<binding></span></span>](../../../misc/binding.md)

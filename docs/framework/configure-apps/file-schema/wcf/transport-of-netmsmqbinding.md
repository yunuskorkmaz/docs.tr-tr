---
description: 'Hakkında daha fazla bilgi <transport> edinin: <netMsmqBinding>'
title: <transport> / <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 72e1b338-39f0-4af1-a5d9-7a2fb79f6a0b
ms.openlocfilehash: 04768f259629277abd758d102f3873bb28f16514
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99773504"
---
# <a name="transport-of-netmsmqbinding"></a><span data-ttu-id="79a2d-103">\<transport> / \<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="79a2d-103">\<transport> of \<netMsmqBinding></span></span>

<span data-ttu-id="79a2d-104">Taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="79a2d-104">Defines the transport security settings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netMsmqBinding>**](netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="79a2d-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="79a2d-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="79a2d-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="79a2d-106">Attributes and Elements</span></span>  

 <span data-ttu-id="79a2d-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="79a2d-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="79a2d-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="79a2d-108">Attributes</span></span>  
  
|<span data-ttu-id="79a2d-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="79a2d-109">Attribute</span></span>|<span data-ttu-id="79a2d-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="79a2d-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="79a2d-111">msmqAuthenticationMode</span><span class="sxs-lookup"><span data-stu-id="79a2d-111">msmqAuthenticationMode</span></span>|<span data-ttu-id="79a2d-112">İletinin MSMQ taşıması tarafından nasıl doğrulanabilmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="79a2d-112">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="79a2d-113">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="79a2d-113">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="79a2d-114">-None: kimlik doğrulaması yok.</span><span class="sxs-lookup"><span data-stu-id="79a2d-114">-   None: No authentication.</span></span><br /><span data-ttu-id="79a2d-115">-WindowsDomain: kimlik doğrulama mekanizması, iletiyle ilişkili güvenlik tanımlayıcısı için X. 509.440 sertifikasını almak üzere Active Directory kullanır.</span><span class="sxs-lookup"><span data-stu-id="79a2d-115">-   WindowsDomain: The authentication mechanism uses Active Directory to retrieve the X.509 certificate for the security identifier associated with the message.</span></span> <span data-ttu-id="79a2d-116">Bu daha sonra kullanıcının sıra için yazma iznine sahip olduğundan emin olmak üzere kuyruğun ACL 'sini denetlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="79a2d-116">This is then used to check the ACL of the queue to ensure the user has write permission for the queue.</span></span><br /><span data-ttu-id="79a2d-117">-Sertifika: Kanal sertifikayı sertifika deposundan alır.</span><span class="sxs-lookup"><span data-stu-id="79a2d-117">-   Certificate: The channel retrieves the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="79a2d-118">Varsayılan değer: `WindowsDomain`.</span><span class="sxs-lookup"><span data-stu-id="79a2d-118">The default is `WindowsDomain`.</span></span><br /><br /> <span data-ttu-id="79a2d-119">Bu öznitelik olarak ayarlandıysa `None` , `msmqProtectionLevel` özniteliği de olarak ayarlanmalıdır `None` .</span><span class="sxs-lookup"><span data-stu-id="79a2d-119">If this attribute is set to `None`, the `msmqProtectionLevel` attribute must also be set to `None`.</span></span> <span data-ttu-id="79a2d-120">Bu öznitelik türü <xref:System.ServiceModel.MsmqAuthenticationMode></span><span class="sxs-lookup"><span data-stu-id="79a2d-120">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode></span></span>|  
|<span data-ttu-id="79a2d-121">Msmqencryptionalgoritması</span><span class="sxs-lookup"><span data-stu-id="79a2d-121">msmqEncryptionAlgorithm</span></span>|<span data-ttu-id="79a2d-122">Message Queue yöneticileri arasında ileti aktarılırken ileti şifreleme için kullanılacak algoritmayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="79a2d-122">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="79a2d-123">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="79a2d-123">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="79a2d-124">- RC4Stream</span><span class="sxs-lookup"><span data-stu-id="79a2d-124">-   RC4Stream</span></span><br /><span data-ttu-id="79a2d-125">-AES</span><span class="sxs-lookup"><span data-stu-id="79a2d-125">-   AES</span></span><br /><span data-ttu-id="79a2d-126">-Varsayılan değer `RC4Stream` .</span><span class="sxs-lookup"><span data-stu-id="79a2d-126">-   The default value is `RC4Stream`.</span></span> <span data-ttu-id="79a2d-127">Bu öznitelik türü <xref:System.ServiceModel.MsmqEncryptionAlgorithm> .</span><span class="sxs-lookup"><span data-stu-id="79a2d-127">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|<span data-ttu-id="79a2d-128">msmqProtectionLevel</span><span class="sxs-lookup"><span data-stu-id="79a2d-128">msmqProtectionLevel</span></span>|<span data-ttu-id="79a2d-129">MSMQ taşıması düzeyinde iletilerin güvenli hale getirilme yöntemini belirtir.</span><span class="sxs-lookup"><span data-stu-id="79a2d-129">Specifies the way messages are secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="79a2d-130">Şifreleme ileti bütünlüğünü sağlar, oturum açma ve şifreleme hem ileti bütünlüğünü hem de Red olmamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="79a2d-130">Encryption ensures message integrity, while sign and encrypt ensures both message integrity and non-repudiation.</span></span> <span data-ttu-id="79a2d-131">Diğer bir deyişle, ileti gerçekten gönderenden geldi ve gönderici kim olduğunu söyledikleri kişidir.</span><span class="sxs-lookup"><span data-stu-id="79a2d-131">That is, the message indeed came from the sender and the sender is who they say they are.</span></span> <span data-ttu-id="79a2d-132">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="79a2d-132">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="79a2d-133">-None: koruma yok.</span><span class="sxs-lookup"><span data-stu-id="79a2d-133">-   None: No protection.</span></span><br /><span data-ttu-id="79a2d-134">-Sign: Iletiler imzalanır.</span><span class="sxs-lookup"><span data-stu-id="79a2d-134">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="79a2d-135">-EncryptAndSign: Iletiler şifrelenir ve imzalanır.</span><span class="sxs-lookup"><span data-stu-id="79a2d-135">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><span data-ttu-id="79a2d-136">-Varsayılan değer `Sign` .</span><span class="sxs-lookup"><span data-stu-id="79a2d-136">-   The default is `Sign`.</span></span>|  
|<span data-ttu-id="79a2d-137">msmqSecureHashAlgorithm</span><span class="sxs-lookup"><span data-stu-id="79a2d-137">msmqSecureHashAlgorithm</span></span>|<span data-ttu-id="79a2d-138">İleti özetinin bilgi işlem için kullanılacak karma algoritmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="79a2d-138">Specifies the hash algorithm to be used for computing the message digest.</span></span> <span data-ttu-id="79a2d-139">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="79a2d-139">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="79a2d-140">-MD5</span><span class="sxs-lookup"><span data-stu-id="79a2d-140">-   MD5</span></span><br /><span data-ttu-id="79a2d-141">-SHA1</span><span class="sxs-lookup"><span data-stu-id="79a2d-141">-   SHA1</span></span><br /><span data-ttu-id="79a2d-142">-SHA256</span><span class="sxs-lookup"><span data-stu-id="79a2d-142">-   SHA256</span></span><br /><span data-ttu-id="79a2d-143">-SHA512 olur</span><span class="sxs-lookup"><span data-stu-id="79a2d-143">-   SHA512</span></span><br /><br /> <span data-ttu-id="79a2d-144">Varsayılan değer: `SHA1`.</span><span class="sxs-lookup"><span data-stu-id="79a2d-144">The default is `SHA1`.</span></span> <span data-ttu-id="79a2d-145">Bu öznitelik türü <xref:System.ServiceModel.MsmqSecureHashAlgorithm> .</span><span class="sxs-lookup"><span data-stu-id="79a2d-145">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span><br><span data-ttu-id="79a2d-146">MD5 ve SHA1 ile ilgili çarpışma sorunları nedeniyle, Microsoft SHA256 veya daha iyi bir performans öneriyor.</span><span class="sxs-lookup"><span data-stu-id="79a2d-146">Due to collision problems with MD5 and SHA1, Microsoft recommends SHA256 or better.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="79a2d-147">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="79a2d-147">Child Elements</span></span>  

 <span data-ttu-id="79a2d-148">Yok</span><span class="sxs-lookup"><span data-stu-id="79a2d-148">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="79a2d-149">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="79a2d-149">Parent Elements</span></span>  
  
|<span data-ttu-id="79a2d-150">Öğe</span><span class="sxs-lookup"><span data-stu-id="79a2d-150">Element</span></span>|<span data-ttu-id="79a2d-151">Açıklama</span><span class="sxs-lookup"><span data-stu-id="79a2d-151">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-netmsmqbinding.md)|<span data-ttu-id="79a2d-152">Sıraya alınan taşıtlar için taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="79a2d-152">Defines the transport security settings for queued transports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="79a2d-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="79a2d-153">See also</span></span>

- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [<span data-ttu-id="79a2d-154">WCF'de Kuyruklar</span><span class="sxs-lookup"><span data-stu-id="79a2d-154">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="79a2d-155">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="79a2d-155">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="79a2d-156">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="79a2d-156">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="79a2d-157">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="79a2d-157">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="79a2d-158">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="79a2d-158">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)

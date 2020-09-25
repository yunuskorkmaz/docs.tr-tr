---
title: <transport> / <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 72e1b338-39f0-4af1-a5d9-7a2fb79f6a0b
ms.openlocfilehash: 84a5437de851ecdb96d0463ec574186ba5f91d9e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203884"
---
# <a name="transport-of-netmsmqbinding"></a><span data-ttu-id="aaa49-102">\<transport> / \<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="aaa49-102">\<transport> of \<netMsmqBinding></span></span>

<span data-ttu-id="aaa49-103">Taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="aaa49-103">Defines the transport security settings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netMsmqBinding>**](netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="aaa49-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="aaa49-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aaa49-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="aaa49-105">Attributes and Elements</span></span>  

 <span data-ttu-id="aaa49-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="aaa49-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aaa49-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="aaa49-107">Attributes</span></span>  
  
|<span data-ttu-id="aaa49-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="aaa49-108">Attribute</span></span>|<span data-ttu-id="aaa49-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aaa49-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="aaa49-110">msmqAuthenticationMode</span><span class="sxs-lookup"><span data-stu-id="aaa49-110">msmqAuthenticationMode</span></span>|<span data-ttu-id="aaa49-111">İletinin MSMQ taşıması tarafından nasıl doğrulanabilmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="aaa49-111">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="aaa49-112">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="aaa49-112">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="aaa49-113">-None: kimlik doğrulaması yok.</span><span class="sxs-lookup"><span data-stu-id="aaa49-113">-   None: No authentication.</span></span><br /><span data-ttu-id="aaa49-114">-WindowsDomain: kimlik doğrulama mekanizması, iletiyle ilişkili güvenlik tanımlayıcısı için X. 509.440 sertifikasını almak üzere Active Directory kullanır.</span><span class="sxs-lookup"><span data-stu-id="aaa49-114">-   WindowsDomain: The authentication mechanism uses Active Directory to retrieve the X.509 certificate for the security identifier associated with the message.</span></span> <span data-ttu-id="aaa49-115">Bu daha sonra kullanıcının sıra için yazma iznine sahip olduğundan emin olmak üzere kuyruğun ACL 'sini denetlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="aaa49-115">This is then used to check the ACL of the queue to ensure the user has write permission for the queue.</span></span><br /><span data-ttu-id="aaa49-116">-Sertifika: Kanal sertifikayı sertifika deposundan alır.</span><span class="sxs-lookup"><span data-stu-id="aaa49-116">-   Certificate: The channel retrieves the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="aaa49-117">Varsayılan değer: `WindowsDomain`.</span><span class="sxs-lookup"><span data-stu-id="aaa49-117">The default is `WindowsDomain`.</span></span><br /><br /> <span data-ttu-id="aaa49-118">Bu öznitelik olarak ayarlandıysa `None` , `msmqProtectionLevel` özniteliği de olarak ayarlanmalıdır `None` .</span><span class="sxs-lookup"><span data-stu-id="aaa49-118">If this attribute is set to `None`, the `msmqProtectionLevel` attribute must also be set to `None`.</span></span> <span data-ttu-id="aaa49-119">Bu öznitelik türü <xref:System.ServiceModel.MsmqAuthenticationMode></span><span class="sxs-lookup"><span data-stu-id="aaa49-119">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode></span></span>|  
|<span data-ttu-id="aaa49-120">Msmqencryptionalgoritması</span><span class="sxs-lookup"><span data-stu-id="aaa49-120">msmqEncryptionAlgorithm</span></span>|<span data-ttu-id="aaa49-121">Message Queue yöneticileri arasında ileti aktarılırken ileti şifreleme için kullanılacak algoritmayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="aaa49-121">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="aaa49-122">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="aaa49-122">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="aaa49-123">- RC4Stream</span><span class="sxs-lookup"><span data-stu-id="aaa49-123">-   RC4Stream</span></span><br /><span data-ttu-id="aaa49-124">-AES</span><span class="sxs-lookup"><span data-stu-id="aaa49-124">-   AES</span></span><br /><span data-ttu-id="aaa49-125">-Varsayılan değer `RC4Stream` .</span><span class="sxs-lookup"><span data-stu-id="aaa49-125">-   The default value is `RC4Stream`.</span></span> <span data-ttu-id="aaa49-126">Bu öznitelik türü <xref:System.ServiceModel.MsmqEncryptionAlgorithm> .</span><span class="sxs-lookup"><span data-stu-id="aaa49-126">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|<span data-ttu-id="aaa49-127">msmqProtectionLevel</span><span class="sxs-lookup"><span data-stu-id="aaa49-127">msmqProtectionLevel</span></span>|<span data-ttu-id="aaa49-128">MSMQ taşıması düzeyinde iletilerin güvenli hale getirilme yöntemini belirtir.</span><span class="sxs-lookup"><span data-stu-id="aaa49-128">Specifies the way messages are secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="aaa49-129">Şifreleme ileti bütünlüğünü sağlar, oturum açma ve şifreleme hem ileti bütünlüğünü hem de Red olmamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="aaa49-129">Encryption ensures message integrity, while sign and encrypt ensures both message integrity and non-repudiation.</span></span> <span data-ttu-id="aaa49-130">Diğer bir deyişle, ileti gerçekten gönderenden geldi ve gönderici kim olduğunu söyledikleri kişidir.</span><span class="sxs-lookup"><span data-stu-id="aaa49-130">That is, the message indeed came from the sender and the sender is who they say they are.</span></span> <span data-ttu-id="aaa49-131">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="aaa49-131">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="aaa49-132">-None: koruma yok.</span><span class="sxs-lookup"><span data-stu-id="aaa49-132">-   None: No protection.</span></span><br /><span data-ttu-id="aaa49-133">-Sign: Iletiler imzalanır.</span><span class="sxs-lookup"><span data-stu-id="aaa49-133">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="aaa49-134">-EncryptAndSign: Iletiler şifrelenir ve imzalanır.</span><span class="sxs-lookup"><span data-stu-id="aaa49-134">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><span data-ttu-id="aaa49-135">-Varsayılan değer `Sign` .</span><span class="sxs-lookup"><span data-stu-id="aaa49-135">-   The default is `Sign`.</span></span>|  
|<span data-ttu-id="aaa49-136">msmqSecureHashAlgorithm</span><span class="sxs-lookup"><span data-stu-id="aaa49-136">msmqSecureHashAlgorithm</span></span>|<span data-ttu-id="aaa49-137">İleti özetinin bilgi işlem için kullanılacak karma algoritmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="aaa49-137">Specifies the hash algorithm to be used for computing the message digest.</span></span> <span data-ttu-id="aaa49-138">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="aaa49-138">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="aaa49-139">-MD5</span><span class="sxs-lookup"><span data-stu-id="aaa49-139">-   MD5</span></span><br /><span data-ttu-id="aaa49-140">-SHA1</span><span class="sxs-lookup"><span data-stu-id="aaa49-140">-   SHA1</span></span><br /><span data-ttu-id="aaa49-141">-SHA256</span><span class="sxs-lookup"><span data-stu-id="aaa49-141">-   SHA256</span></span><br /><span data-ttu-id="aaa49-142">-SHA512 olur</span><span class="sxs-lookup"><span data-stu-id="aaa49-142">-   SHA512</span></span><br /><br /> <span data-ttu-id="aaa49-143">Varsayılan değer: `SHA1`.</span><span class="sxs-lookup"><span data-stu-id="aaa49-143">The default is `SHA1`.</span></span> <span data-ttu-id="aaa49-144">Bu öznitelik türü <xref:System.ServiceModel.MsmqSecureHashAlgorithm> .</span><span class="sxs-lookup"><span data-stu-id="aaa49-144">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span><br><span data-ttu-id="aaa49-145">MD5 ve SHA1 ile ilgili çarpışma sorunları nedeniyle, Microsoft SHA256 veya daha iyi bir performans öneriyor.</span><span class="sxs-lookup"><span data-stu-id="aaa49-145">Due to collision problems with MD5 and SHA1, Microsoft recommends SHA256 or better.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aaa49-146">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="aaa49-146">Child Elements</span></span>  

 <span data-ttu-id="aaa49-147">Yok</span><span class="sxs-lookup"><span data-stu-id="aaa49-147">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="aaa49-148">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="aaa49-148">Parent Elements</span></span>  
  
|<span data-ttu-id="aaa49-149">Öğe</span><span class="sxs-lookup"><span data-stu-id="aaa49-149">Element</span></span>|<span data-ttu-id="aaa49-150">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aaa49-150">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-netmsmqbinding.md)|<span data-ttu-id="aaa49-151">Sıraya alınan taşıtlar için taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="aaa49-151">Defines the transport security settings for queued transports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="aaa49-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aaa49-152">See also</span></span>

- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [<span data-ttu-id="aaa49-153">WCF'de Kuyruklar</span><span class="sxs-lookup"><span data-stu-id="aaa49-153">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="aaa49-154">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="aaa49-154">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="aaa49-155">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="aaa49-155">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="aaa49-156">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="aaa49-156">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="aaa49-157">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="aaa49-157">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)

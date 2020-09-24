---
title: <transport> / <msmqIntegrationBinding>
ms.date: 03/30/2017
ms.assetid: 054579e3-7fdd-47df-99ca-952706ba5c8e
ms.openlocfilehash: 03e6236d1e89f16a460860f5dffff19b7bed8a0a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169836"
---
# <a name="transport-of-msmqintegrationbinding"></a><span data-ttu-id="9cdc5-102">\<transport> / \<msmqIntegrationBinding></span><span class="sxs-lookup"><span data-stu-id="9cdc5-102">\<transport> of \<msmqIntegrationBinding></span></span>

<span data-ttu-id="9cdc5-103">Message Queuing tümleştirme taşıması için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9cdc5-103">Defines the security settings for the Message Queuing integration transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<msmqIntegrationBinding>**](msmqintegrationbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-msmqintegrationbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="9cdc5-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="9cdc5-104">Syntax</span></span>  
  
```xml  
<security>
  <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"
             msmqEncryptionAlgorithm="RC4Stream/AES"
             msmqProtectionLevel="None/Sign/EncryptAndSign"
             msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9cdc5-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9cdc5-105">Attributes and Elements</span></span>  

 <span data-ttu-id="9cdc5-106">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="9cdc5-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9cdc5-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9cdc5-107">Attributes</span></span>  
  
|<span data-ttu-id="9cdc5-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9cdc5-108">Attribute</span></span>|<span data-ttu-id="9cdc5-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9cdc5-109">Description</span></span>|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|<span data-ttu-id="9cdc5-110">İletinin MSMQ taşıması tarafından nasıl doğrulanabilmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9cdc5-110">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="9cdc5-111">Bu olarak ayarlanırsa `None` , `msmqProtectionLevel` özniteliğinin değeri de olarak ayarlanmalıdır `None` .</span><span class="sxs-lookup"><span data-stu-id="9cdc5-111">If this is set to `None`, the value of the `msmqProtectionLevel` attribute must also be set to `None`.</span></span><br /><br /> <span data-ttu-id="9cdc5-112">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="9cdc5-112">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="9cdc5-113">-None: kimlik doğrulaması yok.</span><span class="sxs-lookup"><span data-stu-id="9cdc5-113">-   None: No authentication.</span></span><br /><span data-ttu-id="9cdc5-114">-WindowsDomain: kimlik doğrulama mekanizması, iletiyle ilişkili SID için X. 509.440 sertifikasını almak üzere Active Directory kullanır.</span><span class="sxs-lookup"><span data-stu-id="9cdc5-114">-   WindowsDomain: The authentication mechanism uses Active Directory to get the X.509 certificate for the SID associated with the message.</span></span> <span data-ttu-id="9cdc5-115">Bu daha sonra kullanıcının sıraya yazma izni olduğundan emin olmak için kuyruğun ACL 'sini denetlemek üzere kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9cdc5-115">This is then used to check the ACL of the queue to ensure the user has permission to write to the queue.</span></span><br /><span data-ttu-id="9cdc5-116">-Sertifika: Kanal, sertifika deposundan sertifikayı alır.</span><span class="sxs-lookup"><span data-stu-id="9cdc5-116">-   Certificate: The channel gets the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="9cdc5-117">Varsayılan değer WindowsDomain ' dir.</span><span class="sxs-lookup"><span data-stu-id="9cdc5-117">The default value is WindowsDomain.</span></span> <span data-ttu-id="9cdc5-118">Bu öznitelik türü <xref:System.ServiceModel.MsmqAuthenticationMode> .</span><span class="sxs-lookup"><span data-stu-id="9cdc5-118">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode>.</span></span>|  
|`msmqEncryptionAlgorithm`|<span data-ttu-id="9cdc5-119">Message Queue yöneticileri arasında ileti aktarılırken ileti şifreleme için kullanılacak algoritmayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="9cdc5-119">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="9cdc5-120">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="9cdc5-120">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="9cdc5-121">- RC4Stream</span><span class="sxs-lookup"><span data-stu-id="9cdc5-121">-   RC4Stream</span></span><br /><span data-ttu-id="9cdc5-122">-AES</span><span class="sxs-lookup"><span data-stu-id="9cdc5-122">-   AES</span></span><br /><br /> <span data-ttu-id="9cdc5-123">Varsayılan değer RC4Stream ' dir.</span><span class="sxs-lookup"><span data-stu-id="9cdc5-123">The default value is RC4Stream.</span></span> <span data-ttu-id="9cdc5-124">Bu öznitelik türü <xref:System.ServiceModel.MsmqEncryptionAlgorithm> .</span><span class="sxs-lookup"><span data-stu-id="9cdc5-124">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|`msmqProtectionLevel`|<span data-ttu-id="9cdc5-125">İletinin MSMQ taşıma düzeyinde nasıl güvenlik altına alınacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9cdc5-125">Specifies how the message is secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="9cdc5-126">Şifreleme, her iki ileti bütünlüğünü ve Red olmamasını sağlarken, şifreleme ileti bütünlüğünü sağlar; diğer bir deyişle, ileti gerçekten gönderenden gelir ve gönderici kim olduğunu söyledikleri kişidir.</span><span class="sxs-lookup"><span data-stu-id="9cdc5-126">Encryption ensures message integrity while EncryptAndSign ensures both message integrity and non-repudiation; that is, the message indeed comes from the sender and the sender is who they say they are.</span></span><br /><br /> <span data-ttu-id="9cdc5-127">-Geçerli değerler aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="9cdc5-127">-   Valid values include the following:</span></span><br /><span data-ttu-id="9cdc5-128">-None: koruma yok.</span><span class="sxs-lookup"><span data-stu-id="9cdc5-128">-   None: No protection.</span></span><br /><span data-ttu-id="9cdc5-129">-Sign: Iletiler imzalanır.</span><span class="sxs-lookup"><span data-stu-id="9cdc5-129">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="9cdc5-130">-EncryptAndSign: Iletiler şifrelenir ve imzalanır.</span><span class="sxs-lookup"><span data-stu-id="9cdc5-130">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="9cdc5-131">Varsayılan değer, Işaret ' dır.</span><span class="sxs-lookup"><span data-stu-id="9cdc5-131">The default value is Sign.</span></span> <span data-ttu-id="9cdc5-132">Bu öznitelik ProtectionLevel türündedir.</span><span class="sxs-lookup"><span data-stu-id="9cdc5-132">This attribute is of type ProtectionLevel.</span></span>|  
|`msmqSecureHashAlgorithm`|<span data-ttu-id="9cdc5-133">-İmzaların bir parçası olarak Özet hesaplanırken kullanılacak algoritmayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="9cdc5-133">-   Specifies the algorithm to be used in computing the digest as part of signatures.</span></span> <span data-ttu-id="9cdc5-134">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="9cdc5-134">Valid values include the following:</span></span><br /><span data-ttu-id="9cdc5-135">-MD5</span><span class="sxs-lookup"><span data-stu-id="9cdc5-135">-   MD5</span></span><br /><span data-ttu-id="9cdc5-136">-SHA1</span><span class="sxs-lookup"><span data-stu-id="9cdc5-136">-   SHA1</span></span><br /><span data-ttu-id="9cdc5-137">-SHA256</span><span class="sxs-lookup"><span data-stu-id="9cdc5-137">-   SHA256</span></span><br /><span data-ttu-id="9cdc5-138">-SHA512 olur</span><span class="sxs-lookup"><span data-stu-id="9cdc5-138">-   SHA512</span></span><br /><br /> <span data-ttu-id="9cdc5-139">Varsayılan değer SHA1 ' dır.</span><span class="sxs-lookup"><span data-stu-id="9cdc5-139">The default value is SHA1.</span></span> <span data-ttu-id="9cdc5-140">Bu öznitelik türü <xref:System.ServiceModel.MsmqSecureHashAlgorithm> .</span><span class="sxs-lookup"><span data-stu-id="9cdc5-140">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span><br><span data-ttu-id="9cdc5-141">MD5 ve SHA1 ile ilgili çarpışma sorunları nedeniyle, Microsoft SHA256 veya daha iyi bir performans öneriyor.</span><span class="sxs-lookup"><span data-stu-id="9cdc5-141">Due to collision problems with MD5 and SHA1, Microsoft recommends SHA256 or better.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9cdc5-142">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9cdc5-142">Child Elements</span></span>  

 <span data-ttu-id="9cdc5-143">Yok</span><span class="sxs-lookup"><span data-stu-id="9cdc5-143">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9cdc5-144">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9cdc5-144">Parent Elements</span></span>  
  
|<span data-ttu-id="9cdc5-145">Öğe</span><span class="sxs-lookup"><span data-stu-id="9cdc5-145">Element</span></span>|<span data-ttu-id="9cdc5-146">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9cdc5-146">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-basichttpbinding.md)|<span data-ttu-id="9cdc5-147">MSMQ bağlamasının güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9cdc5-147">Defines the security settings for a MSMQ binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9cdc5-148">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9cdc5-148">Remarks</span></span>  

 <span data-ttu-id="9cdc5-149">Bu öğe Message Queuing tümleştirme aktarımının güvenlik ayarlarını kapsar.</span><span class="sxs-lookup"><span data-stu-id="9cdc5-149">This element encapsulates the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="9cdc5-150">Bu ayarlar hem Message Queuing tümleştirme hem de sıraya alınmış aktarımlara yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="9cdc5-150">The settings are the same for both the Message Queuing integration and queued transports.</span></span> <span data-ttu-id="9cdc5-151">Kimlik doğrulama modu, şifreleme algoritması, güvenli karma algoritması ve koruma düzeyini ayarlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="9cdc5-151">It enables you to set the Authentication Mode, Encryption Algorithm, Secure Hash Algorithm, and Protection Level.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cdc5-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9cdc5-152">See also</span></span>

- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [<span data-ttu-id="9cdc5-153">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="9cdc5-153">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="9cdc5-154">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="9cdc5-154">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="9cdc5-155">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="9cdc5-155">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="9cdc5-156">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="9cdc5-156">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)

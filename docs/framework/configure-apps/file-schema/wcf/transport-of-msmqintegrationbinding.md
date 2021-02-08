---
description: 'Hakkında daha fazla bilgi <transport> edinin: <msmqIntegrationBinding>'
title: <transport> / <msmqIntegrationBinding>
ms.date: 03/30/2017
ms.assetid: 054579e3-7fdd-47df-99ca-952706ba5c8e
ms.openlocfilehash: bcca714320f333a16d518248531efe8039ff566e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99773530"
---
# <a name="transport-of-msmqintegrationbinding"></a><span data-ttu-id="45711-103">\<transport> / \<msmqIntegrationBinding></span><span class="sxs-lookup"><span data-stu-id="45711-103">\<transport> of \<msmqIntegrationBinding></span></span>

<span data-ttu-id="45711-104">Message Queuing tümleştirme taşıması için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="45711-104">Defines the security settings for the Message Queuing integration transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<msmqIntegrationBinding>**](msmqintegrationbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-msmqintegrationbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="45711-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="45711-105">Syntax</span></span>  
  
```xml  
<security>
  <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"
             msmqEncryptionAlgorithm="RC4Stream/AES"
             msmqProtectionLevel="None/Sign/EncryptAndSign"
             msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="45711-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="45711-106">Attributes and Elements</span></span>  

 <span data-ttu-id="45711-107">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="45711-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="45711-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="45711-108">Attributes</span></span>  
  
|<span data-ttu-id="45711-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="45711-109">Attribute</span></span>|<span data-ttu-id="45711-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="45711-110">Description</span></span>|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|<span data-ttu-id="45711-111">İletinin MSMQ taşıması tarafından nasıl doğrulanabilmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="45711-111">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="45711-112">Bu olarak ayarlanırsa `None` , `msmqProtectionLevel` özniteliğinin değeri de olarak ayarlanmalıdır `None` .</span><span class="sxs-lookup"><span data-stu-id="45711-112">If this is set to `None`, the value of the `msmqProtectionLevel` attribute must also be set to `None`.</span></span><br /><br /> <span data-ttu-id="45711-113">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="45711-113">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="45711-114">-None: kimlik doğrulaması yok.</span><span class="sxs-lookup"><span data-stu-id="45711-114">-   None: No authentication.</span></span><br /><span data-ttu-id="45711-115">-WindowsDomain: kimlik doğrulama mekanizması, iletiyle ilişkili SID için X. 509.440 sertifikasını almak üzere Active Directory kullanır.</span><span class="sxs-lookup"><span data-stu-id="45711-115">-   WindowsDomain: The authentication mechanism uses Active Directory to get the X.509 certificate for the SID associated with the message.</span></span> <span data-ttu-id="45711-116">Bu daha sonra kullanıcının sıraya yazma izni olduğundan emin olmak için kuyruğun ACL 'sini denetlemek üzere kullanılır.</span><span class="sxs-lookup"><span data-stu-id="45711-116">This is then used to check the ACL of the queue to ensure the user has permission to write to the queue.</span></span><br /><span data-ttu-id="45711-117">-Sertifika: Kanal, sertifika deposundan sertifikayı alır.</span><span class="sxs-lookup"><span data-stu-id="45711-117">-   Certificate: The channel gets the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="45711-118">Varsayılan değer WindowsDomain ' dir.</span><span class="sxs-lookup"><span data-stu-id="45711-118">The default value is WindowsDomain.</span></span> <span data-ttu-id="45711-119">Bu öznitelik türü <xref:System.ServiceModel.MsmqAuthenticationMode> .</span><span class="sxs-lookup"><span data-stu-id="45711-119">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode>.</span></span>|  
|`msmqEncryptionAlgorithm`|<span data-ttu-id="45711-120">Message Queue yöneticileri arasında ileti aktarılırken ileti şifreleme için kullanılacak algoritmayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="45711-120">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="45711-121">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="45711-121">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="45711-122">- RC4Stream</span><span class="sxs-lookup"><span data-stu-id="45711-122">-   RC4Stream</span></span><br /><span data-ttu-id="45711-123">-AES</span><span class="sxs-lookup"><span data-stu-id="45711-123">-   AES</span></span><br /><br /> <span data-ttu-id="45711-124">Varsayılan değer RC4Stream ' dir.</span><span class="sxs-lookup"><span data-stu-id="45711-124">The default value is RC4Stream.</span></span> <span data-ttu-id="45711-125">Bu öznitelik türü <xref:System.ServiceModel.MsmqEncryptionAlgorithm> .</span><span class="sxs-lookup"><span data-stu-id="45711-125">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|`msmqProtectionLevel`|<span data-ttu-id="45711-126">İletinin MSMQ taşıma düzeyinde nasıl güvenlik altına alınacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="45711-126">Specifies how the message is secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="45711-127">Şifreleme, her iki ileti bütünlüğünü ve Red olmamasını sağlarken, şifreleme ileti bütünlüğünü sağlar; diğer bir deyişle, ileti gerçekten gönderenden gelir ve gönderici kim olduğunu söyledikleri kişidir.</span><span class="sxs-lookup"><span data-stu-id="45711-127">Encryption ensures message integrity while EncryptAndSign ensures both message integrity and non-repudiation; that is, the message indeed comes from the sender and the sender is who they say they are.</span></span><br /><br /> <span data-ttu-id="45711-128">-Geçerli değerler aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="45711-128">-   Valid values include the following:</span></span><br /><span data-ttu-id="45711-129">-None: koruma yok.</span><span class="sxs-lookup"><span data-stu-id="45711-129">-   None: No protection.</span></span><br /><span data-ttu-id="45711-130">-Sign: Iletiler imzalanır.</span><span class="sxs-lookup"><span data-stu-id="45711-130">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="45711-131">-EncryptAndSign: Iletiler şifrelenir ve imzalanır.</span><span class="sxs-lookup"><span data-stu-id="45711-131">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="45711-132">Varsayılan değer, Işaret ' dır.</span><span class="sxs-lookup"><span data-stu-id="45711-132">The default value is Sign.</span></span> <span data-ttu-id="45711-133">Bu öznitelik ProtectionLevel türündedir.</span><span class="sxs-lookup"><span data-stu-id="45711-133">This attribute is of type ProtectionLevel.</span></span>|  
|`msmqSecureHashAlgorithm`|<span data-ttu-id="45711-134">-İmzaların bir parçası olarak Özet hesaplanırken kullanılacak algoritmayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="45711-134">-   Specifies the algorithm to be used in computing the digest as part of signatures.</span></span> <span data-ttu-id="45711-135">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="45711-135">Valid values include the following:</span></span><br /><span data-ttu-id="45711-136">-MD5</span><span class="sxs-lookup"><span data-stu-id="45711-136">-   MD5</span></span><br /><span data-ttu-id="45711-137">-SHA1</span><span class="sxs-lookup"><span data-stu-id="45711-137">-   SHA1</span></span><br /><span data-ttu-id="45711-138">-SHA256</span><span class="sxs-lookup"><span data-stu-id="45711-138">-   SHA256</span></span><br /><span data-ttu-id="45711-139">-SHA512 olur</span><span class="sxs-lookup"><span data-stu-id="45711-139">-   SHA512</span></span><br /><br /> <span data-ttu-id="45711-140">Varsayılan değer SHA1 ' dır.</span><span class="sxs-lookup"><span data-stu-id="45711-140">The default value is SHA1.</span></span> <span data-ttu-id="45711-141">Bu öznitelik türü <xref:System.ServiceModel.MsmqSecureHashAlgorithm> .</span><span class="sxs-lookup"><span data-stu-id="45711-141">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span><br><span data-ttu-id="45711-142">MD5 ve SHA1 ile ilgili çarpışma sorunları nedeniyle, Microsoft SHA256 veya daha iyi bir performans öneriyor.</span><span class="sxs-lookup"><span data-stu-id="45711-142">Due to collision problems with MD5 and SHA1, Microsoft recommends SHA256 or better.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="45711-143">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="45711-143">Child Elements</span></span>  

 <span data-ttu-id="45711-144">Yok</span><span class="sxs-lookup"><span data-stu-id="45711-144">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="45711-145">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="45711-145">Parent Elements</span></span>  
  
|<span data-ttu-id="45711-146">Öğe</span><span class="sxs-lookup"><span data-stu-id="45711-146">Element</span></span>|<span data-ttu-id="45711-147">Açıklama</span><span class="sxs-lookup"><span data-stu-id="45711-147">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-basichttpbinding.md)|<span data-ttu-id="45711-148">MSMQ bağlamasının güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="45711-148">Defines the security settings for a MSMQ binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="45711-149">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="45711-149">Remarks</span></span>  

 <span data-ttu-id="45711-150">Bu öğe Message Queuing tümleştirme aktarımının güvenlik ayarlarını kapsar.</span><span class="sxs-lookup"><span data-stu-id="45711-150">This element encapsulates the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="45711-151">Bu ayarlar hem Message Queuing tümleştirme hem de sıraya alınmış aktarımlara yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="45711-151">The settings are the same for both the Message Queuing integration and queued transports.</span></span> <span data-ttu-id="45711-152">Kimlik doğrulama modu, şifreleme algoritması, güvenli karma algoritması ve koruma düzeyini ayarlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="45711-152">It enables you to set the Authentication Mode, Encryption Algorithm, Secure Hash Algorithm, and Protection Level.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45711-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="45711-153">See also</span></span>

- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [<span data-ttu-id="45711-154">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="45711-154">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="45711-155">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="45711-155">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="45711-156">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="45711-156">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="45711-157">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="45711-157">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)

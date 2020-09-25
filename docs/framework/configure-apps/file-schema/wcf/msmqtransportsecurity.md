---
title: <msmqTransportSecurity>
ms.date: 03/30/2017
ms.assetid: 092e911b-ab1b-4069-a26e-6134c3299e06
ms.openlocfilehash: 9d28f3f08e9c3984c055567df03f2839709a1522
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204651"
---
# \<msmqTransportSecurity>

<span data-ttu-id="a4baa-101">Özel bağlama için MSMQ taşıma güvenlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a4baa-101">Specifies MSMQ transport security settings for a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<msmqIntegration>**](msmqintegration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<msmqTransportSecurity>**  
  
## <a name="syntax"></a><span data-ttu-id="a4baa-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="a4baa-102">Syntax</span></span>  
  
```xml  
<msmqTransportSecurity msmqAuthenticationMode="None/Windows/Certificate"
                       msmqEncryptionAlgorithm="RC4Stream/AES"
                       msmqProtectionLevel="None/Sign/EncryptAndSign"
                       msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
</msmqTransportSecurity>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a4baa-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a4baa-103">Attributes and Elements</span></span>  

 <span data-ttu-id="a4baa-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a4baa-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a4baa-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a4baa-105">Attributes</span></span>  
  
|<span data-ttu-id="a4baa-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a4baa-106">Attribute</span></span>|<span data-ttu-id="a4baa-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a4baa-107">Description</span></span>|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|<span data-ttu-id="a4baa-108">İletinin MSMQ taşıması tarafından nasıl doğrulanabilmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a4baa-108">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="a4baa-109">Bu olarak ayarlanırsa `None` , `msmqProtectionLevel` özniteliğinin değeri de olarak ayarlanmalıdır `None` .</span><span class="sxs-lookup"><span data-stu-id="a4baa-109">If this is set to `None`, the value of the `msmqProtectionLevel` attribute must also be set to `None`.</span></span><br /><br /> <span data-ttu-id="a4baa-110">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="a4baa-110">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="a4baa-111">-None: kimlik doğrulaması yok.</span><span class="sxs-lookup"><span data-stu-id="a4baa-111">-   None: No authentication.</span></span><br /><span data-ttu-id="a4baa-112">-Windows: kimlik doğrulama mekanizması, iletiyle ilişkili SID için X. 509.440 sertifikasını almak üzere Active Directory kullanır.</span><span class="sxs-lookup"><span data-stu-id="a4baa-112">-   Windows: The authentication mechanism uses Active Directory to get the X.509 certificate for the SID associated with the message.</span></span> <span data-ttu-id="a4baa-113">Bu daha sonra kullanıcının sıraya yazma izni olduğundan emin olmak için kuyruğun ACL 'sini denetlemek üzere kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a4baa-113">This is then used to check the ACL of the queue to ensure the user has permission to write to the queue.</span></span><br /><span data-ttu-id="a4baa-114">-Sertifika: Kanal, sertifika deposundan sertifikayı alır.</span><span class="sxs-lookup"><span data-stu-id="a4baa-114">-   Certificate: The channel gets the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="a4baa-115">Varsayılan değer Windows ' dır.</span><span class="sxs-lookup"><span data-stu-id="a4baa-115">The default value is Windows.</span></span> <span data-ttu-id="a4baa-116">Bu öznitelik türü <xref:System.ServiceModel.MsmqAuthenticationMode> .</span><span class="sxs-lookup"><span data-stu-id="a4baa-116">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode>.</span></span>|  
|`msmqEncryptionAlgorithm`|<span data-ttu-id="a4baa-117">Message Queue yöneticileri arasında ileti aktarılırken ileti şifreleme için kullanılacak algoritmayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="a4baa-117">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="a4baa-118">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="a4baa-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="a4baa-119">- RC4Stream</span><span class="sxs-lookup"><span data-stu-id="a4baa-119">-   RC4Stream</span></span><br /><span data-ttu-id="a4baa-120">-AES</span><span class="sxs-lookup"><span data-stu-id="a4baa-120">-   AES</span></span><br /><br /> <span data-ttu-id="a4baa-121">Varsayılan değer RC4Stream ' dir.</span><span class="sxs-lookup"><span data-stu-id="a4baa-121">The default value is RC4Stream.</span></span> <span data-ttu-id="a4baa-122">Bu öznitelik türü <xref:System.ServiceModel.MsmqEncryptionAlgorithm> .</span><span class="sxs-lookup"><span data-stu-id="a4baa-122">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|`msmqProtectionLevel`|<span data-ttu-id="a4baa-123">İletinin MSMQ taşıma düzeyinde nasıl güvenlik altına alınacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a4baa-123">Specifies how the message is secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="a4baa-124">Şifreleme, her iki ileti bütünlüğünü ve Red olmamasını sağlarken, şifreleme ileti bütünlüğünü sağlar; diğer bir deyişle, ileti gerçekten gönderenden gelir ve gönderici kim olduğunu söyledikleri kişidir.</span><span class="sxs-lookup"><span data-stu-id="a4baa-124">Encryption ensures message integrity while EncryptAndSign ensures both message integrity and non-repudiation; that is, the message indeed comes from the sender and the sender is who they say they are.</span></span> <span data-ttu-id="a4baa-125">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="a4baa-125">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="a4baa-126">-None: koruma yok.</span><span class="sxs-lookup"><span data-stu-id="a4baa-126">-   None: No protection.</span></span><br /><span data-ttu-id="a4baa-127">-Sign: Iletiler imzalanır.</span><span class="sxs-lookup"><span data-stu-id="a4baa-127">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="a4baa-128">-EncryptAndSign: Iletiler şifrelenir ve imzalanır.</span><span class="sxs-lookup"><span data-stu-id="a4baa-128">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="a4baa-129">Varsayılan değer, Işaret ' dır.</span><span class="sxs-lookup"><span data-stu-id="a4baa-129">The default value is Sign.</span></span> <span data-ttu-id="a4baa-130">Bu öznitelik türü <xref:System.Net.Security.ProtectionLevel> .</span><span class="sxs-lookup"><span data-stu-id="a4baa-130">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
|`msmqSecureHashAlgorithm`|<span data-ttu-id="a4baa-131">İmzaların bir parçası olarak Özet hesaplanırken kullanılacak algoritmayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="a4baa-131">Specifies the algorithm to be used in computing the digest as part of signatures.</span></span> <span data-ttu-id="a4baa-132">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="a4baa-132">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="a4baa-133">-MD5</span><span class="sxs-lookup"><span data-stu-id="a4baa-133">-   MD5</span></span><br /><span data-ttu-id="a4baa-134">-SHA1</span><span class="sxs-lookup"><span data-stu-id="a4baa-134">-   SHA1</span></span><br /><span data-ttu-id="a4baa-135">-SHA256</span><span class="sxs-lookup"><span data-stu-id="a4baa-135">-   SHA256</span></span><br /><span data-ttu-id="a4baa-136">-SHA512 olur</span><span class="sxs-lookup"><span data-stu-id="a4baa-136">-   SHA512</span></span><br /><br /> <span data-ttu-id="a4baa-137">Varsayılan değer SHA1 ' dır.</span><span class="sxs-lookup"><span data-stu-id="a4baa-137">The default value is SHA1.</span></span> <span data-ttu-id="a4baa-138">Bu öznitelik türü <xref:System.ServiceModel.MsmqSecureHashAlgorithm> .</span><span class="sxs-lookup"><span data-stu-id="a4baa-138">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span><br><span data-ttu-id="a4baa-139">MD5 ve SHA1 ile ilgili çarpışma sorunları nedeniyle, Microsoft SHA256 veya daha iyi bir performans öneriyor.</span><span class="sxs-lookup"><span data-stu-id="a4baa-139">Due to collision problems with MD5 and SHA1, Microsoft recommends SHA256 or better.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a4baa-140">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a4baa-140">Child Elements</span></span>  

 <span data-ttu-id="a4baa-141">Yok.</span><span class="sxs-lookup"><span data-stu-id="a4baa-141">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a4baa-142">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a4baa-142">Parent Elements</span></span>  
  
|<span data-ttu-id="a4baa-143">Öğe</span><span class="sxs-lookup"><span data-stu-id="a4baa-143">Element</span></span>|<span data-ttu-id="a4baa-144">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a4baa-144">Description</span></span>|  
|-------------|-----------------|  
|[\<msmqIntegration>](msmqintegration.md)|<span data-ttu-id="a4baa-145">Message Queuing (MSMQ) gönderici veya alıcısıyla etkileşim için gereken ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="a4baa-145">Specifies settings required for interaction with a Message Queuing (MSMQ) sender or receiver.</span></span>|  
|[\<msmqTransport>](msmqtransport.md)|<span data-ttu-id="a4baa-146">Yerel MSMQ protokolünü kullanan bir Windows Communication Foundation (WCF) hizmeti için sıraya alma iletişim özelliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a4baa-146">Specifies the queuing communication properties for a Windows Communication Foundation (WCF) service that uses the native MSMQ protocol.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a4baa-147">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a4baa-147">Remarks</span></span>  

 <span data-ttu-id="a4baa-148">Taşıma güvenliği hakkında daha fazla bilgi için bkz. [Transport Security](../../../wcf/feature-details/transport-security.md).</span><span class="sxs-lookup"><span data-stu-id="a4baa-148">For more information on transport security, see [Transport Security](../../../wcf/feature-details/transport-security.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4baa-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a4baa-149">See also</span></span>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="a4baa-150">WCF'de Kuyruklar</span><span class="sxs-lookup"><span data-stu-id="a4baa-150">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="a4baa-151">Taşımalar</span><span class="sxs-lookup"><span data-stu-id="a4baa-151">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="a4baa-152">Taşıma Seçme</span><span class="sxs-lookup"><span data-stu-id="a4baa-152">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="a4baa-153">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="a4baa-153">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a4baa-154">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="a4baa-154">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="a4baa-155">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="a4baa-155">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="a4baa-156">Taşıma Güvenliği</span><span class="sxs-lookup"><span data-stu-id="a4baa-156">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)

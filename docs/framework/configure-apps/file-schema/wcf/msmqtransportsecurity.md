---
title: <msmqTransportSecurity>
ms.date: 03/30/2017
ms.assetid: 092e911b-ab1b-4069-a26e-6134c3299e06
ms.openlocfilehash: 5899c609b3cf52c4a275ba6fb10c5826fcf37f1e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153015"
---
# \<msmqTransportSecurity>
<span data-ttu-id="940bc-101">Özel bağlama için MSMQ taşıma güvenlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="940bc-101">Specifies MSMQ transport security settings for a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<msmqIntegration>**](msmqintegration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<msmqTransportSecurity>**  
  
## <a name="syntax"></a><span data-ttu-id="940bc-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="940bc-102">Syntax</span></span>  
  
```xml  
<msmqTransportSecurity msmqAuthenticationMode="None/Windows/Certificate"
                       msmqEncryptionAlgorithm="RC4Stream/AES"
                       msmqProtectionLevel="None/Sign/EncryptAndSign"
                       msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
</msmqTransportSecurity>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="940bc-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="940bc-103">Attributes and Elements</span></span>  
 <span data-ttu-id="940bc-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="940bc-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="940bc-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="940bc-105">Attributes</span></span>  
  
|<span data-ttu-id="940bc-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="940bc-106">Attribute</span></span>|<span data-ttu-id="940bc-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="940bc-107">Description</span></span>|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|<span data-ttu-id="940bc-108">İletinin MSMQ taşıması tarafından nasıl doğrulanabilmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="940bc-108">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="940bc-109">Bu olarak ayarlanırsa `None` , `msmqProtectionLevel` özniteliğinin değeri de olarak ayarlanmalıdır `None` .</span><span class="sxs-lookup"><span data-stu-id="940bc-109">If this is set to `None`, the value of the `msmqProtectionLevel` attribute must also be set to `None`.</span></span><br /><br /> <span data-ttu-id="940bc-110">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="940bc-110">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="940bc-111">-None: kimlik doğrulaması yok.</span><span class="sxs-lookup"><span data-stu-id="940bc-111">-   None: No authentication.</span></span><br /><span data-ttu-id="940bc-112">-Windows: kimlik doğrulama mekanizması, iletiyle ilişkili SID için X. 509.440 sertifikasını almak üzere Active Directory kullanır.</span><span class="sxs-lookup"><span data-stu-id="940bc-112">-   Windows: The authentication mechanism uses Active Directory to get the X.509 certificate for the SID associated with the message.</span></span> <span data-ttu-id="940bc-113">Bu daha sonra kullanıcının sıraya yazma izni olduğundan emin olmak için kuyruğun ACL 'sini denetlemek üzere kullanılır.</span><span class="sxs-lookup"><span data-stu-id="940bc-113">This is then used to check the ACL of the queue to ensure the user has permission to write to the queue.</span></span><br /><span data-ttu-id="940bc-114">-Sertifika: Kanal, sertifika deposundan sertifikayı alır.</span><span class="sxs-lookup"><span data-stu-id="940bc-114">-   Certificate: The channel gets the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="940bc-115">Varsayılan değer Windows ' dır.</span><span class="sxs-lookup"><span data-stu-id="940bc-115">The default value is Windows.</span></span> <span data-ttu-id="940bc-116">Bu öznitelik türü <xref:System.ServiceModel.MsmqAuthenticationMode> .</span><span class="sxs-lookup"><span data-stu-id="940bc-116">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode>.</span></span>|  
|`msmqEncryptionAlgorithm`|<span data-ttu-id="940bc-117">Message Queue yöneticileri arasında ileti aktarılırken ileti şifreleme için kullanılacak algoritmayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="940bc-117">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="940bc-118">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="940bc-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="940bc-119">- RC4Stream</span><span class="sxs-lookup"><span data-stu-id="940bc-119">-   RC4Stream</span></span><br /><span data-ttu-id="940bc-120">-AES</span><span class="sxs-lookup"><span data-stu-id="940bc-120">-   AES</span></span><br /><br /> <span data-ttu-id="940bc-121">Varsayılan değer RC4Stream ' dir.</span><span class="sxs-lookup"><span data-stu-id="940bc-121">The default value is RC4Stream.</span></span> <span data-ttu-id="940bc-122">Bu öznitelik türü <xref:System.ServiceModel.MsmqEncryptionAlgorithm> .</span><span class="sxs-lookup"><span data-stu-id="940bc-122">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|`msmqProtectionLevel`|<span data-ttu-id="940bc-123">İletinin MSMQ taşıma düzeyinde nasıl güvenlik altına alınacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="940bc-123">Specifies how the message is secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="940bc-124">Şifreleme, her iki ileti bütünlüğünü ve Red olmamasını sağlarken, şifreleme ileti bütünlüğünü sağlar; diğer bir deyişle, ileti gerçekten gönderenden gelir ve gönderici kim olduğunu söyledikleri kişidir.</span><span class="sxs-lookup"><span data-stu-id="940bc-124">Encryption ensures message integrity while EncryptAndSign ensures both message integrity and non-repudiation; that is, the message indeed comes from the sender and the sender is who they say they are.</span></span> <span data-ttu-id="940bc-125">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="940bc-125">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="940bc-126">-None: koruma yok.</span><span class="sxs-lookup"><span data-stu-id="940bc-126">-   None: No protection.</span></span><br /><span data-ttu-id="940bc-127">-Sign: Iletiler imzalanır.</span><span class="sxs-lookup"><span data-stu-id="940bc-127">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="940bc-128">-EncryptAndSign: Iletiler şifrelenir ve imzalanır.</span><span class="sxs-lookup"><span data-stu-id="940bc-128">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="940bc-129">Varsayılan değer, Işaret ' dır.</span><span class="sxs-lookup"><span data-stu-id="940bc-129">The default value is Sign.</span></span> <span data-ttu-id="940bc-130">Bu öznitelik türü <xref:System.Net.Security.ProtectionLevel> .</span><span class="sxs-lookup"><span data-stu-id="940bc-130">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
|`msmqSecureHashAlgorithm`|<span data-ttu-id="940bc-131">İmzaların bir parçası olarak Özet hesaplanırken kullanılacak algoritmayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="940bc-131">Specifies the algorithm to be used in computing the digest as part of signatures.</span></span> <span data-ttu-id="940bc-132">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="940bc-132">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="940bc-133">-MD5</span><span class="sxs-lookup"><span data-stu-id="940bc-133">-   MD5</span></span><br /><span data-ttu-id="940bc-134">-SHA1</span><span class="sxs-lookup"><span data-stu-id="940bc-134">-   SHA1</span></span><br /><span data-ttu-id="940bc-135">-SHA256</span><span class="sxs-lookup"><span data-stu-id="940bc-135">-   SHA256</span></span><br /><span data-ttu-id="940bc-136">-SHA512 olur</span><span class="sxs-lookup"><span data-stu-id="940bc-136">-   SHA512</span></span><br /><br /> <span data-ttu-id="940bc-137">Varsayılan değer SHA1 ' dır.</span><span class="sxs-lookup"><span data-stu-id="940bc-137">The default value is SHA1.</span></span> <span data-ttu-id="940bc-138">Bu öznitelik türü <xref:System.ServiceModel.MsmqSecureHashAlgorithm> .</span><span class="sxs-lookup"><span data-stu-id="940bc-138">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span><br><span data-ttu-id="940bc-139">MD5 ve SHA1 ile ilgili çarpışma sorunları nedeniyle, Microsoft SHA256 veya daha iyi bir performans öneriyor.</span><span class="sxs-lookup"><span data-stu-id="940bc-139">Due to collision problems with MD5 and SHA1, Microsoft recommends SHA256 or better.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="940bc-140">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="940bc-140">Child Elements</span></span>  
 <span data-ttu-id="940bc-141">Yok.</span><span class="sxs-lookup"><span data-stu-id="940bc-141">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="940bc-142">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="940bc-142">Parent Elements</span></span>  
  
|<span data-ttu-id="940bc-143">Öğe</span><span class="sxs-lookup"><span data-stu-id="940bc-143">Element</span></span>|<span data-ttu-id="940bc-144">Açıklama</span><span class="sxs-lookup"><span data-stu-id="940bc-144">Description</span></span>|  
|-------------|-----------------|  
|[\<msmqIntegration>](msmqintegration.md)|<span data-ttu-id="940bc-145">Message Queuing (MSMQ) gönderici veya alıcısıyla etkileşim için gereken ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="940bc-145">Specifies settings required for interaction with a Message Queuing (MSMQ) sender or receiver.</span></span>|  
|[\<msmqTransport>](msmqtransport.md)|<span data-ttu-id="940bc-146">Yerel MSMQ protokolünü kullanan bir Windows Communication Foundation (WCF) hizmeti için sıraya alma iletişim özelliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="940bc-146">Specifies the queuing communication properties for a Windows Communication Foundation (WCF) service that uses the native MSMQ protocol.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="940bc-147">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="940bc-147">Remarks</span></span>  
 <span data-ttu-id="940bc-148">Taşıma güvenliği hakkında daha fazla bilgi için bkz. [Transport Security](../../../wcf/feature-details/transport-security.md).</span><span class="sxs-lookup"><span data-stu-id="940bc-148">For more information on transport security, see [Transport Security](../../../wcf/feature-details/transport-security.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="940bc-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="940bc-149">See also</span></span>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="940bc-150">WCF'de Kuyruklar</span><span class="sxs-lookup"><span data-stu-id="940bc-150">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="940bc-151">Taşımalar</span><span class="sxs-lookup"><span data-stu-id="940bc-151">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="940bc-152">Taşıma Seçme</span><span class="sxs-lookup"><span data-stu-id="940bc-152">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="940bc-153">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="940bc-153">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="940bc-154">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="940bc-154">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="940bc-155">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="940bc-155">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="940bc-156">Aktarım Güvenliği</span><span class="sxs-lookup"><span data-stu-id="940bc-156">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)

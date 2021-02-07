---
description: 'Hakkında daha fazla bilgi edinin: <msmqTransportSecurity>'
title: <msmqTransportSecurity>
ms.date: 03/30/2017
ms.assetid: 092e911b-ab1b-4069-a26e-6134c3299e06
ms.openlocfilehash: d5a681c287749598c8c80470ea6d800f1687a80d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99684171"
---
# \<msmqTransportSecurity>

<span data-ttu-id="43db5-102">Özel bağlama için MSMQ taşıma güvenlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="43db5-102">Specifies MSMQ transport security settings for a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<msmqIntegration>**](msmqintegration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<msmqTransportSecurity>**  
  
## <a name="syntax"></a><span data-ttu-id="43db5-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="43db5-103">Syntax</span></span>  
  
```xml  
<msmqTransportSecurity msmqAuthenticationMode="None/Windows/Certificate"
                       msmqEncryptionAlgorithm="RC4Stream/AES"
                       msmqProtectionLevel="None/Sign/EncryptAndSign"
                       msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
</msmqTransportSecurity>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="43db5-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="43db5-104">Attributes and Elements</span></span>  

 <span data-ttu-id="43db5-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="43db5-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="43db5-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="43db5-106">Attributes</span></span>  
  
|<span data-ttu-id="43db5-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="43db5-107">Attribute</span></span>|<span data-ttu-id="43db5-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="43db5-108">Description</span></span>|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|<span data-ttu-id="43db5-109">İletinin MSMQ taşıması tarafından nasıl doğrulanabilmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="43db5-109">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="43db5-110">Bu olarak ayarlanırsa `None` , `msmqProtectionLevel` özniteliğinin değeri de olarak ayarlanmalıdır `None` .</span><span class="sxs-lookup"><span data-stu-id="43db5-110">If this is set to `None`, the value of the `msmqProtectionLevel` attribute must also be set to `None`.</span></span><br /><br /> <span data-ttu-id="43db5-111">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="43db5-111">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="43db5-112">-None: kimlik doğrulaması yok.</span><span class="sxs-lookup"><span data-stu-id="43db5-112">-   None: No authentication.</span></span><br /><span data-ttu-id="43db5-113">-Windows: kimlik doğrulama mekanizması, iletiyle ilişkili SID için X. 509.440 sertifikasını almak üzere Active Directory kullanır.</span><span class="sxs-lookup"><span data-stu-id="43db5-113">-   Windows: The authentication mechanism uses Active Directory to get the X.509 certificate for the SID associated with the message.</span></span> <span data-ttu-id="43db5-114">Bu daha sonra kullanıcının sıraya yazma izni olduğundan emin olmak için kuyruğun ACL 'sini denetlemek üzere kullanılır.</span><span class="sxs-lookup"><span data-stu-id="43db5-114">This is then used to check the ACL of the queue to ensure the user has permission to write to the queue.</span></span><br /><span data-ttu-id="43db5-115">-Sertifika: Kanal, sertifika deposundan sertifikayı alır.</span><span class="sxs-lookup"><span data-stu-id="43db5-115">-   Certificate: The channel gets the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="43db5-116">Varsayılan değer Windows ' dır.</span><span class="sxs-lookup"><span data-stu-id="43db5-116">The default value is Windows.</span></span> <span data-ttu-id="43db5-117">Bu öznitelik türü <xref:System.ServiceModel.MsmqAuthenticationMode> .</span><span class="sxs-lookup"><span data-stu-id="43db5-117">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode>.</span></span>|  
|`msmqEncryptionAlgorithm`|<span data-ttu-id="43db5-118">Message Queue yöneticileri arasında ileti aktarılırken ileti şifreleme için kullanılacak algoritmayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="43db5-118">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="43db5-119">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="43db5-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="43db5-120">- RC4Stream</span><span class="sxs-lookup"><span data-stu-id="43db5-120">-   RC4Stream</span></span><br /><span data-ttu-id="43db5-121">-AES</span><span class="sxs-lookup"><span data-stu-id="43db5-121">-   AES</span></span><br /><br /> <span data-ttu-id="43db5-122">Varsayılan değer RC4Stream ' dir.</span><span class="sxs-lookup"><span data-stu-id="43db5-122">The default value is RC4Stream.</span></span> <span data-ttu-id="43db5-123">Bu öznitelik türü <xref:System.ServiceModel.MsmqEncryptionAlgorithm> .</span><span class="sxs-lookup"><span data-stu-id="43db5-123">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|`msmqProtectionLevel`|<span data-ttu-id="43db5-124">İletinin MSMQ taşıma düzeyinde nasıl güvenlik altına alınacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="43db5-124">Specifies how the message is secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="43db5-125">Şifreleme, her iki ileti bütünlüğünü ve Red olmamasını sağlarken, şifreleme ileti bütünlüğünü sağlar; diğer bir deyişle, ileti gerçekten gönderenden gelir ve gönderici kim olduğunu söyledikleri kişidir.</span><span class="sxs-lookup"><span data-stu-id="43db5-125">Encryption ensures message integrity while EncryptAndSign ensures both message integrity and non-repudiation; that is, the message indeed comes from the sender and the sender is who they say they are.</span></span> <span data-ttu-id="43db5-126">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="43db5-126">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="43db5-127">-None: koruma yok.</span><span class="sxs-lookup"><span data-stu-id="43db5-127">-   None: No protection.</span></span><br /><span data-ttu-id="43db5-128">-Sign: Iletiler imzalanır.</span><span class="sxs-lookup"><span data-stu-id="43db5-128">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="43db5-129">-EncryptAndSign: Iletiler şifrelenir ve imzalanır.</span><span class="sxs-lookup"><span data-stu-id="43db5-129">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="43db5-130">Varsayılan değer, Işaret ' dır.</span><span class="sxs-lookup"><span data-stu-id="43db5-130">The default value is Sign.</span></span> <span data-ttu-id="43db5-131">Bu öznitelik türü <xref:System.Net.Security.ProtectionLevel> .</span><span class="sxs-lookup"><span data-stu-id="43db5-131">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
|`msmqSecureHashAlgorithm`|<span data-ttu-id="43db5-132">İmzaların bir parçası olarak Özet hesaplanırken kullanılacak algoritmayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="43db5-132">Specifies the algorithm to be used in computing the digest as part of signatures.</span></span> <span data-ttu-id="43db5-133">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="43db5-133">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="43db5-134">-MD5</span><span class="sxs-lookup"><span data-stu-id="43db5-134">-   MD5</span></span><br /><span data-ttu-id="43db5-135">-SHA1</span><span class="sxs-lookup"><span data-stu-id="43db5-135">-   SHA1</span></span><br /><span data-ttu-id="43db5-136">-SHA256</span><span class="sxs-lookup"><span data-stu-id="43db5-136">-   SHA256</span></span><br /><span data-ttu-id="43db5-137">-SHA512 olur</span><span class="sxs-lookup"><span data-stu-id="43db5-137">-   SHA512</span></span><br /><br /> <span data-ttu-id="43db5-138">Varsayılan değer SHA1 ' dır.</span><span class="sxs-lookup"><span data-stu-id="43db5-138">The default value is SHA1.</span></span> <span data-ttu-id="43db5-139">Bu öznitelik türü <xref:System.ServiceModel.MsmqSecureHashAlgorithm> .</span><span class="sxs-lookup"><span data-stu-id="43db5-139">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span><br><span data-ttu-id="43db5-140">MD5 ve SHA1 ile ilgili çarpışma sorunları nedeniyle, Microsoft SHA256 veya daha iyi bir performans öneriyor.</span><span class="sxs-lookup"><span data-stu-id="43db5-140">Due to collision problems with MD5 and SHA1, Microsoft recommends SHA256 or better.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="43db5-141">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="43db5-141">Child Elements</span></span>  

 <span data-ttu-id="43db5-142">Yok.</span><span class="sxs-lookup"><span data-stu-id="43db5-142">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="43db5-143">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="43db5-143">Parent Elements</span></span>  
  
|<span data-ttu-id="43db5-144">Öğe</span><span class="sxs-lookup"><span data-stu-id="43db5-144">Element</span></span>|<span data-ttu-id="43db5-145">Açıklama</span><span class="sxs-lookup"><span data-stu-id="43db5-145">Description</span></span>|  
|-------------|-----------------|  
|[\<msmqIntegration>](msmqintegration.md)|<span data-ttu-id="43db5-146">Message Queuing (MSMQ) gönderici veya alıcısıyla etkileşim için gereken ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="43db5-146">Specifies settings required for interaction with a Message Queuing (MSMQ) sender or receiver.</span></span>|  
|[\<msmqTransport>](msmqtransport.md)|<span data-ttu-id="43db5-147">Yerel MSMQ protokolünü kullanan bir Windows Communication Foundation (WCF) hizmeti için sıraya alma iletişim özelliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="43db5-147">Specifies the queuing communication properties for a Windows Communication Foundation (WCF) service that uses the native MSMQ protocol.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43db5-148">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="43db5-148">Remarks</span></span>  

 <span data-ttu-id="43db5-149">Taşıma güvenliği hakkında daha fazla bilgi için bkz. [Transport Security](../../../wcf/feature-details/transport-security.md).</span><span class="sxs-lookup"><span data-stu-id="43db5-149">For more information on transport security, see [Transport Security](../../../wcf/feature-details/transport-security.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43db5-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43db5-150">See also</span></span>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="43db5-151">WCF'de Kuyruklar</span><span class="sxs-lookup"><span data-stu-id="43db5-151">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="43db5-152">Taşımalar</span><span class="sxs-lookup"><span data-stu-id="43db5-152">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="43db5-153">Taşıma Seçme</span><span class="sxs-lookup"><span data-stu-id="43db5-153">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="43db5-154">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="43db5-154">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="43db5-155">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="43db5-155">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="43db5-156">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="43db5-156">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="43db5-157">Taşıma Güvenliği</span><span class="sxs-lookup"><span data-stu-id="43db5-157">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)

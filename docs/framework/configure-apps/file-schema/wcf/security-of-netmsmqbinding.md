---
description: 'Hakkında daha fazla bilgi <security> edinin: <netMsmqBinding>'
title: <security> / <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 001d11a9-7439-498c-b09d-fca20eaf8cd3
ms.openlocfilehash: 1b60d9e390e371555f4c3abf4988e79bb0f04fe8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786856"
---
# <a name="security-of-netmsmqbinding"></a><span data-ttu-id="e0240-103">\<security> / \<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="e0240-103">\<security> of \<netMsmqBinding></span></span>

<span data-ttu-id="e0240-104">MSMQ bağlamasının güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e0240-104">Defines the security settings for a MSMQ binding.</span></span> <span data-ttu-id="e0240-105">Aktarım veya SOAP güvenliğinin etkinleştirilip etkinleştirilmeyeceğini ve bu durumda hangi kimlik doğrulama modunun ve koruma düzeylerinin kullanımda olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e0240-105">It specifies whether transport or SOAP security is enabled and, if so, what authentication mode and protection levels are in use.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netMsmqBinding>**](netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="e0240-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="e0240-106">Syntax</span></span>  
  
```xml  
<security mode="None/Transport/Message/Both">
  <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"
             msmqEncryptionAlgorithm="RC4Stream/AES"
             msmqProtectionLevel="None/Sign/EncryptAndSign"
             msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
    <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
             clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e0240-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e0240-107">Attributes and Elements</span></span>  

 <span data-ttu-id="e0240-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e0240-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e0240-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e0240-109">Attributes</span></span>  
  
|<span data-ttu-id="e0240-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e0240-110">Attribute</span></span>|<span data-ttu-id="e0240-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e0240-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e0240-112">mod</span><span class="sxs-lookup"><span data-stu-id="e0240-112">mode</span></span>|<span data-ttu-id="e0240-113">Bütünlüğü, gizliliği ve kimlik doğrulamasını denetleyen güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="e0240-113">Specifies the type of security that controls integrity, confidentiality and authentication.</span></span> <span data-ttu-id="e0240-114">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e0240-114">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="e0240-115">-None: Bu, güvenliği devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="e0240-115">-   None: This disables security.</span></span><br /><span data-ttu-id="e0240-116">-Taşıma: koruma ve kimlik doğrulama, taşıma tarafından sunulur.</span><span class="sxs-lookup"><span data-stu-id="e0240-116">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="e0240-117">Bu, iki kuyruk yöneticisi arasındaki ileti güvenliği için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="e0240-117">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="e0240-118">Uygulama ve kuyruk Yöneticisi arasında bir güvenlik sunulmaz.</span><span class="sxs-lookup"><span data-stu-id="e0240-118">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="e0240-119">Mevcut MSMQ uygulamaları, bu tür güvenlik moduyla işlevsel olarak eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="e0240-119">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><span data-ttu-id="e0240-120">-Message: son son uygulama güvenliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e0240-120">-   Message: Specifies end-end application security.</span></span> <span data-ttu-id="e0240-121">Aktarım katmanında bir güvenlik sunulmaz.</span><span class="sxs-lookup"><span data-stu-id="e0240-121">There is no security offered at the transport layer.</span></span> <span data-ttu-id="e0240-122">Bu, diğer standart bağlamalar tarafından sunulan güvenliğe benzerdir.</span><span class="sxs-lookup"><span data-stu-id="e0240-122">This is similar to the security offered by other standard bindings.</span></span><br /><span data-ttu-id="e0240-123">-Her ikisi: hem aktarım hem de SOAP mesajlaşma katmanında güvenlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="e0240-123">-   Both: Offers security at both the transport and SOAP messaging layer.</span></span> <span data-ttu-id="e0240-124">Aynı kimlik bilgileri her iki düzeyde de gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e0240-124">The same credential is required at both the levels.</span></span><br /><br /> <span data-ttu-id="e0240-125">Varsayılan değer Aktarım ' dır.</span><span class="sxs-lookup"><span data-stu-id="e0240-125">The default value is Transport.</span></span> <span data-ttu-id="e0240-126">Bu öznitelik türü <xref:System.ServiceModel.NetMsmqSecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="e0240-126">This attribute is of type <xref:System.ServiceModel.NetMsmqSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e0240-127">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e0240-127">Child Elements</span></span>  
  
|<span data-ttu-id="e0240-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="e0240-128">Element</span></span>|<span data-ttu-id="e0240-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e0240-129">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-of-netmsmqbinding.md)|<span data-ttu-id="e0240-130">SOAP iletisi güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e0240-130">Defines the SOAP message security settings.</span></span> <span data-ttu-id="e0240-131">Bu öğe türündedir <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement> .</span><span class="sxs-lookup"><span data-stu-id="e0240-131">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>.</span></span>|  
|[\<transport>](transport-of-netmsmqbinding.md)|<span data-ttu-id="e0240-132">MSMQ taşıması için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e0240-132">Defines the security settings for the MSMQ transport.</span></span> <span data-ttu-id="e0240-133">Bu öğe türündedir <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="e0240-133">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e0240-134">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e0240-134">Parent Elements</span></span>  
  
|<span data-ttu-id="e0240-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="e0240-135">Element</span></span>|<span data-ttu-id="e0240-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e0240-136">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e0240-137">bağlama</span><span class="sxs-lookup"><span data-stu-id="e0240-137">binding</span></span>|<span data-ttu-id="e0240-138">Öğesinin bağlama öğesi [\<netMsmqBinding>](netmsmqbinding.md)</span><span class="sxs-lookup"><span data-stu-id="e0240-138">The binding element of the [\<netMsmqBinding>](netmsmqbinding.md)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e0240-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e0240-139">See also</span></span>

- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement>
- <xref:System.ServiceModel.NetMsmqBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetMsmqBindingElement.Security%2A>
- <xref:System.ServiceModel.NetMsmqSecurity>
- [<span data-ttu-id="e0240-140">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="e0240-140">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="e0240-141">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="e0240-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="e0240-142">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e0240-142">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="e0240-143">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="e0240-143">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- [<span data-ttu-id="e0240-144">WCF'de Kuyruklar</span><span class="sxs-lookup"><span data-stu-id="e0240-144">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)

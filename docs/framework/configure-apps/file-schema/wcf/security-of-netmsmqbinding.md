---
title: <security> / <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 001d11a9-7439-498c-b09d-fca20eaf8cd3
ms.openlocfilehash: 32b066fdf4d8edbbd36fdff7b14bdec87ddc970d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91170083"
---
# <a name="security-of-netmsmqbinding"></a><span data-ttu-id="234ba-102">\<security> / \<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="234ba-102">\<security> of \<netMsmqBinding></span></span>

<span data-ttu-id="234ba-103">MSMQ bağlamasının güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="234ba-103">Defines the security settings for a MSMQ binding.</span></span> <span data-ttu-id="234ba-104">Aktarım veya SOAP güvenliğinin etkinleştirilip etkinleştirilmeyeceğini ve bu durumda hangi kimlik doğrulama modunun ve koruma düzeylerinin kullanımda olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="234ba-104">It specifies whether transport or SOAP security is enabled and, if so, what authentication mode and protection levels are in use.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netMsmqBinding>**](netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="234ba-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="234ba-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="234ba-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="234ba-106">Attributes and Elements</span></span>  

 <span data-ttu-id="234ba-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="234ba-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="234ba-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="234ba-108">Attributes</span></span>  
  
|<span data-ttu-id="234ba-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="234ba-109">Attribute</span></span>|<span data-ttu-id="234ba-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="234ba-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="234ba-111">mod</span><span class="sxs-lookup"><span data-stu-id="234ba-111">mode</span></span>|<span data-ttu-id="234ba-112">Bütünlüğü, gizliliği ve kimlik doğrulamasını denetleyen güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="234ba-112">Specifies the type of security that controls integrity, confidentiality and authentication.</span></span> <span data-ttu-id="234ba-113">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="234ba-113">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="234ba-114">-None: Bu, güvenliği devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="234ba-114">-   None: This disables security.</span></span><br /><span data-ttu-id="234ba-115">-Taşıma: koruma ve kimlik doğrulama, taşıma tarafından sunulur.</span><span class="sxs-lookup"><span data-stu-id="234ba-115">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="234ba-116">Bu, iki kuyruk yöneticisi arasındaki ileti güvenliği için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="234ba-116">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="234ba-117">Uygulama ve kuyruk Yöneticisi arasında bir güvenlik sunulmaz.</span><span class="sxs-lookup"><span data-stu-id="234ba-117">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="234ba-118">Mevcut MSMQ uygulamaları, bu tür güvenlik moduyla işlevsel olarak eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="234ba-118">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><span data-ttu-id="234ba-119">-Message: son son uygulama güvenliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="234ba-119">-   Message: Specifies end-end application security.</span></span> <span data-ttu-id="234ba-120">Aktarım katmanında bir güvenlik sunulmaz.</span><span class="sxs-lookup"><span data-stu-id="234ba-120">There is no security offered at the transport layer.</span></span> <span data-ttu-id="234ba-121">Bu, diğer standart bağlamalar tarafından sunulan güvenliğe benzerdir.</span><span class="sxs-lookup"><span data-stu-id="234ba-121">This is similar to the security offered by other standard bindings.</span></span><br /><span data-ttu-id="234ba-122">-Her ikisi: hem aktarım hem de SOAP mesajlaşma katmanında güvenlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="234ba-122">-   Both: Offers security at both the transport and SOAP messaging layer.</span></span> <span data-ttu-id="234ba-123">Aynı kimlik bilgileri her iki düzeyde de gereklidir.</span><span class="sxs-lookup"><span data-stu-id="234ba-123">The same credential is required at both the levels.</span></span><br /><br /> <span data-ttu-id="234ba-124">Varsayılan değer Aktarım ' dır.</span><span class="sxs-lookup"><span data-stu-id="234ba-124">The default value is Transport.</span></span> <span data-ttu-id="234ba-125">Bu öznitelik türü <xref:System.ServiceModel.NetMsmqSecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="234ba-125">This attribute is of type <xref:System.ServiceModel.NetMsmqSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="234ba-126">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="234ba-126">Child Elements</span></span>  
  
|<span data-ttu-id="234ba-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="234ba-127">Element</span></span>|<span data-ttu-id="234ba-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="234ba-128">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-of-netmsmqbinding.md)|<span data-ttu-id="234ba-129">SOAP iletisi güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="234ba-129">Defines the SOAP message security settings.</span></span> <span data-ttu-id="234ba-130">Bu öğe türündedir <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement> .</span><span class="sxs-lookup"><span data-stu-id="234ba-130">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>.</span></span>|  
|[\<transport>](transport-of-netmsmqbinding.md)|<span data-ttu-id="234ba-131">MSMQ taşıması için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="234ba-131">Defines the security settings for the MSMQ transport.</span></span> <span data-ttu-id="234ba-132">Bu öğe türündedir <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="234ba-132">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="234ba-133">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="234ba-133">Parent Elements</span></span>  
  
|<span data-ttu-id="234ba-134">Öğe</span><span class="sxs-lookup"><span data-stu-id="234ba-134">Element</span></span>|<span data-ttu-id="234ba-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="234ba-135">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="234ba-136">bağlama</span><span class="sxs-lookup"><span data-stu-id="234ba-136">binding</span></span>|<span data-ttu-id="234ba-137">Öğesinin bağlama öğesi [\<netMsmqBinding>](netmsmqbinding.md)</span><span class="sxs-lookup"><span data-stu-id="234ba-137">The binding element of the [\<netMsmqBinding>](netmsmqbinding.md)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="234ba-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="234ba-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement>
- <xref:System.ServiceModel.NetMsmqBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetMsmqBindingElement.Security%2A>
- <xref:System.ServiceModel.NetMsmqSecurity>
- [<span data-ttu-id="234ba-139">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="234ba-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="234ba-140">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="234ba-140">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="234ba-141">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="234ba-141">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="234ba-142">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="234ba-142">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- [<span data-ttu-id="234ba-143">WCF'de Kuyruklar</span><span class="sxs-lookup"><span data-stu-id="234ba-143">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)

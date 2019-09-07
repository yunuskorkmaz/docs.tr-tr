---
title: <security> / <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 001d11a9-7439-498c-b09d-fca20eaf8cd3
ms.openlocfilehash: c780b157d0d566e24c6826c253401a51fbfab69d
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399836"
---
# <a name="security-of-netmsmqbinding"></a><span data-ttu-id="7fef4-102">\<\<NetMsmqBinding > Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="7fef4-102">\<security> of \<netMsmqBinding></span></span>
<span data-ttu-id="7fef4-103">MSMQ bağlamasının güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7fef4-103">Defines the security settings for a MSMQ binding.</span></span> <span data-ttu-id="7fef4-104">Aktarım veya SOAP güvenliğinin etkinleştirilip etkinleştirilmeyeceğini ve bu durumda hangi kimlik doğrulama modunun ve koruma düzeylerinin kullanımda olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="7fef4-104">It specifies whether transport or SOAP security is enabled and, if so, what authentication mode and protection levels are in use.</span></span>  
  
<span data-ttu-id="7fef4-105">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7fef4-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7fef4-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="7fef4-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="7fef4-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlama >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="7fef4-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="7fef4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netMsmqBinding >** ](netmsmqbinding.md)</span><span class="sxs-lookup"><span data-stu-id="7fef4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netMsmqBinding>**](netmsmqbinding.md)</span></span>\
<span data-ttu-id="7fef4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="7fef4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="7fef4-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Güvenlik >**</span><span class="sxs-lookup"><span data-stu-id="7fef4-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fef4-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7fef4-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7fef4-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7fef4-112">Attributes and Elements</span></span>  
 <span data-ttu-id="7fef4-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7fef4-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7fef4-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7fef4-114">Attributes</span></span>  
  
|<span data-ttu-id="7fef4-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7fef4-115">Attribute</span></span>|<span data-ttu-id="7fef4-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7fef4-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7fef4-117">mod</span><span class="sxs-lookup"><span data-stu-id="7fef4-117">mode</span></span>|<span data-ttu-id="7fef4-118">Bütünlüğü, gizliliği ve kimlik doğrulamasını denetleyen güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="7fef4-118">Specifies the type of security that controls integrity, confidentiality and authentication.</span></span> <span data-ttu-id="7fef4-119">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="7fef4-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="7fef4-120">Seçim Bu, güvenliği devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="7fef4-120">-   None: This disables security.</span></span><br /><span data-ttu-id="7fef4-121">Aktarım Koruma ve kimlik doğrulama, taşıma tarafından sunulur.</span><span class="sxs-lookup"><span data-stu-id="7fef4-121">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="7fef4-122">Bu, iki kuyruk yöneticisi arasındaki ileti güvenliği için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="7fef4-122">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="7fef4-123">Uygulama ve kuyruk Yöneticisi arasında bir güvenlik sunulmaz.</span><span class="sxs-lookup"><span data-stu-id="7fef4-123">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="7fef4-124">Mevcut MSMQ uygulamaları, bu tür güvenlik moduyla işlevsel olarak eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="7fef4-124">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><span data-ttu-id="7fef4-125">Mesaj Son uç uygulama güvenliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7fef4-125">-   Message: Specifies end-end application security.</span></span> <span data-ttu-id="7fef4-126">Aktarım katmanında bir güvenlik sunulmaz.</span><span class="sxs-lookup"><span data-stu-id="7fef4-126">There is no security offered at the transport layer.</span></span> <span data-ttu-id="7fef4-127">Bu, diğer standart bağlamalar tarafından sunulan güvenliğe benzerdir.</span><span class="sxs-lookup"><span data-stu-id="7fef4-127">This is similar to the security offered by other standard bindings.</span></span><br /><span data-ttu-id="7fef4-128">İs Hem aktarım hem de SOAP mesajlaşma katmanında güvenlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="7fef4-128">-   Both: Offers security at both the transport and SOAP messaging layer.</span></span> <span data-ttu-id="7fef4-129">Aynı kimlik bilgileri her iki düzeyde de gereklidir.</span><span class="sxs-lookup"><span data-stu-id="7fef4-129">The same credential is required at both the levels.</span></span><br /><br /> <span data-ttu-id="7fef4-130">Varsayılan değer Aktarım ' dır.</span><span class="sxs-lookup"><span data-stu-id="7fef4-130">The default value is Transport.</span></span> <span data-ttu-id="7fef4-131">Bu öznitelik türü <xref:System.ServiceModel.NetMsmqSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="7fef4-131">This attribute is of type <xref:System.ServiceModel.NetMsmqSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7fef4-132">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7fef4-132">Child Elements</span></span>  
  
|<span data-ttu-id="7fef4-133">Öğe</span><span class="sxs-lookup"><span data-stu-id="7fef4-133">Element</span></span>|<span data-ttu-id="7fef4-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7fef4-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7fef4-135">\<ileti ></span><span class="sxs-lookup"><span data-stu-id="7fef4-135">\<message></span></span>](message-of-netmsmqbinding.md)|<span data-ttu-id="7fef4-136">SOAP iletisi güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7fef4-136">Defines the SOAP message security settings.</span></span> <span data-ttu-id="7fef4-137">Bu öğe türündedir <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>.</span><span class="sxs-lookup"><span data-stu-id="7fef4-137">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>.</span></span>|  
|[<span data-ttu-id="7fef4-138">\<Taşıma ></span><span class="sxs-lookup"><span data-stu-id="7fef4-138">\<transport></span></span>](transport-of-netmsmqbinding.md)|<span data-ttu-id="7fef4-139">MSMQ taşıması için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7fef4-139">Defines the security settings for the MSMQ transport.</span></span> <span data-ttu-id="7fef4-140">Bu öğe türündedir <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="7fef4-140">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7fef4-141">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7fef4-141">Parent Elements</span></span>  
  
|<span data-ttu-id="7fef4-142">Öğe</span><span class="sxs-lookup"><span data-stu-id="7fef4-142">Element</span></span>|<span data-ttu-id="7fef4-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7fef4-143">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7fef4-144">bağlama</span><span class="sxs-lookup"><span data-stu-id="7fef4-144">binding</span></span>|<span data-ttu-id="7fef4-145">NetMsmqBinding > bağlama öğesi [ \<](netmsmqbinding.md)</span><span class="sxs-lookup"><span data-stu-id="7fef4-145">The binding element of the [\<netMsmqBinding>](netmsmqbinding.md)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7fef4-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7fef4-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement>
- <xref:System.ServiceModel.NetMsmqBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetMsmqBindingElement.Security%2A>
- <xref:System.ServiceModel.NetMsmqSecurity>
- [<span data-ttu-id="7fef4-147">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="7fef4-147">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="7fef4-148">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="7fef4-148">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="7fef4-149">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="7fef4-149">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="7fef4-150">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="7fef4-150">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="7fef4-151">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="7fef4-151">\<binding></span></span>](../../../misc/binding.md)
- [<span data-ttu-id="7fef4-152">WCF'de Kuyruklar</span><span class="sxs-lookup"><span data-stu-id="7fef4-152">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)

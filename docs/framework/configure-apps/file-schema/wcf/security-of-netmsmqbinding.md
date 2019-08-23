---
title: <security> / <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 001d11a9-7439-498c-b09d-fca20eaf8cd3
ms.openlocfilehash: 1bbc3a460ce707e71b72a469af2e03acd8dc79e5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936695"
---
# <a name="security-of-netmsmqbinding"></a><span data-ttu-id="21646-102">\<\<NetMsmqBinding > Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="21646-102">\<security> of \<netMsmqBinding></span></span>
<span data-ttu-id="21646-103">MSMQ bağlamasının güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="21646-103">Defines the security settings for a MSMQ binding.</span></span> <span data-ttu-id="21646-104">Aktarım veya SOAP güvenliğinin etkinleştirilip etkinleştirilmeyeceğini ve bu durumda hangi kimlik doğrulama modunun ve koruma düzeylerinin kullanımda olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="21646-104">It specifies whether transport or SOAP security is enabled and, if so, what authentication mode and protection levels are in use.</span></span>  
  
 <span data-ttu-id="21646-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="21646-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="21646-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="21646-106">\<bindings></span></span>  
<span data-ttu-id="21646-107">\<netMsmqBinding ></span><span class="sxs-lookup"><span data-stu-id="21646-107">\<netMsmqBinding></span></span>  
<span data-ttu-id="21646-108">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="21646-108">\<binding></span></span>  
<span data-ttu-id="21646-109">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="21646-109">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21646-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="21646-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="21646-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="21646-111">Attributes and Elements</span></span>  
 <span data-ttu-id="21646-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="21646-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="21646-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="21646-113">Attributes</span></span>  
  
|<span data-ttu-id="21646-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="21646-114">Attribute</span></span>|<span data-ttu-id="21646-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="21646-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="21646-116">mod</span><span class="sxs-lookup"><span data-stu-id="21646-116">mode</span></span>|<span data-ttu-id="21646-117">Bütünlüğü, gizliliği ve kimlik doğrulamasını denetleyen güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="21646-117">Specifies the type of security that controls integrity, confidentiality and authentication.</span></span> <span data-ttu-id="21646-118">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="21646-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="21646-119">Seçim Bu, güvenliği devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="21646-119">-   None: This disables security.</span></span><br /><span data-ttu-id="21646-120">Aktarım Koruma ve kimlik doğrulama, taşıma tarafından sunulur.</span><span class="sxs-lookup"><span data-stu-id="21646-120">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="21646-121">Bu, iki kuyruk yöneticisi arasındaki ileti güvenliği için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="21646-121">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="21646-122">Uygulama ve kuyruk Yöneticisi arasında bir güvenlik sunulmaz.</span><span class="sxs-lookup"><span data-stu-id="21646-122">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="21646-123">Mevcut MSMQ uygulamaları, bu tür güvenlik moduyla işlevsel olarak eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="21646-123">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><span data-ttu-id="21646-124">Mesaj Son uç uygulama güvenliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="21646-124">-   Message: Specifies end-end application security.</span></span> <span data-ttu-id="21646-125">Aktarım katmanında bir güvenlik sunulmaz.</span><span class="sxs-lookup"><span data-stu-id="21646-125">There is no security offered at the transport layer.</span></span> <span data-ttu-id="21646-126">Bu, diğer standart bağlamalar tarafından sunulan güvenliğe benzerdir.</span><span class="sxs-lookup"><span data-stu-id="21646-126">This is similar to the security offered by other standard bindings.</span></span><br /><span data-ttu-id="21646-127">İs Hem aktarım hem de SOAP mesajlaşma katmanında güvenlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="21646-127">-   Both: Offers security at both the transport and SOAP messaging layer.</span></span> <span data-ttu-id="21646-128">Aynı kimlik bilgileri her iki düzeyde de gereklidir.</span><span class="sxs-lookup"><span data-stu-id="21646-128">The same credential is required at both the levels.</span></span><br /><br /> <span data-ttu-id="21646-129">Varsayılan değer Aktarım ' dır.</span><span class="sxs-lookup"><span data-stu-id="21646-129">The default value is Transport.</span></span> <span data-ttu-id="21646-130">Bu öznitelik türü <xref:System.ServiceModel.NetMsmqSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="21646-130">This attribute is of type <xref:System.ServiceModel.NetMsmqSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="21646-131">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="21646-131">Child Elements</span></span>  
  
|<span data-ttu-id="21646-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="21646-132">Element</span></span>|<span data-ttu-id="21646-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="21646-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="21646-134">\<ileti ></span><span class="sxs-lookup"><span data-stu-id="21646-134">\<message></span></span>](message-of-netmsmqbinding.md)|<span data-ttu-id="21646-135">SOAP iletisi güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="21646-135">Defines the SOAP message security settings.</span></span> <span data-ttu-id="21646-136">Bu öğe türündedir <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>.</span><span class="sxs-lookup"><span data-stu-id="21646-136">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>.</span></span>|  
|[<span data-ttu-id="21646-137">\<Taşıma ></span><span class="sxs-lookup"><span data-stu-id="21646-137">\<transport></span></span>](transport-of-netmsmqbinding.md)|<span data-ttu-id="21646-138">MSMQ taşıması için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="21646-138">Defines the security settings for the MSMQ transport.</span></span> <span data-ttu-id="21646-139">Bu öğe türündedir <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="21646-139">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="21646-140">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="21646-140">Parent Elements</span></span>  
  
|<span data-ttu-id="21646-141">Öğe</span><span class="sxs-lookup"><span data-stu-id="21646-141">Element</span></span>|<span data-ttu-id="21646-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="21646-142">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="21646-143">bağlama</span><span class="sxs-lookup"><span data-stu-id="21646-143">binding</span></span>|<span data-ttu-id="21646-144">NetMsmqBinding > bağlama öğesi [ \<](netmsmqbinding.md)</span><span class="sxs-lookup"><span data-stu-id="21646-144">The binding element of the [\<netMsmqBinding>](netmsmqbinding.md)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="21646-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21646-145">See also</span></span>

- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement>
- <xref:System.ServiceModel.NetMsmqBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetMsmqBindingElement.Security%2A>
- <xref:System.ServiceModel.NetMsmqSecurity>
- [<span data-ttu-id="21646-146">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="21646-146">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="21646-147">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="21646-147">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="21646-148">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="21646-148">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="21646-149">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="21646-149">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="21646-150">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="21646-150">\<binding></span></span>](../../../misc/binding.md)
- [<span data-ttu-id="21646-151">WCF'de Kuyruklar</span><span class="sxs-lookup"><span data-stu-id="21646-151">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)

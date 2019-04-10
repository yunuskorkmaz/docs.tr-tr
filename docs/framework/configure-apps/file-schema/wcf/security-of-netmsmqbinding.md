---
title: <security> , <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 001d11a9-7439-498c-b09d-fca20eaf8cd3
ms.openlocfilehash: acb4d04663d841a9b494153caa180855959c145e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59206518"
---
# <a name="security-of-netmsmqbinding"></a><span data-ttu-id="a06bc-102">\<Güvenlik >, \<netMsmqBinding ></span><span class="sxs-lookup"><span data-stu-id="a06bc-102">\<security> of \<netMsmqBinding></span></span>
<span data-ttu-id="a06bc-103">MSMQ bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a06bc-103">Defines the security settings for a MSMQ binding.</span></span> <span data-ttu-id="a06bc-104">Bu aktarım veya SOAP Güvenliği etkinleştirilmiş ve bu durumda, hangi kimlik doğrulama modu ve koruma düzeyleri kullanımda olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a06bc-104">It specifies whether transport or SOAP security is enabled and, if so, what authentication mode and protection levels are in use.</span></span>  
  
 <span data-ttu-id="a06bc-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a06bc-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="a06bc-106">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="a06bc-106">\<bindings></span></span>  
<span data-ttu-id="a06bc-107">\<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="a06bc-107">\<netMsmqBinding></span></span>  
<span data-ttu-id="a06bc-108">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="a06bc-108">\<binding></span></span>  
<span data-ttu-id="a06bc-109">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="a06bc-109">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a06bc-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a06bc-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a06bc-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a06bc-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a06bc-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a06bc-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a06bc-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a06bc-113">Attributes</span></span>  
  
|<span data-ttu-id="a06bc-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a06bc-114">Attribute</span></span>|<span data-ttu-id="a06bc-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a06bc-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a06bc-116">mod</span><span class="sxs-lookup"><span data-stu-id="a06bc-116">mode</span></span>|<span data-ttu-id="a06bc-117">Bütünlüğü, gizlilik ve kimlik doğrulama denetimleri güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="a06bc-117">Specifies the type of security that controls integrity, confidentiality and authentication.</span></span> <span data-ttu-id="a06bc-118">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="a06bc-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="a06bc-119">-Yok: Bu güvenlik devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="a06bc-119">-   None: This disables security.</span></span><br /><span data-ttu-id="a06bc-120">-Taşıma: Koruma ve kimlik doğrulaması taşıma tarafından sunulmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a06bc-120">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="a06bc-121">Bu ileti güvenliği iki sıra yöneticileri arasında geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="a06bc-121">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="a06bc-122">Kuyruk Yöneticisi ve uygulama arasında sunulan güvenlik yoktur.</span><span class="sxs-lookup"><span data-stu-id="a06bc-122">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="a06bc-123">Msmq uygulamalara güvenlik modu bu tür işlevsel olarak eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="a06bc-123">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><span data-ttu-id="a06bc-124">-İleti: Uçtan uca uygulama güvenliği belirtir.</span><span class="sxs-lookup"><span data-stu-id="a06bc-124">-   Message: Specifies end-end application security.</span></span> <span data-ttu-id="a06bc-125">Aktarım katmanında sunulan güvenlik yoktur.</span><span class="sxs-lookup"><span data-stu-id="a06bc-125">There is no security offered at the transport layer.</span></span> <span data-ttu-id="a06bc-126">Bu, standart diğer bağlamalar tarafından sunulan güvenlik benzer.</span><span class="sxs-lookup"><span data-stu-id="a06bc-126">This is similar to the security offered by other standard bindings.</span></span><br /><span data-ttu-id="a06bc-127">-Hem: Hem aktarım hem de SOAP ileti katmanı güvenlik sunar.</span><span class="sxs-lookup"><span data-stu-id="a06bc-127">-   Both: Offers security at both the transport and SOAP messaging layer.</span></span> <span data-ttu-id="a06bc-128">Aynı kimlik bilgisini iki düzeyde gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a06bc-128">The same credential is required at both the levels.</span></span><br /><br /> <span data-ttu-id="a06bc-129">Aktarım varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="a06bc-129">The default value is Transport.</span></span> <span data-ttu-id="a06bc-130">Bu öznitelik türünde <xref:System.ServiceModel.NetMsmqSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="a06bc-130">This attribute is of type <xref:System.ServiceModel.NetMsmqSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a06bc-131">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a06bc-131">Child Elements</span></span>  
  
|<span data-ttu-id="a06bc-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="a06bc-132">Element</span></span>|<span data-ttu-id="a06bc-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a06bc-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a06bc-134">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="a06bc-134">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-netmsmqbinding.md)|<span data-ttu-id="a06bc-135">SOAP ileti güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a06bc-135">Defines the SOAP message security settings.</span></span> <span data-ttu-id="a06bc-136">Bu öğe türünde <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>.</span><span class="sxs-lookup"><span data-stu-id="a06bc-136">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>.</span></span>|  
|[<span data-ttu-id="a06bc-137">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="a06bc-137">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-netmsmqbinding.md)|<span data-ttu-id="a06bc-138">MSMQ taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a06bc-138">Defines the security settings for the MSMQ transport.</span></span> <span data-ttu-id="a06bc-139">Bu öğe türünde <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="a06bc-139">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a06bc-140">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a06bc-140">Parent Elements</span></span>  
  
|<span data-ttu-id="a06bc-141">Öğe</span><span class="sxs-lookup"><span data-stu-id="a06bc-141">Element</span></span>|<span data-ttu-id="a06bc-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a06bc-142">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a06bc-143">bağlama</span><span class="sxs-lookup"><span data-stu-id="a06bc-143">binding</span></span>|<span data-ttu-id="a06bc-144">Bağlama öğesi [ \<netMsmqBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)</span><span class="sxs-lookup"><span data-stu-id="a06bc-144">The binding element of the [\<netMsmqBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a06bc-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a06bc-145">See also</span></span>

- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement>
- <xref:System.ServiceModel.NetMsmqBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetMsmqBindingElement.Security%2A>
- <xref:System.ServiceModel.NetMsmqSecurity>
- [<span data-ttu-id="a06bc-146">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="a06bc-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="a06bc-147">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="a06bc-147">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="a06bc-148">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a06bc-148">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="a06bc-149">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="a06bc-149">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="a06bc-150">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="a06bc-150">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
- [<span data-ttu-id="a06bc-151">WCF'de Kuyruklar</span><span class="sxs-lookup"><span data-stu-id="a06bc-151">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)

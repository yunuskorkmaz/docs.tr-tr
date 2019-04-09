---
title: <security> , <msmqIntegrationBinding>
ms.date: 03/30/2017
ms.assetid: ae5c68a8-14a2-4c6e-b9e0-3e94e3e9135e
ms.openlocfilehash: 8d79523db2a1567283b934abbd3de1adbbe6b0b5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125794"
---
# <a name="security-of-msmqintegrationbinding"></a><span data-ttu-id="0b5a6-102">\<Güvenlik >, \<MsmqIntegrationBinding ></span><span class="sxs-lookup"><span data-stu-id="0b5a6-102">\<security> of \<msmqIntegrationBinding></span></span>
<span data-ttu-id="0b5a6-103">Message Queuing (MSMQ) tümleştirme kanal taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0b5a6-103">Defines the transport security settings for the Message Queuing (MSMQ) integration channel.</span></span>  
  
 <span data-ttu-id="0b5a6-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="0b5a6-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="0b5a6-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="0b5a6-105">\<bindings></span></span>  
<span data-ttu-id="0b5a6-106">msmqIntegrationBinding</span><span class="sxs-lookup"><span data-stu-id="0b5a6-106">msmqIntegrationBinding</span></span>  
<span data-ttu-id="0b5a6-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="0b5a6-107">\<binding></span></span>  
<span data-ttu-id="0b5a6-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="0b5a6-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b5a6-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0b5a6-109">Syntax</span></span>  
  
```xml  
<msmqIntegrationBinding>
  <binding>
    <security mode="None/Transport">
      <transport msmqAuthenticationMode="None/Windows/Certificate"
                 msmqEncryptionAlgorithm="RC4Stream/AES"
                 msmqProtectionLevel="None/Sign/EncryptAndSign"
                 msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
      <message algorithmSuite="Aes128/Aes192/Aes256/Rsa15Aes128/ Rsa15Aes256/TripleDes"
               clientCredentialType="None/Windows/UserName/Certificate/CardSpace"
               defaultProtectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</msmqIntegrationBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0b5a6-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0b5a6-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0b5a6-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0b5a6-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0b5a6-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0b5a6-112">Attributes</span></span>  
  
|<span data-ttu-id="0b5a6-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0b5a6-113">Attribute</span></span>|<span data-ttu-id="0b5a6-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0b5a6-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0b5a6-115">mod</span><span class="sxs-lookup"><span data-stu-id="0b5a6-115">mode</span></span>|<span data-ttu-id="0b5a6-116">Güvenlik türü bu denetimleri bütünlüğü, gizlilik ve kimlik doğrulaması ile Message Queuing tümleştirme kanalı belirtir.</span><span class="sxs-lookup"><span data-stu-id="0b5a6-116">Specifies the type of security that controls integrity, confidentiality and authentication with the Message Queuing integration channel.</span></span> <span data-ttu-id="0b5a6-117">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="0b5a6-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="0b5a6-118">-Yok: Bu güvenlik devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="0b5a6-118">-   None: This disables security.</span></span><br /><span data-ttu-id="0b5a6-119">-Taşıma: Koruma ve kimlik doğrulaması taşıma tarafından sunulmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0b5a6-119">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="0b5a6-120">Bu ileti güvenliği iki sıra yöneticileri arasında geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="0b5a6-120">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="0b5a6-121">Kuyruk Yöneticisi ve uygulama arasında sunulan güvenlik yoktur.</span><span class="sxs-lookup"><span data-stu-id="0b5a6-121">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="0b5a6-122">Msmq uygulamalara güvenlik modu bu tür işlevsel olarak eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="0b5a6-122">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><br /> <span data-ttu-id="0b5a6-123">Varsayılan değer `Transport` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="0b5a6-123">The default value is `Transport`.</span></span> <span data-ttu-id="0b5a6-124">Bu öznitelik türünde <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="0b5a6-124">This attribute is of type <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0b5a6-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0b5a6-125">Child Elements</span></span>  
  
|<span data-ttu-id="0b5a6-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="0b5a6-126">Element</span></span>|<span data-ttu-id="0b5a6-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0b5a6-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0b5a6-128">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="0b5a6-128">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-msmqintegrationbinding.md)|<span data-ttu-id="0b5a6-129">Message Queuing tümleştirme taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0b5a6-129">Defines the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="0b5a6-130">Bu öğe türünde <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="0b5a6-130">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0b5a6-131">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0b5a6-131">Parent Elements</span></span>  
  
|<span data-ttu-id="0b5a6-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="0b5a6-132">Element</span></span>|<span data-ttu-id="0b5a6-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0b5a6-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0b5a6-134">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="0b5a6-134">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="0b5a6-135">Bağlama öğesi [ \<MsmqIntegrationBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md).</span><span class="sxs-lookup"><span data-stu-id="0b5a6-135">The binding element of the [\<msmqIntegrationBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0b5a6-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b5a6-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationBindingElement.Security%2A>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- [<span data-ttu-id="0b5a6-137">WCF'de Kuyruklar</span><span class="sxs-lookup"><span data-stu-id="0b5a6-137">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="0b5a6-138">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="0b5a6-138">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="0b5a6-139">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="0b5a6-139">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="0b5a6-140">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="0b5a6-140">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="0b5a6-141">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="0b5a6-141">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="0b5a6-142">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="0b5a6-142">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
- [<span data-ttu-id="0b5a6-143">\<MsmqIntegrationBinding ></span><span class="sxs-lookup"><span data-stu-id="0b5a6-143">\<msmqIntegrationBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md)

---
title: <security> / <msmqIntegrationBinding>
ms.date: 03/30/2017
ms.assetid: ae5c68a8-14a2-4c6e-b9e0-3e94e3e9135e
ms.openlocfilehash: 8d79523db2a1567283b934abbd3de1adbbe6b0b5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61670540"
---
# <a name="security-of-msmqintegrationbinding"></a><span data-ttu-id="e2d2d-102">\<Güvenlik >, \<MsmqIntegrationBinding ></span><span class="sxs-lookup"><span data-stu-id="e2d2d-102">\<security> of \<msmqIntegrationBinding></span></span>
<span data-ttu-id="e2d2d-103">Message Queuing (MSMQ) tümleştirme kanal taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e2d2d-103">Defines the transport security settings for the Message Queuing (MSMQ) integration channel.</span></span>  
  
 <span data-ttu-id="e2d2d-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e2d2d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e2d2d-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="e2d2d-105">\<bindings></span></span>  
<span data-ttu-id="e2d2d-106">msmqIntegrationBinding</span><span class="sxs-lookup"><span data-stu-id="e2d2d-106">msmqIntegrationBinding</span></span>  
<span data-ttu-id="e2d2d-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="e2d2d-107">\<binding></span></span>  
<span data-ttu-id="e2d2d-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="e2d2d-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2d2d-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e2d2d-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e2d2d-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e2d2d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e2d2d-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e2d2d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e2d2d-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e2d2d-112">Attributes</span></span>  
  
|<span data-ttu-id="e2d2d-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e2d2d-113">Attribute</span></span>|<span data-ttu-id="e2d2d-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e2d2d-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e2d2d-115">mod</span><span class="sxs-lookup"><span data-stu-id="e2d2d-115">mode</span></span>|<span data-ttu-id="e2d2d-116">Güvenlik türü bu denetimleri bütünlüğü, gizlilik ve kimlik doğrulaması ile Message Queuing tümleştirme kanalı belirtir.</span><span class="sxs-lookup"><span data-stu-id="e2d2d-116">Specifies the type of security that controls integrity, confidentiality and authentication with the Message Queuing integration channel.</span></span> <span data-ttu-id="e2d2d-117">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e2d2d-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="e2d2d-118">-Yok: Bu güvenlik devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="e2d2d-118">-   None: This disables security.</span></span><br /><span data-ttu-id="e2d2d-119">-Taşıma: Koruma ve kimlik doğrulaması taşıma tarafından sunulmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e2d2d-119">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="e2d2d-120">Bu ileti güvenliği iki sıra yöneticileri arasında geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="e2d2d-120">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="e2d2d-121">Kuyruk Yöneticisi ve uygulama arasında sunulan güvenlik yoktur.</span><span class="sxs-lookup"><span data-stu-id="e2d2d-121">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="e2d2d-122">Msmq uygulamalara güvenlik modu bu tür işlevsel olarak eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="e2d2d-122">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><br /> <span data-ttu-id="e2d2d-123">Varsayılan değer `Transport` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="e2d2d-123">The default value is `Transport`.</span></span> <span data-ttu-id="e2d2d-124">Bu öznitelik türünde <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="e2d2d-124">This attribute is of type <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e2d2d-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e2d2d-125">Child Elements</span></span>  
  
|<span data-ttu-id="e2d2d-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="e2d2d-126">Element</span></span>|<span data-ttu-id="e2d2d-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e2d2d-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e2d2d-128">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="e2d2d-128">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-msmqintegrationbinding.md)|<span data-ttu-id="e2d2d-129">Message Queuing tümleştirme taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e2d2d-129">Defines the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="e2d2d-130">Bu öğe türünde <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="e2d2d-130">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e2d2d-131">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e2d2d-131">Parent Elements</span></span>  
  
|<span data-ttu-id="e2d2d-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="e2d2d-132">Element</span></span>|<span data-ttu-id="e2d2d-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e2d2d-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e2d2d-134">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="e2d2d-134">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="e2d2d-135">Bağlama öğesi [ \<MsmqIntegrationBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md).</span><span class="sxs-lookup"><span data-stu-id="e2d2d-135">The binding element of the [\<msmqIntegrationBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e2d2d-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2d2d-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationBindingElement.Security%2A>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- [<span data-ttu-id="e2d2d-137">WCF'de Kuyruklar</span><span class="sxs-lookup"><span data-stu-id="e2d2d-137">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="e2d2d-138">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="e2d2d-138">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="e2d2d-139">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="e2d2d-139">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="e2d2d-140">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e2d2d-140">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="e2d2d-141">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="e2d2d-141">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="e2d2d-142">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="e2d2d-142">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
- [<span data-ttu-id="e2d2d-143">\<MsmqIntegrationBinding ></span><span class="sxs-lookup"><span data-stu-id="e2d2d-143">\<msmqIntegrationBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md)

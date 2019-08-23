---
title: <security> / <msmqIntegrationBinding>
ms.date: 03/30/2017
ms.assetid: ae5c68a8-14a2-4c6e-b9e0-3e94e3e9135e
ms.openlocfilehash: 5b74c95ef2933fcf7e8d49aed89d95acbd288b80
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936703"
---
# <a name="security-of-msmqintegrationbinding"></a><span data-ttu-id="b7529-102">\<\<MsmqIntegrationBinding > Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="b7529-102">\<security> of \<msmqIntegrationBinding></span></span>
<span data-ttu-id="b7529-103">Message Queuing (MSMQ) tümleştirme kanalının taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b7529-103">Defines the transport security settings for the Message Queuing (MSMQ) integration channel.</span></span>  
  
 <span data-ttu-id="b7529-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b7529-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b7529-105">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="b7529-105">\<bindings></span></span>  
<span data-ttu-id="b7529-106">msmqIntegrationBinding</span><span class="sxs-lookup"><span data-stu-id="b7529-106">msmqIntegrationBinding</span></span>  
<span data-ttu-id="b7529-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="b7529-107">\<binding></span></span>  
<span data-ttu-id="b7529-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="b7529-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7529-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b7529-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b7529-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b7529-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b7529-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b7529-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b7529-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b7529-112">Attributes</span></span>  
  
|<span data-ttu-id="b7529-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b7529-113">Attribute</span></span>|<span data-ttu-id="b7529-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b7529-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b7529-115">mod</span><span class="sxs-lookup"><span data-stu-id="b7529-115">mode</span></span>|<span data-ttu-id="b7529-116">Message Queuing tümleştirme kanalı ile bütünlüğü, gizliliği ve kimlik doğrulamasını denetleyen güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="b7529-116">Specifies the type of security that controls integrity, confidentiality and authentication with the Message Queuing integration channel.</span></span> <span data-ttu-id="b7529-117">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="b7529-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="b7529-118">Seçim Bu, güvenliği devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="b7529-118">-   None: This disables security.</span></span><br /><span data-ttu-id="b7529-119">Aktarım Koruma ve kimlik doğrulama, taşıma tarafından sunulur.</span><span class="sxs-lookup"><span data-stu-id="b7529-119">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="b7529-120">Bu, iki kuyruk yöneticisi arasındaki ileti güvenliği için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b7529-120">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="b7529-121">Uygulama ve kuyruk Yöneticisi arasında bir güvenlik sunulmaz.</span><span class="sxs-lookup"><span data-stu-id="b7529-121">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="b7529-122">Mevcut MSMQ uygulamaları, bu tür güvenlik moduyla işlevsel olarak eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="b7529-122">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><br /> <span data-ttu-id="b7529-123">Varsayılan değer `Transport` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b7529-123">The default value is `Transport`.</span></span> <span data-ttu-id="b7529-124">Bu öznitelik türü <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="b7529-124">This attribute is of type <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b7529-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b7529-125">Child Elements</span></span>  
  
|<span data-ttu-id="b7529-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="b7529-126">Element</span></span>|<span data-ttu-id="b7529-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b7529-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b7529-128">\<Taşıma ></span><span class="sxs-lookup"><span data-stu-id="b7529-128">\<transport></span></span>](transport-of-msmqintegrationbinding.md)|<span data-ttu-id="b7529-129">Message Queuing tümleştirme taşıması için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b7529-129">Defines the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="b7529-130">Bu öğe türündedir <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="b7529-130">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b7529-131">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b7529-131">Parent Elements</span></span>  
  
|<span data-ttu-id="b7529-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="b7529-132">Element</span></span>|<span data-ttu-id="b7529-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b7529-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b7529-134">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="b7529-134">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="b7529-135">[ \<MsmqIntegrationBinding](msmqintegrationbinding.md)'in Binding öğesi >.</span><span class="sxs-lookup"><span data-stu-id="b7529-135">The binding element of the [\<msmqIntegrationBinding>](msmqintegrationbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b7529-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b7529-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationBindingElement.Security%2A>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- [<span data-ttu-id="b7529-137">WCF'de Kuyruklar</span><span class="sxs-lookup"><span data-stu-id="b7529-137">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="b7529-138">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="b7529-138">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="b7529-139">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="b7529-139">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b7529-140">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b7529-140">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="b7529-141">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="b7529-141">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="b7529-142">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="b7529-142">\<binding></span></span>](../../../misc/binding.md)
- [<span data-ttu-id="b7529-143">\<MsmqIntegrationBinding ></span><span class="sxs-lookup"><span data-stu-id="b7529-143">\<msmqIntegrationBinding></span></span>](msmqintegrationbinding.md)

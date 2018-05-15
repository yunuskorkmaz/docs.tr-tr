---
title: '&lt;netNamedPipeBinding&gt; &lt;güvenliği&gt;'
ms.date: 03/30/2017
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 74bf0d14b0acfd8a5382575d2ee1e51174b6b6b8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltsecuritygt-of-ltnetnamedpipebindinggt"></a><span data-ttu-id="e843f-102">&lt;netNamedPipeBinding&gt; &lt;güvenliği&gt;</span><span class="sxs-lookup"><span data-stu-id="e843f-102">&lt;security&gt; of &lt;netNamedPipeBinding&gt;</span></span>
<span data-ttu-id="e843f-103">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e843f-103">Defines the security settings for a binding.</span></span>  
  
 <span data-ttu-id="e843f-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e843f-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e843f-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="e843f-105">\<bindings></span></span>  
<span data-ttu-id="e843f-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="e843f-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="e843f-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="e843f-107">\<binding></span></span>  
<span data-ttu-id="e843f-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="e843f-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e843f-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e843f-109">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>  
      <binding>  
            <security mode="None/Transport">  
                        <transport protectionLevel="None/Sign/EncryptAndSign" />  
            </security>  
      </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e843f-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e843f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e843f-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e843f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e843f-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e843f-112">Attributes</span></span>  
  
|<span data-ttu-id="e843f-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e843f-113">Attribute</span></span>|<span data-ttu-id="e843f-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e843f-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e843f-115">mod</span><span class="sxs-lookup"><span data-stu-id="e843f-115">mode</span></span>|<span data-ttu-id="e843f-116">Bu bağlama uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="e843f-116">Specifies the type of security that is applied to this binding.</span></span> <span data-ttu-id="e843f-117">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e843f-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="e843f-118">-Hiçbiri: Bu güvenlik devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="e843f-118">-   None: This disables security.</span></span><br /><span data-ttu-id="e843f-119">-Taşıma: Güvenlik temel tabanlı taşıma güvenliği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="e843f-119">-   Transport: Security is provided using underlying transport based security.</span></span> <span data-ttu-id="e843f-120">Bu mod koruma düzeyiyle denetlemek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="e843f-120">It is possible to control the protection level with this mode.</span></span><br /><span data-ttu-id="e843f-121">-Taşıma varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="e843f-121">-   The default value is Transport.</span></span> <span data-ttu-id="e843f-122">Bu öznitelik türünde <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="e843f-122">This attribute is of type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e843f-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e843f-123">Child Elements</span></span>  
  
|<span data-ttu-id="e843f-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="e843f-124">Element</span></span>|<span data-ttu-id="e843f-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e843f-125">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e843f-126">taşıma</span><span class="sxs-lookup"><span data-stu-id="e843f-126">transport</span></span>|<span data-ttu-id="e843f-127">Taşıma için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e843f-127">Defines the security settings for the transport.</span></span> <span data-ttu-id="e843f-128">Bu öğe türünde <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="e843f-128">This element is of type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e843f-129">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e843f-129">Parent Elements</span></span>  
  
|<span data-ttu-id="e843f-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="e843f-130">Element</span></span>|<span data-ttu-id="e843f-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e843f-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e843f-132">bağlama</span><span class="sxs-lookup"><span data-stu-id="e843f-132">binding</span></span>|<span data-ttu-id="e843f-133">Bağlama öğesi [ \<netNamedPipeBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).</span><span class="sxs-lookup"><span data-stu-id="e843f-133">The binding element of the [\<netNamedPipeBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e843f-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e843f-134">See Also</span></span>  
 <xref:System.ServiceModel.NetNamedPipeSecurity>  
 <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>  
 [<span data-ttu-id="e843f-135">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="e843f-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="e843f-136">Kimlik Bilgisi Türü Seçme</span><span class="sxs-lookup"><span data-stu-id="e843f-136">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="e843f-137">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="e843f-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="e843f-138">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e843f-138">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="e843f-139">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="e843f-139">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="e843f-140">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="e843f-140">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)

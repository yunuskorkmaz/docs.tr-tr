---
title: "&lt;netNamedPipeBinding&gt; &lt;güvenliği&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
caps.latest.revision: "11"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: efb6289c63cdc98402336949ef5916e7568775a8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltsecuritygt-of-ltnetnamedpipebindinggt"></a><span data-ttu-id="6b434-102">&lt;netNamedPipeBinding&gt; &lt;güvenliği&gt;</span><span class="sxs-lookup"><span data-stu-id="6b434-102">&lt;security&gt; of &lt;netNamedPipeBinding&gt;</span></span>
<span data-ttu-id="6b434-103">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6b434-103">Defines the security settings for a binding.</span></span>  
  
 <span data-ttu-id="6b434-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="6b434-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="6b434-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="6b434-105">\<bindings></span></span>  
<span data-ttu-id="6b434-106">\<netNamedPipeBinding ></span><span class="sxs-lookup"><span data-stu-id="6b434-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="6b434-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="6b434-107">\<binding></span></span>  
<span data-ttu-id="6b434-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="6b434-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b434-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6b434-109">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>  
      <binding>  
            <security mode="None/Transport">  
                        <transport protectionLevel="None/Sign/EncryptAndSign" />  
            </security>  
      </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6b434-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6b434-110">Attributes and Elements</span></span>  
 <span data-ttu-id="6b434-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6b434-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6b434-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6b434-112">Attributes</span></span>  
  
|<span data-ttu-id="6b434-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6b434-113">Attribute</span></span>|<span data-ttu-id="6b434-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6b434-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6b434-115">mod</span><span class="sxs-lookup"><span data-stu-id="6b434-115">mode</span></span>|<span data-ttu-id="6b434-116">Bu bağlama uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="6b434-116">Specifies the type of security that is applied to this binding.</span></span> <span data-ttu-id="6b434-117">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="6b434-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="6b434-118">-Hiçbiri: Bu güvenlik devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="6b434-118">-   None: This disables security.</span></span><br /><span data-ttu-id="6b434-119">-Taşıma: Güvenlik temel tabanlı taşıma güvenliği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="6b434-119">-   Transport: Security is provided using underlying transport based security.</span></span> <span data-ttu-id="6b434-120">Bu mod koruma düzeyiyle denetlemek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="6b434-120">It is possible to control the protection level with this mode.</span></span><br /><span data-ttu-id="6b434-121">-Taşıma varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="6b434-121">-   The default value is Transport.</span></span> <span data-ttu-id="6b434-122">Bu öznitelik türünde <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="6b434-122">This attribute is of type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6b434-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6b434-123">Child Elements</span></span>  
  
|<span data-ttu-id="6b434-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="6b434-124">Element</span></span>|<span data-ttu-id="6b434-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6b434-125">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6b434-126">taşıma</span><span class="sxs-lookup"><span data-stu-id="6b434-126">transport</span></span>|<span data-ttu-id="6b434-127">Taşıma için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6b434-127">Defines the security settings for the transport.</span></span> <span data-ttu-id="6b434-128">Bu öğe türünde <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="6b434-128">This element is of type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6b434-129">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6b434-129">Parent Elements</span></span>  
  
|<span data-ttu-id="6b434-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="6b434-130">Element</span></span>|<span data-ttu-id="6b434-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6b434-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6b434-132">bağlama</span><span class="sxs-lookup"><span data-stu-id="6b434-132">binding</span></span>|<span data-ttu-id="6b434-133">Bağlama öğesi [ \<netNamedPipeBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).</span><span class="sxs-lookup"><span data-stu-id="6b434-133">The binding element of the [\<netNamedPipeBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6b434-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6b434-134">See Also</span></span>  
 <xref:System.ServiceModel.NetNamedPipeSecurity>  
 <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>  
 [<span data-ttu-id="6b434-135">Hizmetler ve istemcileri güvenli hale getirme</span><span class="sxs-lookup"><span data-stu-id="6b434-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="6b434-136">Bir kimlik bilgisi türü seçme</span><span class="sxs-lookup"><span data-stu-id="6b434-136">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="6b434-137">Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="6b434-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="6b434-138">Sistem tarafından sağlanan bağlamaları yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6b434-138">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="6b434-139">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="6b434-139">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="6b434-140">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="6b434-140">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)

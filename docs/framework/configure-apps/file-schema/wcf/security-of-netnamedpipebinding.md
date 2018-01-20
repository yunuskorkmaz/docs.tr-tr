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
ms.workload: dotnet
ms.openlocfilehash: 3a018c502aead84eb6936001acb5bc24c59188f8
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="ltsecuritygt-of-ltnetnamedpipebindinggt"></a><span data-ttu-id="f2eb2-102">&lt;netNamedPipeBinding&gt; &lt;güvenliği&gt;</span><span class="sxs-lookup"><span data-stu-id="f2eb2-102">&lt;security&gt; of &lt;netNamedPipeBinding&gt;</span></span>
<span data-ttu-id="f2eb2-103">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f2eb2-103">Defines the security settings for a binding.</span></span>  
  
 <span data-ttu-id="f2eb2-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f2eb2-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f2eb2-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="f2eb2-105">\<bindings></span></span>  
<span data-ttu-id="f2eb2-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="f2eb2-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="f2eb2-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="f2eb2-107">\<binding></span></span>  
<span data-ttu-id="f2eb2-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="f2eb2-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2eb2-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f2eb2-109">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>  
      <binding>  
            <security mode="None/Transport">  
                        <transport protectionLevel="None/Sign/EncryptAndSign" />  
            </security>  
      </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f2eb2-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f2eb2-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f2eb2-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f2eb2-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f2eb2-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f2eb2-112">Attributes</span></span>  
  
|<span data-ttu-id="f2eb2-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f2eb2-113">Attribute</span></span>|<span data-ttu-id="f2eb2-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f2eb2-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f2eb2-115">mod</span><span class="sxs-lookup"><span data-stu-id="f2eb2-115">mode</span></span>|<span data-ttu-id="f2eb2-116">Bu bağlama uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="f2eb2-116">Specifies the type of security that is applied to this binding.</span></span> <span data-ttu-id="f2eb2-117">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f2eb2-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="f2eb2-118">-Hiçbiri: Bu güvenlik devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="f2eb2-118">-   None: This disables security.</span></span><br /><span data-ttu-id="f2eb2-119">-Taşıma: Güvenlik temel tabanlı taşıma güvenliği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="f2eb2-119">-   Transport: Security is provided using underlying transport based security.</span></span> <span data-ttu-id="f2eb2-120">Bu mod koruma düzeyiyle denetlemek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="f2eb2-120">It is possible to control the protection level with this mode.</span></span><br /><span data-ttu-id="f2eb2-121">-Taşıma varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="f2eb2-121">-   The default value is Transport.</span></span> <span data-ttu-id="f2eb2-122">Bu öznitelik türünde <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="f2eb2-122">This attribute is of type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f2eb2-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f2eb2-123">Child Elements</span></span>  
  
|<span data-ttu-id="f2eb2-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="f2eb2-124">Element</span></span>|<span data-ttu-id="f2eb2-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f2eb2-125">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f2eb2-126">taşıma</span><span class="sxs-lookup"><span data-stu-id="f2eb2-126">transport</span></span>|<span data-ttu-id="f2eb2-127">Taşıma için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f2eb2-127">Defines the security settings for the transport.</span></span> <span data-ttu-id="f2eb2-128">Bu öğe türünde <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="f2eb2-128">This element is of type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f2eb2-129">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f2eb2-129">Parent Elements</span></span>  
  
|<span data-ttu-id="f2eb2-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="f2eb2-130">Element</span></span>|<span data-ttu-id="f2eb2-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f2eb2-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f2eb2-132">bağlama</span><span class="sxs-lookup"><span data-stu-id="f2eb2-132">binding</span></span>|<span data-ttu-id="f2eb2-133">Bağlama öğesi [ \<netNamedPipeBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).</span><span class="sxs-lookup"><span data-stu-id="f2eb2-133">The binding element of the [\<netNamedPipeBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f2eb2-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f2eb2-134">See Also</span></span>  
 <xref:System.ServiceModel.NetNamedPipeSecurity>  
 <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>  
 [<span data-ttu-id="f2eb2-135">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="f2eb2-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="f2eb2-136">Kimlik Bilgisi Türü Seçme</span><span class="sxs-lookup"><span data-stu-id="f2eb2-136">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="f2eb2-137">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="f2eb2-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="f2eb2-138">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f2eb2-138">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="f2eb2-139">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="f2eb2-139">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="f2eb2-140">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="f2eb2-140">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)

---
title: '&lt;netNamedPipeBinding&gt; &lt;güvenliği&gt;'
ms.date: 03/30/2017
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
author: BrucePerlerMS
ms.openlocfilehash: eee4cc13b5181caa4449c3ad6ebc5247cc7e0f1a
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47077063"
---
# <a name="ltsecuritygt-of-ltnetnamedpipebindinggt"></a><span data-ttu-id="e2055-102">&lt;netNamedPipeBinding&gt; &lt;güvenliği&gt;</span><span class="sxs-lookup"><span data-stu-id="e2055-102">&lt;security&gt; of &lt;netNamedPipeBinding&gt;</span></span>
<span data-ttu-id="e2055-103">Bir bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e2055-103">Defines the security settings for a binding.</span></span>  
  
 <span data-ttu-id="e2055-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e2055-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e2055-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="e2055-105">\<bindings></span></span>  
<span data-ttu-id="e2055-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="e2055-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="e2055-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="e2055-107">\<binding></span></span>  
<span data-ttu-id="e2055-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="e2055-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2055-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e2055-109">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>  
      <binding>  
            <security mode="None/Transport">  
                        <transport protectionLevel="None/Sign/EncryptAndSign" />  
            </security>  
      </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e2055-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e2055-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e2055-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e2055-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e2055-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e2055-112">Attributes</span></span>  
  
|<span data-ttu-id="e2055-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e2055-113">Attribute</span></span>|<span data-ttu-id="e2055-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e2055-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e2055-115">mod</span><span class="sxs-lookup"><span data-stu-id="e2055-115">mode</span></span>|<span data-ttu-id="e2055-116">Bu bağlama için uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="e2055-116">Specifies the type of security that is applied to this binding.</span></span> <span data-ttu-id="e2055-117">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e2055-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="e2055-118">-Yok: Bu güvenlik devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="e2055-118">-   None: This disables security.</span></span><br /><span data-ttu-id="e2055-119">-Taşıma: Temel alınan temel aktarım güvenliği kullanarak güvenliği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="e2055-119">-   Transport: Security is provided using underlying transport based security.</span></span> <span data-ttu-id="e2055-120">Bu mod koruma düzeyiyle denetlemek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="e2055-120">It is possible to control the protection level with this mode.</span></span><br /><span data-ttu-id="e2055-121">-Aktarım varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="e2055-121">-   The default value is Transport.</span></span> <span data-ttu-id="e2055-122">Bu öznitelik türünde <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="e2055-122">This attribute is of type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e2055-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e2055-123">Child Elements</span></span>  
  
|<span data-ttu-id="e2055-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="e2055-124">Element</span></span>|<span data-ttu-id="e2055-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e2055-125">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e2055-126">taşıma</span><span class="sxs-lookup"><span data-stu-id="e2055-126">transport</span></span>|<span data-ttu-id="e2055-127">Taşıma için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e2055-127">Defines the security settings for the transport.</span></span> <span data-ttu-id="e2055-128">Bu öğe türünde <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="e2055-128">This element is of type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e2055-129">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e2055-129">Parent Elements</span></span>  
  
|<span data-ttu-id="e2055-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="e2055-130">Element</span></span>|<span data-ttu-id="e2055-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e2055-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e2055-132">bağlama</span><span class="sxs-lookup"><span data-stu-id="e2055-132">binding</span></span>|<span data-ttu-id="e2055-133">Bağlama öğesi [ \<netNamedPipeBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).</span><span class="sxs-lookup"><span data-stu-id="e2055-133">The binding element of the [\<netNamedPipeBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e2055-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e2055-134">See Also</span></span>  
 <xref:System.ServiceModel.NetNamedPipeSecurity>  
 <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>  
 [<span data-ttu-id="e2055-135">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="e2055-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="e2055-136">Kimlik Bilgisi Türü Seçme</span><span class="sxs-lookup"><span data-stu-id="e2055-136">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="e2055-137">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="e2055-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="e2055-138">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e2055-138">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="e2055-139">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="e2055-139">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="e2055-140">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="e2055-140">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)

---
title: '&lt;netNamedPipeBinding&gt; &lt;güvenliği&gt;'
ms.date: 03/30/2017
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
author: BrucePerlerMS
ms.openlocfilehash: e1c93fc344ea4c7dd3b801c876d59c9a799baf44
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48835823"
---
# <a name="ltsecuritygt-of-ltnetnamedpipebindinggt"></a><span data-ttu-id="74fa9-102">&lt;netNamedPipeBinding&gt; &lt;güvenliği&gt;</span><span class="sxs-lookup"><span data-stu-id="74fa9-102">&lt;security&gt; of &lt;netNamedPipeBinding&gt;</span></span>
<span data-ttu-id="74fa9-103">Bir bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="74fa9-103">Defines the security settings for a binding.</span></span>  
  
 <span data-ttu-id="74fa9-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="74fa9-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="74fa9-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="74fa9-105">\<bindings></span></span>  
<span data-ttu-id="74fa9-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="74fa9-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="74fa9-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="74fa9-107">\<binding></span></span>  
<span data-ttu-id="74fa9-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="74fa9-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74fa9-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="74fa9-109">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>  
      <binding>  
            <security mode="None/Transport">  
                        <transport protectionLevel="None/Sign/EncryptAndSign" />  
            </security>  
      </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="74fa9-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="74fa9-110">Attributes and Elements</span></span>  
 <span data-ttu-id="74fa9-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="74fa9-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="74fa9-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="74fa9-112">Attributes</span></span>  
  
|<span data-ttu-id="74fa9-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="74fa9-113">Attribute</span></span>|<span data-ttu-id="74fa9-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="74fa9-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="74fa9-115">mod</span><span class="sxs-lookup"><span data-stu-id="74fa9-115">mode</span></span>|<span data-ttu-id="74fa9-116">Bu bağlama için uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="74fa9-116">Specifies the type of security that is applied to this binding.</span></span> <span data-ttu-id="74fa9-117">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="74fa9-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="74fa9-118">-Yok: Bu güvenlik devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="74fa9-118">-   None: This disables security.</span></span><br /><span data-ttu-id="74fa9-119">-Taşıma: Temel alınan temel aktarım güvenliği kullanarak güvenliği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="74fa9-119">-   Transport: Security is provided using underlying transport based security.</span></span> <span data-ttu-id="74fa9-120">Bu mod koruma düzeyiyle denetlemek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="74fa9-120">It is possible to control the protection level with this mode.</span></span><br /><span data-ttu-id="74fa9-121">-Aktarım varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="74fa9-121">-   The default value is Transport.</span></span> <span data-ttu-id="74fa9-122">Bu öznitelik türünde <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="74fa9-122">This attribute is of type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="74fa9-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="74fa9-123">Child Elements</span></span>  
  
|<span data-ttu-id="74fa9-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="74fa9-124">Element</span></span>|<span data-ttu-id="74fa9-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="74fa9-125">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="74fa9-126">taşıma</span><span class="sxs-lookup"><span data-stu-id="74fa9-126">transport</span></span>|<span data-ttu-id="74fa9-127">Taşıma için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="74fa9-127">Defines the security settings for the transport.</span></span> <span data-ttu-id="74fa9-128">Bu öğe türünde <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="74fa9-128">This element is of type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="74fa9-129">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="74fa9-129">Parent Elements</span></span>  
  
|<span data-ttu-id="74fa9-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="74fa9-130">Element</span></span>|<span data-ttu-id="74fa9-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="74fa9-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="74fa9-132">bağlama</span><span class="sxs-lookup"><span data-stu-id="74fa9-132">binding</span></span>|<span data-ttu-id="74fa9-133">Bağlama öğesi [ \<netNamedPipeBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).</span><span class="sxs-lookup"><span data-stu-id="74fa9-133">The binding element of the [\<netNamedPipeBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="74fa9-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="74fa9-134">See Also</span></span>  
 <xref:System.ServiceModel.NetNamedPipeSecurity>  
 <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>  
 [<span data-ttu-id="74fa9-135">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="74fa9-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="74fa9-136">Kimlik Bilgisi Türü Seçme</span><span class="sxs-lookup"><span data-stu-id="74fa9-136">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="74fa9-137">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="74fa9-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="74fa9-138">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="74fa9-138">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="74fa9-139">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="74fa9-139">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="74fa9-140">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="74fa9-140">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)

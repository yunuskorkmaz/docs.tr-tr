---
title: '&lt;netNamedPipeBinding&gt; &lt;güvenliği&gt;'
ms.date: 03/30/2017
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 0e5a22d6e517bc7a05f74089b7c8ece8c8a4bd39
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43558678"
---
# <a name="ltsecuritygt-of-ltnetnamedpipebindinggt"></a><span data-ttu-id="70d09-102">&lt;netNamedPipeBinding&gt; &lt;güvenliği&gt;</span><span class="sxs-lookup"><span data-stu-id="70d09-102">&lt;security&gt; of &lt;netNamedPipeBinding&gt;</span></span>
<span data-ttu-id="70d09-103">Bir bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="70d09-103">Defines the security settings for a binding.</span></span>  
  
 <span data-ttu-id="70d09-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="70d09-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="70d09-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="70d09-105">\<bindings></span></span>  
<span data-ttu-id="70d09-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="70d09-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="70d09-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="70d09-107">\<binding></span></span>  
<span data-ttu-id="70d09-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="70d09-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70d09-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="70d09-109">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>  
      <binding>  
            <security mode="None/Transport">  
                        <transport protectionLevel="None/Sign/EncryptAndSign" />  
            </security>  
      </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="70d09-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="70d09-110">Attributes and Elements</span></span>  
 <span data-ttu-id="70d09-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="70d09-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="70d09-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="70d09-112">Attributes</span></span>  
  
|<span data-ttu-id="70d09-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="70d09-113">Attribute</span></span>|<span data-ttu-id="70d09-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="70d09-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="70d09-115">mod</span><span class="sxs-lookup"><span data-stu-id="70d09-115">mode</span></span>|<span data-ttu-id="70d09-116">Bu bağlama için uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="70d09-116">Specifies the type of security that is applied to this binding.</span></span> <span data-ttu-id="70d09-117">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="70d09-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="70d09-118">-Yok: Bu güvenlik devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="70d09-118">-   None: This disables security.</span></span><br /><span data-ttu-id="70d09-119">-Taşıma: Temel alınan temel aktarım güvenliği kullanarak güvenliği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="70d09-119">-   Transport: Security is provided using underlying transport based security.</span></span> <span data-ttu-id="70d09-120">Bu mod koruma düzeyiyle denetlemek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="70d09-120">It is possible to control the protection level with this mode.</span></span><br /><span data-ttu-id="70d09-121">-Aktarım varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="70d09-121">-   The default value is Transport.</span></span> <span data-ttu-id="70d09-122">Bu öznitelik türünde <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="70d09-122">This attribute is of type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="70d09-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="70d09-123">Child Elements</span></span>  
  
|<span data-ttu-id="70d09-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="70d09-124">Element</span></span>|<span data-ttu-id="70d09-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="70d09-125">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="70d09-126">taşıma</span><span class="sxs-lookup"><span data-stu-id="70d09-126">transport</span></span>|<span data-ttu-id="70d09-127">Taşıma için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="70d09-127">Defines the security settings for the transport.</span></span> <span data-ttu-id="70d09-128">Bu öğe türünde <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="70d09-128">This element is of type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="70d09-129">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="70d09-129">Parent Elements</span></span>  
  
|<span data-ttu-id="70d09-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="70d09-130">Element</span></span>|<span data-ttu-id="70d09-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="70d09-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="70d09-132">bağlama</span><span class="sxs-lookup"><span data-stu-id="70d09-132">binding</span></span>|<span data-ttu-id="70d09-133">Bağlama öğesi [ \<netNamedPipeBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).</span><span class="sxs-lookup"><span data-stu-id="70d09-133">The binding element of the [\<netNamedPipeBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="70d09-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="70d09-134">See Also</span></span>  
 <xref:System.ServiceModel.NetNamedPipeSecurity>  
 <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>  
 [<span data-ttu-id="70d09-135">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="70d09-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="70d09-136">Kimlik Bilgisi Türü Seçme</span><span class="sxs-lookup"><span data-stu-id="70d09-136">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="70d09-137">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="70d09-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="70d09-138">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="70d09-138">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="70d09-139">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="70d09-139">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="70d09-140">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="70d09-140">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)

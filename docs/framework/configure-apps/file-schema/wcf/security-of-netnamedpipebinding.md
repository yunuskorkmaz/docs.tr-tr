---
title: <security> / <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
ms.openlocfilehash: 0996a98438dc344d96d640abced52ac99709adbf
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936682"
---
# <a name="security-of-netnamedpipebinding"></a><span data-ttu-id="659c9-102">\<\<NetNamedPipeBinding > Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="659c9-102">\<security> of \<netNamedPipeBinding></span></span>
<span data-ttu-id="659c9-103">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="659c9-103">Defines the security settings for a binding.</span></span>  
  
 <span data-ttu-id="659c9-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="659c9-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="659c9-105">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="659c9-105">\<bindings></span></span>  
<span data-ttu-id="659c9-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="659c9-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="659c9-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="659c9-107">\<binding></span></span>  
<span data-ttu-id="659c9-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="659c9-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="659c9-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="659c9-109">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="659c9-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="659c9-110">Attributes and Elements</span></span>  
 <span data-ttu-id="659c9-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="659c9-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="659c9-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="659c9-112">Attributes</span></span>  
  
|<span data-ttu-id="659c9-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="659c9-113">Attribute</span></span>|<span data-ttu-id="659c9-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="659c9-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="659c9-115">mod</span><span class="sxs-lookup"><span data-stu-id="659c9-115">mode</span></span>|<span data-ttu-id="659c9-116">Bu bağlamaya uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="659c9-116">Specifies the type of security that is applied to this binding.</span></span> <span data-ttu-id="659c9-117">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="659c9-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="659c9-118">Seçim Bu, güvenliği devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="659c9-118">-   None: This disables security.</span></span><br /><span data-ttu-id="659c9-119">Aktarım Güvenlik, temel alınan aktarım tabanlı güvenlik kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="659c9-119">-   Transport: Security is provided using underlying transport based security.</span></span> <span data-ttu-id="659c9-120">Koruma düzeyini Bu modla denetlemek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="659c9-120">It is possible to control the protection level with this mode.</span></span><br /><span data-ttu-id="659c9-121">-Varsayılan değer Transport ' dır.</span><span class="sxs-lookup"><span data-stu-id="659c9-121">-   The default value is Transport.</span></span> <span data-ttu-id="659c9-122">Bu öznitelik türü <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="659c9-122">This attribute is of type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="659c9-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="659c9-123">Child Elements</span></span>  
  
|<span data-ttu-id="659c9-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="659c9-124">Element</span></span>|<span data-ttu-id="659c9-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="659c9-125">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="659c9-126">taşıma</span><span class="sxs-lookup"><span data-stu-id="659c9-126">transport</span></span>|<span data-ttu-id="659c9-127">Taşımanın güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="659c9-127">Defines the security settings for the transport.</span></span> <span data-ttu-id="659c9-128">Bu öğe türündedir <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="659c9-128">This element is of type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="659c9-129">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="659c9-129">Parent Elements</span></span>  
  
|<span data-ttu-id="659c9-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="659c9-130">Element</span></span>|<span data-ttu-id="659c9-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="659c9-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="659c9-132">bağlama</span><span class="sxs-lookup"><span data-stu-id="659c9-132">binding</span></span>|<span data-ttu-id="659c9-133">[ \<NetNamedPipeBinding](netnamedpipebinding.md)'in Binding öğesi >.</span><span class="sxs-lookup"><span data-stu-id="659c9-133">The binding element of the [\<netNamedPipeBinding>](netnamedpipebinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="659c9-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="659c9-134">See also</span></span>

- <xref:System.ServiceModel.NetNamedPipeSecurity>
- <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>
- [<span data-ttu-id="659c9-135">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="659c9-135">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="659c9-136">Kimlik Bilgisi Türü Seçme</span><span class="sxs-lookup"><span data-stu-id="659c9-136">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="659c9-137">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="659c9-137">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="659c9-138">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="659c9-138">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="659c9-139">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="659c9-139">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="659c9-140">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="659c9-140">\<binding></span></span>](../../../misc/binding.md)

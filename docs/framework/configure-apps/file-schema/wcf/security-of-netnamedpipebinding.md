---
title: <security> / <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
ms.openlocfilehash: fa31dda3274c9768694bdf5232f31554899e1d82
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61670527"
---
# <a name="security-of-netnamedpipebinding"></a><span data-ttu-id="b1ae0-102">\<Güvenlik >, \<netNamedPipeBinding ></span><span class="sxs-lookup"><span data-stu-id="b1ae0-102">\<security> of \<netNamedPipeBinding></span></span>
<span data-ttu-id="b1ae0-103">Bir bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b1ae0-103">Defines the security settings for a binding.</span></span>  
  
 <span data-ttu-id="b1ae0-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b1ae0-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b1ae0-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="b1ae0-105">\<bindings></span></span>  
<span data-ttu-id="b1ae0-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="b1ae0-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="b1ae0-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="b1ae0-107">\<binding></span></span>  
<span data-ttu-id="b1ae0-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="b1ae0-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1ae0-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b1ae0-109">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b1ae0-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b1ae0-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b1ae0-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b1ae0-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b1ae0-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b1ae0-112">Attributes</span></span>  
  
|<span data-ttu-id="b1ae0-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b1ae0-113">Attribute</span></span>|<span data-ttu-id="b1ae0-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b1ae0-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b1ae0-115">mod</span><span class="sxs-lookup"><span data-stu-id="b1ae0-115">mode</span></span>|<span data-ttu-id="b1ae0-116">Bu bağlama için uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="b1ae0-116">Specifies the type of security that is applied to this binding.</span></span> <span data-ttu-id="b1ae0-117">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="b1ae0-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="b1ae0-118">-Yok: Bu güvenlik devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="b1ae0-118">-   None: This disables security.</span></span><br /><span data-ttu-id="b1ae0-119">-Taşıma: Güvenlik temel alınan temel aktarım güvenliği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="b1ae0-119">-   Transport: Security is provided using underlying transport based security.</span></span> <span data-ttu-id="b1ae0-120">Bu mod koruma düzeyiyle denetlemek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="b1ae0-120">It is possible to control the protection level with this mode.</span></span><br /><span data-ttu-id="b1ae0-121">-Aktarım varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="b1ae0-121">-   The default value is Transport.</span></span> <span data-ttu-id="b1ae0-122">Bu öznitelik türünde <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="b1ae0-122">This attribute is of type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b1ae0-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b1ae0-123">Child Elements</span></span>  
  
|<span data-ttu-id="b1ae0-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="b1ae0-124">Element</span></span>|<span data-ttu-id="b1ae0-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b1ae0-125">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b1ae0-126">taşıma</span><span class="sxs-lookup"><span data-stu-id="b1ae0-126">transport</span></span>|<span data-ttu-id="b1ae0-127">Taşıma için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b1ae0-127">Defines the security settings for the transport.</span></span> <span data-ttu-id="b1ae0-128">Bu öğe türünde <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="b1ae0-128">This element is of type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b1ae0-129">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b1ae0-129">Parent Elements</span></span>  
  
|<span data-ttu-id="b1ae0-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="b1ae0-130">Element</span></span>|<span data-ttu-id="b1ae0-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b1ae0-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b1ae0-132">bağlama</span><span class="sxs-lookup"><span data-stu-id="b1ae0-132">binding</span></span>|<span data-ttu-id="b1ae0-133">Bağlama öğesi [ \<netNamedPipeBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).</span><span class="sxs-lookup"><span data-stu-id="b1ae0-133">The binding element of the [\<netNamedPipeBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b1ae0-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b1ae0-134">See also</span></span>

- <xref:System.ServiceModel.NetNamedPipeSecurity>
- <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>
- [<span data-ttu-id="b1ae0-135">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="b1ae0-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="b1ae0-136">Kimlik Bilgisi Türü Seçme</span><span class="sxs-lookup"><span data-stu-id="b1ae0-136">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="b1ae0-137">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="b1ae0-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="b1ae0-138">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b1ae0-138">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="b1ae0-139">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="b1ae0-139">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="b1ae0-140">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="b1ae0-140">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)

---
title: <security> / <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
ms.openlocfilehash: cd3ff5d3983283f9b4783912b4b9525c5000df61
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399823"
---
# <a name="security-of-netnamedpipebinding"></a><span data-ttu-id="b0a94-102">\<\<NetNamedPipeBinding > Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="b0a94-102">\<security> of \<netNamedPipeBinding></span></span>
<span data-ttu-id="b0a94-103">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b0a94-103">Defines the security settings for a binding.</span></span>  
  
<span data-ttu-id="b0a94-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b0a94-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b0a94-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="b0a94-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="b0a94-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlama >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="b0a94-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="b0a94-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netNamedPipeBinding >** ](netnamedpipebinding.md)</span><span class="sxs-lookup"><span data-stu-id="b0a94-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netNamedPipeBinding>**](netnamedpipebinding.md)</span></span>\
<span data-ttu-id="b0a94-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="b0a94-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="b0a94-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Güvenlik >**</span><span class="sxs-lookup"><span data-stu-id="b0a94-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0a94-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b0a94-110">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b0a94-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b0a94-111">Attributes and Elements</span></span>  
 <span data-ttu-id="b0a94-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b0a94-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b0a94-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b0a94-113">Attributes</span></span>  
  
|<span data-ttu-id="b0a94-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b0a94-114">Attribute</span></span>|<span data-ttu-id="b0a94-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b0a94-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b0a94-116">mod</span><span class="sxs-lookup"><span data-stu-id="b0a94-116">mode</span></span>|<span data-ttu-id="b0a94-117">Bu bağlamaya uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="b0a94-117">Specifies the type of security that is applied to this binding.</span></span> <span data-ttu-id="b0a94-118">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="b0a94-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="b0a94-119">Seçim Bu, güvenliği devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="b0a94-119">-   None: This disables security.</span></span><br /><span data-ttu-id="b0a94-120">Aktarım Güvenlik, temel alınan aktarım tabanlı güvenlik kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="b0a94-120">-   Transport: Security is provided using underlying transport based security.</span></span> <span data-ttu-id="b0a94-121">Koruma düzeyini Bu modla denetlemek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="b0a94-121">It is possible to control the protection level with this mode.</span></span><br /><span data-ttu-id="b0a94-122">-Varsayılan değer Transport ' dır.</span><span class="sxs-lookup"><span data-stu-id="b0a94-122">-   The default value is Transport.</span></span> <span data-ttu-id="b0a94-123">Bu öznitelik türü <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="b0a94-123">This attribute is of type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b0a94-124">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b0a94-124">Child Elements</span></span>  
  
|<span data-ttu-id="b0a94-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="b0a94-125">Element</span></span>|<span data-ttu-id="b0a94-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b0a94-126">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b0a94-127">taşıma</span><span class="sxs-lookup"><span data-stu-id="b0a94-127">transport</span></span>|<span data-ttu-id="b0a94-128">Taşımanın güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b0a94-128">Defines the security settings for the transport.</span></span> <span data-ttu-id="b0a94-129">Bu öğe türündedir <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="b0a94-129">This element is of type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b0a94-130">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b0a94-130">Parent Elements</span></span>  
  
|<span data-ttu-id="b0a94-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="b0a94-131">Element</span></span>|<span data-ttu-id="b0a94-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b0a94-132">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b0a94-133">bağlama</span><span class="sxs-lookup"><span data-stu-id="b0a94-133">binding</span></span>|<span data-ttu-id="b0a94-134">[ \<NetNamedPipeBinding](netnamedpipebinding.md)'in Binding öğesi >.</span><span class="sxs-lookup"><span data-stu-id="b0a94-134">The binding element of the [\<netNamedPipeBinding>](netnamedpipebinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b0a94-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0a94-135">See also</span></span>

- <xref:System.ServiceModel.NetNamedPipeSecurity>
- <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>
- [<span data-ttu-id="b0a94-136">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="b0a94-136">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="b0a94-137">Kimlik Bilgisi Türü Seçme</span><span class="sxs-lookup"><span data-stu-id="b0a94-137">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="b0a94-138">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="b0a94-138">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b0a94-139">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b0a94-139">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="b0a94-140">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="b0a94-140">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="b0a94-141">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="b0a94-141">\<binding></span></span>](../../../misc/binding.md)

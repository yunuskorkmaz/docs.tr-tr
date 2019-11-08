---
title: <security> / <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
ms.openlocfilehash: 31ea31ce6880a770c966350cd931e487396c4d63
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736440"
---
# <a name="security-of-netnamedpipebinding"></a><span data-ttu-id="82afa-102">\<netNamedPipeBinding > Güvenlik > \<</span><span class="sxs-lookup"><span data-stu-id="82afa-102">\<security> of \<netNamedPipeBinding></span></span>
<span data-ttu-id="82afa-103">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="82afa-103">Defines the security settings for a binding.</span></span>  
  
<span data-ttu-id="82afa-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="82afa-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="82afa-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="82afa-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="82afa-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlamaları >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="82afa-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="82afa-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netNamedPipeBinding >** ](netnamedpipebinding.md)</span><span class="sxs-lookup"><span data-stu-id="82afa-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netNamedPipeBinding>**](netnamedpipebinding.md)</span></span>\
<span data-ttu-id="82afa-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="82afa-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="82afa-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<güvenlik >**</span><span class="sxs-lookup"><span data-stu-id="82afa-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82afa-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="82afa-110">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="82afa-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="82afa-111">Attributes and Elements</span></span>  
 <span data-ttu-id="82afa-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="82afa-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="82afa-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="82afa-113">Attributes</span></span>  
  
|<span data-ttu-id="82afa-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="82afa-114">Attribute</span></span>|<span data-ttu-id="82afa-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="82afa-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="82afa-116">mod</span><span class="sxs-lookup"><span data-stu-id="82afa-116">mode</span></span>|<span data-ttu-id="82afa-117">Bu bağlamaya uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="82afa-117">Specifies the type of security that is applied to this binding.</span></span> <span data-ttu-id="82afa-118">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="82afa-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="82afa-119">-None: Bu, güvenliği devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="82afa-119">-   None: This disables security.</span></span><br /><span data-ttu-id="82afa-120">-Transport: güvenlik, temel alınan aktarım tabanlı güvenlik kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="82afa-120">-   Transport: Security is provided using underlying transport based security.</span></span> <span data-ttu-id="82afa-121">Koruma düzeyini Bu modla denetlemek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="82afa-121">It is possible to control the protection level with this mode.</span></span><br /><span data-ttu-id="82afa-122">-Varsayılan değer Transport ' dır.</span><span class="sxs-lookup"><span data-stu-id="82afa-122">-   The default value is Transport.</span></span> <span data-ttu-id="82afa-123">Bu öznitelik <xref:System.ServiceModel.NetNamedPipeSecurityMode>türündedir.</span><span class="sxs-lookup"><span data-stu-id="82afa-123">This attribute is of type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="82afa-124">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="82afa-124">Child Elements</span></span>  
  
|<span data-ttu-id="82afa-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="82afa-125">Element</span></span>|<span data-ttu-id="82afa-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="82afa-126">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="82afa-127">taşıma</span><span class="sxs-lookup"><span data-stu-id="82afa-127">transport</span></span>|<span data-ttu-id="82afa-128">Taşımanın güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="82afa-128">Defines the security settings for the transport.</span></span> <span data-ttu-id="82afa-129">Bu öğe <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>türündedir.</span><span class="sxs-lookup"><span data-stu-id="82afa-129">This element is of type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="82afa-130">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="82afa-130">Parent Elements</span></span>  
  
|<span data-ttu-id="82afa-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="82afa-131">Element</span></span>|<span data-ttu-id="82afa-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="82afa-132">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="82afa-133">bağlama</span><span class="sxs-lookup"><span data-stu-id="82afa-133">binding</span></span>|<span data-ttu-id="82afa-134">[\<netNamedPipeBinding >](netnamedpipebinding.md)bağlama öğesi.</span><span class="sxs-lookup"><span data-stu-id="82afa-134">The binding element of the [\<netNamedPipeBinding>](netnamedpipebinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="82afa-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="82afa-135">See also</span></span>

- <xref:System.ServiceModel.NetNamedPipeSecurity>
- <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>
- [<span data-ttu-id="82afa-136">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="82afa-136">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="82afa-137">Kimlik Bilgisi Türü Seçme</span><span class="sxs-lookup"><span data-stu-id="82afa-137">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="82afa-138">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="82afa-138">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="82afa-139">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="82afa-139">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="82afa-140">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="82afa-140">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="82afa-141">\< bağlama ></span><span class="sxs-lookup"><span data-stu-id="82afa-141">\<binding></span></span>](bindings.md)

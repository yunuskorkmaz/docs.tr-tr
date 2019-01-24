---
title: '&lt;pnrpPeerResolver&gt;'
ms.date: 03/30/2017
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
ms.openlocfilehash: cefd46d7810149264f9c431a212da0f3f51f8186
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54577652"
---
# <a name="ltpnrppeerresolvergt"></a><span data-ttu-id="e5831-102">&lt;pnrpPeerResolver&gt;</span><span class="sxs-lookup"><span data-stu-id="e5831-102">&lt;pnrpPeerResolver&gt;</span></span>
<span data-ttu-id="e5831-103">PNRP (Eş Adı Çözümleme Protokolü) çözümleyici olrak kullanılacak olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e5831-103">Specifies that the PNRP (Peer Name Resolution Protocol) resolver is to be used as a resolver.</span></span> <span data-ttu-id="e5831-104">PNRP varsayılan Çözümleyici, çünkü bu öğe isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e5831-104">This element is optional because PNRP is the default resolver.</span></span>  
  
 <span data-ttu-id="e5831-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e5831-105">\<system.serviceModel></span></span>  
<span data-ttu-id="e5831-106">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="e5831-106">\<bindings></span></span>  
<span data-ttu-id="e5831-107">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="e5831-107">\<customBinding></span></span>  
<span data-ttu-id="e5831-108">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="e5831-108">\<binding></span></span>  
<span data-ttu-id="e5831-109">\<pnrpResolver ></span><span class="sxs-lookup"><span data-stu-id="e5831-109">\<pnrpResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5831-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e5831-110">Syntax</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e5831-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e5831-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e5831-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e5831-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e5831-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e5831-113">Attributes</span></span>  
  
|<span data-ttu-id="e5831-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e5831-114">Attribute</span></span>|<span data-ttu-id="e5831-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e5831-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e5831-116">resolverType</span><span class="sxs-lookup"><span data-stu-id="e5831-116">resolverType</span></span>|<span data-ttu-id="e5831-117">Kullanılacak çözümleyici belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="e5831-117">A string that specifies the resolver to be used.</span></span> <span data-ttu-id="e5831-118">Bu öznitelik isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e5831-118">This attribute is optional.</span></span> <span data-ttu-id="e5831-119">Ayarlı değil veya boş dize olarak ayarlarsanız, PNRP kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e5831-119">If it is not set, or if it is set to an empty string, PNRP is used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e5831-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e5831-120">Child Elements</span></span>  
 <span data-ttu-id="e5831-121">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="e5831-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e5831-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e5831-122">Parent Elements</span></span>  
  
|<span data-ttu-id="e5831-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="e5831-123">Element</span></span>|<span data-ttu-id="e5831-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e5831-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e5831-125">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="e5831-125">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="e5831-126">Özel bağlama tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e5831-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e5831-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="e5831-127">Example</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="see-also"></a><span data-ttu-id="e5831-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5831-128">See also</span></span>
- <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>
- <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="e5831-129">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="e5831-129">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="e5831-130">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="e5831-130">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="e5831-131">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="e5831-131">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="e5831-132">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="e5831-132">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="e5831-133">Eş Çözücüler</span><span class="sxs-lookup"><span data-stu-id="e5831-133">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)

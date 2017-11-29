---
title: '&lt;pnrpPeerResolver&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: cd93bdadec120050813fcc1097d3041d6be94f66
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltpnrppeerresolvergt"></a><span data-ttu-id="50ae9-102">&lt;pnrpPeerResolver&gt;</span><span class="sxs-lookup"><span data-stu-id="50ae9-102">&lt;pnrpPeerResolver&gt;</span></span>
<span data-ttu-id="50ae9-103">PNRP (Eş Adı Çözümleme Protokolü) çözümleyici çözümleyici kullanılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="50ae9-103">Specifies that the PNRP (Peer Name Resolution Protocol) resolver is to be used as a resolver.</span></span> <span data-ttu-id="50ae9-104">PNRP varsayılan çözümleyici olduğundan bu öğe isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="50ae9-104">This element is optional because PNRP is the default resolver.</span></span>  
  
 <span data-ttu-id="50ae9-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="50ae9-105">\<system.serviceModel></span></span>  
<span data-ttu-id="50ae9-106">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="50ae9-106">\<bindings></span></span>  
<span data-ttu-id="50ae9-107">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="50ae9-107">\<customBinding></span></span>  
<span data-ttu-id="50ae9-108">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="50ae9-108">\<binding></span></span>  
<span data-ttu-id="50ae9-109">\<pnrpResolver ></span><span class="sxs-lookup"><span data-stu-id="50ae9-109">\<pnrpResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50ae9-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="50ae9-110">Syntax</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="50ae9-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="50ae9-111">Attributes and Elements</span></span>  
 <span data-ttu-id="50ae9-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="50ae9-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="50ae9-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="50ae9-113">Attributes</span></span>  
  
|<span data-ttu-id="50ae9-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="50ae9-114">Attribute</span></span>|<span data-ttu-id="50ae9-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="50ae9-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="50ae9-116">resolverType</span><span class="sxs-lookup"><span data-stu-id="50ae9-116">resolverType</span></span>|<span data-ttu-id="50ae9-117">Kullanılacak çözümleyici belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="50ae9-117">A string that specifies the resolver to be used.</span></span> <span data-ttu-id="50ae9-118">Bu öznitelik isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="50ae9-118">This attribute is optional.</span></span> <span data-ttu-id="50ae9-119">Ayarlı değil ya da boş bir dize olarak ayarlarsanız, PNRP kullanılır.</span><span class="sxs-lookup"><span data-stu-id="50ae9-119">If it is not set, or if it is set to an empty string, PNRP is used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="50ae9-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="50ae9-120">Child Elements</span></span>  
 <span data-ttu-id="50ae9-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="50ae9-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="50ae9-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="50ae9-122">Parent Elements</span></span>  
  
|<span data-ttu-id="50ae9-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="50ae9-123">Element</span></span>|<span data-ttu-id="50ae9-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="50ae9-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="50ae9-125">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="50ae9-125">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="50ae9-126">Özel bağlama tüm bağlama özelliklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="50ae9-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="50ae9-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="50ae9-127">Example</span></span>  
  
```xml  
<pnrpResolver resolverType="" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="50ae9-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="50ae9-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>  
 <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="50ae9-129">Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="50ae9-129">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="50ae9-130">Bağlamaları genişletme</span><span class="sxs-lookup"><span data-stu-id="50ae9-130">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="50ae9-131">Özel bağlamalar</span><span class="sxs-lookup"><span data-stu-id="50ae9-131">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="50ae9-132">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="50ae9-132">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="50ae9-133">Eş çözücüler</span><span class="sxs-lookup"><span data-stu-id="50ae9-133">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)

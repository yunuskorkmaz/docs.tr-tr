---
title: <pnrpPeerResolver>
ms.date: 03/30/2017
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
ms.openlocfilehash: d3e88d7f2dd991091d3d7abdc715e125ddc9ac56
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738771"
---
# <a name="pnrppeerresolver"></a><span data-ttu-id="258e0-101">\<pnrpPeerResolver ></span><span class="sxs-lookup"><span data-stu-id="258e0-101">\<pnrpPeerResolver></span></span>
<span data-ttu-id="258e0-102">PNRP (eş adı çözümleme Protokolü) Çözümleyicisinin çözümleyici olarak kullanılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="258e0-102">Specifies that the PNRP (Peer Name Resolution Protocol) resolver is to be used as a resolver.</span></span> <span data-ttu-id="258e0-103">PNRP varsayılan çözümleyici olduğundan bu öğe isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="258e0-103">This element is optional because PNRP is the default resolver.</span></span>  
  
<span data-ttu-id="258e0-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="258e0-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="258e0-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="258e0-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="258e0-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlamaları >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="258e0-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="258e0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="258e0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="258e0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="258e0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="258e0-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<pnrpResolver >**</span><span class="sxs-lookup"><span data-stu-id="258e0-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<pnrpResolver>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="258e0-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="258e0-110">Syntax</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="258e0-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="258e0-111">Attributes and Elements</span></span>  
 <span data-ttu-id="258e0-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="258e0-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="258e0-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="258e0-113">Attributes</span></span>  
  
|<span data-ttu-id="258e0-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="258e0-114">Attribute</span></span>|<span data-ttu-id="258e0-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="258e0-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="258e0-116">resolverType</span><span class="sxs-lookup"><span data-stu-id="258e0-116">resolverType</span></span>|<span data-ttu-id="258e0-117">Kullanılacak çözümleyici 'yi belirleyen bir dize.</span><span class="sxs-lookup"><span data-stu-id="258e0-117">A string that specifies the resolver to be used.</span></span> <span data-ttu-id="258e0-118">Bu öznitelik isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="258e0-118">This attribute is optional.</span></span> <span data-ttu-id="258e0-119">Ayarlanmamışsa veya boş bir dizeye ayarlandıysa, PNRP kullanılır.</span><span class="sxs-lookup"><span data-stu-id="258e0-119">If it is not set, or if it is set to an empty string, PNRP is used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="258e0-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="258e0-120">Child Elements</span></span>  
 <span data-ttu-id="258e0-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="258e0-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="258e0-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="258e0-122">Parent Elements</span></span>  
  
|<span data-ttu-id="258e0-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="258e0-123">Element</span></span>|<span data-ttu-id="258e0-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="258e0-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="258e0-125">\< bağlama ></span><span class="sxs-lookup"><span data-stu-id="258e0-125">\<binding></span></span>](bindings.md)|<span data-ttu-id="258e0-126">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="258e0-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="258e0-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="258e0-127">Example</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="see-also"></a><span data-ttu-id="258e0-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="258e0-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>
- <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="258e0-129">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="258e0-129">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="258e0-130">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="258e0-130">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="258e0-131">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="258e0-131">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="258e0-132">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="258e0-132">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="258e0-133">Eş Çözücüler</span><span class="sxs-lookup"><span data-stu-id="258e0-133">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)

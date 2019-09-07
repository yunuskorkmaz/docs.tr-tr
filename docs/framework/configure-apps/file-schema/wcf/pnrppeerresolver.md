---
title: <pnrpPeerResolver>
ms.date: 03/30/2017
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
ms.openlocfilehash: d7c6c8efa971fb60f0257cc1c74ceda72e31cb84
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400045"
---
# <a name="pnrppeerresolver"></a><span data-ttu-id="b2077-101">\<pnrpPeerResolver ></span><span class="sxs-lookup"><span data-stu-id="b2077-101">\<pnrpPeerResolver></span></span>
<span data-ttu-id="b2077-102">PNRP (eş adı çözümleme Protokolü) Çözümleyicisinin çözümleyici olarak kullanılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b2077-102">Specifies that the PNRP (Peer Name Resolution Protocol) resolver is to be used as a resolver.</span></span> <span data-ttu-id="b2077-103">PNRP varsayılan çözümleyici olduğundan bu öğe isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="b2077-103">This element is optional because PNRP is the default resolver.</span></span>  
  
<span data-ttu-id="b2077-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b2077-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b2077-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="b2077-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="b2077-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlama >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="b2077-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="b2077-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="b2077-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="b2077-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="b2077-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="b2077-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<pnrpResolver >**</span><span class="sxs-lookup"><span data-stu-id="b2077-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<pnrpResolver>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2077-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b2077-110">Syntax</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b2077-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b2077-111">Attributes and Elements</span></span>  
 <span data-ttu-id="b2077-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b2077-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b2077-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b2077-113">Attributes</span></span>  
  
|<span data-ttu-id="b2077-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b2077-114">Attribute</span></span>|<span data-ttu-id="b2077-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b2077-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b2077-116">resolverType</span><span class="sxs-lookup"><span data-stu-id="b2077-116">resolverType</span></span>|<span data-ttu-id="b2077-117">Kullanılacak çözümleyici 'yi belirleyen bir dize.</span><span class="sxs-lookup"><span data-stu-id="b2077-117">A string that specifies the resolver to be used.</span></span> <span data-ttu-id="b2077-118">Bu öznitelik isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="b2077-118">This attribute is optional.</span></span> <span data-ttu-id="b2077-119">Ayarlanmamışsa veya boş bir dizeye ayarlandıysa, PNRP kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b2077-119">If it is not set, or if it is set to an empty string, PNRP is used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b2077-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b2077-120">Child Elements</span></span>  
 <span data-ttu-id="b2077-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="b2077-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b2077-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b2077-122">Parent Elements</span></span>  
  
|<span data-ttu-id="b2077-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="b2077-123">Element</span></span>|<span data-ttu-id="b2077-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b2077-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b2077-125">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="b2077-125">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="b2077-126">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b2077-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b2077-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="b2077-127">Example</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="see-also"></a><span data-ttu-id="b2077-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2077-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>
- <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="b2077-129">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="b2077-129">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b2077-130">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="b2077-130">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="b2077-131">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="b2077-131">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="b2077-132">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="b2077-132">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="b2077-133">Eş Çözücüler</span><span class="sxs-lookup"><span data-stu-id="b2077-133">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)

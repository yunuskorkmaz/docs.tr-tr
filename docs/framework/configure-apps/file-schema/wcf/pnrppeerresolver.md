---
title: <pnrpPeerResolver>
ms.date: 03/30/2017
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
ms.openlocfilehash: e7e82117304ac133e5e84c0fc36b987560bcef96
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933806"
---
# <a name="pnrppeerresolver"></a><span data-ttu-id="9ec44-101">\<pnrpPeerResolver ></span><span class="sxs-lookup"><span data-stu-id="9ec44-101">\<pnrpPeerResolver></span></span>
<span data-ttu-id="9ec44-102">PNRP (eş adı çözümleme Protokolü) Çözümleyicisinin çözümleyici olarak kullanılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9ec44-102">Specifies that the PNRP (Peer Name Resolution Protocol) resolver is to be used as a resolver.</span></span> <span data-ttu-id="9ec44-103">PNRP varsayılan çözümleyici olduğundan bu öğe isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="9ec44-103">This element is optional because PNRP is the default resolver.</span></span>  
  
 <span data-ttu-id="9ec44-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="9ec44-104">\<system.serviceModel></span></span>  
<span data-ttu-id="9ec44-105">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="9ec44-105">\<bindings></span></span>  
<span data-ttu-id="9ec44-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="9ec44-106">\<customBinding></span></span>  
<span data-ttu-id="9ec44-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="9ec44-107">\<binding></span></span>  
<span data-ttu-id="9ec44-108">\<pnrpResolver ></span><span class="sxs-lookup"><span data-stu-id="9ec44-108">\<pnrpResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ec44-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9ec44-109">Syntax</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9ec44-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9ec44-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9ec44-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9ec44-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9ec44-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9ec44-112">Attributes</span></span>  
  
|<span data-ttu-id="9ec44-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9ec44-113">Attribute</span></span>|<span data-ttu-id="9ec44-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9ec44-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9ec44-115">resolverType</span><span class="sxs-lookup"><span data-stu-id="9ec44-115">resolverType</span></span>|<span data-ttu-id="9ec44-116">Kullanılacak çözümleyici 'yi belirleyen bir dize.</span><span class="sxs-lookup"><span data-stu-id="9ec44-116">A string that specifies the resolver to be used.</span></span> <span data-ttu-id="9ec44-117">Bu öznitelik isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="9ec44-117">This attribute is optional.</span></span> <span data-ttu-id="9ec44-118">Ayarlanmamışsa veya boş bir dizeye ayarlandıysa, PNRP kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9ec44-118">If it is not set, or if it is set to an empty string, PNRP is used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9ec44-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9ec44-119">Child Elements</span></span>  
 <span data-ttu-id="9ec44-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="9ec44-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9ec44-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9ec44-121">Parent Elements</span></span>  
  
|<span data-ttu-id="9ec44-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="9ec44-122">Element</span></span>|<span data-ttu-id="9ec44-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9ec44-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9ec44-124">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="9ec44-124">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="9ec44-125">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9ec44-125">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9ec44-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="9ec44-126">Example</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="see-also"></a><span data-ttu-id="9ec44-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9ec44-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>
- <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="9ec44-128">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="9ec44-128">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="9ec44-129">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="9ec44-129">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="9ec44-130">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="9ec44-130">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="9ec44-131">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="9ec44-131">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="9ec44-132">Eş Çözücüler</span><span class="sxs-lookup"><span data-stu-id="9ec44-132">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)

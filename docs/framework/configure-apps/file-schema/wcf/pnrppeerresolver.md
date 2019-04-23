---
title: <pnrpPeerResolver>
ms.date: 03/30/2017
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
ms.openlocfilehash: 2404f00b2a3ba03e89c1e21fb25e13cabb8feed3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59214059"
---
# <a name="pnrppeerresolver"></a><span data-ttu-id="37435-101">\<pnrpPeerResolver ></span><span class="sxs-lookup"><span data-stu-id="37435-101">\<pnrpPeerResolver></span></span>
<span data-ttu-id="37435-102">PNRP (Eş Adı Çözümleme Protokolü) çözümleyici olrak kullanılacak olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="37435-102">Specifies that the PNRP (Peer Name Resolution Protocol) resolver is to be used as a resolver.</span></span> <span data-ttu-id="37435-103">PNRP varsayılan Çözümleyici, çünkü bu öğe isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="37435-103">This element is optional because PNRP is the default resolver.</span></span>  
  
 <span data-ttu-id="37435-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="37435-104">\<system.serviceModel></span></span>  
<span data-ttu-id="37435-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="37435-105">\<bindings></span></span>  
<span data-ttu-id="37435-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="37435-106">\<customBinding></span></span>  
<span data-ttu-id="37435-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="37435-107">\<binding></span></span>  
<span data-ttu-id="37435-108">\<pnrpResolver ></span><span class="sxs-lookup"><span data-stu-id="37435-108">\<pnrpResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37435-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="37435-109">Syntax</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="37435-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="37435-110">Attributes and Elements</span></span>  
 <span data-ttu-id="37435-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="37435-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="37435-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="37435-112">Attributes</span></span>  
  
|<span data-ttu-id="37435-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="37435-113">Attribute</span></span>|<span data-ttu-id="37435-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="37435-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="37435-115">resolverType</span><span class="sxs-lookup"><span data-stu-id="37435-115">resolverType</span></span>|<span data-ttu-id="37435-116">Kullanılacak çözümleyici belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="37435-116">A string that specifies the resolver to be used.</span></span> <span data-ttu-id="37435-117">Bu öznitelik isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="37435-117">This attribute is optional.</span></span> <span data-ttu-id="37435-118">Ayarlı değil veya boş dize olarak ayarlarsanız, PNRP kullanılır.</span><span class="sxs-lookup"><span data-stu-id="37435-118">If it is not set, or if it is set to an empty string, PNRP is used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="37435-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="37435-119">Child Elements</span></span>  
 <span data-ttu-id="37435-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="37435-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="37435-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="37435-121">Parent Elements</span></span>  
  
|<span data-ttu-id="37435-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="37435-122">Element</span></span>|<span data-ttu-id="37435-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="37435-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="37435-124">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="37435-124">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="37435-125">Özel bağlama tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="37435-125">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="37435-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="37435-126">Example</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="see-also"></a><span data-ttu-id="37435-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="37435-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>
- <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="37435-128">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="37435-128">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="37435-129">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="37435-129">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="37435-130">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="37435-130">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="37435-131">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="37435-131">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="37435-132">Eş Çözücüler</span><span class="sxs-lookup"><span data-stu-id="37435-132">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)

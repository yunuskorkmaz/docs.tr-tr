---
title: <pnrpPeerResolver>
ms.date: 03/30/2017
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
ms.openlocfilehash: f98c358cc9891e9d7223d280fc8e50c19aad9759
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55260663"
---
# <a name="pnrppeerresolver"></a><span data-ttu-id="86b3c-101">\<pnrpPeerResolver ></span><span class="sxs-lookup"><span data-stu-id="86b3c-101">\<pnrpPeerResolver></span></span>
<span data-ttu-id="86b3c-102">PNRP (Eş Adı Çözümleme Protokolü) çözümleyici olrak kullanılacak olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="86b3c-102">Specifies that the PNRP (Peer Name Resolution Protocol) resolver is to be used as a resolver.</span></span> <span data-ttu-id="86b3c-103">PNRP varsayılan Çözümleyici, çünkü bu öğe isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="86b3c-103">This element is optional because PNRP is the default resolver.</span></span>  
  
 <span data-ttu-id="86b3c-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="86b3c-104">\<system.serviceModel></span></span>  
<span data-ttu-id="86b3c-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="86b3c-105">\<bindings></span></span>  
<span data-ttu-id="86b3c-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="86b3c-106">\<customBinding></span></span>  
<span data-ttu-id="86b3c-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="86b3c-107">\<binding></span></span>  
<span data-ttu-id="86b3c-108">\<pnrpResolver ></span><span class="sxs-lookup"><span data-stu-id="86b3c-108">\<pnrpResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86b3c-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="86b3c-109">Syntax</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="86b3c-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="86b3c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="86b3c-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="86b3c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="86b3c-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="86b3c-112">Attributes</span></span>  
  
|<span data-ttu-id="86b3c-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="86b3c-113">Attribute</span></span>|<span data-ttu-id="86b3c-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="86b3c-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="86b3c-115">resolverType</span><span class="sxs-lookup"><span data-stu-id="86b3c-115">resolverType</span></span>|<span data-ttu-id="86b3c-116">Kullanılacak çözümleyici belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="86b3c-116">A string that specifies the resolver to be used.</span></span> <span data-ttu-id="86b3c-117">Bu öznitelik isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="86b3c-117">This attribute is optional.</span></span> <span data-ttu-id="86b3c-118">Ayarlı değil veya boş dize olarak ayarlarsanız, PNRP kullanılır.</span><span class="sxs-lookup"><span data-stu-id="86b3c-118">If it is not set, or if it is set to an empty string, PNRP is used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="86b3c-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="86b3c-119">Child Elements</span></span>  
 <span data-ttu-id="86b3c-120">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="86b3c-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="86b3c-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="86b3c-121">Parent Elements</span></span>  
  
|<span data-ttu-id="86b3c-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="86b3c-122">Element</span></span>|<span data-ttu-id="86b3c-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="86b3c-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="86b3c-124">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="86b3c-124">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="86b3c-125">Özel bağlama tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="86b3c-125">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="86b3c-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="86b3c-126">Example</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="see-also"></a><span data-ttu-id="86b3c-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86b3c-127">See also</span></span>
- <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>
- <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="86b3c-128">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="86b3c-128">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="86b3c-129">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="86b3c-129">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="86b3c-130">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="86b3c-130">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="86b3c-131">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="86b3c-131">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="86b3c-132">Eş Çözücüler</span><span class="sxs-lookup"><span data-stu-id="86b3c-132">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)

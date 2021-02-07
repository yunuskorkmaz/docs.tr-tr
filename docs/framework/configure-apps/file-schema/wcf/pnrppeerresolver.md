---
description: 'Hakkında daha fazla bilgi edinin: <pnrpPeerResolver>'
title: <pnrpPeerResolver>
ms.date: 03/30/2017
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
ms.openlocfilehash: 4af6a63312fa300cfa33e578f01b8e07267ad3a1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683547"
---
# \<pnrpPeerResolver>

<span data-ttu-id="0ae60-102">PNRP (eş adı çözümleme Protokolü) Çözümleyicisinin çözümleyici olarak kullanılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0ae60-102">Specifies that the PNRP (Peer Name Resolution Protocol) resolver is to be used as a resolver.</span></span> <span data-ttu-id="0ae60-103">PNRP varsayılan çözümleyici olduğundan bu öğe isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="0ae60-103">This element is optional because PNRP is the default resolver.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<pnrpResolver>**  
  
## <a name="syntax"></a><span data-ttu-id="0ae60-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="0ae60-104">Syntax</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0ae60-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0ae60-105">Attributes and Elements</span></span>  

 <span data-ttu-id="0ae60-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0ae60-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0ae60-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0ae60-107">Attributes</span></span>  
  
|<span data-ttu-id="0ae60-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0ae60-108">Attribute</span></span>|<span data-ttu-id="0ae60-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0ae60-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0ae60-110">resolverType</span><span class="sxs-lookup"><span data-stu-id="0ae60-110">resolverType</span></span>|<span data-ttu-id="0ae60-111">Kullanılacak çözümleyici 'yi belirleyen bir dize.</span><span class="sxs-lookup"><span data-stu-id="0ae60-111">A string that specifies the resolver to be used.</span></span> <span data-ttu-id="0ae60-112">Bu öznitelik isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="0ae60-112">This attribute is optional.</span></span> <span data-ttu-id="0ae60-113">Ayarlanmamışsa veya boş bir dizeye ayarlandıysa, PNRP kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0ae60-113">If it is not set, or if it is set to an empty string, PNRP is used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0ae60-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0ae60-114">Child Elements</span></span>  

 <span data-ttu-id="0ae60-115">Yok</span><span class="sxs-lookup"><span data-stu-id="0ae60-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0ae60-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0ae60-116">Parent Elements</span></span>  
  
|<span data-ttu-id="0ae60-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="0ae60-117">Element</span></span>|<span data-ttu-id="0ae60-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0ae60-118">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="0ae60-119">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0ae60-119">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0ae60-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="0ae60-120">Example</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="see-also"></a><span data-ttu-id="0ae60-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ae60-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>
- <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="0ae60-122">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="0ae60-122">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="0ae60-123">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="0ae60-123">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="0ae60-124">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="0ae60-124">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="0ae60-125">Eş Çözücüler</span><span class="sxs-lookup"><span data-stu-id="0ae60-125">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)

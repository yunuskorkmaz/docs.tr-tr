---
title: <pnrpPeerResolver>
ms.date: 03/30/2017
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
ms.openlocfilehash: d3e88d7f2dd991091d3d7abdc715e125ddc9ac56
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738771"
---
# \<pnrpPeerResolver>
<span data-ttu-id="f55a3-101">PNRP (eş adı çözümleme Protokolü) Çözümleyicisinin çözümleyici olarak kullanılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f55a3-101">Specifies that the PNRP (Peer Name Resolution Protocol) resolver is to be used as a resolver.</span></span> <span data-ttu-id="f55a3-102">PNRP varsayılan çözümleyici olduğundan bu öğe isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="f55a3-102">This element is optional because PNRP is the default resolver.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<pnrpResolver>**  
  
## <a name="syntax"></a><span data-ttu-id="f55a3-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f55a3-103">Syntax</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f55a3-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f55a3-104">Attributes and Elements</span></span>  
 <span data-ttu-id="f55a3-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f55a3-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f55a3-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f55a3-106">Attributes</span></span>  
  
|<span data-ttu-id="f55a3-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f55a3-107">Attribute</span></span>|<span data-ttu-id="f55a3-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f55a3-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f55a3-109">resolverType</span><span class="sxs-lookup"><span data-stu-id="f55a3-109">resolverType</span></span>|<span data-ttu-id="f55a3-110">Kullanılacak çözümleyici 'yi belirleyen bir dize.</span><span class="sxs-lookup"><span data-stu-id="f55a3-110">A string that specifies the resolver to be used.</span></span> <span data-ttu-id="f55a3-111">Bu öznitelik isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="f55a3-111">This attribute is optional.</span></span> <span data-ttu-id="f55a3-112">Ayarlanmamışsa veya boş bir dizeye ayarlandıysa, PNRP kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f55a3-112">If it is not set, or if it is set to an empty string, PNRP is used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f55a3-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f55a3-113">Child Elements</span></span>  
 <span data-ttu-id="f55a3-114">Yok</span><span class="sxs-lookup"><span data-stu-id="f55a3-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f55a3-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f55a3-115">Parent Elements</span></span>  
  
|<span data-ttu-id="f55a3-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="f55a3-116">Element</span></span>|<span data-ttu-id="f55a3-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f55a3-117">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="f55a3-118">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f55a3-118">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f55a3-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="f55a3-119">Example</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="see-also"></a><span data-ttu-id="f55a3-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f55a3-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>
- <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="f55a3-121">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="f55a3-121">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f55a3-122">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="f55a3-122">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="f55a3-123">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="f55a3-123">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="f55a3-124">Eş Çözücüler</span><span class="sxs-lookup"><span data-stu-id="f55a3-124">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)

---
title: <useManagedPresentation>
ms.date: 03/30/2017
ms.assetid: 17a0dd77-af54-41db-a9d0-4b17ff42878f
ms.openlocfilehash: bb2989ed52a88d805510d65e1dc1740df7bb55eb
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73735946"
---
# \<useManagedPresentation>
<span data-ttu-id="9eea4-101">WS-Trust CardSpace profilini destekleyen bir CardSpace güvenlik belirteci hizmeti ile iletişim kurmak için kullanılan bağlama öğesi.</span><span class="sxs-lookup"><span data-stu-id="9eea4-101">A binding element used to communicate with a CardSpace Security Token Service that supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="9eea4-102">Bu öğenin bir özniteliği yok ve boş bir anahtar olarak var.</span><span class="sxs-lookup"><span data-stu-id="9eea4-102">This element has no attribute and is present as an empty switch.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<useManagedPresentation>**  
  
## <a name="syntax"></a><span data-ttu-id="9eea4-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9eea4-103">Syntax</span></span>  
  
```xml  
<useManagedPresentation />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9eea4-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9eea4-104">Attributes and Elements</span></span>  
 <span data-ttu-id="9eea4-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9eea4-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9eea4-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9eea4-106">Attributes</span></span>  
 <span data-ttu-id="9eea4-107">Yok.</span><span class="sxs-lookup"><span data-stu-id="9eea4-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9eea4-108">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9eea4-108">Child Elements</span></span>  
 <span data-ttu-id="9eea4-109">Yok</span><span class="sxs-lookup"><span data-stu-id="9eea4-109">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9eea4-110">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9eea4-110">Parent Elements</span></span>  
  
|<span data-ttu-id="9eea4-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="9eea4-111">Element</span></span>|<span data-ttu-id="9eea4-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9eea4-112">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="9eea4-113">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9eea4-113">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9eea4-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9eea4-114">Remarks</span></span>  
 <span data-ttu-id="9eea4-115">Bu öğe, bir kimlik sağlayıcısı tarafından ilkesinde, WS-Trust ' ın CardSpace profilini desteklediği gerçeğini ifade etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9eea4-115">This element is used by an identity provider to express in its policy the fact that it supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="9eea4-116">Bu tür bir ilke onayını yayınlayan kimlik sağlayıcılarının, söz konusu CardSpace profilini temel alan belirteçler yayınlayabilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="9eea4-116">Identity providers that publish such a policy assertion should be able to issue tokens based on that CardSpace profile.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9eea4-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9eea4-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseManagedPresentationElement>
- <xref:System.ServiceModel.Channels.UseManagedPresentationBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="9eea4-118">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="9eea4-118">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="9eea4-119">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="9eea4-119">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="9eea4-120">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="9eea4-120">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)

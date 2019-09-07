---
title: <useManagedPresentation>
ms.date: 03/30/2017
ms.assetid: 17a0dd77-af54-41db-a9d0-4b17ff42878f
ms.openlocfilehash: c410967e84c9318d21ce0b3072d08b026a37b190
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399218"
---
# <a name="usemanagedpresentation"></a><span data-ttu-id="11576-101">\<useManagedPresentation ></span><span class="sxs-lookup"><span data-stu-id="11576-101">\<useManagedPresentation></span></span>
<span data-ttu-id="11576-102">WS-Trust CardSpace profilini destekleyen bir CardSpace güvenlik belirteci hizmeti ile iletişim kurmak için kullanılan bağlama öğesi.</span><span class="sxs-lookup"><span data-stu-id="11576-102">A binding element used to communicate with a CardSpace Security Token Service that supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="11576-103">Bu öğenin bir özniteliği yok ve boş bir anahtar olarak var.</span><span class="sxs-lookup"><span data-stu-id="11576-103">This element has no attribute and is present as an empty switch.</span></span>  
  
<span data-ttu-id="11576-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="11576-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="11576-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="11576-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="11576-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlama >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="11576-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="11576-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="11576-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="11576-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="11576-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="11576-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<useManagedPresentation >**</span><span class="sxs-lookup"><span data-stu-id="11576-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<useManagedPresentation>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11576-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="11576-110">Syntax</span></span>  
  
```xml  
<useManagedPresentation />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="11576-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="11576-111">Attributes and Elements</span></span>  
 <span data-ttu-id="11576-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="11576-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="11576-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="11576-113">Attributes</span></span>  
 <span data-ttu-id="11576-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="11576-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="11576-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="11576-115">Child Elements</span></span>  
 <span data-ttu-id="11576-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="11576-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="11576-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="11576-117">Parent Elements</span></span>  
  
|<span data-ttu-id="11576-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="11576-118">Element</span></span>|<span data-ttu-id="11576-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="11576-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="11576-120">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="11576-120">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="11576-121">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="11576-121">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11576-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="11576-122">Remarks</span></span>  
 <span data-ttu-id="11576-123">Bu öğe, bir kimlik sağlayıcısı tarafından ilkesinde, WS-Trust ' ın CardSpace profilini desteklediği gerçeğini ifade etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="11576-123">This element is used by an identity provider to express in its policy the fact that it supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="11576-124">Bu tür bir ilke onayını yayınlayan kimlik sağlayıcılarının, söz konusu CardSpace profilini temel alan belirteçler yayınlayabilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="11576-124">Identity providers that publish such a policy assertion should be able to issue tokens based on that CardSpace profile.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11576-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="11576-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseManagedPresentationElement>
- <xref:System.ServiceModel.Channels.UseManagedPresentationBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="11576-126">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="11576-126">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="11576-127">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="11576-127">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="11576-128">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="11576-128">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="11576-129">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="11576-129">\<customBinding></span></span>](custombinding.md)

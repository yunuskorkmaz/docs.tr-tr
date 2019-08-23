---
title: <useManagedPresentation>
ms.date: 03/30/2017
ms.assetid: 17a0dd77-af54-41db-a9d0-4b17ff42878f
ms.openlocfilehash: e67cc316b8747ee785055ceb4f954988fa82a44c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940620"
---
# <a name="usemanagedpresentation"></a><span data-ttu-id="183e1-101">\<useManagedPresentation ></span><span class="sxs-lookup"><span data-stu-id="183e1-101">\<useManagedPresentation></span></span>
<span data-ttu-id="183e1-102">WS-Trust CardSpace profilini destekleyen bir CardSpace güvenlik belirteci hizmeti ile iletişim kurmak için kullanılan bağlama öğesi.</span><span class="sxs-lookup"><span data-stu-id="183e1-102">A binding element used to communicate with a CardSpace Security Token Service that supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="183e1-103">Bu öğenin bir özniteliği yok ve boş bir anahtar olarak var.</span><span class="sxs-lookup"><span data-stu-id="183e1-103">This element has no attribute and is present as an empty switch.</span></span>  
  
 <span data-ttu-id="183e1-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="183e1-104">\<system.serviceModel></span></span>  
<span data-ttu-id="183e1-105">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="183e1-105">\<bindings></span></span>  
<span data-ttu-id="183e1-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="183e1-106">\<customBinding></span></span>  
<span data-ttu-id="183e1-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="183e1-107">\<binding></span></span>  
<span data-ttu-id="183e1-108">\<useManagedPresentation ></span><span class="sxs-lookup"><span data-stu-id="183e1-108">\<useManagedPresentation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="183e1-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="183e1-109">Syntax</span></span>  
  
```xml  
<useManagedPresentation />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="183e1-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="183e1-110">Attributes and Elements</span></span>  
 <span data-ttu-id="183e1-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="183e1-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="183e1-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="183e1-112">Attributes</span></span>  
 <span data-ttu-id="183e1-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="183e1-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="183e1-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="183e1-114">Child Elements</span></span>  
 <span data-ttu-id="183e1-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="183e1-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="183e1-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="183e1-116">Parent Elements</span></span>  
  
|<span data-ttu-id="183e1-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="183e1-117">Element</span></span>|<span data-ttu-id="183e1-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="183e1-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="183e1-119">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="183e1-119">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="183e1-120">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="183e1-120">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="183e1-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="183e1-121">Remarks</span></span>  
 <span data-ttu-id="183e1-122">Bu öğe, bir kimlik sağlayıcısı tarafından ilkesinde, WS-Trust ' ın CardSpace profilini desteklediği gerçeğini ifade etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="183e1-122">This element is used by an identity provider to express in its policy the fact that it supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="183e1-123">Bu tür bir ilke onayını yayınlayan kimlik sağlayıcılarının, söz konusu CardSpace profilini temel alan belirteçler yayınlayabilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="183e1-123">Identity providers that publish such a policy assertion should be able to issue tokens based on that CardSpace profile.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="183e1-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="183e1-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseManagedPresentationElement>
- <xref:System.ServiceModel.Channels.UseManagedPresentationBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="183e1-125">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="183e1-125">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="183e1-126">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="183e1-126">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="183e1-127">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="183e1-127">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="183e1-128">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="183e1-128">\<customBinding></span></span>](custombinding.md)

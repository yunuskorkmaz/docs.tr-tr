---
title: '&lt;useManagedPresentation&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 17a0dd77-af54-41db-a9d0-4b17ff42878f
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ae9851794d77972066fb897aa76528fec86fd6f0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltusemanagedpresentationgt"></a><span data-ttu-id="8eb98-102">&lt;useManagedPresentation&gt;</span><span class="sxs-lookup"><span data-stu-id="8eb98-102">&lt;useManagedPresentation&gt;</span></span>
<span data-ttu-id="8eb98-103">CardSpace güvenlik belirteci, WS-Trust CardSpace profilini destekleyen hizmeti ile iletişim kurmak için kullanılan bir bağlama öğesi.</span><span class="sxs-lookup"><span data-stu-id="8eb98-103">A binding element used to communicate with a CardSpace Security Token Service that supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="8eb98-104">Bu öğe hiçbir özniteliği var ve boş bir anahtar yok.</span><span class="sxs-lookup"><span data-stu-id="8eb98-104">This element has no attribute and is present as an empty switch.</span></span>  
  
 <span data-ttu-id="8eb98-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="8eb98-105">\<system.serviceModel></span></span>  
<span data-ttu-id="8eb98-106">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="8eb98-106">\<bindings></span></span>  
<span data-ttu-id="8eb98-107">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="8eb98-107">\<customBinding></span></span>  
<span data-ttu-id="8eb98-108">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="8eb98-108">\<binding></span></span>  
<span data-ttu-id="8eb98-109">\<useManagedPresentation ></span><span class="sxs-lookup"><span data-stu-id="8eb98-109">\<useManagedPresentation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8eb98-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8eb98-110">Syntax</span></span>  
  
```xml  
<useManagedPresentation/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8eb98-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8eb98-111">Attributes and Elements</span></span>  
 <span data-ttu-id="8eb98-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8eb98-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8eb98-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8eb98-113">Attributes</span></span>  
 <span data-ttu-id="8eb98-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="8eb98-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8eb98-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8eb98-115">Child Elements</span></span>  
 <span data-ttu-id="8eb98-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="8eb98-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8eb98-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8eb98-117">Parent Elements</span></span>  
  
|<span data-ttu-id="8eb98-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="8eb98-118">Element</span></span>|<span data-ttu-id="8eb98-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8eb98-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8eb98-120">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="8eb98-120">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="8eb98-121">Özel bağlama tüm bağlama özelliklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8eb98-121">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8eb98-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8eb98-122">Remarks</span></span>  
 <span data-ttu-id="8eb98-123">Bu öğe, WS-Trust CardSpace profilini destekleyen olgu kendi ilkesinde ifade etmek için bir kimlik sağlayıcısı tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8eb98-123">This element is used by an identity provider to express in its policy the fact that it supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="8eb98-124">Bu tür bir ilke onaylama yayımlama kimlik sağlayıcıları bu CardSpace profilini temel sorunu belirteçleri saptayabilmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="8eb98-124">Identity providers that publish such a policy assertion should be able to issue tokens based on that CardSpace profile.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8eb98-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8eb98-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.UseManagedPresentationElement>  
 <xref:System.ServiceModel.Channels.UseManagedPresentationBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="8eb98-126">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="8eb98-126">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="8eb98-127">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="8eb98-127">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="8eb98-128">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="8eb98-128">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="8eb98-129">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="8eb98-129">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)

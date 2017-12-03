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
ms.openlocfilehash: 3aeb64513401164c9c5acb24ede48c2e9aa2b4b3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltusemanagedpresentationgt"></a><span data-ttu-id="5eb84-102">&lt;useManagedPresentation&gt;</span><span class="sxs-lookup"><span data-stu-id="5eb84-102">&lt;useManagedPresentation&gt;</span></span>
<span data-ttu-id="5eb84-103">CardSpace güvenlik belirteci, WS-Trust CardSpace profilini destekleyen hizmeti ile iletişim kurmak için kullanılan bir bağlama öğesi.</span><span class="sxs-lookup"><span data-stu-id="5eb84-103">A binding element used to communicate with a CardSpace Security Token Service that supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="5eb84-104">Bu öğe hiçbir özniteliği var ve boş bir anahtar yok.</span><span class="sxs-lookup"><span data-stu-id="5eb84-104">This element has no attribute and is present as an empty switch.</span></span>  
  
 <span data-ttu-id="5eb84-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="5eb84-105">\<system.serviceModel></span></span>  
<span data-ttu-id="5eb84-106">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="5eb84-106">\<bindings></span></span>  
<span data-ttu-id="5eb84-107">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="5eb84-107">\<customBinding></span></span>  
<span data-ttu-id="5eb84-108">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="5eb84-108">\<binding></span></span>  
<span data-ttu-id="5eb84-109">\<useManagedPresentation ></span><span class="sxs-lookup"><span data-stu-id="5eb84-109">\<useManagedPresentation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5eb84-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5eb84-110">Syntax</span></span>  
  
```xml  
<useManagedPresentation/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5eb84-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5eb84-111">Attributes and Elements</span></span>  
 <span data-ttu-id="5eb84-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5eb84-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5eb84-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5eb84-113">Attributes</span></span>  
 <span data-ttu-id="5eb84-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="5eb84-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5eb84-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5eb84-115">Child Elements</span></span>  
 <span data-ttu-id="5eb84-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="5eb84-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5eb84-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5eb84-117">Parent Elements</span></span>  
  
|<span data-ttu-id="5eb84-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="5eb84-118">Element</span></span>|<span data-ttu-id="5eb84-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5eb84-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5eb84-120">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="5eb84-120">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="5eb84-121">Özel bağlama tüm bağlama özelliklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5eb84-121">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5eb84-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5eb84-122">Remarks</span></span>  
 <span data-ttu-id="5eb84-123">Bu öğe, WS-Trust CardSpace profilini destekleyen olgu kendi ilkesinde ifade etmek için bir kimlik sağlayıcısı tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5eb84-123">This element is used by an identity provider to express in its policy the fact that it supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="5eb84-124">Bu tür bir ilke onaylama yayımlama kimlik sağlayıcıları bu CardSpace profilini temel sorunu belirteçleri saptayabilmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="5eb84-124">Identity providers that publish such a policy assertion should be able to issue tokens based on that CardSpace profile.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5eb84-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5eb84-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.UseManagedPresentationElement>  
 <xref:System.ServiceModel.Channels.UseManagedPresentationBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="5eb84-126">Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="5eb84-126">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="5eb84-127">Bağlamaları genişletme</span><span class="sxs-lookup"><span data-stu-id="5eb84-127">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="5eb84-128">Özel bağlamalar</span><span class="sxs-lookup"><span data-stu-id="5eb84-128">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="5eb84-129">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="5eb84-129">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)

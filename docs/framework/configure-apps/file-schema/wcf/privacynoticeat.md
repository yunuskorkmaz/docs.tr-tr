---
title: '&lt;privacyNoticeAt&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4cc96942-4eb9-4241-b2fd-45aa239915e8
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 46a27dcc35c01d25391c9224d4967937b0a02d52
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltprivacynoticeatgt"></a><span data-ttu-id="c99b8-102">&lt;privacyNoticeAt&gt;</span><span class="sxs-lookup"><span data-stu-id="c99b8-102">&lt;privacyNoticeAt&gt;</span></span>
<span data-ttu-id="c99b8-103">Kullanılan bir gizlilik bildirimi belirten bir yapılandırma öğesi temsil eden `wsFederationHttp` bağlama.</span><span class="sxs-lookup"><span data-stu-id="c99b8-103">Represents a configuration element that specifies a privacy notice used in `wsFederationHttp` binding.</span></span>  
  
 <span data-ttu-id="c99b8-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="c99b8-104">\<system.serviceModel></span></span>  
<span data-ttu-id="c99b8-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="c99b8-105">\<bindings></span></span>  
<span data-ttu-id="c99b8-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="c99b8-106">\<customBinding></span></span>  
<span data-ttu-id="c99b8-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="c99b8-107">\<binding></span></span>  
<span data-ttu-id="c99b8-108">\<privacyNotice ></span><span class="sxs-lookup"><span data-stu-id="c99b8-108">\<privacyNotice></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c99b8-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c99b8-109">Syntax</span></span>  
  
```xml  
<privacyNotice url="String"  
        version="Integer" />  
```  
  
## <a name="type"></a><span data-ttu-id="c99b8-110">Tür</span><span class="sxs-lookup"><span data-stu-id="c99b8-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c99b8-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c99b8-111">Attributes and Elements</span></span>  
 <span data-ttu-id="c99b8-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c99b8-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c99b8-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c99b8-113">Attributes</span></span>  
  
|<span data-ttu-id="c99b8-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c99b8-114">Attribute</span></span>|<span data-ttu-id="c99b8-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c99b8-115">Description</span></span>|  
|---------------|-----------------|  
|`url`|<span data-ttu-id="c99b8-116">Gizlilik bildirimi bulunduğu olduğu URI belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="c99b8-116">A string that specifies the URI at which the privacy notice is located.</span></span>|  
|`version`|<span data-ttu-id="c99b8-117">Bu gizlilik bildirimi sürümünü belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="c99b8-117">An integer that specifies the version of this privacy notice.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c99b8-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c99b8-118">Child Elements</span></span>  
 <span data-ttu-id="c99b8-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="c99b8-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c99b8-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c99b8-120">Parent Elements</span></span>  
  
|<span data-ttu-id="c99b8-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="c99b8-121">Element</span></span>|<span data-ttu-id="c99b8-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c99b8-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c99b8-123">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="c99b8-123">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="c99b8-124">Özel bağlama tüm bağlama özelliklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c99b8-124">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c99b8-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c99b8-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PrivacyNoticeElement>  
 <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="c99b8-126">Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="c99b8-126">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="c99b8-127">Bağlamaları genişletme</span><span class="sxs-lookup"><span data-stu-id="c99b8-127">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="c99b8-128">Özel bağlamalar</span><span class="sxs-lookup"><span data-stu-id="c99b8-128">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="c99b8-129">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="c99b8-129">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)

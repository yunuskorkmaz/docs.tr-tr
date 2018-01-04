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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 30b3f0bdd1aa02473470c354a730bcfa450f0264
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltprivacynoticeatgt"></a><span data-ttu-id="2d263-102">&lt;privacyNoticeAt&gt;</span><span class="sxs-lookup"><span data-stu-id="2d263-102">&lt;privacyNoticeAt&gt;</span></span>
<span data-ttu-id="2d263-103">Kullanılan bir gizlilik bildirimi belirten bir yapılandırma öğesi temsil eden `wsFederationHttp` bağlama.</span><span class="sxs-lookup"><span data-stu-id="2d263-103">Represents a configuration element that specifies a privacy notice used in `wsFederationHttp` binding.</span></span>  
  
 <span data-ttu-id="2d263-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="2d263-104">\<system.serviceModel></span></span>  
<span data-ttu-id="2d263-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="2d263-105">\<bindings></span></span>  
<span data-ttu-id="2d263-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="2d263-106">\<customBinding></span></span>  
<span data-ttu-id="2d263-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="2d263-107">\<binding></span></span>  
<span data-ttu-id="2d263-108">\<privacyNotice ></span><span class="sxs-lookup"><span data-stu-id="2d263-108">\<privacyNotice></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d263-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2d263-109">Syntax</span></span>  
  
```xml  
<privacyNotice url="String"  
        version="Integer" />  
```  
  
## <a name="type"></a><span data-ttu-id="2d263-110">Tür</span><span class="sxs-lookup"><span data-stu-id="2d263-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2d263-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2d263-111">Attributes and Elements</span></span>  
 <span data-ttu-id="2d263-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2d263-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2d263-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2d263-113">Attributes</span></span>  
  
|<span data-ttu-id="2d263-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2d263-114">Attribute</span></span>|<span data-ttu-id="2d263-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2d263-115">Description</span></span>|  
|---------------|-----------------|  
|`url`|<span data-ttu-id="2d263-116">Gizlilik bildirimi bulunduğu olduğu URI belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="2d263-116">A string that specifies the URI at which the privacy notice is located.</span></span>|  
|`version`|<span data-ttu-id="2d263-117">Bu gizlilik bildirimi sürümünü belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="2d263-117">An integer that specifies the version of this privacy notice.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2d263-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2d263-118">Child Elements</span></span>  
 <span data-ttu-id="2d263-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="2d263-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2d263-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2d263-120">Parent Elements</span></span>  
  
|<span data-ttu-id="2d263-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="2d263-121">Element</span></span>|<span data-ttu-id="2d263-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2d263-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2d263-123">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="2d263-123">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="2d263-124">Özel bağlama tüm bağlama özelliklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2d263-124">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2d263-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2d263-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PrivacyNoticeElement>  
 <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="2d263-126">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="2d263-126">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="2d263-127">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="2d263-127">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="2d263-128">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="2d263-128">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="2d263-129">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="2d263-129">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)

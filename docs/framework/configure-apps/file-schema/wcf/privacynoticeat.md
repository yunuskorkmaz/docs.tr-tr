---
title: <privacyNoticeAt>
ms.date: 03/30/2017
ms.assetid: 4cc96942-4eb9-4241-b2fd-45aa239915e8
ms.openlocfilehash: b1de2a304a5dc4295497ea1f3b395240cb5ca9bc
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55254928"
---
# <a name="privacynoticeat"></a><span data-ttu-id="7871e-101">\<privacyNoticeAt ></span><span class="sxs-lookup"><span data-stu-id="7871e-101">\<privacyNoticeAt></span></span>
<span data-ttu-id="7871e-102">Kullanılan bir gizlilik bildirimini belirten bir yapılandırma öğesini temsil eder `wsFederationHttp` bağlama.</span><span class="sxs-lookup"><span data-stu-id="7871e-102">Represents a configuration element that specifies a privacy notice used in `wsFederationHttp` binding.</span></span>  
  
 <span data-ttu-id="7871e-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="7871e-103">\<system.serviceModel></span></span>  
<span data-ttu-id="7871e-104">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="7871e-104">\<bindings></span></span>  
<span data-ttu-id="7871e-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="7871e-105">\<customBinding></span></span>  
<span data-ttu-id="7871e-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="7871e-106">\<binding></span></span>  
<span data-ttu-id="7871e-107">\<privacyNotice ></span><span class="sxs-lookup"><span data-stu-id="7871e-107">\<privacyNotice></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7871e-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7871e-108">Syntax</span></span>  
  
```xml  
<privacyNotice url="String"
               version="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="7871e-109">Tür</span><span class="sxs-lookup"><span data-stu-id="7871e-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7871e-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7871e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7871e-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7871e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7871e-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7871e-112">Attributes</span></span>  
  
|<span data-ttu-id="7871e-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7871e-113">Attribute</span></span>|<span data-ttu-id="7871e-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7871e-114">Description</span></span>|  
|---------------|-----------------|  
|`url`|<span data-ttu-id="7871e-115">Gizlilik bildirimini bulunduğu URI belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="7871e-115">A string that specifies the URI at which the privacy notice is located.</span></span>|  
|`version`|<span data-ttu-id="7871e-116">Bu gizlilik bildiriminin sürümü belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="7871e-116">An integer that specifies the version of this privacy notice.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7871e-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7871e-117">Child Elements</span></span>  
 <span data-ttu-id="7871e-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="7871e-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7871e-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7871e-119">Parent Elements</span></span>  
  
|<span data-ttu-id="7871e-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="7871e-120">Element</span></span>|<span data-ttu-id="7871e-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7871e-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7871e-122">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="7871e-122">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="7871e-123">Özel bağlama tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7871e-123">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7871e-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7871e-124">See also</span></span>
- <xref:System.ServiceModel.Configuration.PrivacyNoticeElement>
- <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="7871e-125">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="7871e-125">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="7871e-126">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="7871e-126">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="7871e-127">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="7871e-127">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="7871e-128">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="7871e-128">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)

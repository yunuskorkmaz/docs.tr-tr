---
title: <privacyNoticeAt>
ms.date: 03/30/2017
ms.assetid: 4cc96942-4eb9-4241-b2fd-45aa239915e8
ms.openlocfilehash: e2ce2111e4bb26cc6a51b4a772b1d8a4d3238c70
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59200772"
---
# <a name="privacynoticeat"></a><span data-ttu-id="7b1e7-101">\<privacyNoticeAt ></span><span class="sxs-lookup"><span data-stu-id="7b1e7-101">\<privacyNoticeAt></span></span>
<span data-ttu-id="7b1e7-102">Kullanılan bir gizlilik bildirimini belirten bir yapılandırma öğesini temsil eder `wsFederationHttp` bağlama.</span><span class="sxs-lookup"><span data-stu-id="7b1e7-102">Represents a configuration element that specifies a privacy notice used in `wsFederationHttp` binding.</span></span>  
  
 <span data-ttu-id="7b1e7-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="7b1e7-103">\<system.serviceModel></span></span>  
<span data-ttu-id="7b1e7-104">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="7b1e7-104">\<bindings></span></span>  
<span data-ttu-id="7b1e7-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="7b1e7-105">\<customBinding></span></span>  
<span data-ttu-id="7b1e7-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="7b1e7-106">\<binding></span></span>  
<span data-ttu-id="7b1e7-107">\<privacyNotice ></span><span class="sxs-lookup"><span data-stu-id="7b1e7-107">\<privacyNotice></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b1e7-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7b1e7-108">Syntax</span></span>  
  
```xml  
<privacyNotice url="String"
               version="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="7b1e7-109">Tür</span><span class="sxs-lookup"><span data-stu-id="7b1e7-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7b1e7-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7b1e7-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7b1e7-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7b1e7-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7b1e7-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7b1e7-112">Attributes</span></span>  
  
|<span data-ttu-id="7b1e7-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7b1e7-113">Attribute</span></span>|<span data-ttu-id="7b1e7-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7b1e7-114">Description</span></span>|  
|---------------|-----------------|  
|`url`|<span data-ttu-id="7b1e7-115">Gizlilik bildirimini bulunduğu URI belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="7b1e7-115">A string that specifies the URI at which the privacy notice is located.</span></span>|  
|`version`|<span data-ttu-id="7b1e7-116">Bu gizlilik bildiriminin sürümü belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="7b1e7-116">An integer that specifies the version of this privacy notice.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7b1e7-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7b1e7-117">Child Elements</span></span>  
 <span data-ttu-id="7b1e7-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="7b1e7-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7b1e7-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7b1e7-119">Parent Elements</span></span>  
  
|<span data-ttu-id="7b1e7-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="7b1e7-120">Element</span></span>|<span data-ttu-id="7b1e7-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7b1e7-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7b1e7-122">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="7b1e7-122">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="7b1e7-123">Özel bağlama tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7b1e7-123">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7b1e7-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7b1e7-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.PrivacyNoticeElement>
- <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="7b1e7-125">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="7b1e7-125">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="7b1e7-126">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="7b1e7-126">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="7b1e7-127">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="7b1e7-127">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="7b1e7-128">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="7b1e7-128">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)

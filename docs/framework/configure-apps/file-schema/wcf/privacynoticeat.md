---
title: <privacyNoticeAt>
ms.date: 03/30/2017
ms.assetid: 4cc96942-4eb9-4241-b2fd-45aa239915e8
ms.openlocfilehash: f7349bf61082c5d8e5bd4249e01b8835a1861cb9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934255"
---
# <a name="privacynoticeat"></a><span data-ttu-id="38115-101">\<privacyNoticeAt ></span><span class="sxs-lookup"><span data-stu-id="38115-101">\<privacyNoticeAt></span></span>
<span data-ttu-id="38115-102">`wsFederationHttp` Bağlamada kullanılan gizlilik bildirimini belirten bir yapılandırma öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="38115-102">Represents a configuration element that specifies a privacy notice used in `wsFederationHttp` binding.</span></span>  
  
 <span data-ttu-id="38115-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="38115-103">\<system.serviceModel></span></span>  
<span data-ttu-id="38115-104">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="38115-104">\<bindings></span></span>  
<span data-ttu-id="38115-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="38115-105">\<customBinding></span></span>  
<span data-ttu-id="38115-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="38115-106">\<binding></span></span>  
<span data-ttu-id="38115-107">\<Privacybildirimin ></span><span class="sxs-lookup"><span data-stu-id="38115-107">\<privacyNotice></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38115-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="38115-108">Syntax</span></span>  
  
```xml  
<privacyNotice url="String"
               version="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="38115-109">Tür</span><span class="sxs-lookup"><span data-stu-id="38115-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="38115-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="38115-110">Attributes and Elements</span></span>  
 <span data-ttu-id="38115-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="38115-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="38115-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="38115-112">Attributes</span></span>  
  
|<span data-ttu-id="38115-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="38115-113">Attribute</span></span>|<span data-ttu-id="38115-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="38115-114">Description</span></span>|  
|---------------|-----------------|  
|`url`|<span data-ttu-id="38115-115">Gizlilik bildiriminin bulunduğu URI 'Yı belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="38115-115">A string that specifies the URI at which the privacy notice is located.</span></span>|  
|`version`|<span data-ttu-id="38115-116">Bu gizlilik bildiriminin sürümünü belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="38115-116">An integer that specifies the version of this privacy notice.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="38115-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="38115-117">Child Elements</span></span>  
 <span data-ttu-id="38115-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="38115-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="38115-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="38115-119">Parent Elements</span></span>  
  
|<span data-ttu-id="38115-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="38115-120">Element</span></span>|<span data-ttu-id="38115-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="38115-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="38115-122">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="38115-122">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="38115-123">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="38115-123">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="38115-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="38115-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.PrivacyNoticeElement>
- <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="38115-125">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="38115-125">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="38115-126">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="38115-126">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="38115-127">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="38115-127">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="38115-128">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="38115-128">\<customBinding></span></span>](custombinding.md)

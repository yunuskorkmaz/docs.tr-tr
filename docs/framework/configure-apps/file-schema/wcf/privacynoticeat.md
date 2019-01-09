---
title: '&lt;privacyNoticeAt&gt;'
ms.date: 03/30/2017
ms.assetid: 4cc96942-4eb9-4241-b2fd-45aa239915e8
ms.openlocfilehash: 104b2b6399ea31273045e43be716947db110715d
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147323"
---
# <a name="ltprivacynoticeatgt"></a><span data-ttu-id="7b85b-102">&lt;privacyNoticeAt&gt;</span><span class="sxs-lookup"><span data-stu-id="7b85b-102">&lt;privacyNoticeAt&gt;</span></span>
<span data-ttu-id="7b85b-103">Kullanılan bir gizlilik bildirimini belirten bir yapılandırma öğesini temsil eder `wsFederationHttp` bağlama.</span><span class="sxs-lookup"><span data-stu-id="7b85b-103">Represents a configuration element that specifies a privacy notice used in `wsFederationHttp` binding.</span></span>  
  
 <span data-ttu-id="7b85b-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="7b85b-104">\<system.serviceModel></span></span>  
<span data-ttu-id="7b85b-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="7b85b-105">\<bindings></span></span>  
<span data-ttu-id="7b85b-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="7b85b-106">\<customBinding></span></span>  
<span data-ttu-id="7b85b-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="7b85b-107">\<binding></span></span>  
<span data-ttu-id="7b85b-108">\<privacyNotice ></span><span class="sxs-lookup"><span data-stu-id="7b85b-108">\<privacyNotice></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b85b-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7b85b-109">Syntax</span></span>  
  
```xml  
<privacyNotice url="String"
               version="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="7b85b-110">Tür</span><span class="sxs-lookup"><span data-stu-id="7b85b-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7b85b-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7b85b-111">Attributes and Elements</span></span>  
 <span data-ttu-id="7b85b-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7b85b-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7b85b-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7b85b-113">Attributes</span></span>  
  
|<span data-ttu-id="7b85b-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7b85b-114">Attribute</span></span>|<span data-ttu-id="7b85b-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7b85b-115">Description</span></span>|  
|---------------|-----------------|  
|`url`|<span data-ttu-id="7b85b-116">Gizlilik bildirimini bulunduğu URI belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="7b85b-116">A string that specifies the URI at which the privacy notice is located.</span></span>|  
|`version`|<span data-ttu-id="7b85b-117">Bu gizlilik bildiriminin sürümü belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="7b85b-117">An integer that specifies the version of this privacy notice.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7b85b-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7b85b-118">Child Elements</span></span>  
 <span data-ttu-id="7b85b-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="7b85b-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7b85b-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7b85b-120">Parent Elements</span></span>  
  
|<span data-ttu-id="7b85b-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="7b85b-121">Element</span></span>|<span data-ttu-id="7b85b-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7b85b-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7b85b-123">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="7b85b-123">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="7b85b-124">Özel bağlama tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7b85b-124">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7b85b-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7b85b-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PrivacyNoticeElement>  
 <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="7b85b-126">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="7b85b-126">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="7b85b-127">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="7b85b-127">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="7b85b-128">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="7b85b-128">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="7b85b-129">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="7b85b-129">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)

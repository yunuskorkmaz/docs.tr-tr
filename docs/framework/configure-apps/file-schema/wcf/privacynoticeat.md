---
title: <privacyNoticeAt>
ms.date: 03/30/2017
ms.assetid: 4cc96942-4eb9-4241-b2fd-45aa239915e8
ms.openlocfilehash: 2ff70d3a8636970434582e417e4549ab6b433fc1
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738768"
---
# <a name="privacynoticeat"></a><span data-ttu-id="f532d-101">\<privacyNoticeAt ></span><span class="sxs-lookup"><span data-stu-id="f532d-101">\<privacyNoticeAt></span></span>
<span data-ttu-id="f532d-102">`wsFederationHttp` bağlamasında kullanılan gizlilik bildirimini belirten bir yapılandırma öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f532d-102">Represents a configuration element that specifies a privacy notice used in `wsFederationHttp` binding.</span></span>  
  
<span data-ttu-id="f532d-103">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="f532d-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f532d-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="f532d-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="f532d-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlamaları >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="f532d-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="f532d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="f532d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="f532d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="f532d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="f532d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Privacybildirimin >**</span><span class="sxs-lookup"><span data-stu-id="f532d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<privacyNotice>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f532d-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f532d-109">Syntax</span></span>  
  
```xml  
<privacyNotice url="String"
               version="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="f532d-110">Tür</span><span class="sxs-lookup"><span data-stu-id="f532d-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f532d-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f532d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="f532d-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f532d-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f532d-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f532d-113">Attributes</span></span>  
  
|<span data-ttu-id="f532d-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f532d-114">Attribute</span></span>|<span data-ttu-id="f532d-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f532d-115">Description</span></span>|  
|---------------|-----------------|  
|`url`|<span data-ttu-id="f532d-116">Gizlilik bildiriminin bulunduğu URI 'Yı belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="f532d-116">A string that specifies the URI at which the privacy notice is located.</span></span>|  
|`version`|<span data-ttu-id="f532d-117">Bu gizlilik bildiriminin sürümünü belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="f532d-117">An integer that specifies the version of this privacy notice.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f532d-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f532d-118">Child Elements</span></span>  
 <span data-ttu-id="f532d-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="f532d-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f532d-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f532d-120">Parent Elements</span></span>  
  
|<span data-ttu-id="f532d-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="f532d-121">Element</span></span>|<span data-ttu-id="f532d-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f532d-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f532d-123">\< bağlama ></span><span class="sxs-lookup"><span data-stu-id="f532d-123">\<binding></span></span>](bindings.md)|<span data-ttu-id="f532d-124">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f532d-124">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f532d-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f532d-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.PrivacyNoticeElement>
- <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="f532d-126">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="f532d-126">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f532d-127">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="f532d-127">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="f532d-128">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="f532d-128">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="f532d-129">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="f532d-129">\<customBinding></span></span>](custombinding.md)

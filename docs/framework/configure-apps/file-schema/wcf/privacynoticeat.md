---
description: 'Hakkında daha fazla bilgi edinin: <privacyNoticeAt>'
title: <privacyNoticeAt>
ms.date: 03/30/2017
ms.assetid: 4cc96942-4eb9-4241-b2fd-45aa239915e8
ms.openlocfilehash: 2e38d43becd783cc50afba5a029d3ab9905ec15a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683508"
---
# \<privacyNoticeAt>

<span data-ttu-id="4cf97-102">Bağlamada kullanılan gizlilik bildirimini belirten bir yapılandırma öğesini temsil eder `wsFederationHttp` .</span><span class="sxs-lookup"><span data-stu-id="4cf97-102">Represents a configuration element that specifies a privacy notice used in `wsFederationHttp` binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<privacyNotice>**  
  
## <a name="syntax"></a><span data-ttu-id="4cf97-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="4cf97-103">Syntax</span></span>  
  
```xml  
<privacyNotice url="String"
               version="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="4cf97-104">Tür</span><span class="sxs-lookup"><span data-stu-id="4cf97-104">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4cf97-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4cf97-105">Attributes and Elements</span></span>  

 <span data-ttu-id="4cf97-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4cf97-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4cf97-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4cf97-107">Attributes</span></span>  
  
|<span data-ttu-id="4cf97-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4cf97-108">Attribute</span></span>|<span data-ttu-id="4cf97-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4cf97-109">Description</span></span>|  
|---------------|-----------------|  
|`url`|<span data-ttu-id="4cf97-110">Gizlilik bildiriminin bulunduğu URI 'Yı belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="4cf97-110">A string that specifies the URI at which the privacy notice is located.</span></span>|  
|`version`|<span data-ttu-id="4cf97-111">Bu gizlilik bildiriminin sürümünü belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="4cf97-111">An integer that specifies the version of this privacy notice.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4cf97-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4cf97-112">Child Elements</span></span>  

 <span data-ttu-id="4cf97-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="4cf97-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4cf97-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4cf97-114">Parent Elements</span></span>  
  
|<span data-ttu-id="4cf97-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="4cf97-115">Element</span></span>|<span data-ttu-id="4cf97-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4cf97-116">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="4cf97-117">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4cf97-117">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4cf97-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4cf97-118">See also</span></span>

- <xref:System.ServiceModel.Configuration.PrivacyNoticeElement>
- <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="4cf97-119">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="4cf97-119">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="4cf97-120">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="4cf97-120">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="4cf97-121">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="4cf97-121">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)

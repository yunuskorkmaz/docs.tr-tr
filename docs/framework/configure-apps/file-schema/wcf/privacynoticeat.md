---
title: <privacyNoticeAt>
ms.date: 03/30/2017
ms.assetid: 4cc96942-4eb9-4241-b2fd-45aa239915e8
ms.openlocfilehash: 2ff70d3a8636970434582e417e4549ab6b433fc1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738768"
---
# \<privacyNoticeAt>
<span data-ttu-id="6a022-101">Bağlamada kullanılan gizlilik bildirimini belirten bir yapılandırma öğesini temsil eder `wsFederationHttp` .</span><span class="sxs-lookup"><span data-stu-id="6a022-101">Represents a configuration element that specifies a privacy notice used in `wsFederationHttp` binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<privacyNotice>**  
  
## <a name="syntax"></a><span data-ttu-id="6a022-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6a022-102">Syntax</span></span>  
  
```xml  
<privacyNotice url="String"
               version="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="6a022-103">Tür</span><span class="sxs-lookup"><span data-stu-id="6a022-103">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6a022-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6a022-104">Attributes and Elements</span></span>  
 <span data-ttu-id="6a022-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6a022-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6a022-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6a022-106">Attributes</span></span>  
  
|<span data-ttu-id="6a022-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6a022-107">Attribute</span></span>|<span data-ttu-id="6a022-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6a022-108">Description</span></span>|  
|---------------|-----------------|  
|`url`|<span data-ttu-id="6a022-109">Gizlilik bildiriminin bulunduğu URI 'Yı belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="6a022-109">A string that specifies the URI at which the privacy notice is located.</span></span>|  
|`version`|<span data-ttu-id="6a022-110">Bu gizlilik bildiriminin sürümünü belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="6a022-110">An integer that specifies the version of this privacy notice.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6a022-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6a022-111">Child Elements</span></span>  
 <span data-ttu-id="6a022-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="6a022-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6a022-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6a022-113">Parent Elements</span></span>  
  
|<span data-ttu-id="6a022-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="6a022-114">Element</span></span>|<span data-ttu-id="6a022-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6a022-115">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="6a022-116">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6a022-116">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6a022-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a022-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.PrivacyNoticeElement>
- <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="6a022-118">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="6a022-118">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="6a022-119">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="6a022-119">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="6a022-120">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="6a022-120">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)

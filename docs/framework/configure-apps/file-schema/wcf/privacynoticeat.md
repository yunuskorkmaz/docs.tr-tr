---
title: <privacyNoticeAt>
ms.date: 03/30/2017
ms.assetid: 4cc96942-4eb9-4241-b2fd-45aa239915e8
ms.openlocfilehash: 5e772e23b21c566c906be854e33b924698dcf3e0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158714"
---
# \<privacyNoticeAt>

<span data-ttu-id="fb04e-101">Bağlamada kullanılan gizlilik bildirimini belirten bir yapılandırma öğesini temsil eder `wsFederationHttp` .</span><span class="sxs-lookup"><span data-stu-id="fb04e-101">Represents a configuration element that specifies a privacy notice used in `wsFederationHttp` binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<privacyNotice>**  
  
## <a name="syntax"></a><span data-ttu-id="fb04e-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="fb04e-102">Syntax</span></span>  
  
```xml  
<privacyNotice url="String"
               version="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="fb04e-103">Tür</span><span class="sxs-lookup"><span data-stu-id="fb04e-103">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fb04e-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fb04e-104">Attributes and Elements</span></span>  

 <span data-ttu-id="fb04e-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fb04e-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fb04e-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fb04e-106">Attributes</span></span>  
  
|<span data-ttu-id="fb04e-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fb04e-107">Attribute</span></span>|<span data-ttu-id="fb04e-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fb04e-108">Description</span></span>|  
|---------------|-----------------|  
|`url`|<span data-ttu-id="fb04e-109">Gizlilik bildiriminin bulunduğu URI 'Yı belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="fb04e-109">A string that specifies the URI at which the privacy notice is located.</span></span>|  
|`version`|<span data-ttu-id="fb04e-110">Bu gizlilik bildiriminin sürümünü belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="fb04e-110">An integer that specifies the version of this privacy notice.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fb04e-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fb04e-111">Child Elements</span></span>  

 <span data-ttu-id="fb04e-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="fb04e-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fb04e-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fb04e-113">Parent Elements</span></span>  
  
|<span data-ttu-id="fb04e-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="fb04e-114">Element</span></span>|<span data-ttu-id="fb04e-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fb04e-115">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="fb04e-116">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fb04e-116">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fb04e-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fb04e-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.PrivacyNoticeElement>
- <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="fb04e-118">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="fb04e-118">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="fb04e-119">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="fb04e-119">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="fb04e-120">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="fb04e-120">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)

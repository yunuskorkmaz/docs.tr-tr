---
description: 'Hakkında daha fazla bilgi edinin: <useManagedPresentation>'
title: <useManagedPresentation>
ms.date: 03/30/2017
ms.assetid: 17a0dd77-af54-41db-a9d0-4b17ff42878f
ms.openlocfilehash: 9203daedcc0553c7a1308b2763b9e818ca6560c1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749044"
---
# \<useManagedPresentation>

<span data-ttu-id="4aa83-102">WS-Trust CardSpace profilini destekleyen bir CardSpace güvenlik belirteci hizmeti ile iletişim kurmak için kullanılan bağlama öğesi.</span><span class="sxs-lookup"><span data-stu-id="4aa83-102">A binding element used to communicate with a CardSpace Security Token Service that supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="4aa83-103">Bu öğenin bir özniteliği yok ve boş bir anahtar olarak var.</span><span class="sxs-lookup"><span data-stu-id="4aa83-103">This element has no attribute and is present as an empty switch.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<useManagedPresentation>**  
  
## <a name="syntax"></a><span data-ttu-id="4aa83-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="4aa83-104">Syntax</span></span>  
  
```xml  
<useManagedPresentation />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4aa83-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4aa83-105">Attributes and Elements</span></span>  

 <span data-ttu-id="4aa83-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4aa83-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4aa83-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4aa83-107">Attributes</span></span>  

 <span data-ttu-id="4aa83-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="4aa83-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4aa83-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4aa83-109">Child Elements</span></span>  

 <span data-ttu-id="4aa83-110">Yok</span><span class="sxs-lookup"><span data-stu-id="4aa83-110">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4aa83-111">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4aa83-111">Parent Elements</span></span>  
  
|<span data-ttu-id="4aa83-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="4aa83-112">Element</span></span>|<span data-ttu-id="4aa83-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4aa83-113">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="4aa83-114">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4aa83-114">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4aa83-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4aa83-115">Remarks</span></span>  

 <span data-ttu-id="4aa83-116">Bu öğe, bir kimlik sağlayıcısı tarafından ilkesinde, WS-Trust ' ın CardSpace profilini desteklediği gerçeğini ifade etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4aa83-116">This element is used by an identity provider to express in its policy the fact that it supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="4aa83-117">Bu tür bir ilke onayını yayınlayan kimlik sağlayıcılarının, söz konusu CardSpace profilini temel alan belirteçler yayınlayabilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="4aa83-117">Identity providers that publish such a policy assertion should be able to issue tokens based on that CardSpace profile.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4aa83-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4aa83-118">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseManagedPresentationElement>
- <xref:System.ServiceModel.Channels.UseManagedPresentationBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="4aa83-119">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="4aa83-119">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="4aa83-120">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="4aa83-120">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="4aa83-121">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="4aa83-121">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)

---
title: <useManagedPresentation>
ms.date: 03/30/2017
ms.assetid: 17a0dd77-af54-41db-a9d0-4b17ff42878f
ms.openlocfilehash: 86a6f975b05133d5f9f21fcfb82ef4c23d2ffaba
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148818"
---
# \<useManagedPresentation>

<span data-ttu-id="2b132-101">WS-Trust CardSpace profilini destekleyen bir CardSpace güvenlik belirteci hizmeti ile iletişim kurmak için kullanılan bağlama öğesi.</span><span class="sxs-lookup"><span data-stu-id="2b132-101">A binding element used to communicate with a CardSpace Security Token Service that supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="2b132-102">Bu öğenin bir özniteliği yok ve boş bir anahtar olarak var.</span><span class="sxs-lookup"><span data-stu-id="2b132-102">This element has no attribute and is present as an empty switch.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<useManagedPresentation>**  
  
## <a name="syntax"></a><span data-ttu-id="2b132-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="2b132-103">Syntax</span></span>  
  
```xml  
<useManagedPresentation />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2b132-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2b132-104">Attributes and Elements</span></span>  

 <span data-ttu-id="2b132-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2b132-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2b132-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2b132-106">Attributes</span></span>  

 <span data-ttu-id="2b132-107">Yok.</span><span class="sxs-lookup"><span data-stu-id="2b132-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2b132-108">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2b132-108">Child Elements</span></span>  

 <span data-ttu-id="2b132-109">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="2b132-109">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2b132-110">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2b132-110">Parent Elements</span></span>  
  
|<span data-ttu-id="2b132-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="2b132-111">Element</span></span>|<span data-ttu-id="2b132-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2b132-112">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="2b132-113">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2b132-113">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b132-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2b132-114">Remarks</span></span>  

 <span data-ttu-id="2b132-115">Bu öğe, bir kimlik sağlayıcısı tarafından ilkesinde, WS-Trust ' ın CardSpace profilini desteklediği gerçeğini ifade etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2b132-115">This element is used by an identity provider to express in its policy the fact that it supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="2b132-116">Bu tür bir ilke onayını yayınlayan kimlik sağlayıcılarının, söz konusu CardSpace profilini temel alan belirteçler yayınlayabilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="2b132-116">Identity providers that publish such a policy assertion should be able to issue tokens based on that CardSpace profile.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b132-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2b132-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseManagedPresentationElement>
- <xref:System.ServiceModel.Channels.UseManagedPresentationBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="2b132-118">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="2b132-118">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="2b132-119">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="2b132-119">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="2b132-120">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="2b132-120">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)

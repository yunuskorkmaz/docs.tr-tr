---
title: <serviceAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 5d69e64f-f325-4d55-8e2d-0fb30f222dda
ms.openlocfilehash: cc5ebcf36a10e88d48ed14f1f10dac6396d7b242
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399702"
---
# <a name="serviceauthenticationmanager"></a><span data-ttu-id="8a61a-101">\<serviceAuthenticationManager ></span><span class="sxs-lookup"><span data-stu-id="8a61a-101">\<serviceAuthenticationManager></span></span>
<span data-ttu-id="8a61a-102">, Hizmet düzeyinde bir iletim, ileti veya gönderen için geçerliliği belirleyen bir iş akışı yapılandırma öğesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="8a61a-102">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator.</span></span>  
  
<span data-ttu-id="8a61a-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8a61a-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8a61a-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="8a61a-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="8a61a-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="8a61a-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="8a61a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Servicedavranışlar >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="8a61a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="8a61a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="8a61a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="8a61a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<serviceAuthenticationManager >**</span><span class="sxs-lookup"><span data-stu-id="8a61a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceAuthenticationManager>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a61a-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8a61a-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8a61a-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8a61a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8a61a-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8a61a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8a61a-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8a61a-112">Attributes</span></span>  
  
|<span data-ttu-id="8a61a-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8a61a-113">Attribute</span></span>|<span data-ttu-id="8a61a-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8a61a-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8a61a-115">serviceAuthenticationManagerType</span><span class="sxs-lookup"><span data-stu-id="8a61a-115">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="8a61a-116">Geçerli davranış için kimlik doğrulama ilkesinin türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="8a61a-116">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8a61a-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8a61a-117">Child Elements</span></span>  
 <span data-ttu-id="8a61a-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="8a61a-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8a61a-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8a61a-119">Parent Elements</span></span>  
  
|<span data-ttu-id="8a61a-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="8a61a-120">Element</span></span>|<span data-ttu-id="8a61a-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8a61a-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8a61a-122">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="8a61a-122">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="8a61a-123">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="8a61a-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8a61a-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8a61a-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>

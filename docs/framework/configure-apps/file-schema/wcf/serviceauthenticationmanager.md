---
title: <serviceAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 5d69e64f-f325-4d55-8e2d-0fb30f222dda
ms.openlocfilehash: a7c1e06c74bd3ba62d52ef833b8ffb6a8fd594fb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167177"
---
# \<serviceAuthenticationManager>

<span data-ttu-id="c04ba-101">, Hizmet düzeyinde bir iletim, ileti veya gönderen için geçerliliği belirleyen bir iş akışı yapılandırma öğesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c04ba-101">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceAuthenticationManager>**  
  
## <a name="syntax"></a><span data-ttu-id="c04ba-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="c04ba-102">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c04ba-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c04ba-103">Attributes and Elements</span></span>  

 <span data-ttu-id="c04ba-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c04ba-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c04ba-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c04ba-105">Attributes</span></span>  
  
|<span data-ttu-id="c04ba-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c04ba-106">Attribute</span></span>|<span data-ttu-id="c04ba-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c04ba-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c04ba-108">serviceAuthenticationManagerType</span><span class="sxs-lookup"><span data-stu-id="c04ba-108">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="c04ba-109">Geçerli davranış için kimlik doğrulama ilkesinin türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="c04ba-109">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c04ba-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c04ba-110">Child Elements</span></span>  

 <span data-ttu-id="c04ba-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="c04ba-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c04ba-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c04ba-112">Parent Elements</span></span>  
  
|<span data-ttu-id="c04ba-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="c04ba-113">Element</span></span>|<span data-ttu-id="c04ba-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c04ba-114">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="c04ba-115">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="c04ba-115">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c04ba-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c04ba-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>

---
description: 'Hakkında daha fazla bilgi edinin: <serviceAuthenticationManager>'
title: <serviceAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 5d69e64f-f325-4d55-8e2d-0fb30f222dda
ms.openlocfilehash: ae9c8d7f74b3ad7d0c61a77d20f38f228c695970
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786778"
---
# \<serviceAuthenticationManager>

<span data-ttu-id="02602-102">, Hizmet düzeyinde bir iletim, ileti veya gönderen için geçerliliği belirleyen bir iş akışı yapılandırma öğesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="02602-102">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceAuthenticationManager>**  
  
## <a name="syntax"></a><span data-ttu-id="02602-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="02602-103">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="02602-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="02602-104">Attributes and Elements</span></span>  

 <span data-ttu-id="02602-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="02602-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="02602-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="02602-106">Attributes</span></span>  
  
|<span data-ttu-id="02602-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="02602-107">Attribute</span></span>|<span data-ttu-id="02602-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="02602-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="02602-109">serviceAuthenticationManagerType</span><span class="sxs-lookup"><span data-stu-id="02602-109">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="02602-110">Geçerli davranış için kimlik doğrulama ilkesinin türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="02602-110">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="02602-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="02602-111">Child Elements</span></span>  

 <span data-ttu-id="02602-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="02602-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="02602-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="02602-113">Parent Elements</span></span>  
  
|<span data-ttu-id="02602-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="02602-114">Element</span></span>|<span data-ttu-id="02602-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="02602-115">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="02602-116">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="02602-116">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="02602-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="02602-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>

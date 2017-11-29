---
title: '&lt;serviceAuthenticationManager&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5d69e64f-f325-4d55-8e2d-0fb30f222dda
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2385b96460e0a3d53efb62054fb7da334ddd2d49
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ltserviceauthenticationmanagergt"></a><span data-ttu-id="8060f-102">&lt;serviceAuthenticationManager&gt;</span><span class="sxs-lookup"><span data-stu-id="8060f-102">&lt;serviceAuthenticationManager&gt;</span></span>
<span data-ttu-id="8060f-103">Hizmet düzeyinde iletim, ileti veya başlatanın geçerliliğini oluşturur. iş akışı yapılandırma öğesi sağlar...</span><span class="sxs-lookup"><span data-stu-id="8060f-103">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator..</span></span>  
  
<span data-ttu-id="8060f-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="8060f-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="8060f-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="8060f-105">\<behaviors></span></span>  
<span data-ttu-id="8060f-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="8060f-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="8060f-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="8060f-107">\<behavior></span></span>  
<span data-ttu-id="8060f-108">\<serviceAuthenticationManager ></span><span class="sxs-lookup"><span data-stu-id="8060f-108">\<serviceAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8060f-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8060f-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8060f-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8060f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8060f-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8060f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8060f-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8060f-112">Attributes</span></span>  
  
|<span data-ttu-id="8060f-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8060f-113">Attribute</span></span>|<span data-ttu-id="8060f-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8060f-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8060f-115">serviceAuthenticationManagerType</span><span class="sxs-lookup"><span data-stu-id="8060f-115">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="8060f-116">Şu anki davranışı kimlik doğrulama İlkesi türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="8060f-116">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8060f-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8060f-117">Child Elements</span></span>  
 <span data-ttu-id="8060f-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="8060f-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8060f-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8060f-119">Parent Elements</span></span>  
  
|<span data-ttu-id="8060f-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="8060f-120">Element</span></span>|<span data-ttu-id="8060f-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8060f-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8060f-122">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="8060f-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="8060f-123">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="8060f-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8060f-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8060f-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>

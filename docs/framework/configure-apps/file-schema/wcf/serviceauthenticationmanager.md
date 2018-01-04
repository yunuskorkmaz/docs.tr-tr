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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b46df4f069259ae4bb2d2769e20c6ad9e6090c00
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltserviceauthenticationmanagergt"></a><span data-ttu-id="9cc97-102">&lt;serviceAuthenticationManager&gt;</span><span class="sxs-lookup"><span data-stu-id="9cc97-102">&lt;serviceAuthenticationManager&gt;</span></span>
<span data-ttu-id="9cc97-103">Hizmet düzeyinde iletim, ileti veya başlatanın geçerliliğini oluşturur. iş akışı yapılandırma öğesi sağlar...</span><span class="sxs-lookup"><span data-stu-id="9cc97-103">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator..</span></span>  
  
<span data-ttu-id="9cc97-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="9cc97-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="9cc97-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="9cc97-105">\<behaviors></span></span>  
<span data-ttu-id="9cc97-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="9cc97-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="9cc97-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="9cc97-107">\<behavior></span></span>  
<span data-ttu-id="9cc97-108">\<serviceAuthenticationManager ></span><span class="sxs-lookup"><span data-stu-id="9cc97-108">\<serviceAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cc97-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9cc97-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9cc97-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9cc97-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9cc97-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9cc97-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9cc97-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9cc97-112">Attributes</span></span>  
  
|<span data-ttu-id="9cc97-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9cc97-113">Attribute</span></span>|<span data-ttu-id="9cc97-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9cc97-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9cc97-115">serviceAuthenticationManagerType</span><span class="sxs-lookup"><span data-stu-id="9cc97-115">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="9cc97-116">Şu anki davranışı kimlik doğrulama İlkesi türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="9cc97-116">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9cc97-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9cc97-117">Child Elements</span></span>  
 <span data-ttu-id="9cc97-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="9cc97-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9cc97-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9cc97-119">Parent Elements</span></span>  
  
|<span data-ttu-id="9cc97-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="9cc97-120">Element</span></span>|<span data-ttu-id="9cc97-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9cc97-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9cc97-122">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="9cc97-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="9cc97-123">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="9cc97-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9cc97-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9cc97-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>

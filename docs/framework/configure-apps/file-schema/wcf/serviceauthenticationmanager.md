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
ms.openlocfilehash: 077878ae1746008532c3bee6b12913f98afc343f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltserviceauthenticationmanagergt"></a><span data-ttu-id="fcffe-102">&lt;serviceAuthenticationManager&gt;</span><span class="sxs-lookup"><span data-stu-id="fcffe-102">&lt;serviceAuthenticationManager&gt;</span></span>
<span data-ttu-id="fcffe-103">Hizmet düzeyinde iletim, ileti veya başlatanın geçerliliğini oluşturur. iş akışı yapılandırma öğesi sağlar...</span><span class="sxs-lookup"><span data-stu-id="fcffe-103">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator..</span></span>  
  
<span data-ttu-id="fcffe-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="fcffe-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="fcffe-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="fcffe-105">\<behaviors></span></span>  
<span data-ttu-id="fcffe-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="fcffe-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="fcffe-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="fcffe-107">\<behavior></span></span>  
<span data-ttu-id="fcffe-108">\<serviceAuthenticationManager ></span><span class="sxs-lookup"><span data-stu-id="fcffe-108">\<serviceAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcffe-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fcffe-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fcffe-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fcffe-110">Attributes and Elements</span></span>  
 <span data-ttu-id="fcffe-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fcffe-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fcffe-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fcffe-112">Attributes</span></span>  
  
|<span data-ttu-id="fcffe-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fcffe-113">Attribute</span></span>|<span data-ttu-id="fcffe-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fcffe-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fcffe-115">serviceAuthenticationManagerType</span><span class="sxs-lookup"><span data-stu-id="fcffe-115">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="fcffe-116">Şu anki davranışı kimlik doğrulama İlkesi türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="fcffe-116">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fcffe-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fcffe-117">Child Elements</span></span>  
 <span data-ttu-id="fcffe-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="fcffe-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fcffe-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fcffe-119">Parent Elements</span></span>  
  
|<span data-ttu-id="fcffe-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="fcffe-120">Element</span></span>|<span data-ttu-id="fcffe-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fcffe-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fcffe-122">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="fcffe-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="fcffe-123">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="fcffe-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fcffe-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fcffe-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>

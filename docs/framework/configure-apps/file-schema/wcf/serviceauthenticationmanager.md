---
title: '&lt;serviceAuthenticationManager&gt;'
ms.date: 03/30/2017
ms.assetid: 5d69e64f-f325-4d55-8e2d-0fb30f222dda
ms.openlocfilehash: 3b58214a1fd7a50fb1a9ab3dfee0a14870f8a476
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltserviceauthenticationmanagergt"></a><span data-ttu-id="7bdd3-102">&lt;serviceAuthenticationManager&gt;</span><span class="sxs-lookup"><span data-stu-id="7bdd3-102">&lt;serviceAuthenticationManager&gt;</span></span>
<span data-ttu-id="7bdd3-103">Hizmet düzeyinde iletim, ileti veya başlatanın geçerliliğini oluşturur. iş akışı yapılandırma öğesi sağlar...</span><span class="sxs-lookup"><span data-stu-id="7bdd3-103">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator..</span></span>  
  
<span data-ttu-id="7bdd3-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7bdd3-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7bdd3-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="7bdd3-105">\<behaviors></span></span>  
<span data-ttu-id="7bdd3-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="7bdd3-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="7bdd3-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="7bdd3-107">\<behavior></span></span>  
<span data-ttu-id="7bdd3-108">\<serviceAuthenticationManager ></span><span class="sxs-lookup"><span data-stu-id="7bdd3-108">\<serviceAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bdd3-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7bdd3-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7bdd3-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7bdd3-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7bdd3-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7bdd3-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7bdd3-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7bdd3-112">Attributes</span></span>  
  
|<span data-ttu-id="7bdd3-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7bdd3-113">Attribute</span></span>|<span data-ttu-id="7bdd3-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7bdd3-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7bdd3-115">serviceAuthenticationManagerType</span><span class="sxs-lookup"><span data-stu-id="7bdd3-115">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="7bdd3-116">Şu anki davranışı kimlik doğrulama İlkesi türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="7bdd3-116">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7bdd3-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7bdd3-117">Child Elements</span></span>  
 <span data-ttu-id="7bdd3-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="7bdd3-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7bdd3-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7bdd3-119">Parent Elements</span></span>  
  
|<span data-ttu-id="7bdd3-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="7bdd3-120">Element</span></span>|<span data-ttu-id="7bdd3-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7bdd3-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7bdd3-122">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="7bdd3-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="7bdd3-123">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="7bdd3-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7bdd3-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7bdd3-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>

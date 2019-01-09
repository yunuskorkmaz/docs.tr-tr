---
title: '&lt;serviceAuthenticationManager&gt;'
ms.date: 03/30/2017
ms.assetid: 5d69e64f-f325-4d55-8e2d-0fb30f222dda
ms.openlocfilehash: 3456ffa952372b014d579b5c420f7c44222fdad5
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145360"
---
# <a name="ltserviceauthenticationmanagergt"></a><span data-ttu-id="5e353-102">&lt;serviceAuthenticationManager&gt;</span><span class="sxs-lookup"><span data-stu-id="5e353-102">&lt;serviceAuthenticationManager&gt;</span></span>
<span data-ttu-id="5e353-103">Hizmet düzeyinde bir iletim, ileti veya gönderen geçerliliğini kurar ve bir iş akışı yapılandırma öğesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="5e353-103">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator.</span></span>  
  
<span data-ttu-id="5e353-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5e353-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5e353-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="5e353-105">\<behaviors></span></span>  
<span data-ttu-id="5e353-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="5e353-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="5e353-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="5e353-107">\<behavior></span></span>  
<span data-ttu-id="5e353-108">\<serviceAuthenticationManager ></span><span class="sxs-lookup"><span data-stu-id="5e353-108">\<serviceAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e353-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5e353-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5e353-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5e353-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5e353-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5e353-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5e353-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5e353-112">Attributes</span></span>  
  
|<span data-ttu-id="5e353-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5e353-113">Attribute</span></span>|<span data-ttu-id="5e353-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5e353-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5e353-115">serviceAuthenticationManagerType</span><span class="sxs-lookup"><span data-stu-id="5e353-115">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="5e353-116">Şu anki davranışı için kimlik doğrulama İlkesi türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="5e353-116">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5e353-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5e353-117">Child Elements</span></span>  
 <span data-ttu-id="5e353-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="5e353-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5e353-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5e353-119">Parent Elements</span></span>  
  
|<span data-ttu-id="5e353-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="5e353-120">Element</span></span>|<span data-ttu-id="5e353-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5e353-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5e353-122">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="5e353-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="5e353-123">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="5e353-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5e353-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5e353-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>

---
title: '&lt;serviceAuthenticationManager&gt;'
ms.date: 03/30/2017
ms.assetid: 5d69e64f-f325-4d55-8e2d-0fb30f222dda
ms.openlocfilehash: fd04b10c0ac0bef4087daa1012a1b8bd3a5880e6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54493644"
---
# <a name="ltserviceauthenticationmanagergt"></a><span data-ttu-id="8f251-102">&lt;serviceAuthenticationManager&gt;</span><span class="sxs-lookup"><span data-stu-id="8f251-102">&lt;serviceAuthenticationManager&gt;</span></span>
<span data-ttu-id="8f251-103">Hizmet düzeyinde bir iletim, ileti veya gönderen geçerliliğini kurar ve bir iş akışı yapılandırma öğesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="8f251-103">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator.</span></span>  
  
<span data-ttu-id="8f251-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="8f251-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="8f251-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="8f251-105">\<behaviors></span></span>  
<span data-ttu-id="8f251-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="8f251-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="8f251-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="8f251-107">\<behavior></span></span>  
<span data-ttu-id="8f251-108">\<serviceAuthenticationManager ></span><span class="sxs-lookup"><span data-stu-id="8f251-108">\<serviceAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f251-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8f251-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8f251-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8f251-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8f251-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8f251-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8f251-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8f251-112">Attributes</span></span>  
  
|<span data-ttu-id="8f251-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8f251-113">Attribute</span></span>|<span data-ttu-id="8f251-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8f251-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8f251-115">serviceAuthenticationManagerType</span><span class="sxs-lookup"><span data-stu-id="8f251-115">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="8f251-116">Şu anki davranışı için kimlik doğrulama İlkesi türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="8f251-116">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8f251-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8f251-117">Child Elements</span></span>  
 <span data-ttu-id="8f251-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="8f251-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8f251-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8f251-119">Parent Elements</span></span>  
  
|<span data-ttu-id="8f251-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="8f251-120">Element</span></span>|<span data-ttu-id="8f251-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8f251-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8f251-122">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="8f251-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="8f251-123">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="8f251-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8f251-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8f251-124">See also</span></span>
- <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>

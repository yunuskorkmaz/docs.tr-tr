---
title: '&lt;serviceAuthenticationManager&gt;'
ms.date: 03/30/2017
ms.assetid: 5d69e64f-f325-4d55-8e2d-0fb30f222dda
ms.openlocfilehash: 34c50e0e8c259190d3f66aa7ad1369befc629d44
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53154091"
---
# <a name="ltserviceauthenticationmanagergt"></a><span data-ttu-id="1ce08-102">&lt;serviceAuthenticationManager&gt;</span><span class="sxs-lookup"><span data-stu-id="1ce08-102">&lt;serviceAuthenticationManager&gt;</span></span>
<span data-ttu-id="1ce08-103">Hizmet düzeyinde bir iletim, ileti veya gönderen geçerliliğini kurar ve bir iş akışı yapılandırma öğesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="1ce08-103">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator.</span></span>  
  
<span data-ttu-id="1ce08-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1ce08-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="1ce08-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="1ce08-105">\<behaviors></span></span>  
<span data-ttu-id="1ce08-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="1ce08-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="1ce08-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="1ce08-107">\<behavior></span></span>  
<span data-ttu-id="1ce08-108">\<serviceAuthenticationManager ></span><span class="sxs-lookup"><span data-stu-id="1ce08-108">\<serviceAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ce08-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1ce08-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1ce08-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1ce08-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1ce08-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1ce08-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1ce08-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1ce08-112">Attributes</span></span>  
  
|<span data-ttu-id="1ce08-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1ce08-113">Attribute</span></span>|<span data-ttu-id="1ce08-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1ce08-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1ce08-115">serviceAuthenticationManagerType</span><span class="sxs-lookup"><span data-stu-id="1ce08-115">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="1ce08-116">Şu anki davranışı için kimlik doğrulama İlkesi türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="1ce08-116">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1ce08-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1ce08-117">Child Elements</span></span>  
 <span data-ttu-id="1ce08-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="1ce08-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1ce08-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1ce08-119">Parent Elements</span></span>  
  
|<span data-ttu-id="1ce08-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="1ce08-120">Element</span></span>|<span data-ttu-id="1ce08-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1ce08-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1ce08-122">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="1ce08-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="1ce08-123">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="1ce08-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1ce08-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1ce08-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>

---
title: <serviceAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 5d69e64f-f325-4d55-8e2d-0fb30f222dda
ms.openlocfilehash: 65488c34931f6d7c424ece58a4855e746ea455bc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936422"
---
# <a name="serviceauthenticationmanager"></a><span data-ttu-id="8d4ae-101">\<serviceAuthenticationManager ></span><span class="sxs-lookup"><span data-stu-id="8d4ae-101">\<serviceAuthenticationManager></span></span>
<span data-ttu-id="8d4ae-102">, Hizmet düzeyinde bir iletim, ileti veya gönderen için geçerliliği belirleyen bir iş akışı yapılandırma öğesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="8d4ae-102">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator.</span></span>  
  
<span data-ttu-id="8d4ae-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="8d4ae-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="8d4ae-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="8d4ae-104">\<behaviors></span></span>  
<span data-ttu-id="8d4ae-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="8d4ae-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="8d4ae-106">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="8d4ae-106">\<behavior></span></span>  
<span data-ttu-id="8d4ae-107">\<serviceAuthenticationManager ></span><span class="sxs-lookup"><span data-stu-id="8d4ae-107">\<serviceAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d4ae-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8d4ae-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8d4ae-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8d4ae-109">Attributes and Elements</span></span>  
 <span data-ttu-id="8d4ae-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8d4ae-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8d4ae-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8d4ae-111">Attributes</span></span>  
  
|<span data-ttu-id="8d4ae-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8d4ae-112">Attribute</span></span>|<span data-ttu-id="8d4ae-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8d4ae-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8d4ae-114">serviceAuthenticationManagerType</span><span class="sxs-lookup"><span data-stu-id="8d4ae-114">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="8d4ae-115">Geçerli davranış için kimlik doğrulama ilkesinin türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="8d4ae-115">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8d4ae-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8d4ae-116">Child Elements</span></span>  
 <span data-ttu-id="8d4ae-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="8d4ae-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8d4ae-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8d4ae-118">Parent Elements</span></span>  
  
|<span data-ttu-id="8d4ae-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="8d4ae-119">Element</span></span>|<span data-ttu-id="8d4ae-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8d4ae-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8d4ae-121">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="8d4ae-121">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="8d4ae-122">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="8d4ae-122">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8d4ae-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8d4ae-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>

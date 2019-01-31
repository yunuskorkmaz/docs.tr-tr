---
title: <serviceAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 5d69e64f-f325-4d55-8e2d-0fb30f222dda
ms.openlocfilehash: 7708dd8a572dd24c2852410b1781fce2807efab9
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55263491"
---
# <a name="serviceauthenticationmanager"></a><span data-ttu-id="dca6d-101">\<serviceAuthenticationManager ></span><span class="sxs-lookup"><span data-stu-id="dca6d-101">\<serviceAuthenticationManager></span></span>
<span data-ttu-id="dca6d-102">Hizmet düzeyinde bir iletim, ileti veya gönderen geçerliliğini kurar ve bir iş akışı yapılandırma öğesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="dca6d-102">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator.</span></span>  
  
<span data-ttu-id="dca6d-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="dca6d-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="dca6d-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="dca6d-104">\<behaviors></span></span>  
<span data-ttu-id="dca6d-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="dca6d-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="dca6d-106">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="dca6d-106">\<behavior></span></span>  
<span data-ttu-id="dca6d-107">\<serviceAuthenticationManager ></span><span class="sxs-lookup"><span data-stu-id="dca6d-107">\<serviceAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dca6d-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dca6d-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dca6d-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="dca6d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="dca6d-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="dca6d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dca6d-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="dca6d-111">Attributes</span></span>  
  
|<span data-ttu-id="dca6d-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="dca6d-112">Attribute</span></span>|<span data-ttu-id="dca6d-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dca6d-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dca6d-114">serviceAuthenticationManagerType</span><span class="sxs-lookup"><span data-stu-id="dca6d-114">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="dca6d-115">Şu anki davranışı için kimlik doğrulama İlkesi türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="dca6d-115">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dca6d-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="dca6d-116">Child Elements</span></span>  
 <span data-ttu-id="dca6d-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="dca6d-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dca6d-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="dca6d-118">Parent Elements</span></span>  
  
|<span data-ttu-id="dca6d-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="dca6d-119">Element</span></span>|<span data-ttu-id="dca6d-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dca6d-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dca6d-121">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="dca6d-121">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="dca6d-122">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="dca6d-122">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dca6d-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dca6d-123">See also</span></span>
- <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>

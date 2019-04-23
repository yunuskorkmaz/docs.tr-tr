---
title: <serviceAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 5d69e64f-f325-4d55-8e2d-0fb30f222dda
ms.openlocfilehash: 0940248364488bb38a329c5e461d72463c574e74
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59192052"
---
# <a name="serviceauthenticationmanager"></a><span data-ttu-id="73445-101">\<serviceAuthenticationManager ></span><span class="sxs-lookup"><span data-stu-id="73445-101">\<serviceAuthenticationManager></span></span>
<span data-ttu-id="73445-102">Hizmet düzeyinde bir iletim, ileti veya gönderen geçerliliğini kurar ve bir iş akışı yapılandırma öğesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="73445-102">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator.</span></span>  
  
<span data-ttu-id="73445-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="73445-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="73445-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="73445-104">\<behaviors></span></span>  
<span data-ttu-id="73445-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="73445-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="73445-106">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="73445-106">\<behavior></span></span>  
<span data-ttu-id="73445-107">\<serviceAuthenticationManager ></span><span class="sxs-lookup"><span data-stu-id="73445-107">\<serviceAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73445-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="73445-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="73445-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="73445-109">Attributes and Elements</span></span>  
 <span data-ttu-id="73445-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="73445-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="73445-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="73445-111">Attributes</span></span>  
  
|<span data-ttu-id="73445-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="73445-112">Attribute</span></span>|<span data-ttu-id="73445-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="73445-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="73445-114">serviceAuthenticationManagerType</span><span class="sxs-lookup"><span data-stu-id="73445-114">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="73445-115">Şu anki davranışı için kimlik doğrulama İlkesi türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="73445-115">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="73445-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="73445-116">Child Elements</span></span>  
 <span data-ttu-id="73445-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="73445-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="73445-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="73445-118">Parent Elements</span></span>  
  
|<span data-ttu-id="73445-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="73445-119">Element</span></span>|<span data-ttu-id="73445-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="73445-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="73445-121">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="73445-121">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="73445-122">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="73445-122">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="73445-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="73445-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>

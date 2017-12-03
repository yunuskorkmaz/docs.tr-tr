---
title: DeliveryRequirementsAttribute
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40c5435c-a325-4cf8-9dd0-d6e24b4a56a3
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 172f7df4f028c1ddc0f5565e95291e857ee6fa1d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="deliveryrequirementsattribute"></a><span data-ttu-id="ff3b6-102">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="ff3b6-102">DeliveryRequirementsAttribute</span></span>
<span data-ttu-id="ff3b6-103">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="ff3b6-103">DeliveryRequirementsAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff3b6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ff3b6-104">Syntax</span></span>  
  
```  
class DeliveryRequirementsAttribute : Behavior  
{  
  string QueuedDeliveryRequirements;  
  boolean RequireOrderedDelivery;  
  string TargetContract;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="ff3b6-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ff3b6-105">Methods</span></span>  
 <span data-ttu-id="ff3b6-106">DeliveryRequirementsAttribute sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="ff3b6-106">The DeliveryRequirementsAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ff3b6-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="ff3b6-107">Properties</span></span>  
 <span data-ttu-id="ff3b6-108">DeliveryRequirementsAttribute sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="ff3b6-108">The DeliveryRequirementsAttribute class has the following properties:</span></span>  
  
### <a name="queueddeliveryrequirements"></a><span data-ttu-id="ff3b6-109">QueuedDeliveryRequirements</span><span class="sxs-lookup"><span data-stu-id="ff3b6-109">QueuedDeliveryRequirements</span></span>  
 <span data-ttu-id="ff3b6-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="ff3b6-110">Data type: string</span></span>  
  
 <span data-ttu-id="ff3b6-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="ff3b6-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ff3b6-112">Bir hizmet için bağlama sözleşmeleri destekleyip desteklemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ff3b6-112">Specifies whether the binding for a service supports contracts.</span></span>  
  
### <a name="requireordereddelivery"></a><span data-ttu-id="ff3b6-113">RequireOrderedDelivery</span><span class="sxs-lookup"><span data-stu-id="ff3b6-113">RequireOrderedDelivery</span></span>  
 <span data-ttu-id="ff3b6-114">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="ff3b6-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="ff3b6-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="ff3b6-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ff3b6-116">Bağlama sıralanan iletileri destekleyip desteklemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ff3b6-116">Specifies whether the binding supports ordered messages.</span></span>  
  
### <a name="targetcontract"></a><span data-ttu-id="ff3b6-117">TargetContract</span><span class="sxs-lookup"><span data-stu-id="ff3b6-117">TargetContract</span></span>  
 <span data-ttu-id="ff3b6-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="ff3b6-118">Data type: string</span></span>  
  
 <span data-ttu-id="ff3b6-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="ff3b6-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ff3b6-120">Geçerli olduğu sözleşme.</span><span class="sxs-lookup"><span data-stu-id="ff3b6-120">The contract to which it applies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff3b6-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ff3b6-121">Requirements</span></span>  
  
|<span data-ttu-id="ff3b6-122">MOF</span><span class="sxs-lookup"><span data-stu-id="ff3b6-122">MOF</span></span>|<span data-ttu-id="ff3b6-123">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="ff3b6-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ff3b6-124">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="ff3b6-124">Namespace</span></span>|<span data-ttu-id="ff3b6-125">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="ff3b6-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ff3b6-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ff3b6-126">See Also</span></span>  
 <xref:System.ServiceModel.DeliveryRequirementsAttribute>

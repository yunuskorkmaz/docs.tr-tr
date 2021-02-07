---
description: 'Daha fazla bilgi edinin: DeliveryRequirementsAttribute'
title: DeliveryRequirementsAttribute
ms.date: 03/30/2017
ms.assetid: 40c5435c-a325-4cf8-9dd0-d6e24b4a56a3
ms.openlocfilehash: ee27ada1c1fb447de3d7a108a4a285ca106e4e8e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757507"
---
# <a name="deliveryrequirementsattribute"></a><span data-ttu-id="47e95-103">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="47e95-103">DeliveryRequirementsAttribute</span></span>

<span data-ttu-id="47e95-104">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="47e95-104">DeliveryRequirementsAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47e95-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="47e95-105">Syntax</span></span>  
  
```csharp
class DeliveryRequirementsAttribute : Behavior  
{  
  string QueuedDeliveryRequirements;  
  boolean RequireOrderedDelivery;  
  string TargetContract;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="47e95-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="47e95-106">Methods</span></span>  

 <span data-ttu-id="47e95-107">DeliveryRequirementsAttribute sınıfı herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="47e95-107">The DeliveryRequirementsAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="47e95-108">Özellikler</span><span class="sxs-lookup"><span data-stu-id="47e95-108">Properties</span></span>  

 <span data-ttu-id="47e95-109">DeliveryRequirementsAttribute sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="47e95-109">The DeliveryRequirementsAttribute class has the following properties:</span></span>  
  
### <a name="queueddeliveryrequirements"></a><span data-ttu-id="47e95-110">QueuedDeliveryRequirements</span><span class="sxs-lookup"><span data-stu-id="47e95-110">QueuedDeliveryRequirements</span></span>  

 <span data-ttu-id="47e95-111">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="47e95-111">Data type: string</span></span>  
  
 <span data-ttu-id="47e95-112">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="47e95-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="47e95-113">Bir hizmet bağlamasının sözleşmeleri destekleyip desteklemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="47e95-113">Specifies whether the binding for a service supports contracts.</span></span>  
  
### <a name="requireordereddelivery"></a><span data-ttu-id="47e95-114">RequireOrderedDelivery</span><span class="sxs-lookup"><span data-stu-id="47e95-114">RequireOrderedDelivery</span></span>  

 <span data-ttu-id="47e95-115">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="47e95-115">Data type: boolean</span></span>  
  
 <span data-ttu-id="47e95-116">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="47e95-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="47e95-117">Bağlamanın sıralanmış iletileri destekleyip desteklemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="47e95-117">Specifies whether the binding supports ordered messages.</span></span>  
  
### <a name="targetcontract"></a><span data-ttu-id="47e95-118">TargetContract</span><span class="sxs-lookup"><span data-stu-id="47e95-118">TargetContract</span></span>  

 <span data-ttu-id="47e95-119">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="47e95-119">Data type: string</span></span>  
  
 <span data-ttu-id="47e95-120">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="47e95-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="47e95-121">Geçerli olduğu sözleşme.</span><span class="sxs-lookup"><span data-stu-id="47e95-121">The contract to which it applies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47e95-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="47e95-122">Requirements</span></span>  
  
|<span data-ttu-id="47e95-123">MOF</span><span class="sxs-lookup"><span data-stu-id="47e95-123">MOF</span></span>|<span data-ttu-id="47e95-124">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="47e95-124">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="47e95-125">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="47e95-125">Namespace</span></span>|<span data-ttu-id="47e95-126">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="47e95-126">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="47e95-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="47e95-127">See also</span></span>

- <xref:System.ServiceModel.DeliveryRequirementsAttribute>

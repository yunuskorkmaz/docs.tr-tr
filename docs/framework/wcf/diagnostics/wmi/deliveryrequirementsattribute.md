---
title: DeliveryRequirementsAttribute
ms.date: 03/30/2017
ms.assetid: 40c5435c-a325-4cf8-9dd0-d6e24b4a56a3
ms.openlocfilehash: d294ba4f14472012b9e311ee53742633b5173f54
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485837"
---
# <a name="deliveryrequirementsattribute"></a><span data-ttu-id="10a46-102">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="10a46-102">DeliveryRequirementsAttribute</span></span>
<span data-ttu-id="10a46-103">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="10a46-103">DeliveryRequirementsAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10a46-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="10a46-104">Syntax</span></span>  
  
```  
class DeliveryRequirementsAttribute : Behavior  
{  
  string QueuedDeliveryRequirements;  
  boolean RequireOrderedDelivery;  
  string TargetContract;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="10a46-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="10a46-105">Methods</span></span>  
 <span data-ttu-id="10a46-106">DeliveryRequirementsAttribute sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="10a46-106">The DeliveryRequirementsAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="10a46-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="10a46-107">Properties</span></span>  
 <span data-ttu-id="10a46-108">DeliveryRequirementsAttribute sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="10a46-108">The DeliveryRequirementsAttribute class has the following properties:</span></span>  
  
### <a name="queueddeliveryrequirements"></a><span data-ttu-id="10a46-109">QueuedDeliveryRequirements</span><span class="sxs-lookup"><span data-stu-id="10a46-109">QueuedDeliveryRequirements</span></span>  
 <span data-ttu-id="10a46-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="10a46-110">Data type: string</span></span>  
  
 <span data-ttu-id="10a46-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="10a46-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="10a46-112">Bir hizmet için bağlama sözleşmeleri destekleyip desteklemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="10a46-112">Specifies whether the binding for a service supports contracts.</span></span>  
  
### <a name="requireordereddelivery"></a><span data-ttu-id="10a46-113">RequireOrderedDelivery</span><span class="sxs-lookup"><span data-stu-id="10a46-113">RequireOrderedDelivery</span></span>  
 <span data-ttu-id="10a46-114">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="10a46-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="10a46-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="10a46-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="10a46-116">Bağlama sıralanan iletileri destekleyip desteklemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="10a46-116">Specifies whether the binding supports ordered messages.</span></span>  
  
### <a name="targetcontract"></a><span data-ttu-id="10a46-117">TargetContract</span><span class="sxs-lookup"><span data-stu-id="10a46-117">TargetContract</span></span>  
 <span data-ttu-id="10a46-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="10a46-118">Data type: string</span></span>  
  
 <span data-ttu-id="10a46-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="10a46-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="10a46-120">Geçerli olduğu sözleşme.</span><span class="sxs-lookup"><span data-stu-id="10a46-120">The contract to which it applies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10a46-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="10a46-121">Requirements</span></span>  
  
|<span data-ttu-id="10a46-122">MOF</span><span class="sxs-lookup"><span data-stu-id="10a46-122">MOF</span></span>|<span data-ttu-id="10a46-123">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="10a46-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="10a46-124">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="10a46-124">Namespace</span></span>|<span data-ttu-id="10a46-125">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="10a46-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="10a46-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="10a46-126">See Also</span></span>  
 <xref:System.ServiceModel.DeliveryRequirementsAttribute>

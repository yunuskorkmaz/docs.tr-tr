---
title: DeliveryRequirementsAttribute
ms.date: 03/30/2017
ms.assetid: 40c5435c-a325-4cf8-9dd0-d6e24b4a56a3
ms.openlocfilehash: a70a4ba40b569acc7893b21d796194224dc4ee78
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96274055"
---
# <a name="deliveryrequirementsattribute"></a><span data-ttu-id="4f5e9-102">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="4f5e9-102">DeliveryRequirementsAttribute</span></span>

<span data-ttu-id="4f5e9-103">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="4f5e9-103">DeliveryRequirementsAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f5e9-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="4f5e9-104">Syntax</span></span>  
  
```csharp
class DeliveryRequirementsAttribute : Behavior  
{  
  string QueuedDeliveryRequirements;  
  boolean RequireOrderedDelivery;  
  string TargetContract;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="4f5e9-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4f5e9-105">Methods</span></span>  

 <span data-ttu-id="4f5e9-106">DeliveryRequirementsAttribute sınıfı herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="4f5e9-106">The DeliveryRequirementsAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="4f5e9-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="4f5e9-107">Properties</span></span>  

 <span data-ttu-id="4f5e9-108">DeliveryRequirementsAttribute sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="4f5e9-108">The DeliveryRequirementsAttribute class has the following properties:</span></span>  
  
### <a name="queueddeliveryrequirements"></a><span data-ttu-id="4f5e9-109">QueuedDeliveryRequirements</span><span class="sxs-lookup"><span data-stu-id="4f5e9-109">QueuedDeliveryRequirements</span></span>  

 <span data-ttu-id="4f5e9-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="4f5e9-110">Data type: string</span></span>  
  
 <span data-ttu-id="4f5e9-111">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="4f5e9-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4f5e9-112">Bir hizmet bağlamasının sözleşmeleri destekleyip desteklemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4f5e9-112">Specifies whether the binding for a service supports contracts.</span></span>  
  
### <a name="requireordereddelivery"></a><span data-ttu-id="4f5e9-113">RequireOrderedDelivery</span><span class="sxs-lookup"><span data-stu-id="4f5e9-113">RequireOrderedDelivery</span></span>  

 <span data-ttu-id="4f5e9-114">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="4f5e9-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="4f5e9-115">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="4f5e9-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4f5e9-116">Bağlamanın sıralanmış iletileri destekleyip desteklemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4f5e9-116">Specifies whether the binding supports ordered messages.</span></span>  
  
### <a name="targetcontract"></a><span data-ttu-id="4f5e9-117">TargetContract</span><span class="sxs-lookup"><span data-stu-id="4f5e9-117">TargetContract</span></span>  

 <span data-ttu-id="4f5e9-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="4f5e9-118">Data type: string</span></span>  
  
 <span data-ttu-id="4f5e9-119">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="4f5e9-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4f5e9-120">Geçerli olduğu sözleşme.</span><span class="sxs-lookup"><span data-stu-id="4f5e9-120">The contract to which it applies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f5e9-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4f5e9-121">Requirements</span></span>  
  
|<span data-ttu-id="4f5e9-122">MOF</span><span class="sxs-lookup"><span data-stu-id="4f5e9-122">MOF</span></span>|<span data-ttu-id="4f5e9-123">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="4f5e9-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="4f5e9-124">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="4f5e9-124">Namespace</span></span>|<span data-ttu-id="4f5e9-125">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="4f5e9-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4f5e9-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4f5e9-126">See also</span></span>

- <xref:System.ServiceModel.DeliveryRequirementsAttribute>

---
title: DeliveryRequirementsAttribute
ms.date: 03/30/2017
ms.assetid: 40c5435c-a325-4cf8-9dd0-d6e24b4a56a3
ms.openlocfilehash: c81e4b27969d879a70806082f48879cbf1b32ccc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59101783"
---
# <a name="deliveryrequirementsattribute"></a><span data-ttu-id="79332-102">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="79332-102">DeliveryRequirementsAttribute</span></span>
<span data-ttu-id="79332-103">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="79332-103">DeliveryRequirementsAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79332-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="79332-104">Syntax</span></span>  
  
```csharp
class DeliveryRequirementsAttribute : Behavior  
{  
  string QueuedDeliveryRequirements;  
  boolean RequireOrderedDelivery;  
  string TargetContract;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="79332-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="79332-105">Methods</span></span>  
 <span data-ttu-id="79332-106">DeliveryRequirementsAttribute sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="79332-106">The DeliveryRequirementsAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="79332-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="79332-107">Properties</span></span>  
 <span data-ttu-id="79332-108">DeliveryRequirementsAttribute sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="79332-108">The DeliveryRequirementsAttribute class has the following properties:</span></span>  
  
### <a name="queueddeliveryrequirements"></a><span data-ttu-id="79332-109">NotAllowed</span><span class="sxs-lookup"><span data-stu-id="79332-109">QueuedDeliveryRequirements</span></span>  
 <span data-ttu-id="79332-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="79332-110">Data type: string</span></span>  
  
 <span data-ttu-id="79332-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="79332-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="79332-112">Bir hizmet için bağlama sözleşmeleri destekleyip desteklemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="79332-112">Specifies whether the binding for a service supports contracts.</span></span>  
  
### <a name="requireordereddelivery"></a><span data-ttu-id="79332-113">RequireOrderedDelivery</span><span class="sxs-lookup"><span data-stu-id="79332-113">RequireOrderedDelivery</span></span>  
 <span data-ttu-id="79332-114">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="79332-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="79332-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="79332-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="79332-116">Bağlama sıralı iletileri destekleyip desteklemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="79332-116">Specifies whether the binding supports ordered messages.</span></span>  
  
### <a name="targetcontract"></a><span data-ttu-id="79332-117">TargetContract</span><span class="sxs-lookup"><span data-stu-id="79332-117">TargetContract</span></span>  
 <span data-ttu-id="79332-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="79332-118">Data type: string</span></span>  
  
 <span data-ttu-id="79332-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="79332-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="79332-120">Geçerli sözleşme.</span><span class="sxs-lookup"><span data-stu-id="79332-120">The contract to which it applies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79332-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="79332-121">Requirements</span></span>  
  
|<span data-ttu-id="79332-122">MOF</span><span class="sxs-lookup"><span data-stu-id="79332-122">MOF</span></span>|<span data-ttu-id="79332-123">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="79332-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="79332-124">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="79332-124">Namespace</span></span>|<span data-ttu-id="79332-125">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="79332-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="79332-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="79332-126">See also</span></span>

- <xref:System.ServiceModel.DeliveryRequirementsAttribute>

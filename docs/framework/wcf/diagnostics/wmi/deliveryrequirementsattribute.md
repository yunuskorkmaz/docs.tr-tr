---
title: DeliveryRequirementsAttribute
ms.date: 03/30/2017
ms.assetid: 40c5435c-a325-4cf8-9dd0-d6e24b4a56a3
ms.openlocfilehash: 7bfc03299fffc8070a7d8a4b3885706ea861bdf6
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50198522"
---
# <a name="deliveryrequirementsattribute"></a><span data-ttu-id="4adfa-102">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="4adfa-102">DeliveryRequirementsAttribute</span></span>
<span data-ttu-id="4adfa-103">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="4adfa-103">DeliveryRequirementsAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4adfa-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4adfa-104">Syntax</span></span>  
  
```csharp
class DeliveryRequirementsAttribute : Behavior  
{  
  string QueuedDeliveryRequirements;  
  boolean RequireOrderedDelivery;  
  string TargetContract;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="4adfa-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4adfa-105">Methods</span></span>  
 <span data-ttu-id="4adfa-106">DeliveryRequirementsAttribute sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="4adfa-106">The DeliveryRequirementsAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="4adfa-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="4adfa-107">Properties</span></span>  
 <span data-ttu-id="4adfa-108">DeliveryRequirementsAttribute sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="4adfa-108">The DeliveryRequirementsAttribute class has the following properties:</span></span>  
  
### <a name="queueddeliveryrequirements"></a><span data-ttu-id="4adfa-109">NotAllowed</span><span class="sxs-lookup"><span data-stu-id="4adfa-109">QueuedDeliveryRequirements</span></span>  
 <span data-ttu-id="4adfa-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="4adfa-110">Data type: string</span></span>  
  
 <span data-ttu-id="4adfa-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="4adfa-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4adfa-112">Bir hizmet için bağlama sözleşmeleri destekleyip desteklemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4adfa-112">Specifies whether the binding for a service supports contracts.</span></span>  
  
### <a name="requireordereddelivery"></a><span data-ttu-id="4adfa-113">RequireOrderedDelivery</span><span class="sxs-lookup"><span data-stu-id="4adfa-113">RequireOrderedDelivery</span></span>  
 <span data-ttu-id="4adfa-114">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="4adfa-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="4adfa-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="4adfa-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4adfa-116">Bağlama sıralı iletileri destekleyip desteklemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4adfa-116">Specifies whether the binding supports ordered messages.</span></span>  
  
### <a name="targetcontract"></a><span data-ttu-id="4adfa-117">TargetContract</span><span class="sxs-lookup"><span data-stu-id="4adfa-117">TargetContract</span></span>  
 <span data-ttu-id="4adfa-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="4adfa-118">Data type: string</span></span>  
  
 <span data-ttu-id="4adfa-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="4adfa-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4adfa-120">Geçerli sözleşme.</span><span class="sxs-lookup"><span data-stu-id="4adfa-120">The contract to which it applies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4adfa-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4adfa-121">Requirements</span></span>  
  
|<span data-ttu-id="4adfa-122">MOF</span><span class="sxs-lookup"><span data-stu-id="4adfa-122">MOF</span></span>|<span data-ttu-id="4adfa-123">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="4adfa-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="4adfa-124">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="4adfa-124">Namespace</span></span>|<span data-ttu-id="4adfa-125">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4adfa-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4adfa-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4adfa-126">See Also</span></span>  
 <xref:System.ServiceModel.DeliveryRequirementsAttribute>

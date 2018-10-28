---
title: DeliveryRequirementsAttribute
ms.date: 03/30/2017
ms.assetid: 40c5435c-a325-4cf8-9dd0-d6e24b4a56a3
ms.openlocfilehash: 7bfc03299fffc8070a7d8a4b3885706ea861bdf6
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/26/2018
ms.locfileid: "50042902"
---
# <a name="deliveryrequirementsattribute"></a><span data-ttu-id="8ac17-102">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="8ac17-102">DeliveryRequirementsAttribute</span></span>
<span data-ttu-id="8ac17-103">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="8ac17-103">DeliveryRequirementsAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ac17-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8ac17-104">Syntax</span></span>  
  
```csharp
class DeliveryRequirementsAttribute : Behavior  
{  
  string QueuedDeliveryRequirements;  
  boolean RequireOrderedDelivery;  
  string TargetContract;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="8ac17-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8ac17-105">Methods</span></span>  
 <span data-ttu-id="8ac17-106">DeliveryRequirementsAttribute sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="8ac17-106">The DeliveryRequirementsAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="8ac17-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="8ac17-107">Properties</span></span>  
 <span data-ttu-id="8ac17-108">DeliveryRequirementsAttribute sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="8ac17-108">The DeliveryRequirementsAttribute class has the following properties:</span></span>  
  
### <a name="queueddeliveryrequirements"></a><span data-ttu-id="8ac17-109">NotAllowed</span><span class="sxs-lookup"><span data-stu-id="8ac17-109">QueuedDeliveryRequirements</span></span>  
 <span data-ttu-id="8ac17-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="8ac17-110">Data type: string</span></span>  
  
 <span data-ttu-id="8ac17-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="8ac17-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8ac17-112">Bir hizmet için bağlama sözleşmeleri destekleyip desteklemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8ac17-112">Specifies whether the binding for a service supports contracts.</span></span>  
  
### <a name="requireordereddelivery"></a><span data-ttu-id="8ac17-113">RequireOrderedDelivery</span><span class="sxs-lookup"><span data-stu-id="8ac17-113">RequireOrderedDelivery</span></span>  
 <span data-ttu-id="8ac17-114">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="8ac17-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="8ac17-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="8ac17-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8ac17-116">Bağlama sıralı iletileri destekleyip desteklemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8ac17-116">Specifies whether the binding supports ordered messages.</span></span>  
  
### <a name="targetcontract"></a><span data-ttu-id="8ac17-117">TargetContract</span><span class="sxs-lookup"><span data-stu-id="8ac17-117">TargetContract</span></span>  
 <span data-ttu-id="8ac17-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="8ac17-118">Data type: string</span></span>  
  
 <span data-ttu-id="8ac17-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="8ac17-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8ac17-120">Geçerli sözleşme.</span><span class="sxs-lookup"><span data-stu-id="8ac17-120">The contract to which it applies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ac17-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8ac17-121">Requirements</span></span>  
  
|<span data-ttu-id="8ac17-122">MOF</span><span class="sxs-lookup"><span data-stu-id="8ac17-122">MOF</span></span>|<span data-ttu-id="8ac17-123">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="8ac17-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="8ac17-124">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="8ac17-124">Namespace</span></span>|<span data-ttu-id="8ac17-125">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="8ac17-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8ac17-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8ac17-126">See Also</span></span>  
 <xref:System.ServiceModel.DeliveryRequirementsAttribute>

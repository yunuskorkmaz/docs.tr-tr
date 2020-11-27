---
title: ServiceTimeoutsBehavior
ms.date: 03/30/2017
ms.assetid: 4412525d-a3cc-4eae-b3e8-a50ce766d09d
ms.openlocfilehash: 867219130fc853f3ba2c1c2f807b1651f6480f13
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273977"
---
# <a name="servicetimeoutsbehavior"></a><span data-ttu-id="5c50b-102">ServiceTimeoutsBehavior</span><span class="sxs-lookup"><span data-stu-id="5c50b-102">ServiceTimeoutsBehavior</span></span>

<span data-ttu-id="5c50b-103">ServiceTimeoutsBehavior</span><span class="sxs-lookup"><span data-stu-id="5c50b-103">ServiceTimeoutsBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c50b-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="5c50b-104">Syntax</span></span>  
  
```csharp
class ServiceTimeoutsBehavior : Behavior  
{  
  datetime TransactionTimeout;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="5c50b-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="5c50b-105">Methods</span></span>  

 <span data-ttu-id="5c50b-106">ServiceTimeoutsBehavior sınıfı herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="5c50b-106">The ServiceTimeoutsBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="5c50b-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="5c50b-107">Properties</span></span>  

 <span data-ttu-id="5c50b-108">ServiceTimeoutsBehavior sınıfı aşağıdaki özelliğe sahiptir:</span><span class="sxs-lookup"><span data-stu-id="5c50b-108">The ServiceTimeoutsBehavior class has the following property:</span></span>  
  
### <a name="transactiontimeout"></a><span data-ttu-id="5c50b-109">Işlem zaman aşımı</span><span class="sxs-lookup"><span data-stu-id="5c50b-109">TransactionTimeout</span></span>  

 <span data-ttu-id="5c50b-110">Veri türü: DateTime</span><span class="sxs-lookup"><span data-stu-id="5c50b-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="5c50b-111">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="5c50b-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5c50b-112">Bir işlemin tamamlaması gereken dönem.</span><span class="sxs-lookup"><span data-stu-id="5c50b-112">The period within which a transaction must complete.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c50b-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5c50b-113">Requirements</span></span>  
  
|<span data-ttu-id="5c50b-114">MOF</span><span class="sxs-lookup"><span data-stu-id="5c50b-114">MOF</span></span>|<span data-ttu-id="5c50b-115">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5c50b-115">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="5c50b-116">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="5c50b-116">Namespace</span></span>|<span data-ttu-id="5c50b-117">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="5c50b-117">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5c50b-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5c50b-118">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>

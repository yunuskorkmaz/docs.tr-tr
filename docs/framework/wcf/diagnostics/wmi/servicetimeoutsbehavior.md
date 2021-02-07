---
description: 'Şu konuda daha fazla bilgi edinin: ServiceTimeoutsBehavior'
title: ServiceTimeoutsBehavior
ms.date: 03/30/2017
ms.assetid: 4412525d-a3cc-4eae-b3e8-a50ce766d09d
ms.openlocfilehash: 147d249af0e87bc41da93a4a31355da7053caaf6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715424"
---
# <a name="servicetimeoutsbehavior"></a><span data-ttu-id="7217b-103">ServiceTimeoutsBehavior</span><span class="sxs-lookup"><span data-stu-id="7217b-103">ServiceTimeoutsBehavior</span></span>

<span data-ttu-id="7217b-104">ServiceTimeoutsBehavior</span><span class="sxs-lookup"><span data-stu-id="7217b-104">ServiceTimeoutsBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7217b-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="7217b-105">Syntax</span></span>  
  
```csharp
class ServiceTimeoutsBehavior : Behavior  
{  
  datetime TransactionTimeout;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="7217b-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="7217b-106">Methods</span></span>  

 <span data-ttu-id="7217b-107">ServiceTimeoutsBehavior sınıfı herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="7217b-107">The ServiceTimeoutsBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="7217b-108">Özellikler</span><span class="sxs-lookup"><span data-stu-id="7217b-108">Properties</span></span>  

 <span data-ttu-id="7217b-109">ServiceTimeoutsBehavior sınıfı aşağıdaki özelliğe sahiptir:</span><span class="sxs-lookup"><span data-stu-id="7217b-109">The ServiceTimeoutsBehavior class has the following property:</span></span>  
  
### <a name="transactiontimeout"></a><span data-ttu-id="7217b-110">Işlem zaman aşımı</span><span class="sxs-lookup"><span data-stu-id="7217b-110">TransactionTimeout</span></span>  

 <span data-ttu-id="7217b-111">Veri türü: DateTime</span><span class="sxs-lookup"><span data-stu-id="7217b-111">Data type: datetime</span></span>  
  
 <span data-ttu-id="7217b-112">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="7217b-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7217b-113">Bir işlemin tamamlaması gereken dönem.</span><span class="sxs-lookup"><span data-stu-id="7217b-113">The period within which a transaction must complete.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7217b-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7217b-114">Requirements</span></span>  
  
|<span data-ttu-id="7217b-115">MOF</span><span class="sxs-lookup"><span data-stu-id="7217b-115">MOF</span></span>|<span data-ttu-id="7217b-116">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7217b-116">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="7217b-117">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="7217b-117">Namespace</span></span>|<span data-ttu-id="7217b-118">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="7217b-118">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7217b-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7217b-119">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>

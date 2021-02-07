---
description: 'Hakkında daha fazla bilgi edinin: Servicekısıtlar Lingbehavior'
title: ServiceThrottlingBehavior
ms.date: 03/30/2017
ms.assetid: 37b9e517-1f1f-4ec4-9fcb-2b8016794f5b
ms.openlocfilehash: c4cf354c96340b910807bf7904e63a08dc01764b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715450"
---
# <a name="servicethrottlingbehavior"></a><span data-ttu-id="fd2f3-103">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="fd2f3-103">ServiceThrottlingBehavior</span></span>

<span data-ttu-id="fd2f3-104">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="fd2f3-104">ServiceThrottlingBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd2f3-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="fd2f3-105">Syntax</span></span>  
  
```csharp  
class ServiceThrottlingBehavior : Behavior  
{  
  sint32 MaxConcurrentCalls;  
  sint32 MaxConcurrentInstances;  
  sint32 MaxConcurrentSessions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="fd2f3-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="fd2f3-106">Methods</span></span>  

 <span data-ttu-id="fd2f3-107">Servicekısıtlar Lingbehavior sınıfı herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="fd2f3-107">The ServiceThrottlingBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="fd2f3-108">Özellikler</span><span class="sxs-lookup"><span data-stu-id="fd2f3-108">Properties</span></span>  

 <span data-ttu-id="fd2f3-109">Servicekısıtlar Lingbehavior sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="fd2f3-109">The ServiceThrottlingBehavior class has the following properties:</span></span>  
  
### <a name="maxconcurrentcalls"></a><span data-ttu-id="fd2f3-110">Maxconcurrentçağrıları</span><span class="sxs-lookup"><span data-stu-id="fd2f3-110">MaxConcurrentCalls</span></span>  

 <span data-ttu-id="fd2f3-111">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="fd2f3-111">Data type: sint32</span></span>  
  
 <span data-ttu-id="fd2f3-112">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="fd2f3-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fd2f3-113">ServiceHost içindeki tüm Dispatcher nesnelerinde etkin olarak işlenen en fazla ileti sayısı.</span><span class="sxs-lookup"><span data-stu-id="fd2f3-113">The maximum number of messages actively processing across all dispatcher objects in a ServiceHost.</span></span>  
  
### <a name="maxconcurrentinstances"></a><span data-ttu-id="fd2f3-114">MaxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="fd2f3-114">MaxConcurrentInstances</span></span>  

 <span data-ttu-id="fd2f3-115">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="fd2f3-115">Data type: sint32</span></span>  
  
 <span data-ttu-id="fd2f3-116">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="fd2f3-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fd2f3-117">Tek seferde yürütebilmesi için en fazla hizmet nesnesi sayısı.</span><span class="sxs-lookup"><span data-stu-id="fd2f3-117">The maximum number of service objects that can execute at one time.</span></span>  
  
### <a name="maxconcurrentsessions"></a><span data-ttu-id="fd2f3-118">MaxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="fd2f3-118">MaxConcurrentSessions</span></span>  

 <span data-ttu-id="fd2f3-119">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="fd2f3-119">Data type: sint32</span></span>  
  
 <span data-ttu-id="fd2f3-120">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="fd2f3-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fd2f3-121">Bir konağın bir anda kabul edebileceği en fazla oturum sayısı.</span><span class="sxs-lookup"><span data-stu-id="fd2f3-121">The maximum number of sessions a host can accept at one time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd2f3-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fd2f3-122">Requirements</span></span>  
  
|<span data-ttu-id="fd2f3-123">MOF</span><span class="sxs-lookup"><span data-stu-id="fd2f3-123">MOF</span></span>|<span data-ttu-id="fd2f3-124">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="fd2f3-124">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="fd2f3-125">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="fd2f3-125">Namespace</span></span>|<span data-ttu-id="fd2f3-126">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="fd2f3-126">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fd2f3-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd2f3-127">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>

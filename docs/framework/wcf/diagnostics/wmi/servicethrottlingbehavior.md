---
title: ServiceThrottlingBehavior
ms.date: 03/30/2017
ms.assetid: 37b9e517-1f1f-4ec4-9fcb-2b8016794f5b
ms.openlocfilehash: 9a7fbf93dbdbf1a6debcf865b4883b5784e2ff4a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33487613"
---
# <a name="servicethrottlingbehavior"></a><span data-ttu-id="edfc7-102">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="edfc7-102">ServiceThrottlingBehavior</span></span>
<span data-ttu-id="edfc7-103">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="edfc7-103">ServiceThrottlingBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edfc7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="edfc7-104">Syntax</span></span>  
  
```  
class ServiceThrottlingBehavior : Behavior  
{  
  sint32 MaxConcurrentCalls;  
  sint32 MaxConcurrentInstances;  
  sint32 MaxConcurrentSessions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="edfc7-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="edfc7-105">Methods</span></span>  
 <span data-ttu-id="edfc7-106">ServiceThrottlingBehavior'dan sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="edfc7-106">The ServiceThrottlingBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="edfc7-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="edfc7-107">Properties</span></span>  
 <span data-ttu-id="edfc7-108">ServiceThrottlingBehavior'dan sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="edfc7-108">The ServiceThrottlingBehavior class has the following properties:</span></span>  
  
### <a name="maxconcurrentcalls"></a><span data-ttu-id="edfc7-109">maxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="edfc7-109">MaxConcurrentCalls</span></span>  
 <span data-ttu-id="edfc7-110">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="edfc7-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="edfc7-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="edfc7-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="edfc7-112">ServiceHost içindeki tüm dağıtıcı nesnelerinde etkin olarak işlenen ileti sayısı.</span><span class="sxs-lookup"><span data-stu-id="edfc7-112">The maximum number of messages actively processing across all dispatcher objects in a ServiceHost.</span></span>  
  
### <a name="maxconcurrentinstances"></a><span data-ttu-id="edfc7-113">MaxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="edfc7-113">MaxConcurrentInstances</span></span>  
 <span data-ttu-id="edfc7-114">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="edfc7-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="edfc7-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="edfc7-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="edfc7-116">Bir kerede yürütebilir hizmet nesneleri maksimum sayısı.</span><span class="sxs-lookup"><span data-stu-id="edfc7-116">The maximum number of service objects that can execute at one time.</span></span>  
  
### <a name="maxconcurrentsessions"></a><span data-ttu-id="edfc7-117">MaxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="edfc7-117">MaxConcurrentSessions</span></span>  
 <span data-ttu-id="edfc7-118">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="edfc7-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="edfc7-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="edfc7-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="edfc7-120">Bir ana bilgisayar aynı anda kabul edebilir oturumları maksimum sayısı.</span><span class="sxs-lookup"><span data-stu-id="edfc7-120">The maximum number of sessions a host can accept at one time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="edfc7-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="edfc7-121">Requirements</span></span>  
  
|<span data-ttu-id="edfc7-122">MOF</span><span class="sxs-lookup"><span data-stu-id="edfc7-122">MOF</span></span>|<span data-ttu-id="edfc7-123">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="edfc7-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="edfc7-124">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="edfc7-124">Namespace</span></span>|<span data-ttu-id="edfc7-125">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="edfc7-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="edfc7-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="edfc7-126">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>

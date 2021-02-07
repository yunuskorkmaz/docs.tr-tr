---
description: 'Hakkında daha fazla bilgi edinin: WAIT_OPTION numaralandırması'
title: WAIT_OPTION Numaralandırması
ms.date: 03/30/2017
api_name:
- WAIT_OPTION
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- WAIT_OPTION
helpviewer_keywords:
- WAIT_OPTION enumeration [.NET Framework hosting]
ms.assetid: 962fc293-8ded-4b3b-90ce-2c21a4f1b244
topic_type:
- apiref
ms.openlocfilehash: 1d651909e0f62f2db7478a6e0b37139d1f953196
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679153"
---
# <a name="wait_option-enumeration"></a><span data-ttu-id="90f44-103">WAIT_OPTION Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="90f44-103">WAIT_OPTION Enumeration</span></span>

<span data-ttu-id="90f44-104">Ortak dil çalışma zamanı (CLR) blokları tarafından istenen işlem için bir konağın yapması gereken eylemi belirten değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="90f44-104">Contains values that indicate the action a host should take if an operation requested by the common language runtime (CLR) blocks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90f44-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="90f44-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    WAIT_MSGPUMP       = 0x1,  
    WAIT_ALERTABLE     = 0x2,  
    WAIT_NOTINDEADLOCK = 0x4,  
} WAIT_OPTION;  
```  
  
## <a name="members"></a><span data-ttu-id="90f44-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="90f44-106">Members</span></span>  
  
|<span data-ttu-id="90f44-107">Üye</span><span class="sxs-lookup"><span data-stu-id="90f44-107">Member</span></span>|<span data-ttu-id="90f44-108">Description</span><span class="sxs-lookup"><span data-stu-id="90f44-108">Description</span></span>|  
|------------|-----------------|  
|`WAIT_ALERTABLE`|<span data-ttu-id="90f44-109">CLR [IHostTask:: Alert](ihosttask-alert-method.md) yöntemini çağırırsa, konağın görevin başlatılabilmesi uyandırılır olması gerektiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="90f44-109">Notifies the host that the task should be awakened if the CLR calls the [IHostTask::Alert](ihosttask-alert-method.md) method.</span></span>|  
|`WAIT_MSGPUMP`|<span data-ttu-id="90f44-110">İş parçacığı engellenirse, konağa geçerli işletim sistemi iş parçacığında ileti göndericisi gerektiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="90f44-110">Notifies the host that it must pump messages on the current OS thread if the thread becomes blocked.</span></span> <span data-ttu-id="90f44-111">Çalışma zamanı bu değeri yalnızca bir <xref:System.Threading.ApartmentState.STA> iş parçacığında belirtir.</span><span class="sxs-lookup"><span data-stu-id="90f44-111">The runtime specifies this value only on an <xref:System.Threading.ApartmentState.STA> thread.</span></span>|  
|`WAIT_NOTINDEADLOCK`|<span data-ttu-id="90f44-112">Ana bilgisayara belirtilen eşitleme isteğinin bir konak tarafından bölünemez olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="90f44-112">Notifies the host that the specified synchronization request cannot be broken by a host.</span></span> <span data-ttu-id="90f44-113">Diğer bir deyişle, ana bilgisayar dönemeyebilir `HOST_E_DEADLOCK` .</span><span class="sxs-lookup"><span data-stu-id="90f44-113">That is, the host cannot return `HOST_E_DEADLOCK`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90f44-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="90f44-114">Remarks</span></span>  

 <span data-ttu-id="90f44-115">[IHostTaskManager:: Sleep](ihosttaskmanager-sleep-method.md) ve [IHostTaskManager:: SwitchToTask](ihosttaskmanager-switchtotask-method.md) yöntemlerinin her ikisi de bu türde bir parametre alır.</span><span class="sxs-lookup"><span data-stu-id="90f44-115">The [IHostTaskManager::Sleep](ihosttaskmanager-sleep-method.md) and [IHostTaskManager::SwitchToTask](ihosttaskmanager-switchtotask-method.md) methods both take a parameter of this type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90f44-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="90f44-116">Requirements</span></span>  

 <span data-ttu-id="90f44-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90f44-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90f44-118">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="90f44-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="90f44-119">**Kitaplık:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="90f44-119">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="90f44-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90f44-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90f44-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="90f44-121">See also</span></span>

- [<span data-ttu-id="90f44-122">Barındırma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="90f44-122">Hosting Enumerations</span></span>](hosting-enumerations.md)

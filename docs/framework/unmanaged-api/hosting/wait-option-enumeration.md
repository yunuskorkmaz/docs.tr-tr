---
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
ms.openlocfilehash: 056d41df328de5796eec9f04589205d18b408f1f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732807"
---
# <a name="wait_option-enumeration"></a><span data-ttu-id="f5c20-102">WAIT_OPTION Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="f5c20-102">WAIT_OPTION Enumeration</span></span>

<span data-ttu-id="f5c20-103">Ortak dil çalışma zamanı (CLR) blokları tarafından istenen işlem için bir konağın yapması gereken eylemi belirten değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="f5c20-103">Contains values that indicate the action a host should take if an operation requested by the common language runtime (CLR) blocks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5c20-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="f5c20-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    WAIT_MSGPUMP       = 0x1,  
    WAIT_ALERTABLE     = 0x2,  
    WAIT_NOTINDEADLOCK = 0x4,  
} WAIT_OPTION;  
```  
  
## <a name="members"></a><span data-ttu-id="f5c20-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="f5c20-105">Members</span></span>  
  
|<span data-ttu-id="f5c20-106">Üye</span><span class="sxs-lookup"><span data-stu-id="f5c20-106">Member</span></span>|<span data-ttu-id="f5c20-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f5c20-107">Description</span></span>|  
|------------|-----------------|  
|`WAIT_ALERTABLE`|<span data-ttu-id="f5c20-108">CLR [IHostTask:: Alert](ihosttask-alert-method.md) yöntemini çağırırsa, konağın görevin başlatılabilmesi uyandırılır olması gerektiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="f5c20-108">Notifies the host that the task should be awakened if the CLR calls the [IHostTask::Alert](ihosttask-alert-method.md) method.</span></span>|  
|`WAIT_MSGPUMP`|<span data-ttu-id="f5c20-109">İş parçacığı engellenirse, konağa geçerli işletim sistemi iş parçacığında ileti göndericisi gerektiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="f5c20-109">Notifies the host that it must pump messages on the current OS thread if the thread becomes blocked.</span></span> <span data-ttu-id="f5c20-110">Çalışma zamanı bu değeri yalnızca bir <xref:System.Threading.ApartmentState.STA> iş parçacığında belirtir.</span><span class="sxs-lookup"><span data-stu-id="f5c20-110">The runtime specifies this value only on an <xref:System.Threading.ApartmentState.STA> thread.</span></span>|  
|`WAIT_NOTINDEADLOCK`|<span data-ttu-id="f5c20-111">Ana bilgisayara belirtilen eşitleme isteğinin bir konak tarafından bölünemez olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="f5c20-111">Notifies the host that the specified synchronization request cannot be broken by a host.</span></span> <span data-ttu-id="f5c20-112">Diğer bir deyişle, ana bilgisayar dönemeyebilir `HOST_E_DEADLOCK` .</span><span class="sxs-lookup"><span data-stu-id="f5c20-112">That is, the host cannot return `HOST_E_DEADLOCK`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f5c20-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f5c20-113">Remarks</span></span>  

 <span data-ttu-id="f5c20-114">[IHostTaskManager:: Sleep](ihosttaskmanager-sleep-method.md) ve [IHostTaskManager:: SwitchToTask](ihosttaskmanager-switchtotask-method.md) yöntemlerinin her ikisi de bu türde bir parametre alır.</span><span class="sxs-lookup"><span data-stu-id="f5c20-114">The [IHostTaskManager::Sleep](ihosttaskmanager-sleep-method.md) and [IHostTaskManager::SwitchToTask](ihosttaskmanager-switchtotask-method.md) methods both take a parameter of this type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5c20-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f5c20-115">Requirements</span></span>  

 <span data-ttu-id="f5c20-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5c20-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5c20-117">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f5c20-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f5c20-118">**Kitaplık:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f5c20-118">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f5c20-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5c20-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5c20-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f5c20-120">See also</span></span>

- [<span data-ttu-id="f5c20-121">Barındırma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="f5c20-121">Hosting Enumerations</span></span>](hosting-enumerations.md)

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
ms.openlocfilehash: 4c57a3fde3565a21800c60794b6c2d1c7616ddd8
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008007"
---
# <a name="wait_option-enumeration"></a><span data-ttu-id="f3785-102">WAIT_OPTION Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="f3785-102">WAIT_OPTION Enumeration</span></span>
<span data-ttu-id="f3785-103">Ortak dil çalışma zamanı (CLR) blokları tarafından istenen işlem için bir konağın yapması gereken eylemi belirten değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="f3785-103">Contains values that indicate the action a host should take if an operation requested by the common language runtime (CLR) blocks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3785-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f3785-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    WAIT_MSGPUMP       = 0x1,  
    WAIT_ALERTABLE     = 0x2,  
    WAIT_NOTINDEADLOCK = 0x4,  
} WAIT_OPTION;  
```  
  
## <a name="members"></a><span data-ttu-id="f3785-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="f3785-105">Members</span></span>  
  
|<span data-ttu-id="f3785-106">Üye</span><span class="sxs-lookup"><span data-stu-id="f3785-106">Member</span></span>|<span data-ttu-id="f3785-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f3785-107">Description</span></span>|  
|------------|-----------------|  
|`WAIT_ALERTABLE`|<span data-ttu-id="f3785-108">CLR [IHostTask:: Alert](ihosttask-alert-method.md) yöntemini çağırırsa, konağın görevin başlatılabilmesi uyandırılır olması gerektiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="f3785-108">Notifies the host that the task should be awakened if the CLR calls the [IHostTask::Alert](ihosttask-alert-method.md) method.</span></span>|  
|`WAIT_MSGPUMP`|<span data-ttu-id="f3785-109">İş parçacığı engellenirse, konağa geçerli işletim sistemi iş parçacığında ileti göndericisi gerektiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="f3785-109">Notifies the host that it must pump messages on the current OS thread if the thread becomes blocked.</span></span> <span data-ttu-id="f3785-110">Çalışma zamanı bu değeri yalnızca bir <xref:System.Threading.ApartmentState.STA> iş parçacığında belirtir.</span><span class="sxs-lookup"><span data-stu-id="f3785-110">The runtime specifies this value only on an <xref:System.Threading.ApartmentState.STA> thread.</span></span>|  
|`WAIT_NOTINDEADLOCK`|<span data-ttu-id="f3785-111">Ana bilgisayara belirtilen eşitleme isteğinin bir konak tarafından bölünemez olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="f3785-111">Notifies the host that the specified synchronization request cannot be broken by a host.</span></span> <span data-ttu-id="f3785-112">Diğer bir deyişle, ana bilgisayar dönemeyebilir `HOST_E_DEADLOCK` .</span><span class="sxs-lookup"><span data-stu-id="f3785-112">That is, the host cannot return `HOST_E_DEADLOCK`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3785-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f3785-113">Remarks</span></span>  
 <span data-ttu-id="f3785-114">[IHostTaskManager:: Sleep](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md) ve [IHostTaskManager:: SwitchToTask](ihosttaskmanager-switchtotask-method.md) yöntemlerinin her ikisi de bu türde bir parametre alır.</span><span class="sxs-lookup"><span data-stu-id="f3785-114">The [IHostTaskManager::Sleep](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md) and [IHostTaskManager::SwitchToTask](ihosttaskmanager-switchtotask-method.md) methods both take a parameter of this type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3785-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f3785-115">Requirements</span></span>  
 <span data-ttu-id="f3785-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3785-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3785-117">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f3785-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f3785-118">**Kitaplık:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f3785-118">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f3785-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3785-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3785-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f3785-120">See also</span></span>

- [<span data-ttu-id="f3785-121">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="f3785-121">Hosting Enumerations</span></span>](hosting-enumerations.md)

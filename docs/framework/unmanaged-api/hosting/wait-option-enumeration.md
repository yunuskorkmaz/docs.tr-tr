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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fb37394799db39baa406ef332066d5ebb2dbf19d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441935"
---
# <a name="waitoption-enumeration"></a><span data-ttu-id="bd1d0-102">WAIT_OPTION Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="bd1d0-102">WAIT_OPTION Enumeration</span></span>
<span data-ttu-id="bd1d0-103">Bir ana bilgisayar ortak dil çalışma zamanı (CLR) bloklarla istenen işlem, eylemde gösteren değerler içeriyor.</span><span class="sxs-lookup"><span data-stu-id="bd1d0-103">Contains values that indicate the action a host should take if an operation requested by the common language runtime (CLR) blocks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd1d0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bd1d0-104">Syntax</span></span>  
  
```  
typedef enum {  
    WAIT_MSGPUMP       = 0x1,  
    WAIT_ALERTABLE     = 0x2,  
    WAIT_NOTINDEADLOCK = 0x4,  
} WAIT_OPTION;  
```  
  
## <a name="members"></a><span data-ttu-id="bd1d0-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="bd1d0-105">Members</span></span>  
  
|<span data-ttu-id="bd1d0-106">Üye</span><span class="sxs-lookup"><span data-stu-id="bd1d0-106">Member</span></span>|<span data-ttu-id="bd1d0-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bd1d0-107">Description</span></span>|  
|------------|-----------------|  
|`WAIT_ALERTABLE`|<span data-ttu-id="bd1d0-108">Ana bilgisayar CLR çağırırsa, görev uyandırdı olduğunu bildirir [Ihosttask::alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="bd1d0-108">Notifies the host that the task should be awakened if the CLR calls the [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) method.</span></span>|  
|`WAIT_MSGPUMP`|<span data-ttu-id="bd1d0-109">Ana iş parçacığı engellenmiş duruma gelirse, geçerli işletim sistemi iş parçacığı iletileri göndermelidir bildirir.</span><span class="sxs-lookup"><span data-stu-id="bd1d0-109">Notifies the host that it must pump messages on the current OS thread if the thread becomes blocked.</span></span> <span data-ttu-id="bd1d0-110">Çalışma zamanı yalnızca bu değeri belirten bir <xref:System.Threading.ApartmentState.STA> iş parçacığı.</span><span class="sxs-lookup"><span data-stu-id="bd1d0-110">The runtime specifies this value only on an <xref:System.Threading.ApartmentState.STA> thread.</span></span>|  
|`WAIT_NOTINDEADLOCK`|<span data-ttu-id="bd1d0-111">Konak belirtilen eşitleme isteği bir ana bilgisayar tarafından ayrılmış bildirir.</span><span class="sxs-lookup"><span data-stu-id="bd1d0-111">Notifies the host that the specified synchronization request cannot be broken by a host.</span></span> <span data-ttu-id="bd1d0-112">Diğer bir deyişle, konak döndüremez `HOST_E_DEADLOCK`.</span><span class="sxs-lookup"><span data-stu-id="bd1d0-112">That is, the host cannot return `HOST_E_DEADLOCK`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bd1d0-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bd1d0-113">Remarks</span></span>  
 <span data-ttu-id="bd1d0-114">[Ihosttaskmanager::Sleep](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md) ve [Ihosttaskmanager::switchtotask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-switchtotask-method.md) yöntemleri hem bu türde bir parametre alın.</span><span class="sxs-lookup"><span data-stu-id="bd1d0-114">The [IHostTaskManager::Sleep](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md) and [IHostTaskManager::SwitchToTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-switchtotask-method.md) methods both take a parameter of this type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd1d0-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bd1d0-115">Requirements</span></span>  
 <span data-ttu-id="bd1d0-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd1d0-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd1d0-117">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bd1d0-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bd1d0-118">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bd1d0-118">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bd1d0-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd1d0-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd1d0-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bd1d0-120">See Also</span></span>  
 [<span data-ttu-id="bd1d0-121">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="bd1d0-121">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)

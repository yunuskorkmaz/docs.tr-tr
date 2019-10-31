---
title: ETaskType Numaralandırması
ms.date: 03/30/2017
api_name:
- ETaskType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ETaskType
helpviewer_keywords:
- ETaskType enumeration [.NET Framework hosting]
ms.assetid: aa527b31-89d4-41f2-ad6f-63b76950b7df
topic_type:
- apiref
ms.openlocfilehash: bc956827ad59fc655137e4147e6d98b6d097d470
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138195"
---
# <a name="etasktype-enumeration"></a><span data-ttu-id="c364a-102">ETaskType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="c364a-102">ETaskType Enumeration</span></span>
<span data-ttu-id="c364a-103">Bir [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) veya [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) arabirimi tarafından temsil edilen görevin türünü gösteren değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="c364a-103">Contains values that indicate the type of task that is represented by either an [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) or an [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c364a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c364a-104">Syntax</span></span>  
  
```cpp  
typedef enum ETaskType {  
    TT_DEBUGGERHELPER           = 0x1,  
    TT_GC                       = 0x2,  
    TT_FINALIZER                = 0x4,  
    TT_THREADPOOL_TIMER         = 0x8,  
    TT_THREADPOOL_GATE          = 0x10,  
    TT_THREADPOOL_WORKER        = 0x20,  
    TT_THREADPOOL_IOCOMPLETION  = 0x40,  
    TT_ADUNLOAD                 = 0x80,  
    TT_USER                     = 0x100,  
    TT_THREADPOOL_WAIT          = 0x200,  
    TT_UNKNOWN                  = 0x80000000  
} ETaskType;  
```  
  
## <a name="members"></a><span data-ttu-id="c364a-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="c364a-105">Members</span></span>  
  
|<span data-ttu-id="c364a-106">Üye</span><span class="sxs-lookup"><span data-stu-id="c364a-106">Member</span></span>|<span data-ttu-id="c364a-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c364a-107">Description</span></span>|  
|------------|-----------------|  
|`TT_ADUNLOAD`|<span data-ttu-id="c364a-108">Arabirim bir uygulama etki alanı kaldırma görevini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c364a-108">The interface represents an application domain unloading task.</span></span>|  
|`TT_DEBUGGERHELPER`|<span data-ttu-id="c364a-109">Arabirim bir hata ayıklayıcı Yardımcısı görevini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c364a-109">The interface represents a debugger helper task.</span></span>|  
|`TT_FINALIZER`|<span data-ttu-id="c364a-110">Arabirim bir Sonlandırıcı görevini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c364a-110">The interface represents a finalizer task.</span></span>|  
|`TT_GC`|<span data-ttu-id="c364a-111">Arabirim bir çöp toplama görevini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c364a-111">The interface represents a garbage collection task.</span></span>|  
|`TT_THREADPOOL_GATE`|<span data-ttu-id="c364a-112">Arabirim bir kapı iş parçacığı görevini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c364a-112">The interface represents a gate thread task.</span></span>|  
|`TT_THREADPOOL_IOCOMPLETION`|<span data-ttu-id="c364a-113">Arabirim bir g/ç iş parçacığı görevini veya tamamlama bağlantı noktası iş parçacığı görevini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c364a-113">The interface represents an I/O thread task or a completion port thread task.</span></span>|  
|`TT_THREADPOOL_TIMER`|<span data-ttu-id="c364a-114">Arabirim bir zamanlayıcı iş parçacığı görevini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c364a-114">The interface represents a timer thread task.</span></span>|  
|`TT_THREADPOOL_WAIT`|<span data-ttu-id="c364a-115">Arabirim bir bekleme iş parçacığı görevini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c364a-115">The interface represents a wait thread task.</span></span>|  
|`TT_THREADPOOL_WORKER`|<span data-ttu-id="c364a-116">Arabirim bir çalışan iş parçacığı görevini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c364a-116">The interface represents a worker thread task.</span></span>|  
|`TT_UNKNOWN`|<span data-ttu-id="c364a-117">Görev bilinmiyor.</span><span class="sxs-lookup"><span data-stu-id="c364a-117">The task is unknown.</span></span>|  
|`TT_USER`|<span data-ttu-id="c364a-118">Arabirim bir Kullanıcı görevini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c364a-118">The interface represents a user task.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c364a-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c364a-119">Requirements</span></span>  
 <span data-ttu-id="c364a-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c364a-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c364a-121">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c364a-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c364a-122">**Kitaplık:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c364a-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c364a-123">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c364a-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c364a-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c364a-124">See also</span></span>

- [<span data-ttu-id="c364a-125">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="c364a-125">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)

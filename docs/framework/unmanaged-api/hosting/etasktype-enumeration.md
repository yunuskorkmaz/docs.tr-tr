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
ms.openlocfilehash: 0fa72568df77c4916a3c6676e1dcca7c0c616c4a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493324"
---
# <a name="etasktype-enumeration"></a><span data-ttu-id="59e10-102">ETaskType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="59e10-102">ETaskType Enumeration</span></span>
<span data-ttu-id="59e10-103">Bir [ICLRTask](iclrtask-interface.md) veya [IHostTask](ihosttask-interface.md) arabirimi tarafından temsil edilen görevin türünü gösteren değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="59e10-103">Contains values that indicate the type of task that is represented by either an [ICLRTask](iclrtask-interface.md) or an [IHostTask](ihosttask-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59e10-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="59e10-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="59e10-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="59e10-105">Members</span></span>  
  
|<span data-ttu-id="59e10-106">Üye</span><span class="sxs-lookup"><span data-stu-id="59e10-106">Member</span></span>|<span data-ttu-id="59e10-107">Description</span><span class="sxs-lookup"><span data-stu-id="59e10-107">Description</span></span>|  
|------------|-----------------|  
|`TT_ADUNLOAD`|<span data-ttu-id="59e10-108">Arabirim bir uygulama etki alanı kaldırma görevini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="59e10-108">The interface represents an application domain unloading task.</span></span>|  
|`TT_DEBUGGERHELPER`|<span data-ttu-id="59e10-109">Arabirim bir hata ayıklayıcı Yardımcısı görevini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="59e10-109">The interface represents a debugger helper task.</span></span>|  
|`TT_FINALIZER`|<span data-ttu-id="59e10-110">Arabirim bir Sonlandırıcı görevini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="59e10-110">The interface represents a finalizer task.</span></span>|  
|`TT_GC`|<span data-ttu-id="59e10-111">Arabirim bir çöp toplama görevini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="59e10-111">The interface represents a garbage collection task.</span></span>|  
|`TT_THREADPOOL_GATE`|<span data-ttu-id="59e10-112">Arabirim bir kapı iş parçacığı görevini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="59e10-112">The interface represents a gate thread task.</span></span>|  
|`TT_THREADPOOL_IOCOMPLETION`|<span data-ttu-id="59e10-113">Arabirim bir g/ç iş parçacığı görevini veya tamamlama bağlantı noktası iş parçacığı görevini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="59e10-113">The interface represents an I/O thread task or a completion port thread task.</span></span>|  
|`TT_THREADPOOL_TIMER`|<span data-ttu-id="59e10-114">Arabirim bir zamanlayıcı iş parçacığı görevini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="59e10-114">The interface represents a timer thread task.</span></span>|  
|`TT_THREADPOOL_WAIT`|<span data-ttu-id="59e10-115">Arabirim bir bekleme iş parçacığı görevini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="59e10-115">The interface represents a wait thread task.</span></span>|  
|`TT_THREADPOOL_WORKER`|<span data-ttu-id="59e10-116">Arabirim bir çalışan iş parçacığı görevini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="59e10-116">The interface represents a worker thread task.</span></span>|  
|`TT_UNKNOWN`|<span data-ttu-id="59e10-117">Görev bilinmiyor.</span><span class="sxs-lookup"><span data-stu-id="59e10-117">The task is unknown.</span></span>|  
|`TT_USER`|<span data-ttu-id="59e10-118">Arabirim bir Kullanıcı görevini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="59e10-118">The interface represents a user task.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="59e10-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="59e10-119">Requirements</span></span>  
 <span data-ttu-id="59e10-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59e10-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59e10-121">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="59e10-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="59e10-122">**Kitaplık:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="59e10-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="59e10-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59e10-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59e10-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="59e10-124">See also</span></span>

- [<span data-ttu-id="59e10-125">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="59e10-125">Hosting Enumerations</span></span>](hosting-enumerations.md)

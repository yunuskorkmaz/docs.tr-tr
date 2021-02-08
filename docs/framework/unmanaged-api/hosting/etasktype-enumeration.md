---
description: 'Daha fazla bilgi edinin: ETaskType numaralandırması'
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
ms.openlocfilehash: 7cb241765b2ff3b4a3402221c6b3e2b7ff6305c1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785412"
---
# <a name="etasktype-enumeration"></a><span data-ttu-id="d58c2-103">ETaskType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="d58c2-103">ETaskType Enumeration</span></span>

<span data-ttu-id="d58c2-104">Bir [ICLRTask](iclrtask-interface.md) veya [IHostTask](ihosttask-interface.md) arabirimi tarafından temsil edilen görevin türünü gösteren değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="d58c2-104">Contains values that indicate the type of task that is represented by either an [ICLRTask](iclrtask-interface.md) or an [IHostTask](ihosttask-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d58c2-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="d58c2-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="d58c2-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="d58c2-106">Members</span></span>  
  
|<span data-ttu-id="d58c2-107">Üye</span><span class="sxs-lookup"><span data-stu-id="d58c2-107">Member</span></span>|<span data-ttu-id="d58c2-108">Description</span><span class="sxs-lookup"><span data-stu-id="d58c2-108">Description</span></span>|  
|------------|-----------------|  
|`TT_ADUNLOAD`|<span data-ttu-id="d58c2-109">Arabirim bir uygulama etki alanı kaldırma görevini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d58c2-109">The interface represents an application domain unloading task.</span></span>|  
|`TT_DEBUGGERHELPER`|<span data-ttu-id="d58c2-110">Arabirim bir hata ayıklayıcı Yardımcısı görevini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d58c2-110">The interface represents a debugger helper task.</span></span>|  
|`TT_FINALIZER`|<span data-ttu-id="d58c2-111">Arabirim bir Sonlandırıcı görevini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d58c2-111">The interface represents a finalizer task.</span></span>|  
|`TT_GC`|<span data-ttu-id="d58c2-112">Arabirim bir çöp toplama görevini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d58c2-112">The interface represents a garbage collection task.</span></span>|  
|`TT_THREADPOOL_GATE`|<span data-ttu-id="d58c2-113">Arabirim bir kapı iş parçacığı görevini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d58c2-113">The interface represents a gate thread task.</span></span>|  
|`TT_THREADPOOL_IOCOMPLETION`|<span data-ttu-id="d58c2-114">Arabirim bir g/ç iş parçacığı görevini veya tamamlama bağlantı noktası iş parçacığı görevini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d58c2-114">The interface represents an I/O thread task or a completion port thread task.</span></span>|  
|`TT_THREADPOOL_TIMER`|<span data-ttu-id="d58c2-115">Arabirim bir zamanlayıcı iş parçacığı görevini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d58c2-115">The interface represents a timer thread task.</span></span>|  
|`TT_THREADPOOL_WAIT`|<span data-ttu-id="d58c2-116">Arabirim bir bekleme iş parçacığı görevini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d58c2-116">The interface represents a wait thread task.</span></span>|  
|`TT_THREADPOOL_WORKER`|<span data-ttu-id="d58c2-117">Arabirim bir çalışan iş parçacığı görevini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d58c2-117">The interface represents a worker thread task.</span></span>|  
|`TT_UNKNOWN`|<span data-ttu-id="d58c2-118">Görev bilinmiyor.</span><span class="sxs-lookup"><span data-stu-id="d58c2-118">The task is unknown.</span></span>|  
|`TT_USER`|<span data-ttu-id="d58c2-119">Arabirim bir Kullanıcı görevini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d58c2-119">The interface represents a user task.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d58c2-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d58c2-120">Requirements</span></span>  

 <span data-ttu-id="d58c2-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d58c2-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d58c2-122">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d58c2-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d58c2-123">**Kitaplık:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d58c2-123">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d58c2-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d58c2-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d58c2-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d58c2-125">See also</span></span>

- [<span data-ttu-id="d58c2-126">Barındırma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="d58c2-126">Hosting Enumerations</span></span>](hosting-enumerations.md)

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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f256195a4cd5b18f568e05156db867aa5dba9161
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59229829"
---
# <a name="etasktype-enumeration"></a><span data-ttu-id="6e723-102">ETaskType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="6e723-102">ETaskType Enumeration</span></span>
<span data-ttu-id="6e723-103">Tarafından temsil edilen bir görev türünü gösteren değerleri içeren bir [Iclrtask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) veya [Ihosttask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="6e723-103">Contains values that indicate the type of task that is represented by either an [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) or an [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e723-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6e723-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="6e723-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="6e723-105">Members</span></span>  
  
|<span data-ttu-id="6e723-106">Üye</span><span class="sxs-lookup"><span data-stu-id="6e723-106">Member</span></span>|<span data-ttu-id="6e723-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6e723-107">Description</span></span>|  
|------------|-----------------|  
|`TT_ADUNLOAD`|<span data-ttu-id="6e723-108">Arabirimi, bir uygulama etki alanı kaldırma görevi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6e723-108">The interface represents an application domain unloading task.</span></span>|  
|`TT_DEBUGGERHELPER`|<span data-ttu-id="6e723-109">Arabirimi, bir hata ayıklayıcı Yardımcısı görevi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6e723-109">The interface represents a debugger helper task.</span></span>|  
|`TT_FINALIZER`|<span data-ttu-id="6e723-110">Arabirimi, bir sonlandırıcı görevi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6e723-110">The interface represents a finalizer task.</span></span>|  
|`TT_GC`|<span data-ttu-id="6e723-111">Arabirimi, bir atık toplama görevi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6e723-111">The interface represents a garbage collection task.</span></span>|  
|`TT_THREADPOOL_GATE`|<span data-ttu-id="6e723-112">Arabirimi, bir ağ geçidi iş parçacığı görevi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6e723-112">The interface represents a gate thread task.</span></span>|  
|`TT_THREADPOOL_IOCOMPLETION`|<span data-ttu-id="6e723-113">Arabirimi, bir g/ç iş parçacığı görevi ya da bir tamamlanma bağlantı noktası iş parçacığı görevi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6e723-113">The interface represents an I/O thread task or a completion port thread task.</span></span>|  
|`TT_THREADPOOL_TIMER`|<span data-ttu-id="6e723-114">Arabirimi, bir zamanlayıcı iş parçacığı görevi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6e723-114">The interface represents a timer thread task.</span></span>|  
|`TT_THREADPOOL_WAIT`|<span data-ttu-id="6e723-115">Arabirimi, bir bekleme iş parçacığı görevi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6e723-115">The interface represents a wait thread task.</span></span>|  
|`TT_THREADPOOL_WORKER`|<span data-ttu-id="6e723-116">Arabirimi, bir çalışan iş parçacığı görevi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6e723-116">The interface represents a worker thread task.</span></span>|  
|`TT_UNKNOWN`|<span data-ttu-id="6e723-117">Görev bilinmiyor.</span><span class="sxs-lookup"><span data-stu-id="6e723-117">The task is unknown.</span></span>|  
|`TT_USER`|<span data-ttu-id="6e723-118">Arabirimi, bir kullanıcı görevini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6e723-118">The interface represents a user task.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6e723-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6e723-119">Requirements</span></span>  
 <span data-ttu-id="6e723-120">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e723-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e723-121">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6e723-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6e723-122">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6e723-122">**Library:** MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="6e723-123">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="6e723-123">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6e723-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e723-124">See also</span></span>

- [<span data-ttu-id="6e723-125">Barındırma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="6e723-125">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)

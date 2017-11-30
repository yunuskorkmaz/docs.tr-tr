---
title: "ETaskType Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ETaskType
api_location: mscoree.dll
api_type: COM
f1_keywords: ETaskType
helpviewer_keywords: ETaskType enumeration [.NET Framework hosting]
ms.assetid: aa527b31-89d4-41f2-ad6f-63b76950b7df
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 52e027c5d2ead70bbd624fafe3021121557cd261
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="etasktype-enumeration"></a><span data-ttu-id="3bbec-102">ETaskType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="3bbec-102">ETaskType Enumeration</span></span>
<span data-ttu-id="3bbec-103">Tarafından temsil edilen görevi türünü belirtmek değerleri içeren bir [Iclrtask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) veya bir [Ihosttask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="3bbec-103">Contains values that indicate the type of task that is represented by either an [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) or an [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bbec-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3bbec-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="3bbec-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="3bbec-105">Members</span></span>  
  
|<span data-ttu-id="3bbec-106">Üye</span><span class="sxs-lookup"><span data-stu-id="3bbec-106">Member</span></span>|<span data-ttu-id="3bbec-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3bbec-107">Description</span></span>|  
|------------|-----------------|  
|`TT_ADUNLOAD`|<span data-ttu-id="3bbec-108">Bir uygulama etki alanı kaldırılırken görev arabirimi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3bbec-108">The interface represents an application domain unloading task.</span></span>|  
|`TT_DEBUGGERHELPER`|<span data-ttu-id="3bbec-109">Arabirimi hata ayıklayıcı yardımcı görev temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3bbec-109">The interface represents a debugger helper task.</span></span>|  
|`TT_FINALIZER`|<span data-ttu-id="3bbec-110">Arabirimi sonlandırıcıyı görev temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3bbec-110">The interface represents a finalizer task.</span></span>|  
|`TT_GC`|<span data-ttu-id="3bbec-111">Arabirimi bir atık toplama görevi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3bbec-111">The interface represents a garbage collection task.</span></span>|  
|`TT_THREADPOOL_GATE`|<span data-ttu-id="3bbec-112">Bir ağ geçidi iş parçacığının görevi arabirimi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3bbec-112">The interface represents a gate thread task.</span></span>|  
|`TT_THREADPOOL_IOCOMPLETION`|<span data-ttu-id="3bbec-113">Bir g/ç iş parçacığı görevi veya görev tamamlama bağlantı noktası iş parçacığı görev arabirimi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3bbec-113">The interface represents an I/O thread task or a completion port thread task.</span></span>|  
|`TT_THREADPOOL_TIMER`|<span data-ttu-id="3bbec-114">Zamanlayıcı iş parçacığı görevi arabirimi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3bbec-114">The interface represents a timer thread task.</span></span>|  
|`TT_THREADPOOL_WAIT`|<span data-ttu-id="3bbec-115">Arabirimi bir bekleme iş parçacığının görevi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3bbec-115">The interface represents a wait thread task.</span></span>|  
|`TT_THREADPOOL_WORKER`|<span data-ttu-id="3bbec-116">Bir çalışan iş parçacığının görevi arabirimi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3bbec-116">The interface represents a worker thread task.</span></span>|  
|`TT_UNKNOWN`|<span data-ttu-id="3bbec-117">Görev bilinmiyor.</span><span class="sxs-lookup"><span data-stu-id="3bbec-117">The task is unknown.</span></span>|  
|`TT_USER`|<span data-ttu-id="3bbec-118">Bir kullanıcı görev arabirimi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3bbec-118">The interface represents a user task.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3bbec-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3bbec-119">Requirements</span></span>  
 <span data-ttu-id="3bbec-120">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3bbec-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3bbec-121">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3bbec-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3bbec-122">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3bbec-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3bbec-123">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3bbec-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bbec-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3bbec-124">See Also</span></span>  
 [<span data-ttu-id="3bbec-125">Barındırma numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="3bbec-125">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)

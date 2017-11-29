---
title: ICorDebugManagedCallback3 Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback3
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback3
helpviewer_keywords: ICorDebugManagedCallback3 interface [.NET Framework debugging]
ms.assetid: a95389d3-cf2e-47a4-9805-61426acc6b65
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d2f24cc8fbd8533ef6717bc1dcd1baab0ea9ab45
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmanagedcallback3-interface"></a><span data-ttu-id="8c8ed-102">ICorDebugManagedCallback3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8c8ed-102">ICorDebugManagedCallback3 Interface</span></span>
<span data-ttu-id="8c8ed-103">Etkinleştirilmiş bir özel hata ayıklayıcı bildiriminin tetiklendiğini gösteren bir geri arama yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="8c8ed-103">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8c8ed-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8c8ed-104">Methods</span></span>  
  
|<span data-ttu-id="8c8ed-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="8c8ed-105">Method</span></span>|<span data-ttu-id="8c8ed-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8c8ed-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8c8ed-107">CustomNotification yöntemi</span><span class="sxs-lookup"><span data-stu-id="8c8ed-107">CustomNotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md)|<span data-ttu-id="8c8ed-108">Etkin özel hata ayıklayıcı bildirim yükseltildiğinde gösterir.</span><span class="sxs-lookup"><span data-stu-id="8c8ed-108">Indicates that an enabled custom debugger notification has been raised.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c8ed-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8c8ed-109">Remarks</span></span>  
 <span data-ttu-id="8c8ed-110">Bu arabirim mantıksal bir uzantısıdır [Icordebugmanagedcallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) ve [Icordebugmanagedcallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) arabirimleri.</span><span class="sxs-lookup"><span data-stu-id="8c8ed-110">This interface is a logical extension of the [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) and [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8c8ed-111">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="8c8ed-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c8ed-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8c8ed-112">Requirements</span></span>  
 <span data-ttu-id="8c8ed-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c8ed-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c8ed-114">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8c8ed-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8c8ed-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8c8ed-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8c8ed-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c8ed-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c8ed-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8c8ed-117">See Also</span></span>  
 [<span data-ttu-id="8c8ed-118">Icordebugmanagedcallback arabirimi</span><span class="sxs-lookup"><span data-stu-id="8c8ed-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)  
 [<span data-ttu-id="8c8ed-119">Icordebugmanagedcallback2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="8c8ed-119">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [<span data-ttu-id="8c8ed-120">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8c8ed-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="8c8ed-121">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="8c8ed-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

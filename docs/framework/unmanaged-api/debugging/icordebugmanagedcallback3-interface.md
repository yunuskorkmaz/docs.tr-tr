---
title: ICorDebugManagedCallback3 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback3
helpviewer_keywords:
- ICorDebugManagedCallback3 interface [.NET Framework debugging]
ms.assetid: a95389d3-cf2e-47a4-9805-61426acc6b65
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ab1dab753728102fc27e39c3ed64bf776e2e5ad5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54634482"
---
# <a name="icordebugmanagedcallback3-interface"></a><span data-ttu-id="6b43e-102">ICorDebugManagedCallback3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6b43e-102">ICorDebugManagedCallback3 Interface</span></span>
<span data-ttu-id="6b43e-103">Etkinleştirilmiş bir özel hata ayıklayıcı bildiriminin tetiklendiğini gösteren bir geri arama yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6b43e-103">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6b43e-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6b43e-104">Methods</span></span>  
  
|<span data-ttu-id="6b43e-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="6b43e-105">Method</span></span>|<span data-ttu-id="6b43e-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6b43e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6b43e-107">CustomNotification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6b43e-107">CustomNotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md)|<span data-ttu-id="6b43e-108">Bir etkin özel hata ayıklayıcı bildiriminin tetiklendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="6b43e-108">Indicates that an enabled custom debugger notification has been raised.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b43e-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6b43e-109">Remarks</span></span>  
 <span data-ttu-id="6b43e-110">Bu arabirim öğesinin mantıksal uzantısıdır [Icordebugmanagedcallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) ve [Icordebugmanagedcallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) arabirimleri.</span><span class="sxs-lookup"><span data-stu-id="6b43e-110">This interface is a logical extension of the [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) and [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6b43e-111">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="6b43e-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b43e-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6b43e-112">Requirements</span></span>  
 <span data-ttu-id="6b43e-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b43e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b43e-114">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6b43e-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6b43e-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6b43e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6b43e-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b43e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b43e-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6b43e-117">See also</span></span>
- [<span data-ttu-id="6b43e-118">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6b43e-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
- [<span data-ttu-id="6b43e-119">ICorDebugManagedCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6b43e-119">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="6b43e-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6b43e-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="6b43e-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="6b43e-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

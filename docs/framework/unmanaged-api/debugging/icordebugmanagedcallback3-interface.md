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
ms.openlocfilehash: b97f29b94ed4fad6892697ca1c7ed4a20c99c03e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793276"
---
# <a name="icordebugmanagedcallback3-interface"></a><span data-ttu-id="b894d-102">ICorDebugManagedCallback3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b894d-102">ICorDebugManagedCallback3 Interface</span></span>
<span data-ttu-id="b894d-103">Etkinleştirilmiş bir özel hata ayıklayıcı bildiriminin tetiklendiğini gösteren bir geri arama yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b894d-103">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b894d-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b894d-104">Methods</span></span>  
  
|<span data-ttu-id="b894d-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="b894d-105">Method</span></span>|<span data-ttu-id="b894d-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b894d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b894d-107">CustomNotification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b894d-107">CustomNotification Method</span></span>](icordebugmanagedcallback3-customnotification-method.md)|<span data-ttu-id="b894d-108">Etkin bir özel hata ayıklayıcı bildiriminin yapıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b894d-108">Indicates that an enabled custom debugger notification has been raised.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b894d-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b894d-109">Remarks</span></span>  
 <span data-ttu-id="b894d-110">Bu arabirim, [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) ve [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) arabirimlerinin mantıksal bir uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="b894d-110">This interface is a logical extension of the [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) and [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b894d-111">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="b894d-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b894d-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b894d-112">Requirements</span></span>  
 <span data-ttu-id="b894d-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b894d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b894d-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b894d-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b894d-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b894d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b894d-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b894d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b894d-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b894d-117">See also</span></span>

- [<span data-ttu-id="b894d-118">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b894d-118">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
- [<span data-ttu-id="b894d-119">ICorDebugManagedCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b894d-119">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="b894d-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b894d-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="b894d-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="b894d-121">Debugging</span></span>](index.md)

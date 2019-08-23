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
ms.openlocfilehash: 138ac80a9abb64d4c004e83e53ed1eea2b124ff2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69909904"
---
# <a name="icordebugmanagedcallback3-interface"></a><span data-ttu-id="fea42-102">ICorDebugManagedCallback3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fea42-102">ICorDebugManagedCallback3 Interface</span></span>
<span data-ttu-id="fea42-103">Etkinleştirilmiş bir özel hata ayıklayıcı bildiriminin tetiklendiğini gösteren bir geri arama yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="fea42-103">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fea42-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="fea42-104">Methods</span></span>  
  
|<span data-ttu-id="fea42-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="fea42-105">Method</span></span>|<span data-ttu-id="fea42-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fea42-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fea42-107">CustomNotification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fea42-107">CustomNotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md)|<span data-ttu-id="fea42-108">Etkin bir özel hata ayıklayıcı bildiriminin yapıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fea42-108">Indicates that an enabled custom debugger notification has been raised.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fea42-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fea42-109">Remarks</span></span>  
 <span data-ttu-id="fea42-110">Bu arabirim, [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) ve [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) arabirimlerinin mantıksal bir uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="fea42-110">This interface is a logical extension of the [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) and [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fea42-111">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="fea42-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fea42-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fea42-112">Requirements</span></span>  
 <span data-ttu-id="fea42-113">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fea42-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fea42-114">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="fea42-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fea42-115">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="fea42-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fea42-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fea42-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fea42-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fea42-117">See also</span></span>

- [<span data-ttu-id="fea42-118">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fea42-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
- [<span data-ttu-id="fea42-119">ICorDebugManagedCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fea42-119">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="fea42-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="fea42-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="fea42-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="fea42-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

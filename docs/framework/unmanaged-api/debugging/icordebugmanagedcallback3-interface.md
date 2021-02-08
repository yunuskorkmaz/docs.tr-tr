---
description: 'Daha fazla bilgi edinin: ICorDebugManagedCallback3 Interface'
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
ms.openlocfilehash: 9fb3d44b1d793935ac997e8e4d8d86de4466f7b2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801195"
---
# <a name="icordebugmanagedcallback3-interface"></a><span data-ttu-id="99f5f-103">ICorDebugManagedCallback3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="99f5f-103">ICorDebugManagedCallback3 Interface</span></span>

<span data-ttu-id="99f5f-104">Etkinleştirilmiş bir özel hata ayıklayıcı bildiriminin tetiklendiğini gösteren bir geri arama yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="99f5f-104">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="99f5f-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="99f5f-105">Methods</span></span>  
  
|<span data-ttu-id="99f5f-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="99f5f-106">Method</span></span>|<span data-ttu-id="99f5f-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="99f5f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="99f5f-108">CustomNotification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="99f5f-108">CustomNotification Method</span></span>](icordebugmanagedcallback3-customnotification-method.md)|<span data-ttu-id="99f5f-109">Etkin bir özel hata ayıklayıcı bildiriminin yapıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="99f5f-109">Indicates that an enabled custom debugger notification has been raised.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99f5f-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="99f5f-110">Remarks</span></span>  

 <span data-ttu-id="99f5f-111">Bu arabirim, [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) ve [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) arabirimlerinin mantıksal bir uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="99f5f-111">This interface is a logical extension of the [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) and [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="99f5f-112">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="99f5f-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99f5f-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="99f5f-113">Requirements</span></span>  

 <span data-ttu-id="99f5f-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99f5f-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99f5f-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="99f5f-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="99f5f-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="99f5f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="99f5f-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99f5f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99f5f-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="99f5f-118">See also</span></span>

- [<span data-ttu-id="99f5f-119">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="99f5f-119">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
- [<span data-ttu-id="99f5f-120">ICorDebugManagedCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="99f5f-120">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="99f5f-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="99f5f-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="99f5f-122">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="99f5f-122">Debugging</span></span>](index.md)

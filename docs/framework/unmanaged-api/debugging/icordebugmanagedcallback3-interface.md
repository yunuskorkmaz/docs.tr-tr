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
ms.openlocfilehash: e04f5be6d2612b26bf7d71807753d170e6a5a7a0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723304"
---
# <a name="icordebugmanagedcallback3-interface"></a><span data-ttu-id="6afe8-102">ICorDebugManagedCallback3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6afe8-102">ICorDebugManagedCallback3 Interface</span></span>

<span data-ttu-id="6afe8-103">Etkinleştirilmiş bir özel hata ayıklayıcı bildiriminin tetiklendiğini gösteren bir geri arama yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6afe8-103">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6afe8-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6afe8-104">Methods</span></span>  
  
|<span data-ttu-id="6afe8-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="6afe8-105">Method</span></span>|<span data-ttu-id="6afe8-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6afe8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6afe8-107">CustomNotification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6afe8-107">CustomNotification Method</span></span>](icordebugmanagedcallback3-customnotification-method.md)|<span data-ttu-id="6afe8-108">Etkin bir özel hata ayıklayıcı bildiriminin yapıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6afe8-108">Indicates that an enabled custom debugger notification has been raised.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6afe8-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6afe8-109">Remarks</span></span>  

 <span data-ttu-id="6afe8-110">Bu arabirim, [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) ve [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) arabirimlerinin mantıksal bir uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="6afe8-110">This interface is a logical extension of the [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) and [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6afe8-111">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="6afe8-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6afe8-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6afe8-112">Requirements</span></span>  

 <span data-ttu-id="6afe8-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6afe8-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6afe8-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6afe8-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6afe8-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6afe8-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6afe8-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6afe8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6afe8-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6afe8-117">See also</span></span>

- [<span data-ttu-id="6afe8-118">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6afe8-118">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
- [<span data-ttu-id="6afe8-119">ICorDebugManagedCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6afe8-119">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="6afe8-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6afe8-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="6afe8-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="6afe8-121">Debugging</span></span>](index.md)

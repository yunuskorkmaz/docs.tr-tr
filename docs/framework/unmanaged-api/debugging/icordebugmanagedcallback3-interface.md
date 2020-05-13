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
ms.openlocfilehash: 63e3f166c4cbf17f4892dccf770343bfbf6e0284
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209753"
---
# <a name="icordebugmanagedcallback3-interface"></a><span data-ttu-id="b8493-102">ICorDebugManagedCallback3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b8493-102">ICorDebugManagedCallback3 Interface</span></span>
<span data-ttu-id="b8493-103">Etkinleştirilmiş bir özel hata ayıklayıcı bildiriminin tetiklendiğini gösteren bir geri arama yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8493-103">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b8493-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b8493-104">Methods</span></span>  
  
|<span data-ttu-id="b8493-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="b8493-105">Method</span></span>|<span data-ttu-id="b8493-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b8493-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b8493-107">CustomNotification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b8493-107">CustomNotification Method</span></span>](icordebugmanagedcallback3-customnotification-method.md)|<span data-ttu-id="b8493-108">Etkin bir özel hata ayıklayıcı bildiriminin yapıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b8493-108">Indicates that an enabled custom debugger notification has been raised.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8493-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b8493-109">Remarks</span></span>  
 <span data-ttu-id="b8493-110">Bu arabirim, [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) ve [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) arabirimlerinin mantıksal bir uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="b8493-110">This interface is a logical extension of the [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) and [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b8493-111">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="b8493-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8493-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b8493-112">Requirements</span></span>  
 <span data-ttu-id="b8493-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8493-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8493-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b8493-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b8493-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b8493-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b8493-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8493-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8493-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b8493-117">See also</span></span>

- [<span data-ttu-id="b8493-118">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b8493-118">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
- [<span data-ttu-id="b8493-119">ICorDebugManagedCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b8493-119">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="b8493-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b8493-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="b8493-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="b8493-121">Debugging</span></span>](index.md)

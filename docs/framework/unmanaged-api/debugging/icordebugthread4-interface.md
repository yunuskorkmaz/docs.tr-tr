---
title: ICorDebugThread4 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugThread4
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4
helpviewer_keywords:
- ICorDebugThread4 interface [.NET Framework debugging]
ms.assetid: a8c7719a-322b-4133-8566-4c27218dc104
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5d66a1aed1936d0146d42c8e4a5ad06dfa39c802
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962960"
---
# <a name="icordebugthread4-interface"></a><span data-ttu-id="cbaa3-102">ICorDebugThread4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cbaa3-102">ICorDebugThread4 Interface</span></span>
<span data-ttu-id="cbaa3-103">İş parçacığı engelleme bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="cbaa3-103">Provides thread blocking information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cbaa3-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="cbaa3-104">Methods</span></span>  
  
|<span data-ttu-id="cbaa3-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="cbaa3-105">Method</span></span>|<span data-ttu-id="cbaa3-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cbaa3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cbaa3-107">GetBlockingObjects Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cbaa3-107">GetBlockingObjects Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getblockingobjects-method.md)|<span data-ttu-id="cbaa3-108">İş parçacığı engelleme bilgileri sağlayan [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) yapılarının sıralı bir listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="cbaa3-108">Provides an ordered enumeration of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures that provide thread blocking information.</span></span>|  
|[<span data-ttu-id="cbaa3-109">HadUnhandledException Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cbaa3-109">HadUnhandledException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-hadunhandledexception-method.md)|<span data-ttu-id="cbaa3-110">İş parçacığının işlenmeyen bir özel duruma sahip olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="cbaa3-110">Indicates whether the thread has ever had an unhandled exception.</span></span>|  
|[<span data-ttu-id="cbaa3-111">GetCurrentCustomDebuggerNotification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cbaa3-111">GetCurrentCustomDebuggerNotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getcurrentcustomdebuggernotification-method.md)|<span data-ttu-id="cbaa3-112">Geçerli iş parçacığında geçerli [ICorDebugManagedCallback3:: CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) nesnesini alır.</span><span class="sxs-lookup"><span data-stu-id="cbaa3-112">Gets the current [ICorDebugManagedCallback3::CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) object on the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cbaa3-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cbaa3-113">Remarks</span></span>  
 <span data-ttu-id="cbaa3-114">Bu arabirim, ICorDebugThread, ICorDebugThread2 ve [ICorDebugThread3](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md) arabirimlerinin mantıksal uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="cbaa3-114">This interface is a logical extension of the ICorDebugThread, ICorDebugThread2, and [ICorDebugThread3](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md) interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cbaa3-115">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="cbaa3-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cbaa3-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cbaa3-116">Requirements</span></span>  
 <span data-ttu-id="cbaa3-117">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cbaa3-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cbaa3-118">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cbaa3-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cbaa3-119">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="cbaa3-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cbaa3-120">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cbaa3-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbaa3-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cbaa3-121">See also</span></span>

- [<span data-ttu-id="cbaa3-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="cbaa3-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="cbaa3-123">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="cbaa3-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

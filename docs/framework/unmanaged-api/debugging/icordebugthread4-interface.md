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
ms.openlocfilehash: f213a35a12bfb5cc92558a76e122a1494d567f93
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61987057"
---
# <a name="icordebugthread4-interface"></a><span data-ttu-id="50f62-102">ICorDebugThread4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="50f62-102">ICorDebugThread4 Interface</span></span>
<span data-ttu-id="50f62-103">İş parçacığı engelleme bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="50f62-103">Provides thread blocking information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="50f62-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="50f62-104">Methods</span></span>  
  
|<span data-ttu-id="50f62-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="50f62-105">Method</span></span>|<span data-ttu-id="50f62-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="50f62-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="50f62-107">GetBlockingObjects Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50f62-107">GetBlockingObjects Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getblockingobjects-method.md)|<span data-ttu-id="50f62-108">Sıralı sabit listesi sağlar [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) sağlayan yapıları iş parçacığı engelleme bilgileri.</span><span class="sxs-lookup"><span data-stu-id="50f62-108">Provides an ordered enumeration of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures that provide thread blocking information.</span></span>|  
|[<span data-ttu-id="50f62-109">HadUnhandledException Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50f62-109">HadUnhandledException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-hadunhandledexception-method.md)|<span data-ttu-id="50f62-110">İş parçacığı işlenmeyen bir özel durum sahipti olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="50f62-110">Indicates whether the thread has ever had an unhandled exception.</span></span>|  
|[<span data-ttu-id="50f62-111">GetCurrentCustomDebuggerNotification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50f62-111">GetCurrentCustomDebuggerNotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getcurrentcustomdebuggernotification-method.md)|<span data-ttu-id="50f62-112">Geçerli alır [Icordebugmanagedcallback3::customnotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) nesne geçerli iş parçacığı üzerinde.</span><span class="sxs-lookup"><span data-stu-id="50f62-112">Gets the current [ICorDebugManagedCallback3::CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) object on the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50f62-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="50f62-113">Remarks</span></span>  
 <span data-ttu-id="50f62-114">Bu arabirim Icordebugthread Icordebugthread2, mantıksal uzantısıdır ve [Icordebugthread3](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md) arabirimleri.</span><span class="sxs-lookup"><span data-stu-id="50f62-114">This interface is a logical extension of the ICorDebugThread, ICorDebugThread2, and [ICorDebugThread3](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md) interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="50f62-115">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="50f62-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50f62-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="50f62-116">Requirements</span></span>  
 <span data-ttu-id="50f62-117">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50f62-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50f62-118">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="50f62-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="50f62-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="50f62-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="50f62-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50f62-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50f62-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="50f62-121">See also</span></span>

- [<span data-ttu-id="50f62-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="50f62-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="50f62-123">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="50f62-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

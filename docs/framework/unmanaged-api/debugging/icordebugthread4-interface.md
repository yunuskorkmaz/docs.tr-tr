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
ms.openlocfilehash: cf486be306e149e2350e7239884c8f05b84f3a86
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422090"
---
# <a name="icordebugthread4-interface"></a><span data-ttu-id="d7f9f-102">ICorDebugThread4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d7f9f-102">ICorDebugThread4 Interface</span></span>
<span data-ttu-id="d7f9f-103">İş parçacığı engelleme bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-103">Provides thread blocking information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d7f9f-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d7f9f-104">Methods</span></span>  
  
|<span data-ttu-id="d7f9f-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d7f9f-105">Method</span></span>|<span data-ttu-id="d7f9f-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d7f9f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d7f9f-107">GetBlockingObjects Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d7f9f-107">GetBlockingObjects Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getblockingobjects-method.md)|<span data-ttu-id="d7f9f-108">Sıralanmış numaralandırması sağlar [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) sağlamak yapıları iş parçacığı engelleme bilgi.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-108">Provides an ordered enumeration of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures that provide thread blocking information.</span></span>|  
|[<span data-ttu-id="d7f9f-109">HadUnhandledException Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d7f9f-109">HadUnhandledException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-hadunhandledexception-method.md)|<span data-ttu-id="d7f9f-110">İş parçacığı işlenmeyen bir özel durum şimdiye kadar süredir sahip olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-110">Indicates whether the thread has ever had an unhandled exception.</span></span>|  
|[<span data-ttu-id="d7f9f-111">GetCurrentCustomDebuggerNotification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d7f9f-111">GetCurrentCustomDebuggerNotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getcurrentcustomdebuggernotification-method.md)|<span data-ttu-id="d7f9f-112">Geçerli alır [Icordebugmanagedcallback3::customnotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) nesne geçerli iş parçacığı üzerinde.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-112">Gets the current [ICorDebugManagedCallback3::CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) object on the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d7f9f-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d7f9f-113">Remarks</span></span>  
 <span data-ttu-id="d7f9f-114">Bu arabirim Icordebugthread2, Icordebugthread mantıksal uzantısıdır ve [Icordebugthread3](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md) arabirimleri.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-114">This interface is a logical extension of the ICorDebugThread, ICorDebugThread2, and [ICorDebugThread3](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md) interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d7f9f-115">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7f9f-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d7f9f-116">Requirements</span></span>  
 <span data-ttu-id="d7f9f-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7f9f-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7f9f-118">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d7f9f-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d7f9f-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d7f9f-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7f9f-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7f9f-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7f9f-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-121">See Also</span></span>  
 [<span data-ttu-id="d7f9f-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d7f9f-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="d7f9f-123">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="d7f9f-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

---
title: ICorDebugThread4 Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread4
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread4
helpviewer_keywords: ICorDebugThread4 interface [.NET Framework debugging]
ms.assetid: a8c7719a-322b-4133-8566-4c27218dc104
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e54611a38193a05a33381e798a61977d7aec41a6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugthread4-interface"></a><span data-ttu-id="45c64-102">ICorDebugThread4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="45c64-102">ICorDebugThread4 Interface</span></span>
<span data-ttu-id="45c64-103">İş parçacığı engelleme bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="45c64-103">Provides thread blocking information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="45c64-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="45c64-104">Methods</span></span>  
  
|<span data-ttu-id="45c64-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="45c64-105">Method</span></span>|<span data-ttu-id="45c64-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="45c64-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="45c64-107">GetBlockingObjects yöntemi</span><span class="sxs-lookup"><span data-stu-id="45c64-107">GetBlockingObjects Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getblockingobjects-method.md)|<span data-ttu-id="45c64-108">Sıralanmış numaralandırması sağlar [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) sağlamak yapıları iş parçacığı engelleme bilgi.</span><span class="sxs-lookup"><span data-stu-id="45c64-108">Provides an ordered enumeration of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures that provide thread blocking information.</span></span>|  
|[<span data-ttu-id="45c64-109">HadUnhandledException yöntemi</span><span class="sxs-lookup"><span data-stu-id="45c64-109">HadUnhandledException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-hadunhandledexception-method.md)|<span data-ttu-id="45c64-110">İş parçacığı işlenmeyen bir özel durum şimdiye kadar süredir sahip olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="45c64-110">Indicates whether the thread has ever had an unhandled exception.</span></span>|  
|[<span data-ttu-id="45c64-111">GetCurrentCustomDebuggerNotification yöntemi</span><span class="sxs-lookup"><span data-stu-id="45c64-111">GetCurrentCustomDebuggerNotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getcurrentcustomdebuggernotification-method.md)|<span data-ttu-id="45c64-112">Geçerli alır [Icordebugmanagedcallback3::customnotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) nesne geçerli iş parçacığı üzerinde.</span><span class="sxs-lookup"><span data-stu-id="45c64-112">Gets the current [ICorDebugManagedCallback3::CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) object on the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="45c64-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="45c64-113">Remarks</span></span>  
 <span data-ttu-id="45c64-114">Bu arabirim Icordebugthread2, Icordebugthread mantıksal uzantısıdır ve [Icordebugthread3](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md) arabirimleri.</span><span class="sxs-lookup"><span data-stu-id="45c64-114">This interface is a logical extension of the ICorDebugThread, ICorDebugThread2, and [ICorDebugThread3](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md) interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="45c64-115">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="45c64-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45c64-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="45c64-116">Requirements</span></span>  
 <span data-ttu-id="45c64-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45c64-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45c64-118">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="45c64-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="45c64-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="45c64-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="45c64-120">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45c64-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45c64-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="45c64-121">See Also</span></span>  
 [<span data-ttu-id="45c64-122">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="45c64-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="45c64-123">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="45c64-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

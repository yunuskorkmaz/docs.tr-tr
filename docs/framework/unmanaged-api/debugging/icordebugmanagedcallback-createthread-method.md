---
title: ICorDebugManagedCallback::CreateThread Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.CreateThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::CreateThread method
helpviewer_keywords:
- ICorDebugManagedCallback::CreateThread method [.NET Framework debugging]
- CreateThread method [.NET Framework debugging]
ms.assetid: 6b961728-21c4-4e8d-ae81-197458be62f4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c48e92c73347957d8acc5c209f6f5473e9e18524
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59223257"
---
# <a name="icordebugmanagedcallbackcreatethread-method"></a><span data-ttu-id="c2720-102">ICorDebugManagedCallback::CreateThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c2720-102">ICorDebugManagedCallback::CreateThread Method</span></span>
<span data-ttu-id="c2720-103">Hata ayıklayıcı, yönetilen bir kodu yürüten bir iş parçacığı başlatıldı bildirir.</span><span class="sxs-lookup"><span data-stu-id="c2720-103">Notifies the debugger that a thread has started executing managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2720-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c2720-104">Syntax</span></span>  
  
```  
HRESULT CreateThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2720-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c2720-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="c2720-106">[in] İş parçacığı içeren uygulama etki alanını temsil eden bir Icordebugappdomain nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="c2720-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the thread.</span></span>  
  
 `thread`  
 <span data-ttu-id="c2720-107">[in] İş parçacığını temsil eden bir Icordebugthread nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="c2720-107">[in] A pointer to an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c2720-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c2720-108">Remarks</span></span>  
 <span data-ttu-id="c2720-109">İş parçacığı yürütülecek ilk yönetilen kod yönerge yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="c2720-109">The thread will be positioned at the first managed code instruction to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2720-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c2720-110">Requirements</span></span>  
 <span data-ttu-id="c2720-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2720-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2720-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c2720-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c2720-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c2720-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="c2720-114">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="c2720-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c2720-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c2720-115">See also</span></span>

- [<span data-ttu-id="c2720-116">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c2720-116">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

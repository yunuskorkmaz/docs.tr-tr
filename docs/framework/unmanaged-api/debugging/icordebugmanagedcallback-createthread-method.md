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
ms.openlocfilehash: 2192b5d3b240211c8982eab7539896ea3626a072
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759673"
---
# <a name="icordebugmanagedcallbackcreatethread-method"></a><span data-ttu-id="11c43-102">ICorDebugManagedCallback::CreateThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="11c43-102">ICorDebugManagedCallback::CreateThread Method</span></span>
<span data-ttu-id="11c43-103">Hata ayıklayıcı, yönetilen bir kodu yürüten bir iş parçacığı başlatıldı bildirir.</span><span class="sxs-lookup"><span data-stu-id="11c43-103">Notifies the debugger that a thread has started executing managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11c43-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="11c43-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11c43-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="11c43-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="11c43-106">[in] İş parçacığı içeren uygulama etki alanını temsil eden bir Icordebugappdomain nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="11c43-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the thread.</span></span>  
  
 `thread`  
 <span data-ttu-id="11c43-107">[in] İş parçacığını temsil eden bir Icordebugthread nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="11c43-107">[in] A pointer to an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11c43-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="11c43-108">Remarks</span></span>  
 <span data-ttu-id="11c43-109">İş parçacığı yürütülecek ilk yönetilen kod yönerge yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="11c43-109">The thread will be positioned at the first managed code instruction to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11c43-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="11c43-110">Requirements</span></span>  
 <span data-ttu-id="11c43-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11c43-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11c43-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="11c43-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="11c43-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="11c43-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="11c43-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11c43-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11c43-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="11c43-115">See also</span></span>

- [<span data-ttu-id="11c43-116">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="11c43-116">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

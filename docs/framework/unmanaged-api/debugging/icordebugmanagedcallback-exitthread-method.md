---
title: ICorDebugManagedCallback::ExitThread Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ExitThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ExitThread
helpviewer_keywords:
- ExitThread method [.NET Framework debugging]
- ICorDebugManagedCallback::ExitThread method [.NET Framework debugging]
ms.assetid: 62db708b-6cf0-45c5-b897-4b5c75bd2505
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 85247f2f3672e7827f4dd0c93e50cd5da914ee8f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755769"
---
# <a name="icordebugmanagedcallbackexitthread-method"></a><span data-ttu-id="353cf-102">ICorDebugManagedCallback::ExitThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="353cf-102">ICorDebugManagedCallback::ExitThread Method</span></span>
<span data-ttu-id="353cf-103">Hata ayıklayıcı, yönetilen kod yürütülmekte olan bir iş parçacığı çıkıldı bildirir.</span><span class="sxs-lookup"><span data-stu-id="353cf-103">Notifies the debugger that a thread that was executing managed code has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="353cf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="353cf-104">Syntax</span></span>  
  
```cpp  
HRESULT ExitThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="353cf-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="353cf-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="353cf-106">[in] Yönetilen iş parçacığı içeren uygulama etki alanını temsil eden bir Icordebugappdomain nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="353cf-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread.</span></span>  
  
 `thread`  
 <span data-ttu-id="353cf-107">[in] Yönetilen iş parçacığını temsil eden bir Icordebugthread nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="353cf-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="353cf-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="353cf-108">Remarks</span></span>  
 <span data-ttu-id="353cf-109">Bir kez `ExitThread` geri çağırma tetiklenir, iş parçacığının iş parçacığı numaralandırmalardan görünmeyecek.</span><span class="sxs-lookup"><span data-stu-id="353cf-109">Once the `ExitThread` callback is fired, the thread will no longer appear in thread enumerations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="353cf-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="353cf-110">Requirements</span></span>  
 <span data-ttu-id="353cf-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="353cf-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="353cf-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="353cf-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="353cf-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="353cf-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="353cf-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="353cf-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="353cf-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="353cf-115">See also</span></span>

- [<span data-ttu-id="353cf-116">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="353cf-116">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

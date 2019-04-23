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
ms.openlocfilehash: 37815d8aead1ec89826c13db6f012f2cd17bc792
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59132450"
---
# <a name="icordebugmanagedcallbackexitthread-method"></a><span data-ttu-id="28ea9-102">ICorDebugManagedCallback::ExitThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="28ea9-102">ICorDebugManagedCallback::ExitThread Method</span></span>
<span data-ttu-id="28ea9-103">Hata ayıklayıcı, yönetilen kod yürütülmekte olan bir iş parçacığı çıkıldı bildirir.</span><span class="sxs-lookup"><span data-stu-id="28ea9-103">Notifies the debugger that a thread that was executing managed code has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28ea9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="28ea9-104">Syntax</span></span>  
  
```  
HRESULT ExitThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="28ea9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="28ea9-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="28ea9-106">[in] Yönetilen iş parçacığı içeren uygulama etki alanını temsil eden bir Icordebugappdomain nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="28ea9-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread.</span></span>  
  
 `thread`  
 <span data-ttu-id="28ea9-107">[in] Yönetilen iş parçacığını temsil eden bir Icordebugthread nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="28ea9-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="28ea9-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="28ea9-108">Remarks</span></span>  
 <span data-ttu-id="28ea9-109">Bir kez `ExitThread` geri çağırma tetiklenir, iş parçacığının iş parçacığı numaralandırmalardan görünmeyecek.</span><span class="sxs-lookup"><span data-stu-id="28ea9-109">Once the `ExitThread` callback is fired, the thread will no longer appear in thread enumerations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28ea9-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="28ea9-110">Requirements</span></span>  
 <span data-ttu-id="28ea9-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28ea9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28ea9-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="28ea9-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="28ea9-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="28ea9-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="28ea9-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28ea9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28ea9-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="28ea9-115">See also</span></span>

- [<span data-ttu-id="28ea9-116">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="28ea9-116">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

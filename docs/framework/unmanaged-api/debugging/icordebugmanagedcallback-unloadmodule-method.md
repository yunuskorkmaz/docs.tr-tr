---
title: ICorDebugManagedCallback::UnloadModule Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UnloadModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadModule
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadModule method [.NET Framework debugging]
- UnloadModule method [.NET Framework debugging]
ms.assetid: b12bfcd9-1e29-48bf-9a3d-44bfae5df5e8
topic_type:
- apiref
ms.openlocfilehash: 70aaf32b9da751b49571ab98a95e432b7f84caa9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130645"
---
# <a name="icordebugmanagedcallbackunloadmodule-method"></a><span data-ttu-id="a24e2-102">ICorDebugManagedCallback::UnloadModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a24e2-102">ICorDebugManagedCallback::UnloadModule Method</span></span>
<span data-ttu-id="a24e2-103">Hata ayıklayıcıya ortak dil çalışma zamanı modülü (DLL) kaldırılmış olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="a24e2-103">Notifies the debugger that a common language runtime module (DLL) has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a24e2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a24e2-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadModule (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugModule     *pModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a24e2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a24e2-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="a24e2-106">'ndaki Modülün bulunduğu uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a24e2-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the module.</span></span>  
  
 `pModule`  
 <span data-ttu-id="a24e2-107">'ndaki Modülünü temsil eden ICorDebugModule nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a24e2-107">[in] A pointer to an ICorDebugModule object that represents the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a24e2-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a24e2-108">Remarks</span></span>  
 <span data-ttu-id="a24e2-109">Modül Bu çağrıdan sonra kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="a24e2-109">The module should not be used after this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a24e2-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a24e2-110">Requirements</span></span>  
 <span data-ttu-id="a24e2-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a24e2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a24e2-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a24e2-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a24e2-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a24e2-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a24e2-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a24e2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a24e2-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a24e2-115">See also</span></span>

- [<span data-ttu-id="a24e2-116">LoadModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a24e2-116">LoadModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md)
- [<span data-ttu-id="a24e2-117">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a24e2-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

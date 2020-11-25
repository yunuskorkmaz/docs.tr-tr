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
ms.openlocfilehash: f24d49189ee81a80397b94ee4113c9514c083dbc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723993"
---
# <a name="icordebugmanagedcallbackunloadmodule-method"></a><span data-ttu-id="75e56-102">ICorDebugManagedCallback::UnloadModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="75e56-102">ICorDebugManagedCallback::UnloadModule Method</span></span>

<span data-ttu-id="75e56-103">Hata ayıklayıcıya ortak dil çalışma zamanı modülü (DLL) kaldırılmış olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="75e56-103">Notifies the debugger that a common language runtime module (DLL) has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75e56-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="75e56-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadModule (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugModule     *pModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="75e56-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="75e56-105">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="75e56-106">'ndaki Modülün bulunduğu uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="75e56-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the module.</span></span>  
  
 `pModule`  
 <span data-ttu-id="75e56-107">'ndaki Modülünü temsil eden ICorDebugModule nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="75e56-107">[in] A pointer to an ICorDebugModule object that represents the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="75e56-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="75e56-108">Remarks</span></span>  

 <span data-ttu-id="75e56-109">Modül Bu çağrıdan sonra kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="75e56-109">The module should not be used after this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75e56-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="75e56-110">Requirements</span></span>  

 <span data-ttu-id="75e56-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75e56-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75e56-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="75e56-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="75e56-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="75e56-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="75e56-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75e56-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75e56-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="75e56-115">See also</span></span>

- [<span data-ttu-id="75e56-116">LoadModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="75e56-116">LoadModule Method</span></span>](icordebugmanagedcallback-loadmodule-method.md)
- [<span data-ttu-id="75e56-117">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="75e56-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)

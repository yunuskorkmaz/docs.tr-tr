---
title: 'ICorDebugManagedCallback:: UnloadAssembly yöntemi'
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UnloadAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadAssembly
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadAssembly method [.NET Framework debugging]
- UnloadAssembly method [.NET Framework debugging]
ms.assetid: 6734321c-c8a9-401f-a558-cad715ec4a77
topic_type:
- apiref
ms.openlocfilehash: 4ae4856eca2c1441ea53df0d9ed3648700b39b24
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130652"
---
# <a name="icordebugmanagedcallbackunloadassembly-method"></a><span data-ttu-id="d8d14-102">ICorDebugManagedCallback:: UnloadAssembly yöntemi</span><span class="sxs-lookup"><span data-stu-id="d8d14-102">ICorDebugManagedCallback::UnloadAssembly Method</span></span>
<span data-ttu-id="d8d14-103">Hata ayıklayıcıyı ortak bir dil çalışma zamanı derlemesinin kaldırılmış olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="d8d14-103">Notifies the debugger that a common language runtime assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8d14-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d8d14-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadAssembly (  
    [in] IcorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugAssembly   *pAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8d14-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d8d14-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="d8d14-106">'ndaki Derlemeyi içeren uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d8d14-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the assembly.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="d8d14-107">'ndaki Derlemeyi temsil eden ICorDebugAssembly nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d8d14-107">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8d14-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d8d14-108">Remarks</span></span>  
 <span data-ttu-id="d8d14-109">Derleme bu geri aramadan sonra kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="d8d14-109">The assembly should not be used after this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8d14-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d8d14-110">Requirements</span></span>  
 <span data-ttu-id="d8d14-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8d14-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8d14-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d8d14-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d8d14-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d8d14-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8d14-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8d14-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8d14-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8d14-115">See also</span></span>

- [<span data-ttu-id="d8d14-116">LoadAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d8d14-116">LoadAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadassembly-method.md)
- [<span data-ttu-id="d8d14-117">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d8d14-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

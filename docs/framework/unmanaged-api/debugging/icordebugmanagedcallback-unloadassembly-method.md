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
ms.openlocfilehash: 06c08499298656c8314d72667d9dac88c8d11e6a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788349"
---
# <a name="icordebugmanagedcallbackunloadassembly-method"></a><span data-ttu-id="dce3e-102">ICorDebugManagedCallback:: UnloadAssembly yöntemi</span><span class="sxs-lookup"><span data-stu-id="dce3e-102">ICorDebugManagedCallback::UnloadAssembly Method</span></span>
<span data-ttu-id="dce3e-103">Hata ayıklayıcıyı ortak bir dil çalışma zamanı derlemesinin kaldırılmış olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="dce3e-103">Notifies the debugger that a common language runtime assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dce3e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dce3e-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadAssembly (  
    [in] IcorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugAssembly   *pAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dce3e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dce3e-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="dce3e-106">'ndaki Derlemeyi içeren uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="dce3e-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the assembly.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="dce3e-107">'ndaki Derlemeyi temsil eden ICorDebugAssembly nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="dce3e-107">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dce3e-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dce3e-108">Remarks</span></span>  
 <span data-ttu-id="dce3e-109">Derleme bu geri aramadan sonra kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="dce3e-109">The assembly should not be used after this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dce3e-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dce3e-110">Requirements</span></span>  
 <span data-ttu-id="dce3e-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dce3e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dce3e-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="dce3e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dce3e-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="dce3e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dce3e-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dce3e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dce3e-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dce3e-115">See also</span></span>

- [<span data-ttu-id="dce3e-116">LoadAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dce3e-116">LoadAssembly Method</span></span>](icordebugmanagedcallback-loadassembly-method.md)
- [<span data-ttu-id="dce3e-117">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dce3e-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)

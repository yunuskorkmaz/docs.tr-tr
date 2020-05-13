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
ms.openlocfilehash: 07996a78d7f559de587c8a3eb2babfc06675169d
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212652"
---
# <a name="icordebugmanagedcallbackunloadassembly-method"></a><span data-ttu-id="84256-102">ICorDebugManagedCallback:: UnloadAssembly yöntemi</span><span class="sxs-lookup"><span data-stu-id="84256-102">ICorDebugManagedCallback::UnloadAssembly Method</span></span>
<span data-ttu-id="84256-103">Hata ayıklayıcıyı ortak bir dil çalışma zamanı derlemesinin kaldırılmış olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="84256-103">Notifies the debugger that a common language runtime assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84256-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="84256-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadAssembly (  
    [in] IcorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugAssembly   *pAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="84256-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="84256-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="84256-106">'ndaki Derlemeyi içeren uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="84256-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the assembly.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="84256-107">'ndaki Derlemeyi temsil eden ICorDebugAssembly nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="84256-107">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="84256-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="84256-108">Remarks</span></span>  
 <span data-ttu-id="84256-109">Derleme bu geri aramadan sonra kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="84256-109">The assembly should not be used after this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84256-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="84256-110">Requirements</span></span>  
 <span data-ttu-id="84256-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84256-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84256-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="84256-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="84256-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="84256-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="84256-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84256-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84256-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="84256-115">See also</span></span>

- [<span data-ttu-id="84256-116">LoadAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="84256-116">LoadAssembly Method</span></span>](icordebugmanagedcallback-loadassembly-method.md)
- [<span data-ttu-id="84256-117">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="84256-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)

---
title: ICorDebugManagedCallback2::FunctionRemapComplete Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.FunctionRemapComplete
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::FunctionRemapComplete
helpviewer_keywords:
- FunctionRemapComplete method [.NET Framework debugging]
- ICorDebugManagedCallback2::FunctionRemapComplete method [.NET Framework debugging]
ms.assetid: 5396c4c3-4ec3-4e3a-a38d-d65b21f0a2fc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 515d434e8d8f1c99cf5052ef9a2f1e098f6021b2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59140562"
---
# <a name="icordebugmanagedcallback2functionremapcomplete-method"></a><span data-ttu-id="91118-102">ICorDebugManagedCallback2::FunctionRemapComplete Yöntemi</span><span class="sxs-lookup"><span data-stu-id="91118-102">ICorDebugManagedCallback2::FunctionRemapComplete Method</span></span>
<span data-ttu-id="91118-103">Hata ayıklayıcı, yürütmeyi düzenlenmiş bir işlevin yeni bir sürüme geçti bildirir.</span><span class="sxs-lookup"><span data-stu-id="91118-103">Notifies the debugger that code execution has switched to a new version of an edited function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91118-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="91118-104">Syntax</span></span>  
  
```  
HRESULT FunctionRemapComplete (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFunction    *pFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91118-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="91118-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="91118-106">[in] İşlev düzenlendi içeren uygulama etki alanını temsil eden bir Icordebugappdomain nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="91118-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the edited function.</span></span>  
  
 `pThread`  
 <span data-ttu-id="91118-107">[in] Kesme noktası eşleme tespit edildi iş parçacığını temsil eden bir Icordebugthread nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="91118-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the remap breakpoint was encountered.</span></span>  
  
 `pFunction`  
 <span data-ttu-id="91118-108">[in] İşlevi iş parçacığı üzerinde şu anda çalışan sürümünü temsil eden bir ICorDebugFunction nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="91118-108">[in] A pointer to an ICorDebugFunction object that represents the version of the function currently running on the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="91118-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="91118-109">Remarks</span></span>  
 <span data-ttu-id="91118-110">Bu geri çağırma, hata ayıklayıcı önceden var olan tüm adımlayıcıların yeniden oluşturmak için bir fırsat sağlar.</span><span class="sxs-lookup"><span data-stu-id="91118-110">This callback gives the debugger an opportunity to recreate any steppers that previously existed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91118-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="91118-111">Requirements</span></span>  
 <span data-ttu-id="91118-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91118-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91118-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="91118-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="91118-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="91118-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="91118-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91118-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91118-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="91118-116">See also</span></span>

- [<span data-ttu-id="91118-117">ICorDebugManagedCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="91118-117">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="91118-118">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="91118-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

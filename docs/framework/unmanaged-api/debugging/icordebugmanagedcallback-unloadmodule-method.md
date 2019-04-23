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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 12e42da015864e83663d2f4d74bab2a34052d760
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59083550"
---
# <a name="icordebugmanagedcallbackunloadmodule-method"></a><span data-ttu-id="6a84e-102">ICorDebugManagedCallback::UnloadModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6a84e-102">ICorDebugManagedCallback::UnloadModule Method</span></span>
<span data-ttu-id="6a84e-103">Hata ayıklayıcı Ortak Dil Çalışma Zamanı Modülü (DLL) kaldırıldı bildirir.</span><span class="sxs-lookup"><span data-stu-id="6a84e-103">Notifies the debugger that a common language runtime module (DLL) has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a84e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6a84e-104">Syntax</span></span>  
  
```  
HRESULT UnloadModule (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugModule     *pModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a84e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6a84e-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="6a84e-106">[in] Modül bulunan uygulama etki alanı temsil eden bir Icordebugappdomain nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="6a84e-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the module.</span></span>  
  
 `pModule`  
 <span data-ttu-id="6a84e-107">[in] Bir modülü temsil eden bir Icordebugmodule nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="6a84e-107">[in] A pointer to an ICorDebugModule object that represents the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6a84e-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6a84e-108">Remarks</span></span>  
 <span data-ttu-id="6a84e-109">Modül, bu çağrıdan sonra kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="6a84e-109">The module should not be used after this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a84e-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6a84e-110">Requirements</span></span>  
 <span data-ttu-id="6a84e-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a84e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a84e-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6a84e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6a84e-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6a84e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a84e-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a84e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a84e-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a84e-115">See also</span></span>

- [<span data-ttu-id="6a84e-116">LoadModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6a84e-116">LoadModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md)
- [<span data-ttu-id="6a84e-117">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6a84e-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

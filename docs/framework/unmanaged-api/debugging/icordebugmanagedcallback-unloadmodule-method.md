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
ms.openlocfilehash: ae4c1cb251f7786a8415449f16b4eb26d15a4fb2
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57491275"
---
# <a name="icordebugmanagedcallbackunloadmodule-method"></a><span data-ttu-id="3bb63-102">ICorDebugManagedCallback::UnloadModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3bb63-102">ICorDebugManagedCallback::UnloadModule Method</span></span>
<span data-ttu-id="3bb63-103">Hata ayıklayıcı Ortak Dil Çalışma Zamanı Modülü (DLL) kaldırıldı bildirir.</span><span class="sxs-lookup"><span data-stu-id="3bb63-103">Notifies the debugger that a common language runtime module (DLL) has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bb63-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3bb63-104">Syntax</span></span>  
  
```  
HRESULT UnloadModule (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugModule     *pModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3bb63-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3bb63-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="3bb63-106">[in] Modül bulunan uygulama etki alanı temsil eden bir Icordebugappdomain nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="3bb63-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the module.</span></span>  
  
 `pModule`  
 <span data-ttu-id="3bb63-107">[in] Bir modülü temsil eden bir Icordebugmodule nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="3bb63-107">[in] A pointer to an ICorDebugModule object that represents the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3bb63-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3bb63-108">Remarks</span></span>  
 <span data-ttu-id="3bb63-109">Modül, bu çağrıdan sonra kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="3bb63-109">The module should not be used after this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3bb63-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3bb63-110">Requirements</span></span>  
 <span data-ttu-id="3bb63-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3bb63-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3bb63-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3bb63-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3bb63-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3bb63-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3bb63-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3bb63-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bb63-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3bb63-115">See also</span></span>
- [<span data-ttu-id="3bb63-116">LoadModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3bb63-116">LoadModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md)
- [<span data-ttu-id="3bb63-117">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3bb63-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

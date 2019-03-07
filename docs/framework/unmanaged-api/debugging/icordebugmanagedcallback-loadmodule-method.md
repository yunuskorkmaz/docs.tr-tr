---
title: ICorDebugManagedCallback::LoadModule Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LoadModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadModule
helpviewer_keywords:
- ICorDebugManagedCallback::LoadModule method [.NET Framework debugging]
- LoadModule method [.NET Framework debugging]
ms.assetid: 66ec04e9-87cb-42ce-9720-81522abb5d5a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e49c20d7627f666efd6561cee19ca505f723b714
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474442"
---
# <a name="icordebugmanagedcallbackloadmodule-method"></a><span data-ttu-id="af110-102">ICorDebugManagedCallback::LoadModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="af110-102">ICorDebugManagedCallback::LoadModule Method</span></span>
<span data-ttu-id="af110-103">Hata ayıklayıcı, bir ortak dil çalışma zamanı (CLR) modülü başarıyla yüklenmemiş olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="af110-103">Notifies the debugger that a common language runtime (CLR) module has been successfully loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af110-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="af110-104">Syntax</span></span>  
  
```  
HRESULT LoadModule (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af110-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="af110-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="af110-106">[in] Modül yüklenmiş olan uygulama etki alanını temsil eden bir Icordebugappdomain nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="af110-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the module has been loaded.</span></span>  
  
 `pModule`  
 <span data-ttu-id="af110-107">[in] Bir CLR modülünü temsil eden bir Icordebugmodule nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="af110-107">[in] A pointer to an ICorDebugModule object that represents the CLR module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af110-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="af110-108">Remarks</span></span>  
 <span data-ttu-id="af110-109">`LoadModule` Geri çağırma modülü için meta verilerini incelemek, just-ın-time (JIT) derleyici bayraklarını ayarlayın veya etkinleştirme veya devre dışı geri çağırmaları modülü için yükleme sınıfı uygun bir zaman sağlar.</span><span class="sxs-lookup"><span data-stu-id="af110-109">The `LoadModule` callback provides an appropriate time to examine metadata for the module, set just-in-time (JIT) compiler flags, or enable or disable class loading callbacks for the module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af110-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="af110-110">Requirements</span></span>  
 <span data-ttu-id="af110-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af110-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af110-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="af110-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="af110-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="af110-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="af110-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af110-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af110-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af110-115">See also</span></span>
- [<span data-ttu-id="af110-116">UnloadModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="af110-116">UnloadModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadmodule-method.md)
- [<span data-ttu-id="af110-117">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="af110-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

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
ms.openlocfilehash: cbf538f066058b4f80d8cfd6cdf1a79683c79be9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413423"
---
# <a name="icordebugmanagedcallbackloadmodule-method"></a><span data-ttu-id="31eff-102">ICorDebugManagedCallback::LoadModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="31eff-102">ICorDebugManagedCallback::LoadModule Method</span></span>
<span data-ttu-id="31eff-103">Hata ayıklayıcı bir ortak dil çalışma zamanı (CLR) modülü başarıyla yüklendi bildirir.</span><span class="sxs-lookup"><span data-stu-id="31eff-103">Notifies the debugger that a common language runtime (CLR) module has been successfully loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31eff-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="31eff-104">Syntax</span></span>  
  
```  
HRESULT LoadModule (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="31eff-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="31eff-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="31eff-106">[in] Bir işaretçi Icordebugappdomain nesneye modülü yüklenmemiş olduğu uygulama etki alanını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="31eff-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the module has been loaded.</span></span>  
  
 `pModule`  
 <span data-ttu-id="31eff-107">[in] Bir işaretçi Icordebugmodule nesneye CLR modülü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="31eff-107">[in] A pointer to an ICorDebugModule object that represents the CLR module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31eff-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="31eff-108">Remarks</span></span>  
 <span data-ttu-id="31eff-109">`LoadModule` Geri çağırma modülü için meta verileri inceleyin, tam zamanında (JIT) derleyici bayraklarını ayarlayın veya etkinleştirebilir veya devre dışı geri aramalar modülü için yükleme sınıfı uygun bir saat sağlar.</span><span class="sxs-lookup"><span data-stu-id="31eff-109">The `LoadModule` callback provides an appropriate time to examine metadata for the module, set just-in-time (JIT) compiler flags, or enable or disable class loading callbacks for the module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31eff-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="31eff-110">Requirements</span></span>  
 <span data-ttu-id="31eff-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31eff-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31eff-112">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="31eff-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="31eff-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="31eff-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="31eff-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31eff-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31eff-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="31eff-115">See Also</span></span>  
 [<span data-ttu-id="31eff-116">UnloadModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="31eff-116">UnloadModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadmodule-method.md)  
 [<span data-ttu-id="31eff-117">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="31eff-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

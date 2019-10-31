---
title: ICorDebugModule::EnableClassLoadCallbacks Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugModule.EnableClassLoadCallbacks
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::EnableClassLoadCallbacks
helpviewer_keywords:
- ICorDebugModule::EnableClassLoadCallbacks method [.NET Framework debugging]
- EnableClassLoadCallbacks method [.NET Framework debugging]
ms.assetid: 78dad5e4-8e2e-400f-bec3-92ff0205cd82
topic_type:
- apiref
ms.openlocfilehash: c18ed781d44c873b4cd1957bf0102a4ce0cccad4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139214"
---
# <a name="icordebugmoduleenableclassloadcallbacks-method"></a><span data-ttu-id="3e2cc-102">ICorDebugModule::EnableClassLoadCallbacks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3e2cc-102">ICorDebugModule::EnableClassLoadCallbacks Method</span></span>
<span data-ttu-id="3e2cc-103">Bu modül için [ICorDebugManagedCallback:: LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) ve [ICorDebugManagedCallback:: UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) geri çağırmaları çağrılıp çağrılmayacağını denetler.</span><span class="sxs-lookup"><span data-stu-id="3e2cc-103">Controls whether the [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e2cc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3e2cc-104">Syntax</span></span>  
  
```cpp  
HRESULT EnableClassLoadCallbacks(  
    [in] BOOL bClassLoadCallbacks  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e2cc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3e2cc-105">Parameters</span></span>  
 `bClassLoadCallbacks`  
 <span data-ttu-id="3e2cc-106">'ndaki Ortak dil çalışma zamanını (CLR), ilişkili olayları gerçekleştiğinde `ICorDebugManagedCallback::LoadClass` ve `ICorDebugManagedCallback::UnloadClass` yöntemlerini çağırmak üzere etkinleştirmek için bu değeri `true` olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="3e2cc-106">[in] Set this value to `true` to enable the common language runtime (CLR) to call the `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` methods when their associated events occur.</span></span>  
  
 <span data-ttu-id="3e2cc-107">Dinamik olmayan modüller için varsayılan değer `false`.</span><span class="sxs-lookup"><span data-stu-id="3e2cc-107">The default value is `false` for non-dynamic modules.</span></span> <span data-ttu-id="3e2cc-108">Değer her zaman dinamik modüller için `true` ve değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="3e2cc-108">The value is always `true` for dynamic modules and cannot be changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3e2cc-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3e2cc-109">Remarks</span></span>  
 <span data-ttu-id="3e2cc-110">`ICorDebugManagedCallback::LoadClass` ve `ICorDebugManagedCallback::UnloadClass` geri çağırmaları her zaman dinamik modüller için etkinleştirilmiştir ve devre dışı bırakılamaz.</span><span class="sxs-lookup"><span data-stu-id="3e2cc-110">The `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` callbacks are always enabled for dynamic modules and cannot be disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e2cc-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3e2cc-111">Requirements</span></span>  
 <span data-ttu-id="3e2cc-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e2cc-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e2cc-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3e2cc-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3e2cc-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3e2cc-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3e2cc-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e2cc-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e2cc-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3e2cc-116">See also</span></span>

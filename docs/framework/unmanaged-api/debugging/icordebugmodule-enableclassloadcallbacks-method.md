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
ms.openlocfilehash: 1f6c6ae3b7cb45b049d0fb0d88bbf89121bccfd7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95710421"
---
# <a name="icordebugmoduleenableclassloadcallbacks-method"></a><span data-ttu-id="855da-102">ICorDebugModule::EnableClassLoadCallbacks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="855da-102">ICorDebugModule::EnableClassLoadCallbacks Method</span></span>

<span data-ttu-id="855da-103">Bu modül için [ICorDebugManagedCallback:: LoadClass](icordebugmanagedcallback-loadclass-method.md) ve [ICorDebugManagedCallback:: UnloadClass](icordebugmanagedcallback-unloadclass-method.md) geri çağırmaları çağrılıp çağrılmayacağını denetler.</span><span class="sxs-lookup"><span data-stu-id="855da-103">Controls whether the [ICorDebugManagedCallback::LoadClass](icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="855da-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="855da-104">Syntax</span></span>  
  
```cpp  
HRESULT EnableClassLoadCallbacks(  
    [in] BOOL bClassLoadCallbacks  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="855da-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="855da-105">Parameters</span></span>  

 `bClassLoadCallbacks`  
 <span data-ttu-id="855da-106">'ndaki `true` Ortak dil çalışma zamanını (CLR), `ICorDebugManagedCallback::LoadClass` ilişkili olayları gerçekleştiğinde ve yöntemlerini çağırmak üzere etkinleştirmek için bu değeri olarak ayarlayın `ICorDebugManagedCallback::UnloadClass` .</span><span class="sxs-lookup"><span data-stu-id="855da-106">[in] Set this value to `true` to enable the common language runtime (CLR) to call the `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` methods when their associated events occur.</span></span>  
  
 <span data-ttu-id="855da-107">Varsayılan değer, `false` dinamik olmayan modüller içindir.</span><span class="sxs-lookup"><span data-stu-id="855da-107">The default value is `false` for non-dynamic modules.</span></span> <span data-ttu-id="855da-108">Değer her zaman `true` Dinamik modüller için ve değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="855da-108">The value is always `true` for dynamic modules and cannot be changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="855da-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="855da-109">Remarks</span></span>  

 <span data-ttu-id="855da-110">`ICorDebugManagedCallback::LoadClass`Ve `ICorDebugManagedCallback::UnloadClass` geri çağırmaları her zaman dinamik modüller için etkindir ve devre dışı bırakılamaz.</span><span class="sxs-lookup"><span data-stu-id="855da-110">The `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` callbacks are always enabled for dynamic modules and cannot be disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="855da-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="855da-111">Requirements</span></span>  

 <span data-ttu-id="855da-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="855da-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="855da-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="855da-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="855da-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="855da-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="855da-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="855da-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="855da-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="855da-116">See also</span></span>

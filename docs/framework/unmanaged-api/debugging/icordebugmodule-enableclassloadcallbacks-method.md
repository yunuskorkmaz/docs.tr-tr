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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 22a838748414f9d89cdc7ff469f7f5cc5e11b9d4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796896"
---
# <a name="icordebugmoduleenableclassloadcallbacks-method"></a><span data-ttu-id="c1a96-102">ICorDebugModule::EnableClassLoadCallbacks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c1a96-102">ICorDebugModule::EnableClassLoadCallbacks Method</span></span>
<span data-ttu-id="c1a96-103">Denetimleri olmadığını [Icordebugmanagedcallback::loadclass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) ve [Icordebugmanagedcallback::unloadclass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) geri çağırmaları bu modül için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="c1a96-103">Controls whether the [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1a96-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c1a96-104">Syntax</span></span>  
  
```  
HRESULT EnableClassLoadCallbacks(  
    [in] BOOL bClassLoadCallbacks  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1a96-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c1a96-105">Parameters</span></span>  
 `bClassLoadCallbacks`  
 <span data-ttu-id="c1a96-106">[in] Bu değer kümesine `true` ortak dil çalışma zamanı (CLR) çağrılacak etkinleştirmek için `ICorDebugManagedCallback::LoadClass` ve `ICorDebugManagedCallback::UnloadClass` kendi ilişkili olaylar meydana geldiğinde yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="c1a96-106">[in] Set this value to `true` to enable the common language runtime (CLR) to call the `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` methods when their associated events occur.</span></span>  
  
 <span data-ttu-id="c1a96-107">Varsayılan değer `false` dinamik olmayan modüller için.</span><span class="sxs-lookup"><span data-stu-id="c1a96-107">The default value is `false` for non-dynamic modules.</span></span> <span data-ttu-id="c1a96-108">Her zaman `true` dinamik modüller için ve değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="c1a96-108">The value is always `true` for dynamic modules and cannot be changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c1a96-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c1a96-109">Remarks</span></span>  
 <span data-ttu-id="c1a96-110">`ICorDebugManagedCallback::LoadClass` Ve `ICorDebugManagedCallback::UnloadClass` geri çağırmaları dinamik modüller için her zaman etkin ve devre dışı bırakılamaz.</span><span class="sxs-lookup"><span data-stu-id="c1a96-110">The `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` callbacks are always enabled for dynamic modules and cannot be disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1a96-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c1a96-111">Requirements</span></span>  
 <span data-ttu-id="c1a96-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1a96-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1a96-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c1a96-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c1a96-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c1a96-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c1a96-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1a96-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1a96-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c1a96-116">See also</span></span>

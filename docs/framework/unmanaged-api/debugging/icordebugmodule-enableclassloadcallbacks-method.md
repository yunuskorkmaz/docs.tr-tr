---
title: "ICorDebugModule::EnableClassLoadCallbacks Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule.EnableClassLoadCallbacks
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule::EnableClassLoadCallbacks
helpviewer_keywords:
- ICorDebugModule::EnableClassLoadCallbacks method [.NET Framework debugging]
- EnableClassLoadCallbacks method [.NET Framework debugging]
ms.assetid: 78dad5e4-8e2e-400f-bec3-92ff0205cd82
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5aa4add6dcaf662f1b5ec48b1243f012a6ae1f1c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmoduleenableclassloadcallbacks-method"></a><span data-ttu-id="145f0-102">ICorDebugModule::EnableClassLoadCallbacks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="145f0-102">ICorDebugModule::EnableClassLoadCallbacks Method</span></span>
<span data-ttu-id="145f0-103">Denetimleri olup olmadığını [Icordebugmanagedcallback::loadclass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) ve [Icordebugmanagedcallback::unloadclass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) geri aramalar, bu modül için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="145f0-103">Controls whether the [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="145f0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="145f0-104">Syntax</span></span>  
  
```  
HRESULT EnableClassLoadCallbacks(  
    [in] BOOL bClassLoadCallbacks  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="145f0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="145f0-105">Parameters</span></span>  
 `bClassLoadCallbacks`  
 <span data-ttu-id="145f0-106">[in] Bu değer ayarlanırsa `true` ortak dil çalışma zamanı (CLR) çağırmak için etkinleştirmek için `ICorDebugManagedCallback::LoadClass` ve `ICorDebugManagedCallback::UnloadClass` bunların ilişkili olaylar meydana geldiğinde yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="145f0-106">[in] Set this value to `true` to enable the common language runtime (CLR) to call the `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` methods when their associated events occur.</span></span>  
  
 <span data-ttu-id="145f0-107">Varsayılan değer `false` dinamik olmayan modüller.</span><span class="sxs-lookup"><span data-stu-id="145f0-107">The default value is `false` for non-dynamic modules.</span></span> <span data-ttu-id="145f0-108">Her zaman değerdir `true` dinamik modüller ve değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="145f0-108">The value is always `true` for dynamic modules and cannot be changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="145f0-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="145f0-109">Remarks</span></span>  
 <span data-ttu-id="145f0-110">`ICorDebugManagedCallback::LoadClass` Ve `ICorDebugManagedCallback::UnloadClass` geri aramalar dinamik modülleri için her zaman etkin ve devre dışı bırakılamaz.</span><span class="sxs-lookup"><span data-stu-id="145f0-110">The `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` callbacks are always enabled for dynamic modules and cannot be disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="145f0-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="145f0-111">Requirements</span></span>  
 <span data-ttu-id="145f0-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="145f0-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="145f0-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="145f0-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="145f0-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="145f0-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="145f0-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="145f0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="145f0-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="145f0-116">See Also</span></span>  
    
 

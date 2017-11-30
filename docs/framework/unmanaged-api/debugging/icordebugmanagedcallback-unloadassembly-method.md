---
title: "ICorDebugManagedCallback::UnloadAssembly Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.UnloadAssembly
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::UnloadAssembly
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadAssembly method [.NET Framework debugging]
- UnloadAssembly method [.NET Framework debugging]
ms.assetid: 6734321c-c8a9-401f-a558-cad715ec4a77
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 29400e5bda2a17c731cb33e67c0123cffc89c48b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmanagedcallbackunloadassembly-method"></a><span data-ttu-id="cdb9d-102">ICorDebugManagedCallback::UnloadAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cdb9d-102">ICorDebugManagedCallback::UnloadAssembly Method</span></span>
<span data-ttu-id="cdb9d-103">Hata ayıklayıcı bir ortak dil çalışma zamanı derlemesi kaldırıldı bildirir.</span><span class="sxs-lookup"><span data-stu-id="cdb9d-103">Notifies the debugger that a common language runtime assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdb9d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cdb9d-104">Syntax</span></span>  
  
```  
HRESULT UnloadAssembly (  
    [in] IcorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugAssembly   *pAssembly  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cdb9d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cdb9d-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="cdb9d-106">[in] Bir işaretçi Icordebugappdomain nesneye derleme bulunan uygulama etki alanını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="cdb9d-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the assembly.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="cdb9d-107">[in] Bir işaretçi Icordebugassembly nesneye derleme temsil eder.</span><span class="sxs-lookup"><span data-stu-id="cdb9d-107">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cdb9d-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cdb9d-108">Remarks</span></span>  
 <span data-ttu-id="cdb9d-109">Derleme, bu geri çağırma sonra kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="cdb9d-109">The assembly should not be used after this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cdb9d-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cdb9d-110">Requirements</span></span>  
 <span data-ttu-id="cdb9d-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cdb9d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cdb9d-112">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cdb9d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cdb9d-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cdb9d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cdb9d-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cdb9d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdb9d-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cdb9d-115">See Also</span></span>  
 [<span data-ttu-id="cdb9d-116">LoadAssembly yöntemi</span><span class="sxs-lookup"><span data-stu-id="cdb9d-116">LoadAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadassembly-method.md)  
 [<span data-ttu-id="cdb9d-117">Icordebugmanagedcallback arabirimi</span><span class="sxs-lookup"><span data-stu-id="cdb9d-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

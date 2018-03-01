---
title: "ICorDebugManagedCallback::UnloadAssembly Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugManagedCallback.UnloadAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadAssembly
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadAssembly method [.NET Framework debugging]
- UnloadAssembly method [.NET Framework debugging]
ms.assetid: 6734321c-c8a9-401f-a558-cad715ec4a77
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 731615729f680bae4c4b8517de4a3e522d4acae2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbackunloadassembly-method"></a><span data-ttu-id="51db0-102">ICorDebugManagedCallback::UnloadAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="51db0-102">ICorDebugManagedCallback::UnloadAssembly Method</span></span>
<span data-ttu-id="51db0-103">Hata ayıklayıcı bir ortak dil çalışma zamanı derlemesi kaldırıldı bildirir.</span><span class="sxs-lookup"><span data-stu-id="51db0-103">Notifies the debugger that a common language runtime assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51db0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="51db0-104">Syntax</span></span>  
  
```  
HRESULT UnloadAssembly (  
    [in] IcorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugAssembly   *pAssembly  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="51db0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="51db0-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="51db0-106">[in] Bir işaretçi Icordebugappdomain nesneye derleme bulunan uygulama etki alanını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="51db0-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the assembly.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="51db0-107">[in] Bir işaretçi Icordebugassembly nesneye derleme temsil eder.</span><span class="sxs-lookup"><span data-stu-id="51db0-107">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="51db0-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="51db0-108">Remarks</span></span>  
 <span data-ttu-id="51db0-109">Derleme, bu geri çağırma sonra kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="51db0-109">The assembly should not be used after this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51db0-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="51db0-110">Requirements</span></span>  
 <span data-ttu-id="51db0-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51db0-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51db0-112">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="51db0-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="51db0-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="51db0-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="51db0-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51db0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51db0-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="51db0-115">See Also</span></span>  
 [<span data-ttu-id="51db0-116">LoadAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="51db0-116">LoadAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadassembly-method.md)  
 [<span data-ttu-id="51db0-117">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="51db0-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

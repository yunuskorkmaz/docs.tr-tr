---
title: ICorDebugManagedCallback::UnloadAssembly Yöntemi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 93d44006dd6652a8d34c23209eb957b23064f976
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54704010"
---
# <a name="icordebugmanagedcallbackunloadassembly-method"></a><span data-ttu-id="1c776-102">ICorDebugManagedCallback::UnloadAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1c776-102">ICorDebugManagedCallback::UnloadAssembly Method</span></span>
<span data-ttu-id="1c776-103">Hata ayıklayıcı, bir ortak dil çalışma zamanı derlemesi kaldırıldı bildirir.</span><span class="sxs-lookup"><span data-stu-id="1c776-103">Notifies the debugger that a common language runtime assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c776-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1c776-104">Syntax</span></span>  
  
```  
HRESULT UnloadAssembly (  
    [in] IcorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugAssembly   *pAssembly  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1c776-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1c776-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="1c776-106">[in] Bütünleştirilmiş kod içeren uygulama etki alanı temsil eden bir Icordebugappdomain nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="1c776-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the assembly.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="1c776-107">[in] Bir işaretçi Icordebugassembly nesneye bütünleştirilmiş kodu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1c776-107">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1c776-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1c776-108">Remarks</span></span>  
 <span data-ttu-id="1c776-109">Derleme, bu geri çağırma sonra kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="1c776-109">The assembly should not be used after this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c776-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1c776-110">Requirements</span></span>  
 <span data-ttu-id="1c776-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c776-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c776-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1c776-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1c776-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1c776-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c776-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c776-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c776-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c776-115">See also</span></span>
- [<span data-ttu-id="1c776-116">LoadAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1c776-116">LoadAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadassembly-method.md)
- [<span data-ttu-id="1c776-117">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1c776-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

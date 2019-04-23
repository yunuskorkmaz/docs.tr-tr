---
title: ICorDebugManagedCallback::LoadAssembly Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LoadAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadAssembly
helpviewer_keywords:
- LoadAssembly method [.NET Framework debugging]
- ICorDebugManagedCallback::LoadAssembly method [.NET Framework debugging]
ms.assetid: 55cb673a-e240-43a6-a406-6912e7c0fe66
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5760287e01257e3f0fc99a18ba20f2f2a1b2b3af
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59083367"
---
# <a name="icordebugmanagedcallbackloadassembly-method"></a><span data-ttu-id="1f733-102">ICorDebugManagedCallback::LoadAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1f733-102">ICorDebugManagedCallback::LoadAssembly Method</span></span>
<span data-ttu-id="1f733-103">Hata ayıklayıcı, bir ortak dil çalışma zamanı (CLR) derlemesi başarıyla yüklenmiş olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="1f733-103">Notifies the debugger that a common language runtime (CLR) assembly has been successfully loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f733-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1f733-104">Syntax</span></span>  
  
```  
HRESULT LoadAssembly (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugAssembly  *pAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f733-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1f733-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="1f733-106">[in] Hangi derleme yüklendi uygulama etki alanını temsil eden bir Icordebugappdomain nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="1f733-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the assembly has been loaded.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="1f733-107">[in] Bir işaretçi Icordebugassembly nesneye bütünleştirilmiş kodu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1f733-107">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f733-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1f733-108">Requirements</span></span>  
 <span data-ttu-id="1f733-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f733-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f733-110">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1f733-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1f733-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1f733-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1f733-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f733-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f733-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f733-113">See also</span></span>

- [<span data-ttu-id="1f733-114">UnloadAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1f733-114">UnloadAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadassembly-method.md)
- [<span data-ttu-id="1f733-115">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1f733-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

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
ms.openlocfilehash: c6d77ff1393bc0ba4884dfa34810fee5316e33ef
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130742"
---
# <a name="icordebugmanagedcallbackloadassembly-method"></a><span data-ttu-id="4882c-102">ICorDebugManagedCallback::LoadAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4882c-102">ICorDebugManagedCallback::LoadAssembly Method</span></span>
<span data-ttu-id="4882c-103">Bir ortak dil çalışma zamanı (CLR) derlemesinin başarıyla yüklendiğini hata ayıklayıcıya bildirir.</span><span class="sxs-lookup"><span data-stu-id="4882c-103">Notifies the debugger that a common language runtime (CLR) assembly has been successfully loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4882c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4882c-104">Syntax</span></span>  
  
```cpp  
HRESULT LoadAssembly (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugAssembly  *pAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4882c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4882c-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="4882c-106">'ndaki Derlemenin yüklendiği uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4882c-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the assembly has been loaded.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="4882c-107">'ndaki Derlemeyi temsil eden ICorDebugAssembly nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4882c-107">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4882c-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4882c-108">Requirements</span></span>  
 <span data-ttu-id="4882c-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4882c-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4882c-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4882c-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4882c-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="4882c-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4882c-112">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4882c-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4882c-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4882c-113">See also</span></span>

- [<span data-ttu-id="4882c-114">UnloadAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4882c-114">UnloadAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadassembly-method.md)
- [<span data-ttu-id="4882c-115">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4882c-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

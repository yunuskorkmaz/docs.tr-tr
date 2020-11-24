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
ms.openlocfilehash: 243a1661ce2910cf1713ef8884bb6ae5422e8013
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679695"
---
# <a name="icordebugmanagedcallbackloadassembly-method"></a><span data-ttu-id="611aa-102">ICorDebugManagedCallback::LoadAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="611aa-102">ICorDebugManagedCallback::LoadAssembly Method</span></span>

<span data-ttu-id="611aa-103">Bir ortak dil çalışma zamanı (CLR) derlemesinin başarıyla yüklendiğini hata ayıklayıcıya bildirir.</span><span class="sxs-lookup"><span data-stu-id="611aa-103">Notifies the debugger that a common language runtime (CLR) assembly has been successfully loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="611aa-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="611aa-104">Syntax</span></span>  
  
```cpp  
HRESULT LoadAssembly (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugAssembly  *pAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="611aa-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="611aa-105">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="611aa-106">'ndaki Derlemenin yüklendiği uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="611aa-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the assembly has been loaded.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="611aa-107">'ndaki Derlemeyi temsil eden ICorDebugAssembly nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="611aa-107">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="611aa-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="611aa-108">Requirements</span></span>  

 <span data-ttu-id="611aa-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="611aa-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="611aa-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="611aa-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="611aa-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="611aa-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="611aa-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="611aa-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="611aa-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="611aa-113">See also</span></span>

- [<span data-ttu-id="611aa-114">UnloadAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="611aa-114">UnloadAssembly Method</span></span>](icordebugmanagedcallback-unloadassembly-method.md)
- [<span data-ttu-id="611aa-115">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="611aa-115">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)

---
description: ': ICorDebugManagedCallback:: LoadAssembly yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: b90391f3c6286323db11dadae841db38f9b785a7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722808"
---
# <a name="icordebugmanagedcallbackloadassembly-method"></a><span data-ttu-id="8183f-103">ICorDebugManagedCallback::LoadAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8183f-103">ICorDebugManagedCallback::LoadAssembly Method</span></span>

<span data-ttu-id="8183f-104">Bir ortak dil çalışma zamanı (CLR) derlemesinin başarıyla yüklendiğini hata ayıklayıcıya bildirir.</span><span class="sxs-lookup"><span data-stu-id="8183f-104">Notifies the debugger that a common language runtime (CLR) assembly has been successfully loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8183f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8183f-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadAssembly (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugAssembly  *pAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8183f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8183f-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="8183f-107">'ndaki Derlemenin yüklendiği uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8183f-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the assembly has been loaded.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="8183f-108">'ndaki Derlemeyi temsil eden ICorDebugAssembly nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8183f-108">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8183f-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8183f-109">Requirements</span></span>  

 <span data-ttu-id="8183f-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8183f-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8183f-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8183f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8183f-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="8183f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8183f-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8183f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8183f-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8183f-114">See also</span></span>

- [<span data-ttu-id="8183f-115">UnloadAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8183f-115">UnloadAssembly Method</span></span>](icordebugmanagedcallback-unloadassembly-method.md)
- [<span data-ttu-id="8183f-116">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8183f-116">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)

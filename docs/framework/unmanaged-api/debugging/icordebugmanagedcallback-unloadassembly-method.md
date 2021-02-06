---
description: ': ICorDebugManagedCallback:: UnloadAssembly yöntemi hakkında daha fazla bilgi edinin'
title: 'ICorDebugManagedCallback:: UnloadAssembly yöntemi'
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
ms.openlocfilehash: b1860e90ba2bab1428a0f8559d18801136bbbb39
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660342"
---
# <a name="icordebugmanagedcallbackunloadassembly-method"></a><span data-ttu-id="1e0d8-103">ICorDebugManagedCallback:: UnloadAssembly yöntemi</span><span class="sxs-lookup"><span data-stu-id="1e0d8-103">ICorDebugManagedCallback::UnloadAssembly Method</span></span>

<span data-ttu-id="1e0d8-104">Hata ayıklayıcıyı ortak bir dil çalışma zamanı derlemesinin kaldırılmış olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="1e0d8-104">Notifies the debugger that a common language runtime assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e0d8-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1e0d8-105">Syntax</span></span>  
  
```cpp  
HRESULT UnloadAssembly (  
    [in] IcorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugAssembly   *pAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1e0d8-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1e0d8-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="1e0d8-107">'ndaki Derlemeyi içeren uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1e0d8-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the assembly.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="1e0d8-108">'ndaki Derlemeyi temsil eden ICorDebugAssembly nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1e0d8-108">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1e0d8-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1e0d8-109">Remarks</span></span>  

 <span data-ttu-id="1e0d8-110">Derleme bu geri aramadan sonra kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="1e0d8-110">The assembly should not be used after this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e0d8-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1e0d8-111">Requirements</span></span>  

 <span data-ttu-id="1e0d8-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e0d8-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e0d8-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1e0d8-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1e0d8-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1e0d8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1e0d8-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e0d8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e0d8-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1e0d8-116">See also</span></span>

- [<span data-ttu-id="1e0d8-117">LoadAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1e0d8-117">LoadAssembly Method</span></span>](icordebugmanagedcallback-loadassembly-method.md)
- [<span data-ttu-id="1e0d8-118">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1e0d8-118">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)

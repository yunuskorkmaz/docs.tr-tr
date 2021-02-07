---
description: ': ICorDebugManagedCallback:: UnloadModule yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugManagedCallback::UnloadModule Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UnloadModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadModule
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadModule method [.NET Framework debugging]
- UnloadModule method [.NET Framework debugging]
ms.assetid: b12bfcd9-1e29-48bf-9a3d-44bfae5df5e8
topic_type:
- apiref
ms.openlocfilehash: d8d37b28d7a7d11000c259f1bcde3138634b2498
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754062"
---
# <a name="icordebugmanagedcallbackunloadmodule-method"></a><span data-ttu-id="ac367-103">ICorDebugManagedCallback::UnloadModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ac367-103">ICorDebugManagedCallback::UnloadModule Method</span></span>

<span data-ttu-id="ac367-104">Hata ayıklayıcıya ortak dil çalışma zamanı modülü (DLL) kaldırılmış olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="ac367-104">Notifies the debugger that a common language runtime module (DLL) has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac367-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ac367-105">Syntax</span></span>  
  
```cpp  
HRESULT UnloadModule (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugModule     *pModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac367-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ac367-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="ac367-107">'ndaki Modülün bulunduğu uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ac367-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the module.</span></span>  
  
 `pModule`  
 <span data-ttu-id="ac367-108">'ndaki Modülünü temsil eden ICorDebugModule nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ac367-108">[in] A pointer to an ICorDebugModule object that represents the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ac367-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ac367-109">Remarks</span></span>  

 <span data-ttu-id="ac367-110">Modül Bu çağrıdan sonra kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="ac367-110">The module should not be used after this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac367-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ac367-111">Requirements</span></span>  

 <span data-ttu-id="ac367-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac367-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac367-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ac367-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ac367-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ac367-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ac367-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac367-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac367-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac367-116">See also</span></span>

- [<span data-ttu-id="ac367-117">LoadModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ac367-117">LoadModule Method</span></span>](icordebugmanagedcallback-loadmodule-method.md)
- [<span data-ttu-id="ac367-118">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ac367-118">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)

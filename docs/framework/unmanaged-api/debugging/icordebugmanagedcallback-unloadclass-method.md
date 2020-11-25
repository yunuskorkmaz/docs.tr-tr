---
title: ICorDebugManagedCallback::UnloadClass Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UnloadClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadClass
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadClass method [.NET Framework debugging]
- UnloadClass method [.NET Framework debugging]
ms.assetid: 66a59b18-ce9a-41f4-b23b-4dd6753d6d36
topic_type:
- apiref
ms.openlocfilehash: 6efd451c6895e8fef443e2e86afa6e98279c6493
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724006"
---
# <a name="icordebugmanagedcallbackunloadclass-method"></a><span data-ttu-id="d7c3a-102">ICorDebugManagedCallback::UnloadClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d7c3a-102">ICorDebugManagedCallback::UnloadClass Method</span></span>

<span data-ttu-id="d7c3a-103">Hata ayıklayıcıya bir sınıfın bellekten kaldırılmakta olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="d7c3a-103">Notifies the debugger that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7c3a-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="d7c3a-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadClass (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugClass      *c  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7c3a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d7c3a-105">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="d7c3a-106">'ndaki Sınıfını içeren uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d7c3a-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the class.</span></span>  
  
 `c`  
 <span data-ttu-id="d7c3a-107">'ndaki Sınıfını temsil eden ICorDebugClass nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d7c3a-107">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d7c3a-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d7c3a-108">Remarks</span></span>  

 <span data-ttu-id="d7c3a-109">Bu çağrıdan sonra sınıfa başvurulmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="d7c3a-109">The class should not be referenced after this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7c3a-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d7c3a-110">Requirements</span></span>  

 <span data-ttu-id="d7c3a-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7c3a-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7c3a-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d7c3a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d7c3a-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d7c3a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7c3a-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7c3a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7c3a-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d7c3a-115">See also</span></span>

- [<span data-ttu-id="d7c3a-116">LoadClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d7c3a-116">LoadClass Method</span></span>](icordebugmanagedcallback-loadclass-method.md)
- [<span data-ttu-id="d7c3a-117">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d7c3a-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)

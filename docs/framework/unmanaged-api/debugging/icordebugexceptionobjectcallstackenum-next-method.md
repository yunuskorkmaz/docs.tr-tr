---
title: ICorDebugExceptionObjectCallStackEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectCallStackEnum::Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectCallStackEnum::Next
helpviewer_keywords:
- ICorDebugExceptionObjectCallStackEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugExceptionObjectCallStackEnum interface [.NET Framework debugging]
ms.assetid: 3328a2c0-1e48-4a54-802a-9b474cf82c21
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0e7d8344c36fb97a73d0f64ebc3a47645527202e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494122"
---
# <a name="icordebugexceptionobjectcallstackenumnext-method"></a><span data-ttu-id="d4138-102">ICorDebugExceptionObjectCallStackEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d4138-102">ICorDebugExceptionObjectCallStackEnum::Next Method</span></span>
<span data-ttu-id="d4138-103">Belirtilen sayıda alır [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) örnekleriyle bir özel durum nesnenin çağrı yığını bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="d4138-103">Gets the specified number of [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) instances that contain information from an exception object's call stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4138-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d4138-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] CorDebugExceptionObjectStackFrame values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4138-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d4138-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="d4138-106">[in] Sayısını [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) alınacak örnekleri.</span><span class="sxs-lookup"><span data-stu-id="d4138-106">[in] The number of [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="d4138-107">[out] Bir dizi işaretçileri, her biri için işaret eden bir [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) nesne.</span><span class="sxs-lookup"><span data-stu-id="d4138-107">[out] An array of pointers, each of which points to a [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="d4138-108">[out] Bir işaretçi sayısına [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) gerçekte döndürülen örnekleri.</span><span class="sxs-lookup"><span data-stu-id="d4138-108">[out] A pointer to the number of [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) instances actually returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4138-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d4138-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4138-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d4138-110">Requirements</span></span>  
 <span data-ttu-id="d4138-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4138-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4138-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d4138-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d4138-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d4138-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d4138-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4138-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4138-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4138-115">See also</span></span>
- [<span data-ttu-id="d4138-116">ICorDebugExceptionObjectCallStackEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d4138-116">ICorDebugExceptionObjectCallStackEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)
- [<span data-ttu-id="d4138-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d4138-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

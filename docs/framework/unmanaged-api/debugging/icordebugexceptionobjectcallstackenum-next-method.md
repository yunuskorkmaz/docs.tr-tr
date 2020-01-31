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
ms.openlocfilehash: 38de810509f15cf93475eb000837892b99684fc9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782744"
---
# <a name="icordebugexceptionobjectcallstackenumnext-method"></a><span data-ttu-id="0f348-102">ICorDebugExceptionObjectCallStackEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0f348-102">ICorDebugExceptionObjectCallStackEnum::Next Method</span></span>
<span data-ttu-id="0f348-103">Özel durum nesnesinin çağrı yığınından bilgi içeren, belirtilen [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) örneklerinin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="0f348-103">Gets the specified number of [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) instances that contain information from an exception object's call stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f348-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0f348-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] CorDebugExceptionObjectStackFrame values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f348-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0f348-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="0f348-106">'ndaki Alınacak [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) örneklerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="0f348-106">[in] The number of [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="0f348-107">dışı Her biri [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) nesnesine işaret eden bir işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="0f348-107">[out] An array of pointers, each of which points to a [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="0f348-108">dışı Gerçekte döndürülen [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) örneklerinin sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0f348-108">[out] A pointer to the number of [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) instances actually returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0f348-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0f348-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f348-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0f348-110">Requirements</span></span>  
 <span data-ttu-id="0f348-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f348-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f348-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0f348-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0f348-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0f348-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0f348-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f348-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f348-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f348-115">See also</span></span>

- [<span data-ttu-id="0f348-116">ICorDebugExceptionObjectCallStackEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0f348-116">ICorDebugExceptionObjectCallStackEnum Interface</span></span>](icordebugexceptionobjectcallstackenum-interface.md)
- [<span data-ttu-id="0f348-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0f348-117">Debugging Interfaces</span></span>](debugging-interfaces.md)

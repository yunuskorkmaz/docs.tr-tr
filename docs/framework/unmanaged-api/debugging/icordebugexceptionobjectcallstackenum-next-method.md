---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugExceptionObjectCallStackEnum:: Next yöntemi'
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
ms.openlocfilehash: df68eb6e4794d294fc39dd943065582dc52a58a1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693323"
---
# <a name="icordebugexceptionobjectcallstackenumnext-method"></a><span data-ttu-id="b37d8-103">ICorDebugExceptionObjectCallStackEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b37d8-103">ICorDebugExceptionObjectCallStackEnum::Next Method</span></span>

<span data-ttu-id="b37d8-104">Özel durum nesnesinin çağrı yığınından bilgi içeren, belirtilen [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) örneklerinin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="b37d8-104">Gets the specified number of [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) instances that contain information from an exception object's call stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b37d8-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b37d8-105">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] CorDebugExceptionObjectStackFrame values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b37d8-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b37d8-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="b37d8-107">'ndaki Alınacak [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) örneklerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="b37d8-107">[in] The number of [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="b37d8-108">dışı Her biri [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) nesnesine işaret eden bir işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="b37d8-108">[out] An array of pointers, each of which points to a [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="b37d8-109">dışı Gerçekte döndürülen [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) örneklerinin sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b37d8-109">[out] A pointer to the number of [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) instances actually returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b37d8-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b37d8-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b37d8-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b37d8-111">Requirements</span></span>  

 <span data-ttu-id="b37d8-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b37d8-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b37d8-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b37d8-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b37d8-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b37d8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b37d8-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b37d8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b37d8-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b37d8-116">See also</span></span>

- [<span data-ttu-id="b37d8-117">ICorDebugExceptionObjectCallStackEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b37d8-117">ICorDebugExceptionObjectCallStackEnum Interface</span></span>](icordebugexceptionobjectcallstackenum-interface.md)
- [<span data-ttu-id="b37d8-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b37d8-118">Debugging Interfaces</span></span>](debugging-interfaces.md)

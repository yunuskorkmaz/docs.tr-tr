---
title: ICorDebugProcess5::EnumerateHandles Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateHandles
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateHandles
helpviewer_keywords:
- EnumerateHandles method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHandles method [.NET Framework debugging]
ms.assetid: 7d7fa796-0dc6-4ee8-9d56-40166246d91d
topic_type:
- apiref
ms.openlocfilehash: e0e68dba1f4d9ac5fa618aa842b823dcc046e70e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129675"
---
# <a name="icordebugprocess5enumeratehandles-method"></a><span data-ttu-id="bdddc-102">ICorDebugProcess5::EnumerateHandles Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bdddc-102">ICorDebugProcess5::EnumerateHandles Method</span></span>
<span data-ttu-id="bdddc-103">İşlemdeki nesne tanıtıcıları için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="bdddc-103">Gets an enumerator for object handles in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdddc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bdddc-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateHandles(     [in] CorGCReferenceType types,  
    [out] ICorDebugGCReferenceEnum **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bdddc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bdddc-105">Parameters</span></span>  
 `types`  
 <span data-ttu-id="bdddc-106">'ndaki Koleksiyona eklenecek tanıtıcıların türünü belirten [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) değerlerinin bit düzeyinde birleşimi.</span><span class="sxs-lookup"><span data-stu-id="bdddc-106">[in] A bitwise combination of [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) values that specifies the type of handles to include in the collection.</span></span>  
  
 `ppENum`  
 <span data-ttu-id="bdddc-107">dışı Çöp toplanabilecek nesneler için bir Numaralandırıcı olan [ıcorıtcggcreferenceenum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bdddc-107">[out] A pointer to the address of an [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) that is an enumerator for the objects to be garbage-collected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bdddc-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bdddc-108">Remarks</span></span>  
 <span data-ttu-id="bdddc-109">`EnumerateHandles`, tanıtıcı tablosunun incelemesini destekleyen bir yardımcı işlevdir.</span><span class="sxs-lookup"><span data-stu-id="bdddc-109">`EnumerateHandles` is a helper function that supports inspection of the handle table.</span></span> <span data-ttu-id="bdddc-110">[ICorDebugProcess5:: EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) yöntemine benzer, ancak tüm nesneler atık toplama olacak şekilde bir [ıcorıtcggcreferenceenum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) koleksiyonu doldurmaktansa, yalnızca tanıtıcılara sahip olan nesneleri içerir. tanıtıcı tablosu.</span><span class="sxs-lookup"><span data-stu-id="bdddc-110">It is similar to the [ICorDebugProcess5::EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) method, except that rather than populating an [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) collection with all objects to be garbage-collected, it includes only objects that have handles from the handle table.</span></span>  
  
 <span data-ttu-id="bdddc-111">`types` parametresi, koleksiyona dahil edilecek tanıtıcı türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="bdddc-111">The `types` parameter specifies the handle types to include in the collection.</span></span> <span data-ttu-id="bdddc-112">`types`, [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) numaralandırması için aşağıdaki üç üyenin herhangi biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="bdddc-112">`types` can be any of the following three members of the [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) enumeration:</span></span>  
  
- <span data-ttu-id="bdddc-113">`CorHandleStrongOnly` (yalnızca güçlü başvurulara yönelik tanıtıcılardır).</span><span class="sxs-lookup"><span data-stu-id="bdddc-113">`CorHandleStrongOnly` (handles to strong references only).</span></span>  
  
- <span data-ttu-id="bdddc-114">`CorHandleWeakOnly` (yalnızca zayıf başvurulara yönelik tanıtıcılardır).</span><span class="sxs-lookup"><span data-stu-id="bdddc-114">`CorHandleWeakOnly` (handles to weak references only).</span></span>  
  
- <span data-ttu-id="bdddc-115">`CorHandleAll` (tüm tutamaçlar).</span><span class="sxs-lookup"><span data-stu-id="bdddc-115">`CorHandleAll` (all handles).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bdddc-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bdddc-116">Requirements</span></span>  
 <span data-ttu-id="bdddc-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bdddc-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bdddc-118">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="bdddc-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bdddc-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="bdddc-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bdddc-120">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bdddc-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdddc-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bdddc-121">See also</span></span>

- [<span data-ttu-id="bdddc-122">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="bdddc-122">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="bdddc-123">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="bdddc-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

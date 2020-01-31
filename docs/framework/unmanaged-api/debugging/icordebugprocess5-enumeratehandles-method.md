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
ms.openlocfilehash: 2a1653055a3834ce1bed0e7de7877b255bea0c38
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792423"
---
# <a name="icordebugprocess5enumeratehandles-method"></a><span data-ttu-id="41768-102">ICorDebugProcess5::EnumerateHandles Yöntemi</span><span class="sxs-lookup"><span data-stu-id="41768-102">ICorDebugProcess5::EnumerateHandles Method</span></span>
<span data-ttu-id="41768-103">İşlemdeki nesne tanıtıcıları için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="41768-103">Gets an enumerator for object handles in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41768-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="41768-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateHandles(     [in] CorGCReferenceType types,  
    [out] ICorDebugGCReferenceEnum **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="41768-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="41768-105">Parameters</span></span>  
 `types`  
 <span data-ttu-id="41768-106">'ndaki Koleksiyona eklenecek tanıtıcıların türünü belirten [CorGCReferenceType](corgcreferencetype-enumeration.md) değerlerinin bit düzeyinde birleşimi.</span><span class="sxs-lookup"><span data-stu-id="41768-106">[in] A bitwise combination of [CorGCReferenceType](corgcreferencetype-enumeration.md) values that specifies the type of handles to include in the collection.</span></span>  
  
 `ppENum`  
 <span data-ttu-id="41768-107">dışı Çöp toplanabilecek nesneler için bir Numaralandırıcı olan [ıcorıtcggcreferenceenum](icordebuggcreferenceenum-interface.md) adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="41768-107">[out] A pointer to the address of an [ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md) that is an enumerator for the objects to be garbage-collected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41768-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="41768-108">Remarks</span></span>  
 <span data-ttu-id="41768-109">`EnumerateHandles`, tanıtıcı tablosunun incelemesini destekleyen bir yardımcı işlevdir.</span><span class="sxs-lookup"><span data-stu-id="41768-109">`EnumerateHandles` is a helper function that supports inspection of the handle table.</span></span> <span data-ttu-id="41768-110">[ICorDebugProcess5:: EnumerateGCReferences](icordebugprocess5-enumerategcreferences-method.md) yöntemine benzer, ancak tüm nesneler ile bir [ıcorıtcggcreferenceenum](icordebuggcreferenceenum-interface.md) koleksiyonu yerleştirmek yerine yalnızca tanıtıcı tablosundan tanıtıcılara sahip nesneleri içerir.</span><span class="sxs-lookup"><span data-stu-id="41768-110">It is similar to the [ICorDebugProcess5::EnumerateGCReferences](icordebugprocess5-enumerategcreferences-method.md) method, except that rather than populating an [ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md) collection with all objects to be garbage-collected, it includes only objects that have handles from the handle table.</span></span>  
  
 <span data-ttu-id="41768-111">`types` parametresi, koleksiyona dahil edilecek tanıtıcı türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="41768-111">The `types` parameter specifies the handle types to include in the collection.</span></span> <span data-ttu-id="41768-112">`types`, [CorGCReferenceType](corgcreferencetype-enumeration.md) numaralandırması için aşağıdaki üç üyenin herhangi biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="41768-112">`types` can be any of the following three members of the [CorGCReferenceType](corgcreferencetype-enumeration.md) enumeration:</span></span>  
  
- <span data-ttu-id="41768-113">`CorHandleStrongOnly` (yalnızca güçlü başvurulara yönelik tanıtıcılardır).</span><span class="sxs-lookup"><span data-stu-id="41768-113">`CorHandleStrongOnly` (handles to strong references only).</span></span>  
  
- <span data-ttu-id="41768-114">`CorHandleWeakOnly` (yalnızca zayıf başvurulara yönelik tanıtıcılardır).</span><span class="sxs-lookup"><span data-stu-id="41768-114">`CorHandleWeakOnly` (handles to weak references only).</span></span>  
  
- <span data-ttu-id="41768-115">`CorHandleAll` (tüm tutamaçlar).</span><span class="sxs-lookup"><span data-stu-id="41768-115">`CorHandleAll` (all handles).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41768-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="41768-116">Requirements</span></span>  
 <span data-ttu-id="41768-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41768-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41768-118">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="41768-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="41768-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="41768-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="41768-120">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41768-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41768-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="41768-121">See also</span></span>

- [<span data-ttu-id="41768-122">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="41768-122">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="41768-123">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="41768-123">Debugging</span></span>](index.md)

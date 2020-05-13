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
ms.openlocfilehash: 291b384d6f0c8c1404b380c653693ec65fcfc960
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213419"
---
# <a name="icordebugprocess5enumeratehandles-method"></a><span data-ttu-id="e829b-102">ICorDebugProcess5::EnumerateHandles Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e829b-102">ICorDebugProcess5::EnumerateHandles Method</span></span>
<span data-ttu-id="e829b-103">İşlemdeki nesne tanıtıcıları için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="e829b-103">Gets an enumerator for object handles in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e829b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e829b-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateHandles(     [in] CorGCReferenceType types,  
    [out] ICorDebugGCReferenceEnum **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e829b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e829b-105">Parameters</span></span>  
 `types`  
 <span data-ttu-id="e829b-106">'ndaki Koleksiyona eklenecek tanıtıcıların türünü belirten [CorGCReferenceType](corgcreferencetype-enumeration.md) değerlerinin bit düzeyinde birleşimi.</span><span class="sxs-lookup"><span data-stu-id="e829b-106">[in] A bitwise combination of [CorGCReferenceType](corgcreferencetype-enumeration.md) values that specifies the type of handles to include in the collection.</span></span>  
  
 `ppENum`  
 <span data-ttu-id="e829b-107">dışı Çöp toplanabilecek nesneler için bir Numaralandırıcı olan [ıcorıtcggcreferenceenum](icordebuggcreferenceenum-interface.md) adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e829b-107">[out] A pointer to the address of an [ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md) that is an enumerator for the objects to be garbage-collected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e829b-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e829b-108">Remarks</span></span>  
 <span data-ttu-id="e829b-109">`EnumerateHandles`, tanıtıcı tablosunun incelemesini destekleyen bir yardımcı işlevdir.</span><span class="sxs-lookup"><span data-stu-id="e829b-109">`EnumerateHandles` is a helper function that supports inspection of the handle table.</span></span> <span data-ttu-id="e829b-110">[ICorDebugProcess5:: EnumerateGCReferences](icordebugprocess5-enumerategcreferences-method.md) yöntemine benzer, ancak tüm nesneler ile bir [ıcorıtcggcreferenceenum](icordebuggcreferenceenum-interface.md) koleksiyonu yerleştirmek yerine yalnızca tanıtıcı tablosundan tanıtıcılara sahip nesneleri içerir.</span><span class="sxs-lookup"><span data-stu-id="e829b-110">It is similar to the [ICorDebugProcess5::EnumerateGCReferences](icordebugprocess5-enumerategcreferences-method.md) method, except that rather than populating an [ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md) collection with all objects to be garbage-collected, it includes only objects that have handles from the handle table.</span></span>  
  
 <span data-ttu-id="e829b-111">`types`Parametresi, koleksiyona dahil edilecek tanıtıcı türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e829b-111">The `types` parameter specifies the handle types to include in the collection.</span></span> <span data-ttu-id="e829b-112">`types`[CorGCReferenceType](corgcreferencetype-enumeration.md) numaralandırması için aşağıdaki üç üyenin herhangi biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="e829b-112">`types` can be any of the following three members of the [CorGCReferenceType](corgcreferencetype-enumeration.md) enumeration:</span></span>  
  
- <span data-ttu-id="e829b-113">`CorHandleStrongOnly`(yalnızca güçlü başvurulara yönelik tanıtıcılardır).</span><span class="sxs-lookup"><span data-stu-id="e829b-113">`CorHandleStrongOnly` (handles to strong references only).</span></span>  
  
- <span data-ttu-id="e829b-114">`CorHandleWeakOnly`(yalnızca zayıf başvurulara yönelik tanıtıcılardır).</span><span class="sxs-lookup"><span data-stu-id="e829b-114">`CorHandleWeakOnly` (handles to weak references only).</span></span>  
  
- <span data-ttu-id="e829b-115">`CorHandleAll`(tüm tutamaçlar).</span><span class="sxs-lookup"><span data-stu-id="e829b-115">`CorHandleAll` (all handles).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e829b-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e829b-116">Requirements</span></span>  
 <span data-ttu-id="e829b-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e829b-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e829b-118">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e829b-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e829b-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e829b-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e829b-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e829b-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e829b-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e829b-121">See also</span></span>

- [<span data-ttu-id="e829b-122">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="e829b-122">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="e829b-123">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="e829b-123">Debugging</span></span>](index.md)

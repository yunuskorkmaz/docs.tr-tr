---
description: 'Daha fazla bilgi edinin: ICorDebugProcess5:: EnumerateHandles yöntemi'
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
ms.openlocfilehash: 62ca1390ceec634e6651dc013345688fe5892bcd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649916"
---
# <a name="icordebugprocess5enumeratehandles-method"></a><span data-ttu-id="9f909-103">ICorDebugProcess5::EnumerateHandles Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9f909-103">ICorDebugProcess5::EnumerateHandles Method</span></span>

<span data-ttu-id="9f909-104">İşlemdeki nesne tanıtıcıları için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="9f909-104">Gets an enumerator for object handles in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f909-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9f909-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateHandles(     [in] CorGCReferenceType types,  
    [out] ICorDebugGCReferenceEnum **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9f909-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9f909-106">Parameters</span></span>  

 `types`  
 <span data-ttu-id="9f909-107">'ndaki Koleksiyona eklenecek tanıtıcıların türünü belirten [CorGCReferenceType](corgcreferencetype-enumeration.md) değerlerinin bit düzeyinde birleşimi.</span><span class="sxs-lookup"><span data-stu-id="9f909-107">[in] A bitwise combination of [CorGCReferenceType](corgcreferencetype-enumeration.md) values that specifies the type of handles to include in the collection.</span></span>  
  
 `ppENum`  
 <span data-ttu-id="9f909-108">dışı Çöp toplanabilecek nesneler için bir Numaralandırıcı olan [ıcorıtcggcreferenceenum](icordebuggcreferenceenum-interface.md) adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9f909-108">[out] A pointer to the address of an [ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md) that is an enumerator for the objects to be garbage-collected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9f909-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9f909-109">Remarks</span></span>  

 <span data-ttu-id="9f909-110">`EnumerateHandles` , tanıtıcı tablosunun incelemesini destekleyen bir yardımcı işlevdir.</span><span class="sxs-lookup"><span data-stu-id="9f909-110">`EnumerateHandles` is a helper function that supports inspection of the handle table.</span></span> <span data-ttu-id="9f909-111">[ICorDebugProcess5:: EnumerateGCReferences](icordebugprocess5-enumerategcreferences-method.md) yöntemine benzer, ancak tüm nesneler ile bir [ıcorıtcggcreferenceenum](icordebuggcreferenceenum-interface.md) koleksiyonu yerleştirmek yerine yalnızca tanıtıcı tablosundan tanıtıcılara sahip nesneleri içerir.</span><span class="sxs-lookup"><span data-stu-id="9f909-111">It is similar to the [ICorDebugProcess5::EnumerateGCReferences](icordebugprocess5-enumerategcreferences-method.md) method, except that rather than populating an [ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md) collection with all objects to be garbage-collected, it includes only objects that have handles from the handle table.</span></span>  
  
 <span data-ttu-id="9f909-112">`types`Parametresi, koleksiyona dahil edilecek tanıtıcı türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9f909-112">The `types` parameter specifies the handle types to include in the collection.</span></span> <span data-ttu-id="9f909-113">`types`[CorGCReferenceType](corgcreferencetype-enumeration.md) numaralandırması için aşağıdaki üç üyenin herhangi biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="9f909-113">`types` can be any of the following three members of the [CorGCReferenceType](corgcreferencetype-enumeration.md) enumeration:</span></span>  
  
- <span data-ttu-id="9f909-114">`CorHandleStrongOnly` (yalnızca güçlü başvurulara yönelik tanıtıcılardır).</span><span class="sxs-lookup"><span data-stu-id="9f909-114">`CorHandleStrongOnly` (handles to strong references only).</span></span>  
  
- <span data-ttu-id="9f909-115">`CorHandleWeakOnly` (yalnızca zayıf başvurulara yönelik tanıtıcılardır).</span><span class="sxs-lookup"><span data-stu-id="9f909-115">`CorHandleWeakOnly` (handles to weak references only).</span></span>  
  
- <span data-ttu-id="9f909-116">`CorHandleAll` (tüm tutamaçlar).</span><span class="sxs-lookup"><span data-stu-id="9f909-116">`CorHandleAll` (all handles).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f909-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9f909-117">Requirements</span></span>  

 <span data-ttu-id="9f909-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f909-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f909-119">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9f909-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9f909-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9f909-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9f909-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f909-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f909-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9f909-122">See also</span></span>

- [<span data-ttu-id="9f909-123">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="9f909-123">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="9f909-124">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="9f909-124">Debugging</span></span>](index.md)

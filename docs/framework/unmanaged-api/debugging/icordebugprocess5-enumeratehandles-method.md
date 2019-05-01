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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2b3cc158c48e8bb9f833429bbddaa74ed459f1b6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61930279"
---
# <a name="icordebugprocess5enumeratehandles-method"></a><span data-ttu-id="7bccb-102">ICorDebugProcess5::EnumerateHandles Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7bccb-102">ICorDebugProcess5::EnumerateHandles Method</span></span>
<span data-ttu-id="7bccb-103">Numaralandırıcı nesnesi tanıtıcıları için bir işlem olarak alır.</span><span class="sxs-lookup"><span data-stu-id="7bccb-103">Gets an enumerator for object handles in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bccb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7bccb-104">Syntax</span></span>  
  
```  
HRESULT EnumerateHandles(     [in] CorGCReferenceType types,  
    [out] ICorDebugGCReferenceEnum **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7bccb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7bccb-105">Parameters</span></span>  
 `types`  
 <span data-ttu-id="7bccb-106">[in] Bitsel bir birleşimi [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) koleksiyona dahil etmek tanıtıcıları türünü belirten değer.</span><span class="sxs-lookup"><span data-stu-id="7bccb-106">[in] A bitwise combination of [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) values that specifies the type of handles to include in the collection.</span></span>  
  
 `ppENum`  
 <span data-ttu-id="7bccb-107">[out] Adresine bir işaretçi bir [Icordebuggcreferenceenum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) atık olarak toplanmış için diğer bir deyişle bir numaralandırıcı nesneler için.</span><span class="sxs-lookup"><span data-stu-id="7bccb-107">[out] A pointer to the address of an [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) that is an enumerator for the objects to be garbage-collected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7bccb-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7bccb-108">Remarks</span></span>  
 <span data-ttu-id="7bccb-109">`EnumerateHandles` tanıtıcı tablosunu incelenmesi destekleyen bir yardımcı işlevdir.</span><span class="sxs-lookup"><span data-stu-id="7bccb-109">`EnumerateHandles` is a helper function that supports inspection of the handle table.</span></span> <span data-ttu-id="7bccb-110">Benzer [Icordebugprocess5::enumerategcreferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) hariç yöntemi doldurma yerine bir [Icordebuggcreferenceenum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) atık olarak toplanmış, alınacak tüm nesneler ile koleksiyon, işleyicisi tablosundan tanıtıcıları içeren nesneleri içerir.</span><span class="sxs-lookup"><span data-stu-id="7bccb-110">It is similar to the [ICorDebugProcess5::EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) method, except that rather than populating an [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) collection with all objects to be garbage-collected, it includes only objects that have handles from the handle table.</span></span>  
  
 <span data-ttu-id="7bccb-111">`types` Parametresi koleksiyona dahil etmek tanıtıcı türlerine belirtir.</span><span class="sxs-lookup"><span data-stu-id="7bccb-111">The `types` parameter specifies the handle types to include in the collection.</span></span> <span data-ttu-id="7bccb-112">`types` Aşağıdaki üç üyeleri olabilir [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) sabit listesi:</span><span class="sxs-lookup"><span data-stu-id="7bccb-112">`types` can be any of the following three members of the [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) enumeration:</span></span>  
  
- <span data-ttu-id="7bccb-113">`CorHandleStrongOnly` (yalnızca tanımlayıcı başvuruları tanıtıcıları).</span><span class="sxs-lookup"><span data-stu-id="7bccb-113">`CorHandleStrongOnly` (handles to strong references only).</span></span>  
  
- <span data-ttu-id="7bccb-114">`CorHandleWeakOnly` (yalnızca zayıf başvurular tanıtıcıları).</span><span class="sxs-lookup"><span data-stu-id="7bccb-114">`CorHandleWeakOnly` (handles to weak references only).</span></span>  
  
- <span data-ttu-id="7bccb-115">`CorHandleAll` (tüm tutamaçlar).</span><span class="sxs-lookup"><span data-stu-id="7bccb-115">`CorHandleAll` (all handles).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7bccb-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7bccb-116">Requirements</span></span>  
 <span data-ttu-id="7bccb-117">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7bccb-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7bccb-118">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7bccb-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7bccb-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7bccb-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7bccb-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7bccb-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bccb-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7bccb-121">See also</span></span>

- [<span data-ttu-id="7bccb-122">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="7bccb-122">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="7bccb-123">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="7bccb-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

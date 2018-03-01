---
title: "ICorDebugProcess5::EnumerateHandles Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c9bf9f1a4d565e0af4f3ee34a2805116407027d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess5enumeratehandles-method"></a><span data-ttu-id="e64e0-102">ICorDebugProcess5::EnumerateHandles Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e64e0-102">ICorDebugProcess5::EnumerateHandles Method</span></span>
<span data-ttu-id="e64e0-103">Bir numaralandırıcı Nesne tanıtıcıları için bir işlem olarak alır.</span><span class="sxs-lookup"><span data-stu-id="e64e0-103">Gets an enumerator for object handles in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e64e0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e64e0-104">Syntax</span></span>  
  
```  
HRESULT EnumerateHandles(     [in] CorGCReferenceType types,  
    [out] ICorDebugGCReferenceEnum **ppEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e64e0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e64e0-105">Parameters</span></span>  
 `types`  
 <span data-ttu-id="e64e0-106">[in] Bit düzeyinde bileşimini [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) koleksiyona dahil etmek tanıtıcıları türünü belirtir. değerler.</span><span class="sxs-lookup"><span data-stu-id="e64e0-106">[in] A bitwise combination of [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) values that specifies the type of handles to include in the collection.</span></span>  
  
 `ppENum`  
 <span data-ttu-id="e64e0-107">[out] Adresine bir işaretçi bir [Icordebuggcreferenceenum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) çöpünün toplanma için diğer bir deyişle bir numaralandırıcı nesneler için.</span><span class="sxs-lookup"><span data-stu-id="e64e0-107">[out] A pointer to the address of an [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) that is an enumerator for the objects to be garbage-collected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e64e0-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e64e0-108">Remarks</span></span>  
 <span data-ttu-id="e64e0-109">`EnumerateHandles`tanıtıcı tablosunu incelenmesi destekleyen bir yardımcı işlevdir.</span><span class="sxs-lookup"><span data-stu-id="e64e0-109">`EnumerateHandles` is a helper function that supports inspection of the handle table.</span></span> <span data-ttu-id="e64e0-110">Aşağıdakine benzer [Icordebugprocess5::enumerategcreferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) hariç yöntemi doldurma yerine bir [Icordebuggcreferenceenum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) çöpünün toplanma olacak tüm nesneleri koleksiyonuyla, tanıtıcı tablosundan tanıtıcıları sahip nesneleri içerir.</span><span class="sxs-lookup"><span data-stu-id="e64e0-110">It is similar to the [ICorDebugProcess5::EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) method, except that rather than populating an [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) collection with all objects to be garbage-collected, it includes only objects that have handles from the handle table.</span></span>  
  
 <span data-ttu-id="e64e0-111">`types` Parametresi koleksiyonda eklenecek tanıtıcı türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e64e0-111">The `types` parameter specifies the handle types to include in the collection.</span></span> <span data-ttu-id="e64e0-112">`types`Aşağıdaki üç üyeleri olabilir [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) numaralandırma:</span><span class="sxs-lookup"><span data-stu-id="e64e0-112">`types` can be any of the following three members of the [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) enumeration:</span></span>  
  
-   <span data-ttu-id="e64e0-113">`CorHandleStrongOnly`(yalnızca güçlü başvuruları işleyicilerine).</span><span class="sxs-lookup"><span data-stu-id="e64e0-113">`CorHandleStrongOnly` (handles to strong references only).</span></span>  
  
-   <span data-ttu-id="e64e0-114">`CorHandleWeakOnly`(yalnızca zayıf başvurular işleyicilerine).</span><span class="sxs-lookup"><span data-stu-id="e64e0-114">`CorHandleWeakOnly` (handles to weak references only).</span></span>  
  
-   <span data-ttu-id="e64e0-115">`CorHandleAll`(tüm tanıtıcı).</span><span class="sxs-lookup"><span data-stu-id="e64e0-115">`CorHandleAll` (all handles).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e64e0-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e64e0-116">Requirements</span></span>  
 <span data-ttu-id="e64e0-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e64e0-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e64e0-118">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e64e0-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e64e0-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e64e0-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e64e0-120">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e64e0-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e64e0-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e64e0-121">See Also</span></span>  
 [<span data-ttu-id="e64e0-122">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="e64e0-122">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="e64e0-123">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="e64e0-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

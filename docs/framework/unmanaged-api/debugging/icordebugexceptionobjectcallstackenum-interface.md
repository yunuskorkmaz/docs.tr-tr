---
title: ICorDebugExceptionObjectCallStackEnum Arabirimi
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
- ICorDebugExceptionObjectCallStackEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectCallStackEnum
helpviewer_keywords:
- ICorDebugExceptionObjectCallStackEnum interface [.NET Framework debugging]
ms.assetid: 39dffa18-c71b-48c4-b11d-e814631ab1e9
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f353ecaf4f0a64920fa7e23b98d09ef3191428cb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugexceptionobjectcallstackenum-interface"></a><span data-ttu-id="998f8-102">ICorDebugExceptionObjectCallStackEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="998f8-102">ICorDebugExceptionObjectCallStackEnum Interface</span></span>
<span data-ttu-id="998f8-103">Özel durum nesnesine katıştırılmış çağrı yığını bilgileri için bir numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="998f8-103">Provides an enumerator for call stack information that is embedded in an exception object.</span></span> <span data-ttu-id="998f8-104">Bu arabirim Icordebugenum arabirimi sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="998f8-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="998f8-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="998f8-105">Methods</span></span>  
  
|<span data-ttu-id="998f8-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="998f8-106">Method</span></span>|<span data-ttu-id="998f8-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="998f8-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="998f8-108">Icordebugexceptionobjectcallstackenum::Next</span><span class="sxs-lookup"><span data-stu-id="998f8-108">ICorDebugExceptionObjectCallStackEnum::Next</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-next-method.md)|<span data-ttu-id="998f8-109">Belirtilen sayıda alır [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) bir özel durum nesnenin çağrı yığını hakkında bilgi içeren nesne.</span><span class="sxs-lookup"><span data-stu-id="998f8-109">Gets a specified number of [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) objects that contain information about an exception object's call stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="998f8-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="998f8-110">Remarks</span></span>  
 <span data-ttu-id="998f8-111">`ICorDebugExceptionObjectCallStackEnum` Arabirimini uygulayan Icordebugenum arabirimi.</span><span class="sxs-lookup"><span data-stu-id="998f8-111">The `ICorDebugExceptionObjectCallStackEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="998f8-112">Bir `ICorDebugExceptionObjectCallStackEnum` örneği ile doldurulur [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) çağırarak nesneleri [Icordebugexceptionobjectvalue::enumerateexceptioncallstack](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="998f8-112">An `ICorDebugExceptionObjectCallStackEnum` instance is populated with [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) objects by calling the [ICorDebugExceptionObjectValue::EnumerateExceptionCallStack](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) method.</span></span> <span data-ttu-id="998f8-113">Koleksiyondaki çağrı yığını öğeleri çağırarak numaralandırılabilecek [Icordebugexceptionobjectcallstackenum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-next-method.md) yöntemi</span><span class="sxs-lookup"><span data-stu-id="998f8-113">The call stack items in the collection can be enumerated by calling the [ICorDebugExceptionObjectCallStackEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-next-method.md) method</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="998f8-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="998f8-114">Requirements</span></span>  
 <span data-ttu-id="998f8-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="998f8-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="998f8-116">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="998f8-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="998f8-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="998f8-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="998f8-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="998f8-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="998f8-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="998f8-119">See Also</span></span>  
 [<span data-ttu-id="998f8-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="998f8-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="998f8-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="998f8-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

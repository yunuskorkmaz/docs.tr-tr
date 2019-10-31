---
title: ICorDebugExceptionObjectCallStackEnum Arabirimi
ms.date: 03/30/2017
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
ms.openlocfilehash: 99a700270794ca92356cb9d134cb869d456199f9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084434"
---
# <a name="icordebugexceptionobjectcallstackenum-interface"></a><span data-ttu-id="6629f-102">ICorDebugExceptionObjectCallStackEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6629f-102">ICorDebugExceptionObjectCallStackEnum Interface</span></span>
<span data-ttu-id="6629f-103">Özel durum nesnesine katıştırılmış çağrı yığını bilgileri için bir numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="6629f-103">Provides an enumerator for call stack information that is embedded in an exception object.</span></span> <span data-ttu-id="6629f-104">Bu arabirim, ıcordebuggenum arabiriminin bir alt sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="6629f-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6629f-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6629f-105">Methods</span></span>  
  
|<span data-ttu-id="6629f-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="6629f-106">Method</span></span>|<span data-ttu-id="6629f-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6629f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6629f-108">ICorDebugExceptionObjectCallStackEnum:: Next</span><span class="sxs-lookup"><span data-stu-id="6629f-108">ICorDebugExceptionObjectCallStackEnum::Next</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-next-method.md)|<span data-ttu-id="6629f-109">Bir özel durum nesnesinin çağrı yığını hakkında bilgi içeren, belirtilen sayıda [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) nesnesi alır.</span><span class="sxs-lookup"><span data-stu-id="6629f-109">Gets a specified number of [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) objects that contain information about an exception object's call stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6629f-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6629f-110">Remarks</span></span>  
 <span data-ttu-id="6629f-111">`ICorDebugExceptionObjectCallStackEnum` arabirimi ıcorı, Genum arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="6629f-111">The `ICorDebugExceptionObjectCallStackEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="6629f-112">[ICorDebugExceptionObjectValue:: EnumerateExceptionCallStack](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) yöntemi çağırarak bir `ICorDebugExceptionObjectCallStackEnum` örneği [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) nesneleriyle doldurulur.</span><span class="sxs-lookup"><span data-stu-id="6629f-112">An `ICorDebugExceptionObjectCallStackEnum` instance is populated with [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) objects by calling the [ICorDebugExceptionObjectValue::EnumerateExceptionCallStack](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) method.</span></span> <span data-ttu-id="6629f-113">Koleksiyondaki çağrı yığını öğeleri [ICorDebugExceptionObjectCallStackEnum:: Next](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-next-method.md) yöntemi çağırarak Numaralandırılabilir</span><span class="sxs-lookup"><span data-stu-id="6629f-113">The call stack items in the collection can be enumerated by calling the [ICorDebugExceptionObjectCallStackEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-next-method.md) method</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6629f-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6629f-114">Requirements</span></span>  
 <span data-ttu-id="6629f-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6629f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6629f-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6629f-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6629f-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6629f-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6629f-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6629f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6629f-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6629f-119">See also</span></span>

- [<span data-ttu-id="6629f-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6629f-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="6629f-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="6629f-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

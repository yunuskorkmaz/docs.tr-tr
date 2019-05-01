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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e7ed6c04a46a767ed122e54df0695429cf923b8a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988916"
---
# <a name="icordebugexceptionobjectcallstackenum-interface"></a><span data-ttu-id="a8eb1-102">ICorDebugExceptionObjectCallStackEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a8eb1-102">ICorDebugExceptionObjectCallStackEnum Interface</span></span>
<span data-ttu-id="a8eb1-103">Özel durum nesnesine katıştırılmış çağrı yığını bilgileri için bir numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="a8eb1-103">Provides an enumerator for call stack information that is embedded in an exception object.</span></span> <span data-ttu-id="a8eb1-104">Icordebugenum arabirimi öğesinin arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="a8eb1-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a8eb1-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a8eb1-105">Methods</span></span>  
  
|<span data-ttu-id="a8eb1-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="a8eb1-106">Method</span></span>|<span data-ttu-id="a8eb1-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a8eb1-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a8eb1-108">Icordebugexceptionobjectcallstackenum::Next</span><span class="sxs-lookup"><span data-stu-id="a8eb1-108">ICorDebugExceptionObjectCallStackEnum::Next</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-next-method.md)|<span data-ttu-id="a8eb1-109">Belirtilen sayıda alır [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) bir özel durum nesnenin çağrı yığını hakkında bilgi içeren nesne.</span><span class="sxs-lookup"><span data-stu-id="a8eb1-109">Gets a specified number of [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) objects that contain information about an exception object's call stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a8eb1-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a8eb1-110">Remarks</span></span>  
 <span data-ttu-id="a8eb1-111">`ICorDebugExceptionObjectCallStackEnum` Arabirimi uygulayan Icordebugenum arabirimi.</span><span class="sxs-lookup"><span data-stu-id="a8eb1-111">The `ICorDebugExceptionObjectCallStackEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="a8eb1-112">Bir `ICorDebugExceptionObjectCallStackEnum` örneği ile doldurulur [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) çağırarak nesneleri [Icordebugexceptionobjectvalue::enumerateexceptioncallstack](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a8eb1-112">An `ICorDebugExceptionObjectCallStackEnum` instance is populated with [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) objects by calling the [ICorDebugExceptionObjectValue::EnumerateExceptionCallStack](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) method.</span></span> <span data-ttu-id="a8eb1-113">Çağrı yığını öğeleri koleksiyonu çağırarak numaralandırılabilir [Icordebugexceptionobjectcallstackenum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-next-method.md) yöntemi</span><span class="sxs-lookup"><span data-stu-id="a8eb1-113">The call stack items in the collection can be enumerated by calling the [ICorDebugExceptionObjectCallStackEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-next-method.md) method</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8eb1-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a8eb1-114">Requirements</span></span>  
 <span data-ttu-id="a8eb1-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8eb1-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8eb1-116">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a8eb1-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a8eb1-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a8eb1-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a8eb1-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8eb1-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8eb1-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a8eb1-119">See also</span></span>

- [<span data-ttu-id="a8eb1-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a8eb1-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="a8eb1-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="a8eb1-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

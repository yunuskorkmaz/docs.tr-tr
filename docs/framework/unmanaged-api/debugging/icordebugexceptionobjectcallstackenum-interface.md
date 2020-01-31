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
ms.openlocfilehash: 9d98bccdfb83cec547b185693c28f25017d3225f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782806"
---
# <a name="icordebugexceptionobjectcallstackenum-interface"></a><span data-ttu-id="1d193-102">ICorDebugExceptionObjectCallStackEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1d193-102">ICorDebugExceptionObjectCallStackEnum Interface</span></span>
<span data-ttu-id="1d193-103">Özel durum nesnesine katıştırılmış çağrı yığını bilgileri için bir numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="1d193-103">Provides an enumerator for call stack information that is embedded in an exception object.</span></span> <span data-ttu-id="1d193-104">Bu arabirim, ıcordebuggenum arabiriminin bir alt sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="1d193-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1d193-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1d193-105">Methods</span></span>  
  
|<span data-ttu-id="1d193-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="1d193-106">Method</span></span>|<span data-ttu-id="1d193-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1d193-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1d193-108">ICorDebugExceptionObjectCallStackEnum:: Next</span><span class="sxs-lookup"><span data-stu-id="1d193-108">ICorDebugExceptionObjectCallStackEnum::Next</span></span>](icordebugexceptionobjectcallstackenum-next-method.md)|<span data-ttu-id="1d193-109">Bir özel durum nesnesinin çağrı yığını hakkında bilgi içeren, belirtilen sayıda [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) nesnesi alır.</span><span class="sxs-lookup"><span data-stu-id="1d193-109">Gets a specified number of [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) objects that contain information about an exception object's call stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d193-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1d193-110">Remarks</span></span>  
 <span data-ttu-id="1d193-111">`ICorDebugExceptionObjectCallStackEnum` arabirimi ıcorı, Genum arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="1d193-111">The `ICorDebugExceptionObjectCallStackEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="1d193-112">[ICorDebugExceptionObjectValue:: EnumerateExceptionCallStack](icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) yöntemi çağırarak bir `ICorDebugExceptionObjectCallStackEnum` örneği [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) nesneleriyle doldurulur.</span><span class="sxs-lookup"><span data-stu-id="1d193-112">An `ICorDebugExceptionObjectCallStackEnum` instance is populated with [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) objects by calling the [ICorDebugExceptionObjectValue::EnumerateExceptionCallStack](icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) method.</span></span> <span data-ttu-id="1d193-113">Koleksiyondaki çağrı yığını öğeleri [ICorDebugExceptionObjectCallStackEnum:: Next](icordebugexceptionobjectcallstackenum-next-method.md) yöntemi çağırarak Numaralandırılabilir</span><span class="sxs-lookup"><span data-stu-id="1d193-113">The call stack items in the collection can be enumerated by calling the [ICorDebugExceptionObjectCallStackEnum::Next](icordebugexceptionobjectcallstackenum-next-method.md) method</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d193-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1d193-114">Requirements</span></span>  
 <span data-ttu-id="1d193-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d193-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d193-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1d193-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1d193-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1d193-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1d193-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d193-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d193-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1d193-119">See also</span></span>

- [<span data-ttu-id="1d193-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1d193-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="1d193-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="1d193-121">Debugging</span></span>](index.md)

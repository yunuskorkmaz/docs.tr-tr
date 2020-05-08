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
ms.openlocfilehash: e6dd951b0f432d455d95bb60f4c42df64d5bee24
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82975998"
---
# <a name="icordebugexceptionobjectcallstackenum-interface"></a><span data-ttu-id="91f5a-102">ICorDebugExceptionObjectCallStackEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="91f5a-102">ICorDebugExceptionObjectCallStackEnum Interface</span></span>
<span data-ttu-id="91f5a-103">Özel durum nesnesine katıştırılmış çağrı yığını bilgileri için bir numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="91f5a-103">Provides an enumerator for call stack information that is embedded in an exception object.</span></span> <span data-ttu-id="91f5a-104">Bu arabirim, ıcordebuggenum arabiriminin bir alt sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="91f5a-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="91f5a-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="91f5a-105">Methods</span></span>  
  
|<span data-ttu-id="91f5a-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="91f5a-106">Method</span></span>|<span data-ttu-id="91f5a-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="91f5a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="91f5a-108">ICorDebugExceptionObjectCallStackEnum:: Next</span><span class="sxs-lookup"><span data-stu-id="91f5a-108">ICorDebugExceptionObjectCallStackEnum::Next</span></span>](icordebugexceptionobjectcallstackenum-next-method.md)|<span data-ttu-id="91f5a-109">Bir özel durum nesnesinin çağrı yığını hakkında bilgi içeren, belirtilen sayıda [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) nesnesi alır.</span><span class="sxs-lookup"><span data-stu-id="91f5a-109">Gets a specified number of [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) objects that contain information about an exception object's call stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="91f5a-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="91f5a-110">Remarks</span></span>  
 <span data-ttu-id="91f5a-111">`ICorDebugExceptionObjectCallStackEnum` Arabirim ıcorı, genum arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="91f5a-111">The `ICorDebugExceptionObjectCallStackEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="91f5a-112">`ICorDebugExceptionObjectCallStackEnum` [ICorDebugExceptionObjectValue:: EnumerateExceptionCallStack](icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) yöntemi çağırarak bir örnek [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) nesneleriyle doldurulur.</span><span class="sxs-lookup"><span data-stu-id="91f5a-112">An `ICorDebugExceptionObjectCallStackEnum` instance is populated with [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) objects by calling the [ICorDebugExceptionObjectValue::EnumerateExceptionCallStack](icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) method.</span></span> <span data-ttu-id="91f5a-113">Koleksiyondaki çağrı yığını öğeleri [ICorDebugExceptionObjectCallStackEnum:: Next](icordebugexceptionobjectcallstackenum-next-method.md) yöntemi çağırarak Numaralandırılabilir</span><span class="sxs-lookup"><span data-stu-id="91f5a-113">The call stack items in the collection can be enumerated by calling the [ICorDebugExceptionObjectCallStackEnum::Next](icordebugexceptionobjectcallstackenum-next-method.md) method</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91f5a-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="91f5a-114">Requirements</span></span>  
 <span data-ttu-id="91f5a-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91f5a-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91f5a-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="91f5a-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="91f5a-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="91f5a-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="91f5a-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91f5a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91f5a-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="91f5a-119">See also</span></span>

- [<span data-ttu-id="91f5a-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="91f5a-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="91f5a-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="91f5a-121">Debugging</span></span>](index.md)

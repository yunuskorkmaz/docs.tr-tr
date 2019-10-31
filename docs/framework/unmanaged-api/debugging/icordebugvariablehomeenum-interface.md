---
title: ICorDebugVariableHomeEnum Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHomeEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHomeEnum
helpviewer_keywords:
- ICorDebugVariableHomeEnum interface [.NET Framework debugging]
ms.assetid: c312ae6d-c8dc-48d6-9f1e-ead515c88fdf
topic_type:
- apiref
ms.openlocfilehash: a9b65449747fde42f9cd770e33741ef34d33fbb8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121033"
---
# <a name="icordebugvariablehomeenum-interface"></a><span data-ttu-id="5252e-102">ICorDebugVariableHomeEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5252e-102">ICorDebugVariableHomeEnum Interface</span></span>
<span data-ttu-id="5252e-103">Bir işlevdeki yerel değişkenlere ve bağımsız değişkenlere bir Numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="5252e-103">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5252e-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="5252e-104">Methods</span></span>  
  
|<span data-ttu-id="5252e-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="5252e-105">Method</span></span>|<span data-ttu-id="5252e-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5252e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5252e-107">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5252e-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md)|<span data-ttu-id="5252e-108">Bir işlevdeki yerel değişkenler ve bağımsız değişkenler hakkında bilgi içeren, belirtilen [ıcordebugvariablehome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) örneği sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="5252e-108">Gets the specified number of [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instances that contain information about the local variables and arguments in a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5252e-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5252e-109">Remarks</span></span>  
 <span data-ttu-id="5252e-110">`ICorDebugVariableHomeEnum` arabirimi ıcorı, Genum arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="5252e-110">The `ICorDebugVariableHomeEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="5252e-111">[ICorDebugCode4:: enumeratevariableevler](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-enumeratevariablehomes-method.md) yöntemi çağırarak [ıcordebugvariablehome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) örnekleriyle birlikte `ICorDebugVariableHomeEnum` bir örnek doldurulur.</span><span class="sxs-lookup"><span data-stu-id="5252e-111">An `ICorDebugVariableHomeEnum` instance is populated with [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instances by calling the [ICorDebugCode4::EnumerateVariableHomes](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-enumeratevariablehomes-method.md) method.</span></span> <span data-ttu-id="5252e-112">Koleksiyondaki her [ıcordebugvariablehome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) örneği, bir işlevdeki yerel bir değişkeni veya bağımsız değişkeni temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5252e-112">Each [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance in the collection represents a local variable or argument in a function.</span></span> <span data-ttu-id="5252e-113">Koleksiyondaki [ıcordebugvariableana](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) nesneleri [ıcordebugvariablehomeenum:: Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) yöntemi çağırarak listelenebilir.</span><span class="sxs-lookup"><span data-stu-id="5252e-113">The  [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objects in the collection can be enumerated by calling the [ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5252e-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5252e-114">Requirements</span></span>  
 <span data-ttu-id="5252e-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5252e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5252e-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5252e-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5252e-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5252e-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5252e-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5252e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5252e-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5252e-119">See also</span></span>

- [<span data-ttu-id="5252e-120">ICorDebugVariableHome Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5252e-120">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
- [<span data-ttu-id="5252e-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5252e-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

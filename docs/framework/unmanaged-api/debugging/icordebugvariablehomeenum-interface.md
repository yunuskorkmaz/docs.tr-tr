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
ms.openlocfilehash: 8e8caad9f0fc60121dbd1c738a6024da3e4d02f6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726008"
---
# <a name="icordebugvariablehomeenum-interface"></a><span data-ttu-id="4f5a7-102">ICorDebugVariableHomeEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4f5a7-102">ICorDebugVariableHomeEnum Interface</span></span>

<span data-ttu-id="4f5a7-103">Bir işlevdeki yerel değişkenlere ve bağımsız değişkenlere bir Numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="4f5a7-103">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4f5a7-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4f5a7-104">Methods</span></span>  
  
|<span data-ttu-id="4f5a7-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="4f5a7-105">Method</span></span>|<span data-ttu-id="4f5a7-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4f5a7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4f5a7-107">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4f5a7-107">Next Method</span></span>](icordebugvariablehomeenum-next-method.md)|<span data-ttu-id="4f5a7-108">Bir işlevdeki yerel değişkenler ve bağımsız değişkenler hakkında bilgi içeren, belirtilen [ıcordebugvariablehome](icordebugvariablehome-interface.md) örneği sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="4f5a7-108">Gets the specified number of [ICorDebugVariableHome](icordebugvariablehome-interface.md) instances that contain information about the local variables and arguments in a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4f5a7-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4f5a7-109">Remarks</span></span>  

 <span data-ttu-id="4f5a7-110">`ICorDebugVariableHomeEnum`Arabirim ıcorı, Genum arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="4f5a7-110">The `ICorDebugVariableHomeEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="4f5a7-111">`ICorDebugVariableHomeEnum` [ICorDebugCode4:: enumeratevariableevler](icordebugcode4-enumeratevariablehomes-method.md) yöntemi çağırarak bir örnek [ıcordebugvariablehome](icordebugvariablehome-interface.md) örnekleriyle doldurulur.</span><span class="sxs-lookup"><span data-stu-id="4f5a7-111">An `ICorDebugVariableHomeEnum` instance is populated with [ICorDebugVariableHome](icordebugvariablehome-interface.md) instances by calling the [ICorDebugCode4::EnumerateVariableHomes](icordebugcode4-enumeratevariablehomes-method.md) method.</span></span> <span data-ttu-id="4f5a7-112">Koleksiyondaki her [ıcordebugvariablehome](icordebugvariablehome-interface.md) örneği, bir işlevdeki yerel bir değişkeni veya bağımsız değişkeni temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4f5a7-112">Each [ICorDebugVariableHome](icordebugvariablehome-interface.md) instance in the collection represents a local variable or argument in a function.</span></span> <span data-ttu-id="4f5a7-113">Koleksiyondaki  [ıcordebugvariableana](icordebugvariablehome-interface.md) nesneleri [ıcordebugvariablehomeenum:: Next](icordebugvariablehomeenum-next-method.md) yöntemi çağırarak listelenebilir.</span><span class="sxs-lookup"><span data-stu-id="4f5a7-113">The  [ICorDebugVariableHome](icordebugvariablehome-interface.md) objects in the collection can be enumerated by calling the [ICorDebugVariableHomeEnum::Next](icordebugvariablehomeenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f5a7-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4f5a7-114">Requirements</span></span>  

 <span data-ttu-id="4f5a7-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f5a7-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f5a7-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4f5a7-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4f5a7-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="4f5a7-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4f5a7-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f5a7-118">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f5a7-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4f5a7-119">See also</span></span>

- [<span data-ttu-id="4f5a7-120">ICorDebugVariableHome Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4f5a7-120">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
- [<span data-ttu-id="4f5a7-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4f5a7-121">Debugging Interfaces</span></span>](debugging-interfaces.md)

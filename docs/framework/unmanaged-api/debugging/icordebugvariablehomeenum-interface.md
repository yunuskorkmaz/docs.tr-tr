---
description: ': Icordebugvariablehomeenum arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: c56c68a6b5f9d329fe8af23f47b40fa629bfe3ba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790626"
---
# <a name="icordebugvariablehomeenum-interface"></a><span data-ttu-id="0c7b5-103">ICorDebugVariableHomeEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0c7b5-103">ICorDebugVariableHomeEnum Interface</span></span>

<span data-ttu-id="0c7b5-104">Bir işlevdeki yerel değişkenlere ve bağımsız değişkenlere bir Numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="0c7b5-104">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0c7b5-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="0c7b5-105">Methods</span></span>  
  
|<span data-ttu-id="0c7b5-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="0c7b5-106">Method</span></span>|<span data-ttu-id="0c7b5-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0c7b5-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0c7b5-108">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0c7b5-108">Next Method</span></span>](icordebugvariablehomeenum-next-method.md)|<span data-ttu-id="0c7b5-109">Bir işlevdeki yerel değişkenler ve bağımsız değişkenler hakkında bilgi içeren, belirtilen [ıcordebugvariablehome](icordebugvariablehome-interface.md) örneği sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="0c7b5-109">Gets the specified number of [ICorDebugVariableHome](icordebugvariablehome-interface.md) instances that contain information about the local variables and arguments in a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0c7b5-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0c7b5-110">Remarks</span></span>  

 <span data-ttu-id="0c7b5-111">`ICorDebugVariableHomeEnum`Arabirim ıcorı, Genum arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="0c7b5-111">The `ICorDebugVariableHomeEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="0c7b5-112">`ICorDebugVariableHomeEnum` [ICorDebugCode4:: enumeratevariableevler](icordebugcode4-enumeratevariablehomes-method.md) yöntemi çağırarak bir örnek [ıcordebugvariablehome](icordebugvariablehome-interface.md) örnekleriyle doldurulur.</span><span class="sxs-lookup"><span data-stu-id="0c7b5-112">An `ICorDebugVariableHomeEnum` instance is populated with [ICorDebugVariableHome](icordebugvariablehome-interface.md) instances by calling the [ICorDebugCode4::EnumerateVariableHomes](icordebugcode4-enumeratevariablehomes-method.md) method.</span></span> <span data-ttu-id="0c7b5-113">Koleksiyondaki her [ıcordebugvariablehome](icordebugvariablehome-interface.md) örneği, bir işlevdeki yerel bir değişkeni veya bağımsız değişkeni temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0c7b5-113">Each [ICorDebugVariableHome](icordebugvariablehome-interface.md) instance in the collection represents a local variable or argument in a function.</span></span> <span data-ttu-id="0c7b5-114">Koleksiyondaki  [ıcordebugvariableana](icordebugvariablehome-interface.md) nesneleri [ıcordebugvariablehomeenum:: Next](icordebugvariablehomeenum-next-method.md) yöntemi çağırarak listelenebilir.</span><span class="sxs-lookup"><span data-stu-id="0c7b5-114">The  [ICorDebugVariableHome](icordebugvariablehome-interface.md) objects in the collection can be enumerated by calling the [ICorDebugVariableHomeEnum::Next](icordebugvariablehomeenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c7b5-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0c7b5-115">Requirements</span></span>  

 <span data-ttu-id="0c7b5-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c7b5-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c7b5-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0c7b5-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0c7b5-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0c7b5-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0c7b5-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c7b5-119">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c7b5-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0c7b5-120">See also</span></span>

- [<span data-ttu-id="0c7b5-121">ICorDebugVariableHome Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0c7b5-121">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
- [<span data-ttu-id="0c7b5-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0c7b5-122">Debugging Interfaces</span></span>](debugging-interfaces.md)

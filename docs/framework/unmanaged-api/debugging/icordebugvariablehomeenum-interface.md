---
title: Icordebugvariablehomeenum arabirimi
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 43f63e09c654c7aab9f1da0db7587a92bee4fb79
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54632042"
---
# <a name="icordebugvariablehomeenum-interface"></a><span data-ttu-id="36c13-102">Icordebugvariablehomeenum arabirimi</span><span class="sxs-lookup"><span data-stu-id="36c13-102">ICorDebugVariableHomeEnum Interface</span></span>
<span data-ttu-id="36c13-103">Bir işlevdeki bağımsız değişkenler ve yerel değişkenler için bir numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="36c13-103">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="36c13-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="36c13-104">Methods</span></span>  
  
|<span data-ttu-id="36c13-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="36c13-105">Method</span></span>|<span data-ttu-id="36c13-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="36c13-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="36c13-107">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="36c13-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md)|<span data-ttu-id="36c13-108">Belirtilen sayıda alır [Icordebugvariablehome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) örnekleriyle yerel değişkenleri ve bir işlevdeki bağımsız değişkenler hakkındaki bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="36c13-108">Gets the specified number of [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instances that contain information about the local variables and arguments in a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="36c13-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="36c13-109">Remarks</span></span>  
 <span data-ttu-id="36c13-110">`ICorDebugVariableHomeEnum` Arabirimi uygulayan Icordebugenum arabirimi.</span><span class="sxs-lookup"><span data-stu-id="36c13-110">The `ICorDebugVariableHomeEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="36c13-111">Bir `ICorDebugVariableHomeEnum` örneği ile doldurulur [Icordebugvariablehome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) çağırarak örnekleri [ICorDebugCode4::EnumerateVariableHomes](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-enumeratevariablehomes-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="36c13-111">An `ICorDebugVariableHomeEnum` instance is populated with [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instances by calling the [ICorDebugCode4::EnumerateVariableHomes](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-enumeratevariablehomes-method.md) method.</span></span> <span data-ttu-id="36c13-112">Her [Icordebugvariablehome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) koleksiyondaki örneği yerel bir değişken veya işlev bağımsız değişkeni temsil eder.</span><span class="sxs-lookup"><span data-stu-id="36c13-112">Each [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance in the collection represents a local variable or argument in a function.</span></span> <span data-ttu-id="36c13-113">[Icordebugvariablehome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) koleksiyonundaki nesneleri numaralandırılan çağırarak [ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="36c13-113">The  [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objects in the collection can be enumerated by calling the [ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36c13-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="36c13-114">Requirements</span></span>  
 <span data-ttu-id="36c13-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36c13-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36c13-116">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="36c13-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="36c13-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="36c13-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="36c13-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36c13-118">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36c13-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="36c13-119">See also</span></span>
- [<span data-ttu-id="36c13-120">ICorDebugVariableHome Arabirimi</span><span class="sxs-lookup"><span data-stu-id="36c13-120">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
- [<span data-ttu-id="36c13-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="36c13-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

---
title: ICorDebugVariableHomeEnum arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a33420d50a964479c74a59bf5b7cc0da320aee04
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvariablehomeenum-interface"></a><span data-ttu-id="9e63c-102">ICorDebugVariableHomeEnum arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e63c-102">ICorDebugVariableHomeEnum Interface</span></span>
<span data-ttu-id="9e63c-103">Yerel değişkenleri ve bir işlev bağımsız değişkenleri için bir numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e63c-103">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9e63c-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="9e63c-104">Methods</span></span>  
  
|<span data-ttu-id="9e63c-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="9e63c-105">Method</span></span>|<span data-ttu-id="9e63c-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9e63c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9e63c-107">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9e63c-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md)|<span data-ttu-id="9e63c-108">Belirtilen sayıda alır [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) yerel değişkenleri ve bir işlev bağımsız değişkenleri hakkında bilgi içeren örnekleri.</span><span class="sxs-lookup"><span data-stu-id="9e63c-108">Gets the specified number of [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instances that contain information about the local variables and arguments in a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e63c-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9e63c-109">Remarks</span></span>  
 <span data-ttu-id="9e63c-110">`ICorDebugVariableHomeEnum` Arabirimini uygulayan Icordebugenum arabirimi.</span><span class="sxs-lookup"><span data-stu-id="9e63c-110">The `ICorDebugVariableHomeEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="9e63c-111">Bir `ICorDebugVariableHomeEnum` örneği ile doldurulur [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) çağırarak örnekleri [ICorDebugCode4::EnumerateVariableHomes](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-enumeratevariablehomes-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9e63c-111">An `ICorDebugVariableHomeEnum` instance is populated with [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instances by calling the [ICorDebugCode4::EnumerateVariableHomes](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-enumeratevariablehomes-method.md) method.</span></span> <span data-ttu-id="9e63c-112">Her [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) örneği koleksiyonda bir yerel değişken veya işlev bağımsız değişkeni temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9e63c-112">Each [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance in the collection represents a local variable or argument in a function.</span></span> <span data-ttu-id="9e63c-113">[ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) koleksiyonundaki nesneleri numaralandırılan çağırarak [ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9e63c-113">The  [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objects in the collection can be enumerated by calling the [ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e63c-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9e63c-114">Requirements</span></span>  
 <span data-ttu-id="9e63c-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e63c-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e63c-116">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9e63c-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9e63c-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9e63c-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9e63c-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e63c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e63c-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9e63c-119">See Also</span></span>  
 [<span data-ttu-id="9e63c-120">ICorDebugVariableHome Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e63c-120">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)  
 [<span data-ttu-id="9e63c-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9e63c-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

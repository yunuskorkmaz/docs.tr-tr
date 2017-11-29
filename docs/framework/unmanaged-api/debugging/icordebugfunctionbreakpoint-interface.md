---
title: Icordebugfunctionbreakpoint Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunctionBreakpoint
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunctionBreakpoint
helpviewer_keywords: ICorDebugFunctionBreakpoint interface [.NET Framework debugging]
ms.assetid: 9c149303-14b1-4138-83d7-e8c3e0fcd332
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 910317bea8af3a80ee66544651de2372808734bb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugfunctionbreakpoint-interface1"></a><span data-ttu-id="d7fee-102">Icordebugfunctionbreakpoint Interface1</span><span class="sxs-lookup"><span data-stu-id="d7fee-102">ICorDebugFunctionBreakpoint Interface1</span></span>
<span data-ttu-id="d7fee-103">Kesme noktaları işlevler içinde desteklemek için Icordebugbreakpoint arabirimi genişletir.</span><span class="sxs-lookup"><span data-stu-id="d7fee-103">Extends the ICorDebugBreakpoint interface to support breakpoints within functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d7fee-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d7fee-104">Methods</span></span>  
  
|<span data-ttu-id="d7fee-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d7fee-105">Method</span></span>|<span data-ttu-id="d7fee-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d7fee-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d7fee-107">GetFunction yöntemi</span><span class="sxs-lookup"><span data-stu-id="d7fee-107">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-getfunction-method.md)|<span data-ttu-id="d7fee-108">Arabirim işaretçisi kesme ayarlanmış işlevi başvuruda bulunan bir ICorDebugFunction alır.</span><span class="sxs-lookup"><span data-stu-id="d7fee-108">Gets an interface pointer to an ICorDebugFunction that references the function in which the breakpoint is set.</span></span>|  
|[<span data-ttu-id="d7fee-109">GetOffset yöntemi</span><span class="sxs-lookup"><span data-stu-id="d7fee-109">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-getoffset-method.md)|<span data-ttu-id="d7fee-110">İşlevin içinden kesme uzaklığını alır.</span><span class="sxs-lookup"><span data-stu-id="d7fee-110">Gets the offset of the breakpoint within the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d7fee-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d7fee-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d7fee-112">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="d7fee-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7fee-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d7fee-113">Requirements</span></span>  
 <span data-ttu-id="d7fee-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7fee-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7fee-115">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d7fee-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d7fee-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d7fee-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7fee-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7fee-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7fee-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d7fee-118">See Also</span></span>  
 [<span data-ttu-id="d7fee-119">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d7fee-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

---
title: ICorDebugFunctionBreakpoint Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugFunctionBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunctionBreakpoint
helpviewer_keywords:
- ICorDebugFunctionBreakpoint interface [.NET Framework debugging]
ms.assetid: 9c149303-14b1-4138-83d7-e8c3e0fcd332
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0f15b9f5961699f905e765426576bdf6f3416793
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61651655"
---
# <a name="icordebugfunctionbreakpoint-interface"></a><span data-ttu-id="4fca0-102">ICorDebugFunctionBreakpoint Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4fca0-102">ICorDebugFunctionBreakpoint Interface</span></span>

<span data-ttu-id="4fca0-103">İşlevlerdeki kesme noktalarını desteklemek için Icordebugbreakpoint arabirimi genişletir.</span><span class="sxs-lookup"><span data-stu-id="4fca0-103">Extends the ICorDebugBreakpoint interface to support breakpoints within functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4fca0-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4fca0-104">Methods</span></span>  
  
|<span data-ttu-id="4fca0-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="4fca0-105">Method</span></span>|<span data-ttu-id="4fca0-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4fca0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4fca0-107">GetFunction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4fca0-107">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-getfunction-method.md)|<span data-ttu-id="4fca0-108">Bir arabirim işaretçisini, Kesme noktasının ayarlandığını işlevi başvuran bir ICorDebugFunction alır.</span><span class="sxs-lookup"><span data-stu-id="4fca0-108">Gets an interface pointer to an ICorDebugFunction that references the function in which the breakpoint is set.</span></span>|  
|[<span data-ttu-id="4fca0-109">GetOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4fca0-109">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-getoffset-method.md)|<span data-ttu-id="4fca0-110">İşlev içinde kesme noktasının uzaklığını alır.</span><span class="sxs-lookup"><span data-stu-id="4fca0-110">Gets the offset of the breakpoint within the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4fca0-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4fca0-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4fca0-112">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="4fca0-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4fca0-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4fca0-113">Requirements</span></span>  
 <span data-ttu-id="4fca0-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4fca0-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fca0-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4fca0-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4fca0-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4fca0-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4fca0-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4fca0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fca0-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4fca0-118">See also</span></span>

- [<span data-ttu-id="4fca0-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4fca0-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

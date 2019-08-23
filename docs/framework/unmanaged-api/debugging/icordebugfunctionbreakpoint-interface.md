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
ms.openlocfilehash: ed09b4f9be71c7f85714b9ee26d45018410fda42
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917072"
---
# <a name="icordebugfunctionbreakpoint-interface"></a><span data-ttu-id="79874-102">ICorDebugFunctionBreakpoint Arabirimi</span><span class="sxs-lookup"><span data-stu-id="79874-102">ICorDebugFunctionBreakpoint Interface</span></span>

<span data-ttu-id="79874-103">İşlevlerdeki kesme noktalarını desteklemek için ICorDebugBreakpoint arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="79874-103">Extends the ICorDebugBreakpoint interface to support breakpoints within functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="79874-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="79874-104">Methods</span></span>  
  
|<span data-ttu-id="79874-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="79874-105">Method</span></span>|<span data-ttu-id="79874-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="79874-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="79874-107">GetFunction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="79874-107">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-getfunction-method.md)|<span data-ttu-id="79874-108">Kesme noktasının ayarlandığı işleve başvuran bir ICorDebugFunction için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="79874-108">Gets an interface pointer to an ICorDebugFunction that references the function in which the breakpoint is set.</span></span>|  
|[<span data-ttu-id="79874-109">GetOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="79874-109">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-getoffset-method.md)|<span data-ttu-id="79874-110">İşlev içindeki kesme noktasının konumunu alır.</span><span class="sxs-lookup"><span data-stu-id="79874-110">Gets the offset of the breakpoint within the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="79874-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="79874-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="79874-112">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="79874-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79874-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="79874-113">Requirements</span></span>  
 <span data-ttu-id="79874-114">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79874-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79874-115">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="79874-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="79874-116">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="79874-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="79874-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79874-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79874-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="79874-118">See also</span></span>

- [<span data-ttu-id="79874-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="79874-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

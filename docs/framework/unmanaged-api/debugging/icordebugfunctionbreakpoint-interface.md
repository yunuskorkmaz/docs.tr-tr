---
description: ': ICorDebugFunctionBreakpoint Arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 5d7597369241272d91de4b94a60d787304dc1c6e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661135"
---
# <a name="icordebugfunctionbreakpoint-interface"></a><span data-ttu-id="a454e-103">ICorDebugFunctionBreakpoint Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a454e-103">ICorDebugFunctionBreakpoint Interface</span></span>

<span data-ttu-id="a454e-104">İşlevlerdeki kesme noktalarını desteklemek için ICorDebugBreakpoint arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="a454e-104">Extends the ICorDebugBreakpoint interface to support breakpoints within functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a454e-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a454e-105">Methods</span></span>  
  
|<span data-ttu-id="a454e-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="a454e-106">Method</span></span>|<span data-ttu-id="a454e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a454e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a454e-108">GetFunction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a454e-108">GetFunction Method</span></span>](icordebugfunctionbreakpoint-getfunction-method.md)|<span data-ttu-id="a454e-109">Kesme noktasının ayarlandığı işleve başvuran bir ICorDebugFunction için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="a454e-109">Gets an interface pointer to an ICorDebugFunction that references the function in which the breakpoint is set.</span></span>|  
|[<span data-ttu-id="a454e-110">GetOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a454e-110">GetOffset Method</span></span>](icordebugfunctionbreakpoint-getoffset-method.md)|<span data-ttu-id="a454e-111">İşlev içindeki kesme noktasının konumunu alır.</span><span class="sxs-lookup"><span data-stu-id="a454e-111">Gets the offset of the breakpoint within the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a454e-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a454e-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a454e-113">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="a454e-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a454e-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a454e-114">Requirements</span></span>  

 <span data-ttu-id="a454e-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a454e-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a454e-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a454e-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a454e-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a454e-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a454e-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a454e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a454e-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a454e-119">See also</span></span>

- [<span data-ttu-id="a454e-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a454e-120">Debugging Interfaces</span></span>](debugging-interfaces.md)

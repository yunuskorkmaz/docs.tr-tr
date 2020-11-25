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
ms.openlocfilehash: 0f1e6bbdf16c953b0dd22d9dfa44bc3585f1269e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726255"
---
# <a name="icordebugfunctionbreakpoint-interface"></a><span data-ttu-id="75bf2-102">ICorDebugFunctionBreakpoint Arabirimi</span><span class="sxs-lookup"><span data-stu-id="75bf2-102">ICorDebugFunctionBreakpoint Interface</span></span>

<span data-ttu-id="75bf2-103">İşlevlerdeki kesme noktalarını desteklemek için ICorDebugBreakpoint arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="75bf2-103">Extends the ICorDebugBreakpoint interface to support breakpoints within functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="75bf2-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="75bf2-104">Methods</span></span>  
  
|<span data-ttu-id="75bf2-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="75bf2-105">Method</span></span>|<span data-ttu-id="75bf2-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="75bf2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="75bf2-107">GetFunction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="75bf2-107">GetFunction Method</span></span>](icordebugfunctionbreakpoint-getfunction-method.md)|<span data-ttu-id="75bf2-108">Kesme noktasının ayarlandığı işleve başvuran bir ICorDebugFunction için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="75bf2-108">Gets an interface pointer to an ICorDebugFunction that references the function in which the breakpoint is set.</span></span>|  
|[<span data-ttu-id="75bf2-109">GetOffset Metodu</span><span class="sxs-lookup"><span data-stu-id="75bf2-109">GetOffset Method</span></span>](icordebugfunctionbreakpoint-getoffset-method.md)|<span data-ttu-id="75bf2-110">İşlev içindeki kesme noktasının konumunu alır.</span><span class="sxs-lookup"><span data-stu-id="75bf2-110">Gets the offset of the breakpoint within the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="75bf2-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="75bf2-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="75bf2-112">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="75bf2-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75bf2-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="75bf2-113">Requirements</span></span>  

 <span data-ttu-id="75bf2-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75bf2-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75bf2-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="75bf2-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="75bf2-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="75bf2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="75bf2-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75bf2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75bf2-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="75bf2-118">See also</span></span>

- [<span data-ttu-id="75bf2-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="75bf2-119">Debugging Interfaces</span></span>](debugging-interfaces.md)

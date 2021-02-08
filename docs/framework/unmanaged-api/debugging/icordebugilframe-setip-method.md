---
description: ': ICorDebugILFrame:: SetIP metodu hakkında daha fazla bilgi edinin'
title: ICorDebugILFrame::SetIP Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.SetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::SetIP
helpviewer_keywords:
- SetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::SetIP method [.NET Framework debugging]
ms.assetid: 23f38dc1-85e4-4263-9235-2d05bbb6a833
topic_type:
- apiref
ms.openlocfilehash: 75d2530a3d9151c64980316757074141776a78d3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791328"
---
# <a name="icordebugilframesetip-method"></a><span data-ttu-id="253fe-103">ICorDebugILFrame::SetIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="253fe-103">ICorDebugILFrame::SetIP Method</span></span>

<span data-ttu-id="253fe-104">Yönerge işaretçisini, Microsoft ara dili (MSIL) kodunda belirtilen konum konumunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="253fe-104">Sets the instruction pointer to the specified offset location in the Microsoft intermediate language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="253fe-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="253fe-105">Syntax</span></span>  
  
```cpp  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="253fe-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="253fe-106">Parameters</span></span>  

 `nOffset`  
 <span data-ttu-id="253fe-107">MSIL kodunda konum konumu.</span><span class="sxs-lookup"><span data-stu-id="253fe-107">The offset location in the MSIL code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="253fe-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="253fe-108">Remarks</span></span>  

 <span data-ttu-id="253fe-109">`SetIP`Geçerli iş parçacığının tüm çerçevelerini ve zincirlerini hemen geçersiz kılmak için çağrılar.</span><span class="sxs-lookup"><span data-stu-id="253fe-109">Calls to `SetIP` immediately invalidate all frames and chains for the current thread.</span></span> <span data-ttu-id="253fe-110">Hata ayıklayıcı, öğesine yapılan çağrıdan sonra çerçeve bilgisine ihtiyaç duyuyorsa `SetIP` , yeni bir yığın izlemesi gerçekleştirmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="253fe-110">If the debugger needs frame information after a call to `SetIP`, it must perform a new stack trace.</span></span>  
  
 <span data-ttu-id="253fe-111">[ICorDebug](icordebug-interface.md) , yığın çerçevesini geçerli bir durumda tutmaya çalışacak.</span><span class="sxs-lookup"><span data-stu-id="253fe-111">[ICorDebug](icordebug-interface.md) will attempt to keep the stack frame in a valid state.</span></span> <span data-ttu-id="253fe-112">Ancak, çerçeve geçerli bir durumdaysa bile başlatılmamış yerel değişkenler gibi sorunlar olabilir.</span><span class="sxs-lookup"><span data-stu-id="253fe-112">However, even if the frame is in a valid state, there still may be problems such as uninitialized local variables.</span></span> <span data-ttu-id="253fe-113">Çağıran, çalışan programın tutarlılığına ilişkin emin olmanın sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="253fe-113">The caller is responsible for ensuring the coherency of the running program.</span></span>  
  
 <span data-ttu-id="253fe-114">64 bit platformlarda, yönerge işaretçisi bir `catch` veya bloğunun dışına taşınamaz `finally` .</span><span class="sxs-lookup"><span data-stu-id="253fe-114">On 64-bit platforms, the instruction pointer cannot be moved out of a `catch` or `finally` block.</span></span> <span data-ttu-id="253fe-115">`SetIP`Bu tür bir taşımayı 64 bitlik bir platformda yapmak için çağrılırsa, hata belirten BIR hresult döndürür.</span><span class="sxs-lookup"><span data-stu-id="253fe-115">If `SetIP` is called to make such a move on a 64-bit platform, it will return an HRESULT indicating failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="253fe-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="253fe-116">Requirements</span></span>  

 <span data-ttu-id="253fe-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="253fe-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="253fe-118">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="253fe-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="253fe-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="253fe-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="253fe-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="253fe-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

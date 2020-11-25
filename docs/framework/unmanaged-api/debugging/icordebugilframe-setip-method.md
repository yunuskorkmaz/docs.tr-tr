---
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
ms.openlocfilehash: fdc3d96fd5ad9a6ff59b863cd3f0450283ea0146
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721380"
---
# <a name="icordebugilframesetip-method"></a><span data-ttu-id="605df-102">ICorDebugILFrame::SetIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="605df-102">ICorDebugILFrame::SetIP Method</span></span>

<span data-ttu-id="605df-103">Yönerge işaretçisini, Microsoft ara dili (MSIL) kodunda belirtilen konum konumunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="605df-103">Sets the instruction pointer to the specified offset location in the Microsoft intermediate language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="605df-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="605df-104">Syntax</span></span>  
  
```cpp  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="605df-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="605df-105">Parameters</span></span>  

 `nOffset`  
 <span data-ttu-id="605df-106">MSIL kodunda konum konumu.</span><span class="sxs-lookup"><span data-stu-id="605df-106">The offset location in the MSIL code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="605df-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="605df-107">Remarks</span></span>  

 <span data-ttu-id="605df-108">`SetIP`Geçerli iş parçacığının tüm çerçevelerini ve zincirlerini hemen geçersiz kılmak için çağrılar.</span><span class="sxs-lookup"><span data-stu-id="605df-108">Calls to `SetIP` immediately invalidate all frames and chains for the current thread.</span></span> <span data-ttu-id="605df-109">Hata ayıklayıcı, öğesine yapılan çağrıdan sonra çerçeve bilgisine ihtiyaç duyuyorsa `SetIP` , yeni bir yığın izlemesi gerçekleştirmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="605df-109">If the debugger needs frame information after a call to `SetIP`, it must perform a new stack trace.</span></span>  
  
 <span data-ttu-id="605df-110">[ICorDebug](icordebug-interface.md) , yığın çerçevesini geçerli bir durumda tutmaya çalışacak.</span><span class="sxs-lookup"><span data-stu-id="605df-110">[ICorDebug](icordebug-interface.md) will attempt to keep the stack frame in a valid state.</span></span> <span data-ttu-id="605df-111">Ancak, çerçeve geçerli bir durumdaysa bile başlatılmamış yerel değişkenler gibi sorunlar olabilir.</span><span class="sxs-lookup"><span data-stu-id="605df-111">However, even if the frame is in a valid state, there still may be problems such as uninitialized local variables.</span></span> <span data-ttu-id="605df-112">Çağıran, çalışan programın tutarlılığına ilişkin emin olmanın sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="605df-112">The caller is responsible for ensuring the coherency of the running program.</span></span>  
  
 <span data-ttu-id="605df-113">64 bit platformlarda, yönerge işaretçisi bir `catch` veya bloğunun dışına taşınamaz `finally` .</span><span class="sxs-lookup"><span data-stu-id="605df-113">On 64-bit platforms, the instruction pointer cannot be moved out of a `catch` or `finally` block.</span></span> <span data-ttu-id="605df-114">`SetIP`Bu tür bir taşımayı 64 bitlik bir platformda yapmak için çağrılırsa, hata belirten BIR hresult döndürür.</span><span class="sxs-lookup"><span data-stu-id="605df-114">If `SetIP` is called to make such a move on a 64-bit platform, it will return an HRESULT indicating failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="605df-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="605df-115">Requirements</span></span>  

 <span data-ttu-id="605df-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="605df-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="605df-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="605df-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="605df-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="605df-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="605df-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="605df-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

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
ms.openlocfilehash: 60273d7cf91be04c5fc3041260e4bb146ce9a45e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73095427"
---
# <a name="icordebugilframesetip-method"></a><span data-ttu-id="2ddd7-102">ICorDebugILFrame::SetIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2ddd7-102">ICorDebugILFrame::SetIP Method</span></span>
<span data-ttu-id="2ddd7-103">Yönerge işaretçisini, Microsoft ara dili (MSIL) kodunda belirtilen konum konumunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="2ddd7-103">Sets the instruction pointer to the specified offset location in the Microsoft intermediate language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ddd7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2ddd7-104">Syntax</span></span>  
  
```cpp  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ddd7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2ddd7-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="2ddd7-106">MSIL kodunda konum konumu.</span><span class="sxs-lookup"><span data-stu-id="2ddd7-106">The offset location in the MSIL code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ddd7-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2ddd7-107">Remarks</span></span>  
 <span data-ttu-id="2ddd7-108">`SetIP` çağrıları, geçerli iş parçacığı için tüm çerçeveleri ve zincirleri hemen geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="2ddd7-108">Calls to `SetIP` immediately invalidate all frames and chains for the current thread.</span></span> <span data-ttu-id="2ddd7-109">Hata ayıklayıcı `SetIP`çağrısından sonra çerçeve bilgilerine ihtiyaç duyuyorsa, yeni bir yığın izlemesi gerçekleştirmelidir.</span><span class="sxs-lookup"><span data-stu-id="2ddd7-109">If the debugger needs frame information after a call to `SetIP`, it must perform a new stack trace.</span></span>  
  
 <span data-ttu-id="2ddd7-110">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) , yığın çerçevesini geçerli bir durumda tutmaya çalışacak.</span><span class="sxs-lookup"><span data-stu-id="2ddd7-110">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) will attempt to keep the stack frame in a valid state.</span></span> <span data-ttu-id="2ddd7-111">Ancak, çerçeve geçerli bir durumdaysa bile başlatılmamış yerel değişkenler gibi sorunlar olabilir.</span><span class="sxs-lookup"><span data-stu-id="2ddd7-111">However, even if the frame is in a valid state, there still may be problems such as uninitialized local variables.</span></span> <span data-ttu-id="2ddd7-112">Çağıran, çalışan programın tutarlılığına ilişkin emin olmanın sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="2ddd7-112">The caller is responsible for ensuring the coherency of the running program.</span></span>  
  
 <span data-ttu-id="2ddd7-113">64 bit platformlarda, yönerge işaretçisi bir `catch` veya `finally` bloğunun dışına taşınamaz.</span><span class="sxs-lookup"><span data-stu-id="2ddd7-113">On 64-bit platforms, the instruction pointer cannot be moved out of a `catch` or `finally` block.</span></span> <span data-ttu-id="2ddd7-114">`SetIP`, 64 bitlik bir platformda böyle bir geçiş yapmak için çağrılırsa, hata belirten bir HRESULT döndürür.</span><span class="sxs-lookup"><span data-stu-id="2ddd7-114">If `SetIP` is called to make such a move on a 64-bit platform, it will return an HRESULT indicating failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ddd7-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2ddd7-115">Requirements</span></span>  
 <span data-ttu-id="2ddd7-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ddd7-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ddd7-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2ddd7-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2ddd7-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2ddd7-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2ddd7-119">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ddd7-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

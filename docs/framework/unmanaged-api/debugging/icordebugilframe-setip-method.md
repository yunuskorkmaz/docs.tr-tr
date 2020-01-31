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
ms.openlocfilehash: 466fe421f4ff3f8983159ccb38503b75551c87bd
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788551"
---
# <a name="icordebugilframesetip-method"></a><span data-ttu-id="35045-102">ICorDebugILFrame::SetIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="35045-102">ICorDebugILFrame::SetIP Method</span></span>
<span data-ttu-id="35045-103">Yönerge işaretçisini, Microsoft ara dili (MSIL) kodunda belirtilen konum konumunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="35045-103">Sets the instruction pointer to the specified offset location in the Microsoft intermediate language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35045-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="35045-104">Syntax</span></span>  
  
```cpp  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="35045-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="35045-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="35045-106">MSIL kodunda konum konumu.</span><span class="sxs-lookup"><span data-stu-id="35045-106">The offset location in the MSIL code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="35045-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="35045-107">Remarks</span></span>  
 <span data-ttu-id="35045-108">`SetIP` çağrıları, geçerli iş parçacığı için tüm çerçeveleri ve zincirleri hemen geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="35045-108">Calls to `SetIP` immediately invalidate all frames and chains for the current thread.</span></span> <span data-ttu-id="35045-109">Hata ayıklayıcı `SetIP`çağrısından sonra çerçeve bilgilerine ihtiyaç duyuyorsa, yeni bir yığın izlemesi gerçekleştirmelidir.</span><span class="sxs-lookup"><span data-stu-id="35045-109">If the debugger needs frame information after a call to `SetIP`, it must perform a new stack trace.</span></span>  
  
 <span data-ttu-id="35045-110">[ICorDebug](icordebug-interface.md) , yığın çerçevesini geçerli bir durumda tutmaya çalışacak.</span><span class="sxs-lookup"><span data-stu-id="35045-110">[ICorDebug](icordebug-interface.md) will attempt to keep the stack frame in a valid state.</span></span> <span data-ttu-id="35045-111">Ancak, çerçeve geçerli bir durumdaysa bile başlatılmamış yerel değişkenler gibi sorunlar olabilir.</span><span class="sxs-lookup"><span data-stu-id="35045-111">However, even if the frame is in a valid state, there still may be problems such as uninitialized local variables.</span></span> <span data-ttu-id="35045-112">Çağıran, çalışan programın tutarlılığına ilişkin emin olmanın sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="35045-112">The caller is responsible for ensuring the coherency of the running program.</span></span>  
  
 <span data-ttu-id="35045-113">64 bit platformlarda, yönerge işaretçisi bir `catch` veya `finally` bloğunun dışına taşınamaz.</span><span class="sxs-lookup"><span data-stu-id="35045-113">On 64-bit platforms, the instruction pointer cannot be moved out of a `catch` or `finally` block.</span></span> <span data-ttu-id="35045-114">`SetIP`, 64 bitlik bir platformda böyle bir geçiş yapmak için çağrılırsa, hata belirten bir HRESULT döndürür.</span><span class="sxs-lookup"><span data-stu-id="35045-114">If `SetIP` is called to make such a move on a 64-bit platform, it will return an HRESULT indicating failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35045-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="35045-115">Requirements</span></span>  
 <span data-ttu-id="35045-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35045-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35045-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="35045-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="35045-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="35045-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="35045-119">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35045-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a25e52c6b858aaa602ffade0e407b1aaf6e5c67e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471400"
---
# <a name="icordebugilframesetip-method"></a><span data-ttu-id="9526e-102">ICorDebugILFrame::SetIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9526e-102">ICorDebugILFrame::SetIP Method</span></span>
<span data-ttu-id="9526e-103">Microsoft Ara dil (MSIL) kodu belirtilen uzaklık konuma yönerge işaretçisini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9526e-103">Sets the instruction pointer to the specified offset location in the Microsoft intermediate language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9526e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9526e-104">Syntax</span></span>  
  
```  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9526e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9526e-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="9526e-106">MSIL kodu uzaklık konumu.</span><span class="sxs-lookup"><span data-stu-id="9526e-106">The offset location in the MSIL code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9526e-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9526e-107">Remarks</span></span>  
 <span data-ttu-id="9526e-108">Çağrılar `SetIP` hemen tüm çerçeveleri ve zincirleri için geçerli iş parçacığı geçersiz.</span><span class="sxs-lookup"><span data-stu-id="9526e-108">Calls to `SetIP` immediately invalidate all frames and chains for the current thread.</span></span> <span data-ttu-id="9526e-109">Hata ayıklayıcı çağrısı yapıldıktan sonra çerçeve bilgileri gerekiyorsa `SetIP`, yeni bir yığın izlemesi gerçekleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9526e-109">If the debugger needs frame information after a call to `SetIP`, it must perform a new stack trace.</span></span>  
  
 <span data-ttu-id="9526e-110">[Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) yığın çerçevesini geçerli bir durumda tutmak çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="9526e-110">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) will attempt to keep the stack frame in a valid state.</span></span> <span data-ttu-id="9526e-111">Ancak, çerçeve geçerli bir durumda olsa bile, yine de olabilir başlatılmamış yerel değişkenler gibi sorunlar.</span><span class="sxs-lookup"><span data-stu-id="9526e-111">However, even if the frame is in a valid state, there still may be problems such as uninitialized local variables.</span></span> <span data-ttu-id="9526e-112">Çağıran, çalışan programa önbelleklerinin sağlamaktan sorumludur.</span><span class="sxs-lookup"><span data-stu-id="9526e-112">The caller is responsible for ensuring the coherency of the running program.</span></span>  
  
 <span data-ttu-id="9526e-113">64-bit platformlarda, yönerge işaretçisini tanesi taşınamaz bir `catch` veya `finally` blok.</span><span class="sxs-lookup"><span data-stu-id="9526e-113">On 64-bit platforms, the instruction pointer cannot be moved out of a `catch` or `finally` block.</span></span> <span data-ttu-id="9526e-114">Varsa `SetIP` çağrılır böyle bir 64-bit platformlarda hareket ettirmek için hata olduğunu gösteren bir HRESULT döndürür.</span><span class="sxs-lookup"><span data-stu-id="9526e-114">If `SetIP` is called to make such a move on a 64-bit platform, it will return an HRESULT indicating failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9526e-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9526e-115">Requirements</span></span>  
 <span data-ttu-id="9526e-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9526e-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9526e-117">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9526e-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9526e-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9526e-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9526e-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9526e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

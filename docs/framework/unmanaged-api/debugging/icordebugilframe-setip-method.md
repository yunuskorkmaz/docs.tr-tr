---
title: "ICorDebugILFrame::SetIP Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame.SetIP
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugILFrame::SetIP
helpviewer_keywords:
- SetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::SetIP method [.NET Framework debugging]
ms.assetid: 23f38dc1-85e4-4263-9235-2d05bbb6a833
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: daffbbd9e961f4fdc7ff2e3c9be57e41e8fa3f78
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframesetip-method"></a><span data-ttu-id="8effe-102">ICorDebugILFrame::SetIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8effe-102">ICorDebugILFrame::SetIP Method</span></span>
<span data-ttu-id="8effe-103">Yönerge işaretçisi Microsoft Ara dili (MSIL) kodda belirtilen uzaklık konumuna ayarlar.</span><span class="sxs-lookup"><span data-stu-id="8effe-103">Sets the instruction pointer to the specified offset location in the Microsoft intermediate language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8effe-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8effe-104">Syntax</span></span>  
  
```  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8effe-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8effe-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="8effe-106">MSIL kodda uzaklık konumu.</span><span class="sxs-lookup"><span data-stu-id="8effe-106">The offset location in the MSIL code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8effe-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8effe-107">Remarks</span></span>  
 <span data-ttu-id="8effe-108">Çağrılar `SetIP` hemen tüm çerçeveler ve zincirleri geçerli iş parçacığı için geçersiz.</span><span class="sxs-lookup"><span data-stu-id="8effe-108">Calls to `SetIP` immediately invalidate all frames and chains for the current thread.</span></span> <span data-ttu-id="8effe-109">Hata ayıklayıcı çerçeve bilgileri yapılan bir çağrı sonra gerekirse `SetIP`, yeni bir yığın izlemesi gerçekleştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="8effe-109">If the debugger needs frame information after a call to `SetIP`, it must perform a new stack trace.</span></span>  
  
 <span data-ttu-id="8effe-110">[Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) yığın çerçevesi geçerli bir durumda tutmak deneyecek.</span><span class="sxs-lookup"><span data-stu-id="8effe-110">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) will attempt to keep the stack frame in a valid state.</span></span> <span data-ttu-id="8effe-111">Ancak, çerçeve geçerli bir durumda olsa bile, yine sorunları olabilir başlatılmayan yerel değişkenlerde gibi.</span><span class="sxs-lookup"><span data-stu-id="8effe-111">However, even if the frame is in a valid state, there still may be problems such as uninitialized local variables.</span></span> <span data-ttu-id="8effe-112">Çağıran, çalışan program önbelleklerinin sağlamak için sorumludur.</span><span class="sxs-lookup"><span data-stu-id="8effe-112">The caller is responsible for ensuring the coherency of the running program.</span></span>  
  
 <span data-ttu-id="8effe-113">64 bit platformlarda dışı yönerge işaretçisi taşınamaz bir `catch` veya `finally` bloğu.</span><span class="sxs-lookup"><span data-stu-id="8effe-113">On 64-bit platforms, the instruction pointer cannot be moved out of a `catch` or `finally` block.</span></span> <span data-ttu-id="8effe-114">Varsa `SetIP` çağrılır böyle bir 64-bit platformu üzerinde hareket ettirmek için hata olduğunu gösteren bir HRESULT döndürür.</span><span class="sxs-lookup"><span data-stu-id="8effe-114">If `SetIP` is called to make such a move on a 64-bit platform, it will return an HRESULT indicating failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8effe-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8effe-115">Requirements</span></span>  
 <span data-ttu-id="8effe-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8effe-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8effe-117">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8effe-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8effe-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8effe-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8effe-119">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8effe-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

---
title: ICorDebugILFrame2::RemapFunction Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame2.RemapFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame2::RemapFunction
helpviewer_keywords:
- ICorDebugILFrame2::RemapFunction method [.NET Framework debugging]
- RemapFunction method [.NET Framework debugging]
ms.assetid: dd639ba0-f77b-426d-9ff6-f92706840348
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bdcc2eccbb24a92643415db8e5d267033ac1ca0a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758754"
---
# <a name="icordebugilframe2remapfunction-method"></a><span data-ttu-id="5ccc6-102">ICorDebugILFrame2::RemapFunction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5ccc6-102">ICorDebugILFrame2::RemapFunction Method</span></span>
<span data-ttu-id="5ccc6-103">Yeni Microsoft Ara dili (MSIL) uzaklık belirterek düzenlenmiş bir işlevi yeniden eşlemesi</span><span class="sxs-lookup"><span data-stu-id="5ccc6-103">Remaps an edited function by specifying the new Microsoft intermediate language (MSIL) offset</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ccc6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5ccc6-104">Syntax</span></span>  
  
```cpp  
HRESULT RemapFunction (  
    [in] ULONG32      newILOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5ccc6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5ccc6-105">Parameters</span></span>  
 `newILOffset`  
 <span data-ttu-id="5ccc6-106">[in] Yönerge işaretçisi yerleştirilmesi gereken yığın çerçeve yeni MSIL uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="5ccc6-106">[in] The stack frame's new MSIL offset at which the instruction pointer should be placed.</span></span> <span data-ttu-id="5ccc6-107">Bu değer bir dizi noktası olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5ccc6-107">This value must be a sequence point.</span></span>  
  
 <span data-ttu-id="5ccc6-108">Bu değerin geçerliliği sağlamak çağrı sahibinin sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="5ccc6-108">It is the caller’s responsibility to ensure the validity of this value.</span></span> <span data-ttu-id="5ccc6-109">Örneğin, MSIL uzaklığı işlevi sınırları dışında olması durumunda geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="5ccc6-109">For example, the MSIL offset is not valid if it is outside the bounds of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5ccc6-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5ccc6-110">Remarks</span></span>  
 <span data-ttu-id="5ccc6-111">Çerçevenin işlevi düzenlendiğini, hata ayıklayıcı çağırabilirsiniz `RemapFunction` yürütülmesi için en son sürümünü çerçeve işlevi takas etmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5ccc6-111">When a frame’s function has been edited, the debugger can call the `RemapFunction` method to swap in the latest version of the frame's function so it can be executed.</span></span> <span data-ttu-id="5ccc6-112">Kod yürütme belirli MSIL uzaklığında başlar.</span><span class="sxs-lookup"><span data-stu-id="5ccc6-112">The code execution will begin at the given MSIL offset.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5ccc6-113">Çağırma `RemapFunction`gibi çağırma [Icordebugılframe::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md), bir iş parçacığı için yığın izlemesi oluşturma ile ilgili tüm hata ayıklama arabirimleri hemen geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="5ccc6-113">Calling `RemapFunction`, like calling [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md), will immediately invalidate all debugging interfaces that are related to generating a stack trace for the thread.</span></span> <span data-ttu-id="5ccc6-114">Bu arabirimler dahil [Icordebugchain](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md), Icordebugılframe Icordebugınternalframe ve Icordebugnativeframe.</span><span class="sxs-lookup"><span data-stu-id="5ccc6-114">These interfaces include [ICorDebugChain](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md), ICorDebugILFrame, ICorDebugInternalFrame, and ICorDebugNativeFrame.</span></span>  
  
 <span data-ttu-id="5ccc6-115">`RemapFunction` Bağlamında geçerli çerçeve yalnızca ve yalnızca aşağıdaki durumlarda birinde yöntemi çağrılabilir:</span><span class="sxs-lookup"><span data-stu-id="5ccc6-115">The `RemapFunction` method can be called only in the context of the current frame, and only in one of the following cases:</span></span>  
  
- <span data-ttu-id="5ccc6-116">Giriş sonra bir [Icordebugmanagedcallback2::functionremapopportunity](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md) değil henüz devam ettirildi geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="5ccc6-116">After receipt of a [ICorDebugManagedCallback2::FunctionRemapOpportunity](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md) callback that has not yet been continued.</span></span>  
  
- <span data-ttu-id="5ccc6-117">Kod yürütme nedeniyle durdurulurken bir [Icordebugmanagedcallback::editandcontinueremap](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-editandcontinueremap-method.md) bu çerçevesi için olay.</span><span class="sxs-lookup"><span data-stu-id="5ccc6-117">While code execution is stopped because of an [ICorDebugManagedCallback::EditAndContinueRemap](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-editandcontinueremap-method.md) event for this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ccc6-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5ccc6-118">Requirements</span></span>  
 <span data-ttu-id="5ccc6-119">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ccc6-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ccc6-120">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5ccc6-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5ccc6-121">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5ccc6-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5ccc6-122">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ccc6-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

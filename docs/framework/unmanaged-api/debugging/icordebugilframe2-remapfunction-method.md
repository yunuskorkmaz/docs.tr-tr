---
description: ': ICorDebugILFrame2:: RemapFunction yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: d8a6c7f966488e7b74a9661e3a18b5248df7400b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791302"
---
# <a name="icordebugilframe2remapfunction-method"></a><span data-ttu-id="d965a-103">ICorDebugILFrame2::RemapFunction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d965a-103">ICorDebugILFrame2::RemapFunction Method</span></span>

<span data-ttu-id="d965a-104">Yeni Microsoft ara dili (MSIL) sapmasını belirterek düzenlenmiş bir işlevi yeniden eşler</span><span class="sxs-lookup"><span data-stu-id="d965a-104">Remaps an edited function by specifying the new Microsoft intermediate language (MSIL) offset</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d965a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d965a-105">Syntax</span></span>  
  
```cpp  
HRESULT RemapFunction (  
    [in] ULONG32      newILOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d965a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d965a-106">Parameters</span></span>  

 `newILOffset`  
 <span data-ttu-id="d965a-107">'ndaki Yığın çerçevesinin, yönerge işaretçisinin yerleştirilmesi gereken yeni MSIL kayması.</span><span class="sxs-lookup"><span data-stu-id="d965a-107">[in] The stack frame's new MSIL offset at which the instruction pointer should be placed.</span></span> <span data-ttu-id="d965a-108">Bu değer bir dizi noktası olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d965a-108">This value must be a sequence point.</span></span>  
  
 <span data-ttu-id="d965a-109">Bu değerin geçerliliğini sağlamak için çağıranın sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="d965a-109">It is the caller’s responsibility to ensure the validity of this value.</span></span> <span data-ttu-id="d965a-110">Örneğin, MSIL boşluğu, işlev sınırlarının dışındaysa geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="d965a-110">For example, the MSIL offset is not valid if it is outside the bounds of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d965a-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d965a-111">Remarks</span></span>  

 <span data-ttu-id="d965a-112">Bir çerçevenin işlevi düzenlendiğinde, hata ayıklayıcı `RemapFunction` çerçeve işlevinin en son sürümünde takas etmek için yöntemini çağırabilir, bu nedenle yürütülür.</span><span class="sxs-lookup"><span data-stu-id="d965a-112">When a frame’s function has been edited, the debugger can call the `RemapFunction` method to swap in the latest version of the frame's function so it can be executed.</span></span> <span data-ttu-id="d965a-113">Kod yürütme, verilen MSIL uzaklığında başlar.</span><span class="sxs-lookup"><span data-stu-id="d965a-113">The code execution will begin at the given MSIL offset.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d965a-114">Çağırma `RemapFunction` , [ICorDebugILFrame:: SetIP](icordebugilframe-setip-method.md)çağırmak gibi, iş parçacığı için yığın izlemesi oluşturma ile ilgili tüm hata ayıklama arabirimlerini hemen geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="d965a-114">Calling `RemapFunction`, like calling [ICorDebugILFrame::SetIP](icordebugilframe-setip-method.md), will immediately invalidate all debugging interfaces that are related to generating a stack trace for the thread.</span></span> <span data-ttu-id="d965a-115">Bu arabirimler [ıcordebugzincirini](icordebugchain-interface.md), ICorDebugILFrame, ICorDebugInternalFrame ve ICorDebugNativeFrame ' i içerir.</span><span class="sxs-lookup"><span data-stu-id="d965a-115">These interfaces include [ICorDebugChain](icordebugchain-interface.md), ICorDebugILFrame, ICorDebugInternalFrame, and ICorDebugNativeFrame.</span></span>  
  
 <span data-ttu-id="d965a-116">`RemapFunction`Yöntemi yalnızca geçerli çerçevenin bağlamında ve yalnızca aşağıdaki durumlardan birinde çağrılabilir:</span><span class="sxs-lookup"><span data-stu-id="d965a-116">The `RemapFunction` method can be called only in the context of the current frame, and only in one of the following cases:</span></span>  
  
- <span data-ttu-id="d965a-117">[ICorDebugManagedCallback2:: FunctionRemapOpportunity](icordebugmanagedcallback2-functionremapopportunity-method.md) geri çağrısının alındıktan sonra henüz devam edilmemiş.</span><span class="sxs-lookup"><span data-stu-id="d965a-117">After receipt of a [ICorDebugManagedCallback2::FunctionRemapOpportunity](icordebugmanagedcallback2-functionremapopportunity-method.md) callback that has not yet been continued.</span></span>  
  
- <span data-ttu-id="d965a-118">Bu çerçeve için [ICorDebugManagedCallback:: EditAndContinueRemap](icordebugmanagedcallback-editandcontinueremap-method.md) olayı nedeniyle kod yürütme işlemi durduruldu.</span><span class="sxs-lookup"><span data-stu-id="d965a-118">While code execution is stopped because of an [ICorDebugManagedCallback::EditAndContinueRemap](icordebugmanagedcallback-editandcontinueremap-method.md) event for this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d965a-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d965a-119">Requirements</span></span>  

 <span data-ttu-id="d965a-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d965a-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d965a-121">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d965a-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d965a-122">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d965a-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d965a-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d965a-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

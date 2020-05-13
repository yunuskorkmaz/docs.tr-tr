---
title: ICorDebugStepperEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugStepperEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepperEnum::Next
helpviewer_keywords:
- Next method, ICorDebugStepperEnum interface [.NET Framework debugging]
- ICorDebugStepperEnum::Next method [.NET Framework debugging]
ms.assetid: d0ea0f30-e8d2-48b0-8477-e1a029ceb4dd
topic_type:
- apiref
ms.openlocfilehash: 293d1a9cd93b5ce45105427e7df864ad8bfbe77a
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379188"
---
# <a name="icordebugstepperenumnext-method"></a><span data-ttu-id="55f4f-102">ICorDebugStepperEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="55f4f-102">ICorDebugStepperEnum::Next Method</span></span>
<span data-ttu-id="55f4f-103">Geçerli konumdan başlayarak Numaralandırmadaki belirtilen ICorDebugStepper örnek sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="55f4f-103">Gets the specified number of ICorDebugStepper instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55f4f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="55f4f-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugStepper *steppers[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="55f4f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="55f4f-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="55f4f-106">'ndaki `ICorDebugStepper`Alınacak örnek sayısı.</span><span class="sxs-lookup"><span data-stu-id="55f4f-106">[in] The number of `ICorDebugStepper` instances to be retrieved.</span></span>  
  
 `steppers`  
 <span data-ttu-id="55f4f-107">dışı Her biri bir nesneye işaret eden işaretçiler dizisi `ICorDebugStepper` .</span><span class="sxs-lookup"><span data-stu-id="55f4f-107">[out] An array of pointers, each of which points to an `ICorDebugStepper` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="55f4f-108">dışı `ICorDebugStepper`Aslında döndürülen örnek sayısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="55f4f-108">[out] Pointer to the number of `ICorDebugStepper` instances actually returned.</span></span> <span data-ttu-id="55f4f-109">Bu değer bir ise null olabilir `celt` .</span><span class="sxs-lookup"><span data-stu-id="55f4f-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55f4f-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="55f4f-110">Requirements</span></span>  
 <span data-ttu-id="55f4f-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55f4f-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55f4f-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="55f4f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="55f4f-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="55f4f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="55f4f-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55f4f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

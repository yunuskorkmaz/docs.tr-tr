---
title: ICorDebugStepper::SetUnmappedStopMask Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.SetUnmappedStopMask
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::SetUnmappedStopMask
helpviewer_keywords:
- ICorDebugStepper::SetUnmappedStopMask method [.NET Framework debugging]
- SetUnmappedStopMask method [.NET Framework debugging]
ms.assetid: b1211981-e90c-4e05-8def-fa18d85ad9ab
topic_type:
- apiref
ms.openlocfilehash: ef458fda8e8b7e75f92a4b3c06eabec106180d23
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379260"
---
# <a name="icordebugsteppersetunmappedstopmask-method"></a><span data-ttu-id="8e4f3-102">ICorDebugStepper::SetUnmappedStopMask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8e4f3-102">ICorDebugStepper::SetUnmappedStopMask Method</span></span>
<span data-ttu-id="8e4f3-103">Yürütmenin durdurmayacak eşlenmemiş kodun türünü belirten bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="8e4f3-103">Sets a value that specifies the type of unmapped code in which execution will halt.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e4f3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8e4f3-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUnmappedStopMask (  
    [in] CorDebugUnmappedStop   mask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8e4f3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8e4f3-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="8e4f3-106">'ndaki Hata ayıklayıcının yürütmeyi durdurulacağı eşlenmemiş kodun türünü belirten CorDebugUnmappedStop numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="8e4f3-106">[in] A value of the CorDebugUnmappedStop enumeration that specifies the type of unmapped code in which the debugger will halt execution.</span></span>  
  
 <span data-ttu-id="8e4f3-107">Varsayılan değer STOP_OTHER_UNMAPPED.</span><span class="sxs-lookup"><span data-stu-id="8e4f3-107">The default value is STOP_OTHER_UNMAPPED.</span></span> <span data-ttu-id="8e4f3-108">STOP_UNMANAGED değeri yalnızca birlikte çalışma hata ayıklaması ile geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="8e4f3-108">The value STOP_UNMANAGED is only valid with interop debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8e4f3-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8e4f3-109">Remarks</span></span>  
 <span data-ttu-id="8e4f3-110">Hata ayıklayıcı, Microsoft ara dili (MSIL) için karşılık gelen hiçbir eşleme olmayan bir tam zamanında (JıT) derleme bulduğunda, bu tür eşlenmemiş kod belirten bayrak ayarlandıysa yürütmeyi halliyorlar. Aksi halde, bu adım saydam olarak devam eder.</span><span class="sxs-lookup"><span data-stu-id="8e4f3-110">When the debugger finds a just-in-time (JIT) compilation that has no corresponding mapping to Microsoft intermediate language (MSIL), it halts execution if the flag specifying that type of unmapped code has been set; otherwise, stepping transparently continues.</span></span>  
  
 <span data-ttu-id="8e4f3-111">Hata ayıklayıcı bir yöntemi girmek için bir Stepper kullanmıyorsa, eşlenmemiş kod üzerinde adım adım değildir.</span><span class="sxs-lookup"><span data-stu-id="8e4f3-111">If the debugger doesn't use a stepper to enter a method, then it won't necessarily step over unmapped code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e4f3-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8e4f3-112">Requirements</span></span>  
 <span data-ttu-id="8e4f3-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e4f3-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e4f3-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8e4f3-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8e4f3-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="8e4f3-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8e4f3-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e4f3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

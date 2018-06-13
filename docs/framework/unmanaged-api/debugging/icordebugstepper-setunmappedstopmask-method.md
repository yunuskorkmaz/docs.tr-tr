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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dc4e51ec60c7526f36bbe4909bec91a527e0862c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419916"
---
# <a name="icordebugsteppersetunmappedstopmask-method"></a><span data-ttu-id="80e10-102">ICorDebugStepper::SetUnmappedStopMask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="80e10-102">ICorDebugStepper::SetUnmappedStopMask Method</span></span>
<span data-ttu-id="80e10-103">İçinde yürütme durdurulur eşlenmemiş kod türünü belirten bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="80e10-103">Sets a value that specifies the type of unmapped code in which execution will halt.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80e10-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="80e10-104">Syntax</span></span>  
  
```  
HRESULT SetUnmappedStopMask (  
    [in] CorDebugUnmappedStop   mask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="80e10-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="80e10-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="80e10-106">[in] Hata ayıklayıcı yürütme durdurulur eşlenmemiş kod türünü belirtir CorDebugUnmappedStop numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="80e10-106">[in] A value of the CorDebugUnmappedStop enumeration that specifies the type of unmapped code in which the debugger will halt execution.</span></span>  
  
 <span data-ttu-id="80e10-107">STOP_OTHER_UNMAPPED varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="80e10-107">The default value is STOP_OTHER_UNMAPPED.</span></span> <span data-ttu-id="80e10-108">STOP_UNMANAGED değeri yalnızca birlikte çalışma hata ayıklamaya geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="80e10-108">The value STOP_UNMANAGED is only valid with interop debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="80e10-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="80e10-109">Remarks</span></span>  
 <span data-ttu-id="80e10-110">Hata ayıklayıcıyı Microsoft Ara dile (MSIL) karşılık gelen hiçbir eşleme sahip bir tam zamanında (JIT) derleme bulduğunda, bu tür bir eşlenmemiş kod belirtme bayrağı ayarlarsanız yürütme durdurur; Aksi takdirde, saydam atlama devam eder.</span><span class="sxs-lookup"><span data-stu-id="80e10-110">When the debugger finds a just-in-time (JIT) compilation that has no corresponding mapping to Microsoft intermediate language (MSIL), it halts execution if the flag specifying that type of unmapped code has been set; otherwise, stepping transparently continues.</span></span>  
  
 <span data-ttu-id="80e10-111">Hata ayıklayıcı, bir yöntem girmek için Adımlayıcı kullanmıyorsa, sonra da mutlaka eşlenmemiş kod adım olmaz.</span><span class="sxs-lookup"><span data-stu-id="80e10-111">If the debugger doesn't use a stepper to enter a method, then it won't necessarily step over unmapped code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80e10-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="80e10-112">Requirements</span></span>  
 <span data-ttu-id="80e10-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80e10-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80e10-114">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="80e10-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="80e10-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="80e10-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="80e10-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80e10-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

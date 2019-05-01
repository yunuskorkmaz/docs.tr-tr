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
ms.openlocfilehash: da799b0d4f4e5e4b281445baa35d95f992ba0b63
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61987460"
---
# <a name="icordebugsteppersetunmappedstopmask-method"></a><span data-ttu-id="0cc27-102">ICorDebugStepper::SetUnmappedStopMask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0cc27-102">ICorDebugStepper::SetUnmappedStopMask Method</span></span>
<span data-ttu-id="0cc27-103">Yürütmeyi durdur eşlenmemiş kodun türünü belirten bir değeri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0cc27-103">Sets a value that specifies the type of unmapped code in which execution will halt.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cc27-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0cc27-104">Syntax</span></span>  
  
```  
HRESULT SetUnmappedStopMask (  
    [in] CorDebugUnmappedStop   mask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0cc27-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0cc27-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="0cc27-106">[in] Hata ayıklayıcı yürütme durdurulur eşlenmemiş kodun türünü belirten CorDebugUnmappedStop sabit listesi değeri.</span><span class="sxs-lookup"><span data-stu-id="0cc27-106">[in] A value of the CorDebugUnmappedStop enumeration that specifies the type of unmapped code in which the debugger will halt execution.</span></span>  
  
 <span data-ttu-id="0cc27-107">STOP_OTHER_UNMAPPED varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="0cc27-107">The default value is STOP_OTHER_UNMAPPED.</span></span> <span data-ttu-id="0cc27-108">' % S'değeri STOP_UNMANAGED yalnızca birlikte çalışma hata ayıklama ile geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="0cc27-108">The value STOP_UNMANAGED is only valid with interop debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0cc27-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0cc27-109">Remarks</span></span>  
 <span data-ttu-id="0cc27-110">Hata ayıklayıcı Microsoft Ara dilini (MSIL) için karşılık gelen bir eşlemesi olmayan bir tam zamanında (JIT) derleme bulduğunda eşlenmemiş kod türünü belirten bayrağı ayarlarsanız yürütmeyi durdurur; Aksi takdirde, Adımlama şeffaf bir şekilde devam eder.</span><span class="sxs-lookup"><span data-stu-id="0cc27-110">When the debugger finds a just-in-time (JIT) compilation that has no corresponding mapping to Microsoft intermediate language (MSIL), it halts execution if the flag specifying that type of unmapped code has been set; otherwise, stepping transparently continues.</span></span>  
  
 <span data-ttu-id="0cc27-111">Hata ayıklayıcı, bir yönteme girmeyi Adımlayıcı kullanmıyorsa, sonra da mutlaka eşlenmemiş bir kod üzerinde Adım olmaz.</span><span class="sxs-lookup"><span data-stu-id="0cc27-111">If the debugger doesn't use a stepper to enter a method, then it won't necessarily step over unmapped code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0cc27-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0cc27-112">Requirements</span></span>  
 <span data-ttu-id="0cc27-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0cc27-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0cc27-114">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0cc27-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0cc27-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0cc27-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0cc27-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0cc27-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

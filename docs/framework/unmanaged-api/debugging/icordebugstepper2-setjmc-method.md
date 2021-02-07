---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugStepper2:: SetJMC Yöntemi'
title: ICorDebugStepper2::SetJMC Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugStepper2.SetJMC
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper2::SetJMC
helpviewer_keywords:
- ICorDebugStepper2::SetJMC method [.NET Framework debugging]
- SetJMC method [.NET Framework debugging]
ms.assetid: f5cdc135-6db4-4b32-9dd1-260ec58b774f
topic_type:
- apiref
ms.openlocfilehash: 07178ab90bb392e64c9d8a8fddf961efbb268002
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717543"
---
# <a name="icordebugstepper2setjmc-method"></a><span data-ttu-id="6bdbd-103">ICorDebugStepper2::SetJMC Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6bdbd-103">ICorDebugStepper2::SetJMC Method</span></span>

<span data-ttu-id="6bdbd-104">Bu ICorDebugStepper adımlarının yalnızca bir uygulamanın geliştiricisi tarafından yazılan kodla ilgili olduğunu belirten bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6bdbd-104">Sets a value that specifies whether this ICorDebugStepper steps only through code that is authored by an application's developer.</span></span> <span data-ttu-id="6bdbd-105">Bu işlem yalnızca kendi kodum (JMC) hata ayıklaması olarak da bilinir.</span><span class="sxs-lookup"><span data-stu-id="6bdbd-105">This process is also known as just my code (JMC) debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bdbd-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6bdbd-106">Syntax</span></span>  
  
```cpp  
HRESULT SetJMC (  
    [in] BOOL    fIsJMCStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6bdbd-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6bdbd-107">Parameters</span></span>  

 `fIsJMCStepper`  
 <span data-ttu-id="6bdbd-108">'ndaki `true` Yalnızca bir uygulamanın geliştiricisi tarafından yazılan kodla adım adım olarak ayarlanır; Aksi takdirde, olarak ayarlayın `false` .</span><span class="sxs-lookup"><span data-stu-id="6bdbd-108">[in] Set to `true` to step only through code that is authored by an application's developer; otherwise, set to `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6bdbd-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6bdbd-109">Requirements</span></span>  

 <span data-ttu-id="6bdbd-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6bdbd-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bdbd-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6bdbd-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6bdbd-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6bdbd-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6bdbd-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6bdbd-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

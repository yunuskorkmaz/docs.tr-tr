---
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
ms.openlocfilehash: 6c076dd2912a22e4f9492492a2d7a9fb73db88e8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139033"
---
# <a name="icordebugstepper2setjmc-method"></a><span data-ttu-id="6bfba-102">ICorDebugStepper2::SetJMC Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6bfba-102">ICorDebugStepper2::SetJMC Method</span></span>
<span data-ttu-id="6bfba-103">Bu ICorDebugStepper adımlarının yalnızca bir uygulamanın geliştiricisi tarafından yazılan kodla ilgili olduğunu belirten bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6bfba-103">Sets a value that specifies whether this ICorDebugStepper steps only through code that is authored by an application's developer.</span></span> <span data-ttu-id="6bfba-104">Bu işlem yalnızca kendi kodum (JMC) hata ayıklaması olarak da bilinir.</span><span class="sxs-lookup"><span data-stu-id="6bfba-104">This process is also known as just my code (JMC) debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bfba-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6bfba-105">Syntax</span></span>  
  
```cpp  
HRESULT SetJMC (  
    [in] BOOL    fIsJMCStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6bfba-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6bfba-106">Parameters</span></span>  
 `fIsJMCStepper`  
 <span data-ttu-id="6bfba-107">'ndaki Yalnızca bir uygulamanın geliştiricisi tarafından yazılan kodla adımla `true` olarak ayarlayın; Aksi takdirde, `false`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="6bfba-107">[in] Set to `true` to step only through code that is authored by an application's developer; otherwise, set to `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6bfba-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6bfba-108">Requirements</span></span>  
 <span data-ttu-id="6bfba-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6bfba-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bfba-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6bfba-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6bfba-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6bfba-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6bfba-112">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6bfba-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

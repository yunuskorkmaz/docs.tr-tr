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
ms.openlocfilehash: 1bbcbcfbb78d421f247a13f58070b68f701e4ed1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697227"
---
# <a name="icordebugstepper2setjmc-method"></a><span data-ttu-id="a088a-102">ICorDebugStepper2::SetJMC Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a088a-102">ICorDebugStepper2::SetJMC Method</span></span>

<span data-ttu-id="a088a-103">Bu ICorDebugStepper adımlarının yalnızca bir uygulamanın geliştiricisi tarafından yazılan kodla ilgili olduğunu belirten bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a088a-103">Sets a value that specifies whether this ICorDebugStepper steps only through code that is authored by an application's developer.</span></span> <span data-ttu-id="a088a-104">Bu işlem yalnızca kendi kodum (JMC) hata ayıklaması olarak da bilinir.</span><span class="sxs-lookup"><span data-stu-id="a088a-104">This process is also known as just my code (JMC) debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a088a-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a088a-105">Syntax</span></span>  
  
```cpp  
HRESULT SetJMC (  
    [in] BOOL    fIsJMCStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a088a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a088a-106">Parameters</span></span>  

 `fIsJMCStepper`  
 <span data-ttu-id="a088a-107">'ndaki `true` Yalnızca bir uygulamanın geliştiricisi tarafından yazılan kodla adım adım olarak ayarlanır; Aksi takdirde, olarak ayarlayın `false` .</span><span class="sxs-lookup"><span data-stu-id="a088a-107">[in] Set to `true` to step only through code that is authored by an application's developer; otherwise, set to `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a088a-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a088a-108">Requirements</span></span>  

 <span data-ttu-id="a088a-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a088a-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a088a-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a088a-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a088a-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a088a-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a088a-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a088a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

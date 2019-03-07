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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 129bf04a097b2019b080f813bf049d41b501f8fd
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474221"
---
# <a name="icordebugstepper2setjmc-method"></a><span data-ttu-id="dc1e9-102">ICorDebugStepper2::SetJMC Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dc1e9-102">ICorDebugStepper2::SetJMC Method</span></span>
<span data-ttu-id="dc1e9-103">Bir uygulamanın geliştiricisi tarafından yazılmış kod aracılığıyla bu ICorDebugStepper adımları olup olmadığını belirten bir değeri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="dc1e9-103">Sets a value that specifies whether this ICorDebugStepper steps only through code that is authored by an application's developer.</span></span> <span data-ttu-id="dc1e9-104">Bu işlem olarak yalnızca benim kodum (JMC) hata ayıklayıcı da bilinir.</span><span class="sxs-lookup"><span data-stu-id="dc1e9-104">This process is also known as just my code (JMC) debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc1e9-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dc1e9-105">Syntax</span></span>  
  
```  
HRESULT SetJMC (  
    [in] BOOL    fIsJMCStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dc1e9-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dc1e9-106">Parameters</span></span>  
 `fIsJMCStepper`  
 <span data-ttu-id="dc1e9-107">[in] Kümesine `true` Uygulama geliştirici tarafından yazılan; Aksi takdirde, kümesine kodu boyunca adım adım `false`.</span><span class="sxs-lookup"><span data-stu-id="dc1e9-107">[in] Set to `true` to step only through code that is authored by an application's developer; otherwise, set to `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc1e9-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dc1e9-108">Requirements</span></span>  
 <span data-ttu-id="dc1e9-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc1e9-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc1e9-110">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dc1e9-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dc1e9-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dc1e9-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dc1e9-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc1e9-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

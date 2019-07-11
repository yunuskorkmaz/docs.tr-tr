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
ms.openlocfilehash: 5c6b53d23410dd310766dab44664c8cd865ee9ba
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771688"
---
# <a name="icordebugstepper2setjmc-method"></a><span data-ttu-id="d74ba-102">ICorDebugStepper2::SetJMC Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d74ba-102">ICorDebugStepper2::SetJMC Method</span></span>
<span data-ttu-id="d74ba-103">Bir uygulamanın geliştiricisi tarafından yazılmış kod aracılığıyla bu ICorDebugStepper adımları olup olmadığını belirten bir değeri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d74ba-103">Sets a value that specifies whether this ICorDebugStepper steps only through code that is authored by an application's developer.</span></span> <span data-ttu-id="d74ba-104">Bu işlem olarak yalnızca benim kodum (JMC) hata ayıklayıcı da bilinir.</span><span class="sxs-lookup"><span data-stu-id="d74ba-104">This process is also known as just my code (JMC) debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d74ba-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d74ba-105">Syntax</span></span>  
  
```cpp  
HRESULT SetJMC (  
    [in] BOOL    fIsJMCStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d74ba-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d74ba-106">Parameters</span></span>  
 `fIsJMCStepper`  
 <span data-ttu-id="d74ba-107">[in] Kümesine `true` Uygulama geliştirici tarafından yazılan; Aksi takdirde, kümesine kodu boyunca adım adım `false`.</span><span class="sxs-lookup"><span data-stu-id="d74ba-107">[in] Set to `true` to step only through code that is authored by an application's developer; otherwise, set to `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d74ba-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d74ba-108">Requirements</span></span>  
 <span data-ttu-id="d74ba-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d74ba-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d74ba-110">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d74ba-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d74ba-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d74ba-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d74ba-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d74ba-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

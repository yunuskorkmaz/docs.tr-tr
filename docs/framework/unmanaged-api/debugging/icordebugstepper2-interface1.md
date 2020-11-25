---
title: ICorDebugStepper2 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugStepper2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper2
helpviewer_keywords:
- ICorDebugStepper2 interface [.NET Framework debugging]
ms.assetid: 7a191c2a-95ea-4d47-83b0-44de2b632d63
topic_type:
- apiref
ms.openlocfilehash: ecbedfbca37a3630fc6d40c173f8a6cd05b4d3fb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727646"
---
# <a name="icordebugstepper2-interface"></a><span data-ttu-id="84a2a-102">ICorDebugStepper2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="84a2a-102">ICorDebugStepper2 Interface</span></span>

<span data-ttu-id="84a2a-103">Yalnızca My Code (JMC) hata ayıklaması için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="84a2a-103">Provides support for just my code (JMC) debugging.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="84a2a-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="84a2a-104">Methods</span></span>  
  
|<span data-ttu-id="84a2a-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="84a2a-105">Method</span></span>|<span data-ttu-id="84a2a-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="84a2a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="84a2a-107">SetJMC Yöntemi</span><span class="sxs-lookup"><span data-stu-id="84a2a-107">SetJMC Method</span></span>](icordebugstepper2-setjmc-method.md)|<span data-ttu-id="84a2a-108">Bu ICorDebugStepper adımlarının yalnızca bir uygulamanın geliştiricisi tarafından yazılan kodla ilgili olduğunu belirten bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="84a2a-108">Sets a value that specifies whether this ICorDebugStepper steps only through code that is authored by an application's developer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="84a2a-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="84a2a-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="84a2a-110">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="84a2a-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84a2a-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="84a2a-111">Requirements</span></span>  

 <span data-ttu-id="84a2a-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84a2a-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84a2a-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="84a2a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="84a2a-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="84a2a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="84a2a-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84a2a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84a2a-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="84a2a-116">See also</span></span>

- [<span data-ttu-id="84a2a-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="84a2a-117">Debugging Interfaces</span></span>](debugging-interfaces.md)

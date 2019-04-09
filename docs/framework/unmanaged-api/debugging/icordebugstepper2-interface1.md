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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 256f67d21a22ee4692d88311cc150736e61563a0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59073073"
---
# <a name="icordebugstepper2-interface"></a><span data-ttu-id="1db1e-102">ICorDebugStepper2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1db1e-102">ICorDebugStepper2 Interface</span></span>
<span data-ttu-id="1db1e-103">Yalnızca benim kodum (JMC) hata ayıklayıcı için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="1db1e-103">Provides support for just my code (JMC) debugging.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1db1e-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1db1e-104">Methods</span></span>  
  
|<span data-ttu-id="1db1e-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="1db1e-105">Method</span></span>|<span data-ttu-id="1db1e-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1db1e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1db1e-107">SetJMC Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1db1e-107">SetJMC Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper2-setjmc-method.md)|<span data-ttu-id="1db1e-108">Bir uygulamanın geliştiricisi tarafından yazılmış kod aracılığıyla bu ICorDebugStepper adımları olup olmadığını belirten bir değeri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="1db1e-108">Sets a value that specifies whether this ICorDebugStepper steps only through code that is authored by an application's developer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1db1e-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1db1e-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1db1e-110">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="1db1e-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1db1e-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1db1e-111">Requirements</span></span>  
 <span data-ttu-id="1db1e-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1db1e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1db1e-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1db1e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1db1e-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1db1e-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="1db1e-115">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="1db1e-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1db1e-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1db1e-116">See also</span></span>

- [<span data-ttu-id="1db1e-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1db1e-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

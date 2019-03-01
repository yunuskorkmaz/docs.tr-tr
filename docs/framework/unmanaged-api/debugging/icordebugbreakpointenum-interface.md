---
title: ICorDebugBreakpointEnum Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpointEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpointEnum
helpviewer_keywords:
- ICorDebugBreakpointEnum interface [.NET Framework debugging]
ms.assetid: 4c6f4f6e-52cc-402e-881b-7b8526544c90
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7b5268eb4240f7c3ff254f4d3d9a13ab494530a1
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56968744"
---
# <a name="icordebugbreakpointenum-interface"></a><span data-ttu-id="8b430-102">ICorDebugBreakpointEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8b430-102">ICorDebugBreakpointEnum Interface</span></span>

<span data-ttu-id="8b430-103">Icordebugenum yöntemlerini uygular ve Icordebugbreakpoint dizilerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="8b430-103">Implements ICorDebugEnum methods, and enumerates ICorDebugBreakpoint arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8b430-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8b430-104">Methods</span></span>  
  
|<span data-ttu-id="8b430-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="8b430-105">Method</span></span>|<span data-ttu-id="8b430-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8b430-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8b430-107">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8b430-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpointenum-next-method.md)|<span data-ttu-id="8b430-108">Belirtilen sayıda alır `ICorDebugBreakpoint` örneklerden geçerli konumunda başlayan bir numaralandırma.</span><span class="sxs-lookup"><span data-stu-id="8b430-108">Gets the specified number of `ICorDebugBreakpoint` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8b430-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8b430-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8b430-110">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="8b430-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b430-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8b430-111">Requirements</span></span>  
 <span data-ttu-id="8b430-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b430-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b430-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8b430-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8b430-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8b430-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b430-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b430-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b430-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8b430-116">See also</span></span>
- [<span data-ttu-id="8b430-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8b430-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

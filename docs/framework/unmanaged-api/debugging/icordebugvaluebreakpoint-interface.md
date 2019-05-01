---
title: ICorDebugValueBreakpoint Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugValueBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValueBreakpoint
helpviewer_keywords:
- ICorDebugValueBreakpoint interface [.NET Framework debugging]
ms.assetid: c02338fe-da6c-467f-9567-70ebb387e901
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 778359a7d26b6e2f19984a1f7ff06a527f2449f0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993734"
---
# <a name="icordebugvaluebreakpoint-interface"></a><span data-ttu-id="ddc2e-102">ICorDebugValueBreakpoint Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ddc2e-102">ICorDebugValueBreakpoint Interface</span></span>
<span data-ttu-id="ddc2e-103">Icordebugbreakpoint arabirimi belirli değerlere erişim için genişletir.</span><span class="sxs-lookup"><span data-stu-id="ddc2e-103">Extends the ICorDebugBreakpoint interface to provide access to specific values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ddc2e-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ddc2e-104">Methods</span></span>  
  
|<span data-ttu-id="ddc2e-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ddc2e-105">Method</span></span>|<span data-ttu-id="ddc2e-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ddc2e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ddc2e-107">GetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ddc2e-107">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvaluebreakpoint-getvalue-method.md)|<span data-ttu-id="ddc2e-108">Icordebugvalue nesneye bağlı Kesme noktasının ayarlandığını nesnenin değerini temsil eden bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="ddc2e-108">Gets an interface pointer to an ICorDebugValue object that represents the value of the object upon which the breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ddc2e-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ddc2e-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ddc2e-110">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="ddc2e-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ddc2e-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ddc2e-111">Requirements</span></span>  
 <span data-ttu-id="ddc2e-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ddc2e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ddc2e-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ddc2e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ddc2e-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ddc2e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ddc2e-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ddc2e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddc2e-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ddc2e-116">See also</span></span>

- [<span data-ttu-id="ddc2e-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ddc2e-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

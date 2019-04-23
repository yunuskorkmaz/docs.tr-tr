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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59167752"
---
# <a name="icordebugvaluebreakpoint-interface"></a><span data-ttu-id="289ec-102">ICorDebugValueBreakpoint Arabirimi</span><span class="sxs-lookup"><span data-stu-id="289ec-102">ICorDebugValueBreakpoint Interface</span></span>
<span data-ttu-id="289ec-103">Icordebugbreakpoint arabirimi belirli değerlere erişim için genişletir.</span><span class="sxs-lookup"><span data-stu-id="289ec-103">Extends the ICorDebugBreakpoint interface to provide access to specific values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="289ec-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="289ec-104">Methods</span></span>  
  
|<span data-ttu-id="289ec-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="289ec-105">Method</span></span>|<span data-ttu-id="289ec-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="289ec-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="289ec-107">GetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="289ec-107">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvaluebreakpoint-getvalue-method.md)|<span data-ttu-id="289ec-108">Icordebugvalue nesneye bağlı Kesme noktasının ayarlandığını nesnenin değerini temsil eden bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="289ec-108">Gets an interface pointer to an ICorDebugValue object that represents the value of the object upon which the breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="289ec-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="289ec-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="289ec-110">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="289ec-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="289ec-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="289ec-111">Requirements</span></span>  
 <span data-ttu-id="289ec-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="289ec-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="289ec-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="289ec-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="289ec-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="289ec-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="289ec-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="289ec-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="289ec-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="289ec-116">See also</span></span>

- [<span data-ttu-id="289ec-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="289ec-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

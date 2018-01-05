---
title: Icordebugvaluebreakpoint Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugValueBreakpoint
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugValueBreakpoint
helpviewer_keywords: ICorDebugValueBreakpoint interface [.NET Framework debugging]
ms.assetid: c02338fe-da6c-467f-9567-70ebb387e901
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 92de5aa960c9ded27aef09d2c795437e9c599835
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvaluebreakpoint-interface1"></a><span data-ttu-id="99ac8-102">Icordebugvaluebreakpoint Interface1</span><span class="sxs-lookup"><span data-stu-id="99ac8-102">ICorDebugValueBreakpoint Interface1</span></span>
<span data-ttu-id="99ac8-103">Icordebugbreakpoint arabirimi belirli değerleri erişim sağlamak için genişletir.</span><span class="sxs-lookup"><span data-stu-id="99ac8-103">Extends the ICorDebugBreakpoint interface to provide access to specific values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="99ac8-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="99ac8-104">Methods</span></span>  
  
|<span data-ttu-id="99ac8-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="99ac8-105">Method</span></span>|<span data-ttu-id="99ac8-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="99ac8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="99ac8-107">GetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="99ac8-107">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvaluebreakpoint-getvalue-method.md)|<span data-ttu-id="99ac8-108">Icordebugvalue nesneye bağlı kesme noktası belirleyerek nesnenin değerini temsil eden bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="99ac8-108">Gets an interface pointer to an ICorDebugValue object that represents the value of the object upon which the breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99ac8-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="99ac8-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="99ac8-110">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="99ac8-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99ac8-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="99ac8-111">Requirements</span></span>  
 <span data-ttu-id="99ac8-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99ac8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99ac8-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="99ac8-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="99ac8-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="99ac8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="99ac8-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99ac8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99ac8-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="99ac8-116">See Also</span></span>  
 [<span data-ttu-id="99ac8-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="99ac8-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

---
title: Icordebugvaluebreakpoint arabirimi1
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
ms.openlocfilehash: 58e6807b0546eadc4baacc276fa1ba7bda4e3aba
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54557766"
---
# <a name="icordebugvaluebreakpoint-interface1"></a><span data-ttu-id="a64ec-102">Icordebugvaluebreakpoint arabirimi1</span><span class="sxs-lookup"><span data-stu-id="a64ec-102">ICorDebugValueBreakpoint Interface1</span></span>
<span data-ttu-id="a64ec-103">Icordebugbreakpoint arabirimi belirli değerlere erişim için genişletir.</span><span class="sxs-lookup"><span data-stu-id="a64ec-103">Extends the ICorDebugBreakpoint interface to provide access to specific values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a64ec-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a64ec-104">Methods</span></span>  
  
|<span data-ttu-id="a64ec-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="a64ec-105">Method</span></span>|<span data-ttu-id="a64ec-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a64ec-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a64ec-107">GetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a64ec-107">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvaluebreakpoint-getvalue-method.md)|<span data-ttu-id="a64ec-108">Icordebugvalue nesneye bağlı Kesme noktasının ayarlandığını nesnenin değerini temsil eden bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="a64ec-108">Gets an interface pointer to an ICorDebugValue object that represents the value of the object upon which the breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a64ec-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a64ec-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a64ec-110">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="a64ec-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a64ec-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a64ec-111">Requirements</span></span>  
 <span data-ttu-id="a64ec-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a64ec-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a64ec-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a64ec-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a64ec-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a64ec-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a64ec-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a64ec-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a64ec-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a64ec-116">See also</span></span>
- [<span data-ttu-id="a64ec-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a64ec-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

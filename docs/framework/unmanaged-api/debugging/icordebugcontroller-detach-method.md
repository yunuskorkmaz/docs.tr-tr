---
title: ICorDebugController::Detach Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugController.Detach
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Detach
helpviewer_keywords:
- Detach method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Detach method [.NET Framework debugging]
ms.assetid: 06fae364-f2c6-4a50-aa7e-3da9f2684dc3
topic_type:
- apiref
ms.openlocfilehash: 480fec4897dac73594515ba8bc0f0e96ceb79ace
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82892909"
---
# <a name="icordebugcontrollerdetach-method"></a><span data-ttu-id="6bac8-102">ICorDebugController::Detach Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6bac8-102">ICorDebugController::Detach Method</span></span>
<span data-ttu-id="6bac8-103">Hata ayıklayıcıyı işlem veya uygulama etki alanından ayırır.</span><span class="sxs-lookup"><span data-stu-id="6bac8-103">Detaches the debugger from the process or application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bac8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6bac8-104">Syntax</span></span>  
  
```cpp  
HRESULT Detach ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="6bac8-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6bac8-105">Remarks</span></span>  
 <span data-ttu-id="6bac8-106">İşlem veya uygulama etki alanı normal şekilde yürütmeye devam eder, ancak "ICorDebugProcess" veya "ICorDebugAppDomain" nesnesi artık geçerli değildir ve başka hiçbir geri çağırma gerçekleşmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="6bac8-106">The process or application domain continues execution normally, but the "ICorDebugProcess" or "ICorDebugAppDomain" object is no longer valid and no further callbacks will occur.</span></span>  
  
 <span data-ttu-id="6bac8-107">.NET Framework sürüm 2,0 ' de, yönetilmeyen hata ayıklama etkinse, bu yöntem işletim sistemi sınırlamaları nedeniyle başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="6bac8-107">In the .NET Framework version 2.0, if unmanaged debugging is enabled, this method will fail due to operating system limitations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6bac8-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6bac8-108">Requirements</span></span>  
 <span data-ttu-id="6bac8-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6bac8-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bac8-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6bac8-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6bac8-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6bac8-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6bac8-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6bac8-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bac8-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6bac8-113">See also</span></span>

---
description: ': ICorDebugController::D etach yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 763386fa72fab023becf4a360556e61d500c7949
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764674"
---
# <a name="icordebugcontrollerdetach-method"></a><span data-ttu-id="30a7e-103">ICorDebugController::Detach Yöntemi</span><span class="sxs-lookup"><span data-stu-id="30a7e-103">ICorDebugController::Detach Method</span></span>

<span data-ttu-id="30a7e-104">Hata ayıklayıcıyı işlem veya uygulama etki alanından ayırır.</span><span class="sxs-lookup"><span data-stu-id="30a7e-104">Detaches the debugger from the process or application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30a7e-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="30a7e-105">Syntax</span></span>  
  
```cpp  
HRESULT Detach ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="30a7e-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="30a7e-106">Remarks</span></span>  

 <span data-ttu-id="30a7e-107">İşlem veya uygulama etki alanı normal şekilde yürütmeye devam eder, ancak "ICorDebugProcess" veya "ICorDebugAppDomain" nesnesi artık geçerli değildir ve başka hiçbir geri çağırma gerçekleşmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="30a7e-107">The process or application domain continues execution normally, but the "ICorDebugProcess" or "ICorDebugAppDomain" object is no longer valid and no further callbacks will occur.</span></span>  
  
 <span data-ttu-id="30a7e-108">.NET Framework sürüm 2,0 ' de, yönetilmeyen hata ayıklama etkinse, bu yöntem işletim sistemi sınırlamaları nedeniyle başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="30a7e-108">In the .NET Framework version 2.0, if unmanaged debugging is enabled, this method will fail due to operating system limitations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30a7e-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="30a7e-109">Requirements</span></span>  

 <span data-ttu-id="30a7e-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30a7e-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30a7e-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="30a7e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="30a7e-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="30a7e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="30a7e-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30a7e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30a7e-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="30a7e-114">See also</span></span>

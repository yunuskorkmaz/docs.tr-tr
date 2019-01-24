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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4f2dae147f8667a73036dbcf873e2082996b2755
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54666991"
---
# <a name="icordebugcontrollerdetach-method"></a><span data-ttu-id="dd7ed-102">ICorDebugController::Detach Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dd7ed-102">ICorDebugController::Detach Method</span></span>
<span data-ttu-id="dd7ed-103">Hata ayıklayıcı işlem veya uygulama etki alanından ayırır.</span><span class="sxs-lookup"><span data-stu-id="dd7ed-103">Detaches the debugger from the process or application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd7ed-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dd7ed-104">Syntax</span></span>  
  
```  
HRESULT Detach ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="dd7ed-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dd7ed-105">Remarks</span></span>  
 <span data-ttu-id="dd7ed-106">İşlem veya uygulama etki alanı normalde, yürütme devam eder, ancak "ICorDebugProcess" veya "ICorDebugAppDomain" nesne artık geçerli değil ve başka hiçbir geri çağırmaları meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="dd7ed-106">The process or application domain continues execution normally, but the "ICorDebugProcess" or "ICorDebugAppDomain" object is no longer valid and no further callbacks will occur.</span></span>  
  
 <span data-ttu-id="dd7ed-107">.NET Framework sürüm 2. 0'da, bu yöntem, yönetilmeyen hata ayıklama etkinleştirilirse, işletim sistemi sınırlamaları nedeniyle başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="dd7ed-107">In the .NET Framework version 2.0, if unmanaged debugging is enabled, this method will fail due to operating system limitations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd7ed-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dd7ed-108">Requirements</span></span>  
 <span data-ttu-id="dd7ed-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd7ed-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd7ed-110">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dd7ed-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dd7ed-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dd7ed-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dd7ed-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd7ed-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd7ed-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dd7ed-113">See also</span></span>


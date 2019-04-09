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
ms.openlocfilehash: 85a9bde77f7c393756ec1d3e7d30b96392aa6a94
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59151807"
---
# <a name="icordebugcontrollerdetach-method"></a><span data-ttu-id="a83d5-102">ICorDebugController::Detach Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a83d5-102">ICorDebugController::Detach Method</span></span>
<span data-ttu-id="a83d5-103">Hata ayıklayıcı işlem veya uygulama etki alanından ayırır.</span><span class="sxs-lookup"><span data-stu-id="a83d5-103">Detaches the debugger from the process or application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a83d5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a83d5-104">Syntax</span></span>  
  
```  
HRESULT Detach ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="a83d5-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a83d5-105">Remarks</span></span>  
 <span data-ttu-id="a83d5-106">İşlem veya uygulama etki alanı normalde, yürütme devam eder, ancak "ICorDebugProcess" veya "ICorDebugAppDomain" nesne artık geçerli değil ve başka hiçbir geri çağırmaları meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="a83d5-106">The process or application domain continues execution normally, but the "ICorDebugProcess" or "ICorDebugAppDomain" object is no longer valid and no further callbacks will occur.</span></span>  
  
 <span data-ttu-id="a83d5-107">.NET Framework sürüm 2. 0'da, bu yöntem, yönetilmeyen hata ayıklama etkinleştirilirse, işletim sistemi sınırlamaları nedeniyle başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="a83d5-107">In the .NET Framework version 2.0, if unmanaged debugging is enabled, this method will fail due to operating system limitations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a83d5-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a83d5-108">Requirements</span></span>  
 <span data-ttu-id="a83d5-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a83d5-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a83d5-110">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a83d5-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a83d5-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a83d5-111">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="a83d5-112">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="a83d5-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a83d5-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a83d5-113">See also</span></span>

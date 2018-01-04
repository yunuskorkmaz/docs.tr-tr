---
title: "ICorDebugController::Detach Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugController.Detach
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugController::Detach
helpviewer_keywords:
- Detach method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Detach method [.NET Framework debugging]
ms.assetid: 06fae364-f2c6-4a50-aa7e-3da9f2684dc3
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 59fe2c4bfbd91afd263a0ada1eb355aaa8914aa2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcontrollerdetach-method"></a><span data-ttu-id="1a443-102">ICorDebugController::Detach Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1a443-102">ICorDebugController::Detach Method</span></span>
<span data-ttu-id="1a443-103">Hata ayıklayıcı işlem veya uygulama etki alanından ayırır.</span><span class="sxs-lookup"><span data-stu-id="1a443-103">Detaches the debugger from the process or application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a443-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1a443-104">Syntax</span></span>  
  
```  
HRESULT Detach ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="1a443-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1a443-105">Remarks</span></span>  
 <span data-ttu-id="1a443-106">İşlem veya uygulama etki alanı yürütme normal şekilde devam eder, ancak "ICorDebugProcess" veya "ICorDebugAppDomain" nesne artık geçerli değil ve başka hiçbir geri aramalar meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="1a443-106">The process or application domain continues execution normally, but the "ICorDebugProcess" or "ICorDebugAppDomain" object is no longer valid and no further callbacks will occur.</span></span>  
  
 <span data-ttu-id="1a443-107">Yönetilmeyen hata ayıklama etkinleştirilirse, .NET Framework sürüm 2. 0'da, işletim sistemi kısıtlamaları nedeniyle bu yöntem başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="1a443-107">In the .NET Framework version 2.0, if unmanaged debugging is enabled, this method will fail due to operating system limitations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a443-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1a443-108">Requirements</span></span>  
 <span data-ttu-id="1a443-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a443-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a443-110">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1a443-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1a443-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1a443-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1a443-112">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a443-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a443-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1a443-113">See Also</span></span>  
 

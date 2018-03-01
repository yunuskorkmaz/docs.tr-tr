---
title: "ICorDebugStepper::Deactivate Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugStepper.Deactivate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::Deactivate
helpviewer_keywords:
- Deactivate method [.NET Framework debugging]
- ICorDebugStepper::Deactivate method [.NET Framework debugging]
ms.assetid: 855f4199-b62d-40ce-998e-1eb4a1772142
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1541c6fa838115655c3ff176a0cb29f803733daa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugstepperdeactivate-method"></a><span data-ttu-id="ad193-102">ICorDebugStepper::Deactivate Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ad193-102">ICorDebugStepper::Deactivate Method</span></span>
<span data-ttu-id="ad193-103">Bu alınan son adımı komutunu iptal etmek bu ICorDebugStepper neden olur.</span><span class="sxs-lookup"><span data-stu-id="ad193-103">Causes this ICorDebugStepper to cancel the last step command that it received.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad193-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ad193-104">Syntax</span></span>  
  
```  
HRESULT Deactivate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="ad193-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ad193-105">Remarks</span></span>  
 <span data-ttu-id="ad193-106">En son alınan adımdaki komut iptal edildikten sonra yeni bir sürüm komutu verilebilir.</span><span class="sxs-lookup"><span data-stu-id="ad193-106">A new stepping command may be issued after the most recently received step command has been canceled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad193-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ad193-107">Requirements</span></span>  
 <span data-ttu-id="ad193-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad193-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad193-109">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ad193-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ad193-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ad193-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad193-111">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad193-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

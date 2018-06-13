---
title: ICorDebugStepper::Deactivate Yöntemi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bcd7bfb52cadf740d8fe3cb92a09b071f530b7ee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417407"
---
# <a name="icordebugstepperdeactivate-method"></a><span data-ttu-id="654ae-102">ICorDebugStepper::Deactivate Yöntemi</span><span class="sxs-lookup"><span data-stu-id="654ae-102">ICorDebugStepper::Deactivate Method</span></span>
<span data-ttu-id="654ae-103">Bu alınan son adımı komutunu iptal etmek bu ICorDebugStepper neden olur.</span><span class="sxs-lookup"><span data-stu-id="654ae-103">Causes this ICorDebugStepper to cancel the last step command that it received.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="654ae-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="654ae-104">Syntax</span></span>  
  
```  
HRESULT Deactivate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="654ae-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="654ae-105">Remarks</span></span>  
 <span data-ttu-id="654ae-106">En son alınan adımdaki komut iptal edildikten sonra yeni bir sürüm komutu verilebilir.</span><span class="sxs-lookup"><span data-stu-id="654ae-106">A new stepping command may be issued after the most recently received step command has been canceled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="654ae-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="654ae-107">Requirements</span></span>  
 <span data-ttu-id="654ae-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="654ae-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="654ae-109">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="654ae-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="654ae-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="654ae-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="654ae-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="654ae-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

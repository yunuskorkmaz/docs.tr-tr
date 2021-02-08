---
description: 'Hakkında daha fazla bilgi edinin: ICorDebugStepper::D eactivate yöntemi'
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
ms.openlocfilehash: 039c52f5bc237506dcc648ace70789c8eb7ef8c9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794669"
---
# <a name="icordebugstepperdeactivate-method"></a><span data-ttu-id="495dd-103">ICorDebugStepper::Deactivate Yöntemi</span><span class="sxs-lookup"><span data-stu-id="495dd-103">ICorDebugStepper::Deactivate Method</span></span>

<span data-ttu-id="495dd-104">Bu ICorDebugStepper, aldığı son adım komutunu iptal etmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="495dd-104">Causes this ICorDebugStepper to cancel the last step command that it received.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="495dd-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="495dd-105">Syntax</span></span>  
  
```cpp  
HRESULT Deactivate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="495dd-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="495dd-106">Remarks</span></span>  

 <span data-ttu-id="495dd-107">Yeni bir Adımlama komutu, en son alınan adım komutu iptal edildikten sonra verilebilir.</span><span class="sxs-lookup"><span data-stu-id="495dd-107">A new stepping command may be issued after the most recently received step command has been canceled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="495dd-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="495dd-108">Requirements</span></span>  

 <span data-ttu-id="495dd-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="495dd-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="495dd-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="495dd-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="495dd-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="495dd-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="495dd-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="495dd-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

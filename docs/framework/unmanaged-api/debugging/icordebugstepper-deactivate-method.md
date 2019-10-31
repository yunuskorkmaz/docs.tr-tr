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
ms.openlocfilehash: 1d75897e00c36bd5c484e837ee68e54443168e77
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131762"
---
# <a name="icordebugstepperdeactivate-method"></a><span data-ttu-id="96fab-102">ICorDebugStepper::Deactivate Yöntemi</span><span class="sxs-lookup"><span data-stu-id="96fab-102">ICorDebugStepper::Deactivate Method</span></span>
<span data-ttu-id="96fab-103">Bu ICorDebugStepper, aldığı son adım komutunu iptal etmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="96fab-103">Causes this ICorDebugStepper to cancel the last step command that it received.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96fab-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="96fab-104">Syntax</span></span>  
  
```cpp  
HRESULT Deactivate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="96fab-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="96fab-105">Remarks</span></span>  
 <span data-ttu-id="96fab-106">Yeni bir Adımlama komutu, en son alınan adım komutu iptal edildikten sonra verilebilir.</span><span class="sxs-lookup"><span data-stu-id="96fab-106">A new stepping command may be issued after the most recently received step command has been canceled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96fab-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="96fab-107">Requirements</span></span>  
 <span data-ttu-id="96fab-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96fab-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96fab-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="96fab-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="96fab-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="96fab-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="96fab-111">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96fab-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

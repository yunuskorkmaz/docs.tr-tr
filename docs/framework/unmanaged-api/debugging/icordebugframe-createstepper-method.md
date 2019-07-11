---
title: ICorDebugFrame::CreateStepper Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.CreateStepper
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::CreateStepper
helpviewer_keywords:
- ICorDebugFrame::CreateStepper method [.NET Framework debugging]
- CreateStepper method, ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 689e7f28-20c1-4d5c-9baa-17441cd63a88
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fd105a5cbdb857aaa902e60968ff1d94473259b6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754245"
---
# <a name="icordebugframecreatestepper-method"></a><span data-ttu-id="e1d86-102">ICorDebugFrame::CreateStepper Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e1d86-102">ICorDebugFrame::CreateStepper Method</span></span>
<span data-ttu-id="e1d86-103">Hata ayıklayıcının bu Icordebugframe göre Adımlama işlemleri gerçekleştirmek için izin veren Adımlayıcı alır.</span><span class="sxs-lookup"><span data-stu-id="e1d86-103">Gets a stepper that allows the debugger to perform stepping operations relative to this ICorDebugFrame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1d86-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e1d86-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateStepper (  
    [out] ICorDebugStepper   **ppStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e1d86-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e1d86-105">Parameters</span></span>  
 `ppStepper`  
 <span data-ttu-id="e1d86-106">[out] Geçerli çerçevesine göre Adımlama işlemleri gerçekleştirmek hata ayıklayıcı izin veren bir ICorDebugStepper nesnesi adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e1d86-106">[out] A pointer to the address of an ICorDebugStepper object that allows the debugger to perform stepping operations relative to the current frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e1d86-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e1d86-107">Remarks</span></span>  
 <span data-ttu-id="e1d86-108">Çerçeve etkin değilse, adımlayıcıdaki nesne adımı tamamlanmadan önce çerçeveye döndürmek genellikle gerekir.</span><span class="sxs-lookup"><span data-stu-id="e1d86-108">If the frame is not active, the stepper object will typically have to return to the frame before the step is completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1d86-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e1d86-109">Requirements</span></span>  
 <span data-ttu-id="e1d86-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1d86-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1d86-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e1d86-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e1d86-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e1d86-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e1d86-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1d86-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

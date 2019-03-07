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
ms.openlocfilehash: 3fe3cbc4bad83496bcc58aaea60e6724b1d1f06c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466394"
---
# <a name="icordebugframecreatestepper-method"></a><span data-ttu-id="0355b-102">ICorDebugFrame::CreateStepper Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0355b-102">ICorDebugFrame::CreateStepper Method</span></span>
<span data-ttu-id="0355b-103">Hata ayıklayıcının bu Icordebugframe göre Adımlama işlemleri gerçekleştirmek için izin veren Adımlayıcı alır.</span><span class="sxs-lookup"><span data-stu-id="0355b-103">Gets a stepper that allows the debugger to perform stepping operations relative to this ICorDebugFrame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0355b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0355b-104">Syntax</span></span>  
  
```  
HRESULT CreateStepper (  
    [out] ICorDebugStepper   **ppStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0355b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0355b-105">Parameters</span></span>  
 `ppStepper`  
 <span data-ttu-id="0355b-106">[out] Geçerli çerçevesine göre Adımlama işlemleri gerçekleştirmek hata ayıklayıcı izin veren bir ICorDebugStepper nesnesi adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0355b-106">[out] A pointer to the address of an ICorDebugStepper object that allows the debugger to perform stepping operations relative to the current frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0355b-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0355b-107">Remarks</span></span>  
 <span data-ttu-id="0355b-108">Çerçeve etkin değilse, adımlayıcıdaki nesne adımı tamamlanmadan önce çerçeveye döndürmek genellikle gerekir.</span><span class="sxs-lookup"><span data-stu-id="0355b-108">If the frame is not active, the stepper object will typically have to return to the frame before the step is completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0355b-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0355b-109">Requirements</span></span>  
 <span data-ttu-id="0355b-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0355b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0355b-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0355b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0355b-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0355b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0355b-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0355b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

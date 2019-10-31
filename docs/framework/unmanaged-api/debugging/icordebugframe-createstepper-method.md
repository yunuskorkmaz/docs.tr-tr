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
ms.openlocfilehash: 6ea2b24d37f56a5cb9e6b3dea0d666c8acc719dc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73091039"
---
# <a name="icordebugframecreatestepper-method"></a><span data-ttu-id="42bb4-102">ICorDebugFrame::CreateStepper Yöntemi</span><span class="sxs-lookup"><span data-stu-id="42bb4-102">ICorDebugFrame::CreateStepper Method</span></span>
<span data-ttu-id="42bb4-103">Hata ayıklayıcının bu ICorDebugFrame 'e göre atlama işlemleri gerçekleştirmesini sağlayan bir Stepper alır.</span><span class="sxs-lookup"><span data-stu-id="42bb4-103">Gets a stepper that allows the debugger to perform stepping operations relative to this ICorDebugFrame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42bb4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="42bb4-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateStepper (  
    [out] ICorDebugStepper   **ppStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="42bb4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="42bb4-105">Parameters</span></span>  
 `ppStepper`  
 <span data-ttu-id="42bb4-106">dışı Hata ayıklayıcının geçerli çerçeveye göre atlama işlemleri gerçekleştirmesini sağlayan bir ICorDebugStepper nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="42bb4-106">[out] A pointer to the address of an ICorDebugStepper object that allows the debugger to perform stepping operations relative to the current frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42bb4-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="42bb4-107">Remarks</span></span>  
 <span data-ttu-id="42bb4-108">Çerçeve etkin değilse, Stepper nesnesi genellikle adım tamamlanmadan önce çerçeveye geri dönmesi gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="42bb4-108">If the frame is not active, the stepper object will typically have to return to the frame before the step is completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42bb4-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="42bb4-109">Requirements</span></span>  
 <span data-ttu-id="42bb4-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42bb4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42bb4-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="42bb4-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="42bb4-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="42bb4-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="42bb4-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42bb4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

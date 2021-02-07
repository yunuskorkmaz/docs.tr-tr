---
description: ': ICorDebugFrame:: CreateStepper yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 394418b89fd7a1c780a5bc33b97b8ef40bab8df2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693102"
---
# <a name="icordebugframecreatestepper-method"></a><span data-ttu-id="e5ff1-103">ICorDebugFrame::CreateStepper Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e5ff1-103">ICorDebugFrame::CreateStepper Method</span></span>

<span data-ttu-id="e5ff1-104">Hata ayıklayıcının bu ICorDebugFrame 'e göre atlama işlemleri gerçekleştirmesini sağlayan bir Stepper alır.</span><span class="sxs-lookup"><span data-stu-id="e5ff1-104">Gets a stepper that allows the debugger to perform stepping operations relative to this ICorDebugFrame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5ff1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e5ff1-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateStepper (  
    [out] ICorDebugStepper   **ppStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e5ff1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e5ff1-106">Parameters</span></span>  

 `ppStepper`  
 <span data-ttu-id="e5ff1-107">dışı Hata ayıklayıcının geçerli çerçeveye göre atlama işlemleri gerçekleştirmesini sağlayan bir ICorDebugStepper nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e5ff1-107">[out] A pointer to the address of an ICorDebugStepper object that allows the debugger to perform stepping operations relative to the current frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e5ff1-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e5ff1-108">Remarks</span></span>  

 <span data-ttu-id="e5ff1-109">Çerçeve etkin değilse, Stepper nesnesi genellikle adım tamamlanmadan önce çerçeveye geri dönmesi gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="e5ff1-109">If the frame is not active, the stepper object will typically have to return to the frame before the step is completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5ff1-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e5ff1-110">Requirements</span></span>  

 <span data-ttu-id="e5ff1-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5ff1-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5ff1-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e5ff1-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e5ff1-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e5ff1-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e5ff1-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5ff1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

---
title: "ICorDebugFrame::CreateStepper Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFrame.CreateStepper
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFrame::CreateStepper
helpviewer_keywords:
- ICorDebugFrame::CreateStepper method [.NET Framework debugging]
- CreateStepper method, ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 689e7f28-20c1-4d5c-9baa-17441cd63a88
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a6f575febc488d01700c32198d4c00916dd5e249
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugframecreatestepper-method"></a><span data-ttu-id="84aa3-102">ICorDebugFrame::CreateStepper Yöntemi</span><span class="sxs-lookup"><span data-stu-id="84aa3-102">ICorDebugFrame::CreateStepper Method</span></span>
<span data-ttu-id="84aa3-103">Hata ayıklayıcı bu Icordebugframe göre sürüm işlemlerini gerçekleştirmek imkan tanıyan Adımlayıcı alır.</span><span class="sxs-lookup"><span data-stu-id="84aa3-103">Gets a stepper that allows the debugger to perform stepping operations relative to this ICorDebugFrame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84aa3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="84aa3-104">Syntax</span></span>  
  
```  
HRESULT CreateStepper (  
    [out] ICorDebugStepper   **ppStepper  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="84aa3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="84aa3-105">Parameters</span></span>  
 `ppStepper`  
 <span data-ttu-id="84aa3-106">[out] Hata ayıklayıcı geçerli çerçeve göre sürüm işlemlerini gerçekleştirmek imkan tanıyan ICorDebugStepper nesnenin adresini gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="84aa3-106">[out] A pointer to the address of an ICorDebugStepper object that allows the debugger to perform stepping operations relative to the current frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="84aa3-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="84aa3-107">Remarks</span></span>  
 <span data-ttu-id="84aa3-108">Çerçeve etkin değilse, Adımlayıcı nesne genellikle adımı tamamlanmadan önce çerçeveye dönmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="84aa3-108">If the frame is not active, the stepper object will typically have to return to the frame before the step is completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84aa3-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="84aa3-109">Requirements</span></span>  
 <span data-ttu-id="84aa3-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84aa3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84aa3-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="84aa3-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="84aa3-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="84aa3-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="84aa3-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84aa3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

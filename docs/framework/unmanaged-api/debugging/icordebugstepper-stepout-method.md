---
title: "ICorDebugStepper::StepOut Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper.StepOut
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper::StepOut
helpviewer_keywords:
- ICorDebugStepper::StepOut method [.NET Framework debugging]
- StepOut method [.NET Framework debugging]
ms.assetid: aae0f48c-4ede-4256-9251-a7fc85a229dc
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8b3ceca69b6b4710a3f1b8e1e9bdb4baf574119c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugstepperstepout-method"></a><span data-ttu-id="c4706-102">ICorDebugStepper::StepOut Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c4706-102">ICorDebugStepper::StepOut Method</span></span>
<span data-ttu-id="c4706-103">Tek adımlı içeren kendi iş parçacığı üzerinden ve geçerli çerçeve denetim arama çerçevenin geri döndüğünde tamamlamak için bu ICorDebugStepper neden olur.</span><span class="sxs-lookup"><span data-stu-id="c4706-103">Causes this ICorDebugStepper to single-step through its containing thread, and to complete when the current frame returns control to the calling frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4706-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c4706-104">Syntax</span></span>  
  
```  
HRESULT StepOut ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="c4706-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c4706-105">Remarks</span></span>  
 <span data-ttu-id="c4706-106">A `StepOut` işlemi, geçerli çerçevesinden normalde arama çerçeveye döndüğünüzde tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="c4706-106">A `StepOut` operation will complete after returning normally from the current frame to the calling frame.</span></span>  
  
 <span data-ttu-id="c4706-107">Varsa `StepOut` aldığında çağrılan adlı Yönetilen kod için geçerli çerçevenin geri döndüğünde yönetilmeyen kodunda adım tamamlayacak.</span><span class="sxs-lookup"><span data-stu-id="c4706-107">If `StepOut` is called when in unmanaged code, the step will complete when the current frame returns to the managed code that called it.</span></span>  
  
 <span data-ttu-id="c4706-108">.NET Framework sürüm 2. 0'da, kullanmayın `StepOut` ile STOP_UNMANAGED bayrağı ayarlanmış çünkü başarısız.</span><span class="sxs-lookup"><span data-stu-id="c4706-108">In the .NET Framework version 2.0, do not use `StepOut` with the STOP_UNMANAGED flag set because it will fail.</span></span> <span data-ttu-id="c4706-109">(Kullanım [ICorDebugStepper::setunmappedstopmask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) atlama bayrakları ayarlamak için.) Birlikte çalışma hata ayıklayıcıları yerel koda kendilerini olmalıdır dışarı adım.</span><span class="sxs-lookup"><span data-stu-id="c4706-109">(Use [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) to set flags for stepping.) Interop debuggers must step out to native code themselves.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4706-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c4706-110">Requirements</span></span>  
 <span data-ttu-id="c4706-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4706-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4706-112">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c4706-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c4706-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c4706-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4706-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4706-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

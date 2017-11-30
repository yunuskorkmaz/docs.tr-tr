---
title: "ICorDebugThread::CreateStepper Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.CreateStepper
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::CreateStepper
helpviewer_keywords:
- ICorDebugThread::CreateStepper method [.NET Framework debugging]
- CreateStepper method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 4657443f-dd12-431b-a648-175c23f13c83
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b66c3e536104a46b65c92fe038fb5a92d79db299
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthreadcreatestepper-method"></a><span data-ttu-id="7821d-102">ICorDebugThread::CreateStepper Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7821d-102">ICorDebugThread::CreateStepper Method</span></span>
<span data-ttu-id="7821d-103">Bu Icordebugthread etkin çerçevesi atlama izin veren bir ICorDebugStepper nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7821d-103">Creates an ICorDebugStepper object that allows stepping through the active frame of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7821d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7821d-104">Syntax</span></span>  
  
```  
HRESULT CreateStepper (  
    [out] ICorDebugStepper **ppStepper  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7821d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7821d-105">Parameters</span></span>  
 `ppStepper`  
 <span data-ttu-id="7821d-106">[out] Adresine bir işaretçi bir `ICorDebugStepper` bu iş parçacığının etkin çerçevesi atlama izin veren nesnesi.</span><span class="sxs-lookup"><span data-stu-id="7821d-106">[out] A pointer to the address of an `ICorDebugStepper` object that allows stepping through the active frame of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7821d-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7821d-107">Remarks</span></span>  
 <span data-ttu-id="7821d-108">Yönetilmeyen kod etkin çerçeveyi olabilir.</span><span class="sxs-lookup"><span data-stu-id="7821d-108">The active frame may be unmanaged code.</span></span>  
  
 <span data-ttu-id="7821d-109">`ICorDebugStepper` Arabirimi, gerçek atlama gerçekleştirmek için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7821d-109">The `ICorDebugStepper` interface must be used to perform the actual stepping.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7821d-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7821d-110">Requirements</span></span>  
 <span data-ttu-id="7821d-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7821d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7821d-112">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7821d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7821d-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7821d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7821d-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7821d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

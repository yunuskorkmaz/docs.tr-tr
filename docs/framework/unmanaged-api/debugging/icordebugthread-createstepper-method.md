---
title: ICorDebugThread::CreateStepper Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugThread.CreateStepper
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::CreateStepper
helpviewer_keywords:
- ICorDebugThread::CreateStepper method [.NET Framework debugging]
- CreateStepper method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 4657443f-dd12-431b-a648-175c23f13c83
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 89182739633984011aaab3d7900d376b6db5ef99
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57476210"
---
# <a name="icordebugthreadcreatestepper-method"></a><span data-ttu-id="4f8eb-102">ICorDebugThread::CreateStepper Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4f8eb-102">ICorDebugThread::CreateStepper Method</span></span>
<span data-ttu-id="4f8eb-103">Bu Icordebugthread etkin çerçeveye Adımlama izin veren bir ICorDebugStepper nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4f8eb-103">Creates an ICorDebugStepper object that allows stepping through the active frame of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f8eb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4f8eb-104">Syntax</span></span>  
  
```  
HRESULT CreateStepper (  
    [out] ICorDebugStepper **ppStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4f8eb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4f8eb-105">Parameters</span></span>  
 `ppStepper`  
 <span data-ttu-id="4f8eb-106">[out] Adresine bir işaretçi bir `ICorDebugStepper` bu iş parçacığının etkin çerçeveye Adımlama sağlayan nesne.</span><span class="sxs-lookup"><span data-stu-id="4f8eb-106">[out] A pointer to the address of an `ICorDebugStepper` object that allows stepping through the active frame of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4f8eb-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4f8eb-107">Remarks</span></span>  
 <span data-ttu-id="4f8eb-108">Yönetilmeyen kod etkin olabilir.</span><span class="sxs-lookup"><span data-stu-id="4f8eb-108">The active frame may be unmanaged code.</span></span>  
  
 <span data-ttu-id="4f8eb-109">`ICorDebugStepper` Arabirimi, gerçek Adımlama gerçekleştirmek için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4f8eb-109">The `ICorDebugStepper` interface must be used to perform the actual stepping.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f8eb-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4f8eb-110">Requirements</span></span>  
 <span data-ttu-id="4f8eb-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f8eb-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f8eb-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4f8eb-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4f8eb-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4f8eb-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4f8eb-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f8eb-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

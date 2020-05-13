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
ms.openlocfilehash: a74d32478bc88ee634fa5ff9b61ac2059bc8e302
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379712"
---
# <a name="icordebugthreadcreatestepper-method"></a><span data-ttu-id="9b92f-102">ICorDebugThread::CreateStepper Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9b92f-102">ICorDebugThread::CreateStepper Method</span></span>
<span data-ttu-id="9b92f-103">Bu ICorDebugThread 'in etkin çerçevesiyle Adımlama sağlayan bir ICorDebugStepper nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9b92f-103">Creates an ICorDebugStepper object that allows stepping through the active frame of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b92f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9b92f-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateStepper (  
    [out] ICorDebugStepper **ppStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b92f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9b92f-105">Parameters</span></span>  
 `ppStepper`  
 <span data-ttu-id="9b92f-106">dışı `ICorDebugStepper`Bu iş parçacığının etkin çerçevesinin üzerinde Adımlama sağlayan bir nesnenin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9b92f-106">[out] A pointer to the address of an `ICorDebugStepper` object that allows stepping through the active frame of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9b92f-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9b92f-107">Remarks</span></span>  
 <span data-ttu-id="9b92f-108">Etkin çerçeve yönetilmeyen bir kod olabilir.</span><span class="sxs-lookup"><span data-stu-id="9b92f-108">The active frame may be unmanaged code.</span></span>  
  
 <span data-ttu-id="9b92f-109">Bu `ICorDebugStepper` arabirim, gerçek adımlamayı gerçekleştirmek için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9b92f-109">The `ICorDebugStepper` interface must be used to perform the actual stepping.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b92f-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9b92f-110">Requirements</span></span>  
 <span data-ttu-id="9b92f-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b92f-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b92f-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9b92f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9b92f-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9b92f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b92f-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b92f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

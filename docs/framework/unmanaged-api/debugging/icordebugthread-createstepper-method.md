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
ms.openlocfilehash: d1b058aef66ed32c2cadcc3cfd72320dd8eb7729
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133588"
---
# <a name="icordebugthreadcreatestepper-method"></a><span data-ttu-id="6fa2a-102">ICorDebugThread::CreateStepper Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6fa2a-102">ICorDebugThread::CreateStepper Method</span></span>
<span data-ttu-id="6fa2a-103">Bu ICorDebugThread 'in etkin çerçevesiyle Adımlama sağlayan bir ICorDebugStepper nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6fa2a-103">Creates an ICorDebugStepper object that allows stepping through the active frame of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fa2a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6fa2a-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateStepper (  
    [out] ICorDebugStepper **ppStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6fa2a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6fa2a-105">Parameters</span></span>  
 `ppStepper`  
 <span data-ttu-id="6fa2a-106">dışı Bu iş parçacığının etkin çerçevesinde Adımlama sağlayan bir `ICorDebugStepper` nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6fa2a-106">[out] A pointer to the address of an `ICorDebugStepper` object that allows stepping through the active frame of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6fa2a-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6fa2a-107">Remarks</span></span>  
 <span data-ttu-id="6fa2a-108">Etkin çerçeve yönetilmeyen bir kod olabilir.</span><span class="sxs-lookup"><span data-stu-id="6fa2a-108">The active frame may be unmanaged code.</span></span>  
  
 <span data-ttu-id="6fa2a-109">`ICorDebugStepper` arabirimi, gerçek adımlamayı gerçekleştirmek için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6fa2a-109">The `ICorDebugStepper` interface must be used to perform the actual stepping.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6fa2a-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6fa2a-110">Requirements</span></span>  
 <span data-ttu-id="6fa2a-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6fa2a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6fa2a-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6fa2a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6fa2a-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6fa2a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6fa2a-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6fa2a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

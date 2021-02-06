---
description: ': ICorDebugThread:: CreateStepper yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 378ce28281f4f284c36194f993a53598a9de3854
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659367"
---
# <a name="icordebugthreadcreatestepper-method"></a><span data-ttu-id="a5ff4-103">ICorDebugThread::CreateStepper Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a5ff4-103">ICorDebugThread::CreateStepper Method</span></span>

<span data-ttu-id="a5ff4-104">Bu ICorDebugThread 'in etkin çerçevesiyle Adımlama sağlayan bir ICorDebugStepper nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a5ff4-104">Creates an ICorDebugStepper object that allows stepping through the active frame of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5ff4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a5ff4-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateStepper (  
    [out] ICorDebugStepper **ppStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a5ff4-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a5ff4-106">Parameters</span></span>  

 `ppStepper`  
 <span data-ttu-id="a5ff4-107">dışı `ICorDebugStepper` Bu iş parçacığının etkin çerçevesinin üzerinde Adımlama sağlayan bir nesnenin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a5ff4-107">[out] A pointer to the address of an `ICorDebugStepper` object that allows stepping through the active frame of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5ff4-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a5ff4-108">Remarks</span></span>  

 <span data-ttu-id="a5ff4-109">Etkin çerçeve yönetilmeyen bir kod olabilir.</span><span class="sxs-lookup"><span data-stu-id="a5ff4-109">The active frame may be unmanaged code.</span></span>  
  
 <span data-ttu-id="a5ff4-110">Bu `ICorDebugStepper` arabirim, gerçek adımlamayı gerçekleştirmek için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a5ff4-110">The `ICorDebugStepper` interface must be used to perform the actual stepping.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5ff4-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a5ff4-111">Requirements</span></span>  

 <span data-ttu-id="a5ff4-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5ff4-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5ff4-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a5ff4-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a5ff4-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a5ff4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a5ff4-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5ff4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

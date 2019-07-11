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
ms.openlocfilehash: 95a00e8646589e7897636c1698b7c2647cd233fd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771806"
---
# <a name="icordebugthreadcreatestepper-method"></a><span data-ttu-id="e6cbc-102">ICorDebugThread::CreateStepper Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e6cbc-102">ICorDebugThread::CreateStepper Method</span></span>
<span data-ttu-id="e6cbc-103">Bu Icordebugthread etkin çerçeveye Adımlama izin veren bir ICorDebugStepper nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e6cbc-103">Creates an ICorDebugStepper object that allows stepping through the active frame of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6cbc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e6cbc-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateStepper (  
    [out] ICorDebugStepper **ppStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e6cbc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e6cbc-105">Parameters</span></span>  
 `ppStepper`  
 <span data-ttu-id="e6cbc-106">[out] Adresine bir işaretçi bir `ICorDebugStepper` bu iş parçacığının etkin çerçeveye Adımlama sağlayan nesne.</span><span class="sxs-lookup"><span data-stu-id="e6cbc-106">[out] A pointer to the address of an `ICorDebugStepper` object that allows stepping through the active frame of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e6cbc-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e6cbc-107">Remarks</span></span>  
 <span data-ttu-id="e6cbc-108">Yönetilmeyen kod etkin olabilir.</span><span class="sxs-lookup"><span data-stu-id="e6cbc-108">The active frame may be unmanaged code.</span></span>  
  
 <span data-ttu-id="e6cbc-109">`ICorDebugStepper` Arabirimi, gerçek Adımlama gerçekleştirmek için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e6cbc-109">The `ICorDebugStepper` interface must be used to perform the actual stepping.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6cbc-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e6cbc-110">Requirements</span></span>  
 <span data-ttu-id="e6cbc-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6cbc-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6cbc-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e6cbc-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e6cbc-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e6cbc-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e6cbc-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6cbc-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

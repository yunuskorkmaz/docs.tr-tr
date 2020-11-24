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
ms.openlocfilehash: dcaa5adc41a9e451b123b088dd900f01d9161689
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688283"
---
# <a name="icordebugthreadcreatestepper-method"></a><span data-ttu-id="52480-102">ICorDebugThread::CreateStepper Yöntemi</span><span class="sxs-lookup"><span data-stu-id="52480-102">ICorDebugThread::CreateStepper Method</span></span>

<span data-ttu-id="52480-103">Bu ICorDebugThread 'in etkin çerçevesiyle Adımlama sağlayan bir ICorDebugStepper nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="52480-103">Creates an ICorDebugStepper object that allows stepping through the active frame of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52480-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="52480-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateStepper (  
    [out] ICorDebugStepper **ppStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="52480-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="52480-105">Parameters</span></span>  

 `ppStepper`  
 <span data-ttu-id="52480-106">dışı `ICorDebugStepper` Bu iş parçacığının etkin çerçevesinin üzerinde Adımlama sağlayan bir nesnenin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="52480-106">[out] A pointer to the address of an `ICorDebugStepper` object that allows stepping through the active frame of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="52480-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="52480-107">Remarks</span></span>  

 <span data-ttu-id="52480-108">Etkin çerçeve yönetilmeyen bir kod olabilir.</span><span class="sxs-lookup"><span data-stu-id="52480-108">The active frame may be unmanaged code.</span></span>  
  
 <span data-ttu-id="52480-109">Bu `ICorDebugStepper` arabirim, gerçek adımlamayı gerçekleştirmek için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="52480-109">The `ICorDebugStepper` interface must be used to perform the actual stepping.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52480-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="52480-110">Requirements</span></span>  

 <span data-ttu-id="52480-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52480-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52480-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="52480-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="52480-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="52480-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="52480-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52480-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

---
title: ICorDebug::Terminate Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebug.Terminate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::Terminate
helpviewer_keywords:
- Terminate method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::Terminate method [.NET Framework debugging]
ms.assetid: fffe5616-0896-4426-ab5e-21869b514883
topic_type:
- apiref
ms.openlocfilehash: 2d3f8360a1fb1164fd4e26f85246251409bee376
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788957"
---
# <a name="icordebugterminate-method"></a><span data-ttu-id="3f3e7-102">ICorDebug::Terminate Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3f3e7-102">ICorDebug::Terminate Method</span></span>
<span data-ttu-id="3f3e7-103">`ICorDebug` nesnesini sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-103">Terminates the `ICorDebug` object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3f3e7-104">hata ayıklamakta olan tüm işlemler için [ICorDebugManagedCallback:: ExitProcess](icordebugmanagedcallback-exitprocess-method.md) geri çağırması alınana kadar `Terminate` çağrılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-104">`Terminate` should not be called until an [ICorDebugManagedCallback::ExitProcess](icordebugmanagedcallback-exitprocess-method.md) callback has been received for all processes being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f3e7-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3f3e7-105">Syntax</span></span>  
  
```cpp  
HRESULT Terminate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="3f3e7-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3f3e7-106">Remarks</span></span>  
 <span data-ttu-id="3f3e7-107">`Terminate`, `ICorDebug` nesnesine artık gerek kalmadığında çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-107">`Terminate` must be called when the `ICorDebug` object is no longer needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f3e7-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3f3e7-108">Requirements</span></span>  
 <span data-ttu-id="3f3e7-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f3e7-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f3e7-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3f3e7-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3f3e7-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3f3e7-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3f3e7-112">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f3e7-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f3e7-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f3e7-113">See also</span></span>

- [<span data-ttu-id="3f3e7-114">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3f3e7-114">ICorDebug Interface</span></span>](icordebug-interface.md)

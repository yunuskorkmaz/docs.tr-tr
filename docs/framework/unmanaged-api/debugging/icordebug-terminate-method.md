---
description: ': ICorDebug:: Terminate yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: c2de27a47bfd4c364a09180c75109679234f3cae
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754296"
---
# <a name="icordebugterminate-method"></a><span data-ttu-id="1da19-103">ICorDebug::Terminate Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1da19-103">ICorDebug::Terminate Method</span></span>

<span data-ttu-id="1da19-104">Nesneyi sonlandırır `ICorDebug` .</span><span class="sxs-lookup"><span data-stu-id="1da19-104">Terminates the `ICorDebug` object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1da19-105">`Terminate` hata ayıklamakta olan tüm işlemler için [ICorDebugManagedCallback:: ExitProcess](icordebugmanagedcallback-exitprocess-method.md) geri çağırması alınana kadar çağrılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="1da19-105">`Terminate` should not be called until an [ICorDebugManagedCallback::ExitProcess](icordebugmanagedcallback-exitprocess-method.md) callback has been received for all processes being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1da19-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="1da19-106">Syntax</span></span>  
  
```cpp  
HRESULT Terminate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="1da19-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1da19-107">Remarks</span></span>  

 <span data-ttu-id="1da19-108">`Terminate``ICorDebug`nesne artık gerekli olmadığında çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1da19-108">`Terminate` must be called when the `ICorDebug` object is no longer needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1da19-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1da19-109">Requirements</span></span>  

 <span data-ttu-id="1da19-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1da19-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1da19-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1da19-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1da19-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1da19-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1da19-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1da19-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1da19-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1da19-114">See also</span></span>

- [<span data-ttu-id="1da19-115">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1da19-115">ICorDebug Interface</span></span>](icordebug-interface.md)

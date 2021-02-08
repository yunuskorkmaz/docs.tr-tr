---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugThread2:: Yakatcurrentexception yöntemi'
title: ICorDebugThread2::InterceptCurrentException Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.InterceptCurrentException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::InterceptCurrentException
helpviewer_keywords:
- InterceptCurrentException method [.NET Framework debugging]
- ICorDebugThread2::InterceptCurrentException method [.NET Framework debugging]
ms.assetid: 536d2357-1b97-49e0-a10c-c860aed74e6e
topic_type:
- apiref
ms.openlocfilehash: 5bf8d3adf6f5e4a24d8fc5abddb72c0c8963c142
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790721"
---
# <a name="icordebugthread2interceptcurrentexception-method"></a><span data-ttu-id="b1fb4-103">ICorDebugThread2::InterceptCurrentException Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b1fb4-103">ICorDebugThread2::InterceptCurrentException Method</span></span>

<span data-ttu-id="b1fb4-104">Bir hata ayıklayıcının bu iş parçacığında geçerli özel durumu kesmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="b1fb4-104">Allows a debugger to intercept the current exception on this thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1fb4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b1fb4-105">Syntax</span></span>  
  
```cpp  
HRESULT InterceptCurrentException (  
    [in] ICorDebugFrame  *pFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1fb4-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b1fb4-106">Parameters</span></span>  

 `pFrame`  
 <span data-ttu-id="b1fb4-107">'ndaki Etkin yığın çerçevesini temsil eden bir ICorDebugFrame işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="b1fb4-107">[in] A pointer to an ICorDebugFrame that represents the active stack frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1fb4-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b1fb4-108">Remarks</span></span>  

 <span data-ttu-id="b1fb4-109">`InterceptCurrentException`Yöntem bir özel durum geri çağırması ([ICorDebugManagedCallback:: Exception](icordebugmanagedcallback-exception-method.md) veya [ICorDebugManagedCallback2:: Exception](icordebugmanagedcallback2-exception-method.md)) Ile ilişkili [ICorDebugController:: Continue](icordebugcontroller-continue-method.md)öğesine yapılan çağrı arasında çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="b1fb4-109">The `InterceptCurrentException` method can be called between an exception callback ([ICorDebugManagedCallback::Exception](icordebugmanagedcallback-exception-method.md) or [ICorDebugManagedCallback2::Exception](icordebugmanagedcallback2-exception-method.md)) and the associated call to [ICorDebugController::Continue](icordebugcontroller-continue-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1fb4-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b1fb4-110">Requirements</span></span>  

 <span data-ttu-id="b1fb4-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1fb4-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1fb4-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b1fb4-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b1fb4-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b1fb4-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1fb4-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1fb4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

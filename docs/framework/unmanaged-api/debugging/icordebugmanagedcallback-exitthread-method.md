---
title: ICorDebugManagedCallback::ExitThread Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ExitThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ExitThread
helpviewer_keywords:
- ExitThread method [.NET Framework debugging]
- ICorDebugManagedCallback::ExitThread method [.NET Framework debugging]
ms.assetid: 62db708b-6cf0-45c5-b897-4b5c75bd2505
topic_type:
- apiref
ms.openlocfilehash: 2ccb06b974cb17dff987ba42b647224cdc4c4ff2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688962"
---
# <a name="icordebugmanagedcallbackexitthread-method"></a><span data-ttu-id="4c30b-102">ICorDebugManagedCallback::ExitThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4c30b-102">ICorDebugManagedCallback::ExitThread Method</span></span>

<span data-ttu-id="4c30b-103">Hata ayıklayıcıya yönetilen kodu yürüten bir iş parçacığının çıkış olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="4c30b-103">Notifies the debugger that a thread that was executing managed code has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c30b-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="4c30b-104">Syntax</span></span>  
  
```cpp  
HRESULT ExitThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4c30b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4c30b-105">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="4c30b-106">'ndaki Yönetilen iş parçacığını içeren uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4c30b-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread.</span></span>  
  
 `thread`  
 <span data-ttu-id="4c30b-107">'ndaki Yönetilen iş parçacığını temsil eden ICorDebugThread nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4c30b-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4c30b-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4c30b-108">Remarks</span></span>  

 <span data-ttu-id="4c30b-109">`ExitThread`Geri çağırma harekete geçirildiğinde, iş parçacığı artık iş parçacığı numaralandırmalar içinde görünmez.</span><span class="sxs-lookup"><span data-stu-id="4c30b-109">Once the `ExitThread` callback is fired, the thread will no longer appear in thread enumerations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c30b-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4c30b-110">Requirements</span></span>  

 <span data-ttu-id="4c30b-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c30b-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c30b-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4c30b-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4c30b-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="4c30b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4c30b-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c30b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c30b-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4c30b-115">See also</span></span>

- [<span data-ttu-id="4c30b-116">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4c30b-116">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)

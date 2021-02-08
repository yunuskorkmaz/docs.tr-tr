---
description: ': ICorDebugManagedCallback:: ExitThread Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 4c9472d6377246833c7c30f072549da9c44f05d8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790951"
---
# <a name="icordebugmanagedcallbackexitthread-method"></a><span data-ttu-id="9da8f-103">ICorDebugManagedCallback::ExitThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9da8f-103">ICorDebugManagedCallback::ExitThread Method</span></span>

<span data-ttu-id="9da8f-104">Hata ayıklayıcıya yönetilen kodu yürüten bir iş parçacığının çıkış olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="9da8f-104">Notifies the debugger that a thread that was executing managed code has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9da8f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9da8f-105">Syntax</span></span>  
  
```cpp  
HRESULT ExitThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9da8f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9da8f-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="9da8f-107">'ndaki Yönetilen iş parçacığını içeren uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9da8f-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread.</span></span>  
  
 `thread`  
 <span data-ttu-id="9da8f-108">'ndaki Yönetilen iş parçacığını temsil eden ICorDebugThread nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9da8f-108">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9da8f-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9da8f-109">Remarks</span></span>  

 <span data-ttu-id="9da8f-110">`ExitThread`Geri çağırma harekete geçirildiğinde, iş parçacığı artık iş parçacığı numaralandırmalar içinde görünmez.</span><span class="sxs-lookup"><span data-stu-id="9da8f-110">Once the `ExitThread` callback is fired, the thread will no longer appear in thread enumerations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9da8f-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9da8f-111">Requirements</span></span>  

 <span data-ttu-id="9da8f-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9da8f-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9da8f-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9da8f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9da8f-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9da8f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9da8f-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9da8f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9da8f-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9da8f-116">See also</span></span>

- [<span data-ttu-id="9da8f-117">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9da8f-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)

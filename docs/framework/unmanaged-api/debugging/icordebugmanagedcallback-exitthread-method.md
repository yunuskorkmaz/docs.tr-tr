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
ms.openlocfilehash: fa649fd1983a76c71d400ad3e6965ac0794da6ed
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781602"
---
# <a name="icordebugmanagedcallbackexitthread-method"></a><span data-ttu-id="b5f33-102">ICorDebugManagedCallback::ExitThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b5f33-102">ICorDebugManagedCallback::ExitThread Method</span></span>
<span data-ttu-id="b5f33-103">Hata ayıklayıcıya yönetilen kodu yürüten bir iş parçacığının çıkış olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="b5f33-103">Notifies the debugger that a thread that was executing managed code has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5f33-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b5f33-104">Syntax</span></span>  
  
```cpp  
HRESULT ExitThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b5f33-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b5f33-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="b5f33-106">'ndaki Yönetilen iş parçacığını içeren uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b5f33-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread.</span></span>  
  
 `thread`  
 <span data-ttu-id="b5f33-107">'ndaki Yönetilen iş parçacığını temsil eden ICorDebugThread nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b5f33-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b5f33-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b5f33-108">Remarks</span></span>  
 <span data-ttu-id="b5f33-109">`ExitThread` geri çağırması harekete geçirildiğinde, iş parçacığı artık iş parçacığı numaralandırmasında görünmez.</span><span class="sxs-lookup"><span data-stu-id="b5f33-109">Once the `ExitThread` callback is fired, the thread will no longer appear in thread enumerations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5f33-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b5f33-110">Requirements</span></span>  
 <span data-ttu-id="b5f33-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5f33-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5f33-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b5f33-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b5f33-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b5f33-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b5f33-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5f33-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5f33-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b5f33-115">See also</span></span>

- [<span data-ttu-id="b5f33-116">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b5f33-116">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)

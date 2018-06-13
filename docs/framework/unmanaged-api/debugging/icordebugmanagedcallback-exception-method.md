---
title: ICorDebugManagedCallback::Exception Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.Exception
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::Exception
helpviewer_keywords:
- Exception method, ICorDebugManagedCallback interface [.NET Framework debugging]
- ICorDebugManagedCallback::Exception method [.NET Framework debugging]
ms.assetid: ab18a509-dff3-4930-b585-bd15e0414176
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bf6152c643395fe52a43424cab33f527d577b5bd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413897"
---
# <a name="icordebugmanagedcallbackexception-method"></a><span data-ttu-id="95b66-102">ICorDebugManagedCallback::Exception Yöntemi</span><span class="sxs-lookup"><span data-stu-id="95b66-102">ICorDebugManagedCallback::Exception Method</span></span>
<span data-ttu-id="95b66-103">Hata ayıklayıcı yönetilen koddan bir özel durum olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="95b66-103">Notifies the debugger that an exception has been thrown from managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95b66-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="95b66-104">Syntax</span></span>  
  
```  
HRESULT Exception (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] BOOL                unhandled  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="95b66-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="95b66-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="95b66-106">[in] Bir işaretçi Icordebugappdomain nesneye özel durum oluştu uygulama etki alanını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="95b66-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="95b66-107">[in] Bir işaretçi Icordebugthread nesneye özel durum oluştu iş parçacığı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="95b66-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the exception was thrown.</span></span>  
  
 `unhandled`  
 <span data-ttu-id="95b66-108">[in] Bu değer ise `false`, özel durum henüz henüz uygulama tarafından işlenen; Aksi durumda, özel durum işlenmemiş ve işlemini sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="95b66-108">[in] If this value is `false`, the exception has not yet been processed by the application; otherwise, the exception is unhandled and will terminate the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="95b66-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="95b66-109">Remarks</span></span>  
 <span data-ttu-id="95b66-110">Bir özel durum iş parçacığı nesneden alınabilir.</span><span class="sxs-lookup"><span data-stu-id="95b66-110">The specific exception can be retrieved from the thread object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95b66-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="95b66-111">Requirements</span></span>  
 <span data-ttu-id="95b66-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95b66-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95b66-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="95b66-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="95b66-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="95b66-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="95b66-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95b66-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95b66-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="95b66-116">See Also</span></span>  
 [<span data-ttu-id="95b66-117">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="95b66-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

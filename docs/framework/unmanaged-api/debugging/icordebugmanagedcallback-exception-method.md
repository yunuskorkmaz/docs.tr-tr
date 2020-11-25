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
ms.openlocfilehash: 05fed13a556cbcc3b8362e41d73c2b659b1e5eeb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731793"
---
# <a name="icordebugmanagedcallbackexception-method"></a><span data-ttu-id="b418b-102">ICorDebugManagedCallback::Exception Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b418b-102">ICorDebugManagedCallback::Exception Method</span></span>

<span data-ttu-id="b418b-103">Hata ayıklayıcıya yönetilen koddan bir özel durum gerçekleştiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="b418b-103">Notifies the debugger that an exception has been thrown from managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b418b-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="b418b-104">Syntax</span></span>  
  
```cpp  
HRESULT Exception (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] BOOL                unhandled  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b418b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b418b-105">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="b418b-106">'ndaki Özel durumun oluşturulduğu uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b418b-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="b418b-107">'ndaki Özel durumun oluşturulduğu iş parçacığını temsil eden ICorDebugThread nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b418b-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the exception was thrown.</span></span>  
  
 `unhandled`  
 <span data-ttu-id="b418b-108">'ndaki Bu değer ise `false` , özel durum uygulama tarafından henüz işlenmemiştir; Aksi takdirde, özel durum işlenmemiş olur ve işlemi sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="b418b-108">[in] If this value is `false`, the exception has not yet been processed by the application; otherwise, the exception is unhandled and will terminate the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b418b-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b418b-109">Remarks</span></span>  

 <span data-ttu-id="b418b-110">Belirli özel durum iş parçacığı nesnesinden alınabilir.</span><span class="sxs-lookup"><span data-stu-id="b418b-110">The specific exception can be retrieved from the thread object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b418b-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b418b-111">Requirements</span></span>  

 <span data-ttu-id="b418b-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b418b-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b418b-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b418b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b418b-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b418b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b418b-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b418b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b418b-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b418b-116">See also</span></span>

- [<span data-ttu-id="b418b-117">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b418b-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)

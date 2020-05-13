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
ms.openlocfilehash: 2d0461709accf1a9300c072b62bd58734cb33fb8
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209819"
---
# <a name="icordebugmanagedcallbackexception-method"></a><span data-ttu-id="9b1cf-102">ICorDebugManagedCallback::Exception Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9b1cf-102">ICorDebugManagedCallback::Exception Method</span></span>
<span data-ttu-id="9b1cf-103">Hata ayıklayıcıya yönetilen koddan bir özel durum gerçekleştiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="9b1cf-103">Notifies the debugger that an exception has been thrown from managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b1cf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9b1cf-104">Syntax</span></span>  
  
```cpp  
HRESULT Exception (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] BOOL                unhandled  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b1cf-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9b1cf-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="9b1cf-106">'ndaki Özel durumun oluşturulduğu uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9b1cf-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="9b1cf-107">'ndaki Özel durumun oluşturulduğu iş parçacığını temsil eden ICorDebugThread nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9b1cf-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the exception was thrown.</span></span>  
  
 `unhandled`  
 <span data-ttu-id="9b1cf-108">'ndaki Bu değer ise `false` , özel durum uygulama tarafından henüz işlenmemiştir; Aksi takdirde, özel durum işlenmemiş olur ve işlemi sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="9b1cf-108">[in] If this value is `false`, the exception has not yet been processed by the application; otherwise, the exception is unhandled and will terminate the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9b1cf-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9b1cf-109">Remarks</span></span>  
 <span data-ttu-id="9b1cf-110">Belirli özel durum iş parçacığı nesnesinden alınabilir.</span><span class="sxs-lookup"><span data-stu-id="9b1cf-110">The specific exception can be retrieved from the thread object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b1cf-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9b1cf-111">Requirements</span></span>  
 <span data-ttu-id="9b1cf-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b1cf-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b1cf-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9b1cf-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9b1cf-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9b1cf-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b1cf-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b1cf-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b1cf-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9b1cf-116">See also</span></span>

- [<span data-ttu-id="9b1cf-117">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9b1cf-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)

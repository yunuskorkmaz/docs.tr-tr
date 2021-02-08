---
description: ': ICorDebugManagedCallback:: Exception yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: f738c328e1f6edfeb61a1d5e2ba8f9dd827d05dd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790977"
---
# <a name="icordebugmanagedcallbackexception-method"></a><span data-ttu-id="67e99-103">ICorDebugManagedCallback::Exception Yöntemi</span><span class="sxs-lookup"><span data-stu-id="67e99-103">ICorDebugManagedCallback::Exception Method</span></span>

<span data-ttu-id="67e99-104">Hata ayıklayıcıya yönetilen koddan bir özel durum gerçekleştiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="67e99-104">Notifies the debugger that an exception has been thrown from managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67e99-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="67e99-105">Syntax</span></span>  
  
```cpp  
HRESULT Exception (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] BOOL                unhandled  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="67e99-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="67e99-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="67e99-107">'ndaki Özel durumun oluşturulduğu uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="67e99-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="67e99-108">'ndaki Özel durumun oluşturulduğu iş parçacığını temsil eden ICorDebugThread nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="67e99-108">[in] A pointer to an ICorDebugThread object that represents the thread in which the exception was thrown.</span></span>  
  
 `unhandled`  
 <span data-ttu-id="67e99-109">'ndaki Bu değer ise `false` , özel durum uygulama tarafından henüz işlenmemiştir; Aksi takdirde, özel durum işlenmemiş olur ve işlemi sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="67e99-109">[in] If this value is `false`, the exception has not yet been processed by the application; otherwise, the exception is unhandled and will terminate the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="67e99-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="67e99-110">Remarks</span></span>  

 <span data-ttu-id="67e99-111">Belirli özel durum iş parçacığı nesnesinden alınabilir.</span><span class="sxs-lookup"><span data-stu-id="67e99-111">The specific exception can be retrieved from the thread object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67e99-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="67e99-112">Requirements</span></span>  

 <span data-ttu-id="67e99-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67e99-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67e99-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="67e99-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="67e99-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="67e99-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="67e99-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67e99-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67e99-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="67e99-117">See also</span></span>

- [<span data-ttu-id="67e99-118">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="67e99-118">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)

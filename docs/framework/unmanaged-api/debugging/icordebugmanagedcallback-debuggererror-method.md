---
title: "ICorDebugManagedCallback::DebuggerError Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.DebuggerError
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::DebuggerError
helpviewer_keywords:
- DebuggerError method [.NET Framework debugging]
- ICorDebugManagedCallback::DebuggerError method [.NET Framework debugging]
ms.assetid: 9e983d11-eaf3-4741-b936-29ec456384a3
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cc92bc6a1718d9d3505443e5b13786d1a359481f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbackdebuggererror-method"></a><span data-ttu-id="c8518-102">ICorDebugManagedCallback::DebuggerError Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c8518-102">ICorDebugManagedCallback::DebuggerError Method</span></span>
<span data-ttu-id="c8518-103">Ortak dil çalışma zamanı (CLR) bir olay işlemeye çalışırken bir hata oluştu hata ayıklayıcı bildirir.</span><span class="sxs-lookup"><span data-stu-id="c8518-103">Notifies the debugger that an error has occurred while attempting to handle an event from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8518-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c8518-104">Syntax</span></span>  
  
```  
HRESULT DebuggerError (  
    [in] ICorDebugProcess *pProcess,  
    [in] HRESULT           errorHR,  
    [in] DWORD             errorCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c8518-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c8518-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="c8518-106">[in] Olayın meydana geldiği işlemi temsil eden bir "ICorDebugProcess" nesnesi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c8518-106">[in] A pointer to an "ICorDebugProcess" object that represents the process in which the event occurred.</span></span>  
  
 `errorHR`  
 <span data-ttu-id="c8518-107">[in] Olay işleyiciden döndürülen HRESULT değeri.</span><span class="sxs-lookup"><span data-stu-id="c8518-107">[in] The HRESULT value that was returned from the event handler.</span></span>  
  
 `errorCode`  
 <span data-ttu-id="c8518-108">[in] CLR hata belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="c8518-108">[in] An integer that specifies the CLR error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c8518-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c8518-109">Remarks</span></span>  
 <span data-ttu-id="c8518-110">İşlem hatası doğasına bağlı olarak geçiş moduna yerleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="c8518-110">The process may be placed into pass-through mode, depending on the nature of the error.</span></span>  
  
 <span data-ttu-id="c8518-111">`DebugError` Geri çağırma hata ayıklayıcıları hata iletisinin kullanıcıya kullanılabilmesini böylece hata ayıklama Hizmetleri bir hata nedeniyle devre dışı bırakılmış olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="c8518-111">The `DebugError` callback indicates that debugging services have been disabled due to an error, so debuggers should make the error message available to the user.</span></span> <span data-ttu-id="c8518-112">[Icordebugprocess::GetID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md) çağrısı ancak dahil olmak üzere tüm diğer yöntemleri, güvenli olacak [Icordebug::Terminate](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md), çağrılmamalı.</span><span class="sxs-lookup"><span data-stu-id="c8518-112">[ICorDebugProcess::GetID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md) will be safe to call, but all other methods, including [ICorDebug::Terminate](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md), should not be called.</span></span> <span data-ttu-id="c8518-113">Hata ayıklayıcı işlemleri sona erdirmek için işletim sistemi özellikleri kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c8518-113">The debugger should use operating-system facilities for terminating processes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8518-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c8518-114">Requirements</span></span>  
 <span data-ttu-id="c8518-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8518-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8518-116">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c8518-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c8518-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c8518-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c8518-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8518-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8518-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c8518-119">See Also</span></span>  
 [<span data-ttu-id="c8518-120">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c8518-120">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

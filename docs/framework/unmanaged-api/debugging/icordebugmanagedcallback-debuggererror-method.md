---
title: ICorDebugManagedCallback::DebuggerError Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.DebuggerError
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::DebuggerError
helpviewer_keywords:
- DebuggerError method [.NET Framework debugging]
- ICorDebugManagedCallback::DebuggerError method [.NET Framework debugging]
ms.assetid: 9e983d11-eaf3-4741-b936-29ec456384a3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fd7909b94343b1fb83836f5c369ddc1993f049d2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59191180"
---
# <a name="icordebugmanagedcallbackdebuggererror-method"></a><span data-ttu-id="af9c8-102">ICorDebugManagedCallback::DebuggerError Yöntemi</span><span class="sxs-lookup"><span data-stu-id="af9c8-102">ICorDebugManagedCallback::DebuggerError Method</span></span>
<span data-ttu-id="af9c8-103">Ortak dil çalışma zamanı (CLR) bir olaydan işlemeye çalışırken bir hata oluştu, hata ayıklayıcı bildirir.</span><span class="sxs-lookup"><span data-stu-id="af9c8-103">Notifies the debugger that an error has occurred while attempting to handle an event from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af9c8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="af9c8-104">Syntax</span></span>  
  
```  
HRESULT DebuggerError (  
    [in] ICorDebugProcess *pProcess,  
    [in] HRESULT           errorHR,  
    [in] DWORD             errorCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af9c8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="af9c8-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="af9c8-106">[in] Olayın gerçekleştiği işlemini temsil eden bir "ICorDebugProcess" nesneye bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="af9c8-106">[in] A pointer to an "ICorDebugProcess" object that represents the process in which the event occurred.</span></span>  
  
 `errorHR`  
 <span data-ttu-id="af9c8-107">[in] Olay işleyicisinden döndürülen HRESULT değerini.</span><span class="sxs-lookup"><span data-stu-id="af9c8-107">[in] The HRESULT value that was returned from the event handler.</span></span>  
  
 `errorCode`  
 <span data-ttu-id="af9c8-108">[in] CLR hata belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="af9c8-108">[in] An integer that specifies the CLR error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af9c8-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="af9c8-109">Remarks</span></span>  
 <span data-ttu-id="af9c8-110">İşlem hata doğasına bağlı olarak doğrudan modu içine yerleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="af9c8-110">The process may be placed into pass-through mode, depending on the nature of the error.</span></span>  
  
 <span data-ttu-id="af9c8-111">`DebugError` Geri çağırma, hata ayıklayıcıları hata iletisinin kullanıcıya kullanılabilmesini için hata ayıklama Hizmetleri bir hata nedeniyle devre dışı bırakılmış olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="af9c8-111">The `DebugError` callback indicates that debugging services have been disabled due to an error, so debuggers should make the error message available to the user.</span></span> <span data-ttu-id="af9c8-112">[Icordebugprocess::GetID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md) çağrısı ancak dahil olmak üzere tüm diğer yöntemler, güvenli olacak [Icordebug::Terminate](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md), çağrılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="af9c8-112">[ICorDebugProcess::GetID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md) will be safe to call, but all other methods, including [ICorDebug::Terminate](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md), should not be called.</span></span> <span data-ttu-id="af9c8-113">Hata ayıklayıcı, işlemleri sonlandırmak için işletim sistemi özelliklerini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="af9c8-113">The debugger should use operating-system facilities for terminating processes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af9c8-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="af9c8-114">Requirements</span></span>  
 <span data-ttu-id="af9c8-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af9c8-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af9c8-116">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="af9c8-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="af9c8-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="af9c8-117">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="af9c8-118">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="af9c8-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="af9c8-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af9c8-119">See also</span></span>

- [<span data-ttu-id="af9c8-120">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="af9c8-120">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

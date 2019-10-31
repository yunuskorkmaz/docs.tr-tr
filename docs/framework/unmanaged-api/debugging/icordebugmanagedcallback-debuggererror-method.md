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
ms.openlocfilehash: c03be2405e1ab0287a2921b6e2e293862c67a193
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137367"
---
# <a name="icordebugmanagedcallbackdebuggererror-method"></a><span data-ttu-id="e3698-102">ICorDebugManagedCallback::DebuggerError Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e3698-102">ICorDebugManagedCallback::DebuggerError Method</span></span>
<span data-ttu-id="e3698-103">Ortak dil çalışma zamanından (CLR) bir olayı işlemeye çalışırken hata ayıklayıcıya bir hata oluştuğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="e3698-103">Notifies the debugger that an error has occurred while attempting to handle an event from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3698-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e3698-104">Syntax</span></span>  
  
```cpp  
HRESULT DebuggerError (  
    [in] ICorDebugProcess *pProcess,  
    [in] HRESULT           errorHR,  
    [in] DWORD             errorCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e3698-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e3698-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="e3698-106">'ndaki Olayın gerçekleştiği işlemi temsil eden bir "ICorDebugProcess" nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e3698-106">[in] A pointer to an "ICorDebugProcess" object that represents the process in which the event occurred.</span></span>  
  
 `errorHR`  
 <span data-ttu-id="e3698-107">'ndaki Olay işleyicisinden döndürülen HRESULT değeri.</span><span class="sxs-lookup"><span data-stu-id="e3698-107">[in] The HRESULT value that was returned from the event handler.</span></span>  
  
 `errorCode`  
 <span data-ttu-id="e3698-108">'ndaki CLR hatasını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="e3698-108">[in] An integer that specifies the CLR error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e3698-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e3698-109">Remarks</span></span>  
 <span data-ttu-id="e3698-110">İşlem, hatanın doğasına bağlı olarak doğrudan geçiş moduna yerleştirilebilecek.</span><span class="sxs-lookup"><span data-stu-id="e3698-110">The process may be placed into pass-through mode, depending on the nature of the error.</span></span>  
  
 <span data-ttu-id="e3698-111">`DebugError` geri çağırması hata nedeniyle hata ayıklama Hizmetleri 'nin devre dışı bırakıldığını belirtir, bu nedenle hata ayıklayıcılar hata iletisini Kullanıcı için kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="e3698-111">The `DebugError` callback indicates that debugging services have been disabled due to an error, so debuggers should make the error message available to the user.</span></span> <span data-ttu-id="e3698-112">[ICorDebugProcess:: GetID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md) çağrısı güvenli olacak, ancak [ICorDebug:: Terminate](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md)dahil diğer tüm yöntemler çağrılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="e3698-112">[ICorDebugProcess::GetID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md) will be safe to call, but all other methods, including [ICorDebug::Terminate](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md), should not be called.</span></span> <span data-ttu-id="e3698-113">Hata ayıklayıcı, işlem sonlandırmakta olan işletim sistemi tesislerini kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e3698-113">The debugger should use operating-system facilities for terminating processes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3698-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e3698-114">Requirements</span></span>  
 <span data-ttu-id="e3698-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3698-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3698-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e3698-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e3698-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e3698-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e3698-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3698-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3698-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e3698-119">See also</span></span>

- [<span data-ttu-id="e3698-120">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e3698-120">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

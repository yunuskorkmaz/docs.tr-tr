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
ms.openlocfilehash: 8f3697f8b193319ebb7b155ad79b8ec25a0a2266
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205271"
---
# <a name="icordebugmanagedcallbackdebuggererror-method"></a><span data-ttu-id="7aef4-102">ICorDebugManagedCallback::DebuggerError Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7aef4-102">ICorDebugManagedCallback::DebuggerError Method</span></span>
<span data-ttu-id="7aef4-103">Ortak dil çalışma zamanından (CLR) bir olayı işlemeye çalışırken hata ayıklayıcıya bir hata oluştuğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="7aef4-103">Notifies the debugger that an error has occurred while attempting to handle an event from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7aef4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7aef4-104">Syntax</span></span>  
  
```cpp  
HRESULT DebuggerError (  
    [in] ICorDebugProcess *pProcess,  
    [in] HRESULT           errorHR,  
    [in] DWORD             errorCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7aef4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7aef4-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="7aef4-106">'ndaki Olayın gerçekleştiği işlemi temsil eden bir "ICorDebugProcess" nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7aef4-106">[in] A pointer to an "ICorDebugProcess" object that represents the process in which the event occurred.</span></span>  
  
 `errorHR`  
 <span data-ttu-id="7aef4-107">'ndaki Olay işleyicisinden döndürülen HRESULT değeri.</span><span class="sxs-lookup"><span data-stu-id="7aef4-107">[in] The HRESULT value that was returned from the event handler.</span></span>  
  
 `errorCode`  
 <span data-ttu-id="7aef4-108">'ndaki CLR hatasını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="7aef4-108">[in] An integer that specifies the CLR error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7aef4-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7aef4-109">Remarks</span></span>  
 <span data-ttu-id="7aef4-110">İşlem, hatanın doğasına bağlı olarak doğrudan geçiş moduna yerleştirilebilecek.</span><span class="sxs-lookup"><span data-stu-id="7aef4-110">The process may be placed into pass-through mode, depending on the nature of the error.</span></span>  
  
 <span data-ttu-id="7aef4-111">`DebugError`Geri çağırma, hata nedeniyle hata ayıklama hizmetlerinin devre dışı bırakıldığını gösterir, bu nedenle hata ayıklayıcılar hata iletisini Kullanıcı için kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="7aef4-111">The `DebugError` callback indicates that debugging services have been disabled due to an error, so debuggers should make the error message available to the user.</span></span> <span data-ttu-id="7aef4-112">[ICorDebugProcess:: GetID](icordebugprocess-getid-method.md) çağrısı güvenli olacak, ancak [ICorDebug:: Terminate](icordebug-terminate-method.md)dahil diğer tüm yöntemler çağrılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="7aef4-112">[ICorDebugProcess::GetID](icordebugprocess-getid-method.md) will be safe to call, but all other methods, including [ICorDebug::Terminate](icordebug-terminate-method.md), should not be called.</span></span> <span data-ttu-id="7aef4-113">Hata ayıklayıcı, işlem sonlandırmakta olan işletim sistemi tesislerini kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7aef4-113">The debugger should use operating-system facilities for terminating processes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7aef4-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7aef4-114">Requirements</span></span>  
 <span data-ttu-id="7aef4-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7aef4-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7aef4-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7aef4-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7aef4-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7aef4-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7aef4-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7aef4-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7aef4-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7aef4-119">See also</span></span>

- [<span data-ttu-id="7aef4-120">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7aef4-120">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)

---
title: ICorDebugManagedCallback::ExitProcess Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ExitProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ExitProcess
helpviewer_keywords:
- ExitProcess method, ICorDebugManagedCallback interface [.NET Framework debugging]
- ICorDebugManagedCallback::ExitProcess method [.NET Framework debugging]
ms.assetid: 63a7d47a-0d54-4e29-9767-9f09feaa38b7
topic_type:
- apiref
ms.openlocfilehash: 7a49bd6626518179c9b5ef008fca28d304537cc8
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205257"
---
# <a name="icordebugmanagedcallbackexitprocess-method"></a><span data-ttu-id="605d9-102">ICorDebugManagedCallback::ExitProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="605d9-102">ICorDebugManagedCallback::ExitProcess Method</span></span>
<span data-ttu-id="605d9-103">Hata ayıklayıcıya bir işlemin çıkış olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="605d9-103">Notifies the debugger that a process has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="605d9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="605d9-104">Syntax</span></span>  
  
```cpp  
HRESULT ExitProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="605d9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="605d9-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="605d9-106">'ndaki İşlemi temsil eden ICorDebugProcess nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="605d9-106">[in] A pointer to an ICorDebugProcess object that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="605d9-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="605d9-107">Remarks</span></span>  
 <span data-ttu-id="605d9-108">Bir olaydan devam edemezsiniz `ExitProcess` .</span><span class="sxs-lookup"><span data-stu-id="605d9-108">You cannot continue from an `ExitProcess` event.</span></span> <span data-ttu-id="605d9-109">Bu olay, işlem durdurulmuş olarak göründüğü sırada diğer olaylara zaman uyumsuz olarak harekete çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="605d9-109">This event may fire asynchronously to other events while the process appears to be stopped.</span></span> <span data-ttu-id="605d9-110">Bu durum, genellikle bazı harici bir zorlamalı nedeniyle işlem durdurulduğunda sonlandırıldığında meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="605d9-110">This can occur if the process terminates while stopped, usually due to some external force.</span></span>  
  
 <span data-ttu-id="605d9-111">Ortak dil çalışma zamanı (CLR) zaten yönetilen bir geri çağırma gönderiyor ise bu olay, geri çağırma geri dönene kadar gecikecek.</span><span class="sxs-lookup"><span data-stu-id="605d9-111">If the common language runtime (CLR) is already dispatching a managed callback, this event will be delayed until after that callback has returned.</span></span>  
  
 <span data-ttu-id="605d9-112">`ExitProcess`Olay, kapatılırken çağrılmanın garanti edilmesi gereken tek çıkış/kaldırma olayıdır.</span><span class="sxs-lookup"><span data-stu-id="605d9-112">The `ExitProcess` event is the only exit/unload event that is guaranteed to get called on shutdown.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="605d9-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="605d9-113">Requirements</span></span>  
 <span data-ttu-id="605d9-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="605d9-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="605d9-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="605d9-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="605d9-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="605d9-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="605d9-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="605d9-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="605d9-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="605d9-118">See also</span></span>

- [<span data-ttu-id="605d9-119">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="605d9-119">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)

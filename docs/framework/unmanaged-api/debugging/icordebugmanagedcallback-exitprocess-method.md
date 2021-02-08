---
description: ': ICorDebugManagedCallback:: ExitProcess yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 3418931b8397edefcb801986275c35b28e00072d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790964"
---
# <a name="icordebugmanagedcallbackexitprocess-method"></a><span data-ttu-id="f3e2e-103">ICorDebugManagedCallback::ExitProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f3e2e-103">ICorDebugManagedCallback::ExitProcess Method</span></span>

<span data-ttu-id="f3e2e-104">Hata ayıklayıcıya bir işlemin çıkış olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="f3e2e-104">Notifies the debugger that a process has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3e2e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f3e2e-105">Syntax</span></span>  
  
```cpp  
HRESULT ExitProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3e2e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f3e2e-106">Parameters</span></span>  

 `pProcess`  
 <span data-ttu-id="f3e2e-107">'ndaki İşlemi temsil eden ICorDebugProcess nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f3e2e-107">[in] A pointer to an ICorDebugProcess object that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f3e2e-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f3e2e-108">Remarks</span></span>  

 <span data-ttu-id="f3e2e-109">Bir olaydan devam edemezsiniz `ExitProcess` .</span><span class="sxs-lookup"><span data-stu-id="f3e2e-109">You cannot continue from an `ExitProcess` event.</span></span> <span data-ttu-id="f3e2e-110">Bu olay, işlem durdurulmuş olarak göründüğü sırada diğer olaylara zaman uyumsuz olarak harekete çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="f3e2e-110">This event may fire asynchronously to other events while the process appears to be stopped.</span></span> <span data-ttu-id="f3e2e-111">Bu durum, genellikle bazı harici bir zorlamalı nedeniyle işlem durdurulduğunda sonlandırıldığında meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="f3e2e-111">This can occur if the process terminates while stopped, usually due to some external force.</span></span>  
  
 <span data-ttu-id="f3e2e-112">Ortak dil çalışma zamanı (CLR) zaten yönetilen bir geri çağırma gönderiyor ise bu olay, geri çağırma geri dönene kadar gecikecek.</span><span class="sxs-lookup"><span data-stu-id="f3e2e-112">If the common language runtime (CLR) is already dispatching a managed callback, this event will be delayed until after that callback has returned.</span></span>  
  
 <span data-ttu-id="f3e2e-113">`ExitProcess`Olay, kapatılırken çağrılmanın garanti edilmesi gereken tek çıkış/kaldırma olayıdır.</span><span class="sxs-lookup"><span data-stu-id="f3e2e-113">The `ExitProcess` event is the only exit/unload event that is guaranteed to get called on shutdown.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3e2e-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f3e2e-114">Requirements</span></span>  

 <span data-ttu-id="f3e2e-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3e2e-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3e2e-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f3e2e-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f3e2e-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f3e2e-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f3e2e-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3e2e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3e2e-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f3e2e-119">See also</span></span>

- [<span data-ttu-id="f3e2e-120">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f3e2e-120">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)

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
ms.openlocfilehash: 4380b8a3803e164aab7318821a9dbde32ecc3a0b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781750"
---
# <a name="icordebugmanagedcallbackexitprocess-method"></a><span data-ttu-id="8be37-102">ICorDebugManagedCallback::ExitProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8be37-102">ICorDebugManagedCallback::ExitProcess Method</span></span>
<span data-ttu-id="8be37-103">Hata ayıklayıcıya bir işlemin çıkış olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="8be37-103">Notifies the debugger that a process has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8be37-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8be37-104">Syntax</span></span>  
  
```cpp  
HRESULT ExitProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8be37-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8be37-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="8be37-106">'ndaki İşlemi temsil eden ICorDebugProcess nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8be37-106">[in] A pointer to an ICorDebugProcess object that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8be37-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8be37-107">Remarks</span></span>  
 <span data-ttu-id="8be37-108">`ExitProcess` olayından devam edemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="8be37-108">You cannot continue from an `ExitProcess` event.</span></span> <span data-ttu-id="8be37-109">Bu olay, işlem durdurulmuş olarak göründüğü sırada diğer olaylara zaman uyumsuz olarak harekete çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="8be37-109">This event may fire asynchronously to other events while the process appears to be stopped.</span></span> <span data-ttu-id="8be37-110">Bu durum, genellikle bazı harici bir zorlamalı nedeniyle işlem durdurulduğunda sonlandırıldığında meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="8be37-110">This can occur if the process terminates while stopped, usually due to some external force.</span></span>  
  
 <span data-ttu-id="8be37-111">Ortak dil çalışma zamanı (CLR) zaten yönetilen bir geri çağırma gönderiyor ise bu olay, geri çağırma geri dönene kadar gecikecek.</span><span class="sxs-lookup"><span data-stu-id="8be37-111">If the common language runtime (CLR) is already dispatching a managed callback, this event will be delayed until after that callback has returned.</span></span>  
  
 <span data-ttu-id="8be37-112">`ExitProcess` olay, kapatılırken çağrılmanın garanti edilmesi gereken tek çıkış/kaldırma olayıdır.</span><span class="sxs-lookup"><span data-stu-id="8be37-112">The `ExitProcess` event is the only exit/unload event that is guaranteed to get called on shutdown.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8be37-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8be37-113">Requirements</span></span>  
 <span data-ttu-id="8be37-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8be37-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8be37-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8be37-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8be37-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="8be37-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8be37-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8be37-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8be37-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8be37-118">See also</span></span>

- [<span data-ttu-id="8be37-119">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8be37-119">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)

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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b4e7b62b7eb038d553b28fbd6422175d511df88d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54540552"
---
# <a name="icordebugmanagedcallbackexitprocess-method"></a><span data-ttu-id="61a14-102">ICorDebugManagedCallback::ExitProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="61a14-102">ICorDebugManagedCallback::ExitProcess Method</span></span>
<span data-ttu-id="61a14-103">Hata ayıklayıcı bir işlemden çıkıldı bildirir.</span><span class="sxs-lookup"><span data-stu-id="61a14-103">Notifies the debugger that a process has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61a14-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="61a14-104">Syntax</span></span>  
  
```  
HRESULT ExitProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="61a14-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="61a14-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="61a14-106">[in] Bir işlemi temsil eden bir Icordebugprocess nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="61a14-106">[in] A pointer to an ICorDebugProcess object that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="61a14-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="61a14-107">Remarks</span></span>  
 <span data-ttu-id="61a14-108">Devam edemiyor bir `ExitProcess` olay.</span><span class="sxs-lookup"><span data-stu-id="61a14-108">You cannot continue from an `ExitProcess` event.</span></span> <span data-ttu-id="61a14-109">İşlem durdurulacak görüntülenirken bu olay için diğer olayları zaman uyumsuz olarak harekete.</span><span class="sxs-lookup"><span data-stu-id="61a14-109">This event may fire asynchronously to other events while the process appears to be stopped.</span></span> <span data-ttu-id="61a14-110">Bu işlem genellikle nedeniyle bazı dış zorla durdurulduğu sırada sona ererse ortaya çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="61a14-110">This can occur if the process terminates while stopped, usually due to some external force.</span></span>  
  
 <span data-ttu-id="61a14-111">Ortak dil çalışma zamanı (CLR) zaten yönetilen bir geri gönderme, geri arama tarafından döndürülen sonra bu olay kadar geciktirilecek.</span><span class="sxs-lookup"><span data-stu-id="61a14-111">If the common language runtime (CLR) is already dispatching a managed callback, this event will be delayed until after that callback has returned.</span></span>  
  
 <span data-ttu-id="61a14-112">`ExitProcess` Kapanışında çağrılmadığı kesin yalnızca çıkış/yüklemeyi kaldırma olay etkinliğidir.</span><span class="sxs-lookup"><span data-stu-id="61a14-112">The `ExitProcess` event is the only exit/unload event that is guaranteed to get called on shutdown.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61a14-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="61a14-113">Requirements</span></span>  
 <span data-ttu-id="61a14-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61a14-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61a14-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="61a14-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="61a14-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="61a14-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="61a14-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61a14-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61a14-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="61a14-118">See also</span></span>
- [<span data-ttu-id="61a14-119">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="61a14-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

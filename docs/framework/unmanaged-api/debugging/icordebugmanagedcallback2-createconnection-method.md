---
title: ICorDebugManagedCallback2::CreateConnection Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.CreateConnection
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::CreateConnection
helpviewer_keywords:
- CreateConnection method [.NET Framework debugging]
- ICorDebugManagedCallback2::CreateConnection method [.NET Framework debugging]
ms.assetid: 49e647be-9d63-4250-9d11-704e2a400d1b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 10d0fc0c65d6c479ee4bf7bf527ee33615d53084
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761171"
---
# <a name="icordebugmanagedcallback2createconnection-method"></a><span data-ttu-id="d76b0-102">ICorDebugManagedCallback2::CreateConnection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d76b0-102">ICorDebugManagedCallback2::CreateConnection Method</span></span>
<span data-ttu-id="d76b0-103">Hata ayıklayıcı, yeni bir bağlantı oluşturulduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="d76b0-103">Notifies the debugger that a new connection has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d76b0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d76b0-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId,  
    [in] WCHAR                *pConnName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d76b0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d76b0-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="d76b0-106">[in] Bağlantı oluşturulduğu işlemini temsil eden bir "ICorDebugProcess" nesneye bir işaretçi</span><span class="sxs-lookup"><span data-stu-id="d76b0-106">[in] A pointer to an "ICorDebugProcess" object that represents the process in which the connection was created</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="d76b0-107">[in] Yeni bir bağlantı kimliği.</span><span class="sxs-lookup"><span data-stu-id="d76b0-107">[in] The ID of the new connection.</span></span>  
  
 `pConnName`  
 <span data-ttu-id="d76b0-108">[in] Yeni bir bağlantı adı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d76b0-108">[in] A pointer to the name of the new connection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d76b0-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d76b0-109">Remarks</span></span>  
 <span data-ttu-id="d76b0-110">A `CreateConnection` geri çağırma harekete aşağıdaki durumlarda birini:</span><span class="sxs-lookup"><span data-stu-id="d76b0-110">A `CreateConnection` callback will be fired in either of the following cases:</span></span>  
  
- <span data-ttu-id="d76b0-111">Ne zaman bir hata ayıklayıcı bağlantıları içeren bir işleme iliştirir.</span><span class="sxs-lookup"><span data-stu-id="d76b0-111">When a debugger attaches to a process that contains connections.</span></span> <span data-ttu-id="d76b0-112">Çalışma zamanı bu durumda, oluşturma ve gönderme bir `CreateConnection` olay ve [Icordebugmanagedcallback2::changeconnection](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-changeconnection-method.md) işlemdeki her bağlantı için olay.</span><span class="sxs-lookup"><span data-stu-id="d76b0-112">In this case, the runtime will generate and dispatch a `CreateConnection` event and a [ICorDebugManagedCallback2::ChangeConnection](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-changeconnection-method.md) event for each connection in the process.</span></span>  
  
- <span data-ttu-id="d76b0-113">Bir konak çağırdığında [Iclrdebugmanager::beginconnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) içinde [barındırma API](../../../../docs/framework/unmanaged-api/hosting/index.md).</span><span class="sxs-lookup"><span data-stu-id="d76b0-113">When a host calls [ICLRDebugManager::BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) in the [Hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d76b0-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d76b0-114">Requirements</span></span>  
 <span data-ttu-id="d76b0-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d76b0-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d76b0-116">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d76b0-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d76b0-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d76b0-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d76b0-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d76b0-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d76b0-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d76b0-119">See also</span></span>

- [<span data-ttu-id="d76b0-120">ICorDebugManagedCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d76b0-120">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="d76b0-121">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d76b0-121">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

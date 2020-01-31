---
title: ICorDebugManagedCallback2::ChangeConnection Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.ChangeConnection
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::ChangeConnection
helpviewer_keywords:
- ICorDebugManagedCallback2::ChangeConnection method [.NET Framework debugging]
- ChangeConnection method [.NET Framework debugging]
ms.assetid: 7263f9a9-4c0b-4d82-a181-288873fb2b18
topic_type:
- apiref
ms.openlocfilehash: d60644d54373dfb3d1d191900df71d3e5f6547a6
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788287"
---
# <a name="icordebugmanagedcallback2changeconnection-method"></a><span data-ttu-id="10911-102">ICorDebugManagedCallback2::ChangeConnection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="10911-102">ICorDebugManagedCallback2::ChangeConnection Method</span></span>
<span data-ttu-id="10911-103">Hata ayıklayıcısını, belirtilen bağlantıyla ilişkili görev kümesinin değiştiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="10911-103">Notifies the debugger that the set of tasks associated with the specified connection has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10911-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="10911-104">Syntax</span></span>  
  
```cpp  
HRESULT ChangeConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="10911-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="10911-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="10911-106">'ndaki Değiştirilen bağlantıyı içeren işlemi temsil eden bir "ICorDebugProcess" nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="10911-106">[in] A pointer to an "ICorDebugProcess" object that represents the process containing the connection that changed.</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="10911-107">'ndaki Değiştirilen bağlantının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="10911-107">[in] The ID of the connection that changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="10911-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="10911-108">Remarks</span></span>  
 <span data-ttu-id="10911-109">`ChangeConnection` geri çağırma aşağıdaki durumlardan biri içinde tetiklenir:</span><span class="sxs-lookup"><span data-stu-id="10911-109">A `ChangeConnection` callback will be fired in either of the following cases:</span></span>  
  
- <span data-ttu-id="10911-110">Bir hata ayıklayıcı bağlantıları içeren bir işleme iliştirayarlandığında.</span><span class="sxs-lookup"><span data-stu-id="10911-110">When a debugger attaches to a process that contains connections.</span></span> <span data-ttu-id="10911-111">Bu durumda, çalışma zamanı işlemdeki her bağlantı için bir [ICorDebugManagedCallback2:: CreateConnection](icordebugmanagedcallback2-createconnection-method.md) olayı ve bir `ChangeConnection` olayı oluşturur ve gönderir.</span><span class="sxs-lookup"><span data-stu-id="10911-111">In this case, the runtime will generate and dispatch a [ICorDebugManagedCallback2::CreateConnection](icordebugmanagedcallback2-createconnection-method.md) event and a `ChangeConnection` event for each connection in the process.</span></span> <span data-ttu-id="10911-112">Bağlantının görev kümesinin oluşturulduktan sonra değiştirilip değiştirilmediğini bağımsız olarak, var olan her bağlantı için `ChangeConnection` bir olay oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="10911-112">A `ChangeConnection` event is generated for every existing connection, regardless of whether that connection’s set of tasks has been changed since its creation.</span></span>  
  
- <span data-ttu-id="10911-113">Bir ana bilgisayar [barındırma API 'Sindeki](../../../../docs/framework/unmanaged-api/hosting/index.md) [ICLRDebugManager:: SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md) öğesini çağırdığında.</span><span class="sxs-lookup"><span data-stu-id="10911-113">When a host calls [ICLRDebugManager::SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md) in the [Hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md).</span></span>  
  
 <span data-ttu-id="10911-114">Hata ayıklayıcı, yeni değişiklikleri almak için işlemdeki tüm iş parçacıklarını taramalıdır.</span><span class="sxs-lookup"><span data-stu-id="10911-114">The debugger should scan all threads in the process to pick up the new changes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10911-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="10911-115">Requirements</span></span>  
 <span data-ttu-id="10911-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10911-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10911-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="10911-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="10911-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="10911-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="10911-119">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10911-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10911-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="10911-120">See also</span></span>

- [<span data-ttu-id="10911-121">ICorDebugManagedCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="10911-121">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="10911-122">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="10911-122">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)

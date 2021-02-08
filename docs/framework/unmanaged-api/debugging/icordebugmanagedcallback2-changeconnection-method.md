---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugManagedCallback2:: ChangeConnection yöntemi'
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
ms.openlocfilehash: 854ea7f40cad9bce613b4034afe7688f4aaf4e52
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790925"
---
# <a name="icordebugmanagedcallback2changeconnection-method"></a><span data-ttu-id="40012-103">ICorDebugManagedCallback2::ChangeConnection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="40012-103">ICorDebugManagedCallback2::ChangeConnection Method</span></span>

<span data-ttu-id="40012-104">Hata ayıklayıcısını, belirtilen bağlantıyla ilişkili görev kümesinin değiştiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="40012-104">Notifies the debugger that the set of tasks associated with the specified connection has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40012-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="40012-105">Syntax</span></span>  
  
```cpp  
HRESULT ChangeConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="40012-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="40012-106">Parameters</span></span>  

 `pProcess`  
 <span data-ttu-id="40012-107">'ndaki Değiştirilen bağlantıyı içeren işlemi temsil eden bir "ICorDebugProcess" nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="40012-107">[in] A pointer to an "ICorDebugProcess" object that represents the process containing the connection that changed.</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="40012-108">'ndaki Değiştirilen bağlantının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="40012-108">[in] The ID of the connection that changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="40012-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="40012-109">Remarks</span></span>  

 <span data-ttu-id="40012-110">`ChangeConnection`Aşağıdaki durumlardan birinde bir geri çağırma harekete geçirilir:</span><span class="sxs-lookup"><span data-stu-id="40012-110">A `ChangeConnection` callback will be fired in either of the following cases:</span></span>  
  
- <span data-ttu-id="40012-111">Bir hata ayıklayıcı bağlantıları içeren bir işleme iliştirayarlandığında.</span><span class="sxs-lookup"><span data-stu-id="40012-111">When a debugger attaches to a process that contains connections.</span></span> <span data-ttu-id="40012-112">Bu durumda, çalışma zamanı bir [ICorDebugManagedCallback2:: CreateConnection](icordebugmanagedcallback2-createconnection-method.md) olayı ve `ChangeConnection` işlemdeki her bağlantı için bir olay oluşturur ve gönderir.</span><span class="sxs-lookup"><span data-stu-id="40012-112">In this case, the runtime will generate and dispatch a [ICorDebugManagedCallback2::CreateConnection](icordebugmanagedcallback2-createconnection-method.md) event and a `ChangeConnection` event for each connection in the process.</span></span> <span data-ttu-id="40012-113">`ChangeConnection`Bağlantının görev kümesinin oluşturulduktan sonra değiştirilip değiştirilmediğini bağımsız olarak, var olan her bağlantı için bir olay oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="40012-113">A `ChangeConnection` event is generated for every existing connection, regardless of whether that connection’s set of tasks has been changed since its creation.</span></span>  
  
- <span data-ttu-id="40012-114">Bir ana bilgisayar [barındırma API 'Sindeki](../hosting/index.md) [ICLRDebugManager:: SetConnectionTasks](../hosting/iclrdebugmanager-setconnectiontasks-method.md) öğesini çağırdığında.</span><span class="sxs-lookup"><span data-stu-id="40012-114">When a host calls [ICLRDebugManager::SetConnectionTasks](../hosting/iclrdebugmanager-setconnectiontasks-method.md) in the [Hosting API](../hosting/index.md).</span></span>  
  
 <span data-ttu-id="40012-115">Hata ayıklayıcı, yeni değişiklikleri almak için işlemdeki tüm iş parçacıklarını taramalıdır.</span><span class="sxs-lookup"><span data-stu-id="40012-115">The debugger should scan all threads in the process to pick up the new changes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40012-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="40012-116">Requirements</span></span>  

 <span data-ttu-id="40012-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40012-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40012-118">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="40012-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="40012-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="40012-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="40012-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40012-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40012-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="40012-121">See also</span></span>

- [<span data-ttu-id="40012-122">ICorDebugManagedCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="40012-122">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="40012-123">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="40012-123">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)

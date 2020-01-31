---
title: ICorDebugManagedCallback2::DestroyConnection Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.DestroyConnection
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::DestroyConnection
helpviewer_keywords:
- DestroyConnection method [.NET Framework debugging]
- ICorDebugManagedCallback2::DestroyConnection method [.NET Framework debugging]
ms.assetid: cf7940e9-4558-4319-925c-09f6c98c8fcd
topic_type:
- apiref
ms.openlocfilehash: 4f6940f863504a9aedd9539e121c7b3791f746b9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788303"
---
# <a name="icordebugmanagedcallback2destroyconnection-method"></a><span data-ttu-id="a5871-102">ICorDebugManagedCallback2::DestroyConnection Metodu</span><span class="sxs-lookup"><span data-stu-id="a5871-102">ICorDebugManagedCallback2::DestroyConnection Method</span></span>
<span data-ttu-id="a5871-103">Hata ayıklayıcıyı belirtilen bağlantının sonlandırıldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="a5871-103">Notifies the debugger that the specified connection has been terminated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5871-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a5871-104">Syntax</span></span>  
  
```cpp  
HRESULT DestroyConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a5871-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a5871-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="a5871-106">'ndaki Yok edilen bağlantıyı içeren işlemi temsil eden ICorDebugProcess nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a5871-106">[in] A pointer to an ICorDebugProcess object that represents the process containing the connection that was destroyed.</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="a5871-107">'ndaki Yok edilen bağlantının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="a5871-107">[in] The ID of the connection that was destroyed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5871-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a5871-108">Remarks</span></span>  
 <span data-ttu-id="a5871-109">[BARıNDıRMA API](../../../../docs/framework/unmanaged-api/hosting/index.md)'sinde bir ana bilgisayar [ICLRDebugManager:: EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md) çağırdığında, bir `DestroyConnection` geri çağırması tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="a5871-109">A `DestroyConnection` callback will be fired when a host calls [ICLRDebugManager::EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md) in the [Hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5871-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a5871-110">Requirements</span></span>  
 <span data-ttu-id="a5871-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5871-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5871-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a5871-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a5871-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a5871-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a5871-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5871-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5871-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a5871-115">See also</span></span>

- [<span data-ttu-id="a5871-116">ICorDebugManagedCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a5871-116">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="a5871-117">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a5871-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)

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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bf6d4acb7d1156babbd698201c5aea2810644db8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415408"
---
# <a name="icordebugmanagedcallback2destroyconnection-method"></a><span data-ttu-id="87e24-102">ICorDebugManagedCallback2::DestroyConnection Metodu</span><span class="sxs-lookup"><span data-stu-id="87e24-102">ICorDebugManagedCallback2::DestroyConnection Method</span></span>
<span data-ttu-id="87e24-103">Hata ayıklayıcı belirtilen bağlantı sonlandırıldı bildirir.</span><span class="sxs-lookup"><span data-stu-id="87e24-103">Notifies the debugger that the specified connection has been terminated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87e24-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="87e24-104">Syntax</span></span>  
  
```  
HRESULT DestroyConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="87e24-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="87e24-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="87e24-106">[in] Bir işaretçi Icordebugprocess nesneye zarar görmüş bağlantıyı içeren işlemi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="87e24-106">[in] A pointer to an ICorDebugProcess object that represents the process containing the connection that was destroyed.</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="87e24-107">[in] Zarar görmüş bağlantının kimliği.</span><span class="sxs-lookup"><span data-stu-id="87e24-107">[in] The ID of the connection that was destroyed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87e24-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="87e24-108">Remarks</span></span>  
 <span data-ttu-id="87e24-109">A `DestroyConnection` geri çağırma harekete bir ana bilgisayar çağırdığında [Iclrdebugmanager::endconnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md) içinde [barındırma API](../../../../docs/framework/unmanaged-api/hosting/index.md).</span><span class="sxs-lookup"><span data-stu-id="87e24-109">A `DestroyConnection` callback will be fired when a host calls [ICLRDebugManager::EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md) in the [Hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87e24-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="87e24-110">Requirements</span></span>  
 <span data-ttu-id="87e24-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87e24-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87e24-112">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="87e24-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="87e24-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="87e24-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="87e24-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87e24-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87e24-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="87e24-115">See Also</span></span>  
 [<span data-ttu-id="87e24-116">ICorDebugManagedCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="87e24-116">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [<span data-ttu-id="87e24-117">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="87e24-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

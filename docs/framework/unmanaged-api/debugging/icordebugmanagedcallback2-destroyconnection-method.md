---
description: 'Hakkında daha fazla bilgi edinin: ICorDebugManagedCallback2::D estroyConnection yöntemi'
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
ms.openlocfilehash: f17def5599dc02ed6b7b49d7f8ed4db02eb40181
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790899"
---
# <a name="icordebugmanagedcallback2destroyconnection-method"></a><span data-ttu-id="4ee48-103">ICorDebugManagedCallback2::DestroyConnection Metodu</span><span class="sxs-lookup"><span data-stu-id="4ee48-103">ICorDebugManagedCallback2::DestroyConnection Method</span></span>

<span data-ttu-id="4ee48-104">Hata ayıklayıcıyı belirtilen bağlantının sonlandırıldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="4ee48-104">Notifies the debugger that the specified connection has been terminated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ee48-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4ee48-105">Syntax</span></span>  
  
```cpp  
HRESULT DestroyConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4ee48-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4ee48-106">Parameters</span></span>  

 `pProcess`  
 <span data-ttu-id="4ee48-107">'ndaki Yok edilen bağlantıyı içeren işlemi temsil eden ICorDebugProcess nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4ee48-107">[in] A pointer to an ICorDebugProcess object that represents the process containing the connection that was destroyed.</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="4ee48-108">'ndaki Yok edilen bağlantının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="4ee48-108">[in] The ID of the connection that was destroyed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4ee48-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4ee48-109">Remarks</span></span>  

 <span data-ttu-id="4ee48-110">`DestroyConnection` [Barındırma API](../hosting/index.md)'sinde bir ana bilgisayar [ICLRDebugManager:: EndConnection](../hosting/iclrdebugmanager-endconnection-method.md) çağırdığında bir geri çağırma tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="4ee48-110">A `DestroyConnection` callback will be fired when a host calls [ICLRDebugManager::EndConnection](../hosting/iclrdebugmanager-endconnection-method.md) in the [Hosting API](../hosting/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ee48-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4ee48-111">Requirements</span></span>  

 <span data-ttu-id="4ee48-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ee48-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ee48-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4ee48-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4ee48-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="4ee48-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4ee48-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ee48-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ee48-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4ee48-116">See also</span></span>

- [<span data-ttu-id="4ee48-117">ICorDebugManagedCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4ee48-117">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="4ee48-118">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4ee48-118">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)

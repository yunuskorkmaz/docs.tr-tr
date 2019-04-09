---
title: ICorDebugManagedCallback::CreateProcess Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.CreateProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::CreateProcess
helpviewer_keywords:
- ICorDebugManagedCallback::CreateProcess method [.NET Framework debugging]
- CreateProcess method, ICorDebugManagedCallback interface [.NET Framework debugging]
ms.assetid: 8e89d5ee-e4e3-4738-8302-0b7d1cf4846e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eda214200ca4c3837ad89ed14887ef6b09af7d30
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59160374"
---
# <a name="icordebugmanagedcallbackcreateprocess-method"></a><span data-ttu-id="8fa13-102">ICorDebugManagedCallback::CreateProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8fa13-102">ICorDebugManagedCallback::CreateProcess Method</span></span>
<span data-ttu-id="8fa13-103">Bir işleme eklenmiş veya için ilk kez başlatıldığında, hata ayıklayıcı size bildirir.</span><span class="sxs-lookup"><span data-stu-id="8fa13-103">Notifies the debugger when a process has been attached or started for the first time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fa13-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8fa13-104">Syntax</span></span>  
  
```  
HRESULT CreateProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8fa13-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8fa13-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="8fa13-106">[in] Eklenen veya çalışmaya işlemi temsil eden bir Icordebugprocess nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="8fa13-106">[in] A pointer to an ICorDebugProcess object that represents the process that has been attached or started.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8fa13-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8fa13-107">Remarks</span></span>  
 <span data-ttu-id="8fa13-108">Bu yöntem, ortak dil çalışma başlatılana kadar çağrılmaz.</span><span class="sxs-lookup"><span data-stu-id="8fa13-108">This method is not called until the common language runtime is initialized.</span></span> <span data-ttu-id="8fa13-109">Çoğu [Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) yöntemleri önce CORDBG_E_NOTREADY döndürür `CreateProcess` geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="8fa13-109">Most of the [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) methods will return CORDBG_E_NOTREADY before the `CreateProcess` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8fa13-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8fa13-110">Requirements</span></span>  
 <span data-ttu-id="8fa13-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8fa13-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8fa13-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8fa13-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8fa13-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8fa13-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="8fa13-114">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="8fa13-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8fa13-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8fa13-115">See also</span></span>

- [<span data-ttu-id="8fa13-116">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8fa13-116">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

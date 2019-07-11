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
ms.openlocfilehash: 0eacb4b0a06fbe086935b59eba7d33135b6bef19
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759714"
---
# <a name="icordebugmanagedcallbackcreateprocess-method"></a><span data-ttu-id="e27cc-102">ICorDebugManagedCallback::CreateProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e27cc-102">ICorDebugManagedCallback::CreateProcess Method</span></span>
<span data-ttu-id="e27cc-103">Bir işleme eklenmiş veya için ilk kez başlatıldığında, hata ayıklayıcı size bildirir.</span><span class="sxs-lookup"><span data-stu-id="e27cc-103">Notifies the debugger when a process has been attached or started for the first time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e27cc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e27cc-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e27cc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e27cc-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="e27cc-106">[in] Eklenen veya çalışmaya işlemi temsil eden bir Icordebugprocess nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="e27cc-106">[in] A pointer to an ICorDebugProcess object that represents the process that has been attached or started.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e27cc-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e27cc-107">Remarks</span></span>  
 <span data-ttu-id="e27cc-108">Bu yöntem, ortak dil çalışma başlatılana kadar çağrılmaz.</span><span class="sxs-lookup"><span data-stu-id="e27cc-108">This method is not called until the common language runtime is initialized.</span></span> <span data-ttu-id="e27cc-109">Çoğu [Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) yöntemleri önce CORDBG_E_NOTREADY döndürür `CreateProcess` geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="e27cc-109">Most of the [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) methods will return CORDBG_E_NOTREADY before the `CreateProcess` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e27cc-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e27cc-110">Requirements</span></span>  
 <span data-ttu-id="e27cc-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e27cc-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e27cc-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e27cc-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e27cc-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e27cc-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e27cc-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e27cc-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e27cc-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e27cc-115">See also</span></span>

- [<span data-ttu-id="e27cc-116">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e27cc-116">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

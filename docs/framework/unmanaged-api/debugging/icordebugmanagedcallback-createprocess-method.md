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
ms.openlocfilehash: 24efa08e9c4b2e242af95112b7f055e9173aaa7c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414683"
---
# <a name="icordebugmanagedcallbackcreateprocess-method"></a><span data-ttu-id="bcb6d-102">ICorDebugManagedCallback::CreateProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bcb6d-102">ICorDebugManagedCallback::CreateProcess Method</span></span>
<span data-ttu-id="bcb6d-103">Bir işlem bağlı veya için ilk kez başlatıldığında, hata ayıklayıcı size bildirir.</span><span class="sxs-lookup"><span data-stu-id="bcb6d-103">Notifies the debugger when a process has been attached or started for the first time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcb6d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bcb6d-104">Syntax</span></span>  
  
```  
HRESULT CreateProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bcb6d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bcb6d-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="bcb6d-106">[in] Bir işaretçi Icordebugprocess nesneye bağlı veya başlatılan işlem temsil eder.</span><span class="sxs-lookup"><span data-stu-id="bcb6d-106">[in] A pointer to an ICorDebugProcess object that represents the process that has been attached or started.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bcb6d-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bcb6d-107">Remarks</span></span>  
 <span data-ttu-id="bcb6d-108">Bu yöntem, ortak dil çalışma zamanı başlatılana kadar çağrılmaz.</span><span class="sxs-lookup"><span data-stu-id="bcb6d-108">This method is not called until the common language runtime is initialized.</span></span> <span data-ttu-id="bcb6d-109">Çoğu [Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) yöntemleri CORDBG_E_NOTREADY önce döndürecektir `CreateProcess` geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="bcb6d-109">Most of the [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) methods will return CORDBG_E_NOTREADY before the `CreateProcess` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bcb6d-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bcb6d-110">Requirements</span></span>  
 <span data-ttu-id="bcb6d-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bcb6d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bcb6d-112">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bcb6d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bcb6d-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bcb6d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bcb6d-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bcb6d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcb6d-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bcb6d-115">See Also</span></span>  
 [<span data-ttu-id="bcb6d-116">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bcb6d-116">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

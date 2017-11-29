---
title: "ICorDebugManagedCallback::CreateProcess Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.CreateProcess
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::CreateProcess
helpviewer_keywords:
- ICorDebugManagedCallback::CreateProcess method [.NET Framework debugging]
- CreateProcess method, ICorDebugManagedCallback interface [.NET Framework debugging]
ms.assetid: 8e89d5ee-e4e3-4738-8302-0b7d1cf4846e
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bef3140717ff977fbfae813d0de89011b89ed062
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmanagedcallbackcreateprocess-method"></a><span data-ttu-id="2c325-102">ICorDebugManagedCallback::CreateProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2c325-102">ICorDebugManagedCallback::CreateProcess Method</span></span>
<span data-ttu-id="2c325-103">Bir işlem bağlı veya için ilk kez başlatıldığında, hata ayıklayıcı size bildirir.</span><span class="sxs-lookup"><span data-stu-id="2c325-103">Notifies the debugger when a process has been attached or started for the first time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c325-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2c325-104">Syntax</span></span>  
  
```  
HRESULT CreateProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2c325-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2c325-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="2c325-106">[in] Bir işaretçi Icordebugprocess nesneye bağlı veya başlatılan işlem temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2c325-106">[in] A pointer to an ICorDebugProcess object that represents the process that has been attached or started.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2c325-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2c325-107">Remarks</span></span>  
 <span data-ttu-id="2c325-108">Bu yöntem, ortak dil çalışma zamanı başlatılana kadar çağrılmaz.</span><span class="sxs-lookup"><span data-stu-id="2c325-108">This method is not called until the common language runtime is initialized.</span></span> <span data-ttu-id="2c325-109">Çoğu [Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) yöntemleri CORDBG_E_NOTREADY önce döndürecektir `CreateProcess` geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="2c325-109">Most of the [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) methods will return CORDBG_E_NOTREADY before the `CreateProcess` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c325-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2c325-110">Requirements</span></span>  
 <span data-ttu-id="2c325-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c325-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c325-112">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2c325-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2c325-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2c325-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c325-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c325-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c325-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2c325-115">See Also</span></span>  
 [<span data-ttu-id="2c325-116">Icordebugmanagedcallback arabirimi</span><span class="sxs-lookup"><span data-stu-id="2c325-116">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

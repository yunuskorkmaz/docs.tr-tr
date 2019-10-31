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
ms.openlocfilehash: d773368c85fd42fd169109cf1c7e6635705ebb7e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73090222"
---
# <a name="icordebugmanagedcallbackcreateprocess-method"></a><span data-ttu-id="ff1f8-102">ICorDebugManagedCallback::CreateProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ff1f8-102">ICorDebugManagedCallback::CreateProcess Method</span></span>
<span data-ttu-id="ff1f8-103">Bir işlem ilk kez eklendiğinde veya başlatıldığında hata ayıklayıcıya bildirir.</span><span class="sxs-lookup"><span data-stu-id="ff1f8-103">Notifies the debugger when a process has been attached or started for the first time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff1f8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ff1f8-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ff1f8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ff1f8-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="ff1f8-106">'ndaki Eklenmiş veya başlatılan işlemi temsil eden ICorDebugProcess nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ff1f8-106">[in] A pointer to an ICorDebugProcess object that represents the process that has been attached or started.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff1f8-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ff1f8-107">Remarks</span></span>  
 <span data-ttu-id="ff1f8-108">Bu yöntem, ortak dil çalışma zamanı başlatılana kadar çağrılmaz.</span><span class="sxs-lookup"><span data-stu-id="ff1f8-108">This method is not called until the common language runtime is initialized.</span></span> <span data-ttu-id="ff1f8-109">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) yöntemlerinin çoğu, `CreateProcess` geri aramadan önce CORDBG_E_NOTREADY döndürür.</span><span class="sxs-lookup"><span data-stu-id="ff1f8-109">Most of the [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) methods will return CORDBG_E_NOTREADY before the `CreateProcess` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff1f8-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ff1f8-110">Requirements</span></span>  
 <span data-ttu-id="ff1f8-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff1f8-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff1f8-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ff1f8-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ff1f8-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ff1f8-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ff1f8-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff1f8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff1f8-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ff1f8-115">See also</span></span>

- [<span data-ttu-id="ff1f8-116">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ff1f8-116">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

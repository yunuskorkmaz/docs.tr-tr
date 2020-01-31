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
ms.openlocfilehash: 0c3059697014cea33081f6cb81b9d93c7d028c2e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777475"
---
# <a name="icordebugmanagedcallbackcreateprocess-method"></a><span data-ttu-id="906fa-102">ICorDebugManagedCallback::CreateProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="906fa-102">ICorDebugManagedCallback::CreateProcess Method</span></span>
<span data-ttu-id="906fa-103">Bir işlem ilk kez eklendiğinde veya başlatıldığında hata ayıklayıcıya bildirir.</span><span class="sxs-lookup"><span data-stu-id="906fa-103">Notifies the debugger when a process has been attached or started for the first time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="906fa-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="906fa-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="906fa-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="906fa-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="906fa-106">'ndaki Eklenmiş veya başlatılan işlemi temsil eden ICorDebugProcess nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="906fa-106">[in] A pointer to an ICorDebugProcess object that represents the process that has been attached or started.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="906fa-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="906fa-107">Remarks</span></span>  
 <span data-ttu-id="906fa-108">Bu yöntem, ortak dil çalışma zamanı başlatılana kadar çağrılmaz.</span><span class="sxs-lookup"><span data-stu-id="906fa-108">This method is not called until the common language runtime is initialized.</span></span> <span data-ttu-id="906fa-109">[ICorDebug](icordebug-interface.md) yöntemlerinin çoğu `CreateProcess` geri aramadan önce CORDBG_E_NOTREADY döndürür.</span><span class="sxs-lookup"><span data-stu-id="906fa-109">Most of the [ICorDebug](icordebug-interface.md) methods will return CORDBG_E_NOTREADY before the `CreateProcess` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="906fa-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="906fa-110">Requirements</span></span>  
 <span data-ttu-id="906fa-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="906fa-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="906fa-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="906fa-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="906fa-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="906fa-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="906fa-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="906fa-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="906fa-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="906fa-115">See also</span></span>

- [<span data-ttu-id="906fa-116">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="906fa-116">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)

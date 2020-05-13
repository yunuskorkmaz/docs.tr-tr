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
ms.openlocfilehash: 0e9ed8054711297173e880c9eecb12c3f5bd0a68
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207133"
---
# <a name="icordebugmanagedcallbackcreateprocess-method"></a><span data-ttu-id="05269-102">ICorDebugManagedCallback::CreateProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="05269-102">ICorDebugManagedCallback::CreateProcess Method</span></span>
<span data-ttu-id="05269-103">Bir işlem ilk kez eklendiğinde veya başlatıldığında hata ayıklayıcıya bildirir.</span><span class="sxs-lookup"><span data-stu-id="05269-103">Notifies the debugger when a process has been attached or started for the first time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05269-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="05269-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05269-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="05269-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="05269-106">'ndaki Eklenmiş veya başlatılan işlemi temsil eden ICorDebugProcess nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="05269-106">[in] A pointer to an ICorDebugProcess object that represents the process that has been attached or started.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="05269-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="05269-107">Remarks</span></span>  
 <span data-ttu-id="05269-108">Bu yöntem, ortak dil çalışma zamanı başlatılana kadar çağrılmaz.</span><span class="sxs-lookup"><span data-stu-id="05269-108">This method is not called until the common language runtime is initialized.</span></span> <span data-ttu-id="05269-109">[ICorDebug](icordebug-interface.md) yöntemlerinin çoğu geri aramadan önce CORDBG_E_NOTREADY döndürür `CreateProcess` .</span><span class="sxs-lookup"><span data-stu-id="05269-109">Most of the [ICorDebug](icordebug-interface.md) methods will return CORDBG_E_NOTREADY before the `CreateProcess` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05269-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="05269-110">Requirements</span></span>  
 <span data-ttu-id="05269-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05269-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05269-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="05269-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="05269-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="05269-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="05269-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05269-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05269-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05269-115">See also</span></span>

- [<span data-ttu-id="05269-116">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="05269-116">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)

---
description: ': ICorDebugManagedCallback:: CreateProcess yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 564c9862dd90431f0626204fdfe49e59b85a124d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791055"
---
# <a name="icordebugmanagedcallbackcreateprocess-method"></a><span data-ttu-id="d9997-103">ICorDebugManagedCallback::CreateProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d9997-103">ICorDebugManagedCallback::CreateProcess Method</span></span>

<span data-ttu-id="d9997-104">Bir işlem ilk kez eklendiğinde veya başlatıldığında hata ayıklayıcıya bildirir.</span><span class="sxs-lookup"><span data-stu-id="d9997-104">Notifies the debugger when a process has been attached or started for the first time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9997-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d9997-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9997-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d9997-106">Parameters</span></span>  

 `pProcess`  
 <span data-ttu-id="d9997-107">'ndaki Eklenmiş veya başlatılan işlemi temsil eden ICorDebugProcess nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d9997-107">[in] A pointer to an ICorDebugProcess object that represents the process that has been attached or started.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d9997-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d9997-108">Remarks</span></span>  

 <span data-ttu-id="d9997-109">Bu yöntem, ortak dil çalışma zamanı başlatılana kadar çağrılmaz.</span><span class="sxs-lookup"><span data-stu-id="d9997-109">This method is not called until the common language runtime is initialized.</span></span> <span data-ttu-id="d9997-110">[ICorDebug](icordebug-interface.md) yöntemlerinin çoğu geri aramadan önce CORDBG_E_NOTREADY döndürür `CreateProcess` .</span><span class="sxs-lookup"><span data-stu-id="d9997-110">Most of the [ICorDebug](icordebug-interface.md) methods will return CORDBG_E_NOTREADY before the `CreateProcess` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9997-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d9997-111">Requirements</span></span>  

 <span data-ttu-id="d9997-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9997-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9997-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d9997-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d9997-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d9997-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d9997-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9997-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9997-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9997-116">See also</span></span>

- [<span data-ttu-id="d9997-117">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d9997-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)

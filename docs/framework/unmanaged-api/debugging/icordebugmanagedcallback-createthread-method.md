---
title: ICorDebugManagedCallback::CreateThread Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.CreateThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::CreateThread method
helpviewer_keywords:
- ICorDebugManagedCallback::CreateThread method [.NET Framework debugging]
- CreateThread method [.NET Framework debugging]
ms.assetid: 6b961728-21c4-4e8d-ae81-197458be62f4
topic_type:
- apiref
ms.openlocfilehash: 5fa3bafd35912a7729833896f7e6f0bb2ff9b121
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212392"
---
# <a name="icordebugmanagedcallbackcreatethread-method"></a><span data-ttu-id="49df9-102">ICorDebugManagedCallback::CreateThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="49df9-102">ICorDebugManagedCallback::CreateThread Method</span></span>
<span data-ttu-id="49df9-103">Hata ayıklayıcıya bir iş parçacığının yönetilen kodu yürütmeye başlatıldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="49df9-103">Notifies the debugger that a thread has started executing managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49df9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="49df9-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="49df9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="49df9-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="49df9-106">'ndaki İş parçacığını içeren uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="49df9-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the thread.</span></span>  
  
 `thread`  
 <span data-ttu-id="49df9-107">'ndaki İş parçacığını temsil eden ICorDebugThread nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="49df9-107">[in] A pointer to an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="49df9-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="49df9-108">Remarks</span></span>  
 <span data-ttu-id="49df9-109">İş parçacığı yürütülecek ilk yönetilen kod yönergesinde konumlandırılacaktır.</span><span class="sxs-lookup"><span data-stu-id="49df9-109">The thread will be positioned at the first managed code instruction to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49df9-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="49df9-110">Requirements</span></span>  
 <span data-ttu-id="49df9-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49df9-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49df9-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="49df9-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="49df9-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="49df9-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="49df9-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49df9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49df9-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="49df9-115">See also</span></span>

- [<span data-ttu-id="49df9-116">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="49df9-116">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)

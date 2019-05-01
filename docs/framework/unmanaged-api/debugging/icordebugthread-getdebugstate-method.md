---
title: ICorDebugThread::GetDebugState Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetDebugState
helpviewer_keywords:
- GetDebugState method [.NET Framework debugging]
- ICorDebugThread::GetDebugState method [.NET Framework debugging]
ms.assetid: 9be27b0c-1d99-4722-b0d4-40cf6753ce5c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 68df19120f2e0b45e73f9d5e137afc8a5e7ac513
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61987161"
---
# <a name="icordebugthreadgetdebugstate-method"></a><span data-ttu-id="bd097-102">ICorDebugThread::GetDebugState Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bd097-102">ICorDebugThread::GetDebugState Method</span></span>
<span data-ttu-id="bd097-103">Bu Icordebugthread nesne geçerli hata ayıklama durumunu alır.</span><span class="sxs-lookup"><span data-stu-id="bd097-103">Gets the current debug state of this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd097-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bd097-104">Syntax</span></span>  
  
```  
HRESULT GetDebugState (  
    [out] CorDebugThreadState   *pState  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bd097-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bd097-105">Parameters</span></span>  
 `pState`  
 <span data-ttu-id="bd097-106">[out] Bu iş parçacığının geçerli hata ayıklama durumunu açıklayan karşılaştırmaya CorDebugThreadState sabit listesi değerleri için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bd097-106">[out] A pointer to a bitwise combination of CorDebugThreadState enumeration values that describes the current debug state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bd097-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bd097-107">Remarks</span></span>  
 <span data-ttu-id="bd097-108">İşlem şu anda durursa, `pState` işlemi devam için bu iş parçacığının gerçek geçerli durumu varsa, bu iş parçacığı için var olan hata ayıklama durumunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="bd097-108">If the process is currently stopped, `pState` represents the debug state that would exist for this thread if the process were to be continued, not the actual current state of this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd097-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bd097-109">Requirements</span></span>  
 <span data-ttu-id="bd097-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd097-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd097-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bd097-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bd097-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bd097-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bd097-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd097-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

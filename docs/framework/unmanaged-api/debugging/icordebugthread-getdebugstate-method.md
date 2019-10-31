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
ms.openlocfilehash: f054f8f2bd7c322e722a1e17290ba6fbad9e37b0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133516"
---
# <a name="icordebugthreadgetdebugstate-method"></a><span data-ttu-id="0190d-102">ICorDebugThread::GetDebugState Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0190d-102">ICorDebugThread::GetDebugState Method</span></span>
<span data-ttu-id="0190d-103">Bu ICorDebugThread nesnesinin geçerli hata ayıklama durumunu alır.</span><span class="sxs-lookup"><span data-stu-id="0190d-103">Gets the current debug state of this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0190d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0190d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDebugState (  
    [out] CorDebugThreadState   *pState  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0190d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0190d-105">Parameters</span></span>  
 `pState`  
 <span data-ttu-id="0190d-106">dışı Bu iş parçacığının geçerli hata ayıklama durumunu açıklayan, CorDebugThreadState numaralandırma değerlerinin bit düzeyinde birleşimine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0190d-106">[out] A pointer to a bitwise combination of CorDebugThreadState enumeration values that describes the current debug state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0190d-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0190d-107">Remarks</span></span>  
 <span data-ttu-id="0190d-108">İşlem şu anda durdurulmuşsa, bu iş parçacığının gerçek geçerli durumu değil, işlem devam etseydi, bu iş parçacığı için mevcut olacak hata ayıklama durumunu temsil `pState`.</span><span class="sxs-lookup"><span data-stu-id="0190d-108">If the process is currently stopped, `pState` represents the debug state that would exist for this thread if the process were to be continued, not the actual current state of this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0190d-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0190d-109">Requirements</span></span>  
 <span data-ttu-id="0190d-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0190d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0190d-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0190d-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0190d-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0190d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0190d-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0190d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

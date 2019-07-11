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
ms.openlocfilehash: 0baabbb736365b138d1754e68070207b4310bf57
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762451"
---
# <a name="icordebugthreadgetdebugstate-method"></a><span data-ttu-id="b9422-102">ICorDebugThread::GetDebugState Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b9422-102">ICorDebugThread::GetDebugState Method</span></span>
<span data-ttu-id="b9422-103">Bu Icordebugthread nesne geçerli hata ayıklama durumunu alır.</span><span class="sxs-lookup"><span data-stu-id="b9422-103">Gets the current debug state of this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9422-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b9422-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDebugState (  
    [out] CorDebugThreadState   *pState  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9422-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b9422-105">Parameters</span></span>  
 `pState`  
 <span data-ttu-id="b9422-106">[out] Bu iş parçacığının geçerli hata ayıklama durumunu açıklayan karşılaştırmaya CorDebugThreadState sabit listesi değerleri için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b9422-106">[out] A pointer to a bitwise combination of CorDebugThreadState enumeration values that describes the current debug state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b9422-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b9422-107">Remarks</span></span>  
 <span data-ttu-id="b9422-108">İşlem şu anda durursa, `pState` işlemi devam için bu iş parçacığının gerçek geçerli durumu varsa, bu iş parçacığı için var olan hata ayıklama durumunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b9422-108">If the process is currently stopped, `pState` represents the debug state that would exist for this thread if the process were to be continued, not the actual current state of this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9422-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b9422-109">Requirements</span></span>  
 <span data-ttu-id="b9422-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9422-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9422-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b9422-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b9422-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b9422-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b9422-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9422-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

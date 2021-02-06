---
description: ': ICorDebugThread:: GetDebugState metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 86534dded9b8e931fe2a7e44f1c95dc2ec7b6f0d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659159"
---
# <a name="icordebugthreadgetdebugstate-method"></a><span data-ttu-id="91cdf-103">ICorDebugThread::GetDebugState Yöntemi</span><span class="sxs-lookup"><span data-stu-id="91cdf-103">ICorDebugThread::GetDebugState Method</span></span>

<span data-ttu-id="91cdf-104">Bu ICorDebugThread nesnesinin geçerli hata ayıklama durumunu alır.</span><span class="sxs-lookup"><span data-stu-id="91cdf-104">Gets the current debug state of this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91cdf-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="91cdf-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDebugState (  
    [out] CorDebugThreadState   *pState  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91cdf-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="91cdf-106">Parameters</span></span>  

 `pState`  
 <span data-ttu-id="91cdf-107">dışı Bu iş parçacığının geçerli hata ayıklama durumunu açıklayan, CorDebugThreadState numaralandırma değerlerinin bit düzeyinde birleşimine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="91cdf-107">[out] A pointer to a bitwise combination of CorDebugThreadState enumeration values that describes the current debug state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="91cdf-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="91cdf-108">Remarks</span></span>  

 <span data-ttu-id="91cdf-109">İşlem şu anda durdurulmuşsa, `pState` işlem devam etseydi, bu iş parçacığının gerçek geçerli durumu değil, bu iş parçacığı için mevcut olacak hata ayıklama durumunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="91cdf-109">If the process is currently stopped, `pState` represents the debug state that would exist for this thread if the process were to be continued, not the actual current state of this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91cdf-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="91cdf-110">Requirements</span></span>  

 <span data-ttu-id="91cdf-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91cdf-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91cdf-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="91cdf-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="91cdf-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="91cdf-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="91cdf-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91cdf-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

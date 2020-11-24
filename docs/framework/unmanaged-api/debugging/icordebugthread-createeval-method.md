---
title: ICorDebugThread::CreateEval Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugThread.CreateEval
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::CreateEval
helpviewer_keywords:
- CreateEval method [.NET Framework debugging]
- ICorDebugThread::CreateEval method [.NET Framework debugging]
ms.assetid: 36605067-33d3-4579-9c72-fb0e551ab0f1
topic_type:
- apiref
ms.openlocfilehash: 1c0037530ae4f40be5bef4da8f398afe5f2bbb91
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688295"
---
# <a name="icordebugthreadcreateeval-method"></a><span data-ttu-id="58ba5-102">ICorDebugThread::CreateEval Yöntemi</span><span class="sxs-lookup"><span data-stu-id="58ba5-102">ICorDebugThread::CreateEval Method</span></span>

<span data-ttu-id="58ba5-103">Bu ICorDebugThread 'in işlevlerini toplayan ve sunan bir ıcordebugger Geval nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="58ba5-103">Creates an ICorDebugEval object that collects and exposes the functionality of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58ba5-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="58ba5-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateEval (  
    [out] ICorDebugEval   **ppEval  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="58ba5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="58ba5-105">Parameters</span></span>  

 `ppEval`  
 <span data-ttu-id="58ba5-106">dışı `ICorDebugEval` Bu iş parçacığının işlevlerini toplayan ve ortaya çıkaran nesnenin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="58ba5-106">[out] A pointer to the address of an `ICorDebugEval` object that collects and exposes the functionality of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="58ba5-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="58ba5-107">Remarks</span></span>  

 <span data-ttu-id="58ba5-108">Değerlendirme nesnesi, hesaplamayı yapmadan önce iş parçacığı üzerinde yeni bir zincir gönderir.</span><span class="sxs-lookup"><span data-stu-id="58ba5-108">The evaluation object will push a new chain on the thread before doing its computation.</span></span> <span data-ttu-id="58ba5-109">Bu, değerlendirme tamamlanana kadar iş parçacığında gerçekleştirilmekte olan hesaplamayı keser.</span><span class="sxs-lookup"><span data-stu-id="58ba5-109">This interrupts the computation currently being performed on the thread until the evaluation completes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58ba5-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="58ba5-110">Requirements</span></span>  

 <span data-ttu-id="58ba5-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58ba5-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58ba5-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="58ba5-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="58ba5-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="58ba5-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="58ba5-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58ba5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

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
ms.openlocfilehash: f66ef88646c314502dcb610cec8ce822cab1fca2
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379277"
---
# <a name="icordebugthreadcreateeval-method"></a><span data-ttu-id="f5b1b-102">ICorDebugThread::CreateEval Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f5b1b-102">ICorDebugThread::CreateEval Method</span></span>
<span data-ttu-id="f5b1b-103">Bu ICorDebugThread 'in işlevlerini toplayan ve sunan bir ıcordebugger Geval nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f5b1b-103">Creates an ICorDebugEval object that collects and exposes the functionality of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5b1b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f5b1b-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateEval (  
    [out] ICorDebugEval   **ppEval  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5b1b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f5b1b-105">Parameters</span></span>  
 `ppEval`  
 <span data-ttu-id="f5b1b-106">dışı `ICorDebugEval`Bu iş parçacığının işlevlerini toplayan ve ortaya çıkaran nesnenin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f5b1b-106">[out] A pointer to the address of an `ICorDebugEval` object that collects and exposes the functionality of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5b1b-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f5b1b-107">Remarks</span></span>  
 <span data-ttu-id="f5b1b-108">Değerlendirme nesnesi, hesaplamayı yapmadan önce iş parçacığı üzerinde yeni bir zincir gönderir.</span><span class="sxs-lookup"><span data-stu-id="f5b1b-108">The evaluation object will push a new chain on the thread before doing its computation.</span></span> <span data-ttu-id="f5b1b-109">Bu, değerlendirme tamamlanana kadar iş parçacığında gerçekleştirilmekte olan hesaplamayı keser.</span><span class="sxs-lookup"><span data-stu-id="f5b1b-109">This interrupts the computation currently being performed on the thread until the evaluation completes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5b1b-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f5b1b-110">Requirements</span></span>  
 <span data-ttu-id="f5b1b-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5b1b-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5b1b-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f5b1b-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f5b1b-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f5b1b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f5b1b-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5b1b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

---
description: ': ICorDebugThread:: CreateEval yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: a789840e099a14b584e5713bee12f5c4b0717fe7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659393"
---
# <a name="icordebugthreadcreateeval-method"></a><span data-ttu-id="c4213-103">ICorDebugThread::CreateEval Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c4213-103">ICorDebugThread::CreateEval Method</span></span>

<span data-ttu-id="c4213-104">Bu ICorDebugThread 'in işlevlerini toplayan ve sunan bir ıcordebugger Geval nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c4213-104">Creates an ICorDebugEval object that collects and exposes the functionality of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4213-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c4213-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateEval (  
    [out] ICorDebugEval   **ppEval  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4213-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c4213-106">Parameters</span></span>  

 `ppEval`  
 <span data-ttu-id="c4213-107">dışı `ICorDebugEval` Bu iş parçacığının işlevlerini toplayan ve ortaya çıkaran nesnenin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c4213-107">[out] A pointer to the address of an `ICorDebugEval` object that collects and exposes the functionality of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4213-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c4213-108">Remarks</span></span>  

 <span data-ttu-id="c4213-109">Değerlendirme nesnesi, hesaplamayı yapmadan önce iş parçacığı üzerinde yeni bir zincir gönderir.</span><span class="sxs-lookup"><span data-stu-id="c4213-109">The evaluation object will push a new chain on the thread before doing its computation.</span></span> <span data-ttu-id="c4213-110">Bu, değerlendirme tamamlanana kadar iş parçacığında gerçekleştirilmekte olan hesaplamayı keser.</span><span class="sxs-lookup"><span data-stu-id="c4213-110">This interrupts the computation currently being performed on the thread until the evaluation completes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4213-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c4213-111">Requirements</span></span>  

 <span data-ttu-id="c4213-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4213-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4213-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c4213-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c4213-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c4213-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4213-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4213-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

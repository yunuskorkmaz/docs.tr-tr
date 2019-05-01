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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2016795e7b2c0588e2bd69e764fb96f7f90b24d0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994077"
---
# <a name="icordebugthreadcreateeval-method"></a><span data-ttu-id="3c78b-102">ICorDebugThread::CreateEval Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3c78b-102">ICorDebugThread::CreateEval Method</span></span>
<span data-ttu-id="3c78b-103">Toplar ve bu Icordebugthread işlevselliğini kullanıma sunan bir Icordebugeval nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3c78b-103">Creates an ICorDebugEval object that collects and exposes the functionality of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c78b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3c78b-104">Syntax</span></span>  
  
```  
HRESULT CreateEval (  
    [out] ICorDebugEval   **ppEval  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3c78b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3c78b-105">Parameters</span></span>  
 `ppEval`  
 <span data-ttu-id="3c78b-106">[out] Adresine bir işaretçi bir `ICorDebugEval` nesnesini toplar ve bu iş parçacığı işlevini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3c78b-106">[out] A pointer to the address of an `ICorDebugEval` object that collects and exposes the functionality of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c78b-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3c78b-107">Remarks</span></span>  
 <span data-ttu-id="3c78b-108">Değerlendirme nesne yeni zinciri kendi hesaplama gerçekleştirmeden önce iş parçacığı üzerinde bildirim yapar.</span><span class="sxs-lookup"><span data-stu-id="3c78b-108">The evaluation object will push a new chain on the thread before doing its computation.</span></span> <span data-ttu-id="3c78b-109">Bu değerlendirme tamamlanana kadar iş parçacığı üzerinde şu anda gerçekleştirilmekte olan hesaplamayı kesintiye uğratır.</span><span class="sxs-lookup"><span data-stu-id="3c78b-109">This interrupts the computation currently being performed on the thread until the evaluation completes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c78b-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3c78b-110">Requirements</span></span>  
 <span data-ttu-id="3c78b-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c78b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c78b-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3c78b-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3c78b-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3c78b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3c78b-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c78b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

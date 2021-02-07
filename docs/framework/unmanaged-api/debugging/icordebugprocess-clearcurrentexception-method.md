---
description: ': ICorDebugProcess:: ClearCurrentException yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugProcess::ClearCurrentException Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.ClearCurrentException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::ClearCurrentException
helpviewer_keywords:
- ClearCurrentException method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::ClearCurrentException method [.NET Framework debugging]
ms.assetid: 9e02ee1a-e495-4578-bfb5-b946274bede7
topic_type:
- apiref
ms.openlocfilehash: 6f356078d8d303acb39cbaa500b7592185ad55ef
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754049"
---
# <a name="icordebugprocessclearcurrentexception-method"></a><span data-ttu-id="0ce0d-103">ICorDebugProcess::ClearCurrentException Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0ce0d-103">ICorDebugProcess::ClearCurrentException Method</span></span>

<span data-ttu-id="0ce0d-104">Belirtilen iş parçacığında geçerli yönetilmeyen özel durumu temizler.</span><span class="sxs-lookup"><span data-stu-id="0ce0d-104">Clears the current unmanaged exception on the given thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ce0d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0ce0d-105">Syntax</span></span>  
  
```cpp  
HRESULT ClearCurrentException([in] DWORD threadID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0ce0d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0ce0d-106">Parameters</span></span>  

 `threadID`  
 <span data-ttu-id="0ce0d-107">'ndaki Geçerli yönetilmeyen özel durumun temizleneceği iş parçacığının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="0ce0d-107">[in] The ID of the thread on which the current unmanaged exception will be cleared.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0ce0d-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0ce0d-108">Remarks</span></span>  

 <span data-ttu-id="0ce0d-109">Bir iş parçacığı hata ayıklanan tarafından yoksayılması gereken yönetilmeyen bir özel durum raporlandığı için [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) öğesini çağırmadan önce bu yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="0ce0d-109">Call this method before calling [ICorDebugController::Continue](icordebugcontroller-continue-method.md) when a thread has reported an unmanaged exception that should be ignored by the debuggee.</span></span> <span data-ttu-id="0ce0d-110">Bu işlem, verilen iş parçacığında hem bekleyen bant içi (ıB) hem de bant dışı (OOB) olaylarını temizler.</span><span class="sxs-lookup"><span data-stu-id="0ce0d-110">This will clear both the outstanding in-band (IB) and out-of-band (OOB) events on the given thread.</span></span> <span data-ttu-id="0ce0d-111">Tüm OOB kesme noktaları ve tek adımlı özel durumlar otomatik olarak temizlenir.</span><span class="sxs-lookup"><span data-stu-id="0ce0d-111">All OOB breakpoints and single-step exceptions are automatically cleared.</span></span>  
  
 <span data-ttu-id="0ce0d-112">Bir iş parçacığında geçerli yönetilen özel durumu ele almak için [ICorDebugThread2:: Yakatcurrentexception](icordebugthread2-interceptcurrentexception-method.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="0ce0d-112">Use [ICorDebugThread2::InterceptCurrentException](icordebugthread2-interceptcurrentexception-method.md) to intercept the current managed exception on a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ce0d-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0ce0d-113">Requirements</span></span>  

 <span data-ttu-id="0ce0d-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ce0d-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ce0d-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0ce0d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0ce0d-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0ce0d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0ce0d-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ce0d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

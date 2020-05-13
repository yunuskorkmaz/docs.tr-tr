---
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
ms.openlocfilehash: b8d20de990ff4a27a82590342494a307c986457e
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207391"
---
# <a name="icordebugprocessclearcurrentexception-method"></a><span data-ttu-id="9851b-102">ICorDebugProcess::ClearCurrentException Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9851b-102">ICorDebugProcess::ClearCurrentException Method</span></span>
<span data-ttu-id="9851b-103">Belirtilen iş parçacığında geçerli yönetilmeyen özel durumu temizler.</span><span class="sxs-lookup"><span data-stu-id="9851b-103">Clears the current unmanaged exception on the given thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9851b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9851b-104">Syntax</span></span>  
  
```cpp  
HRESULT ClearCurrentException([in] DWORD threadID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9851b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9851b-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="9851b-106">'ndaki Geçerli yönetilmeyen özel durumun temizleneceği iş parçacığının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="9851b-106">[in] The ID of the thread on which the current unmanaged exception will be cleared.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9851b-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9851b-107">Remarks</span></span>  
 <span data-ttu-id="9851b-108">Bir iş parçacığı hata ayıklanan tarafından yoksayılması gereken yönetilmeyen bir özel durum raporlandığı için [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) öğesini çağırmadan önce bu yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="9851b-108">Call this method before calling [ICorDebugController::Continue](icordebugcontroller-continue-method.md) when a thread has reported an unmanaged exception that should be ignored by the debuggee.</span></span> <span data-ttu-id="9851b-109">Bu işlem, verilen iş parçacığında hem bekleyen bant içi (ıB) hem de bant dışı (OOB) olaylarını temizler.</span><span class="sxs-lookup"><span data-stu-id="9851b-109">This will clear both the outstanding in-band (IB) and out-of-band (OOB) events on the given thread.</span></span> <span data-ttu-id="9851b-110">Tüm OOB kesme noktaları ve tek adımlı özel durumlar otomatik olarak temizlenir.</span><span class="sxs-lookup"><span data-stu-id="9851b-110">All OOB breakpoints and single-step exceptions are automatically cleared.</span></span>  
  
 <span data-ttu-id="9851b-111">Bir iş parçacığında geçerli yönetilen özel durumu ele almak için [ICorDebugThread2:: Yakatcurrentexception](icordebugthread2-interceptcurrentexception-method.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="9851b-111">Use [ICorDebugThread2::InterceptCurrentException](icordebugthread2-interceptcurrentexception-method.md) to intercept the current managed exception on a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9851b-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9851b-112">Requirements</span></span>  
 <span data-ttu-id="9851b-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9851b-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9851b-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9851b-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9851b-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9851b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9851b-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9851b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

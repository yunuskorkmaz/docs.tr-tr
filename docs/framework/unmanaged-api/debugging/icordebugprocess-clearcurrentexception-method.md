---
title: "ICorDebugProcess::ClearCurrentException Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.ClearCurrentException
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::ClearCurrentException
helpviewer_keywords:
- ClearCurrentException method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::ClearCurrentException method [.NET Framework debugging]
ms.assetid: 9e02ee1a-e495-4578-bfb5-b946274bede7
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 905ade7e5c44861b4ad6e7eb57fe7d3e3e9e3002
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocessclearcurrentexception-method"></a><span data-ttu-id="06003-102">ICorDebugProcess::ClearCurrentException Yöntemi</span><span class="sxs-lookup"><span data-stu-id="06003-102">ICorDebugProcess::ClearCurrentException Method</span></span>
<span data-ttu-id="06003-103">Geçerli yönetilmeyen özel durumu verilen iş parçacığı üzerinde temizler.</span><span class="sxs-lookup"><span data-stu-id="06003-103">Clears the current unmanaged exception on the given thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06003-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="06003-104">Syntax</span></span>  
  
```  
HRESULT ClearCurrentException([in] DWORD threadID);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="06003-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="06003-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="06003-106">[in] Geçerli yönetilmeyen özel durumu silinecek iş parçacığı kimliği.</span><span class="sxs-lookup"><span data-stu-id="06003-106">[in] The ID of the thread on which the current unmanaged exception will be cleared.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06003-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="06003-107">Remarks</span></span>  
 <span data-ttu-id="06003-108">Bu yöntemi çağırmadan önce çağırın [Icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) ne zaman bir iş parçacığı bildirdi tarafından ayıklayıcı yoksayılmalıdır yönetilmeyen bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="06003-108">Call this method before calling [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) when a thread has reported an unmanaged exception that should be ignored by the debuggee.</span></span> <span data-ttu-id="06003-109">Bu işlem bekleyen bant içi (IB) ve bant dışı (OOB) olayları verilen iş parçacığı üzerinde temizleyin.</span><span class="sxs-lookup"><span data-stu-id="06003-109">This will clear both the outstanding in-band (IB) and out-of-band (OOB) events on the given thread.</span></span> <span data-ttu-id="06003-110">Tüm OOB kesme noktaları ve tek adımlı özel durumları otomatik olarak temizlenir.</span><span class="sxs-lookup"><span data-stu-id="06003-110">All OOB breakpoints and single-step exceptions are automatically cleared.</span></span>  
  
 <span data-ttu-id="06003-111">Kullanım [Icordebugthread2::ınterceptcurrentexception](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md) geçerli müdahale yönetilen bir iş parçacığında özel durum.</span><span class="sxs-lookup"><span data-stu-id="06003-111">Use [ICorDebugThread2::InterceptCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md) to intercept the current managed exception on a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06003-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="06003-112">Requirements</span></span>  
 <span data-ttu-id="06003-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06003-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06003-114">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="06003-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="06003-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="06003-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="06003-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06003-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

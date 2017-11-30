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
ms.openlocfilehash: 8c6204f8906a29f7e8541d548872b6e84fd883bb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocessclearcurrentexception-method"></a><span data-ttu-id="e4453-102">ICorDebugProcess::ClearCurrentException Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e4453-102">ICorDebugProcess::ClearCurrentException Method</span></span>
<span data-ttu-id="e4453-103">Geçerli yönetilmeyen özel durumu verilen iş parçacığı üzerinde temizler.</span><span class="sxs-lookup"><span data-stu-id="e4453-103">Clears the current unmanaged exception on the given thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4453-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e4453-104">Syntax</span></span>  
  
```  
HRESULT ClearCurrentException([in] DWORD threadID);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e4453-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e4453-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="e4453-106">[in] Geçerli yönetilmeyen özel durumu silinecek iş parçacığı kimliği.</span><span class="sxs-lookup"><span data-stu-id="e4453-106">[in] The ID of the thread on which the current unmanaged exception will be cleared.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e4453-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e4453-107">Remarks</span></span>  
 <span data-ttu-id="e4453-108">Bu yöntemi çağırmadan önce çağırın [Icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) ne zaman bir iş parçacığı bildirdi tarafından ayıklayıcı yoksayılmalıdır yönetilmeyen bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="e4453-108">Call this method before calling [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) when a thread has reported an unmanaged exception that should be ignored by the debuggee.</span></span> <span data-ttu-id="e4453-109">Bu işlem bekleyen bant içi (IB) ve bant dışı (OOB) olayları verilen iş parçacığı üzerinde temizleyin.</span><span class="sxs-lookup"><span data-stu-id="e4453-109">This will clear both the outstanding in-band (IB) and out-of-band (OOB) events on the given thread.</span></span> <span data-ttu-id="e4453-110">Tüm OOB kesme noktaları ve tek adımlı özel durumları otomatik olarak temizlenir.</span><span class="sxs-lookup"><span data-stu-id="e4453-110">All OOB breakpoints and single-step exceptions are automatically cleared.</span></span>  
  
 <span data-ttu-id="e4453-111">Kullanım [Icordebugthread2::ınterceptcurrentexception](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md) geçerli müdahale yönetilen bir iş parçacığında özel durum.</span><span class="sxs-lookup"><span data-stu-id="e4453-111">Use [ICorDebugThread2::InterceptCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md) to intercept the current managed exception on a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4453-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e4453-112">Requirements</span></span>  
 <span data-ttu-id="e4453-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4453-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4453-114">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e4453-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e4453-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e4453-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e4453-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4453-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

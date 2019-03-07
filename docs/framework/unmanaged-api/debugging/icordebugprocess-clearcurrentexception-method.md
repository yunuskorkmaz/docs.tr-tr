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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f014f9213a4b9a2d5119af9a6dceebb9a9d54b52
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57473480"
---
# <a name="icordebugprocessclearcurrentexception-method"></a><span data-ttu-id="918a9-102">ICorDebugProcess::ClearCurrentException Yöntemi</span><span class="sxs-lookup"><span data-stu-id="918a9-102">ICorDebugProcess::ClearCurrentException Method</span></span>
<span data-ttu-id="918a9-103">Verilen iş parçacığı üzerinde geçerli yönetilmeyen özel durum temizler.</span><span class="sxs-lookup"><span data-stu-id="918a9-103">Clears the current unmanaged exception on the given thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="918a9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="918a9-104">Syntax</span></span>  
  
```  
HRESULT ClearCurrentException([in] DWORD threadID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="918a9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="918a9-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="918a9-106">[in] Geçerli yönetilmeyen özel durum temizlenir iş parçacığı kimliği.</span><span class="sxs-lookup"><span data-stu-id="918a9-106">[in] The ID of the thread on which the current unmanaged exception will be cleared.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="918a9-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="918a9-107">Remarks</span></span>  
 <span data-ttu-id="918a9-108">Bu yöntemi çağırmadan önce çağrı [Icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) ne zaman bir iş parçacığı bildirdi bir yönetilmeyen özel durum hata ayıklanan tarafından yoksayılacak.</span><span class="sxs-lookup"><span data-stu-id="918a9-108">Call this method before calling [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) when a thread has reported an unmanaged exception that should be ignored by the debuggee.</span></span> <span data-ttu-id="918a9-109">Bu, hem bekleyen bant (IB) hem de verilen iş parçacığı üzerinde bant dışı (OOB) olaylarını temizler.</span><span class="sxs-lookup"><span data-stu-id="918a9-109">This will clear both the outstanding in-band (IB) and out-of-band (OOB) events on the given thread.</span></span> <span data-ttu-id="918a9-110">Tüm OOB kesme noktaları ve tek adımlı özel durumları otomatik olarak temizlenir.</span><span class="sxs-lookup"><span data-stu-id="918a9-110">All OOB breakpoints and single-step exceptions are automatically cleared.</span></span>  
  
 <span data-ttu-id="918a9-111">Kullanım [Icordebugthread2::ınterceptcurrentexception](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md) geçerli ele alınması için bir iş parçacığında özel durum yönetilen.</span><span class="sxs-lookup"><span data-stu-id="918a9-111">Use [ICorDebugThread2::InterceptCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md) to intercept the current managed exception on a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="918a9-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="918a9-112">Requirements</span></span>  
 <span data-ttu-id="918a9-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="918a9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="918a9-114">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="918a9-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="918a9-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="918a9-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="918a9-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="918a9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

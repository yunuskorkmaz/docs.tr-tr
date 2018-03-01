---
title: ICorDebugHeapValue3::GetThreadOwningMonitorLock Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugHeapValue3.GetThreadOwningMonitorLock
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue3::GetThreadOwningMonitorLock
helpviewer_keywords:
- GetThreadOwningMonitorLock method [.NET Framework debugging]
- ICorDebugHeapValue3::GetThreadOwningMonitorLock method [.NET Framework debugging]
ms.assetid: e06fc19d-2cf4-4cad-81a3-137a68af8969
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1a2198e54c764fde0248563b040ac98984001888
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugheapvalue3getthreadowningmonitorlock-method"></a><span data-ttu-id="26b69-102">ICorDebugHeapValue3::GetThreadOwningMonitorLock Metodu</span><span class="sxs-lookup"><span data-stu-id="26b69-102">ICorDebugHeapValue3::GetThreadOwningMonitorLock Method</span></span>
<span data-ttu-id="26b69-103">Bu nesne üzerinde İzleyici kilit sahibi yönetilen iş parçacığı döndürür.</span><span class="sxs-lookup"><span data-stu-id="26b69-103">Returns the managed thread that owns the monitor lock on this object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26b69-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="26b69-104">Syntax</span></span>  
  
```  
HRESULT GetThreadOwningMonitorLock (  
    [out] ICorDebugThread   **ppThread,  
    [out] DWORD              *pAcquisitionCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="26b69-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="26b69-105">Parameters</span></span>  
 `ppThread`  
 <span data-ttu-id="26b69-106">[out] Bu nesne üzerinde İzleyici kilit sahibi yönetilen iş parçacığı.</span><span class="sxs-lookup"><span data-stu-id="26b69-106">[out] The managed thread that owns the monitor lock on this object.</span></span>  
  
 `pAcquisitionCount`  
 <span data-ttu-id="26b69-107">[out] Bu iş parçacığı sahipsiz için döndürmeden önce kilidi zorunda sayısı.</span><span class="sxs-lookup"><span data-stu-id="26b69-107">[out] The number of times this thread would have to release the lock before it returns to being unowned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="26b69-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="26b69-108">Return Value</span></span>  
 <span data-ttu-id="26b69-109">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="26b69-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="26b69-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="26b69-110">HRESULT</span></span>|<span data-ttu-id="26b69-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="26b69-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="26b69-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="26b69-112">S_OK</span></span>|<span data-ttu-id="26b69-113">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="26b69-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="26b69-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="26b69-114">S_FALSE</span></span>|<span data-ttu-id="26b69-115">Yönetilen hiçbir iş parçacığı bu nesnede İzleyici kilit sahibi.</span><span class="sxs-lookup"><span data-stu-id="26b69-115">No managed thread owns the monitor lock on this object.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="26b69-116">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="26b69-116">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26b69-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="26b69-117">Remarks</span></span>  
 <span data-ttu-id="26b69-118">Yönetilen iş parçacığı bu nesnede İzleyici kilit sahipse:</span><span class="sxs-lookup"><span data-stu-id="26b69-118">If a managed thread owns the monitor lock on this object:</span></span>  
  
-   <span data-ttu-id="26b69-119">Bu yöntem S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="26b69-119">The method returns S_OK.</span></span>  
  
-   <span data-ttu-id="26b69-120">İş parçacığı çıkar kadar iş parçacığı nesne geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="26b69-120">The thread object is valid until the thread exits.</span></span>  
  
 <span data-ttu-id="26b69-121">Yönetilen hiçbir iş parçacığı bu nesne üzerinde İzleyici kilit sahipse `ppThread` ve `pAcquisitionCount` aynıdır, ve S_FALSE yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="26b69-121">If no managed thread owns the monitor lock on this object, `ppThread` and `pAcquisitionCount` are unchanged, and the method returns S_FALSE.</span></span>  
  
 <span data-ttu-id="26b69-122">Varsa `ppThread` veya `pAcquisitionCount` geçerli bir işaretçi değil sonucu tanımlanmadı.</span><span class="sxs-lookup"><span data-stu-id="26b69-122">If `ppThread` or `pAcquisitionCount` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="26b69-123">Sağlayacak şekilde, iş parçacığı varsa, bu nesne üzerinde İzleyici kilit sahibi belirlenemiyor bir hata oluşursa hata olduğunu gösteren bir HRESULT yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="26b69-123">If an error occurs such that it cannot be determined which, if any, thread owns the monitor lock on this object, the method returns an HRESULT that indicates failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26b69-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="26b69-124">Requirements</span></span>  
 <span data-ttu-id="26b69-125">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26b69-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26b69-126">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="26b69-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="26b69-127">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="26b69-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="26b69-128">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26b69-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26b69-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="26b69-129">See Also</span></span>  
 [<span data-ttu-id="26b69-130">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="26b69-130">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="26b69-131">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="26b69-131">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

---
title: ICorDebugHeapValue3::GetThreadOwningMonitorLock Metodu
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ba09991e9452a86c6b7a1cbb08a38a71ba2aeaa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416770"
---
# <a name="icordebugheapvalue3getthreadowningmonitorlock-method"></a><span data-ttu-id="fe3ca-102">ICorDebugHeapValue3::GetThreadOwningMonitorLock Metodu</span><span class="sxs-lookup"><span data-stu-id="fe3ca-102">ICorDebugHeapValue3::GetThreadOwningMonitorLock Method</span></span>
<span data-ttu-id="fe3ca-103">Bu nesne üzerinde İzleyici kilit sahibi yönetilen iş parçacığı döndürür.</span><span class="sxs-lookup"><span data-stu-id="fe3ca-103">Returns the managed thread that owns the monitor lock on this object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe3ca-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fe3ca-104">Syntax</span></span>  
  
```  
HRESULT GetThreadOwningMonitorLock (  
    [out] ICorDebugThread   **ppThread,  
    [out] DWORD              *pAcquisitionCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fe3ca-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fe3ca-105">Parameters</span></span>  
 `ppThread`  
 <span data-ttu-id="fe3ca-106">[out] Bu nesne üzerinde İzleyici kilit sahibi yönetilen iş parçacığı.</span><span class="sxs-lookup"><span data-stu-id="fe3ca-106">[out] The managed thread that owns the monitor lock on this object.</span></span>  
  
 `pAcquisitionCount`  
 <span data-ttu-id="fe3ca-107">[out] Bu iş parçacığı sahipsiz için döndürmeden önce kilidi zorunda sayısı.</span><span class="sxs-lookup"><span data-stu-id="fe3ca-107">[out] The number of times this thread would have to release the lock before it returns to being unowned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fe3ca-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fe3ca-108">Return Value</span></span>  
 <span data-ttu-id="fe3ca-109">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="fe3ca-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="fe3ca-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fe3ca-110">HRESULT</span></span>|<span data-ttu-id="fe3ca-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fe3ca-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fe3ca-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="fe3ca-112">S_OK</span></span>|<span data-ttu-id="fe3ca-113">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="fe3ca-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="fe3ca-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="fe3ca-114">S_FALSE</span></span>|<span data-ttu-id="fe3ca-115">Yönetilen hiçbir iş parçacığı bu nesnede İzleyici kilit sahibi.</span><span class="sxs-lookup"><span data-stu-id="fe3ca-115">No managed thread owns the monitor lock on this object.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="fe3ca-116">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="fe3ca-116">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fe3ca-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fe3ca-117">Remarks</span></span>  
 <span data-ttu-id="fe3ca-118">Yönetilen iş parçacığı bu nesnede İzleyici kilit sahipse:</span><span class="sxs-lookup"><span data-stu-id="fe3ca-118">If a managed thread owns the monitor lock on this object:</span></span>  
  
-   <span data-ttu-id="fe3ca-119">Bu yöntem S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="fe3ca-119">The method returns S_OK.</span></span>  
  
-   <span data-ttu-id="fe3ca-120">İş parçacığı çıkar kadar iş parçacığı nesne geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="fe3ca-120">The thread object is valid until the thread exits.</span></span>  
  
 <span data-ttu-id="fe3ca-121">Yönetilen hiçbir iş parçacığı bu nesne üzerinde İzleyici kilit sahipse `ppThread` ve `pAcquisitionCount` aynıdır, ve S_FALSE yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="fe3ca-121">If no managed thread owns the monitor lock on this object, `ppThread` and `pAcquisitionCount` are unchanged, and the method returns S_FALSE.</span></span>  
  
 <span data-ttu-id="fe3ca-122">Varsa `ppThread` veya `pAcquisitionCount` geçerli bir işaretçi değil sonucu tanımlanmadı.</span><span class="sxs-lookup"><span data-stu-id="fe3ca-122">If `ppThread` or `pAcquisitionCount` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="fe3ca-123">Sağlayacak şekilde, iş parçacığı varsa, bu nesne üzerinde İzleyici kilit sahibi belirlenemiyor bir hata oluşursa hata olduğunu gösteren bir HRESULT yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="fe3ca-123">If an error occurs such that it cannot be determined which, if any, thread owns the monitor lock on this object, the method returns an HRESULT that indicates failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe3ca-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fe3ca-124">Requirements</span></span>  
 <span data-ttu-id="fe3ca-125">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe3ca-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe3ca-126">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fe3ca-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fe3ca-127">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fe3ca-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fe3ca-128">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe3ca-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe3ca-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fe3ca-129">See Also</span></span>  
 [<span data-ttu-id="fe3ca-130">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="fe3ca-130">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="fe3ca-131">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="fe3ca-131">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

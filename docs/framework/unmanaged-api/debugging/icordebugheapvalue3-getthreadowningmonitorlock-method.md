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
ms.openlocfilehash: ec265525d01dab0669939569501fce91b500a900
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127498"
---
# <a name="icordebugheapvalue3getthreadowningmonitorlock-method"></a><span data-ttu-id="6f7a1-102">ICorDebugHeapValue3::GetThreadOwningMonitorLock Metodu</span><span class="sxs-lookup"><span data-stu-id="6f7a1-102">ICorDebugHeapValue3::GetThreadOwningMonitorLock Method</span></span>
<span data-ttu-id="6f7a1-103">Bu nesne üzerinde izleyici kilidine sahip yönetilen iş parçacığını döndürür.</span><span class="sxs-lookup"><span data-stu-id="6f7a1-103">Returns the managed thread that owns the monitor lock on this object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f7a1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6f7a1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadOwningMonitorLock (  
    [out] ICorDebugThread   **ppThread,  
    [out] DWORD              *pAcquisitionCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6f7a1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6f7a1-105">Parameters</span></span>  
 `ppThread`  
 <span data-ttu-id="6f7a1-106">dışı Bu nesne üzerindeki izleyici kilidine sahip yönetilen iş parçacığı.</span><span class="sxs-lookup"><span data-stu-id="6f7a1-106">[out] The managed thread that owns the monitor lock on this object.</span></span>  
  
 `pAcquisitionCount`  
 <span data-ttu-id="6f7a1-107">dışı Bu iş parçacığının, sahip olunmadan önce kilidi serbest bırakmak zorunda olduğu zaman sayısı.</span><span class="sxs-lookup"><span data-stu-id="6f7a1-107">[out] The number of times this thread would have to release the lock before it returns to being unowned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6f7a1-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6f7a1-108">Return Value</span></span>  
 <span data-ttu-id="6f7a1-109">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="6f7a1-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="6f7a1-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6f7a1-110">HRESULT</span></span>|<span data-ttu-id="6f7a1-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6f7a1-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6f7a1-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="6f7a1-112">S_OK</span></span>|<span data-ttu-id="6f7a1-113">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="6f7a1-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="6f7a1-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="6f7a1-114">S_FALSE</span></span>|<span data-ttu-id="6f7a1-115">Bu nesnede izleyici kilidine sahip yönetilen iş parçacığı yok.</span><span class="sxs-lookup"><span data-stu-id="6f7a1-115">No managed thread owns the monitor lock on this object.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="6f7a1-116">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="6f7a1-116">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6f7a1-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6f7a1-117">Remarks</span></span>  
 <span data-ttu-id="6f7a1-118">Yönetilen bir iş parçacığının bu nesne üzerindeki izleyici kilidine sahip olması durumunda:</span><span class="sxs-lookup"><span data-stu-id="6f7a1-118">If a managed thread owns the monitor lock on this object:</span></span>  
  
- <span data-ttu-id="6f7a1-119">Yöntemi S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="6f7a1-119">The method returns S_OK.</span></span>  
  
- <span data-ttu-id="6f7a1-120">İş parçacığı nesnesi, iş parçacığı çıkış yapılıncaya kadar geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="6f7a1-120">The thread object is valid until the thread exits.</span></span>  
  
 <span data-ttu-id="6f7a1-121">Bu nesnede izleyici kilidine sahip yönetilen bir iş parçacığı yoksa, `ppThread` ve `pAcquisitionCount` değiştirilmez ve Yöntem S_FALSE döndürür.</span><span class="sxs-lookup"><span data-stu-id="6f7a1-121">If no managed thread owns the monitor lock on this object, `ppThread` and `pAcquisitionCount` are unchanged, and the method returns S_FALSE.</span></span>  
  
 <span data-ttu-id="6f7a1-122">`ppThread` veya `pAcquisitionCount` geçerli bir işaretçi değilse, sonuç tanımsızdır.</span><span class="sxs-lookup"><span data-stu-id="6f7a1-122">If `ppThread` or `pAcquisitionCount` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="6f7a1-123">Bir hata oluşursa, eğer varsa, iş parçacığı bu nesnede izleyici kilidine sahipse, yöntem hata belirten bir HRESULT döndürür.</span><span class="sxs-lookup"><span data-stu-id="6f7a1-123">If an error occurs such that it cannot be determined which, if any, thread owns the monitor lock on this object, the method returns an HRESULT that indicates failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f7a1-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6f7a1-124">Requirements</span></span>  
 <span data-ttu-id="6f7a1-125">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f7a1-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f7a1-126">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6f7a1-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6f7a1-127">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6f7a1-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6f7a1-128">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f7a1-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f7a1-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f7a1-129">See also</span></span>

- [<span data-ttu-id="6f7a1-130">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6f7a1-130">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="6f7a1-131">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="6f7a1-131">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

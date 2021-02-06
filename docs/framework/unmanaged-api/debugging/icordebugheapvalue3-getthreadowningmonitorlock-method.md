---
description: ': ICorDebugHeapValue3:: GetThreadOwningMonitorLock metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 9bd9e251c1e04bffd749c0569e4716d4c6fa89e5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660706"
---
# <a name="icordebugheapvalue3getthreadowningmonitorlock-method"></a><span data-ttu-id="1a2cd-103">ICorDebugHeapValue3::GetThreadOwningMonitorLock Metodu</span><span class="sxs-lookup"><span data-stu-id="1a2cd-103">ICorDebugHeapValue3::GetThreadOwningMonitorLock Method</span></span>

<span data-ttu-id="1a2cd-104">Bu nesne üzerinde izleyici kilidine sahip yönetilen iş parçacığını döndürür.</span><span class="sxs-lookup"><span data-stu-id="1a2cd-104">Returns the managed thread that owns the monitor lock on this object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a2cd-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1a2cd-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadOwningMonitorLock (  
    [out] ICorDebugThread   **ppThread,  
    [out] DWORD              *pAcquisitionCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1a2cd-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1a2cd-106">Parameters</span></span>  

 `ppThread`  
 <span data-ttu-id="1a2cd-107">dışı Bu nesne üzerindeki izleyici kilidine sahip yönetilen iş parçacığı.</span><span class="sxs-lookup"><span data-stu-id="1a2cd-107">[out] The managed thread that owns the monitor lock on this object.</span></span>  
  
 `pAcquisitionCount`  
 <span data-ttu-id="1a2cd-108">dışı Bu iş parçacığının, sahip olunmadan önce kilidi serbest bırakmak zorunda olduğu zaman sayısı.</span><span class="sxs-lookup"><span data-stu-id="1a2cd-108">[out] The number of times this thread would have to release the lock before it returns to being unowned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1a2cd-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1a2cd-109">Return Value</span></span>  

 <span data-ttu-id="1a2cd-110">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="1a2cd-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="1a2cd-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1a2cd-111">HRESULT</span></span>|<span data-ttu-id="1a2cd-112">Description</span><span class="sxs-lookup"><span data-stu-id="1a2cd-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1a2cd-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="1a2cd-113">S_OK</span></span>|<span data-ttu-id="1a2cd-114">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="1a2cd-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="1a2cd-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="1a2cd-115">S_FALSE</span></span>|<span data-ttu-id="1a2cd-116">Bu nesnede izleyici kilidine sahip yönetilen iş parçacığı yok.</span><span class="sxs-lookup"><span data-stu-id="1a2cd-116">No managed thread owns the monitor lock on this object.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="1a2cd-117">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="1a2cd-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1a2cd-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1a2cd-118">Remarks</span></span>  

 <span data-ttu-id="1a2cd-119">Yönetilen bir iş parçacığının bu nesne üzerindeki izleyici kilidine sahip olması durumunda:</span><span class="sxs-lookup"><span data-stu-id="1a2cd-119">If a managed thread owns the monitor lock on this object:</span></span>  
  
- <span data-ttu-id="1a2cd-120">Yöntemi S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="1a2cd-120">The method returns S_OK.</span></span>  
  
- <span data-ttu-id="1a2cd-121">İş parçacığı nesnesi, iş parçacığı çıkış yapılıncaya kadar geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="1a2cd-121">The thread object is valid until the thread exits.</span></span>  
  
 <span data-ttu-id="1a2cd-122">Bu nesnede izleyici kilidine sahip yönetilen bir iş parçacığı yoksa ve `ppThread` `pAcquisitionCount` değiştirilmez ve Yöntem S_FALSE döndürür.</span><span class="sxs-lookup"><span data-stu-id="1a2cd-122">If no managed thread owns the monitor lock on this object, `ppThread` and `pAcquisitionCount` are unchanged, and the method returns S_FALSE.</span></span>  
  
 <span data-ttu-id="1a2cd-123">`ppThread`Veya `pAcquisitionCount` geçerli bir işaretçi değilse, sonuç tanımsızdır.</span><span class="sxs-lookup"><span data-stu-id="1a2cd-123">If `ppThread` or `pAcquisitionCount` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="1a2cd-124">Bir hata oluşursa, eğer varsa, iş parçacığı bu nesnede izleyici kilidine sahipse, yöntem hata belirten bir HRESULT döndürür.</span><span class="sxs-lookup"><span data-stu-id="1a2cd-124">If an error occurs such that it cannot be determined which, if any, thread owns the monitor lock on this object, the method returns an HRESULT that indicates failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a2cd-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1a2cd-125">Requirements</span></span>  

 <span data-ttu-id="1a2cd-126">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a2cd-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a2cd-127">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1a2cd-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1a2cd-128">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1a2cd-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1a2cd-129">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a2cd-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a2cd-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1a2cd-130">See also</span></span>

- [<span data-ttu-id="1a2cd-131">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1a2cd-131">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="1a2cd-132">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="1a2cd-132">Debugging</span></span>](index.md)

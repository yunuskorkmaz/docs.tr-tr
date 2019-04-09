---
title: ICorDebugHeapValue3::GetMonitorEventWaitList Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue3.GetMonitorEventWaitList
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue3::GetMonitorEventWaitList
helpviewer_keywords:
- ICorDebugHeapValue3::GetMonitorEventWaitList method [.NET Framework debugging]
- GetMonitorEventWaitList method [.NET Framework debugging]
ms.assetid: 035a9035-ac66-4953-b48a-99652b42b7fe
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: db331d75244d59aacf2207a6b83a3f337a64b989
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59102797"
---
# <a name="icordebugheapvalue3getmonitoreventwaitlist-method"></a><span data-ttu-id="b13b6-102">ICorDebugHeapValue3::GetMonitorEventWaitList Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b13b6-102">ICorDebugHeapValue3::GetMonitorEventWaitList Method</span></span>
<span data-ttu-id="b13b6-103">Monitör kilit ile ilişkili olay sıraya alınan iş parçacıkları sıralı bir listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="b13b6-103">Provides an ordered list of threads that are queued on the event that is associated with a monitor lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b13b6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b13b6-104">Syntax</span></span>  
  
```  
HRESULT GetMonitorEventWaitList (  
    [out] ICorDebugThreadEnum **ppThreadEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b13b6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b13b6-105">Parameters</span></span>  
 `ppThreadEnum`  
 <span data-ttu-id="b13b6-106">[out] Icordebugthreadenum Numaralandırıcı iş parçacıkları sıralı listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="b13b6-106">[out] The ICorDebugThreadEnum enumerator that provides the ordered list of threads.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b13b6-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b13b6-107">Return Value</span></span>  
 <span data-ttu-id="b13b6-108">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="b13b6-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="b13b6-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b13b6-109">HRESULT</span></span>|<span data-ttu-id="b13b6-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b13b6-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b13b6-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="b13b6-111">S_OK</span></span>|<span data-ttu-id="b13b6-112">Liste boş değil.</span><span class="sxs-lookup"><span data-stu-id="b13b6-112">The list is not empty.</span></span>|  
|<span data-ttu-id="b13b6-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="b13b6-113">S_FALSE</span></span>|<span data-ttu-id="b13b6-114">Liste boş olduğu.</span><span class="sxs-lookup"><span data-stu-id="b13b6-114">The list is empty.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="b13b6-115">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="b13b6-115">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b13b6-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b13b6-116">Remarks</span></span>  
 <span data-ttu-id="b13b6-117">Listedeki ilk iş parçacığında sonraki çağrı tarafından yayınlanan ilk iş parçacığıdır <xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b13b6-117">The first thread in the list is the first thread that is released by the next call to <xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b13b6-118">Bir sonraki iş parçacığı listesinde aşağıdaki çağrı ve benzeri serbest bırakılır.</span><span class="sxs-lookup"><span data-stu-id="b13b6-118">The next thread in the list is released on the following call, and so on.</span></span>  
  
 <span data-ttu-id="b13b6-119">Liste boş değilse bu yöntem S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="b13b6-119">If the list is not empty, this method returns S_OK.</span></span> <span data-ttu-id="b13b6-120">Liste boş ise, yöntem S_FALSE döndürür; Bu durumda, sabit listesi boş olmasına rağmen hala geçerli.</span><span class="sxs-lookup"><span data-stu-id="b13b6-120">If the list is empty, the method returns S_FALSE; in this case, the enumeration is still valid, although it is empty.</span></span>  
  
 <span data-ttu-id="b13b6-121">Her iki durumda da, yalnızca geçerli eşitleme durumunun süresi boyunca sabit listesi arabirimi kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b13b6-121">In either case, the enumeration interface is usable only for the duration of the current synchronized state.</span></span> <span data-ttu-id="b13b6-122">Ancak, iş parçacığının arabirimleri buradan dispensed iş parçacığı çıkana kadar geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b13b6-122">However, the thread's interfaces dispensed from it are valid until the thread exits.</span></span>  
  
 <span data-ttu-id="b13b6-123">Varsa `ppThreadEnum` geçerli bir işaretçi değil sonuç tanımsızdır.</span><span class="sxs-lookup"><span data-stu-id="b13b6-123">If `ppThreadEnum` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="b13b6-124">Bu, varsa, iş parçacıkları için izleme, bekleyen belirlenemiyor, bir hata oluşursa yöntemi hata olduğunu gösteren bir HRESULT döndürür.</span><span class="sxs-lookup"><span data-stu-id="b13b6-124">If an error occurs such that it cannot be determined which, if any, threads are waiting for the monitor, the method returns an HRESULT that indicates failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b13b6-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b13b6-125">Requirements</span></span>  
 <span data-ttu-id="b13b6-126">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b13b6-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b13b6-127">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b13b6-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b13b6-128">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b13b6-128">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="b13b6-129">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="b13b6-129">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b13b6-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b13b6-130">See also</span></span>

- [<span data-ttu-id="b13b6-131">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b13b6-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="b13b6-132">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="b13b6-132">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

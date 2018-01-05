---
title: ICorDebugHeapValue3::GetMonitorEventWaitList Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHeapValue3.GetMonitorEventWaitList
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHeapValue3::GetMonitorEventWaitList
helpviewer_keywords:
- ICorDebugHeapValue3::GetMonitorEventWaitList method [.NET Framework debugging]
- GetMonitorEventWaitList method [.NET Framework debugging]
ms.assetid: 035a9035-ac66-4953-b48a-99652b42b7fe
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a4112188ff069184cab998f5bbd0fc70d1ce7dc9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugheapvalue3getmonitoreventwaitlist-method"></a><span data-ttu-id="6c6d3-102">ICorDebugHeapValue3::GetMonitorEventWaitList Metodu</span><span class="sxs-lookup"><span data-stu-id="6c6d3-102">ICorDebugHeapValue3::GetMonitorEventWaitList Method</span></span>
<span data-ttu-id="6c6d3-103">İzleyici kilit ile ilişkili olay sıraya alınan iş parçacıkları sıralı bir listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c6d3-103">Provides an ordered list of threads that are queued on the event that is associated with a monitor lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c6d3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6c6d3-104">Syntax</span></span>  
  
```  
HRESULT GetMonitorEventWaitList (  
    [out] ICorDebugThreadEnum **ppThreadEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6c6d3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6c6d3-105">Parameters</span></span>  
 `ppThreadEnum`  
 <span data-ttu-id="6c6d3-106">[out] İş parçacıkları sıralı listesini sağlar Icordebugthreadenum Numaralandırıcı.</span><span class="sxs-lookup"><span data-stu-id="6c6d3-106">[out] The ICorDebugThreadEnum enumerator that provides the ordered list of threads.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6c6d3-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6c6d3-107">Return Value</span></span>  
 <span data-ttu-id="6c6d3-108">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="6c6d3-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="6c6d3-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6c6d3-109">HRESULT</span></span>|<span data-ttu-id="6c6d3-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6c6d3-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6c6d3-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="6c6d3-111">S_OK</span></span>|<span data-ttu-id="6c6d3-112">Liste boş değil.</span><span class="sxs-lookup"><span data-stu-id="6c6d3-112">The list is not empty.</span></span>|  
|<span data-ttu-id="6c6d3-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="6c6d3-113">S_FALSE</span></span>|<span data-ttu-id="6c6d3-114">Liste boş olduğu.</span><span class="sxs-lookup"><span data-stu-id="6c6d3-114">The list is empty.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="6c6d3-115">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="6c6d3-115">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c6d3-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6c6d3-116">Remarks</span></span>  
 <span data-ttu-id="6c6d3-117">Listedeki ilk iş parçacığı için sonraki çağrı tarafından yayınlanan ilk parçacığıdır <xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6c6d3-117">The first thread in the list is the first thread that is released by the next call to <xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6c6d3-118">Sonraki iş parçacığı listesinde aşağıdaki çağrıyı ve benzeri yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="6c6d3-118">The next thread in the list is released on the following call, and so on.</span></span>  
  
 <span data-ttu-id="6c6d3-119">Liste boş değilse, bu yöntem S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="6c6d3-119">If the list is not empty, this method returns S_OK.</span></span> <span data-ttu-id="6c6d3-120">Liste boş ise, yöntem S_FALSE döndürür; Bu durumda, boş olmasına rağmen numaralandırma hala geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="6c6d3-120">If the list is empty, the method returns S_FALSE; in this case, the enumeration is still valid, although it is empty.</span></span>  
  
 <span data-ttu-id="6c6d3-121">Her iki durumda da, yalnızca geçerli eşitlenmiş durumuna süresince numaralandırması arabirimi kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6c6d3-121">In either case, the enumeration interface is usable only for the duration of the current synchronized state.</span></span> <span data-ttu-id="6c6d3-122">Ancak, iş parçacığı çıkar kadar ondan dispensed iş parçacığının arabirimleri geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="6c6d3-122">However, the thread's interfaces dispensed from it are valid until the thread exits.</span></span>  
  
 <span data-ttu-id="6c6d3-123">Varsa `ppThreadEnum` geçerli bir işaretçi değil sonucu tanımlanmadı.</span><span class="sxs-lookup"><span data-stu-id="6c6d3-123">If `ppThreadEnum` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="6c6d3-124">Sağlayacak şekilde, varsa, iş parçacıkları izleme için bekleyen belirlenemiyor bir hata oluşursa hata olduğunu gösteren bir HRESULT yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="6c6d3-124">If an error occurs such that it cannot be determined which, if any, threads are waiting for the monitor, the method returns an HRESULT that indicates failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c6d3-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6c6d3-125">Requirements</span></span>  
 <span data-ttu-id="6c6d3-126">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c6d3-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c6d3-127">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6c6d3-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6c6d3-128">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6c6d3-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c6d3-129">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c6d3-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c6d3-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6c6d3-130">See Also</span></span>  
 [<span data-ttu-id="6c6d3-131">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6c6d3-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="6c6d3-132">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="6c6d3-132">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

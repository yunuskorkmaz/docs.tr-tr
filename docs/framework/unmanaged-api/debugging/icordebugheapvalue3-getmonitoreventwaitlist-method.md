---
description: 'Daha fazla bilgi edinin: ICorDebugHeapValue3:: GetMonitorEventWaitList Yöntemi'
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
ms.openlocfilehash: ffc849e83151719062133382989344a8f0057caf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791458"
---
# <a name="icordebugheapvalue3getmonitoreventwaitlist-method"></a><span data-ttu-id="0d4b8-103">ICorDebugHeapValue3::GetMonitorEventWaitList Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0d4b8-103">ICorDebugHeapValue3::GetMonitorEventWaitList Method</span></span>

<span data-ttu-id="0d4b8-104">Bir izleyici kilidi ile ilişkili olayda sıraya alınan iş parçacıklarının sıralı bir listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="0d4b8-104">Provides an ordered list of threads that are queued on the event that is associated with a monitor lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d4b8-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0d4b8-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMonitorEventWaitList (  
    [out] ICorDebugThreadEnum **ppThreadEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0d4b8-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0d4b8-106">Parameters</span></span>  

 `ppThreadEnum`  
 <span data-ttu-id="0d4b8-107">dışı Sıralı iş parçacığı listesini sağlayan ICorDebugThreadEnum numaralandırıcısı.</span><span class="sxs-lookup"><span data-stu-id="0d4b8-107">[out] The ICorDebugThreadEnum enumerator that provides the ordered list of threads.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0d4b8-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0d4b8-108">Return Value</span></span>  

 <span data-ttu-id="0d4b8-109">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="0d4b8-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="0d4b8-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0d4b8-110">HRESULT</span></span>|<span data-ttu-id="0d4b8-111">Description</span><span class="sxs-lookup"><span data-stu-id="0d4b8-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0d4b8-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="0d4b8-112">S_OK</span></span>|<span data-ttu-id="0d4b8-113">Liste boş değil.</span><span class="sxs-lookup"><span data-stu-id="0d4b8-113">The list is not empty.</span></span>|  
|<span data-ttu-id="0d4b8-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="0d4b8-114">S_FALSE</span></span>|<span data-ttu-id="0d4b8-115">Liste boş.</span><span class="sxs-lookup"><span data-stu-id="0d4b8-115">The list is empty.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="0d4b8-116">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="0d4b8-116">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0d4b8-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0d4b8-117">Remarks</span></span>  

 <span data-ttu-id="0d4b8-118">Listedeki ilk iş parçacığı, sonraki çağrısıyla yayınlanan ilk iş parçacığıdır <xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="0d4b8-118">The first thread in the list is the first thread that is released by the next call to <xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0d4b8-119">Listedeki bir sonraki iş parçacığı aşağıdaki çağrıda yayımlanır ve bu şekilde devam eder.</span><span class="sxs-lookup"><span data-stu-id="0d4b8-119">The next thread in the list is released on the following call, and so on.</span></span>  
  
 <span data-ttu-id="0d4b8-120">Liste boş değilse, bu yöntem S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="0d4b8-120">If the list is not empty, this method returns S_OK.</span></span> <span data-ttu-id="0d4b8-121">Liste boşsa, yöntem S_FALSE döndürür; Bu durumda, numaralandırma hala geçerlidir, ancak boş olur.</span><span class="sxs-lookup"><span data-stu-id="0d4b8-121">If the list is empty, the method returns S_FALSE; in this case, the enumeration is still valid, although it is empty.</span></span>  
  
 <span data-ttu-id="0d4b8-122">Her iki durumda da, numaralandırma arabirimi yalnızca geçerli eşitlenmiş durumun süresi boyunca kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0d4b8-122">In either case, the enumeration interface is usable only for the duration of the current synchronized state.</span></span> <span data-ttu-id="0d4b8-123">Ancak, iş parçacığından gelen arabirimler, iş parçacığı çıkıncaya kadar geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="0d4b8-123">However, the thread's interfaces dispensed from it are valid until the thread exits.</span></span>  
  
 <span data-ttu-id="0d4b8-124">`ppThreadEnum`Geçerli bir işaretçi değilse, sonuç tanımsızdır.</span><span class="sxs-lookup"><span data-stu-id="0d4b8-124">If `ppThreadEnum` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="0d4b8-125">Bir hata oluşursa, herhangi bir iş parçacığı izleyiciden bekliyorsa, yöntem hata belirten bir HRESULT döndürür.</span><span class="sxs-lookup"><span data-stu-id="0d4b8-125">If an error occurs such that it cannot be determined which, if any, threads are waiting for the monitor, the method returns an HRESULT that indicates failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d4b8-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0d4b8-126">Requirements</span></span>  

 <span data-ttu-id="0d4b8-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d4b8-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d4b8-128">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0d4b8-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0d4b8-129">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0d4b8-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0d4b8-130">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d4b8-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d4b8-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0d4b8-131">See also</span></span>

- [<span data-ttu-id="0d4b8-132">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0d4b8-132">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="0d4b8-133">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="0d4b8-133">Debugging</span></span>](index.md)

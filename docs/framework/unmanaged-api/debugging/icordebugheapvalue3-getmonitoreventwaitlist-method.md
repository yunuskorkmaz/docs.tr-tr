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
ms.openlocfilehash: 0fbff178efd4d0dff3593907b3d40e946be2ff6e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121305"
---
# <a name="icordebugheapvalue3getmonitoreventwaitlist-method"></a><span data-ttu-id="86645-102">ICorDebugHeapValue3::GetMonitorEventWaitList Yöntemi</span><span class="sxs-lookup"><span data-stu-id="86645-102">ICorDebugHeapValue3::GetMonitorEventWaitList Method</span></span>
<span data-ttu-id="86645-103">Bir izleyici kilidi ile ilişkili olayda sıraya alınan iş parçacıklarının sıralı bir listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="86645-103">Provides an ordered list of threads that are queued on the event that is associated with a monitor lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86645-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="86645-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMonitorEventWaitList (  
    [out] ICorDebugThreadEnum **ppThreadEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86645-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="86645-105">Parameters</span></span>  
 `ppThreadEnum`  
 <span data-ttu-id="86645-106">dışı Sıralı iş parçacığı listesini sağlayan ICorDebugThreadEnum numaralandırıcısı.</span><span class="sxs-lookup"><span data-stu-id="86645-106">[out] The ICorDebugThreadEnum enumerator that provides the ordered list of threads.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="86645-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="86645-107">Return Value</span></span>  
 <span data-ttu-id="86645-108">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="86645-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="86645-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="86645-109">HRESULT</span></span>|<span data-ttu-id="86645-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="86645-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="86645-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="86645-111">S_OK</span></span>|<span data-ttu-id="86645-112">Liste boş değil.</span><span class="sxs-lookup"><span data-stu-id="86645-112">The list is not empty.</span></span>|  
|<span data-ttu-id="86645-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="86645-113">S_FALSE</span></span>|<span data-ttu-id="86645-114">Liste boş.</span><span class="sxs-lookup"><span data-stu-id="86645-114">The list is empty.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="86645-115">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="86645-115">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86645-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="86645-116">Remarks</span></span>  
 <span data-ttu-id="86645-117">Listedeki ilk iş parçacığı, <xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType>sonraki çağrısıyla yayınlanan ilk iş parçacığıdır.</span><span class="sxs-lookup"><span data-stu-id="86645-117">The first thread in the list is the first thread that is released by the next call to <xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType>.</span></span> <span data-ttu-id="86645-118">Listedeki bir sonraki iş parçacığı aşağıdaki çağrıda yayımlanır ve bu şekilde devam eder.</span><span class="sxs-lookup"><span data-stu-id="86645-118">The next thread in the list is released on the following call, and so on.</span></span>  
  
 <span data-ttu-id="86645-119">Liste boş değilse, bu yöntem S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="86645-119">If the list is not empty, this method returns S_OK.</span></span> <span data-ttu-id="86645-120">Liste boşsa, yöntem S_FALSE döndürür; Bu durumda, numaralandırma hala geçerlidir, ancak boş olur.</span><span class="sxs-lookup"><span data-stu-id="86645-120">If the list is empty, the method returns S_FALSE; in this case, the enumeration is still valid, although it is empty.</span></span>  
  
 <span data-ttu-id="86645-121">Her iki durumda da, numaralandırma arabirimi yalnızca geçerli eşitlenmiş durumun süresi boyunca kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="86645-121">In either case, the enumeration interface is usable only for the duration of the current synchronized state.</span></span> <span data-ttu-id="86645-122">Ancak, iş parçacığından gelen arabirimler, iş parçacığı çıkıncaya kadar geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="86645-122">However, the thread's interfaces dispensed from it are valid until the thread exits.</span></span>  
  
 <span data-ttu-id="86645-123">`ppThreadEnum` geçerli bir işaretçi değilse, sonuç tanımsızdır.</span><span class="sxs-lookup"><span data-stu-id="86645-123">If `ppThreadEnum` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="86645-124">Bir hata oluşursa, herhangi bir iş parçacığı izleyiciden bekliyorsa, yöntem hata belirten bir HRESULT döndürür.</span><span class="sxs-lookup"><span data-stu-id="86645-124">If an error occurs such that it cannot be determined which, if any, threads are waiting for the monitor, the method returns an HRESULT that indicates failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86645-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="86645-125">Requirements</span></span>  
 <span data-ttu-id="86645-126">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86645-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86645-127">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="86645-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="86645-128">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="86645-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86645-129">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86645-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86645-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86645-130">See also</span></span>

- [<span data-ttu-id="86645-131">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="86645-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="86645-132">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="86645-132">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

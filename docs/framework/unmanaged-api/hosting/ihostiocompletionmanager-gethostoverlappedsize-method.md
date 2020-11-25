---
title: IHostIoCompletionManager::GetHostOverlappedSize Yöntemi
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.GetHostOverlappedSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetHostOverlappedSize
helpviewer_keywords:
- IHostIoCompletionManager::GetHostOverlappedSize method [.NET Framework hosting]
- GetHostOverlappedSize method [.NET Framework hosting]
ms.assetid: 2902578b-d5e2-4f8d-a103-0c7b6dceda9e
topic_type:
- apiref
ms.openlocfilehash: 612a5f08982b1db5c940a7cca93166480b21e612
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724864"
---
# <a name="ihostiocompletionmanagergethostoverlappedsize-method"></a><span data-ttu-id="a7bde-102">IHostIoCompletionManager::GetHostOverlappedSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a7bde-102">IHostIoCompletionManager::GetHostOverlappedSize Method</span></span>

<span data-ttu-id="a7bde-103">Ana bilgisayarın g/ç isteklerine eklenmesini amaçladığı tüm özel verilerin boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="a7bde-103">Gets the size of any custom data the host intends to append to I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7bde-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a7bde-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHostOverlappedSize (  
    [out] DWORD *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7bde-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a7bde-105">Parameters</span></span>  

 `pcbSize`  
 <span data-ttu-id="a7bde-106">dışı Ortak dil çalışma zamanının (CLR) Win32 nesnesinin boyutuna ek olarak ayırması gereken bayt sayısına yönelik bir işaretçi `OVERLAPPED` .</span><span class="sxs-lookup"><span data-stu-id="a7bde-106">[out] A pointer to the number of bytes that the common language runtime (CLR) should allocate in addition to the size of the Win32 `OVERLAPPED` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a7bde-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a7bde-107">Return Value</span></span>  
  
|<span data-ttu-id="a7bde-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a7bde-108">HRESULT</span></span>|<span data-ttu-id="a7bde-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a7bde-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a7bde-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a7bde-110">S_OK</span></span>|<span data-ttu-id="a7bde-111">`GetHostOverlappedSize` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="a7bde-111">`GetHostOverlappedSize` returned successfully.</span></span>|  
|<span data-ttu-id="a7bde-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a7bde-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a7bde-113">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="a7bde-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a7bde-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a7bde-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a7bde-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="a7bde-115">The call timed out.</span></span>|  
|<span data-ttu-id="a7bde-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a7bde-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a7bde-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="a7bde-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a7bde-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a7bde-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a7bde-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="a7bde-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a7bde-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a7bde-120">E_FAIL</span></span>|<span data-ttu-id="a7bde-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="a7bde-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a7bde-122">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a7bde-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a7bde-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="a7bde-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7bde-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a7bde-124">Remarks</span></span>  

 <span data-ttu-id="a7bde-125">Windows platformu API 'Lerine yönelik tüm zaman uyumsuz g/ç çağrıları `OVERLAPPED` , dosya işaretçisi konumu gibi bilgiler sağlayan bir Win32 nesnesi alır.</span><span class="sxs-lookup"><span data-stu-id="a7bde-125">All asynchronous I/O calls to Windows Platform APIs take a Win32 `OVERLAPPED` object, which provides information such as the file pointer position.</span></span> <span data-ttu-id="a7bde-126">Durumu korumak için, zaman uyumsuz g/ç çağrısı yapan uygulamalar genellikle yapıya özel veri ekler.</span><span class="sxs-lookup"><span data-stu-id="a7bde-126">To maintain state, applications that make asynchronous I/O calls typically add custom data to the structure.</span></span> <span data-ttu-id="a7bde-127">`GetHostOverlappedSize` ve [ıhostiocompletionmanager:: ınitializehostoverlamış](ihostiocompletionmanager-initializehostoverlapped-method.md) , konağın bu tür özel verileri eklemesi için bir fırsat sağlar.</span><span class="sxs-lookup"><span data-stu-id="a7bde-127">`GetHostOverlappedSize` and [IHostIoCompletionManager::InitializeHostOverlapped](ihostiocompletionmanager-initializehostoverlapped-method.md) provide an opportunity for the host to include such custom data.</span></span>  
  
 <span data-ttu-id="a7bde-128">CLR, `GetHostOverlappedSize` konağın nesnesine eklenmesini amaçladığı özel verilerin boyutunu belirlemede yöntemini çağırır `OVERLAPPED` .</span><span class="sxs-lookup"><span data-stu-id="a7bde-128">The CLR calls the `GetHostOverlappedSize` method to determine the size of the custom data that the host intends to append to the `OVERLAPPED` object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a7bde-129">`GetHostOverlappedSize` yalnızca bir kez çağrılır.</span><span class="sxs-lookup"><span data-stu-id="a7bde-129">`GetHostOverlappedSize` is called only once.</span></span> <span data-ttu-id="a7bde-130">Konağın özel verileri her g/ç isteği için aynı boyutta olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a7bde-130">The host's custom data must be the same size for every I/O request.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a7bde-131">`OVERLAPPED`Nesnenin kendisi değerine dahil değildir `pcbSize` .</span><span class="sxs-lookup"><span data-stu-id="a7bde-131">The size of the `OVERLAPPED` object itself is not included in the value of `pcbSize`.</span></span>  
  
 <span data-ttu-id="a7bde-132">Yapı hakkında daha fazla bilgi için `OVERLAPPED` bkz. Windows platformu belgeleri.</span><span class="sxs-lookup"><span data-stu-id="a7bde-132">For more information about the `OVERLAPPED` structure, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7bde-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a7bde-133">Requirements</span></span>  

 <span data-ttu-id="a7bde-134">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7bde-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7bde-135">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a7bde-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a7bde-136">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="a7bde-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a7bde-137">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7bde-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7bde-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7bde-138">See also</span></span>

- <xref:System.Threading.NativeOverlapped>
- [<span data-ttu-id="a7bde-139">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a7bde-139">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="a7bde-140">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a7bde-140">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)

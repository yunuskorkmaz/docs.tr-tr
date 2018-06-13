---
title: IHostIoCompletionManager::GetHostOverlappedSize Metodu
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6713fdb822babf607752c1823a32dae43a7d567e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33439615"
---
# <a name="ihostiocompletionmanagergethostoverlappedsize-method"></a><span data-ttu-id="77e68-102">IHostIoCompletionManager::GetHostOverlappedSize Metodu</span><span class="sxs-lookup"><span data-stu-id="77e68-102">IHostIoCompletionManager::GetHostOverlappedSize Method</span></span>
<span data-ttu-id="77e68-103">G/ç istekleri eklemek için ana bilgisayar oranla herhangi bir özel veri boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="77e68-103">Gets the size of any custom data the host intends to append to I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77e68-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="77e68-104">Syntax</span></span>  
  
```  
HRESULT GetHostOverlappedSize (  
    [out] DWORD *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="77e68-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="77e68-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="77e68-106">[out] Ortak dil çalışma zamanı (CLR) Win32 boyuta ek olarak ayırmalısınız bayt sayısı için bir işaretçi `OVERLAPPED` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="77e68-106">[out] A pointer to the number of bytes that the common language runtime (CLR) should allocate in addition to the size of the Win32 `OVERLAPPED` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="77e68-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="77e68-107">Return Value</span></span>  
  
|<span data-ttu-id="77e68-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="77e68-108">HRESULT</span></span>|<span data-ttu-id="77e68-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="77e68-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="77e68-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="77e68-110">S_OK</span></span>|<span data-ttu-id="77e68-111">`GetHostOverlappedSize` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="77e68-111">`GetHostOverlappedSize` returned successfully.</span></span>|  
|<span data-ttu-id="77e68-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="77e68-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="77e68-113">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="77e68-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="77e68-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="77e68-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="77e68-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="77e68-115">The call timed out.</span></span>|  
|<span data-ttu-id="77e68-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="77e68-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="77e68-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="77e68-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="77e68-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="77e68-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="77e68-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="77e68-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="77e68-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="77e68-120">E_FAIL</span></span>|<span data-ttu-id="77e68-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="77e68-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="77e68-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="77e68-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="77e68-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="77e68-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="77e68-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="77e68-124">Remarks</span></span>  
 <span data-ttu-id="77e68-125">Win32 Windows Platform API'leri tüm zaman uyumsuz g/ç çağrıları ele `OVERLAPPED` nesnesini dosya işaretçisini konumu gibi bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="77e68-125">All asynchronous I/O calls to Windows Platform APIs take a Win32 `OVERLAPPED` object, which provides information such as the file pointer position.</span></span> <span data-ttu-id="77e68-126">Zaman uyumsuz g/ç genellikle aramalarda uygulamaları durumunu korumak üzere yapısına özel veri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="77e68-126">To maintain state, applications that make asynchronous I/O calls typically add custom data to the structure.</span></span> <span data-ttu-id="77e68-127">`GetHostOverlappedSize` ve [Ihostıocompletionmanager::ınitializehostoverlapped](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md) gibi özel verileri dahil etmek ana bilgisayar için bir fırsattır.</span><span class="sxs-lookup"><span data-stu-id="77e68-127">`GetHostOverlappedSize` and [IHostIoCompletionManager::InitializeHostOverlapped](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md) provide an opportunity for the host to include such custom data.</span></span>  
  
 <span data-ttu-id="77e68-128">CLR çağrıları `GetHostOverlappedSize` eklemek için ana bilgisayar oranla özel veri boyutunu belirlemek için yöntemi `OVERLAPPED` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="77e68-128">The CLR calls the `GetHostOverlappedSize` method to determine the size of the custom data that the host intends to append to the `OVERLAPPED` object.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="77e68-129">`GetHostOverlappedSize` yalnızca bir kez çağrılır.</span><span class="sxs-lookup"><span data-stu-id="77e68-129">`GetHostOverlappedSize` is called only once.</span></span> <span data-ttu-id="77e68-130">Ana bilgisayarın özel veri her g/ç istek için aynı boyutta olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="77e68-130">The host's custom data must be the same size for every I/O request.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="77e68-131">Boyutunu `OVERLAPPED` nesnenin kendisini değerinde eklenmedi `pcbSize`.</span><span class="sxs-lookup"><span data-stu-id="77e68-131">The size of the `OVERLAPPED` object itself is not included in the value of `pcbSize`.</span></span>  
  
 <span data-ttu-id="77e68-132">Hakkında daha fazla bilgi için `OVERLAPPED` yapısı, Windows platformu belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="77e68-132">For more information about the `OVERLAPPED` structure, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77e68-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="77e68-133">Requirements</span></span>  
 <span data-ttu-id="77e68-134">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77e68-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77e68-135">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="77e68-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="77e68-136">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="77e68-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="77e68-137">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77e68-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77e68-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="77e68-138">See Also</span></span>  
 <xref:System.Threading.NativeOverlapped>  
 [<span data-ttu-id="77e68-139">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="77e68-139">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="77e68-140">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="77e68-140">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)

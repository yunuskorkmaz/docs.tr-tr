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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e4a5661128765cc058417fef6373767d46a4bd7b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59111806"
---
# <a name="ihostiocompletionmanagergethostoverlappedsize-method"></a><span data-ttu-id="a0b5c-102">IHostIoCompletionManager::GetHostOverlappedSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a0b5c-102">IHostIoCompletionManager::GetHostOverlappedSize Method</span></span>
<span data-ttu-id="a0b5c-103">G/ç istekleri eklenecek konak düşünüyor herhangi bir özel veri boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="a0b5c-103">Gets the size of any custom data the host intends to append to I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0b5c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a0b5c-104">Syntax</span></span>  
  
```  
HRESULT GetHostOverlappedSize (  
    [out] DWORD *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a0b5c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a0b5c-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="a0b5c-106">[out] Ortak dil çalışma zamanı (CLR) Win32 boyutuna ek olarak ayırmalısınız bayt sayısı için bir işaretçi `OVERLAPPED` nesne.</span><span class="sxs-lookup"><span data-stu-id="a0b5c-106">[out] A pointer to the number of bytes that the common language runtime (CLR) should allocate in addition to the size of the Win32 `OVERLAPPED` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a0b5c-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a0b5c-107">Return Value</span></span>  
  
|<span data-ttu-id="a0b5c-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a0b5c-108">HRESULT</span></span>|<span data-ttu-id="a0b5c-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a0b5c-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a0b5c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a0b5c-110">S_OK</span></span>|`GetHostOverlappedSize` <span data-ttu-id="a0b5c-111">başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="a0b5c-111">returned successfully.</span></span>|  
|<span data-ttu-id="a0b5c-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a0b5c-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a0b5c-113">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="a0b5c-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a0b5c-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a0b5c-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a0b5c-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="a0b5c-115">The call timed out.</span></span>|  
|<span data-ttu-id="a0b5c-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a0b5c-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a0b5c-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="a0b5c-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a0b5c-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a0b5c-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a0b5c-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="a0b5c-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a0b5c-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a0b5c-120">E_FAIL</span></span>|<span data-ttu-id="a0b5c-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="a0b5c-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a0b5c-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a0b5c-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a0b5c-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="a0b5c-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0b5c-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a0b5c-124">Remarks</span></span>  
 <span data-ttu-id="a0b5c-125">Zaman uyumsuz g/ç çağrısı Windows Platform API'leri için bir Win32 ele `OVERLAPPED` dosya işaretçisi konumunu gibi bilgileri sağlayan nesne.</span><span class="sxs-lookup"><span data-stu-id="a0b5c-125">All asynchronous I/O calls to Windows Platform APIs take a Win32 `OVERLAPPED` object, which provides information such as the file pointer position.</span></span> <span data-ttu-id="a0b5c-126">Genellikle zaman uyumsuz g/ç çağrısı yapan uygulamaların durumunu korumak üzere yapısına özel veri ekleme.</span><span class="sxs-lookup"><span data-stu-id="a0b5c-126">To maintain state, applications that make asynchronous I/O calls typically add custom data to the structure.</span></span> `GetHostOverlappedSize` <span data-ttu-id="a0b5c-127">ve [Ihostıocompletionmanager::ınitializehostoverlapped](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md) bu tür özel veriler içerecek şekilde ana bilgisayar için bir fırsat sunar.</span><span class="sxs-lookup"><span data-stu-id="a0b5c-127">and [IHostIoCompletionManager::InitializeHostOverlapped](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md) provide an opportunity for the host to include such custom data.</span></span>  
  
 <span data-ttu-id="a0b5c-128">CLR çağrıları `GetHostOverlappedSize` eklenecek konak düşünüyor özel veri boyutunu belirlemek için yöntemi `OVERLAPPED` nesne.</span><span class="sxs-lookup"><span data-stu-id="a0b5c-128">The CLR calls the `GetHostOverlappedSize` method to determine the size of the custom data that the host intends to append to the `OVERLAPPED` object.</span></span>  
  
> [!NOTE]
>  `GetHostOverlappedSize` <span data-ttu-id="a0b5c-129">yalnızca bir kez çağrılır.</span><span class="sxs-lookup"><span data-stu-id="a0b5c-129">is called only once.</span></span> <span data-ttu-id="a0b5c-130">Ana bilgisayarın özel veri g/ç her istek için aynı boyutta olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a0b5c-130">The host's custom data must be the same size for every I/O request.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a0b5c-131">Boyutu `OVERLAPPED` nesnenin kendisini değerine dahil değildir `pcbSize`.</span><span class="sxs-lookup"><span data-stu-id="a0b5c-131">The size of the `OVERLAPPED` object itself is not included in the value of `pcbSize`.</span></span>  
  
 <span data-ttu-id="a0b5c-132">Hakkında daha fazla bilgi için `OVERLAPPED` yapısı, Windows Platform belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="a0b5c-132">For more information about the `OVERLAPPED` structure, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0b5c-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a0b5c-133">Requirements</span></span>  
 <span data-ttu-id="a0b5c-134">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0b5c-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0b5c-135">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a0b5c-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a0b5c-136">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="a0b5c-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="a0b5c-137">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="a0b5c-137">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a0b5c-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a0b5c-138">See also</span></span>

- <xref:System.Threading.NativeOverlapped>
- [<span data-ttu-id="a0b5c-139">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a0b5c-139">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="a0b5c-140">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a0b5c-140">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)

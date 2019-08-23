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
ms.openlocfilehash: c43f906961b9e76d5f0f34ba5a5b2f656f5b1488
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937513"
---
# <a name="ihostiocompletionmanagergethostoverlappedsize-method"></a><span data-ttu-id="7bd53-102">IHostIoCompletionManager::GetHostOverlappedSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7bd53-102">IHostIoCompletionManager::GetHostOverlappedSize Method</span></span>
<span data-ttu-id="7bd53-103">Ana bilgisayarın g/ç isteklerine eklenmesini amaçladığı tüm özel verilerin boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="7bd53-103">Gets the size of any custom data the host intends to append to I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bd53-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7bd53-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHostOverlappedSize (  
    [out] DWORD *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7bd53-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7bd53-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="7bd53-106">dışı Ortak dil çalışma zamanının (CLR) Win32 `OVERLAPPED` nesnesinin boyutuna ek olarak ayırması gereken bayt sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7bd53-106">[out] A pointer to the number of bytes that the common language runtime (CLR) should allocate in addition to the size of the Win32 `OVERLAPPED` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7bd53-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7bd53-107">Return Value</span></span>  
  
|<span data-ttu-id="7bd53-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7bd53-108">HRESULT</span></span>|<span data-ttu-id="7bd53-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7bd53-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7bd53-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="7bd53-110">S_OK</span></span>|<span data-ttu-id="7bd53-111">`GetHostOverlappedSize`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="7bd53-111">`GetHostOverlappedSize` returned successfully.</span></span>|  
|<span data-ttu-id="7bd53-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7bd53-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7bd53-113">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="7bd53-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7bd53-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7bd53-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7bd53-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="7bd53-115">The call timed out.</span></span>|  
|<span data-ttu-id="7bd53-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7bd53-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7bd53-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="7bd53-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7bd53-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7bd53-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7bd53-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="7bd53-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7bd53-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7bd53-120">E_FAIL</span></span>|<span data-ttu-id="7bd53-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="7bd53-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7bd53-122">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="7bd53-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7bd53-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="7bd53-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7bd53-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7bd53-124">Remarks</span></span>  
 <span data-ttu-id="7bd53-125">Windows platformu API 'lerine yönelik tüm zaman uyumsuz g/ç çağrıları, `OVERLAPPED` dosya işaretçisi konumu gibi bilgiler sağlayan bir Win32 nesnesi alır.</span><span class="sxs-lookup"><span data-stu-id="7bd53-125">All asynchronous I/O calls to Windows Platform APIs take a Win32 `OVERLAPPED` object, which provides information such as the file pointer position.</span></span> <span data-ttu-id="7bd53-126">Durumu korumak için, zaman uyumsuz g/ç çağrısı yapan uygulamalar genellikle yapıya özel veri ekler.</span><span class="sxs-lookup"><span data-stu-id="7bd53-126">To maintain state, applications that make asynchronous I/O calls typically add custom data to the structure.</span></span> <span data-ttu-id="7bd53-127">`GetHostOverlappedSize`ve [ıhostiocompletionmanager:: ınitializehostoverlamış](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md) , konağın bu tür özel verileri eklemesi için bir fırsat sağlar.</span><span class="sxs-lookup"><span data-stu-id="7bd53-127">`GetHostOverlappedSize` and [IHostIoCompletionManager::InitializeHostOverlapped](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md) provide an opportunity for the host to include such custom data.</span></span>  
  
 <span data-ttu-id="7bd53-128">CLR, konağın `OVERLAPPED` nesnesine `GetHostOverlappedSize` eklenmesini amaçladığı özel verilerin boyutunu belirlemede yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="7bd53-128">The CLR calls the `GetHostOverlappedSize` method to determine the size of the custom data that the host intends to append to the `OVERLAPPED` object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7bd53-129">`GetHostOverlappedSize`yalnızca bir kez çağrılır.</span><span class="sxs-lookup"><span data-stu-id="7bd53-129">`GetHostOverlappedSize` is called only once.</span></span> <span data-ttu-id="7bd53-130">Konağın özel verileri her g/ç isteği için aynı boyutta olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7bd53-130">The host's custom data must be the same size for every I/O request.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7bd53-131">Nesnenin kendisi değerine dahil değildir `pcbSize` `OVERLAPPED` .</span><span class="sxs-lookup"><span data-stu-id="7bd53-131">The size of the `OVERLAPPED` object itself is not included in the value of `pcbSize`.</span></span>  
  
 <span data-ttu-id="7bd53-132">`OVERLAPPED` Yapı hakkında daha fazla bilgi için bkz. Windows platformu belgeleri.</span><span class="sxs-lookup"><span data-stu-id="7bd53-132">For more information about the `OVERLAPPED` structure, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7bd53-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7bd53-133">Requirements</span></span>  
 <span data-ttu-id="7bd53-134">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7bd53-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7bd53-135">**Üst bilgi** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7bd53-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7bd53-136">**Kitaplığı** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="7bd53-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7bd53-137">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7bd53-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bd53-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7bd53-138">See also</span></span>

- <xref:System.Threading.NativeOverlapped>
- [<span data-ttu-id="7bd53-139">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7bd53-139">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="7bd53-140">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7bd53-140">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)

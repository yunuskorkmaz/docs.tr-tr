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
ms.openlocfilehash: 3c662021894acbb8eb448fa2166498254158caa4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133859"
---
# <a name="ihostiocompletionmanagergethostoverlappedsize-method"></a><span data-ttu-id="b7c2c-102">IHostIoCompletionManager::GetHostOverlappedSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b7c2c-102">IHostIoCompletionManager::GetHostOverlappedSize Method</span></span>
<span data-ttu-id="b7c2c-103">Ana bilgisayarın g/ç isteklerine eklenmesini amaçladığı tüm özel verilerin boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="b7c2c-103">Gets the size of any custom data the host intends to append to I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7c2c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b7c2c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHostOverlappedSize (  
    [out] DWORD *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b7c2c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b7c2c-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="b7c2c-106">dışı Ortak dil çalışma zamanının (CLR) Win32 `OVERLAPPED` nesnesinin boyutuna ek olarak ayırması gereken bayt sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b7c2c-106">[out] A pointer to the number of bytes that the common language runtime (CLR) should allocate in addition to the size of the Win32 `OVERLAPPED` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b7c2c-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b7c2c-107">Return Value</span></span>  
  
|<span data-ttu-id="b7c2c-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b7c2c-108">HRESULT</span></span>|<span data-ttu-id="b7c2c-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b7c2c-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b7c2c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b7c2c-110">S_OK</span></span>|<span data-ttu-id="b7c2c-111">`GetHostOverlappedSize` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="b7c2c-111">`GetHostOverlappedSize` returned successfully.</span></span>|  
|<span data-ttu-id="b7c2c-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b7c2c-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b7c2c-113">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="b7c2c-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b7c2c-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b7c2c-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b7c2c-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="b7c2c-115">The call timed out.</span></span>|  
|<span data-ttu-id="b7c2c-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b7c2c-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b7c2c-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="b7c2c-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b7c2c-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b7c2c-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b7c2c-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="b7c2c-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b7c2c-120">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="b7c2c-120">E_FAIL</span></span>|<span data-ttu-id="b7c2c-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="b7c2c-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b7c2c-122">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="b7c2c-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b7c2c-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="b7c2c-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b7c2c-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b7c2c-124">Remarks</span></span>  
 <span data-ttu-id="b7c2c-125">Windows platformu API 'Lerine yönelik tüm zaman uyumsuz g/ç çağrıları, dosya işaretçisi konumu gibi bilgiler sağlayan bir Win32 `OVERLAPPED` nesnesi alır.</span><span class="sxs-lookup"><span data-stu-id="b7c2c-125">All asynchronous I/O calls to Windows Platform APIs take a Win32 `OVERLAPPED` object, which provides information such as the file pointer position.</span></span> <span data-ttu-id="b7c2c-126">Durumu korumak için, zaman uyumsuz g/ç çağrısı yapan uygulamalar genellikle yapıya özel veri ekler.</span><span class="sxs-lookup"><span data-stu-id="b7c2c-126">To maintain state, applications that make asynchronous I/O calls typically add custom data to the structure.</span></span> <span data-ttu-id="b7c2c-127">`GetHostOverlappedSize` ve [ıhostiocompletionmanager:: ınitializehostoverlamış](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md) , konağın bu tür özel verileri eklemesi için bir fırsat sağlar.</span><span class="sxs-lookup"><span data-stu-id="b7c2c-127">`GetHostOverlappedSize` and [IHostIoCompletionManager::InitializeHostOverlapped](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md) provide an opportunity for the host to include such custom data.</span></span>  
  
 <span data-ttu-id="b7c2c-128">CLR, ana bilgisayarın `OVERLAPPED` nesnesine eklenmesini amaçladığı özel verilerin boyutunu belirlemekte `GetHostOverlappedSize` yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="b7c2c-128">The CLR calls the `GetHostOverlappedSize` method to determine the size of the custom data that the host intends to append to the `OVERLAPPED` object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b7c2c-129">`GetHostOverlappedSize` yalnızca bir kez çağrılır.</span><span class="sxs-lookup"><span data-stu-id="b7c2c-129">`GetHostOverlappedSize` is called only once.</span></span> <span data-ttu-id="b7c2c-130">Konağın özel verileri her g/ç isteği için aynı boyutta olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b7c2c-130">The host's custom data must be the same size for every I/O request.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b7c2c-131">`OVERLAPPED` nesnenin kendisi `pcbSize`değerine dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="b7c2c-131">The size of the `OVERLAPPED` object itself is not included in the value of `pcbSize`.</span></span>  
  
 <span data-ttu-id="b7c2c-132">`OVERLAPPED` yapısı hakkında daha fazla bilgi için bkz. Windows platformu belgeleri.</span><span class="sxs-lookup"><span data-stu-id="b7c2c-132">For more information about the `OVERLAPPED` structure, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7c2c-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b7c2c-133">Requirements</span></span>  
 <span data-ttu-id="b7c2c-134">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7c2c-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7c2c-135">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b7c2c-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b7c2c-136">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="b7c2c-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b7c2c-137">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7c2c-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7c2c-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b7c2c-138">See also</span></span>

- <xref:System.Threading.NativeOverlapped>
- [<span data-ttu-id="b7c2c-139">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b7c2c-139">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="b7c2c-140">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b7c2c-140">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)

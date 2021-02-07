---
description: 'Şu konuda daha fazla bilgi edinin: ıhostiocompletionmanager:: GetHostOverlappedSize Yöntemi'
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
ms.openlocfilehash: 2a2ebe1da82c5702269b634eadfe98b72739e3df
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708573"
---
# <a name="ihostiocompletionmanagergethostoverlappedsize-method"></a><span data-ttu-id="adfdd-103">IHostIoCompletionManager::GetHostOverlappedSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="adfdd-103">IHostIoCompletionManager::GetHostOverlappedSize Method</span></span>

<span data-ttu-id="adfdd-104">Ana bilgisayarın g/ç isteklerine eklenmesini amaçladığı tüm özel verilerin boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="adfdd-104">Gets the size of any custom data the host intends to append to I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="adfdd-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="adfdd-105">Syntax</span></span>  
  
```cpp  
HRESULT GetHostOverlappedSize (  
    [out] DWORD *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="adfdd-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="adfdd-106">Parameters</span></span>  

 `pcbSize`  
 <span data-ttu-id="adfdd-107">dışı Ortak dil çalışma zamanının (CLR) Win32 nesnesinin boyutuna ek olarak ayırması gereken bayt sayısına yönelik bir işaretçi `OVERLAPPED` .</span><span class="sxs-lookup"><span data-stu-id="adfdd-107">[out] A pointer to the number of bytes that the common language runtime (CLR) should allocate in addition to the size of the Win32 `OVERLAPPED` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="adfdd-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="adfdd-108">Return Value</span></span>  
  
|<span data-ttu-id="adfdd-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="adfdd-109">HRESULT</span></span>|<span data-ttu-id="adfdd-110">Description</span><span class="sxs-lookup"><span data-stu-id="adfdd-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="adfdd-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="adfdd-111">S_OK</span></span>|<span data-ttu-id="adfdd-112">`GetHostOverlappedSize` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="adfdd-112">`GetHostOverlappedSize` returned successfully.</span></span>|  
|<span data-ttu-id="adfdd-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="adfdd-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="adfdd-114">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="adfdd-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="adfdd-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="adfdd-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="adfdd-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="adfdd-116">The call timed out.</span></span>|  
|<span data-ttu-id="adfdd-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="adfdd-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="adfdd-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="adfdd-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="adfdd-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="adfdd-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="adfdd-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="adfdd-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="adfdd-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="adfdd-121">E_FAIL</span></span>|<span data-ttu-id="adfdd-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="adfdd-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="adfdd-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="adfdd-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="adfdd-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="adfdd-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="adfdd-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="adfdd-125">Remarks</span></span>  

 <span data-ttu-id="adfdd-126">Windows platformu API 'Lerine yönelik tüm zaman uyumsuz g/ç çağrıları `OVERLAPPED` , dosya işaretçisi konumu gibi bilgiler sağlayan bir Win32 nesnesi alır.</span><span class="sxs-lookup"><span data-stu-id="adfdd-126">All asynchronous I/O calls to Windows Platform APIs take a Win32 `OVERLAPPED` object, which provides information such as the file pointer position.</span></span> <span data-ttu-id="adfdd-127">Durumu korumak için, zaman uyumsuz g/ç çağrısı yapan uygulamalar genellikle yapıya özel veri ekler.</span><span class="sxs-lookup"><span data-stu-id="adfdd-127">To maintain state, applications that make asynchronous I/O calls typically add custom data to the structure.</span></span> <span data-ttu-id="adfdd-128">`GetHostOverlappedSize` ve [ıhostiocompletionmanager:: ınitializehostoverlamış](ihostiocompletionmanager-initializehostoverlapped-method.md) , konağın bu tür özel verileri eklemesi için bir fırsat sağlar.</span><span class="sxs-lookup"><span data-stu-id="adfdd-128">`GetHostOverlappedSize` and [IHostIoCompletionManager::InitializeHostOverlapped](ihostiocompletionmanager-initializehostoverlapped-method.md) provide an opportunity for the host to include such custom data.</span></span>  
  
 <span data-ttu-id="adfdd-129">CLR, `GetHostOverlappedSize` konağın nesnesine eklenmesini amaçladığı özel verilerin boyutunu belirlemede yöntemini çağırır `OVERLAPPED` .</span><span class="sxs-lookup"><span data-stu-id="adfdd-129">The CLR calls the `GetHostOverlappedSize` method to determine the size of the custom data that the host intends to append to the `OVERLAPPED` object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="adfdd-130">`GetHostOverlappedSize` yalnızca bir kez çağrılır.</span><span class="sxs-lookup"><span data-stu-id="adfdd-130">`GetHostOverlappedSize` is called only once.</span></span> <span data-ttu-id="adfdd-131">Konağın özel verileri her g/ç isteği için aynı boyutta olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="adfdd-131">The host's custom data must be the same size for every I/O request.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="adfdd-132">`OVERLAPPED`Nesnenin kendisi değerine dahil değildir `pcbSize` .</span><span class="sxs-lookup"><span data-stu-id="adfdd-132">The size of the `OVERLAPPED` object itself is not included in the value of `pcbSize`.</span></span>  
  
 <span data-ttu-id="adfdd-133">Yapı hakkında daha fazla bilgi için `OVERLAPPED` bkz. Windows platformu belgeleri.</span><span class="sxs-lookup"><span data-stu-id="adfdd-133">For more information about the `OVERLAPPED` structure, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="adfdd-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="adfdd-134">Requirements</span></span>  

 <span data-ttu-id="adfdd-135">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="adfdd-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="adfdd-136">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="adfdd-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="adfdd-137">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="adfdd-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="adfdd-138">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="adfdd-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adfdd-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="adfdd-139">See also</span></span>

- <xref:System.Threading.NativeOverlapped>
- [<span data-ttu-id="adfdd-140">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="adfdd-140">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="adfdd-141">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="adfdd-141">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)

---
description: ': Ihostiocompletionmanager:: ınitializehostoverlapoladmethod hakkında daha fazla bilgi edinin'
title: IHostIoCompletionManager::InitializeHostOverlapped Yöntemi
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.InitializeHostOverlapped
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::InitializeHostOverlapped
helpviewer_keywords:
- IHostIoCompletionManager::InitializeHostOverlapped method [.NET Framework hosting]
- InitializeHostOverlapped method [.NET Framework hosting]
ms.assetid: c35199bf-bc47-4901-b467-4e8a37644bbb
topic_type:
- apiref
ms.openlocfilehash: 10be7edb67143937dec6efc6e35466466374d32d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708469"
---
# <a name="ihostiocompletionmanagerinitializehostoverlapped-method"></a><span data-ttu-id="61be6-103">IHostIoCompletionManager::InitializeHostOverlapped Yöntemi</span><span class="sxs-lookup"><span data-stu-id="61be6-103">IHostIoCompletionManager::InitializeHostOverlapped Method</span></span>

<span data-ttu-id="61be6-104">Ana bilgisayara, `OVERLAPPED` zaman uyumsuz g/ç istekleri için kullanılan bir Win32 yapısına eklenecek özel verileri başlatma fırsatı sağlar.</span><span class="sxs-lookup"><span data-stu-id="61be6-104">Provides the host with an opportunity to initialize any custom data to append to a Win32 `OVERLAPPED` structure that is used for asynchronous I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61be6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="61be6-105">Syntax</span></span>  
  
```cpp  
HRESULT InitializeHostOverlapped (  
    [in] void* pvOverlapped  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="61be6-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="61be6-106">Parameters</span></span>  

 `pvOverlapped`  
 <span data-ttu-id="61be6-107">'ndaki `OVERLAPPED` G/ç isteğine dahil edilecek Win32 yapısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="61be6-107">[in] A pointer to the Win32 `OVERLAPPED` structure to be included with the I/O request.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="61be6-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="61be6-108">Return Value</span></span>  
  
|<span data-ttu-id="61be6-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="61be6-109">HRESULT</span></span>|<span data-ttu-id="61be6-110">Description</span><span class="sxs-lookup"><span data-stu-id="61be6-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="61be6-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="61be6-111">S_OK</span></span>|<span data-ttu-id="61be6-112">`InitializeHostOverlapped` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="61be6-112">`InitializeHostOverlapped` returned successfully.</span></span>|  
|<span data-ttu-id="61be6-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="61be6-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="61be6-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="61be6-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="61be6-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="61be6-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="61be6-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="61be6-116">The call timed out.</span></span>|  
|<span data-ttu-id="61be6-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="61be6-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="61be6-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="61be6-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="61be6-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="61be6-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="61be6-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="61be6-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="61be6-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="61be6-121">E_FAIL</span></span>|<span data-ttu-id="61be6-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="61be6-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="61be6-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="61be6-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="61be6-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="61be6-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="61be6-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="61be6-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="61be6-126">İstenen kaynağı ayırmak için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="61be6-126">Not enough memory was available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="61be6-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="61be6-127">Remarks</span></span>  

 <span data-ttu-id="61be6-128">Windows platformu işlevleri, `OVERLAPPED` zaman uyumsuz g/ç isteklerinin durumunu depolamak için yapıyı kullanır.</span><span class="sxs-lookup"><span data-stu-id="61be6-128">The Windows Platform functions use the `OVERLAPPED` structure to store state for asynchronous I/O requests.</span></span> <span data-ttu-id="61be6-129">CLR, `InitializeHostOverlapped` konağa özel verileri ekleme fırsatına bir örneğe çağrı yapmak için yöntemini çağırır `OVERLAPPED` .</span><span class="sxs-lookup"><span data-stu-id="61be6-129">The CLR calls the `InitializeHostOverlapped` method to give the host the opportunity to append custom data to an `OVERLAPPED` instance.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="61be6-130">Özel veri bloğunun başlangıcına ulaşmak için, konaklar yapının () boyutuna kadar olan sapmayı ayarlamış olmalıdır `OVERLAPPED` `sizeof(OVERLAPPED)` .</span><span class="sxs-lookup"><span data-stu-id="61be6-130">To get to the beginning of their custom data block, hosts must set the offset to the size of the `OVERLAPPED` structure (`sizeof(OVERLAPPED)`).</span></span>  
  
 <span data-ttu-id="61be6-131">E_OUTOFMEMORY dönüş değeri konağın özel verilerini başlatamadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="61be6-131">A return value of E_OUTOFMEMORY indicates that the host has failed to initialize its custom data.</span></span> <span data-ttu-id="61be6-132">Bu durumda, CLR bir hata bildirir ve çağrı başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="61be6-132">In this case, the CLR reports an error and fails the call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61be6-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="61be6-133">Requirements</span></span>  

 <span data-ttu-id="61be6-134">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61be6-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61be6-135">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="61be6-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="61be6-136">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="61be6-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="61be6-137">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61be6-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61be6-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="61be6-138">See also</span></span>

- [<span data-ttu-id="61be6-139">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="61be6-139">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="61be6-140">GetHostOverlappedSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="61be6-140">GetHostOverlappedSize Method</span></span>](ihostiocompletionmanager-gethostoverlappedsize-method.md)
- [<span data-ttu-id="61be6-141">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="61be6-141">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)

---
title: IHostIoCompletionManager::GetAvailableThreads Yöntemi
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.GetAvailableThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetAvailableThreads
helpviewer_keywords:
- GetAvailableThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
- IHostIoCompletionManager::GetAvailableThreads method [.NET Framework hosting]
ms.assetid: bab363d1-b859-47a4-9884-5661c611cce7
topic_type:
- apiref
ms.openlocfilehash: 7ea7395bb1f185ba59940d76def562ab5440e560
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804760"
---
# <a name="ihostiocompletionmanagergetavailablethreads-method"></a><span data-ttu-id="04674-102">IHostIoCompletionManager::GetAvailableThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="04674-102">IHostIoCompletionManager::GetAvailableThreads Method</span></span>
<span data-ttu-id="04674-103">Ana bilgisayar tarafından yönetilen ve şu anda istekleri olmayan iş parçacıklarının toplam sayısı olan g/ç Tamamlama iş parçacığı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="04674-103">Gets the number of I/O completion threads, of the total number of threads managed by the host, that are not currently servicing requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04674-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="04674-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAvailableThreads (  
    [out] DWORD *pdwAvailableIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="04674-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="04674-105">Parameters</span></span>  
 `pdwAvailableIoCompletionThreads`  
 <span data-ttu-id="04674-106">dışı Şu anda hizmet istekleri için kullanılabilir olan ana bilgisayar tarafından yönetilen g/ç Tamamlama iş parçacığı sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="04674-106">[out] A pointer to the number of I/O completion threads managed by the host that are currently available to service requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="04674-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="04674-107">Return Value</span></span>  
  
|<span data-ttu-id="04674-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="04674-108">HRESULT</span></span>|<span data-ttu-id="04674-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="04674-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="04674-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="04674-110">S_OK</span></span>|<span data-ttu-id="04674-111">`GetAvailableThreads`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="04674-111">`GetAvailableThreads` returned successfully.</span></span>|  
|<span data-ttu-id="04674-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="04674-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="04674-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="04674-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="04674-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="04674-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="04674-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="04674-115">The call timed out.</span></span>|  
|<span data-ttu-id="04674-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="04674-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="04674-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="04674-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="04674-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="04674-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="04674-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="04674-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="04674-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="04674-120">E_FAIL</span></span>|<span data-ttu-id="04674-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="04674-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="04674-122">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="04674-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="04674-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="04674-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="04674-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="04674-124">E_NOTIMPL</span></span>|<span data-ttu-id="04674-125">Konak, uygulamasının bir uygulamasını sağlamaz `GetAvailableThreads` .</span><span class="sxs-lookup"><span data-stu-id="04674-125">The host does not provide an implementation of `GetAvailableThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="04674-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="04674-126">Remarks</span></span>  
 <span data-ttu-id="04674-127">Bir ana bilgisayar, uygulama, performans veya ölçeklenebilirlik gibi nedenlerle g/ç Tamamlama iş parçacığı havuzunun boyutu üzerinde özel denetim istiyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="04674-127">A host might want exclusive control over the size of the I/O completion thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="04674-128">Bu nedenle, konağın uygulanması gerekli değildir `GetAvailableThreads` .</span><span class="sxs-lookup"><span data-stu-id="04674-128">Therefore, the host is not required to implement `GetAvailableThreads`.</span></span> <span data-ttu-id="04674-129">Bu durumda, ana bilgisayar bu yöntemden E_NOTIMPL döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="04674-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04674-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="04674-130">Requirements</span></span>  
 <span data-ttu-id="04674-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04674-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04674-132">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="04674-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="04674-133">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="04674-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="04674-134">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04674-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04674-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="04674-135">See also</span></span>

- [<span data-ttu-id="04674-136">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="04674-136">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="04674-137">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="04674-137">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)

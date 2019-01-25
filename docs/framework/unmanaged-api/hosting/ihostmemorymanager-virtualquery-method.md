---
title: IHostMemoryManager::VirtualQuery Yöntemi
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.VirtualQuery
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualQuery
helpviewer_keywords:
- IHostMemoryManager::VirtualQuery method [.NET Framework hosting]
- VirtualQuery method [.NET Framework hosting]
ms.assetid: 757af1e6-b9e8-49e7-b5db-342be3aa205f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 885871f3e6b3f10bfb7d660e2d6889e243ef751b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54734370"
---
# <a name="ihostmemorymanagervirtualquery-method"></a><span data-ttu-id="b7625-102">IHostMemoryManager::VirtualQuery Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b7625-102">IHostMemoryManager::VirtualQuery Method</span></span>
<span data-ttu-id="b7625-103">Karşılık gelen Win32 işlevini için mantıksal bir sarmalayıcı olarak görev yapar.</span><span class="sxs-lookup"><span data-stu-id="b7625-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="b7625-104">Win32 uygulaması `VirtualQuery` sayfaları çağırma işleminin sanal adres alanı içinde bir dizi hakkındaki bilgileri alır.</span><span class="sxs-lookup"><span data-stu-id="b7625-104">The Win32 implementation of `VirtualQuery` retrieves information about a range of pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7625-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b7625-105">Syntax</span></span>  
  
```  
HRESULT VirtualQuery (  
    [in]  void*    lpAddress,  
    [out] void*    lpBuffer,  
    [in]  SIZE_T   dwLength,  
    [out] SIZE_T*  pResult  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b7625-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b7625-106">Parameters</span></span>  
 `lpAddress`  
 <span data-ttu-id="b7625-107">[in] Sorgulanacak sanal bellek adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b7625-107">[in] A pointer to the address in virtual memory to be queried.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="b7625-108">[out] Belirtilen bellek bölgesini hakkında bilgi içeren bir yapıya bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b7625-108">[out] A pointer to a structure that contains information about the specified memory region.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="b7625-109">[in] Arabelleğin bayt cinsinden boyutu, `lpBuffer` işaret eder.</span><span class="sxs-lookup"><span data-stu-id="b7625-109">[in] The size, in bytes, of the buffer that `lpBuffer` points to.</span></span>  
  
 `pResult`  
 <span data-ttu-id="b7625-110">[out] Bilgi arabellek tarafından döndürülen bayt sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b7625-110">[out] A pointer to the number of bytes returned by the information buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b7625-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b7625-111">Return Value</span></span>  
  
|<span data-ttu-id="b7625-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b7625-112">HRESULT</span></span>|<span data-ttu-id="b7625-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b7625-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b7625-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="b7625-114">S_OK</span></span>|<span data-ttu-id="b7625-115">`VirtualQuery` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="b7625-115">`VirtualQuery` returned successfully.</span></span>|  
|<span data-ttu-id="b7625-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b7625-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b7625-117">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="b7625-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b7625-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b7625-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b7625-119">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="b7625-119">The call timed out.</span></span>|  
|<span data-ttu-id="b7625-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b7625-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b7625-121">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="b7625-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b7625-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b7625-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b7625-123">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="b7625-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b7625-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b7625-124">E_FAIL</span></span>|<span data-ttu-id="b7625-125">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="b7625-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b7625-126">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="b7625-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b7625-127">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="b7625-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b7625-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b7625-128">Remarks</span></span>  
 <span data-ttu-id="b7625-129">`VirtualQuery` sayfalar çağırma işleminin sanal adres alanı aralığı hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b7625-129">`VirtualQuery` provides information about a range of pages in the virtual address space of the calling process.</span></span> <span data-ttu-id="b7625-130">Bu uygulama ayarlar `pResult` bayt sayısı'için parametre bilgileri arabellekte ve HRESULT değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="b7625-130">This implementation sets the value of the `pResult` parameter to the number of bytes returned in the information buffer, and returns an HRESULT value.</span></span> <span data-ttu-id="b7625-131">Win32'de `VirtualQuery` işlev, dönüş değeri, arabellek boyutu.</span><span class="sxs-lookup"><span data-stu-id="b7625-131">In the Win32 `VirtualQuery` function, the return value is the buffer size.</span></span> <span data-ttu-id="b7625-132">Daha fazla bilgi için Windows Platform belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="b7625-132">For more information, see the Windows Platform documentation.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b7625-133">İşletim sistemi uygulaması `VirtualQuery` kilitlenme tabi değildir ve rastgele iş parçacıkları askıya kullanıcı kodunda tamamlanana kadar çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b7625-133">The operating system's implementation of `VirtualQuery` does not incur deadlock and can run to completion with random threads suspended in user code.</span></span> <span data-ttu-id="b7625-134">Bu yöntem barındırılan bir sürümünü uygularken harika dikkatli kullanın.</span><span class="sxs-lookup"><span data-stu-id="b7625-134">Use great caution when implementing a hosted version of this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7625-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b7625-135">Requirements</span></span>  
 <span data-ttu-id="b7625-136">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7625-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7625-137">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b7625-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b7625-138">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="b7625-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b7625-139">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7625-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7625-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b7625-140">See also</span></span>
- [<span data-ttu-id="b7625-141">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b7625-141">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)

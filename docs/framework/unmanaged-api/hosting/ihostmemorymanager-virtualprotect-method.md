---
title: IHostMemoryManager::VirtualProtect Yöntemi
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.VirtualProtect
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualProtect
helpviewer_keywords:
- IHostMemoryManager::VirtualProtect method [.NET Framework hosting]
- VirtualProtect method [.NET Framework hosting]
ms.assetid: 13be0299-df0d-4951-aabf-0676a30b385f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 62aa6b1d9be86a9b60abf894d67555f706e6a8ac
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59139912"
---
# <a name="ihostmemorymanagervirtualprotect-method"></a><span data-ttu-id="ec145-102">IHostMemoryManager::VirtualProtect Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ec145-102">IHostMemoryManager::VirtualProtect Method</span></span>
<span data-ttu-id="ec145-103">Karşılık gelen Win32 işlevini için mantıksal bir sarmalayıcı olarak görev yapar.</span><span class="sxs-lookup"><span data-stu-id="ec145-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="ec145-104">Win32 uygulaması `VirtualProtect` bölgesindeki korumayı taahhüt edilen sayfa çağırma işleminin sanal adres alanı değiştirir.</span><span class="sxs-lookup"><span data-stu-id="ec145-104">The Win32 implementation of `VirtualProtect` changes the protection on a region of committed pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec145-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ec145-105">Syntax</span></span>  
  
```  
HRESULT VirtualProtect (  
    [in]  void*   lpAddress,  
    [in]  SIZE_T  dwSize,  
    [in]  DWORD   flNewProtect,  
    [out] DWORD*  pflOldProtect  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec145-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ec145-106">Parameters</span></span>  
 `lpAddress`  
 <span data-ttu-id="ec145-107">[in] Taban adresi koruma niteliklerini değiştirilecek olan sanal bellek işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="ec145-107">[in] A pointer to the base address of the virtual memory whose protection attributes are to be changed.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="ec145-108">[in] Değiştirilecek bellek sayfalarının bölgesi bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="ec145-108">[in] The size, in bytes, of the region of memory pages to be changed.</span></span>  
  
 `flNewProtect`  
 <span data-ttu-id="ec145-109">[in] Bellek koruma uygulamak için türü.</span><span class="sxs-lookup"><span data-stu-id="ec145-109">[in] The type of memory protection to apply.</span></span>  
  
 `pflOldProtect`  
 <span data-ttu-id="ec145-110">[out] Önceki bellek koruma değeri için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ec145-110">[out] A pointer to the previous memory protection value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ec145-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ec145-111">Return Value</span></span>  
  
|<span data-ttu-id="ec145-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ec145-112">HRESULT</span></span>|<span data-ttu-id="ec145-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ec145-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ec145-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="ec145-114">S_OK</span></span>|<span data-ttu-id="ec145-115">`VirtualProtect` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="ec145-115">`VirtualProtect` returned successfully.</span></span>|  
|<span data-ttu-id="ec145-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ec145-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ec145-117">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="ec145-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ec145-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ec145-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ec145-119">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="ec145-119">The call timed out.</span></span>|  
|<span data-ttu-id="ec145-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ec145-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ec145-121">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="ec145-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ec145-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ec145-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ec145-123">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="ec145-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ec145-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ec145-124">E_FAIL</span></span>|<span data-ttu-id="ec145-125">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="ec145-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ec145-126">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="ec145-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ec145-127">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="ec145-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ec145-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ec145-128">Remarks</span></span>  
 <span data-ttu-id="ec145-129">Bu uygulaması `VirtualProtect` HRESULT değerini, Win32 uygulaması başarılı olduğunu belirtmek için sıfır olmayan bir değer döndürür ve hata göstermek için sıfır değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="ec145-129">This implementation of `VirtualProtect` returns an HRESULT value, while the Win32 implementation returns a non-zero value to indicate success, and a zero value to indicate failure.</span></span> <span data-ttu-id="ec145-130">Daha fazla bilgi için Windows Platform belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="ec145-130">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec145-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ec145-131">Requirements</span></span>  
 <span data-ttu-id="ec145-132">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec145-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec145-133">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ec145-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ec145-134">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="ec145-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ec145-135">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec145-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec145-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ec145-136">See also</span></span>

- [<span data-ttu-id="ec145-137">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ec145-137">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)

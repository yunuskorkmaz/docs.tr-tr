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
ms.openlocfilehash: b712b7e88e6cb5693c0823799e0980d90e34ff0a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492614"
---
# <a name="ihostmemorymanagervirtualprotect-method"></a><span data-ttu-id="7d7fc-102">IHostMemoryManager::VirtualProtect Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7d7fc-102">IHostMemoryManager::VirtualProtect Method</span></span>
<span data-ttu-id="7d7fc-103">Karşılık gelen Win32 işlevini için mantıksal bir sarmalayıcı olarak görev yapar.</span><span class="sxs-lookup"><span data-stu-id="7d7fc-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="7d7fc-104">Win32 uygulaması `VirtualProtect` bölgesindeki korumayı taahhüt edilen sayfa çağırma işleminin sanal adres alanı değiştirir.</span><span class="sxs-lookup"><span data-stu-id="7d7fc-104">The Win32 implementation of `VirtualProtect` changes the protection on a region of committed pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d7fc-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7d7fc-105">Syntax</span></span>  
  
```  
HRESULT VirtualProtect (  
    [in]  void*   lpAddress,  
    [in]  SIZE_T  dwSize,  
    [in]  DWORD   flNewProtect,  
    [out] DWORD*  pflOldProtect  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7d7fc-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7d7fc-106">Parameters</span></span>  
 `lpAddress`  
 <span data-ttu-id="7d7fc-107">[in] Taban adresi koruma niteliklerini değiştirilecek olan sanal bellek işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="7d7fc-107">[in] A pointer to the base address of the virtual memory whose protection attributes are to be changed.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="7d7fc-108">[in] Değiştirilecek bellek sayfalarının bölgesi bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="7d7fc-108">[in] The size, in bytes, of the region of memory pages to be changed.</span></span>  
  
 `flNewProtect`  
 <span data-ttu-id="7d7fc-109">[in] Bellek koruma uygulamak için türü.</span><span class="sxs-lookup"><span data-stu-id="7d7fc-109">[in] The type of memory protection to apply.</span></span>  
  
 `pflOldProtect`  
 <span data-ttu-id="7d7fc-110">[out] Önceki bellek koruma değeri için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7d7fc-110">[out] A pointer to the previous memory protection value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7d7fc-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7d7fc-111">Return Value</span></span>  
  
|<span data-ttu-id="7d7fc-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7d7fc-112">HRESULT</span></span>|<span data-ttu-id="7d7fc-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7d7fc-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7d7fc-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="7d7fc-114">S_OK</span></span>|<span data-ttu-id="7d7fc-115">`VirtualProtect` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="7d7fc-115">`VirtualProtect` returned successfully.</span></span>|  
|<span data-ttu-id="7d7fc-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7d7fc-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7d7fc-117">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="7d7fc-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7d7fc-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7d7fc-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7d7fc-119">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="7d7fc-119">The call timed out.</span></span>|  
|<span data-ttu-id="7d7fc-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7d7fc-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7d7fc-121">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="7d7fc-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7d7fc-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7d7fc-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7d7fc-123">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="7d7fc-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7d7fc-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7d7fc-124">E_FAIL</span></span>|<span data-ttu-id="7d7fc-125">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="7d7fc-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7d7fc-126">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="7d7fc-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7d7fc-127">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="7d7fc-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d7fc-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7d7fc-128">Remarks</span></span>  
 <span data-ttu-id="7d7fc-129">Bu uygulaması `VirtualProtect` HRESULT değerini, Win32 uygulaması başarılı olduğunu belirtmek için sıfır olmayan bir değer döndürür ve hata göstermek için sıfır değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="7d7fc-129">This implementation of `VirtualProtect` returns an HRESULT value, while the Win32 implementation returns a non-zero value to indicate success, and a zero value to indicate failure.</span></span> <span data-ttu-id="7d7fc-130">Daha fazla bilgi için Windows Platform belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="7d7fc-130">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d7fc-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7d7fc-131">Requirements</span></span>  
 <span data-ttu-id="7d7fc-132">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d7fc-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d7fc-133">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7d7fc-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7d7fc-134">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="7d7fc-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7d7fc-135">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d7fc-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d7fc-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7d7fc-136">See also</span></span>
- [<span data-ttu-id="7d7fc-137">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7d7fc-137">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)

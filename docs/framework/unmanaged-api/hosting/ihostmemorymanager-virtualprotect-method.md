---
title: "IHostMemoryManager::VirtualProtect Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMemoryManager.VirtualProtect
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMemoryManager::VirtualProtect
helpviewer_keywords:
- IHostMemoryManager::VirtualProtect method [.NET Framework hosting]
- VirtualProtect method [.NET Framework hosting]
ms.assetid: 13be0299-df0d-4951-aabf-0676a30b385f
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8f8d363054ab4728ae031ccea44eb8eb853354ef
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ihostmemorymanagervirtualprotect-method"></a><span data-ttu-id="9146d-102">IHostMemoryManager::VirtualProtect Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9146d-102">IHostMemoryManager::VirtualProtect Method</span></span>
<span data-ttu-id="9146d-103">Karşılık gelen Win32 işlevi için mantıksal bir kapsayıcı görevi görür.</span><span class="sxs-lookup"><span data-stu-id="9146d-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="9146d-104">Win32 uygulaması `VirtualProtect` bir bölge koruma çağırma işleminin sanal adres alanındaki taahhüt sayfaların değiştirir.</span><span class="sxs-lookup"><span data-stu-id="9146d-104">The Win32 implementation of `VirtualProtect` changes the protection on a region of committed pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9146d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9146d-105">Syntax</span></span>  
  
```  
HRESULT VirtualProtect (  
    [in]  void*   lpAddress,  
    [in]  SIZE_T  dwSize,  
    [in]  DWORD   flNewProtect,  
    [out] DWORD*  pflOldProtect  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9146d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9146d-106">Parameters</span></span>  
 `lpAddress`  
 <span data-ttu-id="9146d-107">[in] Değiştirilecek koruma niteliklerini olan sanal bellek taban adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9146d-107">[in] A pointer to the base address of the virtual memory whose protection attributes are to be changed.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="9146d-108">[in] Değiştirilecek bellek sayfalarının alanının bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="9146d-108">[in] The size, in bytes, of the region of memory pages to be changed.</span></span>  
  
 `flNewProtect`  
 <span data-ttu-id="9146d-109">[in] Bellek koruması uygulamak için türü.</span><span class="sxs-lookup"><span data-stu-id="9146d-109">[in] The type of memory protection to apply.</span></span>  
  
 `pflOldProtect`  
 <span data-ttu-id="9146d-110">[out] Önceki bellek koruma değeri için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9146d-110">[out] A pointer to the previous memory protection value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9146d-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9146d-111">Return Value</span></span>  
  
|<span data-ttu-id="9146d-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9146d-112">HRESULT</span></span>|<span data-ttu-id="9146d-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9146d-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9146d-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="9146d-114">S_OK</span></span>|<span data-ttu-id="9146d-115">`VirtualProtect`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="9146d-115">`VirtualProtect` returned successfully.</span></span>|  
|<span data-ttu-id="9146d-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9146d-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9146d-117">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="9146d-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9146d-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9146d-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9146d-119">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="9146d-119">The call timed out.</span></span>|  
|<span data-ttu-id="9146d-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9146d-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9146d-121">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="9146d-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9146d-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9146d-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9146d-123">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="9146d-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9146d-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9146d-124">E_FAIL</span></span>|<span data-ttu-id="9146d-125">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="9146d-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9146d-126">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="9146d-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9146d-127">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="9146d-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9146d-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9146d-128">Remarks</span></span>  
 <span data-ttu-id="9146d-129">Bu uygulaması, `VirtualProtect` Win32 uygulaması başarılı olduğunu belirtmek için sıfır olmayan bir değer döndürür sırada bir HRESULT değeri ve hatayı belirtmek için sıfır değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="9146d-129">This implementation of `VirtualProtect` returns an HRESULT value, while the Win32 implementation returns a non-zero value to indicate success, and a zero value to indicate failure.</span></span> <span data-ttu-id="9146d-130">Daha fazla bilgi için Windows platformu belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="9146d-130">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9146d-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9146d-131">Requirements</span></span>  
 <span data-ttu-id="9146d-132">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9146d-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9146d-133">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9146d-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9146d-134">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="9146d-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9146d-135">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9146d-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9146d-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9146d-136">See Also</span></span>  
 [<span data-ttu-id="9146d-137">Ihostmemorymanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="9146d-137">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)

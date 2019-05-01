---
title: IHostMemoryManager::VirtualFree Yöntemi
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.VirtualFree
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualFree
helpviewer_keywords:
- IHostMemoryManager::VirtualFree method [.NET Framework hosting]
- VirtualFree method [.NET Framework hosting]
ms.assetid: 1a436e89-eb28-4d15-bcf1-a072f86dbd99
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03cac2b8433d6491d1fa474a0d4064ef4e260d6e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993232"
---
# <a name="ihostmemorymanagervirtualfree-method"></a><span data-ttu-id="d90a1-102">IHostMemoryManager::VirtualFree Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d90a1-102">IHostMemoryManager::VirtualFree Method</span></span>
<span data-ttu-id="d90a1-103">Karşılık gelen Win32 işlevini için mantıksal bir sarmalayıcı olarak görev yapar.</span><span class="sxs-lookup"><span data-stu-id="d90a1-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="d90a1-104">Win32 uygulaması `VirtualFree` sürümleri, kaydeder, veya serbest bırakır ve çağıran işlemin sanal adres alanı içinde sayfalar bölgesini kaydeder.</span><span class="sxs-lookup"><span data-stu-id="d90a1-104">The Win32 implementation of `VirtualFree` releases, decommits, or releases and decommits a region of pages within the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d90a1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d90a1-105">Syntax</span></span>  
  
```  
HRESULT VirtualFree (  
    [in] LPVOID  lpAddress,  
    [in] SIZE_T  dwSize,  
    [in] DWORD   dwFreeType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d90a1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d90a1-106">Parameters</span></span>  
 `lpAddress`  
 <span data-ttu-id="d90a1-107">[in] Serbest bırakılacak sanal bellek sayfalarının taban adresi işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="d90a1-107">[in] A pointer to the base address of the virtual memory pages to be freed.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="d90a1-108">[in] Serbest bırakılacak alanının bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="d90a1-108">[in] The size, in bytes, of the region to be freed.</span></span>  
  
 `dwFreeType`  
 <span data-ttu-id="d90a1-109">[in] Serbest bırakma işlemi türü.</span><span class="sxs-lookup"><span data-stu-id="d90a1-109">[in] The type of freeing operation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d90a1-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d90a1-110">Return Value</span></span>  
  
|<span data-ttu-id="d90a1-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d90a1-111">HRESULT</span></span>|<span data-ttu-id="d90a1-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d90a1-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d90a1-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="d90a1-113">S_OK</span></span>|<span data-ttu-id="d90a1-114">`VirtualFree` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="d90a1-114">`VirtualFree` returned successfully.</span></span>|  
|<span data-ttu-id="d90a1-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d90a1-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d90a1-116">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="d90a1-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d90a1-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d90a1-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d90a1-118">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="d90a1-118">The call timed out.</span></span>|  
|<span data-ttu-id="d90a1-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d90a1-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d90a1-120">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="d90a1-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d90a1-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d90a1-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d90a1-122">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="d90a1-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d90a1-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d90a1-123">E_FAIL</span></span>|<span data-ttu-id="d90a1-124">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="d90a1-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d90a1-125">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="d90a1-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d90a1-126">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="d90a1-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d90a1-127">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="d90a1-127">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="d90a1-128">Ana bilgisayar üzerinden ayrılmamış belleği boşaltmak için girişimde bulunuldu.</span><span class="sxs-lookup"><span data-stu-id="d90a1-128">An attempt was made to free memory that was not allocated through the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d90a1-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d90a1-129">Remarks</span></span>  
 <span data-ttu-id="d90a1-130">`VirtualFree` ilişkili sanal bellek sayfalarının boşaltır `lpAddress` parametresi çağrısında aracılığıyla [Ihostmemorymanager::VirtualAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="d90a1-130">`VirtualFree` frees virtual memory pages associated with the `lpAddress` parameter through an earlier call to the [IHostMemoryManager::VirtualAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md) function.</span></span> <span data-ttu-id="d90a1-131">Ana bilgisayar üzerinden ayrılmamış belleği boşaltmak için deneme HOST_E_INVALIDOPERATION döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="d90a1-131">Attempts to free memory that was not allocated through the host should return HOST_E_INVALIDOPERATION.</span></span>  
  
 <span data-ttu-id="d90a1-132">Win32 uygulaması için aynı semantiği `VirtualFree`.</span><span class="sxs-lookup"><span data-stu-id="d90a1-132">The semantics are identical to those of the Win32 implementation of `VirtualFree`.</span></span> <span data-ttu-id="d90a1-133">Daha fazla bilgi için Windows Platform belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="d90a1-133">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d90a1-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d90a1-134">Requirements</span></span>  
 <span data-ttu-id="d90a1-135">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d90a1-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d90a1-136">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d90a1-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d90a1-137">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="d90a1-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d90a1-138">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d90a1-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d90a1-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d90a1-139">See also</span></span>

- [<span data-ttu-id="d90a1-140">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d90a1-140">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="d90a1-141">IHostMalloc Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d90a1-141">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)

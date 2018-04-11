---
title: IHostMemoryManager::VirtualFree Yöntemi
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: reference
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
caps.latest.revision: 12
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 663c01d7e4b551ecf18bdd85a63aefc43f9750e2
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/10/2018
---
# <a name="ihostmemorymanagervirtualfree-method"></a><span data-ttu-id="8b2c0-102">IHostMemoryManager::VirtualFree Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8b2c0-102">IHostMemoryManager::VirtualFree Method</span></span>
<span data-ttu-id="8b2c0-103">Karşılık gelen Win32 işlevi için mantıksal bir kapsayıcı görevi görür.</span><span class="sxs-lookup"><span data-stu-id="8b2c0-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="8b2c0-104">Win32 uygulaması `VirtualFree` serbest, decommits, veya serbest bırakır ve çağırma işleminin sanal adres alanı içinde sayfalar bölgesi decommits.</span><span class="sxs-lookup"><span data-stu-id="8b2c0-104">The Win32 implementation of `VirtualFree` releases, decommits, or releases and decommits a region of pages within the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b2c0-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8b2c0-105">Syntax</span></span>  
  
```  
HRESULT VirtualFree (  
    [in] LPVOID  lpAddress,  
    [in] SIZE_T  dwSize,  
    [in] DWORD   dwFreeType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8b2c0-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8b2c0-106">Parameters</span></span>  
 `lpAddress`  
 <span data-ttu-id="8b2c0-107">[in] Sanal bellek sayfalarının boşaltılması için taban adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8b2c0-107">[in] A pointer to the base address of the virtual memory pages to be freed.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="8b2c0-108">[in] Boşaltılacak alanının bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="8b2c0-108">[in] The size, in bytes, of the region to be freed.</span></span>  
  
 `dwFreeType`  
 <span data-ttu-id="8b2c0-109">[in] İşlemi serbest bırakma türü.</span><span class="sxs-lookup"><span data-stu-id="8b2c0-109">[in] The type of freeing operation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8b2c0-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8b2c0-110">Return Value</span></span>  
  
|<span data-ttu-id="8b2c0-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8b2c0-111">HRESULT</span></span>|<span data-ttu-id="8b2c0-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8b2c0-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8b2c0-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="8b2c0-113">S_OK</span></span>|<span data-ttu-id="8b2c0-114">`VirtualFree` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="8b2c0-114">`VirtualFree` returned successfully.</span></span>|  
|<span data-ttu-id="8b2c0-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8b2c0-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8b2c0-116">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="8b2c0-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8b2c0-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8b2c0-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8b2c0-118">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="8b2c0-118">The call timed out.</span></span>|  
|<span data-ttu-id="8b2c0-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8b2c0-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8b2c0-120">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="8b2c0-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8b2c0-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8b2c0-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8b2c0-122">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="8b2c0-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8b2c0-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8b2c0-123">E_FAIL</span></span>|<span data-ttu-id="8b2c0-124">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="8b2c0-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8b2c0-125">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="8b2c0-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8b2c0-126">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="8b2c0-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8b2c0-127">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="8b2c0-127">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="8b2c0-128">Ana bilgisayar üzerinden ayrılmamış belleği boşaltmak için girişimde bulunuldu.</span><span class="sxs-lookup"><span data-stu-id="8b2c0-128">An attempt was made to free memory that was not allocated through the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8b2c0-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8b2c0-129">Remarks</span></span>  
 <span data-ttu-id="8b2c0-130">`VirtualFree` ilişkili sanal bellek sayfalarını boşaltır `lpAddress` önceki bir çağrı aracılığıyla parametresini [Ihostmemorymanager::VirtualAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="8b2c0-130">`VirtualFree` frees virtual memory pages associated with the `lpAddress` parameter through an earlier call to the [IHostMemoryManager::VirtualAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md) function.</span></span> <span data-ttu-id="8b2c0-131">Ana bilgisayar üzerinden ayrılmamış belleği serbest girişimlerini HOST_E_INVALIDOPERATION döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="8b2c0-131">Attempts to free memory that was not allocated through the host should return HOST_E_INVALIDOPERATION.</span></span>  
  
 <span data-ttu-id="8b2c0-132">Semantiğini olanlar Win32 uygulaması aynı `VirtualFree`.</span><span class="sxs-lookup"><span data-stu-id="8b2c0-132">The semantics are identical to those of the Win32 implementation of `VirtualFree`.</span></span> <span data-ttu-id="8b2c0-133">Daha fazla bilgi için Windows platformu belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="8b2c0-133">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b2c0-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8b2c0-134">Requirements</span></span>  
 <span data-ttu-id="8b2c0-135">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b2c0-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b2c0-136">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8b2c0-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8b2c0-137">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="8b2c0-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8b2c0-138">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b2c0-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b2c0-139">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8b2c0-139">See Also</span></span>  
 [<span data-ttu-id="8b2c0-140">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8b2c0-140">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="8b2c0-141">IHostMalloc Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8b2c0-141">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)

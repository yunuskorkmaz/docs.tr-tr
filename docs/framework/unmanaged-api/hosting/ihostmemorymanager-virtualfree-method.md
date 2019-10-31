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
ms.openlocfilehash: b53c0bb38922ae8de048c131807eb32f97423d6c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128586"
---
# <a name="ihostmemorymanagervirtualfree-method"></a><span data-ttu-id="0ceba-102">IHostMemoryManager::VirtualFree Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0ceba-102">IHostMemoryManager::VirtualFree Method</span></span>
<span data-ttu-id="0ceba-103">Karşılık gelen Win32 işlevi için bir mantıksal sarmalayıcı görevi görür.</span><span class="sxs-lookup"><span data-stu-id="0ceba-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="0ceba-104">`VirtualFree` Win32 uygulamasının, çağıran işlemin sanal adres alanı içindeki bir sayfa bölgesini yayınlar, serbest bırakır veya yayınlar ve kaldırır.</span><span class="sxs-lookup"><span data-stu-id="0ceba-104">The Win32 implementation of `VirtualFree` releases, decommits, or releases and decommits a region of pages within the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ceba-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0ceba-105">Syntax</span></span>  
  
```cpp  
HRESULT VirtualFree (  
    [in] LPVOID  lpAddress,  
    [in] SIZE_T  dwSize,  
    [in] DWORD   dwFreeType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0ceba-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0ceba-106">Parameters</span></span>  
 `lpAddress`  
 <span data-ttu-id="0ceba-107">'ndaki Boşaltılacak sanal bellek sayfalarının temel adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0ceba-107">[in] A pointer to the base address of the virtual memory pages to be freed.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="0ceba-108">'ndaki Boşaltılacak bölgenin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="0ceba-108">[in] The size, in bytes, of the region to be freed.</span></span>  
  
 `dwFreeType`  
 <span data-ttu-id="0ceba-109">'ndaki Boşaltma işleminin türü.</span><span class="sxs-lookup"><span data-stu-id="0ceba-109">[in] The type of freeing operation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0ceba-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0ceba-110">Return Value</span></span>  
  
|<span data-ttu-id="0ceba-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0ceba-111">HRESULT</span></span>|<span data-ttu-id="0ceba-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0ceba-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0ceba-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="0ceba-113">S_OK</span></span>|<span data-ttu-id="0ceba-114">`VirtualFree` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="0ceba-114">`VirtualFree` returned successfully.</span></span>|  
|<span data-ttu-id="0ceba-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0ceba-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0ceba-116">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="0ceba-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0ceba-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0ceba-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0ceba-118">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="0ceba-118">The call timed out.</span></span>|  
|<span data-ttu-id="0ceba-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0ceba-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0ceba-120">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="0ceba-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0ceba-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0ceba-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0ceba-122">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="0ceba-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0ceba-123">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="0ceba-123">E_FAIL</span></span>|<span data-ttu-id="0ceba-124">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="0ceba-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0ceba-125">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="0ceba-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0ceba-126">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="0ceba-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0ceba-127">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="0ceba-127">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="0ceba-128">Ana bilgisayar aracılığıyla ayrılmamış belleği serbest bırakma girişiminde bulunuldu.</span><span class="sxs-lookup"><span data-stu-id="0ceba-128">An attempt was made to free memory that was not allocated through the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ceba-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0ceba-129">Remarks</span></span>  
 <span data-ttu-id="0ceba-130">`VirtualFree`, [IHostMemoryManager:: VirtualAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md) işlevine daha önceki bir çağrı yoluyla `lpAddress` parametresiyle ilişkili sanal bellek sayfalarını serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="0ceba-130">`VirtualFree` frees virtual memory pages associated with the `lpAddress` parameter through an earlier call to the [IHostMemoryManager::VirtualAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md) function.</span></span> <span data-ttu-id="0ceba-131">Ana bilgisayar üzerinden ayrılmamış belleği serbest bırakma denemeleri HOST_E_INVALIDOPERATION döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="0ceba-131">Attempts to free memory that was not allocated through the host should return HOST_E_INVALIDOPERATION.</span></span>  
  
 <span data-ttu-id="0ceba-132">Semantiği `VirtualFree`Win32 uygulamasıyla aynıdır.</span><span class="sxs-lookup"><span data-stu-id="0ceba-132">The semantics are identical to those of the Win32 implementation of `VirtualFree`.</span></span> <span data-ttu-id="0ceba-133">Daha fazla bilgi için bkz. Windows platformu belgeleri.</span><span class="sxs-lookup"><span data-stu-id="0ceba-133">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ceba-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0ceba-134">Requirements</span></span>  
 <span data-ttu-id="0ceba-135">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ceba-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ceba-136">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0ceba-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0ceba-137">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="0ceba-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0ceba-138">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ceba-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ceba-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ceba-139">See also</span></span>

- [<span data-ttu-id="0ceba-140">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0ceba-140">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="0ceba-141">IHostMalloc Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0ceba-141">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)

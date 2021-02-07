---
description: 'Şu konuda daha fazla bilgi edinin: IHostMemoryManager:: VirtualFree yöntemi'
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
ms.openlocfilehash: 987661ce1b7bfd08f757f53082313b8eb60ff282
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707550"
---
# <a name="ihostmemorymanagervirtualfree-method"></a><span data-ttu-id="cadde-103">IHostMemoryManager::VirtualFree Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cadde-103">IHostMemoryManager::VirtualFree Method</span></span>

<span data-ttu-id="cadde-104">Karşılık gelen Win32 işlevi için bir mantıksal sarmalayıcı görevi görür.</span><span class="sxs-lookup"><span data-stu-id="cadde-104">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="cadde-105">Uygulamaları `VirtualFree` yayınlar, serbest bırakır veya yayınlar, çağıran işlemin sanal adres alanındaki bir sayfa bölgesini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="cadde-105">The Win32 implementation of `VirtualFree` releases, decommits, or releases and decommits a region of pages within the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cadde-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cadde-106">Syntax</span></span>  
  
```cpp  
HRESULT VirtualFree (  
    [in] LPVOID  lpAddress,  
    [in] SIZE_T  dwSize,  
    [in] DWORD   dwFreeType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cadde-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cadde-107">Parameters</span></span>  

 `lpAddress`  
 <span data-ttu-id="cadde-108">'ndaki Boşaltılacak sanal bellek sayfalarının temel adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cadde-108">[in] A pointer to the base address of the virtual memory pages to be freed.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="cadde-109">'ndaki Boşaltılacak bölgenin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="cadde-109">[in] The size, in bytes, of the region to be freed.</span></span>  
  
 `dwFreeType`  
 <span data-ttu-id="cadde-110">'ndaki Boşaltma işleminin türü.</span><span class="sxs-lookup"><span data-stu-id="cadde-110">[in] The type of freeing operation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cadde-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="cadde-111">Return Value</span></span>  
  
|<span data-ttu-id="cadde-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cadde-112">HRESULT</span></span>|<span data-ttu-id="cadde-113">Description</span><span class="sxs-lookup"><span data-stu-id="cadde-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cadde-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="cadde-114">S_OK</span></span>|<span data-ttu-id="cadde-115">`VirtualFree` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="cadde-115">`VirtualFree` returned successfully.</span></span>|  
|<span data-ttu-id="cadde-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cadde-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cadde-117">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="cadde-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cadde-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cadde-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cadde-119">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="cadde-119">The call timed out.</span></span>|  
|<span data-ttu-id="cadde-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cadde-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cadde-121">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="cadde-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cadde-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cadde-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cadde-123">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="cadde-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="cadde-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cadde-124">E_FAIL</span></span>|<span data-ttu-id="cadde-125">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="cadde-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cadde-126">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="cadde-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cadde-127">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="cadde-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="cadde-128">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="cadde-128">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="cadde-129">Ana bilgisayar aracılığıyla ayrılmamış belleği serbest bırakma girişiminde bulunuldu.</span><span class="sxs-lookup"><span data-stu-id="cadde-129">An attempt was made to free memory that was not allocated through the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cadde-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cadde-130">Remarks</span></span>  

 <span data-ttu-id="cadde-131">`VirtualFree``lpAddress` [IHostMemoryManager:: VirtualAlloc](ihostmemorymanager-virtualalloc-method.md) işlevine daha önceki bir çağrı yoluyla parametresiyle ilişkili sanal bellek sayfalarını boşaltır.</span><span class="sxs-lookup"><span data-stu-id="cadde-131">`VirtualFree` frees virtual memory pages associated with the `lpAddress` parameter through an earlier call to the [IHostMemoryManager::VirtualAlloc](ihostmemorymanager-virtualalloc-method.md) function.</span></span> <span data-ttu-id="cadde-132">Ana bilgisayar üzerinden ayrılmamış belleği serbest bırakma denemeleri HOST_E_INVALIDOPERATION döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="cadde-132">Attempts to free memory that was not allocated through the host should return HOST_E_INVALIDOPERATION.</span></span>  
  
 <span data-ttu-id="cadde-133">Semantiği, Win32 uygulamasıyla aynıdır `VirtualFree` .</span><span class="sxs-lookup"><span data-stu-id="cadde-133">The semantics are identical to those of the Win32 implementation of `VirtualFree`.</span></span> <span data-ttu-id="cadde-134">Daha fazla bilgi için bkz. Windows platformu belgeleri.</span><span class="sxs-lookup"><span data-stu-id="cadde-134">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cadde-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cadde-135">Requirements</span></span>  

 <span data-ttu-id="cadde-136">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cadde-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cadde-137">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="cadde-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cadde-138">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="cadde-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cadde-139">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cadde-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cadde-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cadde-140">See also</span></span>

- [<span data-ttu-id="cadde-141">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cadde-141">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="cadde-142">IHostMalloc Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cadde-142">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)

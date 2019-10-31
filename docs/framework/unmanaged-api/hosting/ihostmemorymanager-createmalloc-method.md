---
title: IHostMemoryManager::CreateMAlloc Yöntemi
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.CreateMAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::CreateMAlloc
helpviewer_keywords:
- CreateAlloc method [.NET Framework hosting]
- IHostMemoryManager::CreateMAlloc method [.NET Framework hosting]
ms.assetid: 9ee6e052-bef7-4350-9e4f-edfffd99ad6f
topic_type:
- apiref
ms.openlocfilehash: 8bcb01f4a19e6043bd59fe6f1565cdf35ed1f77c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136719"
---
# <a name="ihostmemorymanagercreatemalloc-method"></a><span data-ttu-id="f2dcd-102">IHostMemoryManager::CreateMAlloc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f2dcd-102">IHostMemoryManager::CreateMAlloc Method</span></span>
<span data-ttu-id="f2dcd-103">Ana bilgisayar tarafından oluşturulan bir yığından gelen ayırma isteklerini oluşturmak için kullanılan bir [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) örneğine yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="f2dcd-103">Gets an interface pointer to an [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance that is used to make allocation requests from a heap created by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2dcd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f2dcd-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateMalloc (  
    [in]  DWORD         dwMallocType,  
    [out] IHostMalloc **ppMalloc  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f2dcd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f2dcd-105">Parameters</span></span>  
 `dwMallocType`  
 <span data-ttu-id="f2dcd-106">'ndaki Ayrılmakta olan belleğin özelliklerini belirten [MALLOC_TYPE](../../../../docs/framework/unmanaged-api/hosting/malloc-type-enumeration.md) Flags birleşimi.</span><span class="sxs-lookup"><span data-stu-id="f2dcd-106">[in] A combination of [MALLOC_TYPE](../../../../docs/framework/unmanaged-api/hosting/malloc-type-enumeration.md) flags that specifies the characteristics of the memory that is being allocated.</span></span>  
  
 `ppMAlloc`  
 <span data-ttu-id="f2dcd-107">dışı Konak tarafından sağlanmış bir `IHostMAlloc` örneğinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f2dcd-107">[out] A pointer to the address of an `IHostMAlloc` instance provided by the host.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f2dcd-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f2dcd-108">Return Value</span></span>  
  
|<span data-ttu-id="f2dcd-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f2dcd-109">HRESULT</span></span>|<span data-ttu-id="f2dcd-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f2dcd-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f2dcd-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="f2dcd-111">S_OK</span></span>|<span data-ttu-id="f2dcd-112">`CreateMAlloc` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="f2dcd-112">`CreateMAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="f2dcd-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f2dcd-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f2dcd-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="f2dcd-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f2dcd-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f2dcd-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f2dcd-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="f2dcd-116">The call timed out.</span></span>|  
|<span data-ttu-id="f2dcd-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f2dcd-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f2dcd-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="f2dcd-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f2dcd-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f2dcd-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f2dcd-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="f2dcd-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f2dcd-121">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="f2dcd-121">E_FAIL</span></span>|<span data-ttu-id="f2dcd-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="f2dcd-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f2dcd-123">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="f2dcd-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f2dcd-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="f2dcd-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f2dcd-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="f2dcd-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="f2dcd-126">Ayırma isteğini tamamlamaya yetecek kadar fiziksel bellek yoktu.</span><span class="sxs-lookup"><span data-stu-id="f2dcd-126">Not enough physical memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f2dcd-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f2dcd-127">Remarks</span></span>  
 <span data-ttu-id="f2dcd-128">`CreateMAlloc`, CLR 'nin standart Win32 işlevlerini kullanmak yerine ana bilgisayar aracılığıyla ayırma istekleri yapmasına izin veren bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="f2dcd-128">`CreateMAlloc` returns an object that allows the CLR to make allocation requests through the host instead of using the standard Win32 functions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2dcd-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f2dcd-129">Requirements</span></span>  
 <span data-ttu-id="f2dcd-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2dcd-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2dcd-131">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f2dcd-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f2dcd-132">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="f2dcd-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f2dcd-133">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2dcd-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2dcd-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f2dcd-134">See also</span></span>

- [<span data-ttu-id="f2dcd-135">IHostMalloc Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f2dcd-135">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
- [<span data-ttu-id="f2dcd-136">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f2dcd-136">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)

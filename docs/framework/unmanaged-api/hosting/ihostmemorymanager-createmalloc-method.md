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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 194e9b73610ccb7282babf266eea2968a4f035ac
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59179133"
---
# <a name="ihostmemorymanagercreatemalloc-method"></a><span data-ttu-id="320e1-102">IHostMemoryManager::CreateMAlloc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="320e1-102">IHostMemoryManager::CreateMAlloc Method</span></span>
<span data-ttu-id="320e1-103">Bir arabirim işaretçisi alır bir [Ihostmalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) ana bilgisayar tarafından oluşturulan bir yığın ayırma isteklerini yapmak için kullanılan bir örnek.</span><span class="sxs-lookup"><span data-stu-id="320e1-103">Gets an interface pointer to an [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance that is used to make allocation requests from a heap created by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="320e1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="320e1-104">Syntax</span></span>  
  
```  
HRESULT CreateMalloc (  
    [in]  DWORD         dwMallocType,  
    [out] IHostMalloc **ppMalloc  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="320e1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="320e1-105">Parameters</span></span>  
 `dwMallocType`  
 <span data-ttu-id="320e1-106">[in] Bir birleşimi [MALLOC_TYPE](../../../../docs/framework/unmanaged-api/hosting/malloc-type-enumeration.md) ayrılan bellek özelliklerini belirten bayrak.</span><span class="sxs-lookup"><span data-stu-id="320e1-106">[in] A combination of [MALLOC_TYPE](../../../../docs/framework/unmanaged-api/hosting/malloc-type-enumeration.md) flags that specifies the characteristics of the memory that is being allocated.</span></span>  
  
 `ppMAlloc`  
 <span data-ttu-id="320e1-107">[out] Adresine bir işaretçi bir `IHostMAlloc` ana bilgisayar tarafından sağlanan örneği.</span><span class="sxs-lookup"><span data-stu-id="320e1-107">[out] A pointer to the address of an `IHostMAlloc` instance provided by the host.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="320e1-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="320e1-108">Return Value</span></span>  
  
|<span data-ttu-id="320e1-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="320e1-109">HRESULT</span></span>|<span data-ttu-id="320e1-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="320e1-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="320e1-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="320e1-111">S_OK</span></span>|`CreateMAlloc` <span data-ttu-id="320e1-112">başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="320e1-112">returned successfully.</span></span>|  
|<span data-ttu-id="320e1-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="320e1-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="320e1-114">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="320e1-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="320e1-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="320e1-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="320e1-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="320e1-116">The call timed out.</span></span>|  
|<span data-ttu-id="320e1-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="320e1-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="320e1-118">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="320e1-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="320e1-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="320e1-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="320e1-120">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="320e1-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="320e1-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="320e1-121">E_FAIL</span></span>|<span data-ttu-id="320e1-122">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="320e1-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="320e1-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="320e1-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="320e1-124">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="320e1-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="320e1-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="320e1-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="320e1-126">Yeterli fiziksel bellek ayırma isteğini tamamlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="320e1-126">Not enough physical memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="320e1-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="320e1-127">Remarks</span></span>  
 `CreateMAlloc` <span data-ttu-id="320e1-128">standart Win32 işlevlerini kullanmak yerine ana bilgisayar üzerinden ayırma isteğinde bulunmak CLR izin veren bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="320e1-128">returns an object that allows the CLR to make allocation requests through the host instead of using the standard Win32 functions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="320e1-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="320e1-129">Requirements</span></span>  
 <span data-ttu-id="320e1-130">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="320e1-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="320e1-131">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="320e1-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="320e1-132">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="320e1-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="320e1-133">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="320e1-133">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="320e1-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="320e1-134">See also</span></span>

- [<span data-ttu-id="320e1-135">IHostMalloc Arabirimi</span><span class="sxs-lookup"><span data-stu-id="320e1-135">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
- [<span data-ttu-id="320e1-136">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="320e1-136">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)

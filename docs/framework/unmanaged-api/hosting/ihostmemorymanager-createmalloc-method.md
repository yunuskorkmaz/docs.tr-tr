---
description: 'Şu konuda daha fazla bilgi edinin: IHostMemoryManager:: Createmayırma yöntemi'
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
ms.openlocfilehash: de73490a5c8b4e1672beb4750bcc617c2371f07b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707896"
---
# <a name="ihostmemorymanagercreatemalloc-method"></a><span data-ttu-id="9aee9-103">IHostMemoryManager::CreateMAlloc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9aee9-103">IHostMemoryManager::CreateMAlloc Method</span></span>

<span data-ttu-id="9aee9-104">Ana bilgisayar tarafından oluşturulan bir yığından gelen ayırma isteklerini oluşturmak için kullanılan bir [IHostMAlloc](ihostmalloc-interface.md) örneğine yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="9aee9-104">Gets an interface pointer to an [IHostMAlloc](ihostmalloc-interface.md) instance that is used to make allocation requests from a heap created by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9aee9-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9aee9-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateMalloc (  
    [in]  DWORD         dwMallocType,  
    [out] IHostMalloc **ppMalloc  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9aee9-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9aee9-106">Parameters</span></span>  

 `dwMallocType`  
 <span data-ttu-id="9aee9-107">'ndaki Ayrılmakta olan belleğin özelliklerini belirten [MALLOC_TYPE](malloc-type-enumeration.md) bayraklarının birleşimi.</span><span class="sxs-lookup"><span data-stu-id="9aee9-107">[in] A combination of [MALLOC_TYPE](malloc-type-enumeration.md) flags that specifies the characteristics of the memory that is being allocated.</span></span>  
  
 `ppMAlloc`  
 <span data-ttu-id="9aee9-108">dışı Konak tarafından sağlanmış bir örneğin adresine yönelik bir işaretçi `IHostMAlloc` .</span><span class="sxs-lookup"><span data-stu-id="9aee9-108">[out] A pointer to the address of an `IHostMAlloc` instance provided by the host.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9aee9-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9aee9-109">Return Value</span></span>  
  
|<span data-ttu-id="9aee9-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9aee9-110">HRESULT</span></span>|<span data-ttu-id="9aee9-111">Description</span><span class="sxs-lookup"><span data-stu-id="9aee9-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9aee9-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="9aee9-112">S_OK</span></span>|<span data-ttu-id="9aee9-113">`CreateMAlloc` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="9aee9-113">`CreateMAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="9aee9-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9aee9-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9aee9-115">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="9aee9-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9aee9-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9aee9-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9aee9-117">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="9aee9-117">The call timed out.</span></span>|  
|<span data-ttu-id="9aee9-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9aee9-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9aee9-119">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="9aee9-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9aee9-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9aee9-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9aee9-121">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="9aee9-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9aee9-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9aee9-122">E_FAIL</span></span>|<span data-ttu-id="9aee9-123">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="9aee9-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9aee9-124">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="9aee9-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9aee9-125">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="9aee9-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9aee9-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="9aee9-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="9aee9-127">Ayırma isteğini tamamlamaya yetecek kadar fiziksel bellek yoktu.</span><span class="sxs-lookup"><span data-stu-id="9aee9-127">Not enough physical memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9aee9-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9aee9-128">Remarks</span></span>  

 <span data-ttu-id="9aee9-129">`CreateMAlloc` CLR 'nin standart Win32 işlevlerini kullanmak yerine ana bilgisayar aracılığıyla ayırma istekleri yapmasına izin veren bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="9aee9-129">`CreateMAlloc` returns an object that allows the CLR to make allocation requests through the host instead of using the standard Win32 functions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9aee9-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9aee9-130">Requirements</span></span>  

 <span data-ttu-id="9aee9-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9aee9-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9aee9-132">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9aee9-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9aee9-133">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="9aee9-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9aee9-134">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9aee9-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9aee9-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9aee9-135">See also</span></span>

- [<span data-ttu-id="9aee9-136">IHostMalloc Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9aee9-136">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)
- [<span data-ttu-id="9aee9-137">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9aee9-137">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)

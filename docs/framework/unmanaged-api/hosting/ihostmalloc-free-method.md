---
title: IHostMAlloc::Free Yöntemi
ms.date: 03/30/2017
api_name:
- IHostMAlloc.Free
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc::Free
helpviewer_keywords:
- IHostMAlloc::Free method [.NET Framework hosting]
- Free method, IHostMAlloc interface [.NET Framework hosting]
ms.assetid: c89abf5b-1120-4437-8b57-4a99fb3ae7f9
topic_type:
- apiref
ms.openlocfilehash: 1dd5ed4c556a5a4d4425a9c0730cebf22ff1785b
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804615"
---
# <a name="ihostmallocfree-method"></a><span data-ttu-id="1b3ea-102">IHostMAlloc::Free Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1b3ea-102">IHostMAlloc::Free Method</span></span>
<span data-ttu-id="1b3ea-103">[Ayırma](ihostmalloc-alloc-method.md) işlevi kullanılarak ayrılan belleği serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="1b3ea-103">Frees memory that was allocated by using the [Alloc](ihostmalloc-alloc-method.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b3ea-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="1b3ea-104">Syntax</span></span>  
  
```cpp  
HRESULT Free (  
    [in] void* pMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1b3ea-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1b3ea-105">Parameters</span></span>  
 `pMem`  
 <span data-ttu-id="1b3ea-106">'ndaki Boşaltılacak belleğin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="1b3ea-106">[in] A pointer to the memory to be freed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1b3ea-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1b3ea-107">Return Value</span></span>  
  
|<span data-ttu-id="1b3ea-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1b3ea-108">HRESULT</span></span>|<span data-ttu-id="1b3ea-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1b3ea-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1b3ea-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="1b3ea-110">S_OK</span></span>|<span data-ttu-id="1b3ea-111">`Free`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="1b3ea-111">`Free` returned successfully.</span></span>|  
|<span data-ttu-id="1b3ea-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1b3ea-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1b3ea-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="1b3ea-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1b3ea-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1b3ea-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1b3ea-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="1b3ea-115">The call timed out.</span></span>|  
|<span data-ttu-id="1b3ea-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1b3ea-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1b3ea-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="1b3ea-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1b3ea-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1b3ea-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1b3ea-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="1b3ea-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1b3ea-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1b3ea-120">E_FAIL</span></span>|<span data-ttu-id="1b3ea-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="1b3ea-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1b3ea-122">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="1b3ea-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1b3ea-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="1b3ea-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1b3ea-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="1b3ea-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="1b3ea-125">Ana bilgisayar aracılığıyla ayrılmamış belleği serbest bırakma girişiminde bulunuldu.</span><span class="sxs-lookup"><span data-stu-id="1b3ea-125">An attempt was made to free memory that was not allocated through the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b3ea-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1b3ea-126">Remarks</span></span>  
 <span data-ttu-id="1b3ea-127">Parametresi, `pMem` çağrısı kullanılarak ayrılmamış bir bellek bölgesine başvuruyorsa `Alloc` , ana bilgisayar HOST_E_INVALIDOPERATION döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="1b3ea-127">If the `pMem` parameter refers to a region of memory that was not allocated by using a call to `Alloc`, the host should return HOST_E_INVALIDOPERATION.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b3ea-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1b3ea-128">Requirements</span></span>  
 <span data-ttu-id="1b3ea-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b3ea-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b3ea-130">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1b3ea-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1b3ea-131">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="1b3ea-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1b3ea-132">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b3ea-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b3ea-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1b3ea-133">See also</span></span>

- [<span data-ttu-id="1b3ea-134">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1b3ea-134">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="1b3ea-135">IHostMalloc Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1b3ea-135">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)

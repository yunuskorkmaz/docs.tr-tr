---
title: IHostMemoryManager::VirtualQuery Yöntemi
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.VirtualQuery
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualQuery
helpviewer_keywords:
- IHostMemoryManager::VirtualQuery method [.NET Framework hosting]
- VirtualQuery method [.NET Framework hosting]
ms.assetid: 757af1e6-b9e8-49e7-b5db-342be3aa205f
topic_type:
- apiref
ms.openlocfilehash: 00ec0b92a9f7151ee9b831c85548c4f61d87af68
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73192029"
---
# <a name="ihostmemorymanagervirtualquery-method"></a><span data-ttu-id="17490-102">IHostMemoryManager::VirtualQuery Yöntemi</span><span class="sxs-lookup"><span data-stu-id="17490-102">IHostMemoryManager::VirtualQuery Method</span></span>
<span data-ttu-id="17490-103">Karşılık gelen Win32 işlevi için bir mantıksal sarmalayıcı görevi görür.</span><span class="sxs-lookup"><span data-stu-id="17490-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="17490-104">`VirtualQuery` Win32 uygulamasının, çağıran işlemin sanal adres alanındaki bir sayfa aralığı hakkında bilgi alır.</span><span class="sxs-lookup"><span data-stu-id="17490-104">The Win32 implementation of `VirtualQuery` retrieves information about a range of pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17490-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="17490-105">Syntax</span></span>  
  
```cpp  
HRESULT VirtualQuery (  
    [in]  void*    lpAddress,  
    [out] void*    lpBuffer,  
    [in]  SIZE_T   dwLength,  
    [out] SIZE_T*  pResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17490-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="17490-106">Parameters</span></span>  
 `lpAddress`  
 <span data-ttu-id="17490-107">'ndaki Sorgulanacak sanal bellekteki adrese yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="17490-107">[in] A pointer to the address in virtual memory to be queried.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="17490-108">dışı Belirtilen bellek bölgesi hakkında bilgi içeren bir yapıya yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="17490-108">[out] A pointer to a structure that contains information about the specified memory region.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="17490-109">'ndaki `lpBuffer` arabelleğe işaret eden arabelleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="17490-109">[in] The size, in bytes, of the buffer that `lpBuffer` points to.</span></span>  
  
 `pResult`  
 <span data-ttu-id="17490-110">dışı Bilgi arabelleğinin döndürdüğü bayt sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="17490-110">[out] A pointer to the number of bytes returned by the information buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="17490-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="17490-111">Return Value</span></span>  
  
|<span data-ttu-id="17490-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="17490-112">HRESULT</span></span>|<span data-ttu-id="17490-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="17490-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="17490-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="17490-114">S_OK</span></span>|<span data-ttu-id="17490-115">`VirtualQuery` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="17490-115">`VirtualQuery` returned successfully.</span></span>|  
|<span data-ttu-id="17490-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="17490-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="17490-117">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="17490-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="17490-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="17490-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="17490-119">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="17490-119">The call timed out.</span></span>|  
|<span data-ttu-id="17490-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="17490-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="17490-121">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="17490-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="17490-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="17490-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="17490-123">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="17490-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="17490-124">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="17490-124">E_FAIL</span></span>|<span data-ttu-id="17490-125">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="17490-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="17490-126">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="17490-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="17490-127">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="17490-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="17490-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="17490-128">Remarks</span></span>  
 <span data-ttu-id="17490-129">`VirtualQuery`, çağıran işlemin sanal adres alanındaki bir sayfa aralığı hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="17490-129">`VirtualQuery` provides information about a range of pages in the virtual address space of the calling process.</span></span> <span data-ttu-id="17490-130">Bu uygulama, `pResult` parametresinin değerini, bilgi arabelleğinde döndürülen bayt sayısına ayarlar ve bir HRESULT değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="17490-130">This implementation sets the value of the `pResult` parameter to the number of bytes returned in the information buffer, and returns an HRESULT value.</span></span> <span data-ttu-id="17490-131">Win32 `VirtualQuery` işlevinde, dönüş değeri arabellek boyutudur.</span><span class="sxs-lookup"><span data-stu-id="17490-131">In the Win32 `VirtualQuery` function, the return value is the buffer size.</span></span> <span data-ttu-id="17490-132">Daha fazla bilgi için bkz. Windows platformu belgeleri.</span><span class="sxs-lookup"><span data-stu-id="17490-132">For more information, see the Windows Platform documentation.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="17490-133">İşletim sisteminin `VirtualQuery` uygulanması kilitlenmez ve Kullanıcı kodunda askıya alınmış rastgele iş parçacıkları ile tamamlanmayı çalıştırabilir.</span><span class="sxs-lookup"><span data-stu-id="17490-133">The operating system's implementation of `VirtualQuery` does not incur deadlock and can run to completion with random threads suspended in user code.</span></span> <span data-ttu-id="17490-134">Bu yöntemin barındırılan bir sürümünü uygularken harika bir uyarı kullanın.</span><span class="sxs-lookup"><span data-stu-id="17490-134">Use great caution when implementing a hosted version of this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17490-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="17490-135">Requirements</span></span>  
 <span data-ttu-id="17490-136">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17490-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17490-137">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="17490-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="17490-138">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="17490-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="17490-139">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17490-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17490-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="17490-140">See also</span></span>

- [<span data-ttu-id="17490-141">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="17490-141">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)

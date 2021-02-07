---
description: 'Şu konuda daha fazla bilgi edinin: IHostMemoryManager:: VirtualQuery Yöntemi'
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
ms.openlocfilehash: 8518ef71ad7d493fa04d4e2321f1f90ef8ecd18d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707559"
---
# <a name="ihostmemorymanagervirtualquery-method"></a><span data-ttu-id="fffe3-103">IHostMemoryManager::VirtualQuery Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fffe3-103">IHostMemoryManager::VirtualQuery Method</span></span>

<span data-ttu-id="fffe3-104">Karşılık gelen Win32 işlevi için bir mantıksal sarmalayıcı görevi görür.</span><span class="sxs-lookup"><span data-stu-id="fffe3-104">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="fffe3-105">Win32 uygulamasının, `VirtualQuery` çağırma işleminin sanal adres alanındaki bir sayfa aralığı hakkında bilgi alır.</span><span class="sxs-lookup"><span data-stu-id="fffe3-105">The Win32 implementation of `VirtualQuery` retrieves information about a range of pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fffe3-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fffe3-106">Syntax</span></span>  
  
```cpp  
HRESULT VirtualQuery (  
    [in]  void*    lpAddress,  
    [out] void*    lpBuffer,  
    [in]  SIZE_T   dwLength,  
    [out] SIZE_T*  pResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fffe3-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fffe3-107">Parameters</span></span>  

 `lpAddress`  
 <span data-ttu-id="fffe3-108">'ndaki Sorgulanacak sanal bellekteki adrese yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fffe3-108">[in] A pointer to the address in virtual memory to be queried.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="fffe3-109">dışı Belirtilen bellek bölgesi hakkında bilgi içeren bir yapıya yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fffe3-109">[out] A pointer to a structure that contains information about the specified memory region.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="fffe3-110">'ndaki ' I işaret eden arabelleğin bayt cinsinden boyutu `lpBuffer` .</span><span class="sxs-lookup"><span data-stu-id="fffe3-110">[in] The size, in bytes, of the buffer that `lpBuffer` points to.</span></span>  
  
 `pResult`  
 <span data-ttu-id="fffe3-111">dışı Bilgi arabelleğinin döndürdüğü bayt sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fffe3-111">[out] A pointer to the number of bytes returned by the information buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fffe3-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fffe3-112">Return Value</span></span>  
  
|<span data-ttu-id="fffe3-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fffe3-113">HRESULT</span></span>|<span data-ttu-id="fffe3-114">Description</span><span class="sxs-lookup"><span data-stu-id="fffe3-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fffe3-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="fffe3-115">S_OK</span></span>|<span data-ttu-id="fffe3-116">`VirtualQuery` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="fffe3-116">`VirtualQuery` returned successfully.</span></span>|  
|<span data-ttu-id="fffe3-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fffe3-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fffe3-118">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="fffe3-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fffe3-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fffe3-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fffe3-120">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="fffe3-120">The call timed out.</span></span>|  
|<span data-ttu-id="fffe3-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fffe3-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fffe3-122">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="fffe3-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fffe3-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fffe3-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fffe3-124">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="fffe3-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fffe3-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fffe3-125">E_FAIL</span></span>|<span data-ttu-id="fffe3-126">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="fffe3-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fffe3-127">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="fffe3-127">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fffe3-128">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="fffe3-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fffe3-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fffe3-129">Remarks</span></span>  

 <span data-ttu-id="fffe3-130">`VirtualQuery` çağıran işlemin sanal adres alanındaki bir sayfa aralığı hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="fffe3-130">`VirtualQuery` provides information about a range of pages in the virtual address space of the calling process.</span></span> <span data-ttu-id="fffe3-131">Bu uygulama, `pResult` parametrenin değerini bilgi arabelleğinde döndürülen bayt sayısına ayarlar ve bır HRESULT değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="fffe3-131">This implementation sets the value of the `pResult` parameter to the number of bytes returned in the information buffer, and returns an HRESULT value.</span></span> <span data-ttu-id="fffe3-132">Win32 `VirtualQuery` işlevinde, dönüş değeri arabellek boyutudur.</span><span class="sxs-lookup"><span data-stu-id="fffe3-132">In the Win32 `VirtualQuery` function, the return value is the buffer size.</span></span> <span data-ttu-id="fffe3-133">Daha fazla bilgi için bkz. Windows platformu belgeleri.</span><span class="sxs-lookup"><span data-stu-id="fffe3-133">For more information, see the Windows Platform documentation.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="fffe3-134">İşletim sisteminin uygulamasının uygulanması kilitlenme gerektirmez `VirtualQuery` ve Kullanıcı kodunda askıya alınmış rastgele iş parçacıkları ile tamamlanmayı çalıştırabilir.</span><span class="sxs-lookup"><span data-stu-id="fffe3-134">The operating system's implementation of `VirtualQuery` does not incur deadlock and can run to completion with random threads suspended in user code.</span></span> <span data-ttu-id="fffe3-135">Bu yöntemin barındırılan bir sürümünü uygularken harika bir uyarı kullanın.</span><span class="sxs-lookup"><span data-stu-id="fffe3-135">Use great caution when implementing a hosted version of this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fffe3-136">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fffe3-136">Requirements</span></span>  

 <span data-ttu-id="fffe3-137">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fffe3-137">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fffe3-138">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="fffe3-138">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fffe3-139">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="fffe3-139">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fffe3-140">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fffe3-140">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fffe3-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fffe3-141">See also</span></span>

- [<span data-ttu-id="fffe3-142">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fffe3-142">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)

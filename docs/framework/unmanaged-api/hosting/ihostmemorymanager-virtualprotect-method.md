---
title: IHostMemoryManager::VirtualProtect Yöntemi
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.VirtualProtect
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualProtect
helpviewer_keywords:
- IHostMemoryManager::VirtualProtect method [.NET Framework hosting]
- VirtualProtect method [.NET Framework hosting]
ms.assetid: 13be0299-df0d-4951-aabf-0676a30b385f
topic_type:
- apiref
ms.openlocfilehash: d39ad45e143026f40ffcf1339e923837f9e812c4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73195853"
---
# <a name="ihostmemorymanagervirtualprotect-method"></a><span data-ttu-id="1fc5c-102">IHostMemoryManager::VirtualProtect Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1fc5c-102">IHostMemoryManager::VirtualProtect Method</span></span>
<span data-ttu-id="1fc5c-103">Karşılık gelen Win32 işlevi için bir mantıksal sarmalayıcı görevi görür.</span><span class="sxs-lookup"><span data-stu-id="1fc5c-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="1fc5c-104">`VirtualProtect` Win32 uygulamasının, çağıran işlemin sanal adres alanındaki bir kaydedilmiş sayfalar bölgesindeki korumayı değiştirir.</span><span class="sxs-lookup"><span data-stu-id="1fc5c-104">The Win32 implementation of `VirtualProtect` changes the protection on a region of committed pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fc5c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1fc5c-105">Syntax</span></span>  
  
```cpp  
HRESULT VirtualProtect (  
    [in]  void*   lpAddress,  
    [in]  SIZE_T  dwSize,  
    [in]  DWORD   flNewProtect,  
    [out] DWORD*  pflOldProtect  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1fc5c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1fc5c-106">Parameters</span></span>  
 `lpAddress`  
 <span data-ttu-id="1fc5c-107">'ndaki Koruma öznitelikleri değiştirilecek olan sanal belleğin temel adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1fc5c-107">[in] A pointer to the base address of the virtual memory whose protection attributes are to be changed.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="1fc5c-108">'ndaki Değiştirilecek bellek sayfaları bölgesinin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="1fc5c-108">[in] The size, in bytes, of the region of memory pages to be changed.</span></span>  
  
 `flNewProtect`  
 <span data-ttu-id="1fc5c-109">'ndaki Uygulanacak bellek koruması türü.</span><span class="sxs-lookup"><span data-stu-id="1fc5c-109">[in] The type of memory protection to apply.</span></span>  
  
 `pflOldProtect`  
 <span data-ttu-id="1fc5c-110">dışı Önceki bellek koruma değerine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1fc5c-110">[out] A pointer to the previous memory protection value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1fc5c-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1fc5c-111">Return Value</span></span>  
  
|<span data-ttu-id="1fc5c-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1fc5c-112">HRESULT</span></span>|<span data-ttu-id="1fc5c-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1fc5c-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1fc5c-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="1fc5c-114">S_OK</span></span>|<span data-ttu-id="1fc5c-115">`VirtualProtect` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="1fc5c-115">`VirtualProtect` returned successfully.</span></span>|  
|<span data-ttu-id="1fc5c-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1fc5c-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1fc5c-117">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="1fc5c-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1fc5c-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1fc5c-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1fc5c-119">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="1fc5c-119">The call timed out.</span></span>|  
|<span data-ttu-id="1fc5c-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1fc5c-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1fc5c-121">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="1fc5c-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1fc5c-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1fc5c-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1fc5c-123">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="1fc5c-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1fc5c-124">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="1fc5c-124">E_FAIL</span></span>|<span data-ttu-id="1fc5c-125">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="1fc5c-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1fc5c-126">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="1fc5c-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1fc5c-127">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="1fc5c-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1fc5c-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1fc5c-128">Remarks</span></span>  
 <span data-ttu-id="1fc5c-129">Bu `VirtualProtect` uygulamasının bir HRESULT değeri, Win32 uygulamasının başarıyı göstermek için sıfır olmayan bir değer ve hata göstermek için sıfır değeri döndürmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="1fc5c-129">This implementation of `VirtualProtect` returns an HRESULT value, while the Win32 implementation returns a non-zero value to indicate success, and a zero value to indicate failure.</span></span> <span data-ttu-id="1fc5c-130">Daha fazla bilgi için bkz. Windows platformu belgeleri.</span><span class="sxs-lookup"><span data-stu-id="1fc5c-130">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1fc5c-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1fc5c-131">Requirements</span></span>  
 <span data-ttu-id="1fc5c-132">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1fc5c-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1fc5c-133">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1fc5c-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1fc5c-134">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="1fc5c-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1fc5c-135">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1fc5c-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fc5c-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1fc5c-136">See also</span></span>

- [<span data-ttu-id="1fc5c-137">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1fc5c-137">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)

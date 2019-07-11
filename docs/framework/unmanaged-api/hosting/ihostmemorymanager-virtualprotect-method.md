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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1aa4ab44fc8ef1033dcef1a9b36d7487da86cd58
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779361"
---
# <a name="ihostmemorymanagervirtualprotect-method"></a><span data-ttu-id="965f6-102">IHostMemoryManager::VirtualProtect Yöntemi</span><span class="sxs-lookup"><span data-stu-id="965f6-102">IHostMemoryManager::VirtualProtect Method</span></span>
<span data-ttu-id="965f6-103">Karşılık gelen Win32 işlevini için mantıksal bir sarmalayıcı olarak görev yapar.</span><span class="sxs-lookup"><span data-stu-id="965f6-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="965f6-104">Win32 uygulaması `VirtualProtect` bölgesindeki korumayı taahhüt edilen sayfa çağırma işleminin sanal adres alanı değiştirir.</span><span class="sxs-lookup"><span data-stu-id="965f6-104">The Win32 implementation of `VirtualProtect` changes the protection on a region of committed pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="965f6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="965f6-105">Syntax</span></span>  
  
```cpp  
HRESULT VirtualProtect (  
    [in]  void*   lpAddress,  
    [in]  SIZE_T  dwSize,  
    [in]  DWORD   flNewProtect,  
    [out] DWORD*  pflOldProtect  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="965f6-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="965f6-106">Parameters</span></span>  
 `lpAddress`  
 <span data-ttu-id="965f6-107">[in] Taban adresi koruma niteliklerini değiştirilecek olan sanal bellek işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="965f6-107">[in] A pointer to the base address of the virtual memory whose protection attributes are to be changed.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="965f6-108">[in] Değiştirilecek bellek sayfalarının bölgesi bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="965f6-108">[in] The size, in bytes, of the region of memory pages to be changed.</span></span>  
  
 `flNewProtect`  
 <span data-ttu-id="965f6-109">[in] Bellek koruma uygulamak için türü.</span><span class="sxs-lookup"><span data-stu-id="965f6-109">[in] The type of memory protection to apply.</span></span>  
  
 `pflOldProtect`  
 <span data-ttu-id="965f6-110">[out] Önceki bellek koruma değeri için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="965f6-110">[out] A pointer to the previous memory protection value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="965f6-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="965f6-111">Return Value</span></span>  
  
|<span data-ttu-id="965f6-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="965f6-112">HRESULT</span></span>|<span data-ttu-id="965f6-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="965f6-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="965f6-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="965f6-114">S_OK</span></span>|<span data-ttu-id="965f6-115">`VirtualProtect` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="965f6-115">`VirtualProtect` returned successfully.</span></span>|  
|<span data-ttu-id="965f6-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="965f6-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="965f6-117">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="965f6-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="965f6-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="965f6-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="965f6-119">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="965f6-119">The call timed out.</span></span>|  
|<span data-ttu-id="965f6-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="965f6-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="965f6-121">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="965f6-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="965f6-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="965f6-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="965f6-123">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="965f6-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="965f6-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="965f6-124">E_FAIL</span></span>|<span data-ttu-id="965f6-125">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="965f6-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="965f6-126">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="965f6-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="965f6-127">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="965f6-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="965f6-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="965f6-128">Remarks</span></span>  
 <span data-ttu-id="965f6-129">Bu uygulaması `VirtualProtect` HRESULT değerini, Win32 uygulaması başarılı olduğunu belirtmek için sıfır olmayan bir değer döndürür ve hata göstermek için sıfır değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="965f6-129">This implementation of `VirtualProtect` returns an HRESULT value, while the Win32 implementation returns a non-zero value to indicate success, and a zero value to indicate failure.</span></span> <span data-ttu-id="965f6-130">Daha fazla bilgi için Windows Platform belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="965f6-130">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="965f6-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="965f6-131">Requirements</span></span>  
 <span data-ttu-id="965f6-132">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="965f6-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="965f6-133">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="965f6-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="965f6-134">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="965f6-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="965f6-135">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="965f6-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="965f6-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="965f6-136">See also</span></span>

- [<span data-ttu-id="965f6-137">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="965f6-137">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)

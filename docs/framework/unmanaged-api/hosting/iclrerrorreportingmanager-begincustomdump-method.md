---
title: ICLRErrorReportingManager::BeginCustomDump Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRErrorReportingManager.BeginCustomDump
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager::BeginCustomDump
helpviewer_keywords:
- ICLRErrorReportingManager::BeginCustomDump method [.NET Framework hosting]
- BeginCustomDump method
ms.assetid: 93424a87-ba13-4fa1-b4dc-69d44437b7ae
topic_type:
- apiref
ms.openlocfilehash: 7153ac214ab99228ac9c59032aa8248d06d14c3b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129305"
---
# <a name="iclrerrorreportingmanagerbegincustomdump-method"></a><span data-ttu-id="25ca6-102">ICLRErrorReportingManager::BeginCustomDump Yöntemi</span><span class="sxs-lookup"><span data-stu-id="25ca6-102">ICLRErrorReportingManager::BeginCustomDump Method</span></span>
<span data-ttu-id="25ca6-103">Hata raporlama için özel yığın dökümlerinin yapılandırmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="25ca6-103">Specifies the configuration of custom heap dumps for error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25ca6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="25ca6-104">Syntax</span></span>  
  
```cpp  
HRESULT BeginCustomDump (  
    [in] ECustomDumpFlavor dwFlavor,  
    [in] DWORD dwNumItems,  
    [in, size_is(dwNumItems), length_is(dwNumItems)] CustomDumpItem items[],  
    DWORD dwReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25ca6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="25ca6-105">Parameters</span></span>  
 `dwFlavor`  
 <span data-ttu-id="25ca6-106">'ndaki Özel yığın dökümünden sonra oluşturulacak yığın dökümü türünü gösteren bir [ECustomDumpFlavor](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="25ca6-106">[in] A [ECustomDumpFlavor](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md) value that indicates the kind of heap dump upon which to build the custom heap dump.</span></span>  
  
 `dwNumItems`  
 <span data-ttu-id="25ca6-107">'ndaki `items` dizisinin uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="25ca6-107">[in] The length of the `items` array.</span></span> <span data-ttu-id="25ca6-108">`dwFlavor` DUMP_FLAVOR_Mini değilse, `dwNumItems` sıfır olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="25ca6-108">If `dwFlavor` is not DUMP_FLAVOR_Mini, `dwNumItems` should be zero.</span></span>  
  
 `items`  
 <span data-ttu-id="25ca6-109">'ndaki Mini döküme eklenecek öğeleri belirten bir [Customdumpitem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) örnekleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="25ca6-109">[in] An array of [CustomDumpItem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) instances, specifying the items to add to the mini-dump.</span></span> <span data-ttu-id="25ca6-110">`dwFlavor` DUMP_FLAVOR_Mini değilse, `items` null olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="25ca6-110">If `dwFlavor` is not DUMP_FLAVOR_Mini, `items` should be null.</span></span>  
  
 `dwReserved`  
 <span data-ttu-id="25ca6-111">'ndaki Gelecekte kullanılmak üzere ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="25ca6-111">[in] Reserved for future use.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="25ca6-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="25ca6-112">Return Value</span></span>  
  
|<span data-ttu-id="25ca6-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="25ca6-113">HRESULT</span></span>|<span data-ttu-id="25ca6-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="25ca6-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="25ca6-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="25ca6-115">S_OK</span></span>|<span data-ttu-id="25ca6-116">Yöntem başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="25ca6-116">The method returned successfully.</span></span>|  
|<span data-ttu-id="25ca6-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="25ca6-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="25ca6-118">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="25ca6-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="25ca6-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="25ca6-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="25ca6-120">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="25ca6-120">The call timed out.</span></span>|  
|<span data-ttu-id="25ca6-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="25ca6-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="25ca6-122">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="25ca6-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="25ca6-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="25ca6-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="25ca6-124">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="25ca6-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="25ca6-125">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="25ca6-125">E_FAIL</span></span>|<span data-ttu-id="25ca6-126">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="25ca6-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="25ca6-127">Bir yöntem E_FAıL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="25ca6-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="25ca6-128">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="25ca6-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25ca6-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="25ca6-129">Remarks</span></span>  
 <span data-ttu-id="25ca6-130">`BeginCustomDump` yöntemi özel yığın dökümü yapılandırmasını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="25ca6-130">The `BeginCustomDump` method sets custom heap dump configuration.</span></span> <span data-ttu-id="25ca6-131">[EndCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md) yöntemi özel yığın dökümü yapılandırmasını temizler ve ilişkili tüm durumları serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="25ca6-131">The [EndCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md) method clears the custom heap dump configuration and frees any associated state.</span></span> <span data-ttu-id="25ca6-132">Özel yığın dökümü tamamlandıktan sonra çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="25ca6-132">It should be called after the custom heap dump is complete.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="25ca6-133">`EndCustomDump` çağıramaması, belleğin sızmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="25ca6-133">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25ca6-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="25ca6-134">Requirements</span></span>  
 <span data-ttu-id="25ca6-135">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25ca6-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25ca6-136">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="25ca6-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="25ca6-137">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="25ca6-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="25ca6-138">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25ca6-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25ca6-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="25ca6-139">See also</span></span>

- [<span data-ttu-id="25ca6-140">CustomDumpItem Yapısı</span><span class="sxs-lookup"><span data-stu-id="25ca6-140">CustomDumpItem Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md)
- [<span data-ttu-id="25ca6-141">ECustomDumpFlavor Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="25ca6-141">ECustomDumpFlavor Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md)
- [<span data-ttu-id="25ca6-142">ICLRErrorReportingManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="25ca6-142">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)

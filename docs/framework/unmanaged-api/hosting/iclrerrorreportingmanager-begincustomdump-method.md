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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 98eebd489792f57f7f98d3596d4f25be2e847441
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966273"
---
# <a name="iclrerrorreportingmanagerbegincustomdump-method"></a><span data-ttu-id="cb613-102">ICLRErrorReportingManager::BeginCustomDump Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cb613-102">ICLRErrorReportingManager::BeginCustomDump Method</span></span>
<span data-ttu-id="cb613-103">Hata raporlama için özel yığın dökümlerinin yapılandırmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="cb613-103">Specifies the configuration of custom heap dumps for error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb613-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cb613-104">Syntax</span></span>  
  
```cpp  
HRESULT BeginCustomDump (  
    [in] ECustomDumpFlavor dwFlavor,  
    [in] DWORD dwNumItems,  
    [in, size_is(dwNumItems), length_is(dwNumItems)] CustomDumpItem items[],  
    DWORD dwReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb613-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cb613-105">Parameters</span></span>  
 `dwFlavor`  
 <span data-ttu-id="cb613-106">'ndaki Özel yığın dökümünden sonra oluşturulacak yığın dökümü türünü gösteren bir [ECustomDumpFlavor](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="cb613-106">[in] A [ECustomDumpFlavor](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md) value that indicates the kind of heap dump upon which to build the custom heap dump.</span></span>  
  
 `dwNumItems`  
 <span data-ttu-id="cb613-107">'ndaki `items` Dizinin uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="cb613-107">[in] The length of the `items` array.</span></span> <span data-ttu-id="cb613-108">`dwFlavor` DUMP_FLAVOR_Mini`dwNumItems` değilse sıfır olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cb613-108">If `dwFlavor` is not DUMP_FLAVOR_Mini, `dwNumItems` should be zero.</span></span>  
  
 `items`  
 <span data-ttu-id="cb613-109">'ndaki Mini döküme eklenecek öğeleri belirten bir [Customdumpitem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) örnekleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="cb613-109">[in] An array of [CustomDumpItem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) instances, specifying the items to add to the mini-dump.</span></span> <span data-ttu-id="cb613-110">DUMP_FLAVOR_Mini değilse, `items` null olmalıdır. `dwFlavor`</span><span class="sxs-lookup"><span data-stu-id="cb613-110">If `dwFlavor` is not DUMP_FLAVOR_Mini, `items` should be null.</span></span>  
  
 `dwReserved`  
 <span data-ttu-id="cb613-111">'ndaki Gelecekte kullanılmak üzere ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="cb613-111">[in] Reserved for future use.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cb613-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="cb613-112">Return Value</span></span>  
  
|<span data-ttu-id="cb613-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cb613-113">HRESULT</span></span>|<span data-ttu-id="cb613-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cb613-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cb613-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="cb613-115">S_OK</span></span>|<span data-ttu-id="cb613-116">Yöntem başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="cb613-116">The method returned successfully.</span></span>|  
|<span data-ttu-id="cb613-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cb613-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cb613-118">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="cb613-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cb613-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cb613-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cb613-120">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="cb613-120">The call timed out.</span></span>|  
|<span data-ttu-id="cb613-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cb613-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cb613-122">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="cb613-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cb613-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cb613-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cb613-124">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="cb613-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="cb613-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cb613-125">E_FAIL</span></span>|<span data-ttu-id="cb613-126">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="cb613-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cb613-127">Bir yöntem E_FAıL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="cb613-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cb613-128">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="cb613-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cb613-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cb613-129">Remarks</span></span>  
 <span data-ttu-id="cb613-130">`BeginCustomDump` Yöntemi özel yığın dökümü yapılandırmasını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="cb613-130">The `BeginCustomDump` method sets custom heap dump configuration.</span></span> <span data-ttu-id="cb613-131">[EndCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md) yöntemi özel yığın dökümü yapılandırmasını temizler ve ilişkili tüm durumları serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="cb613-131">The [EndCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md) method clears the custom heap dump configuration and frees any associated state.</span></span> <span data-ttu-id="cb613-132">Özel yığın dökümü tamamlandıktan sonra çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cb613-132">It should be called after the custom heap dump is complete.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="cb613-133">Çağırma `EndCustomDump` hatası, belleğin sızmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="cb613-133">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb613-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cb613-134">Requirements</span></span>  
 <span data-ttu-id="cb613-135">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb613-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb613-136">**Üst bilgi** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="cb613-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cb613-137">**Kitaplığı** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="cb613-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cb613-138">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb613-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb613-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cb613-139">See also</span></span>

- [<span data-ttu-id="cb613-140">CustomDumpItem Yapısı</span><span class="sxs-lookup"><span data-stu-id="cb613-140">CustomDumpItem Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md)
- [<span data-ttu-id="cb613-141">ECustomDumpFlavor Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="cb613-141">ECustomDumpFlavor Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md)
- [<span data-ttu-id="cb613-142">ICLRErrorReportingManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cb613-142">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)

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
ms.openlocfilehash: af752ae52956ae1d97fb14ec3b494effdaed35c9
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496618"
---
# <a name="iclrerrorreportingmanagerbegincustomdump-method"></a><span data-ttu-id="6ad71-102">ICLRErrorReportingManager::BeginCustomDump Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6ad71-102">ICLRErrorReportingManager::BeginCustomDump Method</span></span>
<span data-ttu-id="6ad71-103">Hata bildirimi için özel bir yığın dökümlerini yapılandırmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6ad71-103">Specifies the configuration of custom heap dumps for error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ad71-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6ad71-104">Syntax</span></span>  
  
```  
HRESULT BeginCustomDump (  
    [in] ECustomDumpFlavor dwFlavor,  
    [in] DWORD dwNumItems,  
    [in, size_is(dwNumItems), length_is(dwNumItems)] CustomDumpItem items[],  
    DWORD dwReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6ad71-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6ad71-105">Parameters</span></span>  
 `dwFlavor`  
 <span data-ttu-id="6ad71-106">[in] A [ECustomDumpFlavor](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md) alacağı özel yığının döküm oluşturmak yığın dökümü türünü belirten değer.</span><span class="sxs-lookup"><span data-stu-id="6ad71-106">[in] A [ECustomDumpFlavor](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md) value that indicates the kind of heap dump upon which to build the custom heap dump.</span></span>  
  
 `dwNumItems`  
 <span data-ttu-id="6ad71-107">[in] Uzunluğunu `items` dizisi.</span><span class="sxs-lookup"><span data-stu-id="6ad71-107">[in] The length of the `items` array.</span></span> <span data-ttu-id="6ad71-108">Varsa `dwFlavor` DUMP_FLAVOR_Mini, değil `dwNumItems` sıfır olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6ad71-108">If `dwFlavor` is not DUMP_FLAVOR_Mini, `dwNumItems` should be zero.</span></span>  
  
 `items`  
 <span data-ttu-id="6ad71-109">[in] Bir dizi [Customdumpıtem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) örnekleri, mini döküm için eklenecek öğeleri belirtme.</span><span class="sxs-lookup"><span data-stu-id="6ad71-109">[in] An array of [CustomDumpItem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) instances, specifying the items to add to the mini-dump.</span></span> <span data-ttu-id="6ad71-110">Varsa `dwFlavor` DUMP_FLAVOR_Mini, değil `items` null olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6ad71-110">If `dwFlavor` is not DUMP_FLAVOR_Mini, `items` should be null.</span></span>  
  
 `dwReserved`  
 <span data-ttu-id="6ad71-111">[in] Gelecekte kullanılmak üzere ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="6ad71-111">[in] Reserved for future use.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6ad71-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6ad71-112">Return Value</span></span>  
  
|<span data-ttu-id="6ad71-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6ad71-113">HRESULT</span></span>|<span data-ttu-id="6ad71-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6ad71-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6ad71-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="6ad71-115">S_OK</span></span>|<span data-ttu-id="6ad71-116">Yöntemi başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="6ad71-116">The method returned successfully.</span></span>|  
|<span data-ttu-id="6ad71-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6ad71-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6ad71-118">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="6ad71-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6ad71-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6ad71-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6ad71-120">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="6ad71-120">The call timed out.</span></span>|  
|<span data-ttu-id="6ad71-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6ad71-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6ad71-122">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="6ad71-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6ad71-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6ad71-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6ad71-124">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="6ad71-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6ad71-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6ad71-125">E_FAIL</span></span>|<span data-ttu-id="6ad71-126">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="6ad71-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6ad71-127">CLR, artık E_FAIL bir yöntemin dönüşünün ardından, işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="6ad71-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6ad71-128">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="6ad71-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6ad71-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6ad71-129">Remarks</span></span>  
 <span data-ttu-id="6ad71-130">`BeginCustomDump` Yöntemi özel yığının döküm yapılandırmasını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6ad71-130">The `BeginCustomDump` method sets custom heap dump configuration.</span></span> <span data-ttu-id="6ad71-131">[EndCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md) yöntemi özel yığının döküm yapılandırmasını temizler ve herhangi bir ilişkili durumu serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="6ad71-131">The [EndCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md) method clears the custom heap dump configuration and frees any associated state.</span></span> <span data-ttu-id="6ad71-132">Özel yığının döküm tamamlandıktan sonra çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6ad71-132">It should be called after the custom heap dump is complete.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6ad71-133">Aranacak hata `EndCustomDump` bellek sızıntısı neden olur.</span><span class="sxs-lookup"><span data-stu-id="6ad71-133">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ad71-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6ad71-134">Requirements</span></span>  
 <span data-ttu-id="6ad71-135">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ad71-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ad71-136">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6ad71-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6ad71-137">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="6ad71-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6ad71-138">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ad71-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ad71-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6ad71-139">See also</span></span>
- [<span data-ttu-id="6ad71-140">CustomDumpItem Yapısı</span><span class="sxs-lookup"><span data-stu-id="6ad71-140">CustomDumpItem Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md)
- [<span data-ttu-id="6ad71-141">ECustomDumpFlavor Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="6ad71-141">ECustomDumpFlavor Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md)
- [<span data-ttu-id="6ad71-142">ICLRErrorReportingManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6ad71-142">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)

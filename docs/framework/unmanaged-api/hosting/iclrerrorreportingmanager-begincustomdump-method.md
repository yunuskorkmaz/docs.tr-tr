---
title: "ICLRErrorReportingManager::BeginCustomDump Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d09afd9fe0a2905c79ffb2d50b342041865b593b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrerrorreportingmanagerbegincustomdump-method"></a><span data-ttu-id="763e0-102">ICLRErrorReportingManager::BeginCustomDump Yöntemi</span><span class="sxs-lookup"><span data-stu-id="763e0-102">ICLRErrorReportingManager::BeginCustomDump Method</span></span>
<span data-ttu-id="763e0-103">Hata bildirimi için özel yığın dökümleri yapılandırılmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="763e0-103">Specifies the configuration of custom heap dumps for error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="763e0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="763e0-104">Syntax</span></span>  
  
```  
HRESULT BeginCustomDump (  
    [in] ECustomDumpFlavor dwFlavor,  
    [in] DWORD dwNumItems,  
    [in, size_is(dwNumItems), length_is(dwNumItems)] CustomDumpItem items[],  
    DWORD dwReserved  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="763e0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="763e0-105">Parameters</span></span>  
 `dwFlavor`  
 <span data-ttu-id="763e0-106">[in] A [ECustomDumpFlavor](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md) yığın dökümü özel yığın dökümü yapı alacağı türünü belirten değer.</span><span class="sxs-lookup"><span data-stu-id="763e0-106">[in] A [ECustomDumpFlavor](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md) value that indicates the kind of heap dump upon which to build the custom heap dump.</span></span>  
  
 `dwNumItems`  
 <span data-ttu-id="763e0-107">[in] Uzunluğu `items` dizi.</span><span class="sxs-lookup"><span data-stu-id="763e0-107">[in] The length of the `items` array.</span></span> <span data-ttu-id="763e0-108">Varsa `dwFlavor` DUMP_FLAVOR_Mini, değil `dwNumItems` sıfır olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="763e0-108">If `dwFlavor` is not DUMP_FLAVOR_Mini, `dwNumItems` should be zero.</span></span>  
  
 `items`  
 <span data-ttu-id="763e0-109">[in] Bir dizi [Customdumpıtem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) örnekleri, mini döküm eklemek için öğeleri belirtme.</span><span class="sxs-lookup"><span data-stu-id="763e0-109">[in] An array of [CustomDumpItem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) instances, specifying the items to add to the mini-dump.</span></span> <span data-ttu-id="763e0-110">Varsa `dwFlavor` DUMP_FLAVOR_Mini, değil `items` null olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="763e0-110">If `dwFlavor` is not DUMP_FLAVOR_Mini, `items` should be null.</span></span>  
  
 `dwReserved`  
 <span data-ttu-id="763e0-111">[in] Gelecekte kullanılmak üzere ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="763e0-111">[in] Reserved for future use.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="763e0-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="763e0-112">Return Value</span></span>  
  
|<span data-ttu-id="763e0-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="763e0-113">HRESULT</span></span>|<span data-ttu-id="763e0-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="763e0-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="763e0-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="763e0-115">S_OK</span></span>|<span data-ttu-id="763e0-116">Yöntem başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="763e0-116">The method returned successfully.</span></span>|  
|<span data-ttu-id="763e0-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="763e0-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="763e0-118">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="763e0-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="763e0-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="763e0-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="763e0-120">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="763e0-120">The call timed out.</span></span>|  
|<span data-ttu-id="763e0-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="763e0-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="763e0-122">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="763e0-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="763e0-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="763e0-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="763e0-124">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="763e0-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="763e0-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="763e0-125">E_FAIL</span></span>|<span data-ttu-id="763e0-126">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="763e0-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="763e0-127">CLR, artık bir yöntem E_FAIL döndükten sonra işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="763e0-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="763e0-128">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="763e0-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="763e0-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="763e0-129">Remarks</span></span>  
 <span data-ttu-id="763e0-130">`BeginCustomDump` Yöntemi özel yığın dökümü yapılandırmasını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="763e0-130">The `BeginCustomDump` method sets custom heap dump configuration.</span></span> <span data-ttu-id="763e0-131">[EndCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md) yöntemi özel yığın dökümü yapılandırma temizler ve tüm ilişkili durumu boşaltır.</span><span class="sxs-lookup"><span data-stu-id="763e0-131">The [EndCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md) method clears the custom heap dump configuration and frees any associated state.</span></span> <span data-ttu-id="763e0-132">Özel yığın dökümü tamamlandıktan sonra çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="763e0-132">It should be called after the custom heap dump is complete.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="763e0-133">Çağrılacak hatası `EndCustomDump` bellek sızıntısı neden olur.</span><span class="sxs-lookup"><span data-stu-id="763e0-133">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="763e0-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="763e0-134">Requirements</span></span>  
 <span data-ttu-id="763e0-135">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="763e0-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="763e0-136">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="763e0-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="763e0-137">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="763e0-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="763e0-138">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="763e0-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="763e0-139">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="763e0-139">See Also</span></span>  
 [<span data-ttu-id="763e0-140">CustomDumpItem Yapısı</span><span class="sxs-lookup"><span data-stu-id="763e0-140">CustomDumpItem Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md)  
 [<span data-ttu-id="763e0-141">ECustomDumpFlavor Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="763e0-141">ECustomDumpFlavor Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md)  
 [<span data-ttu-id="763e0-142">ICLRErrorReportingManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="763e0-142">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)

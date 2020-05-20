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
ms.openlocfilehash: 4c83ffaf920abe005ba987e0a744e13aa0d3c016
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615676"
---
# <a name="iclrerrorreportingmanagerbegincustomdump-method"></a><span data-ttu-id="465cf-102">ICLRErrorReportingManager::BeginCustomDump Yöntemi</span><span class="sxs-lookup"><span data-stu-id="465cf-102">ICLRErrorReportingManager::BeginCustomDump Method</span></span>
<span data-ttu-id="465cf-103">Hata raporlama için özel yığın dökümlerinin yapılandırmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="465cf-103">Specifies the configuration of custom heap dumps for error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="465cf-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="465cf-104">Syntax</span></span>  
  
```cpp  
HRESULT BeginCustomDump (  
    [in] ECustomDumpFlavor dwFlavor,  
    [in] DWORD dwNumItems,  
    [in, size_is(dwNumItems), length_is(dwNumItems)] CustomDumpItem items[],  
    DWORD dwReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="465cf-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="465cf-105">Parameters</span></span>  
 `dwFlavor`  
 <span data-ttu-id="465cf-106">'ndaki Özel yığın dökümünden sonra oluşturulacak yığın dökümü türünü gösteren bir [ECustomDumpFlavor](ecustomdumpflavor-enumeration.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="465cf-106">[in] A [ECustomDumpFlavor](ecustomdumpflavor-enumeration.md) value that indicates the kind of heap dump upon which to build the custom heap dump.</span></span>  
  
 `dwNumItems`  
 <span data-ttu-id="465cf-107">'ndaki `items`Dizinin uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="465cf-107">[in] The length of the `items` array.</span></span> <span data-ttu-id="465cf-108">`dwFlavor`DUMP_FLAVOR_Mini değilse, sıfır olmalıdır `dwNumItems` .</span><span class="sxs-lookup"><span data-stu-id="465cf-108">If `dwFlavor` is not DUMP_FLAVOR_Mini, `dwNumItems` should be zero.</span></span>  
  
 `items`  
 <span data-ttu-id="465cf-109">'ndaki Mini döküme eklenecek öğeleri belirten bir [Customdumpitem](customdumpitem-structure.md) örnekleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="465cf-109">[in] An array of [CustomDumpItem](customdumpitem-structure.md) instances, specifying the items to add to the mini-dump.</span></span> <span data-ttu-id="465cf-110">`dwFlavor`DUMP_FLAVOR_Mini değilse, null olmalıdır `items` .</span><span class="sxs-lookup"><span data-stu-id="465cf-110">If `dwFlavor` is not DUMP_FLAVOR_Mini, `items` should be null.</span></span>  
  
 `dwReserved`  
 <span data-ttu-id="465cf-111">'ndaki Gelecekte kullanılmak üzere ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="465cf-111">[in] Reserved for future use.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="465cf-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="465cf-112">Return Value</span></span>  
  
|<span data-ttu-id="465cf-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="465cf-113">HRESULT</span></span>|<span data-ttu-id="465cf-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="465cf-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="465cf-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="465cf-115">S_OK</span></span>|<span data-ttu-id="465cf-116">Yöntem başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="465cf-116">The method returned successfully.</span></span>|  
|<span data-ttu-id="465cf-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="465cf-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="465cf-118">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="465cf-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="465cf-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="465cf-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="465cf-120">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="465cf-120">The call timed out.</span></span>|  
|<span data-ttu-id="465cf-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="465cf-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="465cf-122">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="465cf-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="465cf-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="465cf-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="465cf-124">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="465cf-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="465cf-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="465cf-125">E_FAIL</span></span>|<span data-ttu-id="465cf-126">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="465cf-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="465cf-127">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="465cf-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="465cf-128">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="465cf-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="465cf-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="465cf-129">Remarks</span></span>  
 <span data-ttu-id="465cf-130">`BeginCustomDump`Yöntemi özel yığın dökümü yapılandırmasını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="465cf-130">The `BeginCustomDump` method sets custom heap dump configuration.</span></span> <span data-ttu-id="465cf-131">[EndCustomDump](iclrerrorreportingmanager-endcustomdump-method.md) yöntemi özel yığın dökümü yapılandırmasını temizler ve ilişkili tüm durumları serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="465cf-131">The [EndCustomDump](iclrerrorreportingmanager-endcustomdump-method.md) method clears the custom heap dump configuration and frees any associated state.</span></span> <span data-ttu-id="465cf-132">Özel yığın dökümü tamamlandıktan sonra çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="465cf-132">It should be called after the custom heap dump is complete.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="465cf-133">Çağırma hatası, `EndCustomDump` belleğin sızmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="465cf-133">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="465cf-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="465cf-134">Requirements</span></span>  
 <span data-ttu-id="465cf-135">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="465cf-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="465cf-136">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="465cf-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="465cf-137">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="465cf-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="465cf-138">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="465cf-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="465cf-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="465cf-139">See also</span></span>

- [<span data-ttu-id="465cf-140">CustomDumpItem Yapısı</span><span class="sxs-lookup"><span data-stu-id="465cf-140">CustomDumpItem Structure</span></span>](customdumpitem-structure.md)
- [<span data-ttu-id="465cf-141">ECustomDumpFlavor Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="465cf-141">ECustomDumpFlavor Enumeration</span></span>](ecustomdumpflavor-enumeration.md)
- [<span data-ttu-id="465cf-142">ICLRErrorReportingManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="465cf-142">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)

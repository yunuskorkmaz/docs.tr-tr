---
description: ': ICLRErrorReportingManager:: BeginCustomDump Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 3f8498068d50ffc6ea00cf4f08f969c92f010d6c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689488"
---
# <a name="iclrerrorreportingmanagerbegincustomdump-method"></a><span data-ttu-id="c4522-103">ICLRErrorReportingManager::BeginCustomDump Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c4522-103">ICLRErrorReportingManager::BeginCustomDump Method</span></span>

<span data-ttu-id="c4522-104">Hata raporlama için özel yığın dökümlerinin yapılandırmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4522-104">Specifies the configuration of custom heap dumps for error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4522-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c4522-105">Syntax</span></span>  
  
```cpp  
HRESULT BeginCustomDump (  
    [in] ECustomDumpFlavor dwFlavor,  
    [in] DWORD dwNumItems,  
    [in, size_is(dwNumItems), length_is(dwNumItems)] CustomDumpItem items[],  
    DWORD dwReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4522-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c4522-106">Parameters</span></span>  

 `dwFlavor`  
 <span data-ttu-id="c4522-107">'ndaki Özel yığın dökümünden sonra oluşturulacak yığın dökümü türünü gösteren bir [ECustomDumpFlavor](ecustomdumpflavor-enumeration.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="c4522-107">[in] A [ECustomDumpFlavor](ecustomdumpflavor-enumeration.md) value that indicates the kind of heap dump upon which to build the custom heap dump.</span></span>  
  
 `dwNumItems`  
 <span data-ttu-id="c4522-108">'ndaki `items` Dizinin uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="c4522-108">[in] The length of the `items` array.</span></span> <span data-ttu-id="c4522-109">`dwFlavor`DUMP_FLAVOR_Mini değilse, sıfır olmalıdır `dwNumItems` .</span><span class="sxs-lookup"><span data-stu-id="c4522-109">If `dwFlavor` is not DUMP_FLAVOR_Mini, `dwNumItems` should be zero.</span></span>  
  
 `items`  
 <span data-ttu-id="c4522-110">'ndaki Mini döküme eklenecek öğeleri belirten bir [Customdumpitem](customdumpitem-structure.md) örnekleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="c4522-110">[in] An array of [CustomDumpItem](customdumpitem-structure.md) instances, specifying the items to add to the mini-dump.</span></span> <span data-ttu-id="c4522-111">`dwFlavor`DUMP_FLAVOR_Mini değilse, null olmalıdır `items` .</span><span class="sxs-lookup"><span data-stu-id="c4522-111">If `dwFlavor` is not DUMP_FLAVOR_Mini, `items` should be null.</span></span>  
  
 `dwReserved`  
 <span data-ttu-id="c4522-112">'ndaki Gelecekte kullanılmak üzere ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="c4522-112">[in] Reserved for future use.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c4522-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c4522-113">Return Value</span></span>  
  
|<span data-ttu-id="c4522-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c4522-114">HRESULT</span></span>|<span data-ttu-id="c4522-115">Description</span><span class="sxs-lookup"><span data-stu-id="c4522-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c4522-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="c4522-116">S_OK</span></span>|<span data-ttu-id="c4522-117">Yöntem başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="c4522-117">The method returned successfully.</span></span>|  
|<span data-ttu-id="c4522-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c4522-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c4522-119">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="c4522-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c4522-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c4522-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c4522-121">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="c4522-121">The call timed out.</span></span>|  
|<span data-ttu-id="c4522-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c4522-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c4522-123">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="c4522-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c4522-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c4522-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c4522-125">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="c4522-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c4522-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c4522-126">E_FAIL</span></span>|<span data-ttu-id="c4522-127">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="c4522-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c4522-128">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="c4522-128">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c4522-129">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="c4522-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4522-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c4522-130">Remarks</span></span>  

 <span data-ttu-id="c4522-131">`BeginCustomDump`Yöntemi özel yığın dökümü yapılandırmasını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c4522-131">The `BeginCustomDump` method sets custom heap dump configuration.</span></span> <span data-ttu-id="c4522-132">[EndCustomDump](iclrerrorreportingmanager-endcustomdump-method.md) yöntemi özel yığın dökümü yapılandırmasını temizler ve ilişkili tüm durumları serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="c4522-132">The [EndCustomDump](iclrerrorreportingmanager-endcustomdump-method.md) method clears the custom heap dump configuration and frees any associated state.</span></span> <span data-ttu-id="c4522-133">Özel yığın dökümü tamamlandıktan sonra çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c4522-133">It should be called after the custom heap dump is complete.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c4522-134">Çağırma hatası, `EndCustomDump` belleğin sızmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="c4522-134">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4522-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c4522-135">Requirements</span></span>  

 <span data-ttu-id="c4522-136">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4522-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4522-137">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c4522-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c4522-138">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="c4522-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c4522-139">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4522-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4522-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4522-140">See also</span></span>

- [<span data-ttu-id="c4522-141">CustomDumpItem Yapısı</span><span class="sxs-lookup"><span data-stu-id="c4522-141">CustomDumpItem Structure</span></span>](customdumpitem-structure.md)
- [<span data-ttu-id="c4522-142">ECustomDumpFlavor Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="c4522-142">ECustomDumpFlavor Enumeration</span></span>](ecustomdumpflavor-enumeration.md)
- [<span data-ttu-id="c4522-143">ICLRErrorReportingManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c4522-143">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)

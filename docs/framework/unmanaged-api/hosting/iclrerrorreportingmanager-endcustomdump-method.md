---
title: ICLRErrorReportingManager::EndCustomDump Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRErrorReportingManager.EndCustomDump
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager::EndCustomDump
helpviewer_keywords:
- ICLRErrorReportingManager::EndCustomDump method [.NET Framework hosting]
- EndCustomDump method [.NET Framework hosting]
ms.assetid: 88a5da04-8729-4108-82c4-af206a7d483e
topic_type:
- apiref
ms.openlocfilehash: 2acbe72377e4c5b291ab062fcb5faa6503bd7937
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129286"
---
# <a name="iclrerrorreportingmanagerendcustomdump-method"></a><span data-ttu-id="2b6c2-102">ICLRErrorReportingManager::EndCustomDump Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2b6c2-102">ICLRErrorReportingManager::EndCustomDump Method</span></span>
<span data-ttu-id="2b6c2-103">Daha önceki bir çağrıda belirtilen özel yığın dökümü yapılandırmasını [ICLRErrorReportingManager:: BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) metoduna kaldırır.</span><span class="sxs-lookup"><span data-stu-id="2b6c2-103">Removes the custom stack dump configuration that was specified in an earlier call to the [ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b6c2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2b6c2-104">Syntax</span></span>  
  
```cpp  
HRESULT EndCustomDump ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="2b6c2-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2b6c2-105">Return Value</span></span>  
  
|<span data-ttu-id="2b6c2-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2b6c2-106">HRESULT</span></span>|<span data-ttu-id="2b6c2-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2b6c2-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2b6c2-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="2b6c2-108">S_OK</span></span>|<span data-ttu-id="2b6c2-109">`EndCustomDump` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="2b6c2-109">`EndCustomDump` returned successfully.</span></span>|  
|<span data-ttu-id="2b6c2-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2b6c2-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2b6c2-111">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="2b6c2-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2b6c2-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2b6c2-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2b6c2-113">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="2b6c2-113">The call timed out.</span></span>|  
|<span data-ttu-id="2b6c2-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2b6c2-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2b6c2-115">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="2b6c2-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2b6c2-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2b6c2-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2b6c2-117">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="2b6c2-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2b6c2-118">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="2b6c2-118">E_FAIL</span></span>|<span data-ttu-id="2b6c2-119">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="2b6c2-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2b6c2-120">Bir yöntem E_FAıL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="2b6c2-120">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2b6c2-121">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="2b6c2-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b6c2-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2b6c2-122">Remarks</span></span>  
 <span data-ttu-id="2b6c2-123">`EndCustomDump` yöntemi, `BeginCustomDump` yöntemine daha önceki bir çağrı tarafından ayarlanan özel yığın dökümü yapılandırmasını temizler ve ilişkili tüm durumları boşaltır.</span><span class="sxs-lookup"><span data-stu-id="2b6c2-123">The `EndCustomDump` method clears the custom stack dump configuration set by an earlier call to the `BeginCustomDump` method and frees any associated state.</span></span> <span data-ttu-id="2b6c2-124">Özel yığın dökümü tamamlandıktan sonra çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2b6c2-124">It should be called after the custom stack dump is complete.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="2b6c2-125">`EndCustomDump` çağıramaması, belleğin sızmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="2b6c2-125">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b6c2-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2b6c2-126">Requirements</span></span>  
 <span data-ttu-id="2b6c2-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b6c2-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b6c2-128">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2b6c2-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2b6c2-129">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="2b6c2-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2b6c2-130">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b6c2-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b6c2-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2b6c2-131">See also</span></span>

- [<span data-ttu-id="2b6c2-132">CustomDumpItem Yapısı</span><span class="sxs-lookup"><span data-stu-id="2b6c2-132">CustomDumpItem Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md)
- [<span data-ttu-id="2b6c2-133">ECustomDumpFlavor Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="2b6c2-133">ECustomDumpFlavor Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md)
- [<span data-ttu-id="2b6c2-134">ICLRErrorReportingManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2b6c2-134">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)

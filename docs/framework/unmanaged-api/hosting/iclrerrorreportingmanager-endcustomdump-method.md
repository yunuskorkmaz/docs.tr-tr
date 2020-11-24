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
ms.openlocfilehash: feaeba15fcc4e8264f7fde57d3b268a6b583ad83
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677841"
---
# <a name="iclrerrorreportingmanagerendcustomdump-method"></a><span data-ttu-id="d29f4-102">ICLRErrorReportingManager::EndCustomDump Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d29f4-102">ICLRErrorReportingManager::EndCustomDump Method</span></span>

<span data-ttu-id="d29f4-103">Daha önceki bir çağrıda belirtilen özel yığın dökümü yapılandırmasını [ICLRErrorReportingManager:: BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md) metoduna kaldırır.</span><span class="sxs-lookup"><span data-stu-id="d29f4-103">Removes the custom stack dump configuration that was specified in an earlier call to the [ICLRErrorReportingManager::BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d29f4-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="d29f4-104">Syntax</span></span>  
  
```cpp  
HRESULT EndCustomDump ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="d29f4-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d29f4-105">Return Value</span></span>  
  
|<span data-ttu-id="d29f4-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d29f4-106">HRESULT</span></span>|<span data-ttu-id="d29f4-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d29f4-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d29f4-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="d29f4-108">S_OK</span></span>|<span data-ttu-id="d29f4-109">`EndCustomDump` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="d29f4-109">`EndCustomDump` returned successfully.</span></span>|  
|<span data-ttu-id="d29f4-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d29f4-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d29f4-111">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="d29f4-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d29f4-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d29f4-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d29f4-113">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="d29f4-113">The call timed out.</span></span>|  
|<span data-ttu-id="d29f4-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d29f4-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d29f4-115">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="d29f4-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d29f4-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d29f4-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d29f4-117">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="d29f4-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d29f4-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d29f4-118">E_FAIL</span></span>|<span data-ttu-id="d29f4-119">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="d29f4-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d29f4-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="d29f4-120">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d29f4-121">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="d29f4-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d29f4-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d29f4-122">Remarks</span></span>  

 <span data-ttu-id="d29f4-123">`EndCustomDump`Yöntemi, yöntemi için daha önceki bir çağrı tarafından ayarlanan özel yığın dökümü yapılandırmasını temizler `BeginCustomDump` ve ilişkili tüm durumları boşaltır.</span><span class="sxs-lookup"><span data-stu-id="d29f4-123">The `EndCustomDump` method clears the custom stack dump configuration set by an earlier call to the `BeginCustomDump` method and frees any associated state.</span></span> <span data-ttu-id="d29f4-124">Özel yığın dökümü tamamlandıktan sonra çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d29f4-124">It should be called after the custom stack dump is complete.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d29f4-125">Çağırma hatası, `EndCustomDump` belleğin sızmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="d29f4-125">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d29f4-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d29f4-126">Requirements</span></span>  

 <span data-ttu-id="d29f4-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d29f4-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d29f4-128">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d29f4-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d29f4-129">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="d29f4-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d29f4-130">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d29f4-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d29f4-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d29f4-131">See also</span></span>

- [<span data-ttu-id="d29f4-132">CustomDumpItem Yapısı</span><span class="sxs-lookup"><span data-stu-id="d29f4-132">CustomDumpItem Structure</span></span>](customdumpitem-structure.md)
- [<span data-ttu-id="d29f4-133">ECustomDumpFlavor Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="d29f4-133">ECustomDumpFlavor Enumeration</span></span>](ecustomdumpflavor-enumeration.md)
- [<span data-ttu-id="d29f4-134">ICLRErrorReportingManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d29f4-134">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)

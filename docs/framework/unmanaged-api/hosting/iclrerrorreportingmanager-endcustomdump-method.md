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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a262ab26c9bbb93e42a11217fbeea6b3c55c7eb9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966261"
---
# <a name="iclrerrorreportingmanagerendcustomdump-method"></a><span data-ttu-id="bc2f6-102">ICLRErrorReportingManager::EndCustomDump Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bc2f6-102">ICLRErrorReportingManager::EndCustomDump Method</span></span>
<span data-ttu-id="bc2f6-103">Daha önceki bir çağrıda belirtilen özel yığın dökümü yapılandırmasını [ICLRErrorReportingManager:: BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) metoduna kaldırır.</span><span class="sxs-lookup"><span data-stu-id="bc2f6-103">Removes the custom stack dump configuration that was specified in an earlier call to the [ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc2f6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bc2f6-104">Syntax</span></span>  
  
```cpp  
HRESULT EndCustomDump ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="bc2f6-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="bc2f6-105">Return Value</span></span>  
  
|<span data-ttu-id="bc2f6-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bc2f6-106">HRESULT</span></span>|<span data-ttu-id="bc2f6-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bc2f6-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bc2f6-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="bc2f6-108">S_OK</span></span>|<span data-ttu-id="bc2f6-109">`EndCustomDump`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="bc2f6-109">`EndCustomDump` returned successfully.</span></span>|  
|<span data-ttu-id="bc2f6-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bc2f6-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bc2f6-111">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="bc2f6-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bc2f6-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bc2f6-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bc2f6-113">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="bc2f6-113">The call timed out.</span></span>|  
|<span data-ttu-id="bc2f6-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bc2f6-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bc2f6-115">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="bc2f6-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bc2f6-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bc2f6-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bc2f6-117">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="bc2f6-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bc2f6-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bc2f6-118">E_FAIL</span></span>|<span data-ttu-id="bc2f6-119">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="bc2f6-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bc2f6-120">Bir yöntem E_FAıL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="bc2f6-120">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bc2f6-121">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="bc2f6-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc2f6-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bc2f6-122">Remarks</span></span>  
 <span data-ttu-id="bc2f6-123">Yöntemi, `BeginCustomDump` yöntemi için daha önceki bir çağrı tarafından ayarlanan özel yığın dökümü yapılandırmasını temizler ve ilişkili tüm durumları boşaltır. `EndCustomDump`</span><span class="sxs-lookup"><span data-stu-id="bc2f6-123">The `EndCustomDump` method clears the custom stack dump configuration set by an earlier call to the `BeginCustomDump` method and frees any associated state.</span></span> <span data-ttu-id="bc2f6-124">Özel yığın dökümü tamamlandıktan sonra çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bc2f6-124">It should be called after the custom stack dump is complete.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="bc2f6-125">Çağırma `EndCustomDump` hatası, belleğin sızmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="bc2f6-125">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc2f6-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bc2f6-126">Requirements</span></span>  
 <span data-ttu-id="bc2f6-127">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc2f6-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc2f6-128">**Üst bilgi** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="bc2f6-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bc2f6-129">**Kitaplığı** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="bc2f6-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bc2f6-130">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc2f6-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc2f6-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc2f6-131">See also</span></span>

- [<span data-ttu-id="bc2f6-132">CustomDumpItem Yapısı</span><span class="sxs-lookup"><span data-stu-id="bc2f6-132">CustomDumpItem Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md)
- [<span data-ttu-id="bc2f6-133">ECustomDumpFlavor Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="bc2f6-133">ECustomDumpFlavor Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md)
- [<span data-ttu-id="bc2f6-134">ICLRErrorReportingManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bc2f6-134">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)

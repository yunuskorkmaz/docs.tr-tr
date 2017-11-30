---
title: "ICLRErrorReportingManager::EndCustomDump Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRErrorReportingManager.EndCustomDump
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRErrorReportingManager::EndCustomDump
helpviewer_keywords:
- ICLRErrorReportingManager::EndCustomDump method [.NET Framework hosting]
- EndCustomDump method [.NET Framework hosting]
ms.assetid: 88a5da04-8729-4108-82c4-af206a7d483e
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 059ab01d3cc05bac84bb1a4cd8fffc7fc259ed60
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrerrorreportingmanagerendcustomdump-method"></a><span data-ttu-id="03b93-102">ICLRErrorReportingManager::EndCustomDump Yöntemi</span><span class="sxs-lookup"><span data-stu-id="03b93-102">ICLRErrorReportingManager::EndCustomDump Method</span></span>
<span data-ttu-id="03b93-103">Önceki bir çağrıda belirtilen özel yığın dökümü yapılandırmasını kaldırır [Iclrerrorreportingmanager::begincustomdump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="03b93-103">Removes the custom stack dump configuration that was specified in an earlier call to the [ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03b93-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="03b93-104">Syntax</span></span>  
  
```  
HRESULT EndCustomDump ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="03b93-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="03b93-105">Return Value</span></span>  
  
|<span data-ttu-id="03b93-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="03b93-106">HRESULT</span></span>|<span data-ttu-id="03b93-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="03b93-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="03b93-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="03b93-108">S_OK</span></span>|<span data-ttu-id="03b93-109">`EndCustomDump`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="03b93-109">`EndCustomDump` returned successfully.</span></span>|  
|<span data-ttu-id="03b93-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="03b93-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="03b93-111">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="03b93-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="03b93-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="03b93-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="03b93-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="03b93-113">The call timed out.</span></span>|  
|<span data-ttu-id="03b93-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="03b93-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="03b93-115">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="03b93-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="03b93-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="03b93-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="03b93-117">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="03b93-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="03b93-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="03b93-118">E_FAIL</span></span>|<span data-ttu-id="03b93-119">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="03b93-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="03b93-120">CLR, artık bir yöntem E_FAIL döndükten sonra işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="03b93-120">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="03b93-121">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="03b93-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="03b93-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="03b93-122">Remarks</span></span>  
 <span data-ttu-id="03b93-123">`EndCustomDump` Yöntemini temizler özel yığın dökümü yapılandırması için önceki bir çağrı tarafından ayarlanmış `BeginCustomDump` yöntemi ve herhangi bir ilişkili durum boşaltır.</span><span class="sxs-lookup"><span data-stu-id="03b93-123">The `EndCustomDump` method clears the custom stack dump configuration set by an earlier call to the `BeginCustomDump` method and frees any associated state.</span></span> <span data-ttu-id="03b93-124">Özel yığın dökümü tamamlandıktan sonra çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="03b93-124">It should be called after the custom stack dump is complete.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="03b93-125">Çağrılacak hatası `EndCustomDump` bellek sızıntısı neden olur.</span><span class="sxs-lookup"><span data-stu-id="03b93-125">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03b93-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="03b93-126">Requirements</span></span>  
 <span data-ttu-id="03b93-127">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03b93-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03b93-128">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="03b93-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="03b93-129">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="03b93-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="03b93-130">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03b93-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03b93-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="03b93-131">See Also</span></span>  
 [<span data-ttu-id="03b93-132">Customdumpıtem yapısı</span><span class="sxs-lookup"><span data-stu-id="03b93-132">CustomDumpItem Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md)  
 [<span data-ttu-id="03b93-133">ECustomDumpFlavor numaralandırması</span><span class="sxs-lookup"><span data-stu-id="03b93-133">ECustomDumpFlavor Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md)  
 [<span data-ttu-id="03b93-134">Iclrerrorreportingmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="03b93-134">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)

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
ms.openlocfilehash: f5e14749c3596ad22a435a11f75c928110c434de
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61969846"
---
# <a name="iclrerrorreportingmanagerendcustomdump-method"></a><span data-ttu-id="c01a8-102">ICLRErrorReportingManager::EndCustomDump Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c01a8-102">ICLRErrorReportingManager::EndCustomDump Method</span></span>
<span data-ttu-id="c01a8-103">Çağrısında belirtilen özel yığının döküm yapılandırmasını kaldırır [Iclrerrorreportingmanager::begincustomdump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c01a8-103">Removes the custom stack dump configuration that was specified in an earlier call to the [ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c01a8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c01a8-104">Syntax</span></span>  
  
```  
HRESULT EndCustomDump ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="c01a8-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c01a8-105">Return Value</span></span>  
  
|<span data-ttu-id="c01a8-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c01a8-106">HRESULT</span></span>|<span data-ttu-id="c01a8-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c01a8-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c01a8-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="c01a8-108">S_OK</span></span>|<span data-ttu-id="c01a8-109">`EndCustomDump` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="c01a8-109">`EndCustomDump` returned successfully.</span></span>|  
|<span data-ttu-id="c01a8-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c01a8-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c01a8-111">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="c01a8-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c01a8-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c01a8-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c01a8-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="c01a8-113">The call timed out.</span></span>|  
|<span data-ttu-id="c01a8-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c01a8-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c01a8-115">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="c01a8-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c01a8-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c01a8-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c01a8-117">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="c01a8-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c01a8-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c01a8-118">E_FAIL</span></span>|<span data-ttu-id="c01a8-119">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="c01a8-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c01a8-120">CLR, artık E_FAIL bir yöntemin dönüşünün ardından, işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="c01a8-120">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c01a8-121">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="c01a8-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c01a8-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c01a8-122">Remarks</span></span>  
 <span data-ttu-id="c01a8-123">`EndCustomDump` Yöntem çağrısında tarafından ayarlanan özel yığının döküm yapılandırmasını temizler `BeginCustomDump` yöntemi ve herhangi bir ilişkili durumu serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="c01a8-123">The `EndCustomDump` method clears the custom stack dump configuration set by an earlier call to the `BeginCustomDump` method and frees any associated state.</span></span> <span data-ttu-id="c01a8-124">Özel yığının döküm tamamlandıktan sonra çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c01a8-124">It should be called after the custom stack dump is complete.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c01a8-125">Aranacak hata `EndCustomDump` bellek sızıntısı neden olur.</span><span class="sxs-lookup"><span data-stu-id="c01a8-125">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c01a8-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c01a8-126">Requirements</span></span>  
 <span data-ttu-id="c01a8-127">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c01a8-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c01a8-128">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c01a8-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c01a8-129">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="c01a8-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c01a8-130">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c01a8-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c01a8-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c01a8-131">See also</span></span>

- [<span data-ttu-id="c01a8-132">CustomDumpItem Yapısı</span><span class="sxs-lookup"><span data-stu-id="c01a8-132">CustomDumpItem Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md)
- [<span data-ttu-id="c01a8-133">ECustomDumpFlavor Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="c01a8-133">ECustomDumpFlavor Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md)
- [<span data-ttu-id="c01a8-134">ICLRErrorReportingManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c01a8-134">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)

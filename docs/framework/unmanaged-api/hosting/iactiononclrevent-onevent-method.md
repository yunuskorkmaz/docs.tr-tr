---
title: IActionOnCLREvent::OnEvent Yöntemi
ms.date: 03/30/2017
api_name:
- IActionOnCLREvent.OnEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IActionOnCLREvent::OnEvent
helpviewer_keywords:
- OnEvent method [.NET Framework hosting]
- IActionOnCLREvent::OnEvent method [.NET Framework hosting]
ms.assetid: 0970f10c-4304-4c12-91c0-83e51455afb4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7da863df03a70ed21769620c033c4c2877e01a87
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54682235"
---
# <a name="iactiononclreventonevent-method"></a><span data-ttu-id="a7835-102">IActionOnCLREvent::OnEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a7835-102">IActionOnCLREvent::OnEvent Method</span></span>
<span data-ttu-id="a7835-103">Geri çağırmaları bir çağrı kullanılarak kaydedilmiş olayları gerçekleştirir [Iclroneventmanager::registeractiononevent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a7835-103">Performs callbacks on events that have been registered by using a call to the [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7835-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a7835-104">Syntax</span></span>  
  
```  
HRESULT OnEvent (  
    [in] EClrEvent event,  
    [in] PVOID     data  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a7835-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a7835-105">Parameters</span></span>  
 `event`  
 <span data-ttu-id="a7835-106">[in] Aşağıdakilerden birini [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) olay türünü gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="a7835-106">[in] One of the [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) values, which indicates the type of event.</span></span>  
  
 `data`  
 <span data-ttu-id="a7835-107">[in] Hakkında ayrıntılar içeren bir nesne için bir işaretçi `event`.</span><span class="sxs-lookup"><span data-stu-id="a7835-107">[in] A pointer to an object that contains details about `event`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a7835-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a7835-108">Return Value</span></span>  
  
|<span data-ttu-id="a7835-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a7835-109">HRESULT</span></span>|<span data-ttu-id="a7835-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a7835-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a7835-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a7835-111">S_OK</span></span>|<span data-ttu-id="a7835-112">`OnEvent` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="a7835-112">`OnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="a7835-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a7835-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a7835-114">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="a7835-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a7835-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a7835-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a7835-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="a7835-116">The call timed out.</span></span>|  
|<span data-ttu-id="a7835-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a7835-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a7835-118">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="a7835-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a7835-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a7835-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a7835-120">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="a7835-120">An event was cancelled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a7835-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a7835-121">E_FAIL</span></span>|<span data-ttu-id="a7835-122">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="a7835-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a7835-123">CLR, artık bir yöntem E_FAIL döndürürse, işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a7835-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a7835-124">Herhangi bir barındırma yöntemini yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="a7835-124">Subsequent calls to any hosting method return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7835-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a7835-125">Remarks</span></span>  
 <span data-ttu-id="a7835-126">`data` Parametresi belirtilmemiş türünde bir nesne için bir işaretçidir.</span><span class="sxs-lookup"><span data-stu-id="a7835-126">The `data` parameter is a pointer to an object of unspecified type.</span></span> <span data-ttu-id="a7835-127">Varsa `event` parametresi `Event_DomainUnload`, `data` sayısal tanımlayıcısıdır <xref:System.AppDomain> , kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="a7835-127">If the `event` parameter is `Event_DomainUnload`, `data` is the numeric identifier for the <xref:System.AppDomain> that was unloaded.</span></span> <span data-ttu-id="a7835-128">Konak bu tanımlayıcı bir anahtar olarak kullanarak uygun işlemleri gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="a7835-128">The host can take appropriate action using this identifier as a key.</span></span>  
  
 <span data-ttu-id="a7835-129">Varsa `event` olduğu `Event_MDAFired`, `data` işaretçisidir bir [Mdaınfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) içeren gelen bir yönetilen hata ayıklama Yardımcısı (MDA) iletisini çıktı örneği.</span><span class="sxs-lookup"><span data-stu-id="a7835-129">If `event` is `Event_MDAFired`, `data` is a pointer to an [MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) instance that contains the message output from a Managed Debugging Assistant (MDA).</span></span> <span data-ttu-id="a7835-130">Mda'leri, CLR'nin geliştiriciler, aksi takdirde tuzak zor olan olaylar hakkında XML iletileri oluşturarak hatalarını ayıklamaya yardımcı olmak için kullanılan bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="a7835-130">MDAs are a feature of the CLR that help developers with debugging, by generating XML messages about events that are otherwise difficult to trap.</span></span> <span data-ttu-id="a7835-131">Bu türden iletilere yönetilen ve yönetilmeyen kod arasındaki geçişleri hata ayıklama özellikle kullanışlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="a7835-131">Such messages can be especially useful in debugging transitions between managed and unmanaged code.</span></span> <span data-ttu-id="a7835-132">Daha fazla bilgi için [yönetilen hata ayıklama Yardımcıları ile hataları tanılama](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span><span class="sxs-lookup"><span data-stu-id="a7835-132">For more information, see [Diagnosing Errors with Managed Debugging Assistants](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7835-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a7835-133">Requirements</span></span>  
 <span data-ttu-id="a7835-134">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7835-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7835-135">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a7835-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a7835-136">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="a7835-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a7835-137">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7835-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7835-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7835-138">See also</span></span>
- [<span data-ttu-id="a7835-139">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="a7835-139">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="a7835-140">EClrEvent Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="a7835-140">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [<span data-ttu-id="a7835-141">IActionOnCLREvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a7835-141">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [<span data-ttu-id="a7835-142">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a7835-142">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="a7835-143">ICLROnEventManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a7835-143">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
- [<span data-ttu-id="a7835-144">MDAInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="a7835-144">MDAInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md)

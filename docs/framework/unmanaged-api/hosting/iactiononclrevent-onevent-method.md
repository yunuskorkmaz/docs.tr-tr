---
title: "IActionOnCLREvent::OnEvent Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IActionOnCLREvent.OnEvent
api_location: mscoree.dll
api_type: COM
f1_keywords: IActionOnCLREvent::OnEvent
helpviewer_keywords:
- OnEvent method [.NET Framework hosting]
- IActionOnCLREvent::OnEvent method [.NET Framework hosting]
ms.assetid: 0970f10c-4304-4c12-91c0-83e51455afb4
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bfba70cb1e0daf230abd16af6e24b4671334f20d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iactiononclreventonevent-method"></a><span data-ttu-id="2c3b8-102">IActionOnCLREvent::OnEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2c3b8-102">IActionOnCLREvent::OnEvent Method</span></span>
<span data-ttu-id="2c3b8-103">Geri aramalar için bir çağrı kullanılarak kaydedilmiş olayları gerçekleştirir [Iclroneventmanager::registeractiononevent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2c3b8-103">Performs callbacks on events that have been registered by using a call to the [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c3b8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2c3b8-104">Syntax</span></span>  
  
```  
HRESULT OnEvent (  
    [in] EClrEvent event,  
    [in] PVOID     data  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2c3b8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2c3b8-105">Parameters</span></span>  
 `event`  
 <span data-ttu-id="2c3b8-106">[in] Aşağıdakilerden birini [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) olay türünü belirten değer.</span><span class="sxs-lookup"><span data-stu-id="2c3b8-106">[in] One of the [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) values, which indicates the type of event.</span></span>  
  
 `data`  
 <span data-ttu-id="2c3b8-107">[in] Hakkında ayrıntılar içeren bir nesne için bir işaretçi `event`.</span><span class="sxs-lookup"><span data-stu-id="2c3b8-107">[in] A pointer to an object that contains details about `event`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2c3b8-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2c3b8-108">Return Value</span></span>  
  
|<span data-ttu-id="2c3b8-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2c3b8-109">HRESULT</span></span>|<span data-ttu-id="2c3b8-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2c3b8-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2c3b8-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="2c3b8-111">S_OK</span></span>|<span data-ttu-id="2c3b8-112">`OnEvent`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="2c3b8-112">`OnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="2c3b8-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2c3b8-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2c3b8-114">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="2c3b8-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2c3b8-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2c3b8-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2c3b8-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="2c3b8-116">The call timed out.</span></span>|  
|<span data-ttu-id="2c3b8-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2c3b8-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2c3b8-118">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="2c3b8-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2c3b8-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2c3b8-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2c3b8-120">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="2c3b8-120">An event was cancelled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2c3b8-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2c3b8-121">E_FAIL</span></span>|<span data-ttu-id="2c3b8-122">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="2c3b8-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2c3b8-123">Bir yöntem E_FAIL döndürürse, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="2c3b8-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2c3b8-124">Herhangi bir barındırma yöntemi yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="2c3b8-124">Subsequent calls to any hosting method return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c3b8-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2c3b8-125">Remarks</span></span>  
 <span data-ttu-id="2c3b8-126">`data` Belirtilmeyen türünde bir nesne için bir işaretçi bir parametredir.</span><span class="sxs-lookup"><span data-stu-id="2c3b8-126">The `data` parameter is a pointer to an object of unspecified type.</span></span> <span data-ttu-id="2c3b8-127">Varsa `event` parametresi `Event_DomainUnload`, `data` sayısal tanımlayıcısıdır <xref:System.AppDomain> , yüklü değil.</span><span class="sxs-lookup"><span data-stu-id="2c3b8-127">If the `event` parameter is `Event_DomainUnload`, `data` is the numeric identifier for the <xref:System.AppDomain> that was unloaded.</span></span> <span data-ttu-id="2c3b8-128">Konak bir anahtar olarak bu tanımlayıcıyı kullanarak uygun eylemde bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="2c3b8-128">The host can take appropriate action using this identifier as a key.</span></span>  
  
 <span data-ttu-id="2c3b8-129">Varsa `event` olan `Event_MDAFired`, `data` gösteren bir işaretçidir bir [Mdaınfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) ileti çıkış gelen bir yönetilen hata ayıklama Yardımcısı (MDA) içeren örneği.</span><span class="sxs-lookup"><span data-stu-id="2c3b8-129">If `event` is `Event_MDAFired`, `data` is a pointer to an [MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) instance that contains the message output from a Managed Debugging Assistant (MDA).</span></span> <span data-ttu-id="2c3b8-130">Mda'lar, geliştiricilerin, aksi takdirde tuzak zor olan olaylar hakkında XML iletileri oluşturarak hata ayıklamaya yardımcı CLR'ın bir özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="2c3b8-130">MDAs are a feature of the CLR that help developers with debugging, by generating XML messages about events that are otherwise difficult to trap.</span></span> <span data-ttu-id="2c3b8-131">Bu türden iletilere yönetilen ve yönetilmeyen kodu arasında geçişler hata ayıklama özellikle yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="2c3b8-131">Such messages can be especially useful in debugging transitions between managed and unmanaged code.</span></span> <span data-ttu-id="2c3b8-132">Daha fazla bilgi için bkz: [yönetilen hata ayıklama Yardımcıları ile hataları tanılama](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span><span class="sxs-lookup"><span data-stu-id="2c3b8-132">For more information, see [Diagnosing Errors with Managed Debugging Assistants](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c3b8-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2c3b8-133">Requirements</span></span>  
 <span data-ttu-id="2c3b8-134">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c3b8-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c3b8-135">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2c3b8-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2c3b8-136">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="2c3b8-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2c3b8-137">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c3b8-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c3b8-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2c3b8-138">See Also</span></span>  
 [<span data-ttu-id="2c3b8-139">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="2c3b8-139">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="2c3b8-140">EClrEvent Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="2c3b8-140">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)  
 [<span data-ttu-id="2c3b8-141">IActionOnCLREvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2c3b8-141">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 [<span data-ttu-id="2c3b8-142">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2c3b8-142">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="2c3b8-143">ICLROnEventManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2c3b8-143">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)  
 [<span data-ttu-id="2c3b8-144">MDAInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="2c3b8-144">MDAInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md)

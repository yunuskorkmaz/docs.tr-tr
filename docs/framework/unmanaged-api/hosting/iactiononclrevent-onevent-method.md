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
ms.openlocfilehash: 98807717fc913052dae15f9f3cbd462d4f537ad4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126926"
---
# <a name="iactiononclreventonevent-method"></a><span data-ttu-id="9031c-102">IActionOnCLREvent::OnEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9031c-102">IActionOnCLREvent::OnEvent Method</span></span>
<span data-ttu-id="9031c-103">[ICLROnEventManager:: RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) metoduna yapılan bir çağrı kullanılarak kaydedilmiş olaylarda geri çağırmaları gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="9031c-103">Performs callbacks on events that have been registered by using a call to the [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9031c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9031c-104">Syntax</span></span>  
  
```cpp  
HRESULT OnEvent (  
    [in] EClrEvent event,  
    [in] PVOID     data  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9031c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9031c-105">Parameters</span></span>  
 `event`  
 <span data-ttu-id="9031c-106">'ndaki Olay türünü gösteren [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="9031c-106">[in] One of the [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) values, which indicates the type of event.</span></span>  
  
 `data`  
 <span data-ttu-id="9031c-107">'ndaki `event`ayrıntılarını içeren bir nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="9031c-107">[in] A pointer to an object that contains details about `event`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9031c-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9031c-108">Return Value</span></span>  
  
|<span data-ttu-id="9031c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9031c-109">HRESULT</span></span>|<span data-ttu-id="9031c-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9031c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9031c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="9031c-111">S_OK</span></span>|<span data-ttu-id="9031c-112">`OnEvent` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="9031c-112">`OnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="9031c-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9031c-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9031c-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="9031c-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9031c-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9031c-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9031c-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="9031c-116">The call timed out.</span></span>|  
|<span data-ttu-id="9031c-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9031c-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9031c-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="9031c-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9031c-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9031c-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9031c-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="9031c-120">An event was cancelled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9031c-121">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="9031c-121">E_FAIL</span></span>|<span data-ttu-id="9031c-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="9031c-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9031c-123">Bir yöntem E_FAıL döndürürse, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="9031c-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9031c-124">Herhangi bir barındırma yöntemine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="9031c-124">Subsequent calls to any hosting method return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9031c-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9031c-125">Remarks</span></span>  
 <span data-ttu-id="9031c-126">`data` parametresi, belirtilmemiş türdeki bir nesnenin işaretçisidir.</span><span class="sxs-lookup"><span data-stu-id="9031c-126">The `data` parameter is a pointer to an object of unspecified type.</span></span> <span data-ttu-id="9031c-127">`event` parametresi `Event_DomainUnload`, `data` kaldırılan <xref:System.AppDomain> için sayısal tanıtıcıdır.</span><span class="sxs-lookup"><span data-stu-id="9031c-127">If the `event` parameter is `Event_DomainUnload`, `data` is the numeric identifier for the <xref:System.AppDomain> that was unloaded.</span></span> <span data-ttu-id="9031c-128">Ana bilgisayar bu tanımlayıcıyı anahtar olarak kullanarak uygun eylemi gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="9031c-128">The host can take appropriate action using this identifier as a key.</span></span>  
  
 <span data-ttu-id="9031c-129">`event` `Event_MDAFired`, `data` yönetilen hata ayıklama Yardımcısı 'Nın (MDA) ileti çıkışını içeren bir [Mdadınfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) örneğine yönelik bir işaretçidir.</span><span class="sxs-lookup"><span data-stu-id="9031c-129">If `event` is `Event_MDAFired`, `data` is a pointer to an [MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) instance that contains the message output from a Managed Debugging Assistant (MDA).</span></span> <span data-ttu-id="9031c-130">Mdalar, geliştiricilerin hata ayıklamasına yardımcı olan ve tuzak zorluğu eden olaylar hakkında XML iletileri oluşturarak CLR 'nin bir özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="9031c-130">MDAs are a feature of the CLR that help developers with debugging, by generating XML messages about events that are otherwise difficult to trap.</span></span> <span data-ttu-id="9031c-131">Bu tür iletiler, yönetilen ve yönetilmeyen kod arasındaki geçişlerde hata ayıklama için özellikle yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="9031c-131">Such messages can be especially useful in debugging transitions between managed and unmanaged code.</span></span> <span data-ttu-id="9031c-132">Daha fazla bilgi için bkz. [yönetilen hata ayıklama yardımcıları Ile hataları tanılama](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span><span class="sxs-lookup"><span data-stu-id="9031c-132">For more information, see [Diagnosing Errors with Managed Debugging Assistants](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9031c-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9031c-133">Requirements</span></span>  
 <span data-ttu-id="9031c-134">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9031c-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9031c-135">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9031c-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9031c-136">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="9031c-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9031c-137">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9031c-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9031c-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9031c-138">See also</span></span>

- [<span data-ttu-id="9031c-139">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="9031c-139">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="9031c-140">EClrEvent Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="9031c-140">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [<span data-ttu-id="9031c-141">IActionOnCLREvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9031c-141">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [<span data-ttu-id="9031c-142">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9031c-142">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="9031c-143">ICLROnEventManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9031c-143">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
- [<span data-ttu-id="9031c-144">MDAInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="9031c-144">MDAInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md)

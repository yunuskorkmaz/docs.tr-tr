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
ms.openlocfilehash: a216a2925382016adeb100554bdceefdf3ee902b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616066"
---
# <a name="iactiononclreventonevent-method"></a><span data-ttu-id="395d1-102">IActionOnCLREvent::OnEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="395d1-102">IActionOnCLREvent::OnEvent Method</span></span>
<span data-ttu-id="395d1-103">[ICLROnEventManager:: RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) metoduna yapılan bir çağrı kullanılarak kaydedilmiş olaylarda geri çağırmaları gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="395d1-103">Performs callbacks on events that have been registered by using a call to the [ICLROnEventManager::RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="395d1-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="395d1-104">Syntax</span></span>  
  
```cpp  
HRESULT OnEvent (  
    [in] EClrEvent event,  
    [in] PVOID     data  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="395d1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="395d1-105">Parameters</span></span>  
 `event`  
 <span data-ttu-id="395d1-106">'ndaki Olay türünü gösteren [EClrEvent](eclrevent-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="395d1-106">[in] One of the [EClrEvent](eclrevent-enumeration.md) values, which indicates the type of event.</span></span>  
  
 `data`  
 <span data-ttu-id="395d1-107">'ndaki Hakkındaki ayrıntıları içeren bir nesne işaretçisi `event` .</span><span class="sxs-lookup"><span data-stu-id="395d1-107">[in] A pointer to an object that contains details about `event`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="395d1-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="395d1-108">Return Value</span></span>  
  
|<span data-ttu-id="395d1-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="395d1-109">HRESULT</span></span>|<span data-ttu-id="395d1-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="395d1-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="395d1-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="395d1-111">S_OK</span></span>|<span data-ttu-id="395d1-112">`OnEvent`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="395d1-112">`OnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="395d1-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="395d1-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="395d1-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="395d1-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="395d1-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="395d1-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="395d1-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="395d1-116">The call timed out.</span></span>|  
|<span data-ttu-id="395d1-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="395d1-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="395d1-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="395d1-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="395d1-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="395d1-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="395d1-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="395d1-120">An event was cancelled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="395d1-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="395d1-121">E_FAIL</span></span>|<span data-ttu-id="395d1-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="395d1-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="395d1-123">Bir yöntem E_FAIL döndürürse, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="395d1-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="395d1-124">Herhangi bir barındırma yöntemine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="395d1-124">Subsequent calls to any hosting method return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="395d1-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="395d1-125">Remarks</span></span>  
 <span data-ttu-id="395d1-126">`data`Parametresi, belirtilmeyen türdeki bir nesnenin işaretçisidir.</span><span class="sxs-lookup"><span data-stu-id="395d1-126">The `data` parameter is a pointer to an object of unspecified type.</span></span> <span data-ttu-id="395d1-127">Parametresi ise, `event` `Event_DomainUnload` `data` bellekten kaldırılan için sayısal tanıtıcıdır <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="395d1-127">If the `event` parameter is `Event_DomainUnload`, `data` is the numeric identifier for the <xref:System.AppDomain> that was unloaded.</span></span> <span data-ttu-id="395d1-128">Ana bilgisayar bu tanımlayıcıyı anahtar olarak kullanarak uygun eylemi gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="395d1-128">The host can take appropriate action using this identifier as a key.</span></span>  
  
 <span data-ttu-id="395d1-129">`event`İse `Event_MDAFired` , `data` yönetilen hata ayıklama Yardımcısı 'nın (MDA) ileti çıkışını Içeren bir [mdadınfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) örneğine yönelik bir işaretçidir.</span><span class="sxs-lookup"><span data-stu-id="395d1-129">If `event` is `Event_MDAFired`, `data` is a pointer to an [MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) instance that contains the message output from a Managed Debugging Assistant (MDA).</span></span> <span data-ttu-id="395d1-130">Mdalar, geliştiricilerin hata ayıklamasına yardımcı olan ve tuzak zorluğu eden olaylar hakkında XML iletileri oluşturarak CLR 'nin bir özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="395d1-130">MDAs are a feature of the CLR that help developers with debugging, by generating XML messages about events that are otherwise difficult to trap.</span></span> <span data-ttu-id="395d1-131">Bu tür iletiler, yönetilen ve yönetilmeyen kod arasındaki geçişlerde hata ayıklama için özellikle yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="395d1-131">Such messages can be especially useful in debugging transitions between managed and unmanaged code.</span></span> <span data-ttu-id="395d1-132">Daha fazla bilgi için bkz. [yönetilen hata ayıklama yardımcıları Ile hataları tanılama](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span><span class="sxs-lookup"><span data-stu-id="395d1-132">For more information, see [Diagnosing Errors with Managed Debugging Assistants](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="395d1-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="395d1-133">Requirements</span></span>  
 <span data-ttu-id="395d1-134">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="395d1-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="395d1-135">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="395d1-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="395d1-136">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="395d1-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="395d1-137">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="395d1-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="395d1-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="395d1-138">See also</span></span>

- [<span data-ttu-id="395d1-139">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="395d1-139">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="395d1-140">EClrEvent Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="395d1-140">EClrEvent Enumeration</span></span>](eclrevent-enumeration.md)
- [<span data-ttu-id="395d1-141">IActionOnCLREvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="395d1-141">IActionOnCLREvent Interface</span></span>](iactiononclrevent-interface.md)
- [<span data-ttu-id="395d1-142">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="395d1-142">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="395d1-143">ICLROnEventManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="395d1-143">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)
- [<span data-ttu-id="395d1-144">MDAInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="395d1-144">MDAInfo Structure</span></span>](mdainfo-structure.md)

---
title: IHostTaskManager::EndDelayAbort Yöntemi
ms.date: 03/30/2017
api_name:
- IHostTaskManager.EndDelayAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::EndDelayAbort
helpviewer_keywords:
- EndDelayAbort method [.NET Framework hosting]
- IHostTaskManager::EndDelayAbort method [.NET Framework hosting]
ms.assetid: 6e02facb-2504-4356-9af5-0cee1f8436a7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d3e8691461179e4f70a4617fd9487949df62f6cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444385"
---
# <a name="ihosttaskmanagerenddelayabort-method"></a><span data-ttu-id="71dc3-102">IHostTaskManager::EndDelayAbort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="71dc3-102">IHostTaskManager::EndDelayAbort Method</span></span>
<span data-ttu-id="71dc3-103">Yönetilen kod ana bilgisayar, bir önceki çağrısından, geçerli görev gerekir iptal, dönem çıkıyor bildirir [Ihosttaskmanager::begindelayabort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-begindelayabort-method.md).</span><span class="sxs-lookup"><span data-stu-id="71dc3-103">Notifies the host that managed code is exiting the period in which the current task must not be aborted, following an earlier call to [IHostTaskManager::BeginDelayAbort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-begindelayabort-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71dc3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="71dc3-104">Syntax</span></span>  
  
```  
HRESULT EndDelayAbort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="71dc3-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="71dc3-105">Return Value</span></span>  
  
|<span data-ttu-id="71dc3-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="71dc3-106">HRESULT</span></span>|<span data-ttu-id="71dc3-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="71dc3-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="71dc3-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="71dc3-108">S_OK</span></span>|<span data-ttu-id="71dc3-109">`EndDelayAbort` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="71dc3-109">`EndDelayAbort` returned successfully.</span></span>|  
|<span data-ttu-id="71dc3-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="71dc3-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="71dc3-111">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="71dc3-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="71dc3-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="71dc3-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="71dc3-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="71dc3-113">The call timed out.</span></span>|  
|<span data-ttu-id="71dc3-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="71dc3-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="71dc3-115">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="71dc3-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="71dc3-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="71dc3-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="71dc3-117">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="71dc3-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="71dc3-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="71dc3-118">E_FAIL</span></span>|<span data-ttu-id="71dc3-119">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="71dc3-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="71dc3-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="71dc3-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="71dc3-121">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="71dc3-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="71dc3-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="71dc3-122">E_UNEXPECTED</span></span>|<span data-ttu-id="71dc3-123">`EndDelayAbort` karşılık gelen çağrıyı olmadan çağrıldı `BeginDelayAbort`.</span><span class="sxs-lookup"><span data-stu-id="71dc3-123">`EndDelayAbort` was called without a corresponding call to `BeginDelayAbort`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="71dc3-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="71dc3-124">Remarks</span></span>  
 <span data-ttu-id="71dc3-125">CLR karşılık gelen çağrıyı yapar `BeginDelayAbort` çağırmadan önce geçerli görevin üzerinde `EndDelayAbort`.</span><span class="sxs-lookup"><span data-stu-id="71dc3-125">The CLR makes a corresponding call to `BeginDelayAbort` on the current task before calling `EndDelayAbort`.</span></span> <span data-ttu-id="71dc3-126">Bu tür bir karşılık gelen çağrısı olmadığında ana bilgisayarın uyarlamasını [Ihosttaskmanager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) E_UNEXPECTED gelen döndürmelidir `EndDelayAbort`ve herhangi bir eylem yapması.</span><span class="sxs-lookup"><span data-stu-id="71dc3-126">In the absence of such a corresponding call, the host's implementation of [IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) should return E_UNEXPECTED from `EndDelayAbort`, and should take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71dc3-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="71dc3-127">Requirements</span></span>  
 <span data-ttu-id="71dc3-128">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71dc3-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71dc3-129">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="71dc3-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="71dc3-130">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="71dc3-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="71dc3-131">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71dc3-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71dc3-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="71dc3-132">See Also</span></span>  
 <xref:System.Threading>  
 [<span data-ttu-id="71dc3-133">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="71dc3-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="71dc3-134">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="71dc3-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="71dc3-135">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="71dc3-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="71dc3-136">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="71dc3-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)

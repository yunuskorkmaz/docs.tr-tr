---
title: IHostTask::Alert Yöntemi
ms.date: 03/30/2017
api_name:
- IHostTask.Alert
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::Alert
helpviewer_keywords:
- IHostTask::Alert method [.NET Framework hosting]
- Alert method, IHostTask interface [.NET Framework hosting]
ms.assetid: 5245d4b5-b6c3-48df-9cb9-8caf059f43fb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7b1c5132be72cfd9f70d3a81297425109f636195
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54623770"
---
# <a name="ihosttaskalert-method"></a><span data-ttu-id="e9d72-102">IHostTask::Alert Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e9d72-102">IHostTask::Alert Method</span></span>
<span data-ttu-id="e9d72-103">Ana bilgisayar geçerli tarafından temsil edilen bir görev Uyandırma isteklerini [Ihosttask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) görev iptal için örnek.</span><span class="sxs-lookup"><span data-stu-id="e9d72-103">Requests that the host wake the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance, so the task can be aborted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9d72-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e9d72-104">Syntax</span></span>  
  
```  
HRESULT Alert ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="e9d72-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e9d72-105">Return Value</span></span>  
  
|<span data-ttu-id="e9d72-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e9d72-106">HRESULT</span></span>|<span data-ttu-id="e9d72-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e9d72-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e9d72-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="e9d72-108">S_OK</span></span>|<span data-ttu-id="e9d72-109">Yöntemi başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="e9d72-109">The method returned successfully.</span></span>|  
|<span data-ttu-id="e9d72-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e9d72-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e9d72-111">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="e9d72-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e9d72-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e9d72-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e9d72-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="e9d72-113">The call timed out.</span></span>|  
|<span data-ttu-id="e9d72-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e9d72-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e9d72-115">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="e9d72-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e9d72-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e9d72-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e9d72-117">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="e9d72-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e9d72-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e9d72-118">E_FAIL</span></span>|<span data-ttu-id="e9d72-119">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="e9d72-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e9d72-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e9d72-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e9d72-121">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="e9d72-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9d72-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e9d72-122">Remarks</span></span>  
 <span data-ttu-id="e9d72-123">CLR çağrıları `Alert` yöntemi zaman <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> kullanıcı kodundan adlı veya <xref:System.AppDomain> geçerli ilişkili <xref:System.Threading.Thread> kapanıyorsa öyle kapanır.</span><span class="sxs-lookup"><span data-stu-id="e9d72-123">The CLR calls the `Alert` method when <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> is called from user code, or when the <xref:System.AppDomain> associated with the current <xref:System.Threading.Thread> shuts down.</span></span> <span data-ttu-id="e9d72-124">Konak, çağrı zaman uyumsuz olarak yapıldığı için hemen döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="e9d72-124">The host must return immediately, because the call is made asynchronously.</span></span> <span data-ttu-id="e9d72-125">Ana görev hemen uyarı olamaz, sonraki zaman içinde uyarı, bir duruma girer uyku modundan gerekir.</span><span class="sxs-lookup"><span data-stu-id="e9d72-125">If the host cannot alert the task immediately, it must wake up the next time it enters a state in which it can be alerted.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e9d72-126">`Alert` yalnızca çalışma zamanı sonlanana görevleri etkileyen bir [waıt_optıon](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) gibi yöntemler WAIT_ALERTABLE değerine [katılın](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md).</span><span class="sxs-lookup"><span data-stu-id="e9d72-126">`Alert` affects only those tasks to which the runtime has passed a [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) value of WAIT_ALERTABLE to methods such as [Join](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9d72-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e9d72-127">Requirements</span></span>  
 <span data-ttu-id="e9d72-128">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9d72-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9d72-129">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e9d72-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e9d72-130">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="e9d72-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e9d72-131">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9d72-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9d72-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e9d72-132">See also</span></span>
- [<span data-ttu-id="e9d72-133">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e9d72-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="e9d72-134">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e9d72-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="e9d72-135">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e9d72-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="e9d72-136">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e9d72-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)

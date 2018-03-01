---
title: "IHostTask::Alert Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 10dc8b9894c6f5444ccfcfd17f749df1a3fb5d05
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttaskalert-method"></a><span data-ttu-id="184f7-102">IHostTask::Alert Yöntemi</span><span class="sxs-lookup"><span data-stu-id="184f7-102">IHostTask::Alert Method</span></span>
<span data-ttu-id="184f7-103">Ana bilgisayar tarafından geçerli temsil görev Uyandırma isteklerini [Ihosttask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) görevi durduruldu şekilde örneği.</span><span class="sxs-lookup"><span data-stu-id="184f7-103">Requests that the host wake the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance, so the task can be aborted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="184f7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="184f7-104">Syntax</span></span>  
  
```  
HRESULT Alert ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="184f7-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="184f7-105">Return Value</span></span>  
  
|<span data-ttu-id="184f7-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="184f7-106">HRESULT</span></span>|<span data-ttu-id="184f7-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="184f7-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="184f7-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="184f7-108">S_OK</span></span>|<span data-ttu-id="184f7-109">Yöntem başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="184f7-109">The method returned successfully.</span></span>|  
|<span data-ttu-id="184f7-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="184f7-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="184f7-111">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="184f7-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="184f7-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="184f7-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="184f7-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="184f7-113">The call timed out.</span></span>|  
|<span data-ttu-id="184f7-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="184f7-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="184f7-115">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="184f7-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="184f7-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="184f7-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="184f7-117">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="184f7-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="184f7-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="184f7-118">E_FAIL</span></span>|<span data-ttu-id="184f7-119">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="184f7-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="184f7-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="184f7-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="184f7-121">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="184f7-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="184f7-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="184f7-122">Remarks</span></span>  
 <span data-ttu-id="184f7-123">CLR çağrıları `Alert` yöntemi zaman <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> kullanıcı koddan çağrılan veya ne zaman <xref:System.AppDomain> geçerli ilişkili <xref:System.Threading.Thread> kapanır.</span><span class="sxs-lookup"><span data-stu-id="184f7-123">The CLR calls the `Alert` method when <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> is called from user code, or when the <xref:System.AppDomain> associated with the current <xref:System.Threading.Thread> shuts down.</span></span> <span data-ttu-id="184f7-124">Arama zaman uyumsuz olarak yapıldığı için konak hemen döndürmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="184f7-124">The host must return immediately, because the call is made asynchronously.</span></span> <span data-ttu-id="184f7-125">Ana bilgisayar görev hemen uyarı olamaz, sonraki zaman içinde uyarı onu almak bir duruma girdiği Uyandırma gerekir.</span><span class="sxs-lookup"><span data-stu-id="184f7-125">If the host cannot alert the task immediately, it must wake up the next time it enters a state in which it can be alerted.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="184f7-126">`Alert`çalışma zamanı geçtikten görevleri etkiler bir [waıt_optıon](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) gibi yöntemler WAIT_ALERTABLE değerine [katılma](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md).</span><span class="sxs-lookup"><span data-stu-id="184f7-126">`Alert` affects only those tasks to which the runtime has passed a [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) value of WAIT_ALERTABLE to methods such as [Join](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="184f7-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="184f7-127">Requirements</span></span>  
 <span data-ttu-id="184f7-128">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="184f7-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="184f7-129">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="184f7-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="184f7-130">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="184f7-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="184f7-131">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="184f7-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="184f7-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="184f7-132">See Also</span></span>  
 [<span data-ttu-id="184f7-133">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="184f7-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="184f7-134">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="184f7-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="184f7-135">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="184f7-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="184f7-136">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="184f7-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)

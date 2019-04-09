---
title: ICLRTask::Abort Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRTask.Abort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::Abort
helpviewer_keywords:
- ICLRTask::Abort method [.NET Framework hosting]
- Abort method, ICLRTask interface [.NET Framework hosting]
ms.assetid: b3594b5f-2e41-4e36-9096-3586276a138c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 57efd4f29ba7e28adf1af03030d7f83eb32c1c2b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59139782"
---
# <a name="iclrtaskabort-method"></a><span data-ttu-id="9a1f3-102">ICLRTask::Abort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9a1f3-102">ICLRTask::Abort Method</span></span>
<span data-ttu-id="9a1f3-103">Ortak dil çalışma zamanı (CLR) görev iptal isteği, geçerli [Iclrtask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) örneğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9a1f3-103">Requests that the common language runtime (CLR) abort the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a1f3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9a1f3-104">Syntax</span></span>  
  
```  
HRESULT Abort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="9a1f3-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9a1f3-105">Return Value</span></span>  
  
|<span data-ttu-id="9a1f3-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9a1f3-106">HRESULT</span></span>|<span data-ttu-id="9a1f3-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9a1f3-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9a1f3-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="9a1f3-108">S_OK</span></span>|`Abort` <span data-ttu-id="9a1f3-109">başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="9a1f3-109">returned successfully.</span></span>|  
|<span data-ttu-id="9a1f3-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9a1f3-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9a1f3-111">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="9a1f3-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9a1f3-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9a1f3-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9a1f3-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="9a1f3-113">The call timed out.</span></span>|  
|<span data-ttu-id="9a1f3-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9a1f3-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9a1f3-115">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="9a1f3-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9a1f3-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9a1f3-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9a1f3-117">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="9a1f3-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9a1f3-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9a1f3-118">E_FAIL</span></span>|<span data-ttu-id="9a1f3-119">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="9a1f3-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9a1f3-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="9a1f3-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9a1f3-121">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="9a1f3-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9a1f3-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9a1f3-122">Remarks</span></span>  
 <span data-ttu-id="9a1f3-123">CLR'yi başlatır bir <xref:System.Threading.ThreadAbortException> konak çağırdığında `Abort`.</span><span class="sxs-lookup"><span data-stu-id="9a1f3-123">The CLR raises a <xref:System.Threading.ThreadAbortException> when the host calls `Abort`.</span></span> <span data-ttu-id="9a1f3-124">Hemen bir özel durum bilgileri, bir sonlandırıcı ya da özel durum işleme mekanizmalarını, yürütülecek gibi kullanıcı kodu beklemeden başlatıldıktan sonra döndürür.</span><span class="sxs-lookup"><span data-stu-id="9a1f3-124">It returns immediately after the exception information is initialized, without waiting for user code, such as finalizers or exception handling mechanisms, to execute.</span></span> <span data-ttu-id="9a1f3-125">Çağrılar `Abort` böylece hızlı bir şekilde döndürür.</span><span class="sxs-lookup"><span data-stu-id="9a1f3-125">Calls to `Abort` thus return quickly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a1f3-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9a1f3-126">Requirements</span></span>  
 <span data-ttu-id="9a1f3-127">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a1f3-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a1f3-128">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9a1f3-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9a1f3-129">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="9a1f3-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="9a1f3-130">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="9a1f3-130">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9a1f3-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9a1f3-131">See also</span></span>

- [<span data-ttu-id="9a1f3-132">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9a1f3-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="9a1f3-133">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9a1f3-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="9a1f3-134">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9a1f3-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="9a1f3-135">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9a1f3-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)

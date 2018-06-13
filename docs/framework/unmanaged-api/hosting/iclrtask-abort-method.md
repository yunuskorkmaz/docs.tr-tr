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
ms.openlocfilehash: 46d60ff6ab64d57ca5c7020877758657b61125ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434843"
---
# <a name="iclrtaskabort-method"></a><span data-ttu-id="53b08-102">ICLRTask::Abort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="53b08-102">ICLRTask::Abort Method</span></span>
<span data-ttu-id="53b08-103">Ortak dil çalışma zamanı (CLR) görevi iptal isteklerini, geçerli [Iclrtask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) örneğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="53b08-103">Requests that the common language runtime (CLR) abort the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53b08-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="53b08-104">Syntax</span></span>  
  
```  
HRESULT Abort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="53b08-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="53b08-105">Return Value</span></span>  
  
|<span data-ttu-id="53b08-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="53b08-106">HRESULT</span></span>|<span data-ttu-id="53b08-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="53b08-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="53b08-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="53b08-108">S_OK</span></span>|<span data-ttu-id="53b08-109">`Abort` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="53b08-109">`Abort` returned successfully.</span></span>|  
|<span data-ttu-id="53b08-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="53b08-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="53b08-111">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="53b08-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="53b08-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="53b08-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="53b08-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="53b08-113">The call timed out.</span></span>|  
|<span data-ttu-id="53b08-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="53b08-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="53b08-115">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="53b08-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="53b08-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="53b08-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="53b08-117">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="53b08-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="53b08-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="53b08-118">E_FAIL</span></span>|<span data-ttu-id="53b08-119">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="53b08-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="53b08-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="53b08-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="53b08-121">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="53b08-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="53b08-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="53b08-122">Remarks</span></span>  
 <span data-ttu-id="53b08-123">CLR başlatır bir <xref:System.Threading.ThreadAbortException> konak çağırdığında `Abort`.</span><span class="sxs-lookup"><span data-stu-id="53b08-123">The CLR raises a <xref:System.Threading.ThreadAbortException> when the host calls `Abort`.</span></span> <span data-ttu-id="53b08-124">Hemen özel durum bilgilerini, sonlandırıcılar veya özel durum mekanizmaları işleme yürütülecek gibi kullanıcı kodu beklemeden başlatıldıktan sonra döndürür.</span><span class="sxs-lookup"><span data-stu-id="53b08-124">It returns immediately after the exception information is initialized, without waiting for user code, such as finalizers or exception handling mechanisms, to execute.</span></span> <span data-ttu-id="53b08-125">Çağrılar `Abort` böylece hızlı bir şekilde döndürür.</span><span class="sxs-lookup"><span data-stu-id="53b08-125">Calls to `Abort` thus return quickly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53b08-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="53b08-126">Requirements</span></span>  
 <span data-ttu-id="53b08-127">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53b08-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53b08-128">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="53b08-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="53b08-129">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="53b08-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="53b08-130">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53b08-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53b08-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="53b08-131">See Also</span></span>  
 [<span data-ttu-id="53b08-132">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="53b08-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="53b08-133">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="53b08-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="53b08-134">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="53b08-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="53b08-135">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="53b08-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)

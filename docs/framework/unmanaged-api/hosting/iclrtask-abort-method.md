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
ms.openlocfilehash: 026d4c14abed030b80e8e1b3f8363fbd59ac05e4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124913"
---
# <a name="iclrtaskabort-method"></a><span data-ttu-id="092eb-102">ICLRTask::Abort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="092eb-102">ICLRTask::Abort Method</span></span>
<span data-ttu-id="092eb-103">Ortak dil çalışma zamanının (CLR) geçerli [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) örneğinin temsil ettiği görevi iptal ettiği istekler.</span><span class="sxs-lookup"><span data-stu-id="092eb-103">Requests that the common language runtime (CLR) abort the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="092eb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="092eb-104">Syntax</span></span>  
  
```cpp  
HRESULT Abort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="092eb-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="092eb-105">Return Value</span></span>  
  
|<span data-ttu-id="092eb-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="092eb-106">HRESULT</span></span>|<span data-ttu-id="092eb-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="092eb-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="092eb-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="092eb-108">S_OK</span></span>|<span data-ttu-id="092eb-109">`Abort` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="092eb-109">`Abort` returned successfully.</span></span>|  
|<span data-ttu-id="092eb-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="092eb-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="092eb-111">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="092eb-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="092eb-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="092eb-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="092eb-113">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="092eb-113">The call timed out.</span></span>|  
|<span data-ttu-id="092eb-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="092eb-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="092eb-115">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="092eb-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="092eb-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="092eb-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="092eb-117">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="092eb-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="092eb-118">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="092eb-118">E_FAIL</span></span>|<span data-ttu-id="092eb-119">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="092eb-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="092eb-120">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="092eb-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="092eb-121">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="092eb-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="092eb-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="092eb-122">Remarks</span></span>  
 <span data-ttu-id="092eb-123">CLR, ana bilgisayar `Abort`çağırdığında bir <xref:System.Threading.ThreadAbortException> oluşturur.</span><span class="sxs-lookup"><span data-stu-id="092eb-123">The CLR raises a <xref:System.Threading.ThreadAbortException> when the host calls `Abort`.</span></span> <span data-ttu-id="092eb-124">Özel durum bilgileri başlatıldıktan sonra, sonlandırıcılar veya özel durum işleme mekanizmaları gibi Kullanıcı kodunu beklemek zorunda kalmadan hemen geri döner.</span><span class="sxs-lookup"><span data-stu-id="092eb-124">It returns immediately after the exception information is initialized, without waiting for user code, such as finalizers or exception handling mechanisms, to execute.</span></span> <span data-ttu-id="092eb-125">`Abort` çağrısı bu nedenle hızlı döndürülür.</span><span class="sxs-lookup"><span data-stu-id="092eb-125">Calls to `Abort` thus return quickly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="092eb-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="092eb-126">Requirements</span></span>  
 <span data-ttu-id="092eb-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="092eb-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="092eb-128">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="092eb-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="092eb-129">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="092eb-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="092eb-130">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="092eb-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="092eb-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="092eb-131">See also</span></span>

- [<span data-ttu-id="092eb-132">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="092eb-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="092eb-133">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="092eb-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="092eb-134">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="092eb-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="092eb-135">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="092eb-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)

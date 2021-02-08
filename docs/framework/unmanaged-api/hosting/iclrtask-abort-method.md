---
description: ': ICLRTask:: Abort yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: ddb761ac50d7401180355236aa8fdc22cca1c580
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785019"
---
# <a name="iclrtaskabort-method"></a><span data-ttu-id="a6a0d-103">ICLRTask::Abort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a6a0d-103">ICLRTask::Abort Method</span></span>

<span data-ttu-id="a6a0d-104">Ortak dil çalışma zamanının (CLR) geçerli [ICLRTask](iclrtask-interface.md) örneğinin temsil ettiği görevi iptal ettiği istekler.</span><span class="sxs-lookup"><span data-stu-id="a6a0d-104">Requests that the common language runtime (CLR) abort the task that the current [ICLRTask](iclrtask-interface.md) instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6a0d-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="a6a0d-105">Syntax</span></span>  
  
```cpp  
HRESULT Abort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="a6a0d-106">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a6a0d-106">Return Value</span></span>  
  
|<span data-ttu-id="a6a0d-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a6a0d-107">HRESULT</span></span>|<span data-ttu-id="a6a0d-108">Description</span><span class="sxs-lookup"><span data-stu-id="a6a0d-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a6a0d-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="a6a0d-109">S_OK</span></span>|<span data-ttu-id="a6a0d-110">`Abort` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="a6a0d-110">`Abort` returned successfully.</span></span>|  
|<span data-ttu-id="a6a0d-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a6a0d-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a6a0d-112">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="a6a0d-112">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a6a0d-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a6a0d-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a6a0d-114">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="a6a0d-114">The call timed out.</span></span>|  
|<span data-ttu-id="a6a0d-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a6a0d-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a6a0d-116">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="a6a0d-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a6a0d-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a6a0d-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a6a0d-118">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="a6a0d-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a6a0d-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a6a0d-119">E_FAIL</span></span>|<span data-ttu-id="a6a0d-120">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="a6a0d-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a6a0d-121">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a6a0d-121">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a6a0d-122">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="a6a0d-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a6a0d-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a6a0d-123">Remarks</span></span>  

 <span data-ttu-id="a6a0d-124">CLR, <xref:System.Threading.ThreadAbortException> ana bilgisayar çağırdığında bir oluşturur `Abort` .</span><span class="sxs-lookup"><span data-stu-id="a6a0d-124">The CLR raises a <xref:System.Threading.ThreadAbortException> when the host calls `Abort`.</span></span> <span data-ttu-id="a6a0d-125">Özel durum bilgileri başlatıldıktan sonra, sonlandırıcılar veya özel durum işleme mekanizmaları gibi Kullanıcı kodunu beklemek zorunda kalmadan hemen geri döner.</span><span class="sxs-lookup"><span data-stu-id="a6a0d-125">It returns immediately after the exception information is initialized, without waiting for user code, such as finalizers or exception handling mechanisms, to execute.</span></span> <span data-ttu-id="a6a0d-126">Bu nedenle, öğesine yapılan çağrılar `Abort` hızla döndürülür.</span><span class="sxs-lookup"><span data-stu-id="a6a0d-126">Calls to `Abort` thus return quickly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6a0d-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a6a0d-127">Requirements</span></span>  

 <span data-ttu-id="a6a0d-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6a0d-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6a0d-129">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a6a0d-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a6a0d-130">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="a6a0d-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a6a0d-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6a0d-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6a0d-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a6a0d-132">See also</span></span>

- [<span data-ttu-id="a6a0d-133">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a6a0d-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="a6a0d-134">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a6a0d-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="a6a0d-135">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a6a0d-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="a6a0d-136">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a6a0d-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)

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
ms.openlocfilehash: 76f216b12bccc950a34e2b23404ac305de519f4a
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762480"
---
# <a name="iclrtaskabort-method"></a><span data-ttu-id="cebe3-102">ICLRTask::Abort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cebe3-102">ICLRTask::Abort Method</span></span>
<span data-ttu-id="cebe3-103">Ortak dil çalışma zamanının (CLR) geçerli [ICLRTask](iclrtask-interface.md) örneğinin temsil ettiği görevi iptal ettiği istekler.</span><span class="sxs-lookup"><span data-stu-id="cebe3-103">Requests that the common language runtime (CLR) abort the task that the current [ICLRTask](iclrtask-interface.md) instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cebe3-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="cebe3-104">Syntax</span></span>  
  
```cpp  
HRESULT Abort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="cebe3-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="cebe3-105">Return Value</span></span>  
  
|<span data-ttu-id="cebe3-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cebe3-106">HRESULT</span></span>|<span data-ttu-id="cebe3-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cebe3-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cebe3-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="cebe3-108">S_OK</span></span>|<span data-ttu-id="cebe3-109">`Abort`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="cebe3-109">`Abort` returned successfully.</span></span>|  
|<span data-ttu-id="cebe3-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cebe3-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cebe3-111">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="cebe3-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cebe3-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cebe3-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cebe3-113">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="cebe3-113">The call timed out.</span></span>|  
|<span data-ttu-id="cebe3-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cebe3-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cebe3-115">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="cebe3-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cebe3-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cebe3-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cebe3-117">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="cebe3-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="cebe3-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cebe3-118">E_FAIL</span></span>|<span data-ttu-id="cebe3-119">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="cebe3-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cebe3-120">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="cebe3-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cebe3-121">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="cebe3-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cebe3-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cebe3-122">Remarks</span></span>  
 <span data-ttu-id="cebe3-123">CLR, <xref:System.Threading.ThreadAbortException> ana bilgisayar çağırdığında bir oluşturur `Abort` .</span><span class="sxs-lookup"><span data-stu-id="cebe3-123">The CLR raises a <xref:System.Threading.ThreadAbortException> when the host calls `Abort`.</span></span> <span data-ttu-id="cebe3-124">Özel durum bilgileri başlatıldıktan sonra, sonlandırıcılar veya özel durum işleme mekanizmaları gibi Kullanıcı kodunu beklemek zorunda kalmadan hemen geri döner.</span><span class="sxs-lookup"><span data-stu-id="cebe3-124">It returns immediately after the exception information is initialized, without waiting for user code, such as finalizers or exception handling mechanisms, to execute.</span></span> <span data-ttu-id="cebe3-125">Bu nedenle, öğesine yapılan çağrılar `Abort` hızla döndürülür.</span><span class="sxs-lookup"><span data-stu-id="cebe3-125">Calls to `Abort` thus return quickly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cebe3-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cebe3-126">Requirements</span></span>  
 <span data-ttu-id="cebe3-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cebe3-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cebe3-128">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="cebe3-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cebe3-129">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="cebe3-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cebe3-130">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cebe3-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cebe3-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cebe3-131">See also</span></span>

- [<span data-ttu-id="cebe3-132">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cebe3-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="cebe3-133">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cebe3-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="cebe3-134">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cebe3-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="cebe3-135">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cebe3-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)

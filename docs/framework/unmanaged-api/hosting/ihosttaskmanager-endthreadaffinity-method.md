---
title: IHostTaskManager::EndThreadAffinity Yöntemi
ms.date: 03/30/2017
api_name:
- IHostTaskManager.EndThreadAffinity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::EndThreadAffinity
helpviewer_keywords:
- EndThreadAffinity method [.NET Framework hosting]
- IHostTaskManager::EndThreadAffinity method [.NET Framework hosting]
ms.assetid: 7738a904-0cd7-4fde-a3eb-2323a5533157
topic_type:
- apiref
ms.openlocfilehash: 2e857f951a837e1385d02dfc810fc12cfefd0d2b
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83841964"
---
# <a name="ihosttaskmanagerendthreadaffinity-method"></a><span data-ttu-id="51fbb-102">IHostTaskManager::EndThreadAffinity Yöntemi</span><span class="sxs-lookup"><span data-stu-id="51fbb-102">IHostTaskManager::EndThreadAffinity Method</span></span>
<span data-ttu-id="51fbb-103">Şu anda [IHostTaskManager:: Beginthreaerffinity](ihosttaskmanager-beginthreadaffinity-method.md)çağrısından sonra, yönetilen kodun, geçerli görevin başka bir işletim sistemi iş parçacığına taşınmaması gereken dönemden çıkış olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="51fbb-103">Notifies the host that managed code is exiting the period in which the current task must not be moved to another operating system thread, following an earlier call to [IHostTaskManager::BeginThreadAffinity](ihosttaskmanager-beginthreadaffinity-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51fbb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="51fbb-104">Syntax</span></span>  
  
```cpp  
HRESULT EndThreadAffinity ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="51fbb-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="51fbb-105">Return Value</span></span>  
  
|<span data-ttu-id="51fbb-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="51fbb-106">HRESULT</span></span>|<span data-ttu-id="51fbb-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="51fbb-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="51fbb-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="51fbb-108">S_OK</span></span>|<span data-ttu-id="51fbb-109">`EndThreadAffinity`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="51fbb-109">`EndThreadAffinity` returned successfully.</span></span>|  
|<span data-ttu-id="51fbb-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="51fbb-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="51fbb-111">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="51fbb-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="51fbb-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="51fbb-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="51fbb-113">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="51fbb-113">The call timed out.</span></span>|  
|<span data-ttu-id="51fbb-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="51fbb-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="51fbb-115">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="51fbb-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="51fbb-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="51fbb-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="51fbb-117">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="51fbb-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="51fbb-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="51fbb-118">E_FAIL</span></span>|<span data-ttu-id="51fbb-119">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="51fbb-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="51fbb-120">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="51fbb-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="51fbb-121">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="51fbb-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="51fbb-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="51fbb-122">E_UNEXPECTED</span></span>|<span data-ttu-id="51fbb-123">`EndThreadAffinity`daha önceden karşılık gelen bir çağrısı olmadan çağrıldı `BeginThreadAffinity` .</span><span class="sxs-lookup"><span data-stu-id="51fbb-123">`EndThreadAffinity` was called without an earlier corresponding call to `BeginThreadAffinity`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="51fbb-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="51fbb-124">Remarks</span></span>  
 <span data-ttu-id="51fbb-125">CLR `BeginThreadAffinity` çağrılmadan önce geçerli görevde karşılık gelen bir çağrı yapar `EndThreadAffinity` .</span><span class="sxs-lookup"><span data-stu-id="51fbb-125">The CLR makes a corresponding call to `BeginThreadAffinity` on the current task before calling `EndThreadAffinity`.</span></span> <span data-ttu-id="51fbb-126">Buna karşılık gelen bir çağrının yokluğunda, konağın [IHostTaskManager](ihosttaskmanager-interface.md) uygulaması E_UNEXPECTED döndürmelidir ve hiçbir işlem almaz.</span><span class="sxs-lookup"><span data-stu-id="51fbb-126">In the absence of such a corresponding call, the host's implementation of [IHostTaskManager](ihosttaskmanager-interface.md) should return E_UNEXPECTED, and take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51fbb-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="51fbb-127">Requirements</span></span>  
 <span data-ttu-id="51fbb-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51fbb-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51fbb-129">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="51fbb-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="51fbb-130">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="51fbb-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="51fbb-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51fbb-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51fbb-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="51fbb-132">See also</span></span>

- <xref:System.Threading>
- [<span data-ttu-id="51fbb-133">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="51fbb-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="51fbb-134">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="51fbb-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="51fbb-135">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="51fbb-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="51fbb-136">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="51fbb-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)

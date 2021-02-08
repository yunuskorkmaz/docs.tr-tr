---
description: 'Şu konuda daha fazla bilgi edinin: ICLRTask:: Ödemedtask yöntemi'
title: ICLRTask::YieldTask Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRTask.YieldTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::YieldTask
helpviewer_keywords:
- ICLRTask::YieldTask method [.NET Framework hosting]
- YieldTask method [.NET Framework hosting]
ms.assetid: b8eb4095-3a8f-4be3-9446-63e9893dce7d
topic_type:
- apiref
ms.openlocfilehash: b72b31b0a1c10a2b0b1e2ad379b140ff33419fa1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784931"
---
# <a name="iclrtaskyieldtask-method"></a><span data-ttu-id="620ba-103">ICLRTask::YieldTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="620ba-103">ICLRTask::YieldTask Method</span></span>

<span data-ttu-id="620ba-104">Ortak dil çalışma zamanının (CLR) geçerli [ICLRTask](iclrtask-interface.md) örneğinin temsil ettiği görevi yerleştirdiği ve işlemci süresini diğer görevler için kullanılabilir hale getirme istekleri.</span><span class="sxs-lookup"><span data-stu-id="620ba-104">Requests that the common language runtime (CLR) put aside the task that the current [ICLRTask](iclrtask-interface.md) instance represents, and make the processor time available to other tasks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="620ba-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="620ba-105">Syntax</span></span>  
  
```cpp  
HRESULT YieldTask ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="620ba-106">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="620ba-106">Return Value</span></span>  
  
|<span data-ttu-id="620ba-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="620ba-107">HRESULT</span></span>|<span data-ttu-id="620ba-108">Description</span><span class="sxs-lookup"><span data-stu-id="620ba-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="620ba-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="620ba-109">S_OK</span></span>|<span data-ttu-id="620ba-110">`YieldTask` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="620ba-110">`YieldTask` returned successfully.</span></span>|  
|<span data-ttu-id="620ba-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="620ba-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="620ba-112">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="620ba-112">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="620ba-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="620ba-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="620ba-114">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="620ba-114">The call timed out.</span></span>|  
|<span data-ttu-id="620ba-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="620ba-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="620ba-116">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="620ba-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="620ba-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="620ba-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="620ba-118">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="620ba-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="620ba-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="620ba-119">E_FAIL</span></span>|<span data-ttu-id="620ba-120">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="620ba-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="620ba-121">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="620ba-121">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="620ba-122">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="620ba-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="620ba-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="620ba-123">Remarks</span></span>  

 <span data-ttu-id="620ba-124">`YieldTask`Diğer görevler veya süreçler için işlemci kaynakları istemek üzere bir ana bilgisayar çağrısı.</span><span class="sxs-lookup"><span data-stu-id="620ba-124">A host calls `YieldTask` to request processor resources for other tasks or processes.</span></span> <span data-ttu-id="620ba-125">Bu yöntem öncelikle uzun süre çalışan kodun CPU süresi vermesini sağlamak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="620ba-125">This method is primarily intended to allow long-running code to give up CPU time.</span></span> <span data-ttu-id="620ba-126">Çalışma zamanı, geçerli `ICLRTask` Örneğin işlem süresini karşılayabileceği ancak başarılı olma garantisi olmayan bir durumda görevi temsil eden görevi koymaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="620ba-126">The runtime attempts to put the task that the current `ICLRTask` instance represents in a state where it can yield processing time, but makes no guarantee of success.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="620ba-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="620ba-127">Requirements</span></span>  

 <span data-ttu-id="620ba-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="620ba-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="620ba-129">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="620ba-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="620ba-130">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="620ba-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="620ba-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="620ba-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="620ba-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="620ba-132">See also</span></span>

- [<span data-ttu-id="620ba-133">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="620ba-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="620ba-134">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="620ba-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="620ba-135">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="620ba-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="620ba-136">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="620ba-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)

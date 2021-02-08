---
description: ': ICLRTask:: ExitTask yöntemi hakkında daha fazla bilgi edinin'
title: ICLRTask::ExitTask Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRTask.ExitTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::ExitTask
helpviewer_keywords:
- ExitTask method [.NET Framework hosting]
- ICLRTask::ExitTask method [.NET Framework hosting]
ms.assetid: 746c85a6-4b33-4f72-a2e9-379fdf2e96af
topic_type:
- apiref
ms.openlocfilehash: 267b7f284ccac5b535a72dab425c035b6c689361
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784972"
---
# <a name="iclrtaskexittask-method"></a><span data-ttu-id="26c61-103">ICLRTask::ExitTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="26c61-103">ICLRTask::ExitTask Method</span></span>

<span data-ttu-id="26c61-104">Geçerli [ICLRTask](iclrtask-interface.md) örneği tarafından temsil edilen görevin sona erme olduğunu ve görevi düzgün bir şekilde kapatmayı denediğinde ortak dil çalışma ZAMANıNı (CLR) bildirir.</span><span class="sxs-lookup"><span data-stu-id="26c61-104">Notifies the common language runtime (CLR) that the task represented by the current [ICLRTask](iclrtask-interface.md) instance is ending, and attempts to shut the task down gracefully.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26c61-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="26c61-105">Syntax</span></span>  
  
```cpp  
HRESULT ExitTask ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="26c61-106">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="26c61-106">Return Value</span></span>  
  
|<span data-ttu-id="26c61-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="26c61-107">HRESULT</span></span>|<span data-ttu-id="26c61-108">Description</span><span class="sxs-lookup"><span data-stu-id="26c61-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="26c61-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="26c61-109">S_OK</span></span>|<span data-ttu-id="26c61-110">`ExitTask` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="26c61-110">`ExitTask` returned successfully.</span></span>|  
|<span data-ttu-id="26c61-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="26c61-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="26c61-112">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="26c61-112">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="26c61-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="26c61-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="26c61-114">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="26c61-114">The call timed out.</span></span>|  
|<span data-ttu-id="26c61-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="26c61-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="26c61-116">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="26c61-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="26c61-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="26c61-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="26c61-118">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="26c61-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="26c61-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="26c61-119">E_FAIL</span></span>|<span data-ttu-id="26c61-120">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="26c61-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="26c61-121">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="26c61-121">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="26c61-122">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="26c61-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="26c61-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="26c61-123">Remarks</span></span>  

 <span data-ttu-id="26c61-124">`ExitTask` bir görevi, yönetilmeyen bir tür kitaplığından bir iş parçacığını ayırmaya benzer şekilde, temiz bir şekilde kapanmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="26c61-124">`ExitTask` attempts a clean shutdown of a task, in a manner analogous to detaching a thread from an unmanaged type library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26c61-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="26c61-125">Requirements</span></span>  

 <span data-ttu-id="26c61-126">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26c61-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26c61-127">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="26c61-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="26c61-128">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="26c61-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="26c61-129">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26c61-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26c61-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="26c61-130">See also</span></span>

- [<span data-ttu-id="26c61-131">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="26c61-131">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="26c61-132">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="26c61-132">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="26c61-133">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="26c61-133">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="26c61-134">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="26c61-134">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)

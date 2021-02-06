---
description: ': ICLRTask:: RudeAbort Yöntemi hakkında daha fazla bilgi edinin'
title: ICLRTask::RudeAbort Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRTask.RudeAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::RudeAbort
helpviewer_keywords:
- RudeAbort method, ICLRTask interface [.NET Framework hosting]
- ICLRTask::RudeAbort method [.NET Framework hosting]
ms.assetid: b5785468-fcd7-4cc3-8a5d-8796337b53fc
topic_type:
- apiref
ms.openlocfilehash: f152f11ce41018b458ed2cb4df255e486ad54da0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636890"
---
# <a name="iclrtaskrudeabort-method"></a><span data-ttu-id="8e9c9-103">ICLRTask::RudeAbort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8e9c9-103">ICLRTask::RudeAbort Method</span></span>

<span data-ttu-id="8e9c9-104">Ortak dil çalışma zamanı 'nın (CLR) geçerli [ICLRTask arabirimi](iclrtask-interface.md) örneği tarafından temsil edilen görevi hemen ve koşulsuz olarak iptal etmek için yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="8e9c9-104">Instructs the common language runtime (CLR) to abort the task represented by the current [ICLRTask Interface](iclrtask-interface.md) instance immediately and unconditionally.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e9c9-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="8e9c9-105">Syntax</span></span>  
  
```cpp  
HRESULT RudeAbort ();
```  
  
## <a name="return-value"></a><span data-ttu-id="8e9c9-106">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8e9c9-106">Return Value</span></span>  
  
|<span data-ttu-id="8e9c9-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8e9c9-107">HRESULT</span></span>|<span data-ttu-id="8e9c9-108">Description</span><span class="sxs-lookup"><span data-stu-id="8e9c9-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8e9c9-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="8e9c9-109">S_OK</span></span>|<span data-ttu-id="8e9c9-110">`RudeAbort` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="8e9c9-110">`RudeAbort` returned successfully.</span></span>|  
|<span data-ttu-id="8e9c9-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8e9c9-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8e9c9-112">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="8e9c9-112">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8e9c9-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8e9c9-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8e9c9-114">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="8e9c9-114">The call timed out.</span></span>|  
|<span data-ttu-id="8e9c9-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8e9c9-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8e9c9-116">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="8e9c9-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8e9c9-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8e9c9-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8e9c9-118">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="8e9c9-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8e9c9-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8e9c9-119">E_FAIL</span></span>|<span data-ttu-id="8e9c9-120">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="8e9c9-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8e9c9-121">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="8e9c9-121">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8e9c9-122">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="8e9c9-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8e9c9-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8e9c9-123">Remarks</span></span>  

 <span data-ttu-id="8e9c9-124">Bir ana bilgisayar bir `RudeAbort` görevi hemen iptal etmek için çağırır.</span><span class="sxs-lookup"><span data-stu-id="8e9c9-124">A host calls `RudeAbort` to abort a task immediately.</span></span> <span data-ttu-id="8e9c9-125">Sonlandırıcılar ve özel durum işleme yordamlarının yürütülmesi garanti edilmez.</span><span class="sxs-lookup"><span data-stu-id="8e9c9-125">Finalizers and exception handling routines are not guaranteed to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e9c9-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8e9c9-126">Requirements</span></span>  

 <span data-ttu-id="8e9c9-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e9c9-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e9c9-128">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8e9c9-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8e9c9-129">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="8e9c9-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8e9c9-130">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e9c9-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e9c9-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8e9c9-131">See also</span></span>

- [<span data-ttu-id="8e9c9-132">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8e9c9-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="8e9c9-133">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8e9c9-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="8e9c9-134">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8e9c9-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="8e9c9-135">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8e9c9-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)

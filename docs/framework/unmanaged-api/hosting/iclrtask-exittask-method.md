---
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
ms.openlocfilehash: 3f6ccf2eb25e96e0f94c558fb642b153ae3472c1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124905"
---
# <a name="iclrtaskexittask-method"></a><span data-ttu-id="1a9bd-102">ICLRTask::ExitTask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1a9bd-102">ICLRTask::ExitTask Method</span></span>
<span data-ttu-id="1a9bd-103">Geçerli [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) örneği tarafından temsil edilen görevin sona erme olduğunu ve görevi düzgün bir şekilde kapatmayı denediğinde ortak dil çalışma ZAMANıNı (CLR) bildirir.</span><span class="sxs-lookup"><span data-stu-id="1a9bd-103">Notifies the common language runtime (CLR) that the task represented by the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance is ending, and attempts to shut the task down gracefully.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a9bd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1a9bd-104">Syntax</span></span>  
  
```cpp  
HRESULT ExitTask ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="1a9bd-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1a9bd-105">Return Value</span></span>  
  
|<span data-ttu-id="1a9bd-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1a9bd-106">HRESULT</span></span>|<span data-ttu-id="1a9bd-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1a9bd-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1a9bd-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="1a9bd-108">S_OK</span></span>|<span data-ttu-id="1a9bd-109">`ExitTask` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="1a9bd-109">`ExitTask` returned successfully.</span></span>|  
|<span data-ttu-id="1a9bd-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1a9bd-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1a9bd-111">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="1a9bd-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1a9bd-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1a9bd-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1a9bd-113">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="1a9bd-113">The call timed out.</span></span>|  
|<span data-ttu-id="1a9bd-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1a9bd-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1a9bd-115">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="1a9bd-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1a9bd-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1a9bd-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1a9bd-117">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="1a9bd-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1a9bd-118">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="1a9bd-118">E_FAIL</span></span>|<span data-ttu-id="1a9bd-119">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="1a9bd-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1a9bd-120">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="1a9bd-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1a9bd-121">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="1a9bd-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1a9bd-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1a9bd-122">Remarks</span></span>  
 <span data-ttu-id="1a9bd-123">`ExitTask`, bir görevin, yönetilmeyen bir tür kitaplığından bir iş parçacığını ayırmaya benzer şekilde temiz bir şekilde kapatılmasını dener.</span><span class="sxs-lookup"><span data-stu-id="1a9bd-123">`ExitTask` attempts a clean shutdown of a task, in a manner analogous to detaching a thread from an unmanaged type library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a9bd-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1a9bd-124">Requirements</span></span>  
 <span data-ttu-id="1a9bd-125">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a9bd-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a9bd-126">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1a9bd-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1a9bd-127">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="1a9bd-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1a9bd-128">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a9bd-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a9bd-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1a9bd-129">See also</span></span>

- [<span data-ttu-id="1a9bd-130">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1a9bd-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="1a9bd-131">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1a9bd-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="1a9bd-132">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1a9bd-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="1a9bd-133">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1a9bd-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)

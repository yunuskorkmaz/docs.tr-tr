---
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
ms.openlocfilehash: 69e3ecfc82985d52bd5b14e9faf2566e395b622b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124650"
---
# <a name="iclrtaskrudeabort-method"></a><span data-ttu-id="491c5-102">ICLRTask::RudeAbort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="491c5-102">ICLRTask::RudeAbort Method</span></span>
<span data-ttu-id="491c5-103">Ortak dil çalışma zamanı 'nın (CLR) geçerli [ICLRTask arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) örneği tarafından temsil edilen görevi hemen ve koşulsuz olarak iptal etmek için yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="491c5-103">Instructs the common language runtime (CLR) to abort the task represented by the current [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance immediately and unconditionally.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="491c5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="491c5-104">Syntax</span></span>  
  
```cpp  
HRESULT RudeAbort ();   
```  
  
## <a name="return-value"></a><span data-ttu-id="491c5-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="491c5-105">Return Value</span></span>  
  
|<span data-ttu-id="491c5-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="491c5-106">HRESULT</span></span>|<span data-ttu-id="491c5-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="491c5-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="491c5-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="491c5-108">S_OK</span></span>|<span data-ttu-id="491c5-109">`RudeAbort` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="491c5-109">`RudeAbort` returned successfully.</span></span>|  
|<span data-ttu-id="491c5-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="491c5-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="491c5-111">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="491c5-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="491c5-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="491c5-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="491c5-113">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="491c5-113">The call timed out.</span></span>|  
|<span data-ttu-id="491c5-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="491c5-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="491c5-115">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="491c5-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="491c5-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="491c5-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="491c5-117">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="491c5-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="491c5-118">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="491c5-118">E_FAIL</span></span>|<span data-ttu-id="491c5-119">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="491c5-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="491c5-120">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="491c5-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="491c5-121">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="491c5-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="491c5-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="491c5-122">Remarks</span></span>  
 <span data-ttu-id="491c5-123">Bir konak bir görevi hemen durdurmak için `RudeAbort` çağırır.</span><span class="sxs-lookup"><span data-stu-id="491c5-123">A host calls `RudeAbort` to abort a task immediately.</span></span> <span data-ttu-id="491c5-124">Sonlandırıcılar ve özel durum işleme yordamlarının yürütülmesi garanti edilmez.</span><span class="sxs-lookup"><span data-stu-id="491c5-124">Finalizers and exception handling routines are not guaranteed to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="491c5-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="491c5-125">Requirements</span></span>  
 <span data-ttu-id="491c5-126">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="491c5-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="491c5-127">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="491c5-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="491c5-128">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="491c5-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="491c5-129">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="491c5-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="491c5-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="491c5-130">See also</span></span>

- [<span data-ttu-id="491c5-131">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="491c5-131">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="491c5-132">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="491c5-132">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="491c5-133">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="491c5-133">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="491c5-134">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="491c5-134">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)

---
title: IHostThreadPoolManager::QueueUserWorkItem Yöntemi
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.QueueUserWorkItem
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::QueueUserWorkItem
helpviewer_keywords:
- IHostThreadPoolManager::QueueUserWorkItem method [.NET Framework hosting]
- QueueUserWorkItem method [.NET Framework hosting]
ms.assetid: 41602053-8670-4827-9d61-cbfcba509b9c
topic_type:
- apiref
ms.openlocfilehash: 39c35884d0fb53baefafbf86391a349e141418a0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141320"
---
# <a name="ihostthreadpoolmanagerqueueuserworkitem-method"></a><span data-ttu-id="a286a-102">IHostThreadPoolManager::QueueUserWorkItem Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a286a-102">IHostThreadPoolManager::QueueUserWorkItem Method</span></span>
<span data-ttu-id="a286a-103">Yürütme için bir işlevi sıraya alır ve bu işlev tarafından kullanılacak verileri içeren bir nesne belirtir.</span><span class="sxs-lookup"><span data-stu-id="a286a-103">Queues a function for execution, and specifies an object containing data to be used by that function.</span></span> <span data-ttu-id="a286a-104">İşlevi bir iş parçacığı kullanılabilir hale geldiğinde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="a286a-104">The function executes when a thread becomes available.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a286a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a286a-105">Syntax</span></span>  
  
```cpp  
HRESULT QueueUserWorkItem (  
    [in] LPTHREAD_START_ROUTINE Function,  
    [in] PVOID Context,  
    [in] ULONG Flags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a286a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a286a-106">Parameters</span></span>  
 `Function`  
 <span data-ttu-id="a286a-107">'ndaki Yürütülecek işlevi temsil eden bir işlev işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="a286a-107">[in] A function pointer that represents the function to execute.</span></span>  
  
 `Context`  
 <span data-ttu-id="a286a-108">'ndaki `Function`tarafından kullanılacak verileri içeren bir nesne.</span><span class="sxs-lookup"><span data-stu-id="a286a-108">[in] An object that contains data to be used by `Function`.</span></span>  
  
 `Flags`  
 <span data-ttu-id="a286a-109">'ndaki Win32 `QueueUserWorkItem` yöntemi için tanımlanan, denetim yürütme denetimi olan bayraklar değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="a286a-109">[in] One of the flags values, as defined for the Win32 `QueueUserWorkItem` method, that control execution.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a286a-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a286a-110">Return Value</span></span>  
  
|<span data-ttu-id="a286a-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a286a-111">HRESULT</span></span>|<span data-ttu-id="a286a-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a286a-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a286a-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="a286a-113">S_OK</span></span>|<span data-ttu-id="a286a-114">`QueueUserWorkItem` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="a286a-114">`QueueUserWorkItem` returned successfully.</span></span>|  
|<span data-ttu-id="a286a-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a286a-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a286a-116">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="a286a-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a286a-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a286a-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a286a-118">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="a286a-118">The call timed out.</span></span>|  
|<span data-ttu-id="a286a-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a286a-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a286a-120">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="a286a-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a286a-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a286a-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a286a-122">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="a286a-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a286a-123">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="a286a-123">E_FAIL</span></span>|<span data-ttu-id="a286a-124">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="a286a-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a286a-125">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a286a-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a286a-126">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="a286a-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a286a-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a286a-127">Remarks</span></span>  
 <span data-ttu-id="a286a-128">`QueueUserWorkItem` iş öğesini iş parçacığı havuzunda çalışan iş parçacığına sıralar.</span><span class="sxs-lookup"><span data-stu-id="a286a-128">`QueueUserWorkItem` queues a work item to a worker thread in the thread pool.</span></span> <span data-ttu-id="a286a-129">İmzası ve parametre türleri, aynı ada sahip karşılık gelen Win32 fonksiyonuyla aynıdır.</span><span class="sxs-lookup"><span data-stu-id="a286a-129">Its signature and parameter types are identical to those of the corresponding Win32 function, which has the same name.</span></span> <span data-ttu-id="a286a-130">Daha fazla bilgi için bkz. Windows platformu belgeleri.</span><span class="sxs-lookup"><span data-stu-id="a286a-130">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a286a-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a286a-131">Requirements</span></span>  
 <span data-ttu-id="a286a-132">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a286a-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a286a-133">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a286a-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a286a-134">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="a286a-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a286a-135">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a286a-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a286a-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a286a-136">See also</span></span>

- <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="a286a-137">IHostThreadPoolManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a286a-137">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)

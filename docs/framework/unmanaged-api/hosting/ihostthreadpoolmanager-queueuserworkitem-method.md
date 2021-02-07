---
description: ': IHostThreadPoolManager:: QueueUserWorkItem yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: edfbf5cfb34473a5fd920307981237fd5deab9aa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753789"
---
# <a name="ihostthreadpoolmanagerqueueuserworkitem-method"></a><span data-ttu-id="b3a50-103">IHostThreadPoolManager::QueueUserWorkItem Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b3a50-103">IHostThreadPoolManager::QueueUserWorkItem Method</span></span>

<span data-ttu-id="b3a50-104">Yürütme için bir işlevi sıraya alır ve bu işlev tarafından kullanılacak verileri içeren bir nesne belirtir.</span><span class="sxs-lookup"><span data-stu-id="b3a50-104">Queues a function for execution, and specifies an object containing data to be used by that function.</span></span> <span data-ttu-id="b3a50-105">İşlevi bir iş parçacığı kullanılabilir hale geldiğinde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="b3a50-105">The function executes when a thread becomes available.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3a50-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b3a50-106">Syntax</span></span>  
  
```cpp  
HRESULT QueueUserWorkItem (  
    [in] LPTHREAD_START_ROUTINE Function,  
    [in] PVOID Context,  
    [in] ULONG Flags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b3a50-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b3a50-107">Parameters</span></span>  

 `Function`  
 <span data-ttu-id="b3a50-108">'ndaki Yürütülecek işlevi temsil eden bir işlev işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="b3a50-108">[in] A function pointer that represents the function to execute.</span></span>  
  
 `Context`  
 <span data-ttu-id="b3a50-109">'ndaki Tarafından kullanılacak verileri içeren nesne `Function` .</span><span class="sxs-lookup"><span data-stu-id="b3a50-109">[in] An object that contains data to be used by `Function`.</span></span>  
  
 `Flags`  
 <span data-ttu-id="b3a50-110">'ndaki Win32 yöntemi için tanımlanan, yürütme denetimi olan bayraklar değerlerinden biri `QueueUserWorkItem` .</span><span class="sxs-lookup"><span data-stu-id="b3a50-110">[in] One of the flags values, as defined for the Win32 `QueueUserWorkItem` method, that control execution.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b3a50-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b3a50-111">Return Value</span></span>  
  
|<span data-ttu-id="b3a50-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b3a50-112">HRESULT</span></span>|<span data-ttu-id="b3a50-113">Description</span><span class="sxs-lookup"><span data-stu-id="b3a50-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b3a50-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="b3a50-114">S_OK</span></span>|<span data-ttu-id="b3a50-115">`QueueUserWorkItem` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="b3a50-115">`QueueUserWorkItem` returned successfully.</span></span>|  
|<span data-ttu-id="b3a50-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b3a50-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b3a50-117">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="b3a50-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b3a50-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b3a50-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b3a50-119">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="b3a50-119">The call timed out.</span></span>|  
|<span data-ttu-id="b3a50-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b3a50-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b3a50-121">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="b3a50-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b3a50-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b3a50-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b3a50-123">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="b3a50-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b3a50-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b3a50-124">E_FAIL</span></span>|<span data-ttu-id="b3a50-125">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="b3a50-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b3a50-126">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="b3a50-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b3a50-127">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="b3a50-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b3a50-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b3a50-128">Remarks</span></span>  

 <span data-ttu-id="b3a50-129">`QueueUserWorkItem` iş öğesini iş parçacığı havuzundaki bir çalışan iş parçacığına sıralar.</span><span class="sxs-lookup"><span data-stu-id="b3a50-129">`QueueUserWorkItem` queues a work item to a worker thread in the thread pool.</span></span> <span data-ttu-id="b3a50-130">İmzası ve parametre türleri, aynı ada sahip karşılık gelen Win32 fonksiyonuyla aynıdır.</span><span class="sxs-lookup"><span data-stu-id="b3a50-130">Its signature and parameter types are identical to those of the corresponding Win32 function, which has the same name.</span></span> <span data-ttu-id="b3a50-131">Daha fazla bilgi için bkz. Windows platformu belgeleri.</span><span class="sxs-lookup"><span data-stu-id="b3a50-131">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3a50-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b3a50-132">Requirements</span></span>  

 <span data-ttu-id="b3a50-133">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3a50-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3a50-134">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b3a50-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b3a50-135">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="b3a50-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b3a50-136">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3a50-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3a50-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b3a50-137">See also</span></span>

- <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="b3a50-138">IHostThreadPoolManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b3a50-138">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)

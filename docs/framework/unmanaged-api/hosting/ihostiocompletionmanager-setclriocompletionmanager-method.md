---
title: IHostIoCompletionManager::SetCLRIoCompletionManager Yöntemi
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.SetCLRIoCompletionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::SetCLRIoCompletionManager
helpviewer_keywords:
- IHostIoCompletionManager::SetCLRIoCompletionManager method [.NET Framework hosting]
- SetCLRIoCompletionManager method [.NET Framework hosting]
ms.assetid: 4254bb01-3a14-4f34-a3be-60ff1f5072b5
topic_type:
- apiref
ms.openlocfilehash: d370cc81942269bd79e06e0fa57fe5d79832b3c2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724851"
---
# <a name="ihostiocompletionmanagersetclriocompletionmanager-method"></a><span data-ttu-id="759e5-102">IHostIoCompletionManager::SetCLRIoCompletionManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="759e5-102">IHostIoCompletionManager::SetCLRIoCompletionManager Method</span></span>

<span data-ttu-id="759e5-103">Ana bilgisayara, ortak dil çalışma zamanı (CLR) tarafından uygulanan [ıclriocompletionmanager](iclriocompletionmanager-interface.md) örneğine yönelik bir arabirim işaretçisi sağlar.</span><span class="sxs-lookup"><span data-stu-id="759e5-103">Provides the host with an interface pointer to the [ICLRIoCompletionManager](iclriocompletionmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="759e5-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="759e5-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRIoCompletionManager (  
    [in] ICLRIoCompletionManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="759e5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="759e5-105">Parameters</span></span>  

 `pManager`  
 <span data-ttu-id="759e5-106">'ndaki `ICLRIoCompletionManager` Clr tarafından sağlanmış bir örneğe yönelik arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="759e5-106">[in] An interface pointer to an `ICLRIoCompletionManager` instance provided by the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="759e5-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="759e5-107">Return Value</span></span>  
  
|<span data-ttu-id="759e5-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="759e5-108">HRESULT</span></span>|<span data-ttu-id="759e5-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="759e5-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="759e5-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="759e5-110">S_OK</span></span>|<span data-ttu-id="759e5-111">`SetCLRIoCompletionManager` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="759e5-111">`SetCLRIoCompletionManager` returned successfully.</span></span>|  
|<span data-ttu-id="759e5-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="759e5-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="759e5-113">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="759e5-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="759e5-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="759e5-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="759e5-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="759e5-115">The call timed out.</span></span>|  
|<span data-ttu-id="759e5-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="759e5-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="759e5-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="759e5-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="759e5-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="759e5-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="759e5-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="759e5-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="759e5-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="759e5-120">E_FAIL</span></span>|<span data-ttu-id="759e5-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="759e5-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="759e5-122">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="759e5-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="759e5-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="759e5-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="759e5-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="759e5-124">Remarks</span></span>  

 <span data-ttu-id="759e5-125">CLR çağrıldıktan sonra `SetCLRIoCompletionManager` , bir g/ç isteği TAMAMLANDıĞıNDA clr 'yi bilgilendirmek için konağın [ıclriocompletionmanager:: OnCompleted](iclriocompletionmanager-oncomplete-method.md) çağrısı gerekir.</span><span class="sxs-lookup"><span data-stu-id="759e5-125">After the CLR has called `SetCLRIoCompletionManager`, the host must call [ICLRIoCompletionManager::OnComplete](iclriocompletionmanager-oncomplete-method.md) to notify the CLR when an I/O request has been completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="759e5-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="759e5-126">Requirements</span></span>  

 <span data-ttu-id="759e5-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="759e5-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="759e5-128">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="759e5-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="759e5-129">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="759e5-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="759e5-130">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="759e5-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="759e5-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="759e5-131">See also</span></span>

- [<span data-ttu-id="759e5-132">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="759e5-132">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="759e5-133">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="759e5-133">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)

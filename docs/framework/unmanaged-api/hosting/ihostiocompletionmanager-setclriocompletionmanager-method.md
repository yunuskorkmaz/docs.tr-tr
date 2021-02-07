---
description: 'Şu konuda daha fazla bilgi edinin: ıhostiocompletionmanager:: SetCLRIoCompletionManager Yöntemi'
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
ms.openlocfilehash: 1075c33d6de4f5edf34364d67cbc0a21c4f19802
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708300"
---
# <a name="ihostiocompletionmanagersetclriocompletionmanager-method"></a><span data-ttu-id="3b63c-103">IHostIoCompletionManager::SetCLRIoCompletionManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3b63c-103">IHostIoCompletionManager::SetCLRIoCompletionManager Method</span></span>

<span data-ttu-id="3b63c-104">Ana bilgisayara, ortak dil çalışma zamanı (CLR) tarafından uygulanan [ıclriocompletionmanager](iclriocompletionmanager-interface.md) örneğine yönelik bir arabirim işaretçisi sağlar.</span><span class="sxs-lookup"><span data-stu-id="3b63c-104">Provides the host with an interface pointer to the [ICLRIoCompletionManager](iclriocompletionmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b63c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3b63c-105">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRIoCompletionManager (  
    [in] ICLRIoCompletionManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b63c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3b63c-106">Parameters</span></span>  

 `pManager`  
 <span data-ttu-id="3b63c-107">'ndaki `ICLRIoCompletionManager` Clr tarafından sağlanmış bir örneğe yönelik arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="3b63c-107">[in] An interface pointer to an `ICLRIoCompletionManager` instance provided by the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3b63c-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3b63c-108">Return Value</span></span>  
  
|<span data-ttu-id="3b63c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3b63c-109">HRESULT</span></span>|<span data-ttu-id="3b63c-110">Description</span><span class="sxs-lookup"><span data-stu-id="3b63c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3b63c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="3b63c-111">S_OK</span></span>|<span data-ttu-id="3b63c-112">`SetCLRIoCompletionManager` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="3b63c-112">`SetCLRIoCompletionManager` returned successfully.</span></span>|  
|<span data-ttu-id="3b63c-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3b63c-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3b63c-114">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="3b63c-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3b63c-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3b63c-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3b63c-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="3b63c-116">The call timed out.</span></span>|  
|<span data-ttu-id="3b63c-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3b63c-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3b63c-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="3b63c-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3b63c-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3b63c-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3b63c-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="3b63c-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3b63c-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3b63c-121">E_FAIL</span></span>|<span data-ttu-id="3b63c-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="3b63c-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3b63c-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="3b63c-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3b63c-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="3b63c-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3b63c-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3b63c-125">Remarks</span></span>  

 <span data-ttu-id="3b63c-126">CLR çağrıldıktan sonra `SetCLRIoCompletionManager` , bir g/ç isteği TAMAMLANDıĞıNDA clr 'yi bilgilendirmek için konağın [ıclriocompletionmanager:: OnCompleted](iclriocompletionmanager-oncomplete-method.md) çağrısı gerekir.</span><span class="sxs-lookup"><span data-stu-id="3b63c-126">After the CLR has called `SetCLRIoCompletionManager`, the host must call [ICLRIoCompletionManager::OnComplete](iclriocompletionmanager-oncomplete-method.md) to notify the CLR when an I/O request has been completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b63c-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3b63c-127">Requirements</span></span>  

 <span data-ttu-id="3b63c-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b63c-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b63c-129">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3b63c-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3b63c-130">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="3b63c-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3b63c-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b63c-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b63c-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3b63c-132">See also</span></span>

- [<span data-ttu-id="3b63c-133">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3b63c-133">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="3b63c-134">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3b63c-134">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)

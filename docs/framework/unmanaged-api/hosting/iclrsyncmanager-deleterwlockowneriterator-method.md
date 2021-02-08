---
description: ': ICLRSyncManager::D Eleterwlockownerıterator yöntemi hakkında daha fazla bilgi edinin'
title: ICLRSyncManager::DeleteRWLockOwnerIterator Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.DeleteRWLockOwnerIterator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::DeleteRWLockOwnerIterator
helpviewer_keywords:
- ICLRSyncManager::DeleteRWLockOwnerIterator method [.NET Framework hosting]
- DeleteRWLockOwnerIterator method [.NET Framework hosting]
ms.assetid: fcfd340a-b7d6-44e4-8167-2c05b789d483
topic_type:
- apiref
ms.openlocfilehash: 7968f326f1ad92fe6e3a0f91749fb7e462e81c04
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789781"
---
# <a name="iclrsyncmanagerdeleterwlockowneriterator-method"></a><span data-ttu-id="200f7-103">ICLRSyncManager::DeleteRWLockOwnerIterator Yöntemi</span><span class="sxs-lookup"><span data-stu-id="200f7-103">ICLRSyncManager::DeleteRWLockOwnerIterator Method</span></span>

<span data-ttu-id="200f7-104">Ortak dil çalışma zamanının (CLR) [ICLRSyncManager:: CreateRWLockOwnerIterator](iclrsyncmanager-createrwlockowneriterator-method.md)çağrısıyla oluşturulmuş bir yineleyiciyi yok ettiğini ister.</span><span class="sxs-lookup"><span data-stu-id="200f7-104">Requests that the common language runtime (CLR) destroy an iterator that was created by a call to [ICLRSyncManager::CreateRWLockOwnerIterator](iclrsyncmanager-createrwlockowneriterator-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="200f7-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="200f7-105">Syntax</span></span>  
  
```cpp  
HRESULT DeleteRWLockOwnerIterator (  
    [in] SIZE_T  Iterator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="200f7-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="200f7-106">Parameters</span></span>  

 `Iterator`  
 <span data-ttu-id="200f7-107">'ndaki Çağrısı kullanılarak oluşturulan Yineleyici `CreateRWLockOwnerIterator` .</span><span class="sxs-lookup"><span data-stu-id="200f7-107">[in] The iterator that was created by using a call to `CreateRWLockOwnerIterator`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="200f7-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="200f7-108">Return Value</span></span>  
  
|<span data-ttu-id="200f7-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="200f7-109">HRESULT</span></span>|<span data-ttu-id="200f7-110">Description</span><span class="sxs-lookup"><span data-stu-id="200f7-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="200f7-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="200f7-111">S_OK</span></span>|<span data-ttu-id="200f7-112">`DeleteRWLockOwnerIterator` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="200f7-112">`DeleteRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="200f7-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="200f7-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="200f7-114">CLR bir işleme yüklenmemiş veya yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="200f7-114">The CLR has not been loaded into a process, or is in a state in which it cannot run managed code or successfully process the call.</span></span>|  
|<span data-ttu-id="200f7-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="200f7-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="200f7-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="200f7-116">The call timed out.</span></span>|  
|<span data-ttu-id="200f7-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="200f7-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="200f7-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="200f7-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="200f7-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="200f7-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="200f7-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="200f7-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="200f7-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="200f7-121">E_FAIL</span></span>|<span data-ttu-id="200f7-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="200f7-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="200f7-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="200f7-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="200f7-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="200f7-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="200f7-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="200f7-125">Remarks</span></span>  

 <span data-ttu-id="200f7-126">Ana bilgisayar bu yöntemi çağırabilir ve `CreateRWLockOwnerIterator` iş parçacığı uygulamasının eşitlenmiş kalmasını sağlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="200f7-126">The host can call this method and `CreateRWLockOwnerIterator` to ensure that its threading implementation remains synchronized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="200f7-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="200f7-127">Requirements</span></span>  

 <span data-ttu-id="200f7-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="200f7-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="200f7-129">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="200f7-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="200f7-130">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="200f7-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="200f7-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="200f7-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="200f7-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="200f7-132">See also</span></span>

- [<span data-ttu-id="200f7-133">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="200f7-133">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="200f7-134">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="200f7-134">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)

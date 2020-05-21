---
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
ms.openlocfilehash: a4094a64d27072ce257341398bb49419bef9b8bb
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763156"
---
# <a name="iclrsyncmanagerdeleterwlockowneriterator-method"></a><span data-ttu-id="92b4f-102">ICLRSyncManager::DeleteRWLockOwnerIterator Yöntemi</span><span class="sxs-lookup"><span data-stu-id="92b4f-102">ICLRSyncManager::DeleteRWLockOwnerIterator Method</span></span>
<span data-ttu-id="92b4f-103">Ortak dil çalışma zamanının (CLR) [ICLRSyncManager:: CreateRWLockOwnerIterator](iclrsyncmanager-createrwlockowneriterator-method.md)çağrısıyla oluşturulmuş bir yineleyiciyi yok ettiğini ister.</span><span class="sxs-lookup"><span data-stu-id="92b4f-103">Requests that the common language runtime (CLR) destroy an iterator that was created by a call to [ICLRSyncManager::CreateRWLockOwnerIterator](iclrsyncmanager-createrwlockowneriterator-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92b4f-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="92b4f-104">Syntax</span></span>  
  
```cpp  
HRESULT DeleteRWLockOwnerIterator (  
    [in] SIZE_T  Iterator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92b4f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="92b4f-105">Parameters</span></span>  
 `Iterator`  
 <span data-ttu-id="92b4f-106">'ndaki Çağrısı kullanılarak oluşturulan Yineleyici `CreateRWLockOwnerIterator` .</span><span class="sxs-lookup"><span data-stu-id="92b4f-106">[in] The iterator that was created by using a call to `CreateRWLockOwnerIterator`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="92b4f-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="92b4f-107">Return Value</span></span>  
  
|<span data-ttu-id="92b4f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="92b4f-108">HRESULT</span></span>|<span data-ttu-id="92b4f-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="92b4f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="92b4f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="92b4f-110">S_OK</span></span>|<span data-ttu-id="92b4f-111">`DeleteRWLockOwnerIterator`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="92b4f-111">`DeleteRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="92b4f-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="92b4f-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="92b4f-113">CLR bir işleme yüklenmemiş veya yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="92b4f-113">The CLR has not been loaded into a process, or is in a state in which it cannot run managed code or successfully process the call.</span></span>|  
|<span data-ttu-id="92b4f-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="92b4f-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="92b4f-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="92b4f-115">The call timed out.</span></span>|  
|<span data-ttu-id="92b4f-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="92b4f-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="92b4f-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="92b4f-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="92b4f-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="92b4f-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="92b4f-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="92b4f-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="92b4f-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="92b4f-120">E_FAIL</span></span>|<span data-ttu-id="92b4f-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="92b4f-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="92b4f-122">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="92b4f-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="92b4f-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="92b4f-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="92b4f-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="92b4f-124">Remarks</span></span>  
 <span data-ttu-id="92b4f-125">Ana bilgisayar bu yöntemi çağırabilir ve `CreateRWLockOwnerIterator` iş parçacığı uygulamasının eşitlenmiş kalmasını sağlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="92b4f-125">The host can call this method and `CreateRWLockOwnerIterator` to ensure that its threading implementation remains synchronized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92b4f-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="92b4f-126">Requirements</span></span>  
 <span data-ttu-id="92b4f-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92b4f-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92b4f-128">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="92b4f-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="92b4f-129">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="92b4f-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="92b4f-130">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92b4f-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92b4f-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="92b4f-131">See also</span></span>

- [<span data-ttu-id="92b4f-132">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="92b4f-132">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="92b4f-133">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="92b4f-133">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)

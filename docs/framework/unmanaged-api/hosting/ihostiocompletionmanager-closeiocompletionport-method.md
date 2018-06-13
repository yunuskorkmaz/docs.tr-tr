---
title: IHostIoCompletionManager::CloseIoCompletionPort Yöntemi
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.CloseIoCompletionPort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::CloseIoCompletionPort
helpviewer_keywords:
- IHostIoCompletionManager::CloseIoCompletionPort method [.NET Framework hosting]
- CloseIoCompletionPort method [.NET Framework hosting]
ms.assetid: e86ad7be-3758-498a-a972-5522d69dfbb3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 761e3b22014bdd628ffc6763615a285a16a86309
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441775"
---
# <a name="ihostiocompletionmanagercloseiocompletionport-method"></a><span data-ttu-id="5e8fd-102">IHostIoCompletionManager::CloseIoCompletionPort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5e8fd-102">IHostIoCompletionManager::CloseIoCompletionPort Method</span></span>
<span data-ttu-id="5e8fd-103">Ana bilgisayar daha önceki bir çağrı aracılığıyla açılmış bir bağlantı noktasını kapatmak istekleri [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span><span class="sxs-lookup"><span data-stu-id="5e8fd-103">Requests that the host close a port that was opened through an earlier call to [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e8fd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5e8fd-104">Syntax</span></span>  
  
```  
HRESULT CloseIoCompletionPort (  
    [in] HANDLE hPort  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5e8fd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5e8fd-105">Parameters</span></span>  
 `hPort`  
 <span data-ttu-id="5e8fd-106">[in] Kapatmak için bağlantı noktası işleci.</span><span class="sxs-lookup"><span data-stu-id="5e8fd-106">[in] The handle of the port to close.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5e8fd-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5e8fd-107">Return Value</span></span>  
  
|<span data-ttu-id="5e8fd-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5e8fd-108">HRESULT</span></span>|<span data-ttu-id="5e8fd-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5e8fd-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5e8fd-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="5e8fd-110">S_OK</span></span>|<span data-ttu-id="5e8fd-111">`CloseIoCompletionPort` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="5e8fd-111">`CloseIoCompletionPort` returned successfully.</span></span>|  
|<span data-ttu-id="5e8fd-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5e8fd-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5e8fd-113">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="5e8fd-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5e8fd-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5e8fd-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5e8fd-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="5e8fd-115">The call timed out.</span></span>|  
|<span data-ttu-id="5e8fd-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5e8fd-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5e8fd-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="5e8fd-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5e8fd-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5e8fd-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5e8fd-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="5e8fd-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5e8fd-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5e8fd-120">E_FAIL</span></span>|<span data-ttu-id="5e8fd-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="5e8fd-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5e8fd-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="5e8fd-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5e8fd-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="5e8fd-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="5e8fd-124">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="5e8fd-124">E_INVALIDARG</span></span>|<span data-ttu-id="5e8fd-125">Geçersiz bağlantı noktası tanıtıcı geçirildi.</span><span class="sxs-lookup"><span data-stu-id="5e8fd-125">An invalid port handle was passed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5e8fd-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5e8fd-126">Remarks</span></span>  
 <span data-ttu-id="5e8fd-127">`hPort` önceki bir çağrı tarafından oluşturulan bir bağlantı noktası için bir tanıtıcı olmalıdır `CreateIoCompletionPort`.</span><span class="sxs-lookup"><span data-stu-id="5e8fd-127">`hPort` must be a handle to a port that was created by an earlier call to `CreateIoCompletionPort`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e8fd-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5e8fd-128">Requirements</span></span>  
 <span data-ttu-id="5e8fd-129">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e8fd-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e8fd-130">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5e8fd-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5e8fd-131">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="5e8fd-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5e8fd-132">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e8fd-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e8fd-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5e8fd-133">See Also</span></span>  
 [<span data-ttu-id="5e8fd-134">ICLRIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5e8fd-134">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="5e8fd-135">IHostIoCompletionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5e8fd-135">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)

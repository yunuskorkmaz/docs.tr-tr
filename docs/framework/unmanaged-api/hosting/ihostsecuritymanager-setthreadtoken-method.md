---
title: IHostSecurityManager::SetThreadToken Yöntemi
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.SetThreadToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::SetThreadToken
helpviewer_keywords:
- SetThreadToken method [.NET Framework hosting]
- IHostSecurityManager::SetThreadToken method [.NET Framework hosting]
ms.assetid: e951c345-8a86-4587-911b-a1a57bc6428a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 71f5cdfaf47c55107980edf089f8964c5936fb23
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440992"
---
# <a name="ihostsecuritymanagersetthreadtoken-method"></a><span data-ttu-id="e7848-102">IHostSecurityManager::SetThreadToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e7848-102">IHostSecurityManager::SetThreadToken Method</span></span>
<span data-ttu-id="e7848-103">Şu anda yürütülen iş parçacığı için bir tanıtıcı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e7848-103">Sets a handle for the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7848-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e7848-104">Syntax</span></span>  
  
```  
HRESULT SetThreadToken (  
    [in] HANDLE hToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e7848-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e7848-105">Parameters</span></span>  
 `hToken`  
 <span data-ttu-id="e7848-106">[in] Şu anda yürütülen iş parçacığı ayarlamak için belirteci işleyici.</span><span class="sxs-lookup"><span data-stu-id="e7848-106">[in] A handle to the token to set for the currently executing thread.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e7848-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e7848-107">Return Value</span></span>  
  
|<span data-ttu-id="e7848-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e7848-108">HRESULT</span></span>|<span data-ttu-id="e7848-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e7848-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e7848-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="e7848-110">S_OK</span></span>|<span data-ttu-id="e7848-111">`SetThreadToken` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="e7848-111">`SetThreadToken` returned successfully.</span></span>|  
|<span data-ttu-id="e7848-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e7848-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e7848-113">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="e7848-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e7848-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e7848-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e7848-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="e7848-115">The call timed out.</span></span>|  
|<span data-ttu-id="e7848-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e7848-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e7848-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="e7848-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e7848-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e7848-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e7848-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="e7848-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e7848-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e7848-120">E_FAIL</span></span>|<span data-ttu-id="e7848-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="e7848-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e7848-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e7848-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e7848-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="e7848-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e7848-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e7848-124">Remarks</span></span>  
 <span data-ttu-id="e7848-125">`IHostSecurityManager::SetThreadToken` davranır benzer şekilde rasgele bir iş parçacığı için bir tanıtıcı geçirmek arayan Win32 işlevi sağlar ancak bu, aynı adlı karşılık gelen Win32 işlevi while `IHostSecurityManager::SetThreadToken` bir belirteç yalnızca şu anda yürütülen iş parçacığı ile ilişkilendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e7848-125">`IHostSecurityManager::SetThreadToken` behaves similarly to the corresponding Win32 function of the same name, except that the Win32 function allows the caller to pass in a handle to an arbitrary thread, while `IHostSecurityManager::SetThreadToken` can associate a token only with the currently executing thread.</span></span>  
  
 <span data-ttu-id="e7848-126">`HANDLE` Türü COM uyumlu değil; diğer bir deyişle, boyutuna bir işletim sistemine özeldir ve özel hazırlama gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e7848-126">The `HANDLE` type is not COM-compliant; that is, its size is specific to an operating system and it requires custom marshaling.</span></span> <span data-ttu-id="e7848-127">Bu nedenle, bu belirteç CLR ve ana bilgisayar arasında yalnızca işlemdeki kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e7848-127">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7848-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e7848-128">Requirements</span></span>  
 <span data-ttu-id="e7848-129">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7848-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7848-130">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e7848-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e7848-131">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="e7848-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e7848-132">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7848-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7848-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e7848-133">See Also</span></span>  
 [<span data-ttu-id="e7848-134">IHostSecurityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e7848-134">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 [<span data-ttu-id="e7848-135">IHostThreadPoolManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e7848-135">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)

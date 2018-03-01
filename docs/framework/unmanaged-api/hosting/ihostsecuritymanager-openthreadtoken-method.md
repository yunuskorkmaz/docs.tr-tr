---
title: "IHostSecurityManager::OpenThreadToken Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IHostSecurityManager.OpenThreadToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::OpenThreadToken
helpviewer_keywords:
- IHostSecurityManager::OpenThreadToken method [.NET Framework hosting]
- OpenThreadToken method [.NET Framework hosting]
ms.assetid: d5999052-8bf0-4a9e-8621-da6284406b18
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9b5c39632d7628d30149a0a0278f9bf6c865bc29
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsecuritymanageropenthreadtoken-method"></a><span data-ttu-id="3990f-102">IHostSecurityManager::OpenThreadToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3990f-102">IHostSecurityManager::OpenThreadToken Method</span></span>
<span data-ttu-id="3990f-103">Şu anda yürütülen iş parçacığı ile ilişkili isteğe bağlı erişim belirteci açar.</span><span class="sxs-lookup"><span data-stu-id="3990f-103">Opens the discretionary access token associated with the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3990f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3990f-104">Syntax</span></span>  
  
```  
HRESULT OpenThreadToken (  
    [in]  DWORD    dwDesiredAccess,   
    [in]  BOOL     bOpenAsSelf,   
    [out] HANDLE   *phThreadToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3990f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3990f-105">Parameters</span></span>  
 `dwDesiredAccess`  
 <span data-ttu-id="3990f-106">[in] Bir maskesi erişim değerlerin iş parçacığından erişimi istenen türlerini belirtin.</span><span class="sxs-lookup"><span data-stu-id="3990f-106">[in] A mask of access values that specify the requested types of access to the thread token.</span></span> <span data-ttu-id="3990f-107">Bu değerleri Win32 tanımlanan `OpenThreadToken` işlevi.</span><span class="sxs-lookup"><span data-stu-id="3990f-107">These values are defined in the Win32 `OpenThreadToken` function.</span></span> <span data-ttu-id="3990f-108">Belirtecin kısıtlı erişim denetim listesi (DACL) erişim vermek veya reddetmek için hangi tür belirlemek için karşı mutabık istenen erişim türleridir.</span><span class="sxs-lookup"><span data-stu-id="3990f-108">The requested access types are reconciled against the token's discretionary access control list (DACL) to determine which types of access to grant or deny.</span></span>  
  
 `bOpenAsSelf`  
 <span data-ttu-id="3990f-109">[in] `true` erişim denetimi için çağıran iş parçacığı; işlemin güvenlik bağlamını kullanarak yapılması gerektiğini belirtmek için `false` çağıran iş parçacığı için kendi güvenlik bağlamını kullanarak erişim denetimi gerçekleştirilmesi gerektiğini belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="3990f-109">[in] `true` to specify that the access check should be made using the security context of the process for the calling thread; `false` to specify that the access check should be performed using the security context for the calling thread itself.</span></span> <span data-ttu-id="3990f-110">İş parçacığı bir istemcinin kimliğine bürünüyor, güvenlik bağlamı, bir istemci işlemi olabilir.</span><span class="sxs-lookup"><span data-stu-id="3990f-110">If the thread is impersonating a client, the security context can be that of a client process.</span></span>  
  
 `phThreadToken`  
 <span data-ttu-id="3990f-111">[out] Yeni açılan erişim belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3990f-111">[out] A pointer to the newly opened access token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3990f-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3990f-112">Return Value</span></span>  
  
|<span data-ttu-id="3990f-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3990f-113">HRESULT</span></span>|<span data-ttu-id="3990f-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3990f-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3990f-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="3990f-115">S_OK</span></span>|<span data-ttu-id="3990f-116">`OpenThreadToken`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="3990f-116">`OpenThreadToken` returned successfully.</span></span>|  
|<span data-ttu-id="3990f-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3990f-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3990f-118">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="3990f-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3990f-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3990f-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3990f-120">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="3990f-120">The call timed out.</span></span>|  
|<span data-ttu-id="3990f-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3990f-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3990f-122">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="3990f-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3990f-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3990f-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3990f-124">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="3990f-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3990f-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3990f-125">E_FAIL</span></span>|<span data-ttu-id="3990f-126">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="3990f-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3990f-127">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="3990f-127">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3990f-128">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="3990f-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3990f-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3990f-129">Remarks</span></span>  
 <span data-ttu-id="3990f-130">`IHostSecurityManager::OpenThreadToken`davranır benzer şekilde rasgele bir iş parçacığı için bir tanıtıcı geçirmek arayan Win32 işlevi sağlar ancak bu, aynı adlı karşılık gelen Win32 işlevi while `IHostSecurityManager::OpenThreadToken` yalnızca çağıran iş parçacığı ile ilişkili belirteci açar.</span><span class="sxs-lookup"><span data-stu-id="3990f-130">`IHostSecurityManager::OpenThreadToken` behaves similarly to the corresponding Win32 function of the same name, except that the Win32 function allows the caller to pass in a handle to an arbitrary thread, while `IHostSecurityManager::OpenThreadToken` opens only the token associated with the calling thread.</span></span>  
  
 <span data-ttu-id="3990f-131">`HANDLE` Türü COM uyumlu değil, diğer bir deyişle, boyutuna işletim sistemine özeldir ve özel hazırlama gerektirir.</span><span class="sxs-lookup"><span data-stu-id="3990f-131">The `HANDLE` type is not COM-compliant, that is, its size is specific to the operating system, and it requires custom marshaling.</span></span> <span data-ttu-id="3990f-132">Bu nedenle, bu belirteç CLR ve ana bilgisayar arasında yalnızca işlemdeki kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3990f-132">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3990f-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3990f-133">Requirements</span></span>  
 <span data-ttu-id="3990f-134">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3990f-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3990f-135">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3990f-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3990f-136">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="3990f-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3990f-137">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3990f-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3990f-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3990f-138">See Also</span></span>  
 [<span data-ttu-id="3990f-139">IHostSecurityContext Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3990f-139">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [<span data-ttu-id="3990f-140">IHostSecurityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3990f-140">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)

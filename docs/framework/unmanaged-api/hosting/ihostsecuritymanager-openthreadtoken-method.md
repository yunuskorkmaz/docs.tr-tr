---
title: IHostSecurityManager::OpenThreadToken Yöntemi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c1beeb0ff6b2e3493f0814fc3371f189bd4d485d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778012"
---
# <a name="ihostsecuritymanageropenthreadtoken-method"></a><span data-ttu-id="273b6-102">IHostSecurityManager::OpenThreadToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="273b6-102">IHostSecurityManager::OpenThreadToken Method</span></span>
<span data-ttu-id="273b6-103">Şu anda yürütülen iş parçacığıyla ilişkilendirilmiş isteğe bağlı erişim belirteci açılır.</span><span class="sxs-lookup"><span data-stu-id="273b6-103">Opens the discretionary access token associated with the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="273b6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="273b6-104">Syntax</span></span>  
  
```cpp  
HRESULT OpenThreadToken (  
    [in]  DWORD    dwDesiredAccess,   
    [in]  BOOL     bOpenAsSelf,   
    [out] HANDLE   *phThreadToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="273b6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="273b6-105">Parameters</span></span>  
 `dwDesiredAccess`  
 <span data-ttu-id="273b6-106">[in] İstenen iş parçacığı belirteci erişim türlerini belirten erişim değerleri maskesi.</span><span class="sxs-lookup"><span data-stu-id="273b6-106">[in] A mask of access values that specify the requested types of access to the thread token.</span></span> <span data-ttu-id="273b6-107">Bu değerleri Win32'de tanımlanan `OpenThreadToken` işlevi.</span><span class="sxs-lookup"><span data-stu-id="273b6-107">These values are defined in the Win32 `OpenThreadToken` function.</span></span> <span data-ttu-id="273b6-108">İstenen erişim türleri, belirtecin isteğe bağlı erişim denetim listesini (DACL) vermek veya reddetmek için erişim türlerini belirlemek için karşı mutabık kılınır.</span><span class="sxs-lookup"><span data-stu-id="273b6-108">The requested access types are reconciled against the token's discretionary access control list (DACL) to determine which types of access to grant or deny.</span></span>  
  
 `bOpenAsSelf`  
 <span data-ttu-id="273b6-109">[in] `true` erişim denetimi için çağıran iş parçacığını; işlemin güvenlik bağlamını kullanarak yapılması gerektiğini belirtmek için `false` çağıran iş parçacığı için kendi güvenlik bağlamını kullanarak erişim denetimi gerçekleştirilmesi gerektiğini belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="273b6-109">[in] `true` to specify that the access check should be made using the security context of the process for the calling thread; `false` to specify that the access check should be performed using the security context for the calling thread itself.</span></span> <span data-ttu-id="273b6-110">İş parçacığı bir istemci kimliğine bürünme, güvenlik bağlamı, istemci işlemi olabilir.</span><span class="sxs-lookup"><span data-stu-id="273b6-110">If the thread is impersonating a client, the security context can be that of a client process.</span></span>  
  
 `phThreadToken`  
 <span data-ttu-id="273b6-111">[out] Yeni açılan bir erişim belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="273b6-111">[out] A pointer to the newly opened access token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="273b6-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="273b6-112">Return Value</span></span>  
  
|<span data-ttu-id="273b6-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="273b6-113">HRESULT</span></span>|<span data-ttu-id="273b6-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="273b6-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="273b6-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="273b6-115">S_OK</span></span>|<span data-ttu-id="273b6-116">`OpenThreadToken` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="273b6-116">`OpenThreadToken` returned successfully.</span></span>|  
|<span data-ttu-id="273b6-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="273b6-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="273b6-118">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="273b6-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="273b6-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="273b6-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="273b6-120">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="273b6-120">The call timed out.</span></span>|  
|<span data-ttu-id="273b6-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="273b6-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="273b6-122">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="273b6-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="273b6-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="273b6-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="273b6-124">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="273b6-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="273b6-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="273b6-125">E_FAIL</span></span>|<span data-ttu-id="273b6-126">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="273b6-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="273b6-127">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="273b6-127">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="273b6-128">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="273b6-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="273b6-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="273b6-129">Remarks</span></span>  
 <span data-ttu-id="273b6-130">`IHostSecurityManager::OpenThreadToken` davranışını benzer şekilde aynı ada karşılık gelen Win32 işlevini çağıran bir tanıtıcıda rastgele bir iş parçacığına geçirmek Win32 işlevini sağlar dışında while `IHostSecurityManager::OpenThreadToken` yalnızca çağıran iş parçacığıyla ilişkilendirilmiş belirteci açılır.</span><span class="sxs-lookup"><span data-stu-id="273b6-130">`IHostSecurityManager::OpenThreadToken` behaves similarly to the corresponding Win32 function of the same name, except that the Win32 function allows the caller to pass in a handle to an arbitrary thread, while `IHostSecurityManager::OpenThreadToken` opens only the token associated with the calling thread.</span></span>  
  
 <span data-ttu-id="273b6-131">`HANDLE` Tür COM uyumlu değil, diğer bir deyişle, boyutunu işletim sistemine özeldir ve özel sıralama gerektirir.</span><span class="sxs-lookup"><span data-stu-id="273b6-131">The `HANDLE` type is not COM-compliant, that is, its size is specific to the operating system, and it requires custom marshaling.</span></span> <span data-ttu-id="273b6-132">Bu nedenle, bu belirteci yalnızca CLR ile konak arasındaki işlemin içinde kullanıma yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="273b6-132">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="273b6-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="273b6-133">Requirements</span></span>  
 <span data-ttu-id="273b6-134">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="273b6-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="273b6-135">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="273b6-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="273b6-136">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="273b6-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="273b6-137">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="273b6-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="273b6-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="273b6-138">See also</span></span>

- [<span data-ttu-id="273b6-139">IHostSecurityContext Arabirimi</span><span class="sxs-lookup"><span data-stu-id="273b6-139">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="273b6-140">IHostSecurityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="273b6-140">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)

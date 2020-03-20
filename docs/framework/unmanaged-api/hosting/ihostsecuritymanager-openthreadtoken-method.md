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
ms.openlocfilehash: 11d042ea9eecc8d428761da6eaa15f7c2907ebd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176272"
---
# <a name="ihostsecuritymanageropenthreadtoken-method"></a><span data-ttu-id="bc7c3-102">IHostSecurityManager::OpenThreadToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bc7c3-102">IHostSecurityManager::OpenThreadToken Method</span></span>
<span data-ttu-id="bc7c3-103">Şu anda çalıştırılamakta olan iş parçacığıyla ilişkili isteğe bağlı erişim belirteci açılır.</span><span class="sxs-lookup"><span data-stu-id="bc7c3-103">Opens the discretionary access token associated with the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc7c3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bc7c3-104">Syntax</span></span>  
  
```cpp  
HRESULT OpenThreadToken (  
    [in]  DWORD    dwDesiredAccess,
    [in]  BOOL     bOpenAsSelf,
    [out] HANDLE   *phThreadToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bc7c3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bc7c3-105">Parameters</span></span>  
 `dwDesiredAccess`  
 <span data-ttu-id="bc7c3-106">[içinde] İş parçacığı belirteci için istenen erişim türlerini belirten erişim değerleri maskesi.</span><span class="sxs-lookup"><span data-stu-id="bc7c3-106">[in] A mask of access values that specify the requested types of access to the thread token.</span></span> <span data-ttu-id="bc7c3-107">Bu değerler Win32 `OpenThreadToken` işlevinde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="bc7c3-107">These values are defined in the Win32 `OpenThreadToken` function.</span></span> <span data-ttu-id="bc7c3-108">İstenen erişim türleri, hangi erişim türlerinin hibe veya reddedildiğini belirlemek için belirteci isteğe bağlı erişim denetim listesine (DACL) göre uzlaştırılır.</span><span class="sxs-lookup"><span data-stu-id="bc7c3-108">The requested access types are reconciled against the token's discretionary access control list (DACL) to determine which types of access to grant or deny.</span></span>  
  
 `bOpenAsSelf`  
 <span data-ttu-id="bc7c3-109">[içinde] `true` erişim denetiminin arama iş parçacığı için işlemin güvenlik bağlamı kullanılarak yapılması gerektiğini belirtmek için; `false` erişim denetiminin arama iş parçacığının kendisi için güvenlik bağlamı kullanılarak gerçekleştirilmesi gerektiğini belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="bc7c3-109">[in] `true` to specify that the access check should be made using the security context of the process for the calling thread; `false` to specify that the access check should be performed using the security context for the calling thread itself.</span></span> <span data-ttu-id="bc7c3-110">İş parçacığı istemci nin kimliğine bürünüyorsa, güvenlik bağlamı istemci işlemine ait olabilir.</span><span class="sxs-lookup"><span data-stu-id="bc7c3-110">If the thread is impersonating a client, the security context can be that of a client process.</span></span>  
  
 `phThreadToken`  
 <span data-ttu-id="bc7c3-111">[çıkış] Yeni açılan erişim belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bc7c3-111">[out] A pointer to the newly opened access token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bc7c3-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="bc7c3-112">Return Value</span></span>  
  
|<span data-ttu-id="bc7c3-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bc7c3-113">HRESULT</span></span>|<span data-ttu-id="bc7c3-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bc7c3-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bc7c3-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="bc7c3-115">S_OK</span></span>|<span data-ttu-id="bc7c3-116">`OpenThreadToken`başarıyla döndürülür.</span><span class="sxs-lookup"><span data-stu-id="bc7c3-116">`OpenThreadToken` returned successfully.</span></span>|  
|<span data-ttu-id="bc7c3-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bc7c3-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bc7c3-118">Ortak dil çalışma süresi (CLR) bir işleme yüklenmedi veya CLR yönetilen kodu çalıştıramadığı veya aramayı başarıyla işleyemediği bir durumdadır.</span><span class="sxs-lookup"><span data-stu-id="bc7c3-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bc7c3-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bc7c3-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bc7c3-120">Arama zaman doldu.</span><span class="sxs-lookup"><span data-stu-id="bc7c3-120">The call timed out.</span></span>|  
|<span data-ttu-id="bc7c3-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bc7c3-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bc7c3-122">Arayan kilidin sahibi değildir.</span><span class="sxs-lookup"><span data-stu-id="bc7c3-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bc7c3-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bc7c3-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bc7c3-124">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="bc7c3-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bc7c3-125">E_faıl</span><span class="sxs-lookup"><span data-stu-id="bc7c3-125">E_FAIL</span></span>|<span data-ttu-id="bc7c3-126">Bilinmeyen bir felaket hatası meydana geldi.</span><span class="sxs-lookup"><span data-stu-id="bc7c3-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bc7c3-127">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bc7c3-127">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bc7c3-128">Barındırma yöntemleri sonraki aramalar HOST_E_CLRNOTAVAILABLE döndürün.</span><span class="sxs-lookup"><span data-stu-id="bc7c3-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc7c3-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bc7c3-129">Remarks</span></span>  
 <span data-ttu-id="bc7c3-130">`IHostSecurityManager::OpenThreadToken`Win32 işlevi, arayan kişinin bir tutamaç içinde rasgele bir iş parçacığına geçmesine izin verir, ancak `IHostSecurityManager::OpenThreadToken` yalnızca arama iş parçacığı ile ilişkili belirteci açar.</span><span class="sxs-lookup"><span data-stu-id="bc7c3-130">`IHostSecurityManager::OpenThreadToken` behaves similarly to the corresponding Win32 function of the same name, except that the Win32 function allows the caller to pass in a handle to an arbitrary thread, while `IHostSecurityManager::OpenThreadToken` opens only the token associated with the calling thread.</span></span>  
  
 <span data-ttu-id="bc7c3-131">Tür `HANDLE` COM uyumlu değildir, yani boyutu işletim sistemine özgüdür ve özel mareşalleme gerektirir.</span><span class="sxs-lookup"><span data-stu-id="bc7c3-131">The `HANDLE` type is not COM-compliant, that is, its size is specific to the operating system, and it requires custom marshaling.</span></span> <span data-ttu-id="bc7c3-132">Bu nedenle, bu belirteç yalnızca işlem içinde, CLR ve ana bilgisayar arasında kullanım içindir.</span><span class="sxs-lookup"><span data-stu-id="bc7c3-132">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc7c3-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bc7c3-133">Requirements</span></span>  
 <span data-ttu-id="bc7c3-134">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc7c3-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc7c3-135">**Üstbilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bc7c3-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bc7c3-136">**Kütüphane:** MSCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="bc7c3-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bc7c3-137">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc7c3-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc7c3-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc7c3-138">See also</span></span>

- [<span data-ttu-id="bc7c3-139">IHostSecurityContext Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bc7c3-139">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="bc7c3-140">IHostSecurityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bc7c3-140">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)

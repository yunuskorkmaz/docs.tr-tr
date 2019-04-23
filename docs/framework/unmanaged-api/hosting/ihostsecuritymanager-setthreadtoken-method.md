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
ms.openlocfilehash: c67471c0d88ccffbfe9b7c77809124452ccc2e5b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59208078"
---
# <a name="ihostsecuritymanagersetthreadtoken-method"></a><span data-ttu-id="6ada5-102">IHostSecurityManager::SetThreadToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6ada5-102">IHostSecurityManager::SetThreadToken Method</span></span>
<span data-ttu-id="6ada5-103">Şu anda çalışan bir iş parçacığı için bir tanıtıcı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6ada5-103">Sets a handle for the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ada5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6ada5-104">Syntax</span></span>  
  
```  
HRESULT SetThreadToken (  
    [in] HANDLE hToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6ada5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6ada5-105">Parameters</span></span>  
 `hToken`  
 <span data-ttu-id="6ada5-106">[in] Yürütülmekte olan iş parçacığını için ayarlanacak belirteci işleyici.</span><span class="sxs-lookup"><span data-stu-id="6ada5-106">[in] A handle to the token to set for the currently executing thread.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6ada5-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6ada5-107">Return Value</span></span>  
  
|<span data-ttu-id="6ada5-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6ada5-108">HRESULT</span></span>|<span data-ttu-id="6ada5-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6ada5-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6ada5-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="6ada5-110">S_OK</span></span>|<span data-ttu-id="6ada5-111">`SetThreadToken` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="6ada5-111">`SetThreadToken` returned successfully.</span></span>|  
|<span data-ttu-id="6ada5-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6ada5-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6ada5-113">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="6ada5-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6ada5-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6ada5-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6ada5-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="6ada5-115">The call timed out.</span></span>|  
|<span data-ttu-id="6ada5-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6ada5-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6ada5-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="6ada5-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6ada5-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6ada5-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6ada5-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="6ada5-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6ada5-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6ada5-120">E_FAIL</span></span>|<span data-ttu-id="6ada5-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="6ada5-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6ada5-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="6ada5-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6ada5-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="6ada5-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6ada5-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6ada5-124">Remarks</span></span>  
 <span data-ttu-id="6ada5-125">`IHostSecurityManager::SetThreadToken` davranışını benzer şekilde aynı ada karşılık gelen Win32 işlevini çağıran bir tanıtıcıda rastgele bir iş parçacığına geçirmek Win32 işlevini sağlar dışında while `IHostSecurityManager::SetThreadToken` bir belirteç yalnızca şu anda yürütülen iş parçacığı ile ilişkilendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ada5-125">`IHostSecurityManager::SetThreadToken` behaves similarly to the corresponding Win32 function of the same name, except that the Win32 function allows the caller to pass in a handle to an arbitrary thread, while `IHostSecurityManager::SetThreadToken` can associate a token only with the currently executing thread.</span></span>  
  
 <span data-ttu-id="6ada5-126">`HANDLE` Tür COM uyumlu değil; diğer bir deyişle, bir işletim sistemine özgü boyutuna ve özel sıralama gerektirir.</span><span class="sxs-lookup"><span data-stu-id="6ada5-126">The `HANDLE` type is not COM-compliant; that is, its size is specific to an operating system and it requires custom marshaling.</span></span> <span data-ttu-id="6ada5-127">Bu nedenle, bu belirteci yalnızca CLR ile konak arasındaki işlemin içinde kullanıma yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="6ada5-127">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ada5-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6ada5-128">Requirements</span></span>  
 <span data-ttu-id="6ada5-129">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ada5-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ada5-130">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6ada5-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6ada5-131">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="6ada5-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6ada5-132">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ada5-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ada5-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6ada5-133">See also</span></span>

- [<span data-ttu-id="6ada5-134">IHostSecurityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6ada5-134">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [<span data-ttu-id="6ada5-135">IHostThreadPoolManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6ada5-135">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)

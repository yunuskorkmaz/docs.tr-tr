---
title: IHostSecurityManager::ImpersonateLoggedOnUser Yöntemi
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.ImpersonateLoggedOnUser
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::ImpersonateLoggedOnUser
helpviewer_keywords:
- ImpersonateLoggedOnUser method [.NET Framework hosting]
- IHostSecurityManager::ImpersonateLoggedOnUser method [.NET Framework hosting]
ms.assetid: acc49ba0-f1d9-45ad-871f-9d053a89dcbe
topic_type:
- apiref
ms.openlocfilehash: 93051ca9a0b6f57f41d0d17335a838fe92832d8d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121493"
---
# <a name="ihostsecuritymanagerimpersonateloggedonuser-method"></a><span data-ttu-id="98266-102">IHostSecurityManager::ImpersonateLoggedOnUser Yöntemi</span><span class="sxs-lookup"><span data-stu-id="98266-102">IHostSecurityManager::ImpersonateLoggedOnUser Method</span></span>
<span data-ttu-id="98266-103">Geçerli Kullanıcı kimliğinin kimlik bilgileri kullanılarak kodun yürütülmesini ister.</span><span class="sxs-lookup"><span data-stu-id="98266-103">Requests that code be executed using the credentials of the current user identity.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98266-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="98266-104">Syntax</span></span>  
  
```cpp  
HRESULT ImpersonateLoggedOnUser (  
    [in] HANDLE hToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="98266-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="98266-105">Parameters</span></span>  
 `hToken`  
 <span data-ttu-id="98266-106">'ndaki Kimliğine bürünülen kullanıcının kimlik bilgilerini temsil eden bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="98266-106">[in] A token representing the credentials of the user to be impersonated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="98266-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="98266-107">Return Value</span></span>  
  
|<span data-ttu-id="98266-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="98266-108">HRESULT</span></span>|<span data-ttu-id="98266-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="98266-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="98266-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="98266-110">S_OK</span></span>|<span data-ttu-id="98266-111">`ImpersonateLoggedOnUser` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="98266-111">`ImpersonateLoggedOnUser` returned successfully.</span></span>|  
|<span data-ttu-id="98266-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="98266-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="98266-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="98266-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="98266-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="98266-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="98266-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="98266-115">The call timed out.</span></span>|  
|<span data-ttu-id="98266-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="98266-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="98266-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="98266-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="98266-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="98266-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="98266-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="98266-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="98266-120">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="98266-120">E_FAIL</span></span>|<span data-ttu-id="98266-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="98266-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="98266-122">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="98266-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="98266-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="98266-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="98266-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="98266-124">Remarks</span></span>  
 <span data-ttu-id="98266-125">Geçerli Kullanıcı kimliğinin kimlik bilgilerine yönelik bir tanıtıcı almak için `LogonUser` veya ilgili bir Win32 işlevi çağırın.</span><span class="sxs-lookup"><span data-stu-id="98266-125">Call `LogonUser` or a related Win32 function to get a handle to the credentials of the current user identity.</span></span>  
  
 <span data-ttu-id="98266-126">`HANDLE` türü, COM uyumlu değildir, diğer bir deyişle, boyutu bir işletim sistemine özeldir ve özel sıralama gerektirir.</span><span class="sxs-lookup"><span data-stu-id="98266-126">The `HANDLE` type is not COM-compliant, that is, its size is specific to an operating system, and it requires custom marshaling.</span></span> <span data-ttu-id="98266-127">Bu nedenle, bu belirteç yalnızca işlem içinde, CLR ile ana bilgisayar arasında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="98266-127">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98266-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="98266-128">Requirements</span></span>  
 <span data-ttu-id="98266-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98266-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98266-130">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="98266-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="98266-131">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="98266-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="98266-132">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98266-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98266-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="98266-133">See also</span></span>

- [<span data-ttu-id="98266-134">IHostSecurityContext Arabirimi</span><span class="sxs-lookup"><span data-stu-id="98266-134">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="98266-135">IHostSecurityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="98266-135">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [<span data-ttu-id="98266-136">RevertToSelf Yöntemi</span><span class="sxs-lookup"><span data-stu-id="98266-136">RevertToSelf Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md)
